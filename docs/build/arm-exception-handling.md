---
title: Obsługa wyjątków ARM
ms.date: 07/11/2018
ms.assetid: fe0e615f-c033-4ad5-97f4-ff96af45b201
ms.openlocfilehash: 4bdf0c88f0c2fe445f3a8865353ca1259ba586fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323226"
---
# <a name="arm-exception-handling"></a>Obsługa wyjątków ARM

System Windows na arm używa tego samego mechanizmu obsługi wyjątków strukturalnych dla asynchronicznych wyjątków generowanych sprzętowo i wyjątków generowanych przez oprogramowanie synchroniczne. Programy obsługi wyjątków specyficzne dla języka są oparte na ustrukturyzowanej obsługi wyjątków systemu Windows przy użyciu funkcji pomocnika języka. W tym dokumencie opisano obsługę wyjątków w systemie Windows na arm i pomocników języka używane przez kod, który jest generowany przez asemblera ARM firmy Microsoft i kompilatora MSVC.

## <a name="arm-exception-handling"></a>Obsługa wyjątków ARM

System Windows na ARM używa *kodów unwind* do kontrolowania odwijania stosu podczas [obsługi wyjątków strukturalnych](/windows/win32/debug/structured-exception-handling) (SEH). Kody unwind to sekwencja bajtów przechowywanych w sekcji .xdata obrazu wykonywalnego. Opisują one działanie funkcji prologu i epilogu kodu w sposób abstrakcyjny, tak aby skutki prologu funkcji można cofnąć w ramach przygotowań do odwijania do ramki stosu wywołującego.

ARM EABI (wbudowany interfejs binarny aplikacji) określa model odwijania wyjątku, który używa kodów unwind, ale nie jest wystarczający dla odwijania SEH w systemie Windows, który musi obsługiwać asynchroniczne przypadki, w których procesor znajduje się w środku prologu lub epilogu funkcji. System Windows oddziela również formant odwijania do odwijania na poziomie funkcji i odwijania zakresu specyficznego dla języka, który jest ujednolicony w ARM EABI. Z tych powodów system Windows na ARM określa więcej szczegółów dla danych i procedury odwijania.

### <a name="assumptions"></a>Założenia

Obrazy wykonywalne dla systemu Windows w systemie ARM używają formatu Portable Executable (PE). Aby uzyskać więcej informacji, zobacz [Microsoft PE i COFF Specification](https://go.microsoft.com/fwlink/p/?linkid=84140). Informacje dotyczące obsługi wyjątków są przechowywane w sekcjach .pdata i .xdata obrazu.

Mechanizm obsługi wyjątków sprawia, że pewne założenia dotyczące kodu, który następuje ABI dla systemu Windows na ARM:

- Gdy wyjątek występuje w treści funkcji, nie ma znaczenia, czy operacje prologu są cofnięte lub operacje epilogu są wykonywane w sposób do przodu. Oba powinny przynieść identyczne wyniki.

- Prologi i epilogi mają tendencję do lustrzanego odbicia. Może to służyć do zmniejszenia rozmiaru metadanych potrzebnych do opisania odwijania.

- Funkcje wydają się być stosunkowo małe. Kilka optymalizacji polega na tym, aby uzyskać wydajne pakowanie danych.

- Jeśli warunek jest umieszczony na epilogu, stosuje się również do każdej instrukcji w epilogu.

- Jeśli wskaźnik stosu (SP) jest zapisywany w innym rejestrze w prologu, ten rejestr musi pozostać niezmieniony w całej funkcji, tak aby oryginalny SP może zostać odzyskany w dowolnym momencie.

- O ile SP nie zostanie zapisany w innym rejestrze, wszystkie manipulacje muszą odbywać się ściśle w prologu i epilogu.

- Aby odwinąć dowolną ramkę stosu, te operacje są wymagane:

  - Wyreguluj r13 (SP) w odstępach 4-bajtowych.

  - Pop jeden lub więcej rejestrów całkowitych.

  - Pop jeden lub więcej VFP (wirtualny zmiennoprzecinkowego) rejestrów.

  - Skopiuj dowolną wartość rejestru do r13 (SP).

  - Załaduj sp ze stosu przy użyciu małej operacji po dekreacji.

  - Przejaś jedno z kilku dobrze zdefiniowanych typów ramek.

### <a name="pdata-records"></a>Rekordy .pdata

Rekordy .pdata w obrazie w formacie PE są uporządkowaną tablicą elementów o stałej długości, które opisują każdą funkcję manipulowania stosem. Funkcje typu liść, które są funkcjami, które nie wywołują innych funkcji, nie wymagają rekordów .pdata, gdy nie manipulują stosem. (Oznacza to, że nie wymagają żadnego magazynu lokalnego i nie trzeba zapisywać ani przywracać rejestrów nieulotnych.). Rekordy dla tych funkcji można pominąć w sekcji .pdata, aby zaoszczędzić miejsce. Operacja unwind z jednej z tych funkcji można po prostu skopiować adres zwrotny z Łącze rejestru (LR) do licznika programu (PC), aby przejść do wywołującego.

Każdy rekord .pdata dla ARM ma długość 8 bajtów. Ogólny format rekordu umieszcza względny adres wirtualny (RVA) początku funkcji w pierwszym 32-bitowym słowie, a następnie drugie słowo, które zawiera wskaźnik do bloku .xdata o zmiennej długości lub spakowane słowo opisujące sekwencję odwijania funkcji kanonicznych, jak pokazano w tej tabeli:

|Przesunięcie wyrazu|Bity|Przeznaczenie|
|-----------------|----------|-------------|
|0|0-31|*Funkcja Start RVA* jest 32-bitowym RVA uruchomienia funkcji. Jeśli funkcja zawiera kod kciuka, należy ustawić niski bit tego adresu.|
|1|0-1|*Flaga* to pole 2-bitowe, które wskazuje sposób interpretowania pozostałych 30 bitów drugiego wyrazu .pdata. Jeśli *Flag* jest 0, a następnie pozostałe bity tworzą *RVA informacji o wyjątku* (z niskimi dwoma bitami niejawnie 0). Jeśli *Flag* jest niezerowy, pozostałe bity tworzą *strukturę Spakowane dane unwind.*|
|1|2-31|*Informacje o wyjątkach RVA* lub *pakowane dane unwind*.<br /><br /> *Informacje o wyjątku RVA* to adres struktury informacji o wyjątku o zmiennej długości, przechowywany w sekcji .xdata. Te dane muszą być wyrównane 4-bajtowe.<br /><br /> *Packed Unwind Data* to skompresowany opis operacji wymaganych do odwijania z funkcji, przy założeniu, że forma kanoniczna. W takim przypadku nie jest wymagany rekord .xdata.|

### <a name="packed-unwind-data"></a>Spakowane dane unwind

W przypadku funkcji, których prologi i epilogi są zgodne z opisaną poniżej formą kanoniczną, można użyć spakowanych danych unwind. Eliminuje to potrzebę rekordu xdata i znacznie zmniejsza miejsce wymagane do zapewnienia danych unwind. Prologi kanoniczne i epilogi są zaprojektowane w taki sposób, aby spełniać wspólne wymagania prostej funkcji, która nie wymaga obsługi wyjątków i wykonuje swoje operacje konfiguracji i usuwania w standardowej kolejności.

W tej tabeli przedstawiono format rekordu .pdata, który zawiera spakowane dane unwind:

|Przesunięcie wyrazu|Bity|Przeznaczenie|
|-----------------|----------|-------------|
|0|0-31|*Funkcja Start RVA* jest 32-bitowym RVA uruchomienia funkcji. Jeśli funkcja zawiera kod kciuka, należy ustawić niski bit tego adresu.|
|1|0-1|*Flaga* jest polem 2-bitowym, które ma następujące znaczenie:<br /><br />- 00 = spakowane dane unwind nie są używane; pozostałe bity wskazują rekord .xdata.<br />- 01 = spakowane dane unwind.<br />- 10 = spakowane dane unwind, gdzie zakłada się, że funkcja nie ma prologu. Jest to przydatne do opisywania fragmentów funkcji, które są nietknięte wraz z rozpoczęciem funkcji.<br />- 11 = zarezerwowane.|
|1|2-12|*Długość funkcji* jest 11-bitowym polem, które zapewnia długość całej funkcji w bajtach podzielonych przez 2. Jeśli funkcja jest większa niż bajty 4K, zamiast niego należy użyć pełnego rekordu .xdata.|
|1|13-14|*Ret* to pole 2-bitowe, które wskazuje sposób zwracania funkcji:<br /><br />- 00 = powrót przez pop {pc} (w tym przypadku bit flagi *L* musi być ustawiony na 1).<br />- 01 = return przy użyciu gałęzi 16-bitowej.<br />- 10 = powrót przy użyciu gałęzi 32-bitowej.<br />- 11 = brak epilogu w ogóle. Jest to przydatne do opisywania fragmentu funkcji discontiguous, który może zawierać tylko prolog, ale którego epilog jest gdzie indziej.|
|1|15|*H* jest flagą 1-bitową, która wskazuje, czy funkcja "domy" parametru całkowitej rejestruje (r0-r3) przez wypychanie ich na początku funkcji i rozdziela alokacje 16 bajtów stosu przed zwróceniem. (0 = nie rejestruje domu, 1 = domy rejestry.)|
|1|16-18|*Reg* to pole 3-bitowe, które wskazuje indeks ostatniego zapisanego rejestru nieulotnego. Jeśli bit *R* wynosi 0, to zapisywane są tylko rejestry całkowite i zakłada się, że znajdują się w zakresie r4-rN, gdzie N jest równe 4 + *Reg*. Jeśli bit *R* wynosi 1, to zapisywane są tylko rejestry zmiennoprzecinowe i zakłada się, że znajdują się w zakresie d8-dN, gdzie N jest równe 8 + *Reg*. Specjalna kombinacja *R* = 1 i *Reg* = 7 wskazuje, że nie są zapisywane żadne rejestry.|
|1|19|*R* jest flagą 1-bitową, która wskazuje, czy zapisane rejestry nieulotne są rejestrami całkowitymi (0) czy rejestrami zmiennoprzecinkowymi (1). Jeśli *R* jest ustawiona na 1, a pole *Reg* jest ustawione na 7, nie zostały wypchnięte żadne rejestry nieulotne.|
|1|20|*L* jest flagą 1-bitową, która wskazuje, czy funkcja zapisuje/przywraca LR, wraz z innymi rejestrami wskazanymi przez pole *Reg.* (0 = nie zapisuje/przywraca, 1 = zapisuje/przywraca).|
|1|21|*C* jest flagą 1-bitową, która wskazuje, czy funkcja zawiera dodatkowe instrukcje konfigurowania łańcucha ramki dla szybkiego chodzenia stosu (1) czy nie (0). Jeśli ten bit jest ustawiony, r11 jest niejawnie dodawany do listy rejestrowań nieulotnych zapisanych. (Zobacz ograniczenia poniżej, jeśli flaga *C* jest używana.|
|1|22-31|*Stack Adjust* to 10-bitowe pole, które wskazuje liczbę bajtów stosu, które są przydzielone dla tej funkcji, podzielone przez 4. Jednak tylko wartości między 0x000-0x3F3 mogą być bezpośrednio zakodowane. Funkcje, które przydzielają więcej niż 4044 bajtów stosu, muszą używać pełnego rekordu xdata. Jeśli pole *Dopasowywanie stosu* ma wartość 0x3F4 lub większą, niskie 4 bity mają specjalne znaczenie:<br /><br />- Bity 0-1 wskazują liczbę słów regulacji stosu (1-4) minus 1.<br />- Bit 2 jest ustawiony na 1, jeśli prolog połączył tę regulację z operacją wypychania.<br />- Bit 3 jest ustawiony na 1, jeśli epilog połączył tę regulację z operacją pop.|

Ze względu na możliwe nadmiarowości w kodowania powyżej, te ograniczenia mają zastosowanie:

- Jeśli flaga *C* jest ustawiona na 1:

  - Flaga *L* musi być również ustawiona na 1, ponieważ tworzenie łańcucha ramek wymaga zarówno r11, jak i LR.

  - r11 nie może być włączony do zbioru rejestrów opisanych przez *Reg*. Oznacza to, że jeśli r4-r11 są wypychane, *Reg* powinien opisywać tylko r4-r10, ponieważ flaga *C* implikuje r11.

- Jeśli pole *Ret* jest ustawione na 0, flaga *L* musi być ustawiona na 1.

Naruszenie tych ograniczeń powoduje nieobsługiwanie sekwencji.

Na potrzeby poniższej dyskusji dwie pseudokibice pochodzą z *Stack Adjust:*

- *PF* lub "prolog składany" wskazuje, że *stack Adjust* jest 0x3F4 lub większy i bit 2 jest ustawiony.

- *EF* lub "składanie epilogu" wskazuje, że *stack Adjust* jest 0x3F4 lub większy i bit 3 jest ustawiony.

Prologi dla funkcji kanonicznych mogą mieć do 5 instrukcji (zwróć uwagę, że 3a i 3b wzajemnie się wykluczają):

|Instrukcja|Opcode zakłada się obecny, jeśli:|Rozmiar|Opcode|Kody odwijania|
|-----------------|-----------------------------------|----------|------------|------------------|
|1|*H*==1|16|`push {r0-r3}`|04|
|2|*C*==1 lub *L*==1 lub *R*==0 lub PF==1|16/32|`push {registers}`|80-BF/D0-DF/EC-ED|
|3a|*C*==1 i (*L*==0 i *R*==1 i PF==0)|16|`mov r11,sp`|C0-CF/FB|
|3b|*C*==1 i (*L*==1 lub *R*==0 lub PF==1)|32|`add r11,sp,#xx`|Fc|
|4|*R*==1 i *Reg* != 7|32|`vpush {d8-dE}`|E0-E7|
|5|*Regulacja stosu* != 0 i PF==0|16/32|`sub sp,sp,#xx`|00-7F/E8-EB|

Instrukcja 1 jest zawsze obecna, jeśli bit *H* jest ustawiony na 1.

Aby skonfigurować tworzenie łańcucha ramek, instrukcja 3a lub 3b jest obecna, jeśli bit *C* jest ustawiony. Jest to 16-bitowe, `mov` jeśli nie są wypychane żadne rejestry inne niż r11 i LR; w przeciwnym razie jest to `add`32-bitowy .

Jeśli określono niezłogowane dopasowanie, instrukcja 5 jest jawną korektą stosu.

Instrukcje 2 i 4 są ustawione na podstawie tego, czy wymagane jest naciśnięcie. W tej tabeli podsumowano, które rejestry są zapisywane na podstawie pól *C,* *L,* *R*i *PF.* We wszystkich przypadkach *N* jest równa *Reg* + 4, *E* jest równa *Reg* + 8, a *S* jest równa (~*Stack Adjust)*& 3.

|C|L|R|PF|Rejestry całkowite wypchnięte|VFP Rejestry wypchnięte|
|-------|-------|-------|--------|------------------------------|--------------------------|
|0|0|0|0|r4-r*N*|brak|
|0|0|0|1|r*S*-r*N*|brak|
|0|0|1|0|brak|d8-d*E*|
|0|0|1|1|r*S*-r3|d8-d*E*|
|0|1|0|0|r4-r*N*, LR|brak|
|0|1|0|1|r*S*-r*N*, LR|brak|
|0|1|1|0|LR|d8-d*E*|
|0|1|1|1|r*S*-r3, LR|d8-d*E*|
|1|0|0|0|r4-r*N*, r11|brak|
|1|0|0|1|r*S*-r*N*, r11|brak|
|1|0|1|0|r11|d8-d*E*|
|1|0|1|1|r*S*-r3, r11|d8-d*E*|
|1|1|0|0|r4-r*N*, r11, LR|brak|
|1|1|0|1|r*S*-r*N*, r11, LR|brak|
|1|1|1|0|r11, LR|d8-d*E*|
|1|1|1|1|r*S*-r3, r11, LR|d8-d*E*|

Epilogi dla funkcji kanonicznych są podobnej formie, ale w odwrotnej i z pewnymi dodatkowymi opcjami. Epilog może mieć do 5 instrukcji długości, a jego forma jest ściśle podyktowana formą prologu.

|Instrukcja|Opcode zakłada się obecny, jeśli:|Rozmiar|Opcode|
|-----------------|-----------------------------------|----------|------------|
|6|*Regulacja stosu*!=0 i *EF*==0|16/32|`add   sp,sp,#xx`|
|7|*R*==1 i *Reg*!=7|32|`vpop  {d8-dE}`|
|8|*C*==1 lub (*L*==1 i *H*==0) lub *R*==0 lub *EF*==1|16/32|`pop   {registers}`|
|9|*H*==1 i *L*==0|16|`add   sp,sp,#0x10`|
|9b|*H*==1 i *L*==1|32|`ldr   pc,[sp],#0x14`|
|10|*Ret*==1|16|`bx    reg`|
|10b|*Ret*==2|32|`b     address`|

Instrukcja 6 jest jawną korektą stosu, jeśli określono niezłomną regulację. Ponieważ *PF* jest niezależna od *EF,* możliwe jest, aby instrukcja 5 obecny bez instrukcji 6 lub odwrotnie.

Instrukcje 7 i 8 używają tej samej logiki co prolog, aby określić, które rejestry są przywracane ze stosu, ale z tymi dwoma zmianami: po pierwsze, *EF* jest używany zamiast *PF;* po drugie, jeśli *Ret* = 0, a następnie LR jest zastępowany pc na liście rejestru i epilog kończy się natychmiast.

Jeśli *H* jest ustawiony, to instrukcja 9a lub 9b jest obecny. Instrukcja 9a jest używana, gdy *L* jest 0, aby wskazać, że LR nie znajduje się na stosie. W takim przypadku stos jest ręcznie dostosowywany i *Ret* musi być 1 lub 2, aby określić jawny zwrot. Instrukcja 9b jest używana, gdy *L* jest 1, aby wskazać wczesny koniec epilogu i powrócić i dostosować stos w tym samym czasie.

Jeśli epilog jeszcze się nie zakończył, wówczas istnieje instrukcja 10a lub 10b, aby wskazać gałąź 16-bitową lub 32-bitową, na podstawie wartości *Ret*.

### <a name="xdata-records"></a>Rekordy .xdata

Gdy format packed unwind jest niewystarczający do opisania odwijania funkcji, należy utworzyć rekord xdata o zmiennej długości. Adres tego rekordu jest przechowywany w drugim słowie rekordu .pdata. Format .xdata to spakowany zestaw wyrazów o zmiennej długości, który zawiera cztery sekcje:

1. Nagłówek 1 lub 2-wyrazowy, który opisuje ogólny rozmiar struktury .xdata i udostępnia kluczowe dane funkcji. Drugie słowo jest obecny tylko wtedy, gdy *epilogu Count* i *Słowa kodowe* pola są ustawione na 0. Pola są podzielone w tej tabeli:

   |Word|Bity|Przeznaczenie|
   |----------|----------|-------------|
   |0|0–17|*Długość funkcji* to 18-bitowe pole wskazujące całkowitą długość funkcji w bajtach, podzieloną przez 2. Jeśli funkcja jest większa niż 512 KB, do opisania funkcji należy użyć wielu rekordów .pdata i .xdata. Aby uzyskać szczegółowe informacje, zobacz sekcję Duże funkcje w tym dokumencie.|
   |0|18-19|*Vers* to 2-bitowe pole opisujące wersję pozostałego xdata. Tylko wersja 0 jest obecnie zdefiniowana; wartości 1-3 są zastrzeżone.|
   |0|20|*X* to pole 1-bitowe, które wskazuje obecność (1) lub brak (0) danych wyjątku.|
   |0|21|*E* to pole 1-bitowe, które wskazuje, że informacje opisujące pojedynczy epilog są pakowane do nagłówka (1), a nie wymagają dodatkowych słów zakresu później (0).|
   |0|22|*F* jest polem 1-bitowym, które wskazuje, że ten rekord opisuje fragment funkcji (1) lub pełną funkcję (0). Fragment oznacza, że nie ma prologu i że wszystkie przetwarzanie prologu powinny być ignorowane.|
   |0|23-27|*Epilog Count* to 5-bitowe pole, które ma dwa znaczenia, w zależności od stanu bitu *E:*<br /><br /> - Jeśli *E* wynosi 0, to pole jest liczbą całkowitych zakresów wyjątków opisanych w sekcji 3. Jeśli w funkcji istnieje więcej niż 31 zakresów, to to pole i pole *Słowa kodowe* muszą być ustawione na 0, aby wskazać, że wymagane jest słowo rozszerzeniu.<br />- Jeśli *E* jest 1, to pole określa indeks pierwszego kodu unwind, który opisuje tylko epilogu.|
   |0|28-31|*Słowa kodowe* to 4-bitowe pole określające liczbę 32-bitowych wyrazów wymaganych do umieszczenia wszystkich kodów unwind w sekcji 4. Jeśli dla więcej niż 63 bajtów kodu unwind jest wymagana więcej niż 15 wyrazów, to pole i pole *Liczba epilogu* muszą być ustawione na 0, aby wskazać, że wymagane jest słowo rozszerzenia.|
   |1|0-15|*Rozszerzona liczba epilogów* to 16-bitowe pole, które zapewnia więcej miejsca na kodowanie niezwykle dużej liczby epilogów. Słowo rozmnżycie, które zawiera to pole, jest obecne tylko wtedy, gdy pola *Liczba epilogu* i *Słowa kodowe* w pierwszym wierszu nagłówka są ustawione na 0.|
   |1|16-23|*Rozszerzone słowa kodu* to 8-bitowe pole, które zapewnia więcej miejsca na kodowanie niezwykle dużej liczby słów kodowych unwind. Słowo rozmnżycie, które zawiera to pole, jest obecne tylko wtedy, gdy pola *Liczba epilogu* i *Słowa kodowe* w pierwszym wierszu nagłówka są ustawione na 0.|
   |1|24-31|Zarezerwowano|

1. Po danych wyjątku (jeśli bit *E* w nagłówku został ustawiony na 0) jest lista informacji o zakresach epilogu, które są pakowane jeden do wyrazu i przechowywane w kolejności zwiększania początkowego offsetu. Każdy zakres zawiera następujące pola:

   |Bity|Przeznaczenie|
   |----------|-------------|
   |0–17|*Przesunięcie rozpoczęcia epilogu* to 18-bitowe pole opisujące przesunięcie epilogu w bajtach podzielonych przez 2 względem początku funkcji.|
   |18-19|*Res* to 2-bitowe pole zarezerwowane dla przyszłej ekspansji. Jego wartość musi wynosić 0.|
   |20-23|*Warunek* jest 4-bitowym polem, które daje warunek, w którym epilog jest wykonywany. W przypadku bezwarunkowych epilogów należy ustawić na 0xE, co oznacza "zawsze". (Epilog musi być całkowicie warunkowe lub całkowicie bezwarunkowe, a w trybie Thumb-2 epilog rozpoczyna się od pierwszej instrukcji po it opcode.)|
   |24-31|*Epilog Start Index* to 8-bitowe pole, które wskazuje indeks bajtów pierwszego kodu unwind, który opisuje ten epilog.|

1. Po liście zakresów epilogu jest tablica bajtów, które zawierają kody unwind, które są szczegółowo opisane w unwind kody sekcji w tym artykule. Ta tablica jest wypełniana na końcu do najbliższej granicy pełnego wyrazu. Bajty są przechowywane w porządku little-endian, dzięki czemu mogą być pobierane bezpośrednio w trybie little-endian.

1. Jeśli pole *X* w nagłówku jest 1, bajty kodu unwind następuje informacje obsługi wyjątków. Składa się z jednego *RVA obsługi wyjątków,* który zawiera adres obsługi wyjątków, a następnie natychmiast (zmiennej długości) ilość danych wymaganych przez program obsługi wyjątków.

Rekord .xdata jest zaprojektowany w taki sposób, aby można było pobrać pierwsze 8 bajtów i obliczyć pełny rozmiar rekordu, z wyłączeniem długości następujących danych wyjątku o zmiennym rozmiarze. Ten fragment kodu oblicza rozmiar rekordu:

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

Mimo że prolog i każdy epilog ma indeks do kodów unwind, tabela jest dzielona między nimi. Nie jest rzadkością, że wszystkie one mogą współużytkować te same kody unwind. Zaleca się, że moduł zapisujący kompilatora zoptymalizować dla tego przypadku, ponieważ największy indeks, który można określić jest 255 i że ogranicza całkowitą liczbę kodów unwind możliwe dla określonej funkcji.

### <a name="unwind-codes"></a>Kody odwijania

Tablica unwind kody jest pulą sekwencji instrukcji, które opisują dokładnie, jak cofnąć skutki prologu, w kolejności, w jakiej operacje muszą zostać cofnięte. Kody unwind to mini zestaw instrukcji, zakodowany jako ciąg bajtów. Po zakończeniu wykonywania, adres zwrotny do funkcji wywołującej znajduje się w rejestrze LR i wszystkie rejestry nieulotne są przywracane do ich wartości w czasie, gdy funkcja została wywołana.

Jeśli wyjątki były gwarantowane tylko kiedykolwiek wystąpić w treści funkcji i nigdy w prologu lub epilogu, a następnie tylko jedna sekwencja unwind byłoby konieczne. Jednak model odwijania systemu Windows wymaga możliwość odwijania się z wewnątrz częściowo wykonane prologu lub epilogu. Aby spełnić to wymaganie, kody unwind zostały starannie zaprojektowane tak, aby mieć jednoznaczne mapowanie jeden do jednego do każdego odpowiedniego kodu opcode w prologu i epilogu. Ma to kilka implikacji:

- Można obliczyć długość prologu i epilogu, licząc liczbę kodów unwind. Jest to możliwe nawet w przypadku instrukcji Thumb-2 o zmiennej długości, ponieważ istnieją różne mapowania dla 16-bitowych i 32-bitowych kodów opcode.

- Zliczając liczbę instrukcji po rozpoczęciu zakresu epilogu, można pominąć równoważną liczbę kodów unwind i wykonać resztę sekwencji, aby zakończyć częściowo wykonane unwind, który epilogu wykonywał.

- Zliczając liczbę instrukcji przed końcem prologu, można pominąć równoważną liczbę kodów unwind i wykonać resztę sekwencji, aby cofnąć tylko te części prologu, które zakończyły wykonanie.

W poniższej tabeli przedstawiono mapowanie od kodów unwind do opcodes. Najczęstsze kody to tylko jeden bajt, podczas gdy mniej powszechne wymagają dwóch, trzech, a nawet czterech bajtów. Każdy kod jest przechowywany z najbardziej znaczących bajtów do najmniej znaczących bajtów. Struktura kodu unwind różni się od kodowania opisanego w ARM EABI, ponieważ te kody unwind są przeznaczone do mapowania jeden do jednego do kodów opcodes w prologu i epilogu, aby umożliwić odwijanie częściowo wykonanych prologów i epilogów.

|Bajt 1|Bajt 2|Bajt 3|Bajt 4|Rozmiar opsize|Wyjaśnienie|
|------------|------------|------------|------------|------------|-----------------|
|00-7F||||16|`add   sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x7F) \* 4|
|80-BF|00-FF|||32|`pop   {r0-r12, lr}`<br /><br /> gdzie LR jest pojawiał się, jeśli Kod & 0x2000 i r0-r12 są pojawiały się, jeśli odpowiedni bit jest ustawiony w kodzie & 0x1FFF|
|C0-CF||||16|`mov   sp,rX`<br /><br /> gdzie X to Kod & 0x0F|
|D0-D7||||16|`pop   {r4-rX,lr}`<br /><br /> gdzie X jest (Kod & 0x03) + 4 i LR jest wyskoczył, jeśli kod & 0x04|
|D8-DF||||32|`pop   {r4-rX,lr}`<br /><br /> gdzie X jest (Kod & 0x03) + 8 i LR jest wyskoczył, jeśli kod & 0x04|
|E0-E7||||32|`vpop  {d8-dX}`<br /><br /> gdzie X jest (kod & 0x07) + 8|
|E8-EB|00-FF|||32|`addw  sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x03FF) \* 4|
|EC-ED|00-FF|||16|`pop   {r0-r7,lr}`<br /><br /> gdzie LR jest pojawiał się, jeśli Kod & 0x0100 i r0-r7 są pojawiały się, jeśli odpowiedni bit jest ustawiony w kodzie & 0x00FF|
|EE|00-0F|||16|specyficzne dla firmy Microsoft|
|EE|10-FF|||16|Dostępne|
|Ef|00-0F|||32|`ldr   lr,[sp],#X`<br /><br /> gdzie X jest (kod & 0x000F) \* 4|
|Ef|10-FF|||32|Dostępne|
|F0-F4||||-|Dostępne|
|F5|00-FF|||32|`vpop  {dS-dE}`<br /><br /> gdzie S jest (Kod & 0x00F0) >> 4 i E jest kod & 0x000F|
|F6|00-FF|||32|`vpop  {dS-dE}`<br /><br /> gdzie S jest ((Kod & 0x00F0) >> 4) + 16 i E jest (Kod & 0x000F) + 16|
|F7|00-FF|00-FF||16|`add   sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x00FFFF) \* 4|
|F8|00-FF|00-FF|00-FF|16|`add   sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x00FFFFFF) \* 4|
|F9|00-FF|00-FF||32|`add   sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x00FFFF) \* 4|
|Fa|00-FF|00-FF|00-FF|32|`add   sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x00FFFFFF) \* 4|
|Fb||||16|nop (16-bitowy)|
|Fc||||32|nop (32-bitowy)|
|Fd||||16|koniec + 16-bitowy nop w epilogu|
|Fe||||32|koniec + 32-bitowy nop w epilogu|
|Ff||||-|end|

Pokazuje zakres wartości szesnastowych dla każdego bajtu w *kodzie unwind,* wraz z opcode size *Opsize* i odpowiedniej oryginalnej interpretacji instrukcji. Puste komórki wskazują krótsze kody unwind. W instrukcjach, które mają duże wartości obejmujące wiele bajtów, najbardziej znaczące bity są przechowywane jako pierwsze. *Opsize* pole pokazuje niejawny rozmiar opcode skojarzone z każdej operacji Thumb-2. Pozorne zduplikowane wpisy w tabeli z różnymi kodowania są używane do rozróżniania różnych rozmiarów opcode.

Kody unwind są zaprojektowane tak, aby pierwszy bajt kodu informuje zarówno całkowity rozmiar w bajtach kodu, jak i rozmiar odpowiedniego kodu opcode w strumieniu instrukcji. Aby obliczyć rozmiar prologu lub epilogu, przejdź kody unwind od początku sekwencji do końca i użyj tabeli odnośnika lub podobnej metody, aby określić, jak długo jest odpowiedni kod operacyjny.

Unwind kody 0xFD i 0xFE są równoważne z regularnym kodem końcowym 0xFF, ale stanowią jeden dodatkowy nop opcode w przypadku epilogu, 16-bitowy lub 32-bitowy. Dla prologów kody 0xFD, 0xFE i 0xFF są dokładnie równoważne. To stanowi wspólne zakończenia `bx lr` epilogu `b <tailcall-target>`lub , które nie mają równoważne instrukcje prologu. Zwiększa to prawdopodobieństwo, że sekwencje unwind mogą być współużytkowane między prologiem i epilogues.

W wielu przypadkach powinno być możliwe użycie tego samego zestawu kodów unwind dla prologu i wszystkich epilogów. Jednak do obsługi odwijania częściowo wykonane prologi i epilogues, może być trzeba mieć wiele sekwencji kodu unwind, które różnią się w kolejności lub zachowania. Dlatego każdy epilog ma swój własny indeks do tablicy unwind, aby pokazać, gdzie należy rozpocząć wykonywanie.

### <a name="unwinding-partial-prologues-and-epilogues"></a>Odwijanie częściowych prologów i epilogów

Najczęstszym przypadku unwinding jest, gdy wyjątek występuje w treści funkcji, z dala od prologu i wszystkich epilogues. W takim przypadku unwinder wykonuje kody w tablicy unwind począwszy od indeksu 0 i kontynuuje aż do wykrycia opcode końca.

Gdy wystąpi wyjątek podczas wykonywania prologu lub epilogu, ramka stosu jest tylko częściowo skonstruowana, a unwinder musi określić dokładnie, co zostało zrobione, aby poprawnie cofnąć.

Rozważmy na przykład tę sekwencję prologu i epilogu:

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

Obok każdego opcode jest odpowiedni kod unwind do opisania tej operacji. Sekwencja kodów unwind dla prologu jest lustrzanym odbiciem kodów unwind dla epilogu, nie licząc instrukcji końcowej. Ten przypadek jest wspólny i jest powodem, dla którego kody unwind dla prologu są zawsze zakłada się, że są przechowywane w odwrotnej kolejności z kolejności wykonywania prologu. Daje nam to wspólny zestaw kodów odwijania:

```asm
0xc7, 0xdd, 0x04, 0xfd
```

Kod 0xFD jest specjalny kod na końcu sekwencji, co oznacza, że epilog jest jeden 16-bitowa instrukcja dłuższa niż prolog. Dzięki temu możliwe jest większe udostępnianie kodów unwind.

W przykładzie jeśli wystąpi wyjątek, gdy treść funkcji między prologu i epilogu jest wykonywana, odwijanie rozpoczyna się od przypadku epilogu, z przesunięciem 0 w kodzie epilogu. Odpowiada to przesunięcie 0x140 w przykładzie. Unwinder wykonuje sekwencję pełnego unwind, ponieważ nie oczyszczania zostało zrobione. Jeśli zamiast tego wyjątek występuje jedna instrukcja po rozpoczęciu kodu epilogu, unwinder można pomyślnie odwinąć, pomijając pierwszy kod unwind. Biorąc pod uwagę mapowanie jeden do jednego między kodami opcodes i unwind kody, jeśli odwijanie z instrukcji *n* w epilogu, unwinder należy pominąć pierwsze *n* unwind kody.

Podobna logika działa w odwrotnej kolejności dla prologu. Jeśli odwijanie od przesunięcia 0 w prologu, nic nie musi być wykonane. Jeśli odwijanie z jednej instrukcji w, sekwencji unwind należy uruchomić jeden kod unwind od końca, ponieważ kody unwind prologu są przechowywane w odwrotnej kolejności. W ogólnym przypadku, jeśli odwijanie z instrukcji *n* w prologu, odwijanie należy rozpocząć wykonywanie w *n* unwind kody od końca listy kodów.

Kody odwijające prologu i epilogu nie zawsze dokładnie pasują do siebie. W takim przypadku tablica kodu unwind może zawierać kilka sekwencji kodów. Aby określić przesunięcie, aby rozpocząć przetwarzanie kodów, należy użyć następującej logiki:

1. Jeśli odwijanie z wewnątrz treści funkcji, rozpocząć wykonywanie unwind kody w indeksie 0 i kontynuować aż do zakończenia opcode zostanie osiągnięty.

2. Jeśli odwijanie z wewnątrz epilogu, należy użyć epilogu specyficzne indeksu początkowego przewidziane przez zakres epilogu. Oblicz, ile bajtów komputer jest od początku epilogu. Przejdź do przodu przez kody unwind, dopóki nie zostaną uwzględnione wszystkie już wykonane instrukcje. Wykonaj sekwencję unwind począwszy od tego punktu.

3. Jeśli odwijanie z wewnątrz prologu, rozpocząć od indeksu 0 w kody unwind. Oblicz długość kodu prologu z sekwencji, a następnie oblicz, ile bajtów komputer jest od końca prologu. Przejdź do przodu przez kody unwind, aż wszystkie niezadane instrukcje zostaną uwzględnione. Wykonaj sekwencję unwind począwszy od tego punktu.

Kody unwind dla prologu zawsze musi być pierwszy w tablicy. Są one również kody używane do odwijania w ogólnym przypadku odwijania się z wewnątrz ciała. Wszelkie sekwencje kodu specyficzne dla epilogu należy wykonać natychmiast po sekwencji kodu prologu.

### <a name="function-fragments"></a>Fragmenty funkcji

W celu optymalizacji kodu może być przydatne do podziału funkcji na części discontiguous. Po wykonaniu tej czynności każdy fragment funkcji wymaga osobnego rekordu .pdata — i ewentualnie .xdata.

Zakładając, że prolog funkcji znajduje się na początku funkcji i nie można go podzielić, istnieją cztery przypadki fragmentu funkcji:

- Tylko prolog; wszystkich epilogów w innych fragmentach.

- Prolog i jeden lub więcej epilogów; dodatkowe epilogi w innych fragmentach.

- Brak prologu lub epilogów; prologu i jednego lub więcej epilogów w innych fragmentach.

- Tylko epilogi; prologu i ewentualnie dodatkowych epilogów w innych fragmentach.

W pierwszym przypadku należy opisać tylko prolog. Można to zrobić w formie compact .pdata, opisując prolog normalnie i określając wartość *Ret* 3, aby wskazać brak epilogu. W formularzu .xdata można to zrobić, udostępniając kody odwijania prologu w indeksie 0 jak zwykle i określając liczbę epilogu 0.

Drugi przypadek jest jak normalna funkcja. Jeśli we fragmencie znajduje się tylko jeden epilog i znajduje się on na końcu fragmentu, można użyć kompaktowego rekordu .pdata. W przeciwnym razie należy użyć pełnego rekordu xdata. Należy pamiętać, że odsunięcia określone dla początku epilogu są względem początku fragmentu, a nie oryginalny początek funkcji.

Trzeci i czwarty przypadki są wariantami pierwszego i drugiego przypadku, odpowiednio, z wyjątkiem, że nie zawierają prologu. W takich sytuacjach zakłada się, że istnieje kod przed rozpoczęciem epilogu i jest uważany za część treści funkcji, która normalnie zostałaby rozwiana przez cofnięcie skutków prologu. W związku z tym przypadki te muszą być zakodowane za pomocą pseudoprologu, który opisuje sposób odwijania się z wewnątrz ciała, ale który jest traktowany jako 0-długość podczas określania, czy wykonać częściowe odwijanie na początku fragmentu. Alternatywnie ten pseudoprolog można opisać przy użyciu tych samych kodów unwind jako epilogu, ponieważ prawdopodobnie wykonują równoważne operacje.

W trzecim i czwartym przypadku obecność pseudo-prologu jest określona przez ustawienie pola *Flaga* rekordu _pdata na 2 lub przez ustawienie flagi *F* w nagłówku .xdata na 1. W obu przypadkach sprawdzanie częściowego odprężenia prologu jest ignorowane, a wszystkie unwinds non-epilogu są uważane za pełne.

#### <a name="large-functions"></a>Duże funkcje

Fragmenty mogą służyć do opisywania funkcji większych niż limit 512 KB narzucony przez pola bitowe w nagłówku .xdata. Aby opisać bardzo dużą funkcję, po prostu podziel ją na fragmenty mniejsze niż 512 KB. Każdy fragment powinien być dostosowany tak, aby nie dzielił epilogu na wiele kawałków.

Tylko pierwszy fragment funkcji zawiera prolog; wszystkie inne fragmenty są oznaczone jako nie posiadające prologu. W zależności od liczby epilogów każdy fragment może zawierać zero lub więcej epilogów. Należy pamiętać, że każdy zakres epilogu we fragmencie określa jego początkowe przesunięcie względem początku fragmentu, a nie początek funkcji.

Jeśli fragment nie ma prologu i nie ma epilogu, nadal wymaga własnego rekordu .pdata — i ewentualnie .xdata — do opisania sposobu odwijania się z treści funkcji.

#### <a name="shrink-wrapping"></a>Owijanie kurczliwe

Bardziej złożonym specjalnym przypadkiem fragmentów funkcji jest *zawijanie kurczliwe*, technika odroczenia zapisu zapisuje od początku funkcji do późniejszej funkcji, aby zoptymalizować dla prostych przypadków, które nie wymagają zapisywania rejestru. Można to opisać jako region zewnętrzny, który przydziela miejsce na stosie, ale zapisuje minimalny zestaw rejestrów i wewnętrzny region, który zapisuje i przywraca dodatkowe rejestry.

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

Zazwyczaj oczekuje się, że funkcje opakowane w folię termokurczliwą wstępnie przydzielą miejsce `str` na `stm` dodatkowe `push`zapisy rejestru w zwykłym prologu, a następnie wykonaj zapisy rejestru przy użyciu lub zamiast . Dzięki temu wszystkie stack-pointer manipulacji w oryginalnej funkcji prologu.

Przykładowa funkcja opakowana w zmniejszanie musi być podzielona na trzy regiony, które są oznaczone jako A, B i C w komentarzach. Pierwszy region A obejmuje rozpoczęcie funkcji przez koniec dodatkowych zapisów nieulotnych. Rekord .pdata lub .xdata musi być skonstruowany w taki sposób, aby opisywał ten fragment jako posiadający prolog i bez epilogów.

Środkowy region B pobiera własny rekord .pdata lub .xdata, który opisuje fragment, który nie ma prologu i nie ma epilogu. Jednak kody unwind dla tego regionu musi nadal być obecny, ponieważ jest uważany za treść funkcji. Kody muszą opisywać złożony prolog, który reprezentuje zarówno oryginalne rejestry zapisane w prologu regionu A, jak i dodatkowe rejestry zapisane przed wejściem do regionu B, tak jakby zostały wyprodukowane przez jedną sekwencję operacji.

Zapisy rejestru dla regionu B nie mogą być traktowane jako "wewnętrzny prolog", ponieważ prolog złożony opisany dla regionu B musi opisywać zarówno prolog regionu A, jak i zapisane dodatkowe rejestry. Jeśli fragment B zostały opisane jako posiadające prologu, unwind kody również oznacza rozmiar tego prologu i nie ma sposobu, aby opisać prologu złożonego w sposób, który mapuje jeden do jednego z opcodes, które zapisują tylko dodatkowe rejestry.

Dodatkowe zapisywanie rejestru należy uznać za część regionu A, ponieważ dopóki nie zostaną zakończone, złożony prolog nie dokładnie opisać stan stosu.

Ostatni region C pobiera własny rekord .pdata lub .xdata, opisujący fragment, który nie ma prologu, ale ma epilog.

Alternatywne podejście może również działać, jeśli manipulacja stosu wykonana przed wejściem do regionu B może zostać zmniejszona do jednej instrukcji:

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

Kluczem jest to, że na każdej granicy instrukcji stosu jest w pełni zgodne z kodów unwind dla regionu. Jeśli unwind występuje przed wypychaniem wewnętrznym w tym przykładzie, jest uważany za część regionu A i tylko region A prolog jest rozwijany. Jeśli unwind występuje po wewnętrznej push, jest uważany za część regionu B, który nie ma prologu, ale ma unwind kody, które opisują zarówno wewnętrznego wypychania i oryginalnego prologu z regionu A. Podobna logika posiada dla wewnętrznego pop.

### <a name="encoding-optimizations"></a>Optymalizacje kodowania

Ze względu na bogactwo kodów unwind i możliwość wykorzystania kompaktowych i rozszerzonych form danych, istnieje wiele możliwości optymalizacji kodowania w celu dalszego zmniejszenia przestrzeni. Przy agresywnym użyciu tych technik obciążenie netto opisujące funkcje i fragmenty przy użyciu kodów unwind może być dość minimalne.

Najważniejszą optymalizacją jest uważać, aby nie mylić granic prologu/epilogu do celów odwijania z logicznymi granicami prologu/epilogu z perspektywy kompilatora. Granice odwijania można zmniejszać i mocniej zmniejszać, aby poprawić wydajność. Na przykład prolog może zawierać kod po konfiguracji stosu, aby wykonać dodatkowe kontrole weryfikacyjne. Ale po zakończeniu wszystkie manipulowanie stosem, nie ma potrzeby kodowania dalszych operacji i wszystko poza tym można usunąć z prologu odwijania.

Ta sama reguła ma zastosowanie do długości funkcji. Jeśli istnieją dane — na przykład pula literału — która następuje po epilogu w funkcji, nie powinny być uwzględniane jako część długości funkcji. Zmniejszając funkcję tylko do kodu, który jest częścią funkcji, szanse są znacznie większe, że epilog będzie na samym końcu i kompaktowy. można użyć rekordu pdata.

W prologu, gdy wskaźnik stosu jest zapisywany do innego rejestru, zazwyczaj nie ma potrzeby rejestrowania żadnych dalszych kodów opcodes. Aby odwinąć funkcję, pierwszą rzeczą, która jest wykonywana jest odzyskanie sp z zapisanego rejestru, a więc dalsze operacje nie mają żadnego wpływu na unwind.

Epilogues pojedynczej instrukcji nie muszą być w ogóle kodowane, jako zakresy lub jako kody unwind. Jeśli unwind odbywa się przed wykonaniem tej instrukcji, następnie można założyć, że z wewnątrz treści funkcji i po prostu wykonywanie kodów unwind prologu jest wystarczająca. Jeśli unwind odbywa się po wykonaniu pojedynczej instrukcji, a następnie z definicji odbywa się w innym regionie.

Epilogues wielu instrukcji nie trzeba kodować pierwszą instrukcję epilogu, z tego samego powodu, co poprzedni punkt: jeśli unwind odbywa się przed wykonaniem tej instrukcji, pełne odwijanie prologu jest wystarczające. Jeśli odprężenie odbywa się po tej instrukcji, należy wziąć pod uwagę tylko kolejne operacje.

Ponowne użycie kodu Unwind powinno być agresywne. Indeks określony przez każdy zakres epilogu wskazuje na dowolny punkt początkowy w tablicy kodów unwind. Nie musi wskazywać na początek poprzedniej sekwencji; może wskazywać w środku. Najlepszym rozwiązaniem w tym miejscu jest wygenerowanie żądanej sekwencji kodu, a następnie skanowanie w poszukiwaniu dokładnego dopasowania bajtów w już zakodowanej puli sekwencji i użycie dowolnego idealnego dopasowania jako punktu wyjścia do ponownego użycia.

Jeśli po jednej instrukcji epilogues są ignorowane, nie ma żadnych pozostałych epilogues, należy rozważyć użycie kompaktowy .pdata formularza; staje się znacznie bardziej prawdopodobne w przypadku braku epilogu.

## <a name="examples"></a>Przykłady

W tych przykładach baza obrazu jest na 0x00400000.

### <a name="example-1-leaf-function-no-locals"></a>Przykład 1: Funkcja liścia, brak miejscowych

```asm
Prologue:
  004535F8: B430      push        {r4-r5}
Epilogue:
  00453656: BC30      pop         {r4-r5}
  00453658: 4770      bx          lr
```

.pdata (stała, 2 słowa):

- Słowo 0

  - *Uruchomienie funkcji RVA* = 0x000535F8 (= 0x004535F8-0x00400000)

- Słowo 1

  - *Flaga* = 1, wskazująca formaty prologu kanonicznego i epilogu

  - *Długość funkcji* = 0x31 (= 0x62/2)

  - *Ret* = 1, wskazujący 16-bitowy zwrot gałęzi

  - *H* = 0, wskazując, że parametry nie były

  - *R*=0 i *Reg* = 1, wskazując push/pop r4-r5

  - *L* = 0, co oznacza brak zapisywania/przywracania LR

  - *C* = 0, wskazując brak łańcucha ramy

  - *Stack Adjust* = 0, wskazując brak regulacji stosu

### <a name="example-2-nested-function-with-local-allocation"></a>Przykład 2: Funkcja zagnieżdżona z alokacją lokalną

```asm
Prologue:
  004533AC: B5F0      push        {r4-r7, lr}
  004533AE: B083      sub         sp, sp, #0xC
Epilogue:
  00453412: B003      add         sp, sp, #0xC
  00453414: BDF0      pop         {r4-r7, pc}
```

.pdata (stała, 2 słowa):

- Słowo 0

  - *Uruchomienie funkcji RVA* = 0x000533AC (= 0x004533AC -0x00400000)

- Słowo 1

  - *Flaga* = 1, wskazująca formaty prologu kanonicznego i epilogu

  - *Długość funkcji* = 0x35 (= 0x6A/2)

  - *Ret* = 0, wskazując pop {pc} return

  - *H* = 0, wskazując, że parametry nie były

  - *R*=0 i *Reg* = 3, wskazując push/pop r4-r7

  - *L* = 1, wskazując LR został zapisany /przywrócony

  - *C* = 0, wskazując brak łańcucha ramy

  - *Regulacja stosu* = 3 (= 0x0C/4)

### <a name="example-3-nested-variadic-function"></a>Przykład 3: Zagnieżdżona funkcja zmienniczna

```asm
Prologue:
  00453988: B40F      push        {r0-r3}
  0045398A: B570      push        {r4-r6, lr}
Epilogue:
  004539D4: E8BD 4070 pop         {r4-r6}
  004539D8: F85D FB14 ldr         pc, [sp], #0x14
```

.pdata (stała, 2 słowa):

- Słowo 0

  - *Uruchomienie funkcji RVA* = 0x00053988 (= 0x00453988-0x00400000)

- Słowo 1

  - *Flaga* = 1, wskazująca formaty prologu kanonicznego i epilogu

  - *Długość funkcji* = 0x2A (= 0x54/2)

  - *Ret* = 0, wskazujący powrót w stylu pop {pc}(w tym przypadku ldr pc,[sp],#0x14 return)

  - *H* = 1, wskazując parametry były homed

  - *R*=0 i *Reg* = 2, wskazując push/pop r4-r6

  - *L* = 1, wskazując LR został zapisany /przywrócony

  - *C* = 0, wskazując brak łańcucha ramy

  - *Stack Adjust* = 0, wskazując brak regulacji stosu

### <a name="example-4-function-with-multiple-epilogues"></a>Przykład 4: Funkcja z wieloma epilogami

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

.pdata (stała, 2 słowa):

- Słowo 0

  - *Uruchomienie funkcji RVA* = 0x000592F4 (= 0x004592F4-0x00400000)

- Słowo 1

  - *Flaga* = 0, wskazująca .xdata record present (wymagana z powodu wielu epilogów)

  - *.xdata adres* - 0x00400000

.xdata (zmienna, 6 słów):

- Słowo 0

  - *Długość funkcji* = 0x0001A3 (= 0x000346/2)

  - *Vers* = 0, wskazując pierwszą wersję xdata

  - *X* = 0, wskazując brak danych wyjątków

  - *E* = 0, wskazując listę zakresów epilogu

  - *F* = 0, wskazując pełny opis funkcji, w tym prolog

  - *Liczba epilogu* = 0x04, wskazująca 4 zakresy epilogu całkowitego

  - *Słowa kodowe* = 0x01, wskazujące jedno 32-bitowe słowo kodów unwind

- Słowa 1-4, opisujące 4 zakresy epilogu w 4 lokalizacjach. Każdy zakres ma wspólny zestaw kodów unwind, współużytkowane z prologu, z przesunięciem 0x00 i jest bezwarunkowy, określając warunek 0x0E (zawsze).

- Kody unwind, począwszy od programu Word 5: (współużytkowane przez prolog/epilog)

  - Kod odwijania 0 = 0x06: sp += (6 << 2)

  - Kod unwind 1 = 0xDE: pop {r4-r10, lr}

  - Kod unwind 2 = 0xFF: koniec

### <a name="example-5-function-with-dynamic-stack-and-inner-epilogue"></a>Przykład 5: Funkcja z dynamicznym stosem i epilogiem wewnętrznym

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

.pdata (stała, 2 słowa):

- Słowo 0

  - *Uruchomienie funkcji RVA* = 0x00085A20 (= 0x00485A20-0x00400000)

- Słowo 1

  - *Flaga* = 0, wskazująca .xdata record present (potrzebne ze względu na wiele epilogów)

  - *.xdata adres* - 0x00400000

.xdata (zmienna, 3 słowa):

- Słowo 0

  - *Długość funkcji* = 0x0001A3 (= 0x000346/2)

  - *Vers* = 0, wskazując pierwszą wersję xdata

  - *X* = 0, wskazując brak danych wyjątków

  - *E* = 0, wskazując listę zakresów epilogu

  - *F* = 0, wskazując pełny opis funkcji, w tym prolog

  - *Liczba epilogu* = 0x001, wskazująca 1 całkowity zakres epilogu

  - *Słowa kodowe* = 0x01, wskazujące jedno 32-bitowe słowo kodów unwind

- Słowo 1: Zakres epilogu z przesunięciem 0xC6 (= 0x18C/2), uruchamianie indeksu kodu unwind na 0x00 i z warunkiem 0x0E (zawsze)

- Kody unwind, począwszy od programu Word 2: (współużytkowane przez prolog/epilog)

  - Kod unwind 0 = 0xC6: sp = r6

  - Kod unwind 1 = 0xDC: pop {r4-r8, lr}

  - Kod odwijania 2 = 0x04: sp += (4 << 2)

  - Kod unwind 3 = 0xFD: koniec, liczy się jako 16-bitowa instrukcja dla epilogu

### <a name="example-6-function-with-exception-handler"></a>Przykład 6: Funkcja z funkcją obsługi wyjątków

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

.pdata (stała, 2 słowa):

- Słowo 0

  - *Uruchomienie funkcji RVA* = 0x00088C24 (= 0x00488C24-0x00400000)

- Słowo 1

  - *Flaga* = 0, wskazująca .xdata record present (potrzebne ze względu na wiele epilogów)

  - *.xdata adres* - 0x00400000

.xdata (zmienna, 5 słów):

- Słowo 0

  - *Długość funkcji* = 0x000027 (= 0x00004E/2)

  - *Vers* = 0, wskazując pierwszą wersję xdata

  - *X* = 1, wskazując dane wyjątku obecne

  - *E* = 1, wskazując pojedynczy epilog

  - *F* = 0, wskazując pełny opis funkcji, w tym prolog

  - *Liczba epilogu* = 0x00, wskazujące kody odwijania epilogu zaczynają się od przesunięcia 0x00

  - *Słowa kodowe* = 0x02, wskazujące dwa 32-bitowe słowa kodów unwind

- Odwiń kody, począwszy od programu Word 1:

  - Kod unwind 0 = 0xC7: sp = r7

  - Kod odwijania 1 = 0x05: sp += (5 << 2)

  - Kod unwind 2 = 0xED/0x90: pop {r4, r7, lr}

  - Kod unwind 4 = 0xFF: koniec

- Word 3 określa program obsługi wyjątków = 0x0019A7ED (= 0x0059A7ED - 0x00400000)

- Słowa 4 i więcej są inlined dane wyjątku

### <a name="example-7-funclet"></a>Przykład 7: Funclet

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

.pdata (stała, 2 słowa):

- Słowo 0

  - *Uruchomienie funkcji RVA* = 0x00088C72 (= 0x00488C72-0x00400000)

- Słowo 1

  - *Flaga* = 1, wskazująca formaty prologu kanonicznego i epilogu

  - *Długość funkcji* = 0x0B (= 0x16/2)

  - *Ret* = 0, wskazując pop {pc} return

  - *H* = 0, wskazując, że parametry nie były

  - *R*=0 i *Reg* = 7, co oznacza, że nie zapisano/przywracano żadnych rejestrów

  - *L* = 1, wskazując LR został zapisany /przywrócony

  - *C* = 0, wskazując brak łańcucha ramy

  - *Stack Adjust* = 1, wskazując 1 × 4 bajtową regulację stosu

## <a name="see-also"></a>Zobacz też

[Omówienie konwencji ARM ABI](overview-of-arm-abi-conventions.md)<br/>
[Typowe problemy przy migracji Visual C++ ARM](common-visual-cpp-arm-migration-issues.md)
