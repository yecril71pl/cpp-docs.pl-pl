---
title: "Obsługa wyjątków ARM | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: fe0e615f-c033-4ad5-97f4-ff96af45b201
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 803e4e0556026eaa5a3fb75c8faa7fd87f34052f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="arm-exception-handling"></a>Obsługa wyjątków ARM
System Windows na ARM używa tego samego wyjątków strukturalnych obsługę mechanizmem asynchroniczne wyjątki generowane przez sprzęt i synchroniczne wyjątki generowane przez oprogramowanie. Programy obsługi wyjątków specyficzne dla języka są wbudowane obsługi przy użyciu funkcji języka pomocnika wyjątków strukturalnych systemu Windows. W tym dokumencie opisano obsługi wyjątków w systemu Windows na ARM i pomocników języka używany przez kod, który jest generowany przez MASM i kompilatora języka Visual C++.  
  
## <a name="arm-exception-handling"></a>Obsługa wyjątków ARM  
 Korzysta z systemu Windows na ARM *unwind kodów* do sterowania odwijanie stosu podczas [Obsługa wyjątków strukturalnych](http://msdn.microsoft.com/library/windows/desktop/ms680657) (SEH). Unwind kody są sekwencję bajtów przechowywanych w sekcji .xdata obrazu wykonywalnego. Opisują operacji kod prologu i epilogu funkcji abstrakcyjnej sposób, aby skutków prologu funkcji można odwrócić w ramach przygotowania do rozwinięcia do obiektu wywołującego ramki stosu.  
  
 EABI ARM (interfejs binarnych osadzonego aplikacji) Określa kody operacji unwind odwijaniem model wyjątków, na którym jest używana, ale nie jest wystarczająca do rozwinięcia SEH w systemie Windows musi obsługiwać asynchroniczne przypadki, w którym procesor jest w trakcie prologu lub epilogu funkcji. Windows oddziela również odwijaniem sterowanie na poziomie funkcji rozwinięcia i zakresu specyficzny dla języka rozwinięcia, jest unified w ARM EABI. Z tego względu systemu Windows na ARM określa szczegółowe odwijaniem danych i procedury.  
  
### <a name="assumptions"></a>Założenia  
 Obrazy wykonywalne dla systemu Windows na ARM formacie przenośnego pliku wykonawczego (PE). Aby uzyskać więcej informacji, zobacz [PE firmy Microsoft i specyfikacja COFF](http://go.microsoft.com/fwlink/p/?linkid=84140). Wyjątek obsługi informacji znajduje się w sekcji .pdata i .xdata obrazu.  
  
 Obsługa mechanizmu wyjątków sprawia, że pewne założenia dotyczące kodu znajdujący się na ARM ABI dla systemu Windows:  
  
-   Po wystąpieniu wyjątku w treści funkcji, nie ma znaczenia, czy operacje prologu są cofnąć lub epilogu operacje są wykonywane w sposób przekazywania. Oba powinny być identyczne wyniki.  
  
-   Prologues i epilogues zazwyczaj dublować. Może to służyć do zmniejszyć rozmiar metadane wymagane do opisywania rozwinięcia.  
  
-   Funkcje często być stosunkowo mały. Kilka optymalizacji zależne to efektywne pakowania danych.  
  
-   Warunek jest umieszczony na epilogu, stosuje jednakowo do każdej instrukcji w epilogu.  
  
-   Jeśli wskaźnik stosu (SP) jest zapisana w innym rejestru w prologu, które rejestru musi pozostać bez zmian w całej funkcji, dzięki czemu oryginalne SP może odzyskać w dowolnej chwili.  
  
-   O ile PS jest zapisywany w rejestrze innego manipulowania wszystkie jego musi wystąpić wyłącznie w prologu i epilogu.  
  
-   Cofnąć wszystkie ramki stosu, wymagane są następujące operacje:  
  
    -   Dostosuj r13 (SP1) w przyrostach 4-bajtowych.  
  
    -   POP jedną lub więcej całkowitą rejestrów.  
  
    -   POP co najmniej jeden VFP (wirtualny zmiennoprzecinkowe) rejestruje.  
  
    -   Kopiuj wartość rejestru dowolnego do r13 (SP).  
  
    -   Załaduj SP ze stosu przy użyciu małych operacji dekrementacji po.  
  
    -   Jeden z kilku typów ramki dobrze zdefiniowany przeanalizować.  
  
### <a name="pdata-records"></a>rejestruje .pdata  
 Rekordy .pdata w obrazie środowiska Preinstalacyjnego formatu są uporządkowane tablicę elementów o stałej długości, które opisują co funkcja manipulowanie stosu. Funkcje typu liść, które są funkcje, które nie wymagają innych funkcji, nie wymagają rekordów .pdata podczas ich stosu nie jest modyfikowany. (Oznacza to, ich nie wymagają żadnych Magazyn lokalny i nie ma do zapisania lub przywrócenia rejestrów trwałej). Rejestruje dla tych funkcji można pominąć, z sekcji .pdata, aby zaoszczędzić miejsce. Operacji unwind z jednego z tych funkcji można po prostu skopiuj adres zwrotny z łącza Zarejestruj (LR) do licznik programu (komputer), aby przenieść do obiektu wywołującego.  
  
 Każdy rekord .pdata dla ARM jest 8 bajtów. Ogólny format rekordu umieszcza wirtualny adres względny (RVA) początku funkcji w pierwsze słowo 32-bitowy, następuje drugi słowa zawierającego wskaźnik do bloku .xdata o zmiennej długości lub spakowana programu word opisujący kanonicznej funkcji Sekwencja odwijaniem, jak pokazano w poniższej tabeli:  
  
|Przesunięcie programu Word|Bity|Cel|  
|-----------------|----------|-------------|  
|0|0-31|*Funkcja Start RVA* jest RVA 32-bitowych uruchamiania funkcji. Jeśli funkcja zawiera kod przenośny, niski bit ten adres musi być ustawiona.|  
|1|0-1|*Flaga* jest polem 2-bitowe, które wskazuje sposób interpretowania pozostałe 30 bitów drugi Word .pdata. Jeśli *flagi* ma wartość 0, a następnie pozostałe bity formularza *wyjątek informacji RVA* (z niskim dwa bity niejawnie 0). Jeśli *flagi* jest różna od zera, pozostałe bity formularza *spakowane dane operacji Unwind* struktury.|  
|1|2-31|*Informacje o wyjątku RVA* lub *spakowane dane operacji Unwind*.<br /><br /> *Adres RVA informacji wyjątek* adres struktury informacji o zmiennej długości wyjątek, przechowywane w sekcji .xdata. Te dane muszą być wyrównane 4-bajtowych.<br /><br /> *Spakowane dane operacji Unwind* jest skompresowany opis operacje wymagane do rozwijają się od funkcji, przy założeniu w formie kanonicznej. W takim przypadku żaden rekord .xdata jest wymagana.|  
  
### <a name="packed-unwind-data"></a>Spakowane dane operacji Unwind  
 Dla operacji unwind funkcje, których wykonaj prologues i epilogues spakowane w formie kanonicznej opisane poniżej, można danych. To eliminuje potrzebę stosowania rekord .xdata i znacznie ograniczyć miejsce wymagane do świadczenia dane operacji unwind. Canonical prologues i epilogues są przeznaczone do typowych wymagań proste funkcję, która nie wymaga obsługi wyjątków i wykonuje operacje jego instalacji i usuwania w standardowej kolejności.  
  
 W poniższej tabeli przedstawiono format z .pdata rekordu, który ma spakowane unwind danych:  
  
|Przesunięcie programu Word|Bity|Cel|  
|-----------------|----------|-------------|  
|0|0-31|*Funkcja Start RVA* jest RVA 32-bitowych uruchamiania funkcji. Jeśli funkcja zawiera kod przenośny, niski bit ten adres musi być ustawiona.|  
|1|0-1|*Flaga* jest pole 2-bitowe, które ma następujące znaczenie:<br /><br /> -00 = spakowana unwind dane nie zostały użyte; pozostałe bitów wskaż .xdata rekordu.<br />-01 = spakowane dane operacji unwind.<br />-10 = spakowane dane, gdy funkcja przyjęto nie prologu operacji unwind. Jest to przydatne dla opisu fragmenty funkcji, które są nieciągłe z początku funkcji.<br />-11 = zastrzeżone.|  
|1|2-12|*Funkcja długość* jest pole 11-bitowe, które udostępnia długość całą funkcję w bajtach podzielona przez 2. Funkcja jest większy niż 4 KB, zamiast tego należy użyć rekordu .xdata pełna.|  
|1|13-14|*RET* jest polem 2-bitowe, które wskazuje, jak funkcja zwraca:<br /><br /> -00 = Wróć za pośrednictwem protokołu pop {pc} ( *L* bit flagi musi mieć wartość 1 w takim przypadku).<br />-01 = Wróć za pomocą gałęzi 16-bitowych.<br />-10 = Wróć za pomocą gałęzi 32-bitowych.<br />-11 = nie epilogu wcale. Jest to przydatne dla opisu fragmentu nieciągłe — funkcja, która może zawierać tylko prologu, ale których epilogu znajduje się w innym.|  
|1|15|*H* flagi 1-bitowy, która wskazuje, czy funkcja "homes" parametru liczby całkowitej rejestruje (r0 r3), przesyłając je na początku funkcji i zwalnia 16 bajtów stosu przed zwróceniem. (0 = nie home rejestrów, 1 = domach rejestrów.)|  
|1|16-18|*Reg* pola 3-bitową wskazujący indeks ostatniego zapisaniu trwałej rejestru. Jeśli *R* bit ma wartość 0, tylko liczbą całkowitą rejestrów są zapisywane, a następnie muszą należeć do zakresu rN r4, gdzie N jest równy 4 + *Reg*. Jeśli *R* bit ma wartość 1, a następnie rejestruje tylko zmiennoprzecinkowe są zapisywane i muszą należeć do zakresu dN d8, gdzie N jest równy 8 + *Reg*. Specjalne kombinację *R* = 1 i *Reg* = 7 wskazuje, że rejestrów nie zostaną zapisane.|  
|1|19|*R* jest flagą 1-bitowy, która wskazuje, czy są zapisane rejestrów trwałej całkowitą rejestruje (0) lub rejestrów zmiennoprzecinkowych (1). Jeśli *R* jest ustawiona na 1 i *Reg* pole jest ustawione na 7, nie rejestruje trwałej zostały przekazane.|  
|1|20|*L* jest flagi 1-bitowy, która wskazuje, czy funkcja zapisuje/przywracania LR, wraz z innymi rejestrów wskazywanym przez *Reg* pola. (0 = nie zapisać/przywrócić, 1 = czy zapisać/przywrócić.)|  
|1|21|*C* jest flagą 1-bitowy, która wskazuje, czy funkcja zawiera dodatkowe instrukcje dotyczące konfigurowania łańcucha ramki stosu szybkie przejście (1) czy nie (0). Jeśli ten bit jest ustawiona, r11 jest niejawnie dodany do listy zapisane rejestrów trwałej liczby całkowitej. (Zobacz ograniczenia poniżej if *C* flaga jest wykorzystywana.)|  
|1|22-31|*Stack — Dostosuj* jest polem 10-bitowy, wskazującą liczbę bajtów stosu przydzielonych dla tej funkcji, rozdzielonych 4. Jednak tylko wartości między 0x000 0x3F3 może bezpośrednio zakodowany. Funkcje, które przydzielić więcej niż 4044 bajtów stosu musi przy użyciu rekordu .xdata pełna. Jeśli *stosu dostosować* pole jest 0x3F4 lub większych niski 4 bity mają specjalne znaczenie, a następnie:<br /><br /> -Bitowej 0-1 wskazuje liczbę słów korekty stosu (1-4) pomniejszonej o 1.<br />-Bitowych 2 jest równa 1, jeśli prologu połączone dostosowania do swoich operacji wypychania.<br />-Bitowych 3 jest równa 1, jeśli epilogu połączone dostosowania do swoich operacji pop.|  
  
 Z powodu możliwych zwolnienia w powyższym kodowania następujące ograniczenia:  
  
-   Jeśli *C* flaga jest ustawiona na 1:  
  
    -   *L* flagi również musi mieć wartość 1, ponieważ łańcucha ramki wymagane zarówno r11 i LR.  
  
    -   R11 nie może być uwzględniony w zestawie rejestrów opisanego przez *Reg*. Oznacza to, jeśli są usuwane, r4 r11, *Reg* tylko powinna opisać r4 r10, *C* r11 oznacza flagą.  
  
-   Jeśli *Ret* pole jest ustawione na 0, *L* Flaga musi być ustawiona na 1.  
  
 Naruszenie ograniczenia powoduje, że nieobsługiwany sekwencji.  
  
 Do celów opis poniżej, dwie pseudo-flagi pochodzą od *stosu dostosować*:  
  
-   *PF* lub "prologu składania" wskazuje, że *stosu dostosować* jest 0x3F4 lub wartość 2 większych i bit.  
  
-   *EF* lub "epilogu składania" wskazuje, że *stosu dostosować* jest 0x3F4 lub wartość większą i bit 3.  
  
 Prologues kanonicznej funkcji mogą mieć maksymalnie 5 instrukcje (powiadomienie, że 3a i 3b wzajemnie się wykluczają):  
  
|Instrukcja|Kod operacji przyjęto, że istnieje jeśli:|Rozmiar|Kod operacji|Kody unwind|  
|-----------------|-----------------------------------|----------|------------|------------------|  
|1|*H*== 1|16|`push {r0-r3}`|04|  
|2|*C*== 1 lub *L*== 1 lub *R*== 0 lub PF == 1|16/32|`push {registers}`|80-BF/D0-DF/WE ED|  
|3a|*C*== 1 i (*L*== 0 i *R*== 1 i PF == 0)|16|`mov r11,sp`|C0-CF/FB|  
|3b|*C*== 1 i (*L*== 1 lub *R*== 0 lub PF == 1)|32|`add r11,sp,#xx`|FC|  
|4|*R*== 1 i *Reg* ! = 7|32|`vpush {d8-dE}`|E0 E7|  
|5|*Dostosuj stosu* ! = 0 i PF == 0|16/32|`sub sp,sp,#xx`|00-7F/E8-EB|  
  
 Zawsze występuje instrukcja 1 Jeśli *H* bit jest ustawiony na wartość 1.  
  
 Aby skonfigurować tworzenie łańcucha ramki, występuje instrukcja 3a lub 3b Jeśli *C* ustawiono bit. Jest 16-bitowych `mov` Jeśli nie rejestruje inne niż r11 i LR są usuwane; w przeciwnym razie jest 32-bitowa `add`.  
  
 Jeśli określono korekty nie zostało zwinięte, instrukcji 5 to dostosowywanie jawne stosu.  
  
 Instrukcje 2 i 4 są ustawiane na podstawie czy wypychania jest wymagana. Ta tabela zawiera podsumowanie rejestrujący są zapisywane na podstawie *C*, *L*, *R*, i *PF* pola. We wszystkich przypadkach *N* jest równa *Reg* + 4, *E* jest równa *Reg* + 8, i *S* jest równe (~*Dostosować stosu*) i 3.  
  
|C|L|R|PF|Wypychana rejestrów liczba całkowita|Rejestruje VFP wypychana|  
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
  
 Epilogues monitująca funkcji kanonicznej formie podobne, ale odwrotnie, a niektóre dodatkowe opcje. Epilogu może być maksymalnie 5 instrukcje długie i jego formularza jest ściśle zależna formę prologu.  
  
|Instrukcja|Kod operacji przyjęto, że istnieje jeśli:|Rozmiar|Kod operacji|  
|-----------------|-----------------------------------|----------|------------|  
|6|*Dostosuj stosu*! = 0 i *EF*== 0|16/32|`add   sp,sp,#xx`|  
|7|*R*== 1 i *Reg*! = 7|32|`vpop  {d8-dE}`|  
|8|*C*== 1 lub (*L*== 1 i *H*== 0) lub *R*== 0 lub *EF*== 1|16/32|`pop   {registers}`|  
|9a|*H*== 1 i *L*== 0|16|`add   sp,sp,#0x10`|  
|9b|*H*== 1 i *L*== 1|32|`ldr   pc,[sp],#0x14`|  
|10a|*RET*== 1|16|`bx    reg`|  
|10b|*RET*== 2|32|`b     address`|  
  
 Instrukcja 6 to dostosowanie jawne stosu, jeśli określono korekty nie zostało zwinięte. Ponieważ *PF* jest niezależna od *EF*, istnieje możliwość instrukcji 5 obecny bez instrukcji 6 lub na odwrót.  
  
 Instrukcje 7 i 8 używać tej samej logiki jako prologu ustalenie, który rejestruje zostaną przywrócone ze stosu, ale z tych dwóch zmienia: najpierw *EF* jest używany zamiast *PF*; druga, jeśli *Ret*  = 0, a następnie LR jest zastępowany na liście rejestr PC i epilogu kończy się natychmiast.  
  
 Jeśli *H* jest ustawiona, a następnie 9a instrukcji lub 9b jest obecny. 9a instrukcji jest używany podczas *L* ma wartość 0, aby wskazać, że LR nie znajduje się na stosie. W takim przypadku stosu ręcznie jest dostosowana i *Ret* musi wynosić 1 lub 2, aby określić jawne powrotu. 9b instrukcji jest używany podczas *L* 1 wskazują wczesne zakończenie epilogu i aby powrócić i dopasować stosu w tym samym czasie.  
  
 Jeśli epilogu nie już zakończyła, następnie albo instrukcji 10a lub 10b jest obecny, aby wskazać 16-bitowych lub 32-bitowych gałęzi, na podstawie wartości z *Ret*.  
  
### <a name="xdata-records"></a>rejestruje .xdata  
 Format spakowana unwind jest niewystarczający do opisania rozwinięcia funkcji, rekord o zmiennej długości .xdata musi zostać utworzona. Adres tego rekordu są przechowywane w drugiej word rekordu .pdata. Format .xdata jest spakowany o zmiennej długości zestaw wyrazów zawierający cztery sekcje:  
  
1.  Nagłówek 1 lub 2-word opisujący łączny rozmiar struktury .xdata i udostępnia dane funkcji klucza. Drugi wyraz jest obecna tylko, jeśli *liczba epilogu* i *wyrazów* pola są ustawione na 0. Pola są podzielone w tej tabeli:  
  
    |Word|Bity|Cel|  
    |----------|----------|-------------|  
    |0|0-17|*Funkcja długość* jest polem 18-bitowy, wskazującą całkowita długość w bajtach podzielona przez 2 funkcji. Jeśli funkcja jest większy niż 512 KB, wiele rekordów .pdata i .xdata musi można używać do opisywania funkcji. Aby uzyskać więcej informacji zobacz sekcję długie funkcje, w tym dokumencie.|  
    |0|18-19|*Sterowniki* jest pole 2-bitowe, które zawiera opis wersji xdata pozostałych. Obecnie jest zdefiniowana tylko wersję 0; wartości 1 – 3 są zastrzeżone.|  
    |0|20|*X* jest polem 1-bitowy, wskazujący obecności (1) lub dane wyjątku braku (0).|  
    |0|21|*E* jest pola 1-bitowy, która wskazuje, że informacje opisujące pojedynczego epilogu są pakowane w nagłówku (1) zamiast konieczności dodatkowego zakresu wyrazów nowszej (0).|  
    |0|22|*F* jest polem 1-bitowy, który wskazuje, że ten rekord zawiera opis fragmentu — funkcja (1) lub pełne działanie (0). Fragment oznacza prologu nie istnieje i należy ją ignorować wszystkie przetwarzania prologu.|  
    |0|23-27|*Liczba epilogu* jest polem 5-bitowy, która ma dwa znaczenie, w zależności od stanu *E* bitowe:<br /><br /> -Jeśli *E* wynosi 0, to pole jest liczba całkowita liczba zakresów wyjątek opisane w sekcji 3. Jeśli istnieje więcej niż 31 zakresów w funkcję, a następnie to pole i *wyrazów* pole musi jednocześnie być ustawione na 0 Aby wskazać, że rozszerzenia wyraz jest wymagana.<br />-Jeśli *E* 1, to pole określa indeks pierwszego kodu unwind, który opisuje tylko epilogu.|  
    |0|28-31|*Wyrazy kodu* jest polem 4-bitowy, określająca liczbę słów 32-bitowe muszą zawierać wszystkie kody unwind w sekcji 4. Jeśli więcej niż 15 wyrazy są wymagane do więcej niż 63 bajtów kodu unwind, to pole i *liczba epilogu* pole musi jednocześnie być ustawione na 0 Aby wskazać, że rozszerzenia wyraz jest wymagana.|  
    |1|0-15|*Rozszerzony liczba epilogu* jest polem 16-bitowego kodowania niezwykle dużą liczbę epilogues zapewnia więcej miejsca. Rozszerzenia programu word, zawierającym to pole jest obecna tylko, jeśli *liczba epilogu* i *wyrazów* pól w pierwsze słowo nagłówka są ustawione na 0.|  
    |1|16-23|*Rozszerzony wyrazów* jest 8-bitową pola, które zawiera więcej miejsca do kodowania niezwykle dużą liczbę unwind wyrazów. Rozszerzenia programu word, zawierającym to pole jest obecna tylko, jeśli *liczba epilogu* i *wyrazów* pól w pierwsze słowo nagłówka są ustawione na 0.|  
    |1|24-31|Zastrzeżone|  
  
2.  Po dane wyjątku (Jeśli *E* bit w nagłówku został ustawiony na wartość 0) znajduje się lista informacji o zakresach epilogu, które są pakować je do programu word i przechowywane w porządku rosnących początkowe przesunięcie. Każdego zakresu zawiera następujące pola:  
  
    |Bity|Cel|  
    |----------|-------------|  
    |0-17|*Przesunięcie Start epilogu* to pole bitowe 18 opisujący przesunięcie epilogu, w bajtach podzielona przez 2 względem początku funkcji.|  
    |18-19|*Res* to pole bitowe 2 zarezerwowane dla przyszłego rozszerzenia. Jego wartość musi być równa 0.|  
    |20-23|*Warunek* jest polem 4-bitowy, zapewniająca warunku, pod którym jest wykonywany epilogu. Dla bezwarunkowe epilogues go powinna być równa 0xE, co oznacza "zawsze". (Epilogu musi być całkowicie warunkowych lub całkowicie bezwarunkowe, a w trybie Thumb-2 epilogu rozpoczyna się od pierwszej instrukcji po IT opcode).|  
    |24-31|*Indeks Start epilogu* jest 8-bitową pola, które wskazuje indeks bajt pierwszy kod unwind opisujący ten epilogu.|  
  
3.  Po liście zakresów epilogu zawiera tablicę bajtów, które zawierają kody unwind, które opisano szczegółowo w sekcji dotyczącej kodów Unwind w tym artykule. Ta tablica jest uzupełniana na końcu do najbliższej granicy pełnego wyrazu. Bajty są przechowywane w kolejności little endian, dzięki czemu mogą być bezpośrednio pobierane w trybie little endian.  
  
4.  Jeśli *X* pole w nagłówku wynosi 1, b kodu unwind następują informacji obsługi wyjątków. Ten krok składa się z jednego *RVA obsługi wyjątków* zawierający adres program obsługi wyjątku, bezpośrednio po ilość danych wymaganych przez program obsługi wyjątku (zmiennej długości).  
  
 Rekord .xdata zaprojektowano tak, aby można pobrać pierwszych 8 bajtów i pełnego rozmiaru rekordu nie długość danych o zmiennej długości wyjątek, znajdujący się w tym obliczeniowe. Następujący fragment kodu oblicza rozmiar rekordu:  
  
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
  
 Athough prologu i każdego epilogu ma indeks na kody unwind, tabela jest udostępniana między nimi. Nie jest rzadko, że wszystkie udostępniają te same kody unwind. Zaleca się, że autorów kompilatora Optymalizuj dla tego przypadku ponieważ największy indeksu, który może być określony wynosi 255, a liczba kodów unwind możliwe określonej funkcji, która ogranicza.  
  
### <a name="unwind-codes"></a>Kody unwind  
 Tablica kodów unwind jest pula sekwencji instrukcji, które opisują dokładnie, jak cofnąć skutków prologu, w kolejności, w którym musi można cofnąć operacji. Kody unwind to zestaw instrukcji mini, został zakodowany jako ciąg bajtów. Po zakończeniu wykonywania adres zwrotny do wywoływania funkcji znajduje się w rejestrze LR i wszystkich rejestrów trwałej zostaną przywrócone do wartości w czasie, gdy została wywołana funkcja.  
  
 Jeśli wyjątki były gwarantowane występuje tylko w treści funkcji, i nigdy nie w obrębie prologu / epilogu, następnie tylko jeden unwind sekwencji będzie konieczne. Model odwijaniem systemu Windows wymaga jednak możliwość rozwijają się od w prologu częściowo wykonanego lub epilogu. Aby spełnić to wymaganie, kody unwind zostały starannie zaprojektowane, aby mieć jednoznaczne mapowanie jeden do jednego, aby każdy odpowiedni kod operacji w prologu i epilogu. Ma to wpływ na kilku:  
  
-   Istnieje możliwość obliczeniowe długość prologu i epilogu liczbą unwind kodów. Jest to możliwe nawet o zmiennej długości instrukcje Thumb-2, ponieważ istnieją różne mapowania dla opcodes 16-bitowe i 32-bitowych.  
  
-   Przez liczenie instrukcje po uruchomieniu epilogu zakresu, można pominąć równoważną liczbę kodów unwind i wykonać pozostałej części sekwencji do ukończenia częściowo wykonywane jest unwind wykonywała epilogu.  
  
-   Liczenie instrukcje przed końcem prologu, istnieje możliwość pominąć równoważną liczbę kodów unwind i wykonać pozostałej części sekwencji, aby cofnąć tylko te części prologu wykonanych wykonywania.  
  
 W poniższej tabeli przedstawiono mapowanie kody unwind kody operacji. Najbardziej typowe kody są tylko jednego bajtu, podczas gdy mniej typowe wymagają tych dwóch, trzech lub czterech nawet bajtów. Każdy kod jest przechowywany z najbardziej znaczący bajt najmniej znaczący bajt. Struktura kodu unwind różni się od kodowanie opisanego w ARM EABI, ponieważ te kody unwind zostały zaprojektowane w celu zapewnienia mapowanie jeden do jednego do opcodes prologu i epilogu, aby umożliwić rozwinięcia z częściowo wykonane prologues i epilogues.  
  
|Bajt 1|Bajt 2|Bajt 3|Bajt 4|Opsize|Wyjaśnienie|  
|------------|------------|------------|------------|------------|-----------------|  
|00 7F||||16|`add   sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x7F) * 4|  
|80 BF|00 DO FF|||32|`pop   {r0-r12, lr}`<br /><br /> gdzie LR jest zdjęte ze stosu, jeśli kod & 0x2000 i r0 r12 są zdjęte ze stosu Jeśli odpowiadający mu bit jest ustawiony w 0x1FFF & kodu|  
|C0 CF||||16|`mov   sp,rX`<br /><br /> gdzie X jest 0x0F & kodu|  
|D0 D7||||16|`pop   {r4-rX,lr}`<br /><br /> gdzie X jest (kod & 0x03) + 4 i LR jest zdjęte ze stosu Jeśli 0x04 & kodu|  
|D8 DF||||32|`pop   {r4-rX,lr}`<br /><br /> gdzie X jest (kod & 0x03) + 8 i LR jest zdjęte ze stosu Jeśli 0x04 & kodu|  
|E0 E7||||32|`vpop  {d8-dX}`<br /><br /> gdzie X jest (kod & 0x07) + 8|  
|E8 EB|00 DO FF|||32|`addw  sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x03FF) * 4|  
|WE ED|00 DO FF|||16|`pop   {r0-r7,lr}`<br /><br /> gdzie LR jest zdjęte ze stosu, jeśli kod & 0x0100 i r0 r7 są zdjęte ze stosu Jeśli odpowiadający mu bit jest ustawiony w 0x00FF & kodu|  
|EE|00 0F|||16|specyficzne dla firmy Microsoft|  
|EE|10-FF.|||16|Dostępne|  
|EF|00 0F|||32|`ldr   lr,[sp],#X`<br /><br /> gdzie X jest (kod & 0x000F) * 4|  
|EF|10-FF.|||32|Dostępne|  
|F0 F4||||-|Dostępne|  
|F5|00 DO FF|||32|`vpop  {dS-dE}`<br /><br /> gdzie S jest (kod & 0x00F0) >> 4 i E jest 0x000F & kodu|  
|F6|00 DO FF|||32|`vpop  {dS-dE}`<br /><br /> w przypadku S ((Code & 0x00F0) >> 4) + 16 i E jest (kod & 0x000F) + 16|  
|F7|00 DO FF|00 DO FF||16|`add   sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x00FFFF) * 4|  
|F8|00 DO FF|00 DO FF|00 DO FF|16|`add   sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x00FFFFFF) * 4|  
|F9|00 DO FF|00 DO FF||32|`add   sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x00FFFF) * 4|  
|FA|00 DO FF|00 DO FF|00 DO FF|32|`add   sp,sp,#X`<br /><br /> gdzie X jest (kod & 0x00FFFFFF) * 4|  
|FB||||16|NOP (16-bitowy)|  
|FC||||32|NOP (32-bitowe)|  
|FD||||16|End + nop 16-bitową w epilogu|  
|FE||||32|End + nop 32-bitowe w epilogu|  
|FF||||-|end|  
  
 Oznacza to zakres wartości szesnastkowe dla każdego bajtu w kodzie unwind *kod*, wraz z rozmiarem opcode *Opsize* i odpowiednie oryginalnego interpretacji instrukcji. Puste komórki wskazują krótszą unwind kodów. W instrukcjach, które mają duże wartości obejmujące wiele bajtów najpierw są przechowywane najbardziej znaczących bitów. *Opsize* pole zawiera rozmiar niejawne opcode skojarzony z każdej operacji Thumb-2. Jawne zduplikowane wpisy w tabeli o różnych kodowań są używane do rozróżnienia opcode różne rozmiary.  
  
 Kody unwind są zaprojektowane tak, aby pierwszy bajt kodu informuje zarówno całkowity rozmiar w bajtach kodu i rozmiar odpowiedni kod operacji w strumieniu instrukcji. Do obliczenia rozmiaru prologu lub epilogu, objaśniono kody unwind na początku sekwencji do końca i umożliwia określenie, jak długo trwa odpowiedni kod operacji tabeli odnośników lub podobnej metody.  
  
 Unwind kodów 0xFD i 0xFE są równoważne kod zakończenia prawidłowe 0xFF, ale konto dla jednego opcode nop dodatkowe w przypadku epilogu 16-bitowych lub 32-bitowy. Prologues 0xFD, 0xFE i 0xFF są równoważne. To konta dla typowych zakończenia epilogu `bx lr` lub `b <tailcall-target>`, który nie ma instrukcji prologu równoważne. Dzięki temu rośnie ryzyko, że unwind sekwencji może być współużytkowana prologu i epilogues.  
  
 W wielu przypadkach należy używać ten sam zestaw kodów unwind prologu i epilogues wszystkie. Aby obsłużyć rozwinięcia częściowo wykonanego prologues i epilogues, może być mieć wiele unwind sekwencje kodu, które różnią się w kolejności lub zachowanie. Jest to, dlaczego epilogu każdy ma własny indeks w tablicy unwind do wyświetlenia, gdzie można rozpocząć wykonywania.  
  
### <a name="unwinding-partial-prologues-and-epilogues"></a>Odwijaniem Prologues częściowe i Epilogues  
 Najbardziej typowych przypadkach odwijaniem jest po wystąpieniu wyjątku w treści funkcji prologu i wszystkie epilogues. W takim przypadku unwinder wykonuje kody na początku tablicy unwind pod indeksem 0 i będzie wykonywany do momentu zakończenia opcode została wykryta.  
  
 Gdy wystąpi wyjątek podczas prologu lub epilogu jest wykonywany, ramka stosu jest tylko częściowo wykonane, a unwinder musi określić dokładnie co zostało wykonane prawidłowo Cofnij go w celu.  
  
 Rozważmy na przykład ta sekwencja prologu i epilogu:  
  
```  
0000:   push  {r0-r3}         ; 0x04  
0002:   push  {r4-r9, lr}     ; 0xdd  
0006:   mov   r7, sp          ; 0xc7  
...  
0140:   mov   sp, r7          ; 0xc7  
0142:   pop   {r4-r9, lr}     ; 0xdd  
0146:   add   sp, sp, #16     ; 0x04  
0148:   bx    lr  
```  
  
 Obok każdego opcode jest kod unwind odpowiednie do opisywania tej operacji. Sekwencja kodów unwind dla prologu jest odbicie lustrzane kody unwind epilogu, bez uwzględnienia instrukcja końcowa. Ten przypadek często i jest przyczyną kody unwind prologu są zawsze zakłada, że mają być przechowywane w odwrotnej kolejności z prologu kolejność wykonywania. Daje wspólny zestaw kodów unwind:  
  
```  
0xc7, 0xdd, 0x04, 0xfd  
```  
  
 Kod 0xFD jest specjalne koniec sekwencji, która oznacza, że epilogu jest dłuższa niż prologu jednej instrukcji 16-bitowych. Umożliwia udostępnianie większej unwind kodów.  
  
 W tym przykładzie Jeśli wystąpi wyjątek podczas wykonywania treści funkcji między prologu i epilogu odwijaniem rozpoczyna się epilogu sprawy, przy przesunięciu 0 kodem epilogu. Odpowiada to przesunięcie 0x140 w przykładzie. Unwinder wykonuje sekwencji unwind pełne, ponieważ nie została wykonana nie czyszczenia. Zamiast tego wyjątki jednej instrukcji po rozpoczęciu kod epilogu, unwinder można pomyślnie operacji unwind przez pominięcie pierwszy kod unwind. Podane mapowanie jeden do jednego między opcodes i unwind kody, jeśli odwijanie od instrukcji  *n*  w epilogu unwinder należy pominąć pierwszy  *n*  unwind kodów.  
  
 Podobne logiki działa odwrotnie dla prologu. Odwijanie od przesunięcia 0 w prologu, nic nie musi być wykonywane. Jeśli odwijanie od jednej instrukcji w, sekwencji unwind należy uruchomić jeden kod unwind od jej końca, ponieważ prologu unwind kody są przechowywane w odwrotnej kolejności. W przypadku ogólne, jeśli odwijanie od instrukcji  *n*  w prologu rozwinięcia powinien rozpocząć wykonywania na  *n*  unwind kody od końca listy kodów.  
  
 Kody unwind prologu i epilogu nie zawsze pasują dokładnie. W takim przypadku unwind tablicy kod może być zawiera kilka sekwencji kodów. Aby określić przesunięcie rozpoczęcie przetwarzania kodów, użyj logiki to:  
  
1.  Jeśli odwijanie od w treści funkcji, Rozpocznij wykonywanie kody unwind pod indeksem 0 i kontynuować do momentu osiągnięcia kod zakończenia operacji.  
  
2.  Jeśli odwijanie od wewnątrz epilogu, użyj indeks początkowy specyficzne dla epilogu udostępniane przez zakres epilogu. Oblicza liczbę bajtów komputer jest na początku epilogu. Przejść do przodu przez kody unwind aż wszystkie instrukcje już wykonane wyjaśnić. Wykonanie sekwencji unwind w tym momencie uruchamiania.  
  
3.  Jeśli odwijanie od w prologu, należy uruchomić z indeksem 0 w kodach unwind. Obliczenia długość kodu prologu z sekwencji, a następnie obliczyć liczbę bajtów komputer jest na końcu prologu. Przejść do przodu przez kody unwind aż wszystkie instrukcje cofnąć wyjaśnić. Wykonanie sekwencji unwind w tym momencie uruchamiania.  
  
 Kody unwind prologu zawsze musi być pierwszym w tablicy. Są one również kody używane do operacji unwind w przypadku ogólnych odwijanie od w treści. Wszystkie sekwencje epilogu unikatowy kod powinien być zgodny natychmiast po sekwencji kodu prologu.  
  
### <a name="function-fragments"></a>Fragmenty — funkcja  
 Optymalizacji kodu mogą być przydatne do dzielenia na części nieciągłe funkcji. Po zakończeniu każdego fragmentu funkcji wymaga własnego oddzielnych .pdata — i prawdopodobnie .xdata — rekord.  
  
 Przy założeniu, że prologu funkcji znajduje się na początku funkcji i nie można podzielić, istnieją cztery przypadków fragmentu funkcji:  
  
-   Prologu. wszystkie epilogues w innych fragmentach.  
  
-   Prologu i co najmniej jeden epilogues; dodatkowe epilogues w innych fragmentach.  
  
-   Brak prologu lub epilogues; prologu i co najmniej jeden epilogues w innych fragmentach.  
  
-   Epilogues. a także ewentualne dodatkowe epilogues w innych fragmentach prologu.  
  
 W pierwszym przypadku należy opisać tylko prologu. Można to zrobić w postaci compact .pdata opisujące prologu normalnie i określając *Ret* wartość 3, aby wskazać nie epilogu. W formularzu pełna .xdata można to zrobić, zapewniając kody unwind prologu pod indeksem 0 w zwykły sposób i określanie epilogu liczby 0.  
  
 Drugim przypadku działa tak jak normalne funkcji. Jeśli istnieje tylko jeden epilogu we fragmencie, i znajduje się na końcu fragmentu, rekord compact .pdata można użyć. W przeciwnym razie należy użyć rekordu .xdata pełna. Należy pamiętać, które przesunięcie określone dla uruchomienia epilogu są względem początek fragmentu nie oryginalnego uruchomienia funkcji.  
  
 Trzeci i czwarty przypadkach są wariantów przypadków pierwszego i drugiego, odpowiednio, z wyjątkiem nie zawierają one prologu. W takich przypadkach zakłada się, że jest kod przed rozpoczęciem epilogu i jest uznawany za część treści funkcji, która może być zwykle odwinięty, cofając skutków prologu. W związku z tym tych przypadkach musi być zakodowane za pomocą pseudo-prologu, w którym opisano sposób unwind z wewnątrz treści, ale który jest traktowany jako długość 0 podczas określania czy wykonywać częściowym unwind początek fragmentu. Alternatywnie to pseudo-prologu mogą być opisane przy użyciu tych samych kodów unwind jako epilogu, ponieważ prawdopodobnie wykonują operacje równoważne.  
  
 W trzecim i czwartym przypadkach obecności pseudo-prologu jest określona przez ustawienie *flagi* pola rekordu compact .pdata do 2 lub przez ustawienie *F* flagi w nagłówku .xdata do 1. W obu przypadkach sprawdzania unwind częściowe prologu jest ignorowana, a wszystkie z systemem innym niż epilogu cofa są uważane pełna.  
  
#### <a name="large-functions"></a>Długie funkcje  
 Fragmenty może służyć do opisywania większy niż limit 512 KB powodowanego przez pola bitowe w nagłówku .xdata funkcji. Do opisania funkcja bardzo duży, tylko podziel go na fragmenty mniejsze niż 512 KB. Należy dostosować tak, aby nie dzieli epilogu na wielu części każdego fragmentu.  
  
 Tylko pierwszy fragment funkcji zawiera prologu; pozostałych fragmentów są oznaczone jako mający nie prologu. W zależności od liczby epilogues każdego fragmentu może zawierać zero lub więcej epilogues. Należy pamiętać, że każdego zakresu epilogu w fragmentu określa ich początkowe przesunięcie względem początek fragmentu nie uruchomienia funkcji.  
  
 Jeśli fragmentu nie prologu i epilogu nie, nadal wymaga własnego .pdata — i prawdopodobnie .xdata — rekord opisujący sposób rozwijają się od w treści funkcji.  
  
#### <a name="shrink-wrapping"></a>Shrink-wrapping  
 Jest bardziej złożonych przypadkach specjalnych funkcji fragmentów *shrink-wrapping*, technika odkładanie rejestru zapisuje od początku funkcji później w funkcji, aby zoptymalizować dla prostego przypadków, które nie wymagają zapisywania rejestru. Można to określić jako zewnętrzne regionu, przydziela miejsce stosu, który zapisuje minimalny zbiór rejestrów i wewnętrzny region, który zapisuje i przywraca rejestrów dodatkowe.  
  
```  
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
  
 Funkcje porządnie zapakowane zwykle mają wstępnie przydzielić miejsca dla dodatkowych rejestru jest zapisywany w prologu regularnych, a następnie wykonaj zapisuje rejestru za pomocą `str` lub `stm` zamiast `push`. Dzięki temu wszystkie manipulowania wskaźnik stosu w oryginalnym prologu funkcji.  
  
 Funkcja porządnie zapakowane przykład musi podzielone na trzy obszary, które są oznaczone jako A, B i C w komentarzach. Najpierw region obejmuje początku funkcji do końca dodatkowe zapisuje trwałej. Rekord .pdata lub .xdata musi być skonstruowany do opisu tego fragmentu jako mający prologu i nie epilogues.  
  
 Region bliski B pobiera swój rekord .pdata lub .xdata opisujący fragment, który ma nie prologu i epilogu nie. Jednak nadal musi być obecny kody unwind dla tego obszaru, ponieważ ma on uznawany za treść funkcji. Kody musi opisywać prologu złożonego, reprezentujący oryginalny rejestrów zapisane w prologu region A i dodatkowe rejestrów zapisane przed wejściem w region B, tak jakby były one produkowane przez jeden sekwencja operacji.  
  
 Rejestr jest zapisywany w regionie, który B nie można uznać za "prologu wewnętrzny", ponieważ złożonego prologu opisane dla regionu B musi opisywać zarówno prologu region A, jak i dodatkowych rejestrów zapisane. Jeśli fragmentu B zostały opisane jako mający prologu, kody unwind również oznaczałoby rozmiar tego prologu, a nie istnieje sposób do opisywania złożonego prologu w taki sposób, który mapuje jeden do jednego z opcodes, który tylko Zapisz dodatkowe rejestrów.  
  
 Zapisuje dodatkowe rejestrowanie, należy rozważyć częścią regionu A, ponieważ dopiero po ich zakończeniu złożonego prologu niedokładnie opisuje stanu stosu.  
  
 Ostatniego regionu C pobiera swój .pdata lub .xdata rekord opisujący fragmentu, które prologu nie ma epilogu.  
  
 Informacje o innym podejściu mogą również działać, jeśli stosem zrobić przed wejściem w region B można zmniejszyć do jednej instrukcji:  
  
```  
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
  
 Klucz, w tym miejscu jest na każdej granicy rozkazu stosu pełni zgodne z kodami unwind dla regionu. Jeśli unwind występuje przed wewnętrzny wypychania w tym przykładzie, jest on uznawany za część region A, a tylko region prologu to oddzielić. Sytuacji unwind po wewnętrzny wypychania uważa się, że część region B, który nie prologu, ale skonfigurowano kody unwind, które opisują wewnętrzny wypychania i oryginalnego prologu z regionu A. podobne logiki przechowuje dla wewnętrznego protokołu pop.  
  
### <a name="encoding-optimizations"></a>Kodowanie optymalizacji  
 Z powodu siłę kodów unwind i możliwość compact wykorzystać i rozszerzonej formy danych istnieje wiele możliwości w celu zoptymalizowania kodowania w celu dalszego ograniczenia miejsca. Z aktywnego użycia tych metod net obciążenie opisujące funkcje i fragmenty przy użyciu kodów unwind może być całkiem mały.  
  
 Optymalizacja najważniejszych jest należy zachować ostrożność, nie należy mylić prologu/epilogu granice dla celów odwijaniem z logiczną prologu/epilogu granice z punktu widzenia kompilatora. Odwijaniem granice można zmniejszyć i wprowadzone większego w celu zwiększenia wydajności. Na przykład prologu mogą zawierać kod po sprawdza ustawienia stosu do przeprowadzenia dodatkowej weryfikacji. Jednak po ukończeniu wszystkich stosem nie istnieje potrzeba do kodowania więcej operacji i niczego poza ten można usunąć z odwijaniem prologu.  
  
 Ten sam reguła ma zastosowanie do długości funkcji. Jeśli dane — na przykład puli literału — następujący epilogu w funkcji, nie powinien być dołączane jako część długości funkcji. Zmniejszając funkcji do tylko kod, który jest częścią funkcji, ryzyko jest większa konieczności epilogu na końcu i CD. rekordu PData mogą być używane.  
  
 W prologu po zapisaniu wskaźnik stosu do innego rejestru nie ma zwykle nie trzeba rejestrować wszystkie dodatkowe kody operacji. Cofnąć funkcji, najpierw, która została wykonana jest pozwoli na odzyskanie SP rejestru zapisane i dlatego dalszych operacji nie mają wpływu na unwind.  
  
 Epilogues pojedynczych instrukcji nie mają być kodowane jako zakresy gwarancja, lub jako unwind kodów. Jeśli unwind ma miejsce przed wykonaniem tej instrukcji, a następnie może być zakłada się od w treści funkcji i wykonania kody unwind prologu jest wystarczająca. Jeśli unwind ma miejsce po wykonaniu pojedynczej instrukcji, następnie zgodnie z definicją go odbywa się w innym regionie.  
  
 Nie trzeba kodować pierwszej instrukcji epilogu, z tego samego powodu jako poprzedniego punktu epilogues wiele instrukcji: Jeśli unwind odbywa się przed wykonaniem tej instrukcji, unwind pełne prologu jest wystarczająca. Jeśli unwind ma miejsce po tej instrukcji, a następnie kolejne operacje powinny być traktowane.  
  
 Kodzie operacji unwind ponownego użycia powinna być aktywnego. Indeks określony przez poszczególnych punktów zakresu epilogu do dowolnego punktu początkowego w tablicy unwind kodów. Nie trzeba polecenie uruchomienia sekwencji poprzedniej; może wskazywać w środku. Najlepszym podejściem jest generowanie sekwencji odpowiedni kod, a następnie skanowania pod kątem dopasowania dokładne bajtów w puli już zakodowane w sekwencji i użyj żadnego dopasowania doskonałe jako punktu wyjścia do ponownego użycia.  
  
 Jeśli po epilogues pojedynczych instrukcji są ignorowane, nie istnieją żadne pozostałych epilogues należy wziąć pod uwagę przy użyciu formularza compact .pdata; staje się bardziej prawdopodobne w przypadku braku epilogu.  
  
## <a name="examples"></a>Przykłady  
 W tym przykładzie baza obrazu jest w 0x00400000.  
  
### <a name="example-1-leaf-function-no-locals"></a>Przykład 1: Funkcja typu liść, nie zmienne lokalne  
  
```  
Prologue:  
  004535F8: B430      push        {r4-r5}  
Epilogue:  
  00453656: BC30      pop         {r4-r5}  
  00453658: 4770      bx          lr  
```  
  
 .PData (stała, słowa 2):  
  
-   Word 0  
  
    -   *Funkcja początkowy adres RVA* = 0x000535F8 (= 0x004535F8 0x00400000)  
  
-   Word 1  
  
    -   *Flaga* = 1, wskazujący canonical formatów prologu i epilogu  
  
    -   *Funkcja długość* = 0x31 (= 0x62/2)  
  
    -   *RET* = 1 i wskazujący zwracany gałąź 16-bitowych  
  
    -   *H* = 0, wskazującą parametrów nie zostały podłączony.  
  
    -   *R*= 0 i *Reg* = 1, wskazujący wypychanych/pop z r4 r5  
  
    -   *L* = 0, co oznacza nie LR zapisać/przywrócić  
  
    -   *C* = 0, co oznacza nie łańcucha ramki  
  
    -   *Stack — Dostosuj* = 0, co oznacza nie dopasowania stosu  
  
### <a name="example-2-nested-function-with-local-allocation"></a>Przykład 2: Zagnieżdżonej funkcji z lokalnej Alokacja  
  
```  
Prologue:  
  004533AC: B5F0      push        {r4-r7, lr}  
  004533AE: B083      sub         sp, sp, #0xC  
Epilogue:  
  00453412: B003      add         sp, sp, #0xC  
  00453414: BDF0      pop         {r4-r7, pc}  
```  
  
 .PData (stała, słowa 2):  
  
-   Word 0  
  
    -   *Funkcja początkowy adres RVA* = 0x000533AC (= 0x004533AC-0x00400000)  
  
-   Word 1  
  
    -   *Flaga* = 1, wskazujący canonical formatów prologu i epilogu  
  
    -   *Funkcja długość* = 0x35 (= 0x6A/2)  
  
    -   *RET* = 0, co oznacza punktu obecności {pc} return  
  
    -   *H* = 0, wskazującą parametrów nie zostały podłączony.  
  
    -   *R*= 0 i *Reg* = 3, wskazującą wypychanych/pop z r4 r7  
  
    -   *L* = 1, wskazujący LR zapisane/przywrócono  
  
    -   *C* = 0, co oznacza nie łańcucha ramki  
  
    -   *Dostosuj stosu* = 3 (0x0C/4 =)  
  
### <a name="example-3-nested-variadic-function"></a>Przykład 3: Zagnieżdżonej funkcji ze zmienną liczbą argumentów  
  
```  
Prologue:  
  00453988: B40F      push        {r0-r3}  
  0045398A: B570      push        {r4-r6, lr}  
Epilogue:  
  004539D4: E8BD 4070 pop         {r4-r6}  
  004539D8: F85D FB14 ldr         pc, [sp], #0x14  
```  
  
 .PData (stała, słowa 2):  
  
-   Word 0  
  
    -   *Funkcja początkowy adres RVA* = 0x00053988 (= 0x00453988 0x00400000)  
  
-   Word 1  
  
    -   *Flaga* = 1, wskazujący canonical formatów prologu i epilogu  
  
    -   *Funkcja długość* = 0x2A (= 0x54/2)  
  
    -   *RET* = 0, co oznacza pop {pc} — styl return (w takim przypadku pc ldr [sp], nr 0x14 return)  
  
    -   *H* = 1, wskazujący parametry zostały adresem IP.  
  
    -   *R*= 0 i *Reg* = 2, wskazującą wypychanych/pop z r4 r6  
  
    -   *L* = 1, wskazujący LR zapisane/przywrócono  
  
    -   *C* = 0, co oznacza nie łańcucha ramki  
  
    -   *Stack — Dostosuj* = 0, co oznacza nie dopasowania stosu  
  
### <a name="example-4-function-with-multiple-epilogues"></a>Przykład 4: Funkcja z wielu Epilogues  
  
```  
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
  
 .PData (stała, słowa 2):  
  
-   Word 0  
  
    -   *Funkcja początkowy adres RVA* = 0x000592F4 (= 0x004592F4 0x00400000)  
  
-   Word 1  
  
    -   *Flaga* = 0, wskazując istniejącego rekordu .xdata (wymagane ze względu na wiele epilogues)  
  
    -   *adres .xdata* -0x00400000  
  
 .xdata (zmiennej, słowa 6):  
  
-   Word 0  
  
    -   *Funkcja długość* = 0x0001A3 (= 0x000346/2)  
  
    -   *Sterowniki* = 0, co oznacza pierwszej wersji xdata  
  
    -   *X* = 0, co oznacza nie wyjątku  
  
    -   *E* = 0, co oznacza listę zakresów epilogu  
  
    -   *F* = 0, co oznacza pełne działanie opis, tym prologu  
  
    -   *Liczba epilogu* = 0x04 i wskazujący 4 zakresy całkowita epilogu  
  
    -   *Wyrazy kodu* = 0x01 i wskazujący jedno słowo w 32-bitowych kodów unwind  
  
-   Wyrazy opisujące 4 zakresy epilogu w lokalizacjach 4 1-4. Każdego zakresu ma wspólny zestaw kodów unwind, udostępnione prologu, przy przesunięciu 0x00 i bezwarunkowe, określając warunek 0x0E (zawsze).  
  
-   Unwind kody, zaczynając od 5 słowa: (współużytkowane prologu/epilogu)  
  
    -   Wartość 0 = 0x06 kodzie operacji unwind: sp += (6 << 2)  
  
    -   1 = 0xDE kodzie operacji unwind: pop {r4 r10, lr}  
  
    -   2 = 0xFF kodzie operacji unwind: zakończenia  
  
### <a name="example-5-function-with-dynamic-stack-and-inner-epilogue"></a>Przykład 5: Funkcja dynamicznej stosu i wewnętrzny epilogu  
  
```  
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
  
 .PData (stała, słowa 2):  
  
-   Word 0  
  
    -   *Funkcja początkowy adres RVA* = 0x00085A20 (= 0x00485A20 0x00400000)  
  
-   Word 1  
  
    -   *Flaga* = 0, wskazując istniejącego rekordu .xdata (wymagane ze względu na wiele epilogues)  
  
    -   *adres .xdata* -0x00400000  
  
 .xdata (zmiennej, słowa 3):  
  
-   Word 0  
  
    -   *Funkcja długość* = 0x0001A3 (= 0x000346/2)  
  
    -   *Sterowniki* = 0, co oznacza pierwszej wersji xdata  
  
    -   *X* = 0, co oznacza nie wyjątku  
  
    -   *E* = 0, co oznacza listę zakresów epilogu  
  
    -   *F* = 0, co oznacza pełne działanie opis, tym prologu  
  
    -   *Liczba epilogu* = 0x001 i wskazujący 1 zakres łączny epilogu  
  
    -   *Wyrazy kodu* = 0x01 i wskazujący jedno słowo w 32-bitowych kodów unwind  
  
-   Word 1: Epilogu zakresu przy przesunięciu 0xC6 (= 0x18C/2), począwszy od indeksu kodu unwind, na 0x00 i z warunkiem 0x0E (zawsze)  
  
-   Unwind kody, począwszy od programu Word 2: (współużytkowane prologu/epilogu)  
  
    -   0 = 0xC6 kodzie operacji unwind: sp = r6  
  
    -   1 = 0xDC kodzie operacji unwind: pop {r4 r8, lr}  
  
    -   2 = 0x04 kodzie operacji unwind: sp += (4 << 2)  
  
    -   3 = 0xFD kodzie operacji unwind: celu liczby jako 16-bitowych instrukcję epilogu  
  
### <a name="example-6-function-with-exception-handler"></a>Przykład 6: Funkcja z obsługą wyjątków  
  
```  
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
  
 .PData (stała, słowa 2):  
  
-   Word 0  
  
    -   *Funkcja początkowy adres RVA* = 0x00088C24 (= 0x00488C24 0x00400000)  
  
-   Word 1  
  
    -   *Flaga* = 0, wskazując istniejącego rekordu .xdata (wymagane ze względu na wiele epilogues)  
  
    -   *adres .xdata* -0x00400000  
  
 .xdata (zmiennej, słowa 5):  
  
-   Word 0  
  
    -   *Funkcja długość* = 0x000027 (= 0x00004E/2)  
  
    -   *Sterowniki* = 0, co oznacza pierwszej wersji xdata  
  
    -   *X* = 1, wskazujący danych wyjątku  
  
    -   *E* = 1 i wskazujący pojedynczego epilogu  
  
    -   *F* = 0, co oznacza pełne działanie opis, tym prologu  
  
    -   *Liczba epilogu* = 0x00 i wskazujący kody unwind epilogu start przy przesunięciu 0x00  
  
    -   *Wyrazy kodu* = 0x02 i wskazujący dwa wyrazy 32-bitowych kodów unwind  
  
-   Unwind kody, zaczynając od 1 do programu Word:  
  
    -   0 = 0xC7 kodzie operacji unwind: sp = r7  
  
    -   1 = 0x05 kodzie operacji unwind: sp += (5 << 2).  
  
    -   2 = 0xED/0x90 kodzie operacji unwind: pop {r4 r7, lr}  
  
    -   4 = 0xFF kodzie operacji unwind: zakończenia  
  
-   Word 3 Określa program obsługi wyjątku = 0x0019A7ED (= 0x0059A7ED - 0x00400000)  
  
-   Słów 4 i nowszych są wbudowane wyjątku  
  
### <a name="example-7-funclet"></a>Przykład 7: Funclet  
  
```  
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
  
 .PData (stała, słowa 2):  
  
-   Word 0  
  
    -   *Funkcja początkowy adres RVA* = 0x00088C72 (= 0x00488C72 0x00400000)  
  
-   Word 1  
  
    -   *Flaga* = 1, wskazujący canonical formatów prologu i epilogu  
  
    -   *Funkcja długość* = 0x0B (= 0x16/2)  
  
    -   *RET* = 0, co oznacza punktu obecności {pc} return  
  
    -   *H* = 0, wskazującą parametrów nie zostały podłączony.  
  
    -   *R*= 0 i *Reg* = 7, wskazujący nie rejestrów zostały zapisane przywrócony  
  
    -   *L* = 1, wskazujący LR zapisane/przywrócono  
  
    -   *C* = 0, co oznacza nie łańcucha ramki  
  
    -   *Stack — Dostosuj* = 1 i wskazujący korekty stosu 1 bajt x 4  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd Konwencji ABI ARM](../build/overview-of-arm-abi-conventions.md)   
 [Typowe problemy przy migracji ARM Visual C++](../build/common-visual-cpp-arm-migration-issues.md)