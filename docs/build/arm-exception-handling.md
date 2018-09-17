---
title: Obsługa wyjątków ARM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/11/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fe0e615f-c033-4ad5-97f4-ff96af45b201
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2251aefebd6805cfd071d014ad6be30cbea065bb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711233"
---
# <a name="arm-exception-handling"></a>Obsługa wyjątków ARM

Windows na ARM używa tego samego strukturalnej obsługi wyjątków mechanizm asynchroniczne wyjątki generowane przez sprzęt i synchroniczne wyjątki generowane przez oprogramowanie. Programy obsługi wyjątków specyficzne dla języka są tworzone na podstawie Windows obsługi przy użyciu języka funkcji pomocnika wyjątków strukturalnych. W tym dokumencie opisano obsługę wyjątków w Windows na ARM i pomocników język używany przez kod, który jest generowany przez asemblera ARM firmy Microsoft i kompilator języka Visual C++.

## <a name="arm-exception-handling"></a>Obsługa wyjątków ARM

Używa Windows na ARM *kodów odwinięcia* do kontrolowania, podczas wykonywania operacji odwijania stosu [obsługę wyjątków strukturalnych](https://msdn.microsoft.com/library/windows/desktop/ms680657) (SEH). Operacja unwind kody to sekwencja bajtów przechowywanych w sekcji .xdata obrazu pliku wykonywalnego. Opisują one działania kodu prologu i epilogu funkcji abstrakcyjne przebiega tak, aby skutki prologu funkcji można cofnąć w ramach przygotowania do rozwinięcia do obiektu wywołującego ramki stosu.

EABI ARM (interfejsem binarnym aplikacji osadzonej) określa kodów odwinięcia odwijania model wyjątków, który używa, ale nie jest wystarczająca dla SEH odwijanie w Windows, który musi obsługiwać asynchronicznego przypadki, w którym procesor jest w trakcie prologu lub epilogu funkcji. Windows oddziela również odwijania kontroli na poziomie funkcji odwijanie i odwijanie zakres specyficzny dla języka, który jest jednolita w ARM EABI. Z tego względu Windows na ARM określa więcej szczegółów odwijania danych i procedury.

### <a name="assumptions"></a>Założenia

Obrazy wykonywalne dla Windows na ARM formatu przenośnego pliku wykonywalnego (PE). Aby uzyskać więcej informacji, zobacz [Microsoft PE i COFF specyfikacji](http://go.microsoft.com/fwlink/p/?linkid=84140). Wyjątek obsługi informacji znajduje się w sekcjach .pdata i .xdata obrazu.

Mechanizm obsługi wyjątków sprawia, że niektóre założenia dotyczące kodu, który następuje dla interfejsu ABI Windows na ARM:

- Gdy wystąpi wyjątek w treści funkcji, nie ma znaczenia, czy operacje prologu zostaną cofnięte, epilogu operacje są wykonywane w sposób do przodu. Obie powinny być takie same wyniki.

- Prologues i epilogues zwykle duplikatów siebie nawzajem. To może służyć do zmniejszenia rozmiaru metadane potrzebne do opisania odwijanie.

- Funkcje zwykle jest stosunkowo mały. Wprowadzono kilka optymalizacji opierają się na to wydajne pakowania danych.

- Jeśli warunek jest umieszczany na epilogu, jego stosuje się jednakowo do każdej instrukcji w epilogu.

- Jeśli wskaźnik stosu (SP) zostanie zapisany w innym Zarejestruj się w prologu, który rejestru musi pozostać bez zmian w całej funkcji, tak, aby oryginalny SP może zostać odzyskana w dowolnym momencie.

- Chyba że PS zostanie zapisany w innym rejestru, manipulowania wszystkie jego musi zawierać wyłącznie się w prologu i epilogu.

- Na odpoczynek, wszystkie ramki stosu, wymagane są następujące operacje:

  - Dostosuj r13 (SP) w przyrostach co 4-bajtowe.

  - POP jeden lub więcej całkowitą rejestruje.

  - POP co najmniej jeden Visual FOXPRO (wirtualny zmiennoprzecinkowych) rejestruje.

  - Skopiuj wartości z dowolnego rejestru do r13 (SP).

  - Załaduj SP ze stosu przy użyciu małych operacji dekrementacji po wydaniu.

  - Analizowanie jeden z kilku typów dobrze zdefiniowanych ramki.

### <a name="pdata-records"></a>rekordy .pdata

Rekordy .pdata w obrazie środowiska Preinstalacyjnego formatu są uporządkowanej tablicy elementów o stałej długości, które opisują co funkcja manipulowania stosu. Funkcje typu liść, które są funkcje, które nie wymagają innych funkcji, nie wymagają rekordów .pdata podczas ich stosu nie jest modyfikowany. (Oznacza to, ich nie wymagają żadnych magazynu lokalnego i nie ma do zapisania lub przywrócenia rejestrów trwałej). Rekordy dla tych funkcji można pominąć z sekcji .pdata, aby zaoszczędzić miejsce. Operacji unwind z jednej z tych funkcji można po prostu skopiuj adres zwrotny z Link Zarejestruj (LR) do licznik programu (PC), aby przenieść do obiektu wywołującego.

Każdy rekord .pdata dla ARM jest 8 bajtów. Ogólny format rekordu umieszcza względnych adresów wirtualnych (RVA) początku funkcji w pierwszy wyraz 32-bitowych, następuje w drugi programu word, który zawiera wskaźnik do bloku .xdata o zmiennej długości lub upakowaną słowo opisujące kanonicznej funkcji Sekwencja odwijania, jak pokazano w poniższej tabeli:

|Przesunięcie programu Word|Bity|Cel|
|-----------------|----------|-------------|
|0|0-31|*Funkcja Start RVA* jest RVA 32-bitowych uruchomienia funkcji. Jeśli funkcja zawiera kod thumb, należy ustawić niski bitu ten adres.|
|1|0-1|*Flaga* jest polem 2-bitowy, która wskazuje, jak interpretować pozostałych bitów 30 drugi wyrazu, .pdata. Jeśli *flagi* wynosi 0, a następnie pozostałe bits formularza *RVA informacje o wyjątku* (za pomocą niski dwa bity niejawnie 0). Jeśli *flagi* jest różna od zera, pozostałe bits formularza *spakowane dane operacji Unwind* struktury.|
|1|2-31|*Informacje o wyjątku RVA* lub *spakowane dane operacji Unwind*.<br /><br /> *Adres RVA informacje o wyjątku* to adres struktury informacji o zmiennej długości wyjątek, przechowywane w sekcji .xdata. Musi to być 4-bajtowego wyrównania.<br /><br /> *Spakowane dane operacji Unwind* jest skompresowany opis czynności wymagane do odkręcanie z funkcji, zakładając, że forma kanoniczna. W tym przypadku żadnego rekordu .xdata jest wymagany.|

### <a name="packed-unwind-data"></a>Spakowane dane operacji Unwind

Dla operacji unwind funkcje, których prologues i epilogues postępuj zgodnie z spakowane w formie kanonicznej opisane poniżej, dane mogą być używane. To eliminuje potrzebę stosowania rekord .xdata i znacznie zmniejsza miejsce wymagane jest podanie dane operacji unwind. Canonical prologues i epilogues są przeznaczone do typowych wymagań prostej funkcji, który nie wymaga obsługi wyjątków i wykonuje jej operacje instalacji i usuwania w standardowej kolejności.

W poniższej tabeli przedstawiono format elementu .pdata rekord, który ma spakowane unwind danych:

|Przesunięcie programu Word|Bity|Cel|
|-----------------|----------|-------------|
|0|0-31|*Funkcja Start RVA* jest RVA 32-bitowych uruchomienia funkcji. Jeśli funkcja zawiera kod thumb, należy ustawić niski bitu ten adres.|
|1|0-1|*Flaga* jest polem 2-bitowy, który ma znaczenie tych:<br /><br /> -00 = upakowaną nie jest używany; dane operacji unwind pozostałych bitów wskazują rekord .xdata.<br />-01 = spakowane dane operacji unwind.<br />-10 = spakowana gdy funkcja jest zakłada się, że nie prologu dane operacji unwind. Jest to przydatne do opisywania fragmenty funkcja, które są nieciągłe z początku funkcji.<br />-11 = zastrzeżone.|
|1|2-12|*Funkcja długość* jest polem 11-bitowy, zapewniająca długość całej funkcji w bajtach podzielonej przez 2. Funkcja jest większy niż 4 KB, zamiast tego należy użyć rekordu pełną .xdata.|
|1|13-14|*RET* jest polem 2-bitowy, która wskazuje, jak funkcja zwraca:<br /><br /> -00 = Wróć za pośrednictwem pop {komputera} ( *L* bit flagi musi być równa 1 w tym przypadku).<br />-01 = Wróć za pomocą gałęzi 16-bitowych.<br />-10 = Wróć za pomocą gałęzi 32-bitowych.<br />-11 = nie epilogu wcale. Jest to przydatne do opisywania fragmentu nieciągłe — funkcja, która może zawierać tylko prologu, ale których epilogu znajduje się w innym.|
|1|15|*H* flagi 1-bitowego, która wskazuje, czy funkcja "homes" parametru liczby całkowitej rejestruje (r0 r3) przez wypychanie ich na początku funkcji, a następnie zwalnia 16 bajtów stosu przed zwróceniem. (0 = nie główna rejestrów, 1 = domów rejestrów.)|
|1|16-18|*Reg* pole 3-bitową, który wskazuje indeks ostatniego zapisaniu register-volatile. Jeśli *R* bit ma wartość 0, a następnie utworzyć tylko liczby całkowitej rejestrów są zapisywane są zakłada się, że w zakresie rN r4, gdzie N jest równa 4 + *Reg*. Jeśli *R* bit ma wartość 1, a następnie utworzyć rejestrów zmiennoprzecinkowych tylko są zapisywane są zakłada się, że w zakresie dN d8, gdzie N jest równa 8 + *Reg*. Specjalne kombinacji *R* = 1 i *Reg* = 7 wskazuje, że brak rejestrów są zapisywane.|
|1|19|*R* jest flaga 1-bitowego, która wskazuje, czy są zapisane rejestrów trwałej całkowitą rejestruje (0) lub rejestrów zmiennoprzecinkowych (1). Jeśli *R* jest ustawiona na 1 i *Reg* pole jest ustawione na 7, brak rejestrów trwałej zostały przekazane.|
|1|20|*L* jest flaga 1-bitowego, która wskazuje, czy funkcja zapisuje/Przywracanie LR, wraz z innych rejestrów wskazywanym przez *Reg* pola. (0 = nie zapisać/przywrócić, 1 = czy zapisać/przywrócić.)|
|1|21|*C* jest flagę 1-bitowego, która wskazuje, czy funkcja zawiera dodatkowe instrukcje dotyczące ustawiania łańcuch ramki dla szybkie przechodzenie po stosie (1) czy nie (0). Jeśli ten bit jest ustawiony, r11 niejawnie jest dodawany do listy rejestrów trwałej całkowitą zapisane. (Zobacz ograniczenia poniższy *C* flaga jest używana.)|
|1|22-31|*Stack — Dostosuj* jest polem 10-bitowy, który wskazuje liczbę bajtów stosu, które są przydzielane dla tej funkcji, podzielona przez 4. Jednak tylko wartości z zakresu od 0x000 0x3F3 może bezpośrednio zakodowany. Funkcje, które przydzielić więcej niż 4044 bajtów stosu, należy użyć rekordu pełną .xdata. Jeśli *dostosowanie stosu* pole jest 0x3F4 lub większą, a następnie niski 4 bity mają specjalne znaczenie:<br /><br /> -Bitów 0-1 wskazuje liczbę wyrazów dostosowanie stosu (1-4), minus 1.<br />-Bit 2 jest ustawiona na 1, jeśli prologu połączone to dostosowanie do swoich operacji wypychania.<br />-Bit 3 jest ustawiona na 1, jeśli epilogu połączone to dostosowanie do swoich operacji pop.|

Ze względu na możliwe zwolnień w powyższym kodowania są stosowane następujące ograniczenia:

- Jeśli *C* flaga jest ustawiona na 1:

   - *L* flagi również musi być ustawiona na 1, ponieważ łańcuch ramki wymagane r11 i LR.

   - R11, nie muszą być zawarte w zestaw rejestrów opisanego przez *Reg*. Oznacza to, jeśli wypychania r4 r11 *Reg* tylko powinna opisywać r4-r10 *C* Flaga implikuje r11.

- Jeśli *Ret* pole jest ustawione na 0, *L* flagi musi być równa 1.

Naruszenie ograniczenia te powoduje, że nieobsługiwany sekwencji.

Na potrzeby poniższego omówienia, dwie pseudo-flagi są uzyskiwane z *dostosowanie stosu*:

- *PF* lub "prologu składanie" oznacza to, że *dostosowanie stosu* jest 0x3F4 lub większych i bit 2 została ustawiona.

- *EF* lub "epilogu składanie" oznacza to, że *dostosowanie stosu* jest 0x3F4 lub większych i bit 3 jest ustawiona.

Prologues kanonicznej funkcji może mieć maksymalnie 5 instrukcje (Zwróć uwagę, że 3a i 3b wykluczają się wzajemnie):

|Instrukcja|OpCode zakłada, że istnieje jeśli:|Rozmiar|OpCode|Kodów odwinięcia|
|-----------------|-----------------------------------|----------|------------|------------------|
|1|*H*== 1|16|`push {r0-r3}`|04|
|2|*C*== 1 lub *L*== 1 lub *R*== 0 lub PF == 1|16/32|`push {registers}`|80-BF/D0-DF/WE ED|
|3a|*C*== 1 i (*L*== 0 i *R*== 1 i PF == 0)|16|`mov r11,sp`|C0-CF/PLATFORMY FB|
|3b|*C*== 1 i (*L*== 1 lub *R*== 0 lub PF == 1)|32|`add r11,sp,#xx`|FC|
|4|*R*== 1 i *Reg* ! = 7|32|`vpush {d8-dE}`|E0 E7|
|5|*Dostosowanie stosu* ! = 0 i PF == 0|16/32|`sub sp,sp,#xx`|00-7F/E8-EB|

Zawsze występuje instrukcja 1 Jeśli *H* bit jest ustawiony na 1.

Aby skonfigurować łańcuch ramki, występuje instrukcja 3a lub 3b Jeśli *C* bit jest ustawiony. Jest 16-bitowych `mov` Jeśli nie są przekazywane w rejestrach innych niż r11 i LR; w przeciwnym razie jest 32-bitowa `add`.

Jeśli określono korekty składane, instrukcji 5 jest dostosowanie jawne stosu.

Instrukcje 2 i 4 są ustawiane w zależności od tego, czy jest wymagane powiadomienie wypychane. Ta tabela zawiera podsumowanie, który rejestruje są zapisywane w oparciu o *C*, *L*, *R*, i *PF* pola. We wszystkich przypadkach *N* jest równa *Reg* + 4, *E* jest równa *Reg* + 8, a *S* jest równa (~*Dostosowanie stosu*) i 3.

|C|L|R|PF|Liczba całkowita rejestrach wypychane|Rejestruje Visual FOXPRO wypychania|
|-------|-------|-------|--------|------------------------------|--------------------------|
|0|0|0|0|R4 r*N*|brak|
|0|0|0|1|r*S*- r*N*|brak|
|0|0|1|0|brak|D8 d*E*|
|0|0|1|1|r*S*-r3|D8 d*E*|
|0|1|0|0|R4 r*N*, LR|brak|
|0|1|0|1|r*S*- r*N*, LR|brak|
|0|1|1|0|LR|D8 d*E*|
|0|1|1|1|r*S*-r3, LR|D8 d*E*|
|1|0|0|0|R4 r*N*, r11|brak|
|1|0|0|1|r*S*- r*N*, r11|brak|
|1|0|1|0|R11|D8 d*E*|
|1|0|1|1|r*S*-r3, r11|D8 d*E*|
|1|1|0|0|R4 r*N*, r11, LR|brak|
|1|1|0|1|r*S*- r*N*, r11, LR|brak|
|1|1|1|0|R11, LR|D8 d*E*|
|1|1|1|1|r*S*-r3 r11, LR|D8 d*E*|

Epilogues funkcje canonical postępuj zgodnie z formularzem podobne, ale w odwrotnej kolejności i z pewne dodatkowe opcje. Epilogu może być maksymalnie 5 instrukcji długich i jego formularza ściśle jest zależna od postaci prologu.

|Instrukcja|OpCode zakłada, że istnieje jeśli:|Rozmiar|OpCode|
|-----------------|-----------------------------------|----------|------------|
|6|*Dostosowanie stosu*! = 0 i *EF*== 0|16/32|`add   sp,sp,#xx`|
|7|*R*== 1 i *Reg*! = 7|32|`vpop  {d8-dE}`|
|8|*C*== 1 lub (*L*== 1 i *H*== 0) lub *R*== 0 lub *EF*== 1|16/32|`pop   {registers}`|
|9a|*H*== 1 i *L*== 0|16|`add   sp,sp,#0x10`|
|9b|*H*== 1 i *L*== 1|32|`ldr   pc,[sp],#0x14`|
|10a|*RET*== 1|16|`bx    reg`|
|10b|*RET*== 2|32|`b     address`|

Instrukcji 6 jest dostosowanie stosu jawne, jeśli określono-składanych dopasowania. Ponieważ *PF* jest niezależna od *EF*, istnieje możliwość instrukcji 5 obecne bez instrukcji 6 lub na odwrót.

Instrukcje 7 i 8 pełnić tę samą logikę prologu do określenia, który rejestruje zostaną przywrócone ze stosu, ale te dwie zmiany: po pierwsze, *EF* jest używana zamiast *PF*; drugi, jeśli *Ret*  = 0, a LR zostaje zastąpiona opcją komputera, na liście rejestru epilogu kończy się natychmiast.

Jeśli *H* jest ustawiona, 9a instrukcji lub 9b jest obecny. 9a instrukcja jest używane podczas *L* ma wartość 0, aby wskazać, że LR nie znajduje się na stosie. W tym przypadku jest ręcznie korygowana stosu i *Ret* musi wynosić 1 lub 2, aby określić jawnego powrotu. 9b instrukcja jest używane podczas *L* wynosi 1, aby wskazać koniec wczesne epilogu oraz do powrócić i dopasować stosu, w tym samym czasie.

Jeśli epilogu nie została już zakończona, następnie albo instrukcja 10a lub 10b jest obecny, aby wskazać gałąź 16-bitowe czy 32-bitowe, na podstawie wartości z *Ret*.

### <a name="xdata-records"></a>rekordy .xdata

Format upakowaną odwijania jest niewystarczający do opisania rozwinięcia funkcji, rekord o zmiennej długości .xdata musi zostać utworzona. Adres ten rekord jest przechowywany w drugim słowie rekordu .pdata. Format .xdata jest spakowany o zmiennej długości zbiór słów, które zawiera cztery sekcje:

1. Nagłówek 1 lub 2-programu word opisujący całkowity rozmiar struktury .xdata i dostarcza danych kluczowa funkcja. Drugi word jest obecny tylko, jeśli *liczba epilogu* i *wyrazów* pola są ustawione na 0. Pola są podzielone w tej tabeli:

   |Word|Bity|Cel|
   |----------|----------|-------------|
   |0|0-17|*Funkcja długość* jest pole 18-bitowe, które wskazuje całkowita długość tej funkcji w bajtach, podzielonej przez 2. Jeśli funkcja jest większa niż 512 KB, wiele rekordów .pdata i .xdata musi używane do opisywania tej funkcji. Aby uzyskać szczegółowe informacje Zobacz sekcję długie funkcje, w tym dokumencie.|
   |0|18-19|*Sterowniki* jest polem 2-bitowy, opisujący wersję pozostałe xdata. Wersja 0 jest obecnie zdefiniowany; wartości 1-3 są zastrzeżone.|
   |0|20|*X* jest polem 1-bitowego, który wskazuje obecność (1) lub dane wyjątku braku (0).|
   |0|21|*E* jest polem 1-bitowego, która wskazuje, że w nagłówku (1) zawiera informacje opisujące pojedynczego epilogu zamiast konieczności dodatkowego zakresu wyrazów nowszej (0).|
   |0|22|*F* jest polem 1-bitowego, która wskazuje, czy ten rekord zawiera opis fragmentu — funkcja (1) lub pełne działanie (0). Fragment oznacza, że nie istnieje żadne prologu i całego procesu przetwarzania prologu mają być ignorowane.|
   |0|23-27|*Liczba epilogu* jest polem 5-bitowy, który ma dwa znaczenia, w zależności od stanu *E* bitowych:<br /><br /> -Jeśli *E* wynosi 0, to pole jest liczba całkowita liczba zakresów wyjątek opisane w sekcji 3. Jeśli istnieje więcej niż 31-zakresami, w funkcji, a następnie tego pola i *wyrazów* pola musi mieć wartość 0 Aby wskazać, że wymagane jest rozszerzenie programu word.<br />-Jeśli *E* wynosi 1, w tym polu określa indeks pierwszego kodu odwijania, który opisuje tylko epilogu.|
   |0|28-31|*Wyrazy kodu* pole 4-bitowy, określający liczbę wyrazów 32-bitowe muszą zawierać wszystkie kody unwind w sekcji 4. Jeśli więcej niż 15 wyrazy są wymagane dla więcej niż 63 unwind bajty kodu, w tym polu i *liczba epilogu* pola musi mieć wartość 0 Aby wskazać, że wymagane jest rozszerzenie programu word.|
   |1|0-15|*Rozszerzony liczba epilogu* jest polem 16-bitowych, który zapewnia więcej miejsca na potrzeby kodowania niezwykle dużą liczbę epilogues. Słowo rozszerzenia, które zawiera to pole jest obecny tylko, jeśli *liczba epilogu* i *wyrazów* pól w pierwszy wyraz nagłówka są ustawione na 0.|
   |1|16-23|*Rozszerzony wyrazów* jest pole 8-bitowych, które udostępnia więcej miejsca do kodowania niezwykle dużą liczbę wyrazów unwind. Słowo rozszerzenia, które zawiera to pole jest obecny tylko, jeśli *liczba epilogu* i *wyrazów* pól w pierwszy wyraz nagłówka są ustawione na 0.|
   |1|24-31|Zastrzeżone|

2. Po dane wyjątku (Jeśli *E* bit w nagłówku został ustawiony na 0) znajduje się lista informacji o zakresach epilogu, które są pakowane do programu word i przechowywane w celu zwiększenia początkowe przesunięcie. Każdy zakres zawiera następujące pola:

   |Bity|Cel|
   |----------|-------------|
   |0-17|*Przesunięcie Start epilogu* jest polem 18-bitowe, opisujący przesunięcie epilogu, w bajtach podzielonej przez 2 względem początku funkcji.|
   |18-19|*Res* jest polem 2-bitowy zarezerwowane dla przyszłego rozszerzenia. Musi wynosić 0.|
   |20-23|*Warunek* pole 4-bitowy, zapewniająca warunek, pod którym jest wykonywany epilogu. Dla bezwarunkowe epilogues go powinna być równa 0xE, co oznacza "zawsze". (Epilogu musi być całkowicie warunkowych lub całkowicie bezwarunkowe, i w trybie Thumb-2 epilogu zaczyna się od pierwszej instrukcji po IT opcode).|
   |24-31|*Indeks Start epilogu* jest pole 8-bitowych, które wskazuje indeks bajtu pierwszy kod unwind opisujący tego epilogu.|

3. Po listy zakresów epilogu zawiera tablicę bajtów, które zawierają kody odwijania, które są szczegółowo opisane w sekcji Unwind kody w tym artykule. Ta tablica jest uzupełniana na końcu do najbliższej granicy pełny wyraz. Bajty są przechowywane w kolejności little-endian, dzięki czemu mogą być bezpośrednio pobierane w trybie little-endian.

4. Jeśli *X* polu nagłówka wynosi 1, bajty kodu unwind następują informacje o program obsługi wyjątku. Składa się z jednego *RVA obsługi wyjątków* zawierający adres aparatu obsługi wyjątków, a następnie od razu (zmiennej długości) ilość danych wymaganych przez program obsługi wyjątków.

Rekord .xdata jest zaprojektowana tak, że istnieje możliwość pobrania pierwsze 8 bajtów i obliczeń w pełnym rozmiarze rekordu, nie wliczając długość dane o zmiennym rozmiarze wyjątku, który następuje po. Ten fragment kodu oblicza rozmiar rekordu:

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

Athough prologu i epilogu każdy ma indeks kody unwind, tabela jest współużytkowana przez je. Nie jest niczym niezwykłym, że wszystkie udostępniają te same kody unwind. Zaleca się, że twórcom kompilatorów zoptymalizować dla tego przypadku, ponieważ największego indeksu, który może być określony wynosi 255 i który ogranicza łączną liczbę kodów unwind możliwe dla danej funkcji.

### <a name="unwind-codes"></a>Kodów odwinięcia

Tablica kodów odwijania jest pulę sekwencje instrukcji, które opisują dokładnie, jak cofnąć skutki prologu, w kolejności, w którym musi zostać cofnięta operacji. Kody unwind to zestaw instrukcji mini zakodowany jako ciąg bajtów. Po zakończeniu wykonywania adres zwrotny wywołania funkcji znajduje się w rejestrze LR, a wszystkie rejestrów trwałej zostaną przywrócone do ich wartości w czasie, gdy wywołana została funkcja.

Jeśli wyjątki były gwarantowane tylko nigdy nie występuje w treści funkcji, i nigdy nie znajduje się w prologu i epilogu, następnie tylko jedna operacja unwind sekwencji będzie to konieczne. Model odwijania Windows wymaga jednak możliwość rozwijają się od w częściowo wykonane prologu i epilogu. Aby spełnić to wymaganie, kody unwind staranne wyznaczone do ma jednoznaczną mapowanie jeden do jednego do każdego odpowiedni kod operacji w prologu i epilogu. To ma wpływ kilka:

- Istnieje możliwość obliczenia długość prologu i epilogu przez liczenie kodów unwind. Jest to możliwe nawet w przypadku instrukcji Thumb-2 o zmiennej długości, ponieważ istnieją mapowania odrębne dla rozkazów 16-bitowe i 32-bitowych.

- Przez liczenie instrukcji po uruchomieniu zakresu epilogu, jest możliwe, aby pominąć równoważną liczbę kodów unwind i wykonania pozostałej części sekwencji, aby ukończyć częściowo wykonywane unwind działał epilogu.

- Przez liczenie instrukcji przed zakończeniem prologu, jest możliwe, aby pominąć równoważną liczbę kodów unwind i wykonania pozostałej części sekwencji, aby cofnąć tylko te części prologu, które zostaną ukończone.

W poniższej tabeli przedstawiono mapowanie kody unwind rozkazów. Najbardziej typowe kody są tylko jednego bajtu, podczas gdy mniej typowe te wymagają dwóch, trzech lub nawet czterech bajtów. Każdy kod znajduje się od najbardziej znaczącego bajtu najmniej znaczący bajt. Struktura kodu unwind różni się od kodowania, opisanego w ARM EABI, ponieważ te kody unwind mają mieć mapowanie jeden do jednego na rozkazów w prologu i epilogu, aby umożliwić odwijanie z częściowo wykonane prologues i epilogues.

|1 bajt|Bajt 2|Bajt 3|4 bajtów|Opsize|Wyjaśnienie|
|------------|------------|------------|------------|------------|-----------------|
|00 7F||||16|`add   sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x7F) \* 4|
|80 BF|00 DO FF|||32|`pop   {r0-r12, lr}`<br /><br /> gdzie jest zdejmowany LR, jeśli kod i 0x2000 i r0 r12 są zdjęte ze stosu jeśli odnośny bit jest ustawiony w 0x1FFF & kodu|
|C0 CF||||16|`mov   sp,rX`<br /><br /> gdzie X jest 0x0F & kodu|
|D0 D7||||16|`pop   {r4-rX,lr}`<br /><br /> gdzie X jest (kod & 0x03) + 4 i LR jest zdejmowany, jeśli 0x04 & kodu|
|D8 DF||||32|`pop   {r4-rX,lr}`<br /><br /> gdzie X jest (kod & 0x03) + 8 i LR jest zdejmowany, jeśli 0x04 & kodu|
|E0 E7||||32|`vpop  {d8-dX}`<br /><br /> gdzie X jest (kod & 0x07) + 8|
|E8 EB|00 DO FF|||32|`addw  sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x03FF) \* 4|
|WE ED|00 DO FF|||16|`pop   {r0-r7,lr}`<br /><br /> gdzie jest zdejmowany LR, jeśli kod & 0x0100 i r0 r7 są zdjęte ze stosu jeśli odnośny bit jest ustawiony w 0x00FF & kodu|
|EE|00 0F|||16|specyficzne dla firmy Microsoft|
|EE|10-FF|||16|Dostępne|
|EF|00 0F|||32|`ldr   lr,[sp],#X`<br /><br /> gdzie X jest (kod & 0x000F) \* 4|
|EF|10-FF|||32|Dostępne|
|F0 F4||||-|Dostępne|
|F5|00 DO FF|||32|`vpop  {dS-dE}`<br /><br /> gdzie S jest (kod & 0x00F0) >> 4 i E jest 0x000F & kodu|
|F6|00 DO FF|||32|`vpop  {dS-dE}`<br /><br /> gdzie jest S ((Code & 0x00F0) >> 4) + 16 i E jest (kod & 0x000F) + 16|
|F7|00 DO FF|00 DO FF||16|`add   sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x00FFFF) \* 4|
|F8|00 DO FF|00 DO FF|00 DO FF|16|`add   sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x00FFFFFF) \* 4|
|F9|00 DO FF|00 DO FF||32|`add   sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x00FFFF) \* 4|
|FA|00 DO FF|00 DO FF|00 DO FF|32|`add   sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x00FFFFFF) \* 4|
|PLATFORMY FB||||16|NOP (16-bitowy)|
|FC||||32|NOP (32-bitowy)|
|FD||||16|End + nop 16-bitowych w epilogu|
|FE||||32|End + nop 32-bitowych w epilogu|
|FF||||-|end|

Ten element pokazuje zakres wartości szesnastkowe poszczególne bajty kodu unwind *kodu*, wraz z rozmiarem opcode *Opsize* i odpowiednie oryginalnego interpretację instrukcji. Puste komórki wskazują krótszy kody unwind. W instrukcji, które mają duże wartości obejmujących wiele bajtów najbardziej znaczące bity są przechowywane najpierw. *Opsize* pole zawiera rozmiar niejawne opcode skojarzony z każdej operacji Thumb-2. Jawnego zduplikowane wpisy w tabeli z różnych kodowań są używane do rozróżnienia opcode różnych rozmiarów.

Kody unwind zaprojektowano tak, aby pierwszy bajt kodu informuje całkowity rozmiar w bajtach, kodu i rozmiar odpowiedni kod operacji w usłudze stream instrukcji. Do obliczenia rozmiaru prologu i epilogu, szczegółowe kody odwijanie od samego początku sekwencji do końca, a następnie użyj tabeli odnośników lub podobnej metody, aby ustalić, ile jest odpowiedni kod operacji.

0xFD kodów odwinięcia i 0xFE są równoważne kod zakończenia regularne 0xFF, ale konto dla jednego opcode nop dodatkowego w tym przypadku epilogu 16-bitowe czy 32-bitowe. W przypadku prologues kody 0xFD, 0xFE i 0xFF są równoważne. To konta dla typowych końce epilogu `bx lr` lub `b <tailcall-target>`, które nie mają instrukcję prologu równoważne. Dzięki temu rośnie ryzyko, że operacja unwind sekwencji mogą być współużytkowane między prologu i epilogues.

W wielu przypadkach należy można użyć tego samego zestawu unwind kodów prologu i epilogues wszystkich. Aby obsłużyć odwijanie prologues częściowo wykonane i epilogues, może być mieć wiele unwind sekwencji kodu, które różnią się w kolejności lub zachowania. Jest to, dlaczego epilogu każdy ma własny indeks w tablicy odwijania, aby pokazać, gdzie rozpocząć wykonywanie skryptu.

### <a name="unwinding-partial-prologues-and-epilogues"></a>Odwijania Prologues częściowe i Epilogues

Najbardziej typowych przypadków odwijania jest, gdy wystąpi wyjątek w treści funkcji, od prologu i wszystkie epilogues. W takim przypadku unwinder wykonuje kody w tablicy unwind zaczynając od indeksu 0 i jest kontynuowane, dopóki nie zostanie wykryty kod zakończenia operacji.

Gdy wystąpi wyjątek podczas prologu i epilogu jest wykonywany, ramka stosu jest tylko częściowo wykonane, a unwinder musi określić dokładnie co zostało zrobione w celu poprawnie cofnąć tę operację.

Na przykład należy wziąć pod uwagę tę sekwencję prologu i epilogu:

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

Obok każdego opcode jest kodem unwind odpowiednie do opisywania tej operacji. Sekwencja unwind kodów prologu jest obraz lustrzany kody unwind epilogu, nie licząc zamykającego instrukcja końcowa. Ten przypadek jest wspólnego i powodów, dla którego unwind kodów prologu są zawsze zakłada się, że można przechowywane w odwrotnej kolejności niż kolejność wykonywania prologu. To daje nam wspólny zestaw kodów unwind:

```asm
0xc7, 0xdd, 0x04, 0xfd
```

Kod 0xFD jest specjalny kod dla elementu end sekwencji, która oznacza, że epilogu jest dłuższa niż prologu jednej instrukcji 16-bitowych. Umożliwia większą udostępnianie kodów unwind.

W przykładzie Jeśli wystąpi wyjątek podczas wykonywania treść funkcji między prologu i epilogu odwijania rozpoczyna się od epilogu zamierzone, Zapisz, przy przesunięciu 0 kodem epilogu. Odpowiada to przesunięcie 0x140 w przykładzie. Unwinder wykonuje sekwencję pełne rozwinięcie, ponieważ nie została wykonana żadne oczyszczanie. Zamiast pojedynczej instrukcji po rozpoczęciu kod epilogu wystąpi wyjątek, unwinder może pomyślnie operacji unwind przez pominięcie pierwszy kod unwind. Biorąc pod uwagę mapowanie jeden do jednego między rozkazów i unwind kodów, jeśli odwijanie od instrukcji *n* w epilogu unwinder należy pominąć pierwszy *n* kodów odwinięcia.

Podobnej logiki działa w odwrotnej kolejności dla prologu. Odwijanie od przesunięcia 0 w prologu, nic nie musi być wykonywane. Jeśli odwijanie od jednej instrukcji w, sekwencji unwind należy uruchomić jeden kod unwind od końca, ponieważ prologu unwind kody są przechowywane w odwrotnej kolejności. W przypadku ogólnych, jeśli odwijanie od instrukcji *n* w prologu, odwijanie powinien rozpocząć wykonywanie w *n* kodów od końca listy kodów odwinięcia.

Kody unwind prologu i epilogu nie zawsze dokładnie. W takim przypadku unwind tablicy kod może być zawierać kilka sekwencje kodów. Aby określić przesunięcie, aby rozpocząć przetwarzanie kodów, użyj tej logiki:

1. Jeśli odwijanie od w treści funkcji, rozpoczyna się ich wykonywanie kody unwind pod indeksem 0, aż do osiągnięcia kod zakończenia operacji.

2. Jeśli odwijanie od w ramach epilogu, należy użyć konkretnego epilogu indeks początkowy dostarczone przez zakres epilogu. Obliczyć liczbę bajtów komputera od początku epilogu. Przeskocz do przodu za pomocą kodów unwind dopóki wszystkie instrukcje już wykonywane są rozliczane. Wykonaj sekwencję unwind uruchamianie w tym momencie.

3. Jeśli odwijanie od w prologu, należy uruchomić z indeksu od 0 do kodów unwind. Obliczają długość kodu prologu z sekwencji, a następnie obliczyć liczbę bajtów komputer jest na końcu prologu. Przeskocz do przodu za pomocą kodów unwind dopóki wszystkie instrukcje cofnąć są rozliczane. Wykonaj sekwencję unwind uruchamianie w tym momencie.

Rozwinięcie kodów prologu zawsze musi być pierwszym w tablicy. Są one również kody używane na odpoczynek generalnie w przypadku odwijanie od treści. Istnienie sekwencji kodu specyficznego dla epilogu należy stosować bezpośrednio po sekwencji kodu prologu.

### <a name="function-fragments"></a>Funkcja fragmentów

Optymalizacji kodu może być przydatne do podziału funkcji na części niesąsiadujących ze sobą. Po zakończeniu tej operacji poszczególne fragmenty funkcja wymaga własnej oddzielnych .pdata — i prawdopodobnie .xdata — rekord.

Przy założeniu, że prologu funkcji znajduje się na początku funkcji i nie można podzielić, istnieją cztery przypadków fragmentu funkcji:

- Prologu. wszystkie epilogues w innych fragmentach.

- Prologu i co najmniej jeden epilogues; dodatkowe epilogues w innych fragmentach.

- Brak prologu lub epilogues; prologu i co najmniej jeden epilogues w innych fragmentach.

- Epilogues. prologu, a także ewentualne dodatkowe epilogues w innych fragmentach.

W pierwszym przypadku należy opisać tylko prologu. Można to zrobić w postaci compact .pdata zwykle opisujące prologu i określając *Ret* wartość 3, aby wskazać nie epilogu. W formularzu pełną .xdata można to zrobić, podając kody unwind prologu pod indeksem 0 w zwykły sposób i określając epilogu liczba 0.

Drugi przypadek jest podobne do normalnej funkcji. Jeśli istnieje tylko jeden epilogu we fragmencie i jest na końcu tego fragmentu, następnie rekord compact .pdata może służyć. W przeciwnym razie należy użyć rekordu pełną .xdata. Należy pamiętać, będące przesunięcia określony na potrzeby start epilogu względem początku fragmentu, a nie oryginalnego początku funkcji.

Trzecia i czwarta przypadków są wariantów przypadków pierwszego i drugiego, z wyjątkiem nie zawierają one prologu. W takich sytuacjach zakłada się, że ma kodu przed rozpoczęciem epilogu i jest on uznawany za część treści funkcji, która będzie można normalnie odwinięty wycofując skutki prologu. Te przypadki, w związku z tym musi być zakodowany za pomocą pseudo-prologu, w którym opisano sposób operacji unwind z w ramach treści, ale która jest traktowana jako 0-length podczas ustalania, czy ma być przeprowadzane częściowym unwind na początku tego fragmentu. Alternatywnie to pseudo-prologu mogą być opisane przy użyciu tych samych kodów unwind jako epilogu, ponieważ prawdopodobnie wykonują operacje równoważne.

W przypadku trzecia i czwarta obecności pseudo-prologu jest określona przez ustawienie *flagi* pola rekordu compact .pdata na 2 lub poprzez skonfigurowanie *F* flagi w nagłówku .xdata 1. W obu przypadkach wyboru unwind częściowe prologu jest ignorowany i rozwija wszystkie inne niż epilogu są uznawane za pełną.

#### <a name="large-functions"></a>Duże funkcje

Fragmenty mogą służyć do opisu funkcji przekracza limit 512 KB określonych przez pola bitowe w nagłówku .xdata. Aby opisać bardzo dużych funkcji, po prostu podzielenie go na fragmenty mniejsze niż 512 KB. Każdy fragment należy dostosować tak, aby nie podzielona epilogu do wielu fragmentów.

Tylko pierwszy fragment funkcji zawiera prologu; wszystkie inne fragmenty są oznaczone jako mające nie prologu. W zależności od liczby epilogues każdy fragment może zawierać zero lub więcej epilogues. Należy pamiętać, że zakres epilogu każdego fragmentu określa ich początkowe przesunięcie względem początku fragmentu, a nie na początku funkcji.

Jeśli fragment nie prologu i epilogu nie, nadal wymaga własnej .pdata — i prawdopodobnie .xdata — rekord opisano, jak rozwijają się od w treści funkcji.

#### <a name="shrink-wrapping"></a>Shrink-wrapping

Jest szczególnym przypadkiem bardziej złożonych funkcji fragmenty *shrink-wrapping*, technika odkładania rejestru zapisuje od samego początku funkcji do funkcji, zoptymalizowane pod kątem prostego przypadki, które nie wymagają zapisywanie w rejestrze w dalszej części. To można opisać jako zewnętrzne region, przydziela miejsce stosu, która zapisuje to minimalny zestaw rejestrów, a wewnętrzny region, która zapisuje i przywraca dodatkowe rejestry.

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

Funkcje porządnie zapakowane są zwykle wstępnie przydziel miejsce dla dodatkowych rejestru są zapisywane w regularnych prologu i następnie wykonać zapisuje rejestr przy użyciu `str` lub `stm` zamiast `push`. Dzięki temu wszystkie manipulacje wskaźnik stosu w oryginalnym prologu funkcji.

Przykład funkcja porządnie zapakowane muszą być podzielone w trzech regionach, które są oznaczone jako A, B i C w komentarzach. Najpierw region obejmuje początku funkcji do końca dodatkowe zapisuje trwałej. Do opisania ten fragment w dziedzinie prologu i nie epilogues, muszą być zbudowane rekord .pdata i .xdata.

W regionie bliski B pobiera swój własny rekord .pdata i .xdata, który opisuje fragment, który ma nie prologu i epilogu nie. Jednak nadal musi być obecny kody unwind dla tego obszaru, ponieważ zakłada się treści funkcji. Kody muszą zawierać opis złożonego prologu, reprezentujący oryginalny rejestrów zapisane w prologu region A i dodatkowe rejestry zapisane przed wejściem region B, tak, jakby zostały wyprodukowane przez jednej sekwencji operacji.

Zapisuje rejestru dla regionu, w których B nie należy traktować jako "prologu wewnętrzny", ponieważ złożonego prologu opisane dla regionu B musi opisywać zarówno prologu region A, jak i dodatkowych rejestrów zapisane. Jeśli fragment B została opisana w dziedzinie prologu, kody unwind również oznaczałoby rozmiar tego prologu i nie ma możliwości do opisania złożonego prologu w sposób, który mapuje jeden do jednego z rozkazów, który tylko zapisać dodatkowe rejestry.

Zapisuje dodatkowe rejestrowanie musi je traktować jako część A, region, ponieważ dopiero po ich zakończeniu złożonego prologu niedokładnie opisuje stanu stosu.

Ostatniego regionu C pobiera swój własny rekord .pdata i .xdata, zawierająca opis fragmentu, który ma nie prologu, ale mają epilogu.

Alternatywnym podejściem może również współpracować, jeśli stosem wykonać przed rozpoczęciem wprowadzania region B, można zmniejszyć do pojedynczej instrukcji:

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

Tutaj klucz jest, czy w każdej granicy rozkazu stosu jest w pełni zgodna z kodami unwind dla regionu. Jeśli odwijania wystąpi przed wewnętrzny powiadomienia wypychane w tym przykładzie, jest on uznawany za część region A, a tylko regionu prologu jest rozwinięty. Sytuacji unwind po wewnętrzny wypychania uważa się, że część B, który ma nie prologu, ale ma kody odwijania, które opisują wewnętrzny wypychania i oryginalnego prologu z regionu A. podobnej logiki w regionie odnosi się do wewnętrznego pop.

### <a name="encoding-optimizations"></a>Optymalizacja kodowania

Z powodu bogactwa kodów unwind i możliwość kompaktowania Wykorzystaj i rozwiniętej rodzaje danych istnieje wiele okazji do promowania Optymalizacja kodowania, aby jeszcze bardziej ograniczyć miejsce. Agresywne użycia tych metod net obciążenie związane z opisem funkcji i fragmenty za pomocą kodów unwind może być całkiem mały.

Najważniejsze optymalizacji jest należy zachować ostrożność nie należy mylić granice prologu/epilogu celów odwijania z logiczną prologu/epilogu granice z punktu widzenia kompilatora. Granice odwijania można zmniejszyć i wprowadzone większego w celu poprawy wydajności. Na przykład prologu może zawierać kod po sprawdza, czy Instalator stosu do przeprowadzenia dodatkowej weryfikacji. Jednak po ukończeniu wszystkich stosem nie ma potrzeby do zakodowania dalszych operacji i niczego poza tym może zostać usunięty z odwijania prologu.

Zostanie zastosowana ta reguła tej samej długości funkcji. Jeśli ma danych — na przykład, literał puli — następujący epilogu funkcji, nie może być dołączane jako część długości funkcji. Zmniejszanie funkcji, aby tylko kod, który jest częścią funkcji, szanse są znacznie większe, że na końcu i compact będzie epilogu. możliwość użycia rekordu PData.

W prologu po zapisaniu wskaźnik stosu do innego rejestru, ma zwykle nie trzeba rejestrować wszelkie dalsze rozkazów. Na odpoczynek, funkcji, pierwszą rzeczą, jaka została wykonana jest odzyskanie SP z rejestru zapisane, a więc dalszych operacji nie ma żadnego wpływu na unwind.

Epilogues pojedynczych instrukcji nie ma być zakodowany jako zakresów w ogóle lub jako kodów odwinięcia. Jeśli rozwinięcie odbywa się przed wykonaniem tej instrukcji, a może być zakłada się od w treści funkcji, wystarczy po prostu wykonywanie kody unwind prologu. Jeśli rozwinięcie odbywa się po wykonaniu pojedynczej instrukcji, następnie zgodnie z definicją jej odbywa się w innym regionie.

Nie trzeba kodować pierwsza instrukcja epilogu, z tego samego powodu jako poprzedniego punktu epilogues wielu instrukcji: Jeśli rozwinięcie odbywa się przed wykonaniem tej instrukcji, unwind pełną prologu jest wystarczająca. Jeśli rozwinięcie odbywa się po tej instrukcji, a następnie tylko kolejne operacje powinny być traktowane.

Kodzie operacji unwind ponownego użycia powinny być agresywne. Indeks określony przez poszczególnych punktów zakresu epilogu do dowolnego punktu początkowego w tablicy kodów unwind. Nie ma punktu na początku sekwencji poprzedniej; może wskazywać na środku. Najlepszym rozwiązaniem jest generowanie kolejny odpowiedni kod i następnie wyszukiwać dopasowania dokładne bajtów w puli już zaszyfrowana sekwencji i użyj dowolnego doskonałe dopasowanie jako punktu wyjścia do ponownego użycia.

Jeśli po epilogues pojedynczych instrukcji są ignorowane, nie istnieją żadne pozostałe epilogues należy wziąć pod uwagę przy użyciu formularza compact .pdata; staje się znacznie bardziej prawdopodobne w przypadku braku epilogu.

## <a name="examples"></a>Przykłady

W tych przykładach podstawowy obraz wynosi 0x00400000.

### <a name="example-1-leaf-function-no-locals"></a>Przykład 1: Liścia funkcji nie zmiennych lokalnych

```asm
Prologue:
  004535F8: B430      push        {r4-r5}
Epilogue:
  00453656: BC30      pop         {r4-r5}
  00453658: 4770      bx          lr
```

.PData (2 wyrazy stałe):

- Word 0

   - *Początek funkcji RVA* = 0x000535F8 (= 0x004535F8 0x00400000)

- Word 1

   - *Flaga* = 1, wskazujący canonical formaty prologu i epilogu

   - *Funkcja długość* = 0x31 (= 0x62/2)

   - *RET* = 1, wskazujący zwracany gałęzi 16-bitowych

   - *H* = 0, wskazując parametry nie zostały umieszczone.

   - *R*= 0 i *Reg* = 1, wskazujący wypychane/pop o r4 r5

   - *L* = 0, co oznacza nie LR zapisać/przywrócić

   - *C* = 0, co oznacza nie łańcucha ramki

   - *Stack — Dostosuj* = 0, co oznacza nie dopasowania stosu

### <a name="example-2-nested-function-with-local-allocation"></a>Przykład 2: Zagnieżdżonej funkcji przy użyciu lokalnego alokacji

```asm
Prologue:
  004533AC: B5F0      push        {r4-r7, lr}
  004533AE: B083      sub         sp, sp, #0xC
Epilogue:
  00453412: B003      add         sp, sp, #0xC
  00453414: BDF0      pop         {r4-r7, pc}
```

.PData (2 wyrazy stałe):

- Word 0

   - *Początek funkcji RVA* = 0x000533AC (= 0x004533AC-0x00400000)

- Word 1

   - *Flaga* = 1, wskazujący canonical formaty prologu i epilogu

   - *Funkcja długość* = 0x35 (= 0x6A/2)

   - *RET* = 0, co oznacza punkt pop {komputera} zwrotu

   - *H* = 0, wskazując parametry nie zostały umieszczone.

   - *R*= 0 i *Reg* = 3, wskazujący wypychane/pop o r4 r7

   - *L* = 1, wskazując LR zapisane/przywrócono

   - *C* = 0, co oznacza nie łańcucha ramki

   - *Dostosowanie stosu* = 3 (= 0x0C/4)

### <a name="example-3-nested-variadic-function"></a>Przykład 3: Zagnieżdżonej funkcji ze zmienną liczbą argumentów

```asm
Prologue:
  00453988: B40F      push        {r0-r3}
  0045398A: B570      push        {r4-r6, lr}
Epilogue:
  004539D4: E8BD 4070 pop         {r4-r6}
  004539D8: F85D FB14 ldr         pc, [sp], #0x14
```

.PData (2 wyrazy stałe):

- Word 0

   - *Początek funkcji RVA* = 0x00053988 (= 0x00453988 0x00400000)

- Word 1

   - *Flaga* = 1, wskazujący canonical formaty prologu i epilogu

   - *Funkcja długość* = 0x2A (= 0x54/2)

   - *RET* = 0, co oznacza pop {komputera}-stylu return (w tym przypadku pc ldr [sp] #0x14 return)

   - *H* = 1, wskazując parametry zostały umieszczone

   - *R*= 0 i *Reg* = 2, wskazujący wypychane/pop o r4 r6

   - *L* = 1, wskazując LR zapisane/przywrócono

   - *C* = 0, co oznacza nie łańcucha ramki

   - *Stack — Dostosuj* = 0, co oznacza nie dopasowania stosu

### <a name="example-4-function-with-multiple-epilogues"></a>Przykład 4: Funkcji z wieloma Epilogues

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

.PData (2 wyrazy stałe):

- Word 0

   - *Początek funkcji RVA* = 0x000592F4 (= 0x004592F4 0x00400000)

- Word 1

   - *Flaga* = 0, wskazując istniejącego rekordu .xdata (wymagane ze względu na wiele epilogues)

   - *adres .xdata* -0x00400000

.xdata (zmienna, słowa 6):

- Word 0

   - *Funkcja długość* = 0x0001A3 (= 0x000346/2)

   - *Sterowniki* = 0, co oznacza pierwszą wersję xdata

   - *X* = 0, co oznacza nie dane wyjątku

   - *E* = 0, co oznacza listę zakresów epilogu

   - *F* = 0, co oznacza opis pełne działanie, w tym prologu

   - *Liczba epilogu* = 0x04, wskazujący 4 zakresy całkowita epilogu

   - *Wyrazy kodu* = 0x01, wskazując jedno słowo w 32-bitowych kodów unwind

- Wyrazy 1 – 4 opisujące 4 zakresy epilogu w lokalizacjach 4. Każdego zakresu ma wspólny zestaw kodów odwijania, udostępnione prologu, przesunięciem 0x00 i bezwarunkowe, określając warunek 0x0E (zawsze).

- Operacja unwind kodów, zaczynając od 5 do programu Word: (udostępniane między prologu/epilogu)

   - Wartość 0 = 0x06 kodzie operacji unwind: sp += (6 << 2)

   - 1 = 0xDE kodzie operacji unwind: pop {r4 r10, lr}

   - 2 = 0xFF kodzie operacji unwind: koniec

### <a name="example-5-function-with-dynamic-stack-and-inner-epilogue"></a>Przykład 5: Funkcja dynamicznej stosu i epilogu wewnętrzny

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

.PData (2 wyrazy stałe):

- Word 0

   - *Początek funkcji RVA* = 0x00085A20 (= 0x00485A20 0x00400000)

- Word 1

   - *Flaga* = 0, wskazując istniejącego rekordu .xdata (wymagane ze względu na wiele epilogues)

   - *adres .xdata* -0x00400000

.xdata (zmienna, słowa 3):

- Word 0

   - *Funkcja długość* = 0x0001A3 (= 0x000346/2)

   - *Sterowniki* = 0, co oznacza pierwszą wersję xdata

   - *X* = 0, co oznacza nie dane wyjątku

   - *E* = 0, co oznacza listę zakresów epilogu

   - *F* = 0, co oznacza opis pełne działanie, w tym prologu

   - *Liczba epilogu* = 0x001, wskazujący 1 zakres całkowita epilogu

   - *Wyrazy kodu* = 0x01, wskazując jedno słowo w 32-bitowych kodów unwind

- Word 1: Epilogu zakresu przesunięciem 0xC6 (= 0x18C/2), od indeksu kodu unwind na 0x00 i z warunkiem 0x0E (zawsze)

- Operacja unwind kodów, począwszy od programu Word 2: (udostępniane między prologu/epilogu)

   - 0 = 0xC6 kodzie operacji unwind: sp = r6

   - 1 = 0xDC kodzie operacji unwind: pop {r4 r8, lr}

   - 2 = 0x04 kodzie operacji unwind: sp += (4 << 2)

   - 3 = 0xFD kodzie operacji unwind: koniec traktowany jak 16-bitowych instrukcję epilogu

### <a name="example-6-function-with-exception-handler"></a>Przykład 6: Funkcja z obsługą wyjątków

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

.PData (2 wyrazy stałe):

- Word 0

   - *Początek funkcji RVA* = 0x00088C24 (= 0x00488C24 0x00400000)

- Word 1

   - *Flaga* = 0, wskazując istniejącego rekordu .xdata (wymagane ze względu na wiele epilogues)

   - *adres .xdata* -0x00400000

.xdata (zmienna, 5 słów):

- Word 0

   - *Funkcja długość* = 0x000027 (= 0x00004E/2)

   - *Sterowniki* = 0, co oznacza pierwszą wersję xdata

   - *X* = 1, wskazując obecny dane wyjątku

   - *E* = 1, wskazujący pojedynczego epilogu

   - *F* = 0, co oznacza opis pełne działanie, w tym prologu

   - *Liczba epilogu* = 0x00, wskazujący, kody unwind epilogu rozpoczynają się od przesunięcia 0x00

   - *Wyrazy kodu* = 0x02, wskazując dwa wyrazy 32-bitowych kodów unwind

- Operacja unwind kodów, zaczynając od 1 do programu Word:

   - 0 = 0xC7 kodzie operacji unwind: sp = r7

   - 1 = 0x05 kodzie operacji unwind: sp += (5 << 2).

   - 2 = 0xED/0x90 kodzie operacji unwind: pop {r4, r7, lr}

   - 4 = 0xFF kodzie operacji unwind: koniec

- Word 3 Określa program obsługi wyjątku = 0x0019A7ED (= 0x0059A7ED - 0x00400000)

- Wyrazy 4 i nowszych są dane o wyjątkach śródwierszowych

### <a name="example-7-funclet"></a>Przykład 7: polecenie Funclet

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

.PData (2 wyrazy stałe):

- Word 0

   - *Początek funkcji RVA* = 0x00088C72 (= 0x00488C72 0x00400000)

- Word 1

   - *Flaga* = 1, wskazujący canonical formaty prologu i epilogu

   - *Funkcja długość* = 0x0B (= 0x16/2)

   - *RET* = 0, co oznacza punkt pop {komputera} zwrotu

   - *H* = 0, wskazując parametry nie zostały umieszczone.

   - *R*= 0 i *Reg* = 7, wskazujący brak rejestrów zostały zapisać/przywrócić

   - *L* = 1, wskazując LR zapisane/przywrócono

   - *C* = 0, co oznacza nie łańcucha ramki

   - *Stack — Dostosuj* = 1, wskazujący 1 dostosowanie stosu × 4 bajtów

## <a name="see-also"></a>Zobacz także

[Przegląd konwencji ABI ARM](../build/overview-of-arm-abi-conventions.md)<br/>
[Typowe problemy przy migracji Visual C++ ARM](../build/common-visual-cpp-arm-migration-issues.md)
