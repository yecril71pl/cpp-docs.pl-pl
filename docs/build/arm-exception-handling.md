---
title: Obsługa wyjątków ARM
ms.date: 07/11/2018
ms.assetid: fe0e615f-c033-4ad5-97f4-ff96af45b201
ms.openlocfilehash: c55baf453c1879f1e0a857cc746bba7802d69f88
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303283"
---
# <a name="arm-exception-handling"></a>Obsługa wyjątków ARM

System Windows on ARM używa tego samego mechanizmu obsługi wyjątków strukturalnych dla asynchronicznie generowanych przez sprzęt wyjątków i synchronicznych wyjątków generowanych przez oprogramowanie. Obsługa wyjątków specyficznych dla języka jest tworzona w oparciu o obsługę wyjątków strukturalnych systemu Windows przy użyciu funkcji pomocnika języka. W tym dokumencie opisano obsługę wyjątków w systemie Windows na platformie ARM oraz pomocników języka używanych przez kod generowany przez asembler Microsoft ARM i kompilator MSVC.

## <a name="arm-exception-handling"></a>Obsługa wyjątków ARM

System Windows on ARM używa *kodów operacji unwind* do kontrolowania odwinięcia stosu podczas [obsługi wyjątków strukturalnych](/windows/win32/debug/structured-exception-handling) (SEH). Kody operacji unwind są sekwencją bajtów przechowywanych w sekcji. xdata obrazu wykonywalnego. Opisują one operacje prologu i kodu epilogu w sposób abstrakcyjny, dzięki czemu efekty prologu funkcji mogą być cofnięte w celu odwinięcia ramki stosu obiektu wywołującego.

EABI ARM (interfejs binarny aplikacji osadzonych) Określa model odwinięcia wyjątku, który używa kodów unwindy, ale nie jest wystarczający do rozwinięcia SEH w systemie Windows, który musi obsługiwać asynchroniczne przypadki, w których procesor jest w środku prologuu lub epilogu funkcji. System Windows oddziela także kontrolę odwracania do niezawijania na poziomie funkcji oraz odwracania zakresu specyficznego dla języka, który jest ujednolicony w EABI ARM. Z tego względu system Windows on ARM określa więcej szczegółów dotyczących odwinięcia danych i procedury.

### <a name="assumptions"></a>Założenia

Obrazy wykonywalne dla systemu Windows w usłudze ARM używają przenośnego formatu pliku wykonywalnego (PE). Aby uzyskać więcej informacji, zobacz [Specyfikacja środowiska Microsoft PE i COFF](https://go.microsoft.com/fwlink/p/?linkid=84140). Informacje o obsłudze wyjątków są przechowywane w sekcjach. pdata i. xdata obrazu.

Mechanizm obsługi wyjątków wprowadza pewne założenia dotyczące kodu, który następuje po ABI dla systemu Windows na ARM:

- Gdy wystąpi wyjątek w treści funkcji, nie ma znaczenia, czy operacje prologu są cofnięte lub operacje epilogu są wykonywane w sposób do przodu. Oba powinny generować identyczne wyniki.

- Prologues i epilogues są wzajemnie dublowane. Może to służyć do zmniejszenia rozmiaru metadanych potrzebnych do opisania odwinięcia.

- Funkcje są stosunkowo małe. Niektóre optymalizacje bazują na tym na wydajnej pakowaniu danych.

- Jeśli warunek jest umieszczony na epilogu, ma on zastosowanie równo do każdej instrukcji w epilogu.

- Jeśli wskaźnik stosu (SP) jest zapisywany w innym rejestrze w prologu, ten rejestr musi pozostać niezmieniony w całej funkcji, dzięki czemu oryginalna SP może zostać odzyskana w dowolnym momencie.

- Jeśli SP nie zostanie zapisany w innym rejestrze, wszystkie manipulowanie nim musi nastąpić wyłącznie w prologu i epilogu.

- Aby można było odwinięcie dowolnej ramki stosu, wymagane są następujące operacje:

  - Dostosuj R13 (SP) w przyrostach 4-bajtowych.

  - Wyskakujące jedno lub więcej rejestrów całkowitych.

  - Wyskakujące jedno lub więcej rejestrów Visual FoxPro (wirtualne zmiennoprzecinkowe).

  - Skopiuj dowolną wartość rejestru do R13 (SP).

  - Załaduj SP ze stosu przy użyciu małej operacji po zmniejszeniu.

  - Przeanalizuj jeden z kilku dobrze zdefiniowanych typów ramek.

### <a name="pdata-records"></a>Rekordy. pdata

Rekordy. pdata w obrazie w formacie PE to uporządkowana Tablica elementów o stałej długości, która opisuje każdą funkcję manipulowania stosem. Funkcje liścia, które są funkcjami, które nie wywołują innych funkcji, nie wymagają rekordów. pdata, gdy nie manipulują stosem. (Oznacza to, że nie wymagają żadnego lokalnego magazynu i nie trzeba zapisywać ani przywracać rejestrów nietrwałych.). Rekordy dla tych funkcji można pominąć w sekcji. pdata, aby zaoszczędzić miejsce. Operacja unwind z jednej z tych funkcji może po prostu skopiować adres zwrotny z usługi link Register (LR) do licznika programu (komputer), aby przejść do obiektu wywołującego.

Każdy rekord pData dla ARM ma długość 8 bajtów. Ogólny format rekordu umieszcza względny adres wirtualny (RVA) funkcji uruchamianej w pierwszym słowie 32-bitowym, a następnie drugi wyraz zawierający wskaźnik do zmiennej length. xdata lub spakowany wyraz, który opisuje funkcję kanoniczną Sekwencja odwinięcia, jak pokazano w poniższej tabeli:

|Przesunięcie wyrazu|Bity|Cel|
|-----------------|----------|-------------|
|0|0-31|*Początkowy adres RVA funkcji* to 32-bitowy adres RVA początku funkcji. Jeśli funkcja zawiera kod kciuka, musi być ustawiony niski bit tego adresu.|
|1|0-1|*Flaga* to pole 2-bitowe, które wskazuje, jak interpretować pozostałe 30 bitów drugiego. pdata. Jeśli *Flaga* ma wartość 0, pozostałe bity tworzą *adres RVA informacji o wyjątku* (z niską liczbą bitów niejawnie 0). Jeśli *Flaga* jest różna od zera, pozostałe bity tworzą *spakowaną strukturę danych unwind* .|
|1|2-31|*Informacje o wyjątku adres RVA* lub *spakowane dane operacji unwind*.<br /><br /> *Informacje o wyjątku adres RVA* jest adresem struktury informacji o wyjątku o zmiennej długości przechowywanej w sekcji. xdata. Te dane muszą być wyrównane 4-bajtowo.<br /><br /> *Spakowane dane unwind* to skompresowany opis operacji wymaganych do odwinięcia od funkcji, przy założeniu, że forma kanoniczna. W takim przypadku nie jest wymagany żaden rekord. xdata.|

### <a name="packed-unwind-data"></a>Spakowane dane operacji unwind

W przypadku funkcji, których prologues i epilogues postępują zgodnie z poniższym formularzem kanonicznym, można użyć zapakowanych danych operacji unwind. Eliminuje to konieczność stosowania rekordu. xdata i znacząco zmniejsza ilość miejsca wymaganego do udostępnienia danych unwind. Kanoniczne prologues i epilogues są zaprojektowane tak, aby spełniały typowe wymagania prostej funkcji, która nie wymaga obsługi wyjątków, i wykonuje jej instalację i usuwania w standardowej kolejności.

W tej tabeli przedstawiono format rekordu. pdata, który ma spakowane dane unwind:

|Przesunięcie wyrazu|Bity|Cel|
|-----------------|----------|-------------|
|0|0-31|*Początkowy adres RVA funkcji* to 32-bitowy adres RVA początku funkcji. Jeśli funkcja zawiera kod kciuka, musi być ustawiony niski bit tego adresu.|
|1|0-1|*Flaga* to pole 2-bitowe, które ma następujące znaczenie:<br /><br />-00 = spakowane dane operacji unwind nie są używane; pozostałe bity punktu do rekordu. xdata.<br />-01 = spakowane dane operacji unwind.<br />-10 = spakowane dane operacji unwindy, gdy zakłada się, że nie ma żadnych prologu. Jest to przydatne w przypadku opisywania fragmentów funkcji, które są rozłączone z początkiem funkcji.<br />-11 = zarezerwowane.|
|1|2-12|*Długość funkcji* to pole 11-bitowe, które zapewnia długość całej funkcji w bajtach podzieloną przez 2. Jeśli funkcja jest większa niż 4K bajtów, w zamian należy użyć pełnego rekordu. xdata.|
|1|13-14|*RET* to pole 2-bitowe, które określa sposób, w jaki funkcja zwraca:<br /><br />-00 = Return za pośrednictwem pop {PC} (w tym przypadku bit flagi *L* musi mieć wartość 1).<br />-01 = Return przy użyciu gałęzi 16-bitowej.<br />-10 = Return przy użyciu gałęzi 32-bitowej.<br />-11 = nie epilogu. Jest to przydatne w przypadku opisywania nieciągłego fragmentu funkcji, który może zawierać tylko prologu, ale którego epilogu jest w innym miejscu.|
|1|15|*H* jest flagą 1-bitową wskazującą, czy funkcja "domy" jest rejestrem parametru Integer (r0-r3) przez wypchnięcie ich na początku funkcji, i cofa alokację 16 bajtów stosu przed zwróceniem. (0 = nie zawiera rejestrów domowych, 1 = Rejestr domów).|
|1|16-18|*Reg* to pole 3-bitowe, które wskazuje indeks ostatniego zapisanego nietrwałego rejestru. Jeśli wartość *R* bit to 0, są zapisywane tylko rejestry całkowite i przyjmuje się, że znajdują się one w zakresie R4-RN, gdzie N jest równa 4 + *reg*. Jeśli wartość *R* bit to 1, są zapisywane tylko rejestry zmiennoprzecinkowe i przyjmuje się, że znajdują się one w zakresie D8-DN, gdzie N jest równa 8 + *reg*. Specjalna kombinacja *R* = 1 i *reg* = 7 wskazuje, że żadne rejestry nie są zapisywane.|
|1|19|*R* jest flagą 1-bitową wskazującą, czy zapisane rejestry nietrwałe są rejestrami typu Liczba całkowita (0) czy rejestry zmiennoprzecinkowe (1). Jeśli wartość *R* jest ustawiona na 1, a pole *reg* ma wartość 7, żadne nietrwałe rejestry zostały wypchnięte.|
|1|20|*L* jest flagą 1-bitową wskazującą, czy funkcja zapisuje/przywraca LR, wraz z innymi rejestrami wskazanymi przez pole *reg* . (0 = nie zapisuje/przywraca, 1 = wykonuje zapisywanie/Przywracanie).|
|1|21|*C* jest flagą 1-bitową wskazującą, czy funkcja zawiera dodatkowe instrukcje dotyczące konfigurowania łańcucha ramek na potrzeby szybkiego przechodzenia do stosu (1) lub nie (0). Jeśli ten bit jest ustawiony, R11 jest niejawnie dodawany do listy liczb całkowitych nietrwałych rejestrów. (Zobacz poniższe ograniczenia, jeśli jest używana flaga *C* ).|
|1|22-31|*Dopasowanie stosu* jest polem 10-bitowym wskazującym liczbę bajtów stosu przydzielonych do tej funkcji podzieloną przez 4. Jednak tylko wartości między 0x000-0x3F3 może być zakodowana bezpośrednio. Funkcje, które przydzielą więcej niż 4044 bajtów stosu, muszą używać pełnego rekordu. xdata. Jeśli pole *dopasowuje stos* ma wartość 0x3F4 lub większe, to niska 4 bity mają specjalne znaczenie:<br /><br />-Bity 0-1 wskazuje liczbę słów dopasowania stosu (1-4) minus 1.<br />-Bit 2 jest ustawiony na 1, jeśli prologu połączone to dopasowanie do operacji wypychania.<br />-Bit 3 jest ustawiony na 1, jeśli epilogu połączone to dostosowanie do swojej operacji pop.|

Ze względu na ewentualne nadmiarowość w powyższych kodowaniu obowiązują następujące ograniczenia:

- Jeśli flaga *C* jest ustawiona na 1:

   - Flaga *L* musi również mieć ustawioną wartość 1, ponieważ łańcuch ramek wymaga zarówno R11, jak i LR.

   - R11 nie mogą być uwzględnione w zestawie rejestrów opisanym przez *reg*. Oznacza to, że jeśli R4-R11 są wypychane, *reg* powinien opisywać tylko R4-R10, ponieważ flaga *C* oznacza R11.

- Jeśli pole *RET* ma wartość 0, flaga *L* musi być ustawiona na 1.

Naruszenie tych ograniczeń powoduje nieobsługiwaną sekwencję.

Na potrzeby dyskusji poniżej dwa pseudo flagi są wyprowadzane ze *stosu*:

- *PF* lub "prologu składania" wskazuje, że *stos* jest ustawiony na 0x3F4 lub większy, a ustawiono bit 2.

- *EF* lub "składanie epilogu" wskazuje, że *stos* jest ustawiony na 0x3F4 lub większy, a ustawiono bit 3.

Prologues dla funkcji kanonicznych mogą zawierać do 5 instrukcji (należy zauważyć, że 3A i 3B wykluczają się wzajemnie):

|Instrukcja|Przyjęto, że kod operacji jest obecny, jeśli:|Rozmiar|Kod operacji|Kody operacji unwind|
|-----------------|-----------------------------------|----------|------------|------------------|
|1|*H*==1|16|`push {r0-r3}`|04|
|2|*C*= = 1 lub *L*= = 1 lub *R*= = 0 lub PF = = 1|16/32|`push {registers}`|80-BF/D0-DF/EC-ED|
|art|*C*= = 1 i (*L*= = 0 i *R*= = 1 i PF = = 0)|16|`mov r11,sp`|C0-CF/FB|
|3b|*C*= = 1 i (*L*= = 1 lub *R*= = 0 lub PF = = 1)|32|`add r11,sp,#xx`|FC|
|4|*R*= = 1 i *reg* ! = 7|32|`vpush {d8-dE}`|E0 — E7|
|5|*Dopasowanie stosu* ! = 0 i PF = = 0|16/32|`sub sp,sp,#xx`|00-7F/E8-EB|

Instrukcja 1 jest zawsze obecna, jeśli bit *H* jest ustawiony na 1.

Aby skonfigurować łańcuch ramek, instrukcja 3A lub 3B jest obecna, jeśli ustawiono bit *C* . Jest to 16-bitowa `mov`, jeśli żadne rejestry inne niż R11 i LR są wypychane; w przeciwnym razie jest to 32-bitowa `add`.

Jeśli określono nieskładane dopasowanie, instrukcja 5 jest jawnym dopasowaniem stosu.

Instrukcje 2 i 4 są ustawiane na podstawie tego, czy jest wymagana wypychanie. Ta tabela zawiera podsumowanie, które rejestry są zapisywane w oparciu o pola *C*, *L*, *R*i *PF* . We wszystkich przypadkach *N* jest równa *reg* + 4, *E* jest równe *reg* + 8, a *S* jest równa (~*dopasowuje stos*) & 3.

|C|L|R|PF|Wypychanie rejestrów liczb całkowitych|Wypchnięcie rejestry Visual FoxPro|
|-------|-------|-------|--------|------------------------------|--------------------------|
|0|0|0|0|R4-r*N*|brak|
|0|0|0|1|r*S*-r*N*|brak|
|0|0|1|0|brak|D8-d*E*|
|0|0|1|1|r*S*-R3|D8-d*E*|
|0|1|0|0|R4-r*N*, LR|brak|
|0|1|0|1|r*S*-r*N*, LR|brak|
|0|1|1|0|LR|D8-d*E*|
|0|1|1|1|r*S*-R3, LR|D8-d*E*|
|1|0|0|0|R4-r*N*, R11|brak|
|1|0|0|1|r*S*-r*N*, R11|brak|
|1|0|1|0|r11|D8-d*E*|
|1|0|1|1|r*S*-R3, R11|D8-d*E*|
|1|1|0|0|R4-r*N*, R11, LR|brak|
|1|1|0|1|r*S*-r*N*, R11, LR|brak|
|1|1|1|0|R11, LR|D8-d*E*|
|1|1|1|1|r*S*-R3, R11, LR|D8-d*E*|

Epilogues dla funkcji kanonicznych są zgodne z podobnym formularzem, ale w odwrocie i z kilkoma dodatkowymi opcjami. Epilogu może być maksymalnie 5 instrukcji, a jego forma jest ściśle podyktowana formą prologu.

|Instrukcja|Przyjęto, że kod operacji jest obecny, jeśli:|Rozmiar|Kod operacji|
|-----------------|-----------------------------------|----------|------------|
|6|*Dopasowanie stosu*! = 0 i *Dr*= = 0|16/32|`add   sp,sp,#xx`|
|7|*R*= = 1 i *reg*! = 7|32|`vpop  {d8-dE}`|
|8|*C*= = 1 lub (*L*= = 1 i *H*= = 0) lub *R*= = 0 lub *Dr*= = 1|16/32|`pop   {registers}`|
|9a|*H*= = 1 i *L*= = 0|16|`add   sp,sp,#0x10`|
|9b|*H*= = 1 i *L*= = 1|32|`ldr   pc,[sp],#0x14`|
|10a|*RET*= = 1|16|`bx    reg`|
|10B|*RET*= = 2|32|`b     address`|

Instrukcja 6 to jawne dopasowanie stosu w przypadku określenia nieskładanej korekty. Ze względu na to, że *PF* jest niezależny od *EF*, istnieje możliwość, że instrukcja 5 jest obecna bez instrukcji 6 lub na odwrót.

Instrukcje 7 i 8 używają tej samej logiki co prologu, aby określić, które rejestry są przywracane ze stosu, ale z tymi dwoma zmianami: pierwszy, *EF* jest używany zamiast *PF*; Po drugie, jeśli *RET* = 0, LR jest zastępowany komputerem na liście rejestrów, a epilogu kończą się natychmiast.

Jeśli jest ustawiona wartość *H* , jest obecna instrukcja "9a" lub "9B". Instrukcja 9a jest używana, gdy *L* ma wartość 0, aby wskazać, że LR nie znajduje się na stosie. W takim przypadku stos jest dostosowywany ręcznie, a *RET* musi mieć wartość 1 lub 2, aby określić jawny zwrot. Instrukcja 9b jest używana, gdy *L* to 1, aby wskazać wczesne zakończenie do epilogu i zwrócić i dostosować stos w tym samym czasie.

Jeśli epilogu jeszcze nie zakończył się, należy wykonać instrukcje 10A lub 10b, aby wskazać 16-bitową lub 32-bitową gałąź na podstawie wartości *RET*.

### <a name="xdata-records"></a>Rekordy. xdata

Gdy spakowany format unwindy jest niewystarczający do opisania odwinięcia funkcji, należy utworzyć rekord o zmiennej długości. xdata. Adres tego rekordu jest przechowywany w drugim słowie rekordu. pdata. Format. xdata to spakowany zestaw słów o zmiennej długości, który ma cztery sekcje:

1. Nagłówek 1 lub 2-Word, który opisuje ogólny rozmiar struktury. xdata i udostępnia kluczowe dane funkcji. Drugi wyraz jest obecny tylko wtedy, gdy *Liczba epilogu* i *słowa kodu* są ustawione na 0. Pola są rozbite w tej tabeli:

   |Word|Bity|Cel|
   |----------|----------|-------------|
   |0|0-17|*Długość funkcji* to pole 18-bitowe, które wskazuje łączną długość funkcji w bajtach podzieloną przez 2. Jeśli funkcja jest większa niż 512 KB, do opisania funkcji należy użyć wielu rekordów. pdata i. xdata. Aby uzyskać szczegółowe informacje, zobacz sekcję duże funkcje w tym dokumencie.|
   |0|18-19|*Verse* to pole 2-bitowe opisujące wersję pozostałej XData. Tylko wersja 0 jest obecnie zdefiniowana; wartości 1-3 są zastrzeżone.|
   |0|20|*X* to pole 1-bitowe, które wskazuje obecność (1) lub nieobecność (0) danych wyjątku.|
   |0|21|*E* to pole 1-bitowe, które wskazuje, że informacje opisujące pojedynczy epilogu są pakowane do nagłówka (1), a nie wymagają dodatkowych słów Scope w dalszej części (0).|
   |0|22|*F* to pole 1-bitowe, które wskazuje, że ten rekord opisuje fragment funkcji (1) lub pełną funkcję (0). Fragment oznacza, że nie istnieje prologu i że wszystkie prologu przetwarzania powinny być ignorowane.|
   |0|23-27|*Epilogu Count* to pole 5-bitowe, które ma dwa średnie, w zależności od stanu bitu *E* :<br /><br /> -Jeśli *E* jest 0, to pole jest liczbą całkowitej liczby zakresów wyjątków opisanych w sekcji 3. Jeśli w funkcji istnieje więcej niż 31 zakresów, to pole i pole *kod słowa* muszą mieć wartość 0, aby wskazać, że wymagane jest słowo rozszerzenia.<br />-Jeśli *E* to 1, to pole określa indeks pierwszego kodu unwind, który opisuje tylko epilogu.|
   |0|28-31|*Słowa kodu* to pole 4-bitowe, które określa liczbę 32-bitowych słów wymaganych do zawierania wszystkich kodów operacji unwind w sekcji 4. Jeśli więcej niż 15 słów jest wymaganych przez więcej niż 63 bajtów kodu wywinięcia, to pole i pole *Count epilogu* muszą mieć ustawioną wartość 0, aby wskazać, że wymagane jest słowo rozszerzenia.|
   |1|0-15|*Extended epilogu Count* to pole 16-bitowe, które zapewnia więcej miejsca do kodowania nietypowo dużej liczby epilogues. Słowo rozszerzenia, które zawiera to pole, jest obecne tylko wtedy, gdy pola *Liczba epilogu* i *słowa kodu* w pierwszym wyrazie nagłówka są ustawione na 0.|
   |1|16-23|*Rozszerzone słowa kodu* to pole 8-bitowe, które zapewnia więcej miejsca do kodowania nietypowo dużej liczby słów kodu unwind. Słowo rozszerzenia, które zawiera to pole, jest obecne tylko wtedy, gdy pola *Liczba epilogu* i *słowa kodu* w pierwszym wyrazie nagłówka są ustawione na 0.|
   |1|24-31|Zarezerwowany|

1. Po danych wyjątku (Jeśli bit *E* w nagłówku został ustawiony na 0) jest listą informacji na temat zakresów epilogu, które są pakowane jeden do wyrazu i przechowywane w kolejności rosnącego przesunięcia początkowego. Każdy zakres zawiera następujące pola:

   |Bity|Cel|
   |----------|-------------|
   |0-17|*Epilogu rozpoczęcia przesunięcia* to pole 18-bitowe, które opisuje przesunięcie epilogu w bajtach podzielone przez 2, względem początku funkcji.|
   |18-19|*Res* to pole 2-bitowe zarezerwowane do użytku w przyszłości. Wartość musi być równa 0.|
   |20-23|*Warunek* to pole 4-bitowe, które zapewnia warunek, pod którym jest wykonywane epilogu. W przypadku epilogues bezwarunkowego powinien być ustawiony na wartość 0xE, co oznacza, że wartość "always". (Epilogu muszą być całkowicie warunkowe lub całkowicie bezwarunkowe, a w trybie kciuka 2 epilogu rozpoczyna się od pierwszej instrukcji po tym, jak kod operacji IT).|
   |24-31|*Indeks początkowy epilogu* to pole 8-bitowe wskazujące indeks bajtów pierwszego kodu unwind, który opisuje ten epilogu.|

1. Po liście zakresów epilogu jest tablicą bajtów zawierającą kody wyłączania, które opisano szczegółowo w sekcji kody operacji unwind w tym artykule. Ta tablica jest dopełniana na końcu do najbliższej pełnej granicy słowa. Bajty są przechowywane w kolejności little-endian, dzięki czemu można je bezpośrednio pobrać w trybie little-endian.

1. Jeśli pole *X* w nagłówku ma wartość 1, następuje informacje o programie obsługi wyjątków. Składa się z jednego adresu *RVA procedury obsługi wyjątków* , który zawiera adres programu obsługi wyjątków, po którym następuje ilość danych (zmienna-długość) wymagana przez program obsługi wyjątków.

Rekord. xdata został zaprojektowany tak, aby można było pobrać pierwsze 8 bajtów i obliczyć pełny rozmiar rekordu, bez uwzględniania długości następujących danych wyjątku o zmiennej wielkości. Ten fragment kodu oblicza rozmiar rekordu:

```cpp
ULONG ComputeXdataSize(PULONG *Xdata)
{
    ULONG EpilogueScopes;
    ULONG Size;
    ULONG UnwindWords;

    if ((Xdata[0] >> 23) != 0) {
        Size = 4;
        EpilogueScopes = (Xdata[0] >> 23) & 0x1f;
        UnwindWords = (Xdata[0] >> 28) & 0x0f;
    } else {
        Size = 8;
        EpilogueScopes = Xdata[1] & 0xffff;
        UnwindWords = (Xdata[1] >> 16) & 0xff;
    }

    if (!(Xdata[0] & (1 << 21))) {
        Size += 4 * EpilogueScopes;
    }
    Size += 4 * UnwindWords;
    if (Xdata[0] & (1 << 20)) {
        Size += 4;
    }
    return Size;
}
```

Chociaż prologu i każdy epilogu ma indeks w kodach unwind, tabela jest udostępniana między nimi. Niektóre z tych samych kodów operacji unwind nie są nietypowe. Zalecamy, aby autorzy kompilatora optymalizować w tym przypadku, ponieważ największy indeks, który można określić, to 255, i ogranicza łączną liczbę kodów operacji unwind dla określonej funkcji.

### <a name="unwind-codes"></a>Kody operacji unwind

Tablica kodów operacji unwind jest pulą sekwencji instrukcji, które opisują dokładnie sposób cofania efektów prologu, w kolejności, w której operacje muszą być cofnięte. Kody operacji unwind są zestawem miniinstalacji, zakodowanym jako ciąg bajtów. Po zakończeniu wykonywania, adres zwrotny do wywołania funkcji znajduje się w rejestrze LR i wszystkie nietrwałe rejestry są przywracane do ich wartości w momencie wywołania funkcji.

Jeśli pewne wyjątki były gwarantowane tylko w obrębie treści funkcji i nigdy w prologu lub epilogu, tylko jedna sekwencja operacji unwind będzie potrzebna. Jednak model unwindy dla systemu Windows wymaga możliwości odwinięcia od częściowo wykonanego prologu lub epilogu. Aby spełnić to wymaganie, kody unwind zostały starannie zaprojektowane jako jednojednoznaczne mapowanie jeden-do-jednego do każdego odpowiedniego kodu operacji w prologu i epilogu. Ma to kilka implikacji:

- Istnieje możliwość obliczenia długości prologu i epilogu przez obliczenie liczby kodów unwind. Jest to możliwe nawet z instrukcją przewijania o zmiennej długości 2, ponieważ istnieją oddzielne mapowania dla 16-bitowych i 32-bitowych kodów operacji.

- Zliczając liczbę instrukcji poza początkiem zakresu epilogu, można pominąć równoważną liczbę kodów unwind i wykonać pozostałe sekwencje w celu ukończenia częściowo wykonanego elementu unwindy, który był wykonywany przez epilogu.

- Zliczając liczbę instrukcji przed końcem prologu, można pominąć równoważną liczbę kodów unwind i wykonać resztę sekwencji, aby cofnąć tylko te części prologu, które zostały ukończone.

W poniższej tabeli przedstawiono mapowanie od kodów unwind do opcode. Najbardziej typowe kody to tylko jeden bajt, a mniej typowe wymagają dwóch, trzech lub nawet czterech bajtów. Każdy kod jest przechowywany od najbardziej znaczącego bajtu do najmniej znaczącego bajtu. Struktura kodu unwind różni się od kodowania opisanego w EABI ARM, ponieważ te kody odwinięcia zostały zaprojektowane tak, aby miało mapowanie jeden do jednego do kodów operacji w prologu i epilogu, aby zezwolić na odwinięcie częściowo wykonanych prologues i epilogues.

|Bajt 1|Bajt 2|Bajt 3|Bajt 4|Opsize|Wyjaśnienie|
|------------|------------|------------|------------|------------|-----------------|
|00 — 7F||||16|`add   sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x7F) \* 4|
|80-Z|00-FF|||32|`pop   {r0-r12, lr}`<br /><br /> gdzie LR jest zdjęte, jeśli kod & 0x2000 i R0-R12 są zdjęte, jeśli odpowiedni bit jest ustawiony w kodzie & 0x1FFF|
|C0-CF||||16|`mov   sp,rX`<br /><br /> gdzie X jest kodem & 0x0F|
|D0 — D7||||16|`pop   {r4-rX,lr}`<br /><br /> gdzie X jest (Code & 0x03) + 4 i LR jest zdjęte, jeśli kod & 0x04|
|D8-DF||||32|`pop   {r4-rX,lr}`<br /><br /> gdzie X jest (Code & 0x03) + 8 i LR jest zdjęte, jeśli kod & 0x04|
|E0 — E7||||32|`vpop  {d8-dX}`<br /><br /> gdzie X jest (Code & 0x07) + 8|
|E8 — EB|00-FF|||32|`addw  sp,sp,#X`<br /><br /> gdzie X jest (Code & 0x03FF) \* 4|
|WE-ED|00-FF|||16|`pop   {r0-r7,lr}`<br /><br /> gdzie LR jest zdjęte, jeśli kod & 0x0100 i R0-R7 są zdjęte, jeśli odpowiedni bit jest ustawiony w kodzie & 0x00FF|
|EE|00 — 0F|||16|specyficzne dla firmy Microsoft|
|EE|10-FF|||16|Dostępne|
|BIEŻĄCO|00 — 0F|||32|`ldr   lr,[sp],#X`<br /><br /> gdzie X jest (Code & 0x000F) \* 4|
|BIEŻĄCO|10-FF|||32|Dostępne|
|F0-F4||||-|Dostępne|
|F5|00-FF|||32|`vpop  {dS-dE}`<br /><br /> gdzie S jest (Code & 0x00F0) > > 4 i E to kod & 0x000F|
|F6|00-FF|||32|`vpop  {dS-dE}`<br /><br /> gdzie S jest ((Code & 0x00F0) > > 4) + 16 i E jest (kod & 0x000F) + 16|
|F7|00-FF|00-FF||16|`add   sp,sp,#X`<br /><br /> gdzie X jest (Code & 0x00FFFF) \* 4|
|F8|00-FF|00-FF|00-FF|16|`add   sp,sp,#X`<br /><br /> gdzie X jest (Code & 0x00FFFFFF) \* 4|
|F9|00-FF|00-FF||32|`add   sp,sp,#X`<br /><br /> gdzie X jest (Code & 0x00FFFF) \* 4|
|FA|00-FF|00-FF|00-FF|32|`add   sp,sp,#X`<br /><br /> gdzie X jest (Code & 0x00FFFFFF) \* 4|
|FB||||16|NOP (16 bitów)|
|FC||||32|NOP (32-bitowa)|
|FD||||16|End + 16-bitowy NOP w epilogu|
|FE||||32|End + 32-bit NOP w epilogu|
|FF||||-|end|

Pokazuje zakres wartości szesnastkowych dla każdego bajtu w *kodzie*kodu unwind, wraz z rozmiarem opcode *Opsize* i odpowiadającą jej pierwotną interpretacją instrukcji. Puste komórki wskazują krótsze kody operacji unwind. W instrukcjach, które mają duże wartości obejmujące wiele bajtów, najbardziej znaczące bity są przechowywane jako pierwsze. Pole *Opsize* pokazuje niejawny rozmiar kodu operacji skojarzony z każdą operacją kciuka 2. Widoczne zduplikowane wpisy w tabeli z różnymi kodowaniem są używane do rozróżniania między różnymi rozmiarami kodu.

Kody operacji unwind są zaprojektowane tak, aby pierwszy bajt kodu nakazuje zarówno całkowity rozmiar w bajtach kodu, jak i rozmiar odpowiedniego kodu w strumieniu instrukcji. Aby obliczyć rozmiar prologu lub epilogu, należy przeszukać kody operacji unwind od początku sekwencji do końca, a następnie użyć tabeli odnośników lub podobnej metody do określenia, jak długo jest odpowiedni opcode.

Kody unwind 0xFD i 0xFE są równoważne zwykłemu kodowi, ale konto dla jednego NOP kodu operacji w przypadku epilogu, 16-bitowy lub 32-bitowy. W przypadku prologues kody 0xFD, 0xFE i 0xFF są dokładnie równoważne. Te konta dla typowych epilogu kończących się `bx lr` lub `b <tailcall-target>`, które nie mają równoważnej instrukcji prologu. Zwiększa to prawdopodobieństwo, że sekwencje odwinięcia mogą być współużytkowane przez prologu i epilogues.

W wielu przypadkach powinno być możliwe użycie tego samego zestawu kodów operacji unwind dla prologu i wszystkie epilogues. Jednak aby obsłużyć niewietrzenie częściowo wykonanych prologues i epilogues, może być konieczne posiadanie wielu sekwencji kodu operacji unwind, które różnią się w zależności od kolejności lub zachowania. To dlatego, że każdy epilogu ma swój własny indeks w tablicy unwind, aby pokazać, gdzie rozpocząć wykonywanie.

### <a name="unwinding-partial-prologues-and-epilogues"></a>Rozciąganie częściowe Prologues i epilogues

Najbardziej typowym przypadkiem odejść jest wyjątek występujący w treści funkcji — od prologu i wszystkie epilogues. W takim przypadku w odniesieniu do kodu w tablicy unwinder są wykonywane kody zaczynające się od indeksu 0 i kontynuuje się do momentu wykrycia końcowego elementu opcode.

Gdy wystąpi wyjątek podczas wykonywania operacji prologu lub epilogu, Ramka stosu jest tylko częściowo skonstruowana, a w przypadku niewiatru należy określić dokładnie to, co zostało zrobione, aby prawidłowo go cofnąć.

Rozważmy na przykład tę prologuę i sekwencję epilogu:

```asm
0000:   push  {r0-r3}         ; 0x04
0002:   push  {r4-r9, lr}     ; 0xdd
0006:   mov   r7, sp          ; 0xc7
...
0140:   mov   sp, r7          ; 0xc7
0142:   pop   {r4-r9, lr}     ; 0xdd
0146:   add   sp, sp, #16     ; 0x04
0148:   bx    lr
```

Obok każdego kodu operacji jest to odpowiedni kod operacji unwindy opisujący tę operację. Sekwencja kodów operacji unwind dla prologu to lustrzany obraz kodów unwind dla epilogu, który nie zlicza końcowej instrukcji. Ten przypadek jest typowy i jest przyczyną, że kody operacji unwind dla prologu są zawsze uznawane za przechowywane w kolejności odwrotnej od kolejności wykonywania prologu. Daje to wspólny zestaw kodów operacji unwind:

```asm
0xc7, 0xdd, 0x04, 0xfd
```

Kod 0xFD jest specjalnym kodem dla końca sekwencji, co oznacza, że epilogu jest 1 16-bitowe instrukcje dłuższe niż prologu. Dzięki temu można zwiększyć udostępnianie kodów operacji unwind.

W przykładzie, jeśli wystąpi wyjątek podczas wykonywania treści funkcji między prologu i epilogu, rozwinięcia rozpoczyna się od przypadku epilogu, przy przesunięciu 0 w kodzie epilogu. Odnosi się to do przesunięcia 0x140 w przykładzie. Unwiatrer wykonuje pełną sekwencję operacji unwind, ponieważ nie zostało wykonane żadne oczyszczanie. Jeśli zamiast tego wyjątek występuje po wykonaniu jednej instrukcji po rozpoczęciu kodu epilogu, program unwiatrer może pomyślnie przełączyć się, pomijając pierwszy kod operacji unwind. W przypadku mapowania jeden-do-jednego między opcode i kody odwinięcia, jeśli zostanie odsunięty od instrukcji *n* w epilogu, element unwiatrer powinien pominąć pierwsze *n* kodów unwind.

Podobna logika działa w odniesieniu do prologu. W przypadku odwinięcia od przesunięcia 0 w prologu nic nie trzeba wykonywać. W przypadku rozwinięcia z jednej instrukcji w programie sekwencja operacji unwind powinna rozpoczynać jeden kod operacji unwindy od końca, ponieważ kody prologu unwind są przechowywane w kolejności odwrotnej. W ogólnym przypadku, jeśli odwinięcie od instrukcji *n* w prologu, należy rozpocząć wykonywanie od *n* kodów unwind na końcu listy kodów.

Kody unwind prologu i epilogu nie zawsze pasują do siebie. W takim przypadku tablica kodu unwind może zawierać kilka sekwencji kodów. Aby określić przesunięcie do rozpoczęcia kodów przetwarzania, Użyj tej logiki:

1. W przypadku odwinięcia od treści funkcji, Rozpocznij wykonywanie kodów unwind na indeksie 0 i Kontynuuj do momentu osiągnięcia końcowego kodu operacji.

2. W przypadku rozwinięcia z epilogu należy użyć początkowego indeksu epilogu dostarczonego przez zakres epilogu. Oblicz liczbę bajtów odebranych przez komputer z początku epilogu. Pomiń przechodzenie do kolejnych kodów unwind, dopóki nie zostaną uwzględnione wszystkie już wykonywane instrukcje. Wykonaj sekwencję unwind, rozpoczynając od tego momentu.

3. W przypadku odwinięcia z prologu, Zacznij od indeksu 0 w kodach unwind. Oblicz długość kodu prologu z sekwencji, a następnie Oblicz, ile bajtów znajduje się na końcu prologu. Pomiń przechodzenie do kolejnych kodów unwind, dopóki nie zostaną uwzględnione wszystkie niewykonane instrukcje. Wykonaj sekwencję unwind, rozpoczynając od tego momentu.

Kody operacji unwind dla prologu muszą zawsze być pierwszym w tablicy. Są one również kodami używanymi do rozwinięcia w ogólnym przypadku odwracania od wewnątrz treści. Wszystkie sekwencje kodu specyficzne dla epilogu powinny być stosowane bezpośrednio po sekwencji kodu prologu.

### <a name="function-fragments"></a>Fragmenty funkcji

Aby zoptymalizować kod, warto podzielić funkcję na części zamienne. Gdy to zrobisz, każdy fragment funkcji wymaga własnego rekordu. pdata — i prawdopodobnie. xdata-Record.

Przy założeniu, że funkcja prologu jest na początku funkcji i nie można jej podzielić, istnieją cztery przypadki fragmentacji funkcji:

- Tylko prologu; wszystkie epilogues w innych fragmentach.

- Prologu i co najmniej jeden epilogues; dodatkowe epilogues w innych fragmentach.

- Nie prologu ani epilogues; prologu i co najmniej jeden epilogues w innych fragmentach.

- Tylko epilogues; prologu i ewentualne dodatkowe epilogues w innych fragmentach.

W pierwszym przypadku należy opisać tylko prologu. Można to zrobić w formularzu Compact. pdata, opisując prologu normalnie i określając wartość *RET* równą 3, aby wskazać, że nie epilogu. W pełnym formularzu. xdata można to zrobić, dostarczając kody operacji unwind prologu na indeksie 0 w zwykły sposób i określając liczbę epilogu równą 0.

Drugi przypadek jest podobny do zwykłej funkcji. Jeśli istnieje tylko jeden epilogu fragmentu i znajduje się na końcu fragmentu, można użyć rekordu Compact. pdata. W przeciwnym razie należy użyć pełnego rekordu. xdata. Należy pamiętać, że przesunięcia określone dla uruchomienia epilogu są względne względem początku fragmentu, a nie od początkowego początku funkcji.

Trzecia i czwarta przypadków są wariantami pierwszego i drugiego przypadku, z wyjątkiem tych, które nie zawierają prologu. W takich sytuacjach zakłada się, że występuje kod przed rozpoczęciem epilogu i jest on traktowany jako część treści funkcji, która zwykle jest odjmowana przez cofnięcie skutków działania prologu. Te przypadki muszą zostać zakodowane za pomocą pseudo prologu, który opisuje sposób odwinięcia z treści, ale jest traktowany jak 0-długość podczas ustalania, czy należy wykonać częściowe odwinięcie na początku fragmentu. Alternatywnie ten pseudo prologu można opisać przy użyciu tych samych kodów operacji unwind jako epilogu, ponieważ zakładają one równoważne operacje.

W trzecim i czwartym przypadkach obecność pseudo prologu jest określana przez ustawienie pola *flag* w rekordzie Compact. pdata na 2 lub przez ustawienie flagi *F* w nagłówku. xdata na 1. W obu przypadkach sprawdzanie częściowego rozwinięcia prologu jest ignorowane, a wszystkie nieepilogue są uznawane za zapełnione.

#### <a name="large-functions"></a>Duże funkcje

Fragmenty mogą służyć do opisywania funkcji większych niż limit 512 KB narzuconych przez pola bitowe w nagłówku. xdata. Aby opisać bardzo dużą funkcję, po prostu Podziel ją na fragmenty mniejsze niż 512 KB. Każdy fragment powinien zostać dostosowany, aby nie dzielił epilogu na wiele elementów.

Tylko pierwszy fragment funkcji zawiera element prologu; wszystkie inne fragmenty są oznaczane jako niemające prologu. W zależności od liczby epilogues każdy fragment może zawierać zero lub więcej epilogues. Należy pamiętać, że każdy zakres epilogu w fragmencie określa jego Przesunięcie początkowe względem początku fragmentu, a nie na początku funkcji.

Jeśli fragment nie ma prologu i nie epilogu, nadal wymaga własnego. pdata — i prawdopodobnie. xdata — rekord, aby opisać sposób odwinięcia z wewnątrz treści funkcji.

#### <a name="shrink-wrapping"></a>Zmniejsz — Zawijanie

Bardziej skomplikowany specjalny przypadek fragmentów funkcji jest *zawijania*, a technika odwołująca się do rejestru jest zapisywana od początku funkcji do późniejszej funkcji, aby zoptymalizować w przypadku prostych przypadków, które nie wymagają zapisywania. Ten element można opisać jako zewnętrzny region, który przydziela miejsce na stosie, ale zapisuje minimalny zestaw rejestrów i region wewnętrzny, który zapisuje i przywraca dodatkowe rejestry.

```asm
ShrinkWrappedFunction
    push   {r4, lr}          ; A: save minimal non-volatiles
    sub    sp, sp, #0x100    ; A: allocate all stack space up front
    ...                      ; A:
    add    r0, sp, #0xE4     ; A: prepare to do the inner save
    stm    r0, {r5-r11}      ; A: save remaining non-volatiles
    ...                      ; B:
    add    r0, sp, #0xE4     ; B: prepare to do the inner restore
    ldm    r0, {r5-r11}      ; B: restore remaining non-volatiles
    ...                      ; C:
    pop    {r4, pc}          ; C:
```

Funkcje z otoką są zwykle oczekiwane w celu wstępnego przydzielenia miejsca na zarejestrowanie dodatkowych zapisów w regularnym prologu, a następnie przeprowadzenie rejestracji przy użyciu `str` lub `stm` zamiast `push`. Dzięki temu wszystkie operacje na wskaźniku stosu są zachowywane w oryginalnym prologu funkcji.

Przykładowa funkcja zmniejszania z otoką musi być podzielona na trzy regiony, które są oznaczone jako, B i C w komentarzach. Pierwszy region obejmuje początek funkcji przez koniec dodatkowych, nietrwałych zapisywanych. Aby opisać ten fragment jako prologu i nie epilogues, należy utworzyć rekord. pdata lub. xdata.

Środkowy region B pobiera własny rekord. pdata lub. xdata, który opisuje fragment, który nie ma prologu i nie epilogu. Jednak kody operacji unwind dla tego regionu muszą być nadal obecne, ponieważ są uważane za treść funkcji. Kody muszą opisywać prologu złożony, który reprezentuje zarówno oryginalne rejestry zapisane w regionie-A prologu, jak i dodatkowe rejestry zapisane przed wprowadzeniem regionu B, tak jakby były wytwarzane przez jedną sekwencję operacji.

Nie można traktować rejestru dla regionu B jako "prologu wewnętrzny", ponieważ złożone prologu opisane dla regionu B muszą opisywać zarówno region-A prologu, jak i dodatkowe zapisane rejestry. Jeśli fragment B został opisany jako prologu, kody operacji unwind również spowodują, że rozmiar tego prologu i nie ma sposobu opisywania złożonego prologu w sposób, który mapuje jeden do jednego z opcode, które zapisują tylko dodatkowe rejestry.

Dodatkowa rejestracja zapisywanych elementów musi być uważana za część regionu A, ponieważ do momentu zakończenia nie zostanie ona zapisana, a złożone prologu nie opisują dokładnie stanu stosu.

Ostatni region C pobiera własny rekord. pdata lub. xdata, opisujący fragment, który nie ma prologu, ale ma epilogu.

Alternatywne podejście może również działać, jeśli manipulowanie stosem wykonane przed wprowadzeniem regionu B można zmniejszyć do jednej instrukcji:

```asm
ShrinkWrappedFunction
    push   {r4, lr}          ; A: save minimal non-volatile registers
    sub    sp, sp, #0xE0     ; A: allocate minimal stack space up front
    ...                      ; A:
    push   {r4-r9}           ; A: save remaining non-volatiles
    ...                      ; B:
    pop    {r4-r9}           ; B: restore remaining non-volatiles
    ...                      ; C:
    pop    {r4, pc}          ; C: restore non-volatile registers
```

W tym kluczu jest to, że na każdej granicy instrukcji stos jest w pełni spójny z kodami operacji unwind dla regionu. Jeśli element unwind występuje przed rozpoczęciem wewnętrznego wypychania w tym przykładzie, jest uznawany za część regionu A, a tylko region prologu jest rozwinięcia. Jeśli operacja unwind występuje po wewnętrznym wypychaniu, jest uważana za część regionu B, która nie ma prologu, ale zawiera kody operacji unwind, które opisują zarówno wewnętrzne wypychanie, jak i oryginalne prologu z regionu A. Podobna logika dla wewnętrznego punktu obecności.

### <a name="encoding-optimizations"></a>Optymalizacje kodowania

Ze względu na rozbudowanie kodów unwind i możliwość korzystania z zwartej i rozwiniętej postaci danych, istnieje wiele możliwości zoptymalizowania kodowania w celu dodatkowego zmniejszenia ilości miejsca. Dzięki agresywnemu korzystaniu z tych technik obciążenie netto opisujące funkcje i fragmenty za pomocą kodów unwind może być dość minimalne.

Najważniejszym optymalizacjam jest staranne, aby nie mylić granic prologu/epilogu dla celów odwinięcia z logicznymi granicami prologu/epilogu z perspektywy kompilatora. Granice odwinięcia można zmniejszyć i zwiększyć wydajność. Na przykład prologu może zawierać kod po zakończeniu konfiguracji stosu, aby przeprowadzić dodatkowe sprawdzenia weryfikacyjne. Jednak po zakończeniu całego procesu manipulowania stosem nie ma potrzeby kodowania dalszych operacji i wszystkie elementy poza tym, które mogą zostać usunięte z prologu.

Ta sama reguła ma zastosowanie do długości funkcji. Jeśli istnieją dane — na przykład Pula literałów, która następuje po elemencie epilogu w funkcji, nie powinna być uwzględniana jako część długości funkcji. Zmniejszając funkcję do tylko kodu, który jest częścią funkcji, szanse są znacznie większe, że epilogu będzie na bardzo kompletny i zwarty. można użyć rekordu pdata.

W prologu, gdy wskaźnik stosu jest zapisywany w innym rejestrze, zazwyczaj nie trzeba rejestrować żadnych dalszych kodów operacji. W celu odwinięcia funkcji należy najpierw wykonać odzyskiwanie SP z zapisanego rejestru, a więc dalsze operacje nie mają wpływu na operację unwind.

Epilogues pojedynczej instrukcji nie muszą być w ogóle kodowane jako zakresy lub jako kody operacji unwind. Jeśli rozwinięcie ma miejsce przed wykonaniem tej instrukcji, można założyć, że należy ona do treści funkcji i wystarczy wykonać prologu kody operacji unwind. Jeśli po wykonaniu pojedynczej instrukcji rozwinięcia będzie odbywać się, jego definicja odbywa się w innym regionie.

Wiele instrukcji epilogues nie musi kodować pierwszej instrukcji epilogu, z tego samego powodu, co w poprzednim punkcie: Jeśli element unwind jest wykonywany przed wykonaniem tej instrukcji, wystarczający jest pełny element unwind prologu. Jeśli po wykonaniu tej instrukcji rozwinięcia ma miejsce, należy rozważyć tylko kolejne operacje.

Ponowne użycie kodu unwind należy agresywnie. Indeks określony przez każdy zakres epilogu wskazuje dowolny punkt początkowy w tablicy kodów unwind. Nie musi wskazywać początku poprzedniej sekwencji; może wskazywać na środku. Najlepszym rozwiązaniem jest wygenerowanie odpowiedniej sekwencji kodu, a następnie przeskanowanie pod kątem dokładnego dopasowania bajtów w już zakodowanej puli sekwencji i użycie dowolnego najlepszego dopasowania jako punktu wyjścia do ponownego użycia.

Jeśli po epilogues pojedynczej instrukcji nie ma żadnych pozostałych epilogues, rozważ użycie typu Compact. pdata; stanie się znacznie bardziej prawdopodobnie w przypadku braku epilogu.

## <a name="examples"></a>Przykłady

W tych przykładach baza obrazu ma 0x00400000.

### <a name="example-1-leaf-function-no-locals"></a>Przykład 1: funkcja liścia, brak elementów lokalnych

```asm
Prologue:
  004535F8: B430      push        {r4-r5}
Epilogue:
  00453656: BC30      pop         {r4-r5}
  00453658: 4770      bx          lr
```

. pdata (stałe, 2 słowa):

- Słowo 0

   - *Początkowy adres RVA funkcji* = 0x000535F8 (= 0x004535F8-0x00400000)

- Słowo 1

   - *Flaga* = 1, wskazującą kanoniczne formaty prologu i epilogu

   - *Długość funkcji* = 0x31 (= 0x62/2)

   - *RET* = 1, wskazujący, że jest zwracana wartość 16-bitowa.

   - *H* = 0, wskazujący, że parametry nie zostały naznajdowały się w domu

   - *R*= 0 i *reg* = 1 wskazujące wypychanie/pop z R4-R5

   - *L* = 0, co oznacza brak LR zapisywania/przywracania

   - *C* = 0, co oznacza brak łańcucha ramek

   - *Dopasowanie stosu* = 0, wskazując brak dopasowania stosu

### <a name="example-2-nested-function-with-local-allocation"></a>Przykład 2: funkcja zagnieżdżona z przydziałem lokalnym

```asm
Prologue:
  004533AC: B5F0      push        {r4-r7, lr}
  004533AE: B083      sub         sp, sp, #0xC
Epilogue:
  00453412: B003      add         sp, sp, #0xC
  00453414: BDF0      pop         {r4-r7, pc}
```

. pdata (stałe, 2 słowa):

- Słowo 0

   - *Początkowy adres RVA funkcji* = 0x000533AC (= 0x004533AC-0x00400000)

- Słowo 1

   - *Flaga* = 1, wskazującą kanoniczne formaty prologu i epilogu

   - *Długość funkcji* = 0x35 (= 0x6A/2)

   - *RET* = 0, co oznacza, że punkt pop {PC} zwraca

   - *H* = 0, wskazujący, że parametry nie zostały naznajdowały się w domu

   - *R*= 0 i *reg* = 3 wskazujące wypychanie/pop z R4-R7

   - *L* = 1 wskazuje, że LR został zapisany/przywrócony

   - *C* = 0, co oznacza brak łańcucha ramek

   - *Dopasowanie stosu* = 3 (= 0x0c/4)

### <a name="example-3-nested-variadic-function"></a>Przykład 3: zagnieżdżona funkcja wariadyczne

```asm
Prologue:
  00453988: B40F      push        {r0-r3}
  0045398A: B570      push        {r4-r6, lr}
Epilogue:
  004539D4: E8BD 4070 pop         {r4-r6}
  004539D8: F85D FB14 ldr         pc, [sp], #0x14
```

. pdata (stałe, 2 słowa):

- Słowo 0

   - *Początkowy adres RVA funkcji* = 0x00053988 (= 0x00453988-0x00400000)

- Słowo 1

   - *Flaga* = 1, wskazującą kanoniczne formaty prologu i epilogu

   - *Długość funkcji* = 0x2A (= 0x54/2)

   - *RET* = 0, co oznacza, że ciąg pop {PC} (w tym przypadku jest to komputer LDR, [Sp], #0x14 Return)

   - *H* = 1, wskazujący na parametry

   - *R*= 0 i *reg* = 2 wskazujące wypychanie/pop z R4-R6

   - *L* = 1 wskazuje, że LR został zapisany/przywrócony

   - *C* = 0, co oznacza brak łańcucha ramek

   - *Dopasowanie stosu* = 0, wskazując brak dopasowania stosu

### <a name="example-4-function-with-multiple-epilogues"></a>Przykład 4: funkcja z wieloma epilogues

```asm
Prologue:
  004592F4: E92D 47F0 stmdb       sp!, {r4-r10, lr}
  004592F8: B086      sub         sp, sp, #0x18
Epilogues:
  00459316: B006      add         sp, sp, #0x18
  00459318: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  0045943E: B006      add         sp, sp, #0x18
  00459440: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  004595D4: B006      add         sp, sp, #0x18
  004595D6: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  00459606: B006      add         sp, sp, #0x18
  00459608: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  00459636: F028 FF0F bl          KeBugCheckEx     ; end of function
```

. pdata (stałe, 2 słowa):

- Słowo 0

   - *Początkowy adres RVA funkcji* = 0x000592F4 (= 0x004592F4-0x00400000)

- Słowo 1

   - *Flaga* = 0, wskazującą, że rekord XData jest obecny (wymagany z powodu wielu epilogues)

   - *adres. xdata* — 0x00400000

. xdata (zmienna, 6 słów):

- Słowo 0

   - *Długość funkcji* = 0x0001A3 (= 0x000346/2)

   - *Verse* = 0, wskazujące pierwszą wersję xdata

   - *X* = 0, bez danych wyjątku

   - *E* = 0, wskazującą listę zakresów epilogu

   - *F* = 0, co oznacza pełny opis funkcji, w tym prologu

   - *Epilogu Count* = 0x04, wskazujący 4 zakresy całkowitej epilogu

   - *Słowa kodu* = 0x01 wskazujące 1 32-bitowe słowo kodów unwind

- Wyrazy 1-4, opisujące 4 zakresy epilogu w 4 miejscach. Każdy zakres ma wspólny zestaw kodów operacji unwind, współużytkowany z prologu, w odsunięciu 0x00 i jest bezwarunkowy, określając warunek 0x0E (zawsze).

- Kody operacji unwind, zaczynając od słowa 5: (współużytkowane przez prologu/epilogu)

   - Kod unwind 0 = 0x06: SP + = (6 < < 2)

   - Kod unwind 1 = 0xDE: pop {R4-R10, LR}

   - Kod unwind 2 = 0xFF: end

### <a name="example-5-function-with-dynamic-stack-and-inner-epilogue"></a>Przykład 5: funkcja ze stosem dynamicznym i wewnętrznym epilogu

```asm
Prologue:
  00485A20: B40F      push        {r0-r3}
  00485A22: E92D 41F0 stmdb       sp!, {r4-r8, lr}
  00485A26: 466E      mov         r6, sp
  00485A28: 0934      lsrs        r4, r6, #4
  00485A2A: 0124      lsls        r4, r4, #4
  00485A2C: 46A5      mov         sp, r4
  00485A2E: F2AD 2D90 subw        sp, sp, #0x290
Epilogue:
  00485BAC: 46B5      mov         sp, r6
  00485BAE: E8BD 41F0 ldm         sp!, {r4-r8, lr}
  00485BB2: B004      add         sp, sp, #0x10
  00485BB4: 4770      bx          lr
  ...
  00485E2A: F7FF BE7D b           #0x485B28    ; end of function
```

. pdata (stałe, 2 słowa):

- Słowo 0

   - *Początkowy adres RVA funkcji* = 0x00085A20 (= 0x00485A20-0x00400000)

- Słowo 1

   - *Flaga* = 0, wskazująca obecność rekordu. xdata (wymagana z powodu wielu epilogues)

   - *adres. xdata* — 0x00400000

. xdata (zmienna, 3 słowa):

- Słowo 0

   - *Długość funkcji* = 0x0001A3 (= 0x000346/2)

   - *Verse* = 0, wskazujące pierwszą wersję xdata

   - *X* = 0, bez danych wyjątku

   - *E* = 0, wskazującą listę zakresów epilogu

   - *F* = 0, co oznacza pełny opis funkcji, w tym prologu

   - *Epilogu Count* = 0x001, wskazujący 1 całkowity zakres epilogu

   - *Słowa kodu* = 0x01 wskazujące 1 32-bitowe słowo kodów unwind

- Word 1: epilogu zakres w przesunięciu 0xC6 (= 0x18C/2), początkowy indeks kodu unwindy w 0x00 i z warunkiem 0x0E (zawsze)

- Kody operacji unwind, zaczynając od słowa 2: (współużytkowane przez prologu/epilogu)

   - Kod unwind 0 = 0xC6: SP = R6

   - Kod unwind 1 = 0xDC: pop {R4-R8, LR}

   - Kod unwind 2 = 0x04: SP + = (4 < < 2)

   - Kod unwind 3 = 0xFD: end, liczy jako 16-bitowe instrukcje dla epilogu

### <a name="example-6-function-with-exception-handler"></a>Przykład 6: funkcja z obsługą wyjątków

```asm
Prologue:
  00488C1C: 0059 A7ED dc.w  0x0059A7ED
  00488C20: 005A 8ED0 dc.w  0x005A8ED0
FunctionStart:
  00488C24: B590      push        {r4, r7, lr}
  00488C26: B085      sub         sp, sp, #0x14
  00488C28: 466F      mov         r7, sp
Epilogue:
  00488C6C: 46BD      mov         sp, r7
  00488C6E: B005      add         sp, sp, #0x14
  00488C70: BD90      pop         {r4, r7, pc}
```

. pdata (stałe, 2 słowa):

- Słowo 0

   - *Początkowy adres RVA funkcji* = 0x00088C24 (= 0x00488C24-0x00400000)

- Słowo 1

   - *Flaga* = 0, wskazująca obecność rekordu. xdata (wymagana z powodu wielu epilogues)

   - *adres. xdata* — 0x00400000

. xdata (zmienna, 5 słów):

- Słowo 0

   - *Długość funkcji* = 0x000027 (= 0x00004E/2)

   - *Verse* = 0, wskazujące pierwszą wersję xdata

   - *X* = 1, wskazującą obecność danych wyjątku

   - *E* = 1, co oznacza pojedynczy epilogu

   - *F* = 0, co oznacza pełny opis funkcji, w tym prologu

   - *Liczba epilogu* = 0x00, wskazująca, że kody operacji unwind epilogu zaczynają się w przesunięciu 0x00

   - *Słowa kodu* = 0x02, wskazujące 2 32-bitowe słowa kodów unwind

- Kody unwind, zaczynając od słowa 1:

   - Kod unwind 0 = 0xC7: SP = R7

   - Kod unwind 1 = 0x05: SP + = (5 < < 2)

   - Kod unwind 2 = 0xED/0x90: pop {R4, R7, LR}

   - Kod unwind 4 = 0xFF: end

- Słowo 3 określa procedurę obsługi wyjątków = 0x0019A7ED (= 0x0059A7ED-0x00400000)

- Wyrazy 4 i poza są danymi wyjątku w wierszu

### <a name="example-7-funclet"></a>Przykład 7: polecenie funclet

```asm
Function:
  00488C72: B500      push        {lr}
  00488C74: B081      sub         sp, sp, #4
  00488C76: 3F20      subs        r7, #0x20
  00488C78: F117 0308 adds        r3, r7, #8
  00488C7C: 1D3A      adds        r2, r7, #4
  00488C7E: 1C39      adds        r1, r7, #0
  00488C80: F7FF FFAC bl          target
  00488C84: B001      add         sp, sp, #4
  00488C86: BD00      pop         {pc}
```

. pdata (stałe, 2 słowa):

- Słowo 0

   - *Początkowy adres RVA funkcji* = 0x00088C72 (= 0x00488C72-0x00400000)

- Słowo 1

   - *Flaga* = 1, wskazującą kanoniczne formaty prologu i epilogu

   - *Długość funkcji* = 0x0B (= 0x16/2)

   - *RET* = 0, co oznacza, że punkt pop {PC} zwraca

   - *H* = 0, wskazujący, że parametry nie zostały naznajdowały się w domu

   - *R*= 0 i *reg* = 7 wskazuje, że nie zapisano/przywrócono rejestrów

   - *L* = 1 wskazuje, że LR został zapisany/przywrócony

   - *C* = 0, co oznacza brak łańcucha ramek

   - *Dopasowanie stosu* = 1, wskazując 1 x 4-bajtowe dopasowanie stosu

## <a name="see-also"></a>Zobacz także

[Przegląd konwencji ABI ARM](overview-of-arm-abi-conventions.md)<br/>
[Typowe problemy przy migracji Visual C++ ARM](common-visual-cpp-arm-migration-issues.md)
