---
title: Przegląd Konwencji ABI ARM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 23f4ae8c-3148-4657-8c47-e933a9f387de
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f78e5731e6c8d4125fb8afc184cd6e4f2a74cb7a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="overview-of-arm-abi-conventions"></a>Przegląd Konwencji ABI ARM
Interfejs binarne aplikacji (ABI) dla kodu skompilowanego dla systemu Windows na procesorów ARM jest oparta na standardowe EABI ARM. W tym artykule omówiono podstawowe różnice między systemem Windows na ARM i standardowe. Aby uzyskać więcej informacji o standardowych EABI ARM, zobacz [aplikacji binarny interfejsu (ABI) dla architektury ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html).  
  
## <a name="base-requirements"></a>Wymagania podstawowe  
 Systemu Windows na ARM zakłada, że jest on uruchomiony na architekturę ARMv7 przez cały czas. Obsługa modelu zmiennoprzecinkowego w formularzu VFPv3 D32 lub nowszej musi być obecny w sprzęcie. VFP musi obsługiwać zarówno pojedynczej precyzji, jak i zmiennoprzecinkowych sprzętu podwójnej precyzji. Środowisko wykonawcze systemu Windows nie obsługuje emulację liczb zmiennoprzecinkowych, aby umożliwić uruchamianie na urządzeniu z systemem innym niż VFP.  
  
 Zaawansowana obsługa SIMD Extensions (NEON) — dotyczy zarówno całkowitą i operacjach liczb zmiennoprzecinkowych — musi być obecny w sprzęcie. Brak obsługi czasu wykonywania dla emulacji podano.  
  
 Obsługa dzielenie liczby całkowitej (UDIV/SDIV) jest zdecydowanie zalecane, ale nie jest wymagane. Platformy, które nie obsługują dzielenie liczby całkowitej może spowodować zmniejszenie wydajności, ponieważ te operacje muszą być kolor i prawdopodobnie poprawkami.  
  
## <a name="endianness"></a>Kolejności bajtów  
 Wykonuje na ARM z systemem Windows w trybie little endian. Zarówno kompilatora Visual C++ i środowiska wykonawczego systemu Windows należy oczekiwać little endian danych przez cały czas. Mimo że instrukcja SETEND w instrukcji ARM ustawić architektura (ISA) umożliwia kod nawet trybu użytkownika, aby zmienić bieżącego kolejności bajtów, to tak nie jest zalecane, ponieważ jest niebezpieczne dla aplikacji. Jeśli wyjątek jest generowany w trybie big-endian zachowanie jest nieprzewidywalne i może prowadzić do błędu aplikacji w trybie użytkownika lub wyniki operacji w trybie jądra.  
  
## <a name="alignment"></a>Wyrównanie  
 Mimo że systemu Windows umożliwia sprzęt ARM, aby obsłużyć całkowitą niewyrównanych uzyskuje dostęp do przejrzysty, wyrównanie błędów nadal mogą być generowane w niektórych sytuacjach. Wykonaj te reguły dla wyrównania:  
  
-   Połowa word o rozmiarze (16-bitowy) i ładuje o rozmiarze word całkowitą (32-bitowe) i magazyny nie muszą być wyrównane. Sprzęt obsługuje je wydajne i w sposób niewidoczny dla użytkownika.  
  
-   Zmiennoprzecinkowe obciążenia sieci i magazynów powinno być wyrównane. Jądro obsługuje niewyrównany obciążenia i są przechowywane w sposób niewidoczny dla użytkownika, ale z znaczne obciążenie.  
  
-   Ładowania lub przechowywania o podwójnej precyzji (LDRD/STRD) i wiele operacji (LDM/STM) powinno być wyrównane. Jądro obsługuje większość z nich w sposób niewidoczny dla użytkownika, ale z znaczne obciążenie.  
  
-   Pełny dostęp bez buforowania pamięci muszą być wyrównane, nawet w przypadku uzyskuje dostęp do liczby całkowitej. Niewyrównane dostępy spowodować błąd wyrównania.  
  
## <a name="instruction-set"></a>Zestaw instrukcji  
 Instrukcja dla systemu Windows na ARM jest ograniczone do Thumb-2. Cały kod wykonywany na tej platformie powinien rozpocząć i pozostają w trybie podglądu przez cały czas. Próba przełączenia do starszej wersji zestaw instrukcji ARM może się powieść, ale jeśli tak jest, wszystkie wyjątki lub przerwania, które występują może prowadzić do błędu aplikacji w trybie użytkownika lub wyniki operacji w trybie jądra.  
  
 Efekt uboczny to wymaganie jest, że wszystkie wskaźniki kod musi mieć ustawiony jest bit niski. Jest to, aby po załadowane i rozgałęzionych się za pośrednictwem BLX lub BX, procesor będą pozostawać w trybie podglądu i próbuje wykonać kod docelowy jako 32-bitowe instrukcje ARM.  
  
### <a name="it-instructions"></a>Instrukcje IT  
 Użycie instrukcji IT w kodzie Thumb-2 jest niedozwolone, z wyjątkiem takich szczególnych przypadkach:  
  
-   Instrukcja IT tylko może służyć do modyfikowania jednej instrukcji docelowej.  
  
-   Instrukcja docelowy musi być instrukcji 16-bitowych.  
  
-   Instrukcja docelowy musi być jeden z nich:  
  
    |Kody operacji 16-bitowych|Class|Ograniczenia|  
    |---------------------|-----------|------------------|  
    |MOV, MVN|Przenieś|RM! = PC, usług pulpitu zdalnego! = PC|  
    |LDR, LDR [S] B, H LDR [S]|Ładowanie z pamięci|Ale nie LDR literału formularzy|  
    |STRH STR, CIĄG_B,|Przechowywanie w pamięci||  
    |DODAJ ADC, RSB, SBC, SUB|Dodaj lub usuń|Ale nie SP ADD/SUB, SP, imm7 formularzy<br /><br /> RM! = PC, Rdn! = PC, Rdm! = PC|  
    |CMP, CMN|{1&gt;Compare&lt;1}|RM! = PC, Rn! = PC|  
    |MUL|Mnożenia||  
    |FUNKCJA AUTOMATYCZNEGO ODZYSKIWANIA SYSTEMU LSL, LSR, ROR|Przesunięcia bitowego||  
    |I ORR KOD, EOR, TST|Operatory arytmetyczne||  
    |BX|Gałąź, aby zarejestrować|RM! = PC|  
  
 Mimo że bieżący procesorów ARMv7 nie można utworzyć raportu na użycie niezatwierdzonych instrukcji formularzy, przyszłych generacji powinny. Wykrycie formach dowolnego programu, który używa tych może zostać zakończona z powodu wyjątku Niezdefiniowany instrukcji.  
  
### <a name="sdivudiv-instructions"></a>Instrukcje SDIV/UDIV  
 Korzystanie z liczbą całkowitą dzielenia instrukcje SDIV i UDIV jest w pełni obsługiwane, nawet na platformach bez natywnego sprzętu do ich obsługi. Narzut na SDIV lub UDIV dzielenia procesora Cortex A9 jest około 80 cykle, oprócz całkowity czas dzielenia cykli 20-250, w zależności od danych wejściowych.  
  
## <a name="integer-registers"></a>Liczba całkowita rejestrów  
 Procesor ARM obsługuje 16 rejestrów całkowitą:  
  
|Rejestruj|Volatile?|Rola|  
|--------------|---------------|----------|  
|r0|Volatile|Parametr, wynik, pliki tymczasowe rejestru 1|  
|R1|Volatile|Parametr, wynik, pliki tymczasowe rejestru 2|  
|R2|Volatile|Parametr rejestru pliki tymczasowe 3|  
|R3|Volatile|Parametr rejestru pliki tymczasowe 4|  
|R4|Non-volatile||  
|R5|Non-volatile||  
|R6|Non-volatile||  
|R7|Non-volatile||  
|R8|Non-volatile||  
|R9|Non-volatile||  
|R10|Non-volatile||  
|R11|Non-volatile|Wskaźnika ramki|  
|R12|Volatile|Pliki tymczasowe rejestru wewnątrz wywoływania|  
|R13 (SP1)|Non-volatile|Wskaźnik stosu|  
|R14 (LR)|Non-volatile|Rejestr łącza|  
|R15 (komputera)|Non-volatile|Licznik programu|  
  
 Aby uzyskać więcej informacji o sposobie używania parametru i rejestruje zwracanej wartości, zobacz sekcję przekazywanie parametru w tym artykule.  
  
 System Windows używa r11 szybkie przejście ramki stosu. Aby uzyskać więcej informacji zobacz sekcję przejście stosu. Ze względu na to wymaganie r11 musi wskazywać łącze najwyższego poziomu w łańcuchu przez cały czas. Nie używaj r11 do ogólnych celów — kod nie będzie już generował przeszukiwań stosu poprawne podczas analizy.  
  
## <a name="vfp-registers"></a>Rejestruje VFP  
 System Windows obsługuje tylko ARM wariantów, które mają Koprocesor VFPv3 D32 obsługuje. To oznacza, że rejestrów zmiennoprzecinkowych zawsze są obecne i mogą być dla parametru przekazywanie i pełny zbiór 32 rejestrów jest dostępny do użytku. Rejestruje VFP i ich użycia podsumowano w poniższej tabeli:  
  
|Wybiera|podwojenia|Quads|Volatile?|Rola|  
|-------------|-------------|-----------|---------------|----------|  
|s0 s3|D0 d1|q0|Volatile|Parametry, wynik, pliki tymczasowe rejestru|  
|S4 s7|d2 d3|1.|Volatile|Zarejestruj parametry pliki tymczasowe|  
|s8 s11|D4 d5|K2|Volatile|Zarejestruj parametry pliki tymczasowe|  
|S12 s15|D6 d7|K3|Volatile|Zarejestruj parametry pliki tymczasowe|  
|S16 s19|D8 d9|KWARTAŁ 4|Non-volatile||  
|S20 s23|D10 d11|Q5|Non-volatile||  
|S24 s27|D12 d13|Q6|Non-volatile||  
|S28 s31|D14 d15|Q7|Non-volatile||  
||D16 d31|Q8 q15|Volatile||  
  
 Następnej tabeli przedstawiono zmiennoprzecinkowy stan i kontroli zarejestrować pola bitów (FPSCR):  
  
|Bity|Znaczenie|Volatile?|Rola|  
|----------|-------------|---------------|----------|  
|31-28|NZCV|Volatile|Flagi stanu|  
|27|QC|Volatile|Zbiorcza nasycenie|  
|26|AHP|Non-volatile|Alternatywne kontroli połowie dokładności|  
|25|NAZWA WYRÓŻNIAJĄCA|Non-volatile|Domyślna kontroli trybu NaN|  
|24|FZ|Non-volatile|Formant trybu opróżniania do zera.|  
|23-22|RMode|Non-volatile|Formant trybu zaokrąglania|  
|21-20|STRIDE|Non-volatile|Vector — krok, zawsze musi mieć wartość 0|  
|18-16|Długość|Non-volatile|Długość wektora, zawsze musi mieć wartość 0|  
|15, 12-8|IDE, IXE itp.|Non-volatile|Wyjątek pułapki Włącz usługi bits, zawsze musi mieć wartość 0|  
|7, 4-0|IDC IXC, itp.|Volatile|Flagi zbiorczą wyjątku|  
  
## <a name="floating-point-exceptions"></a>Wyjątki zmiennoprzecinkowe  
 Większość ARM sprzęt nie obsługuje wyjątki zmiennoprzecinkowe IEEE. Na wariantów procesora, które mają wyjątki zmiennoprzecinkowe sprzętu jądra systemu Windows niezauważenie przechwycony wyjątek i domyślnie wyłącza je w rejestrze FPSCR. Dzięki temu zachowanie znormalizowaną przez procesor wariantów. W przeciwnym razie kod opracowany na platformie, która nie ma obsługi wyjątków otrzymać nieoczekiwanego wyjątku jest uruchomiona na platformie, która ma obsługi wyjątków.  
  
## <a name="parameter-passing"></a>Przekazywanie parametru  
 Dla funkcji wariadyczne z systemem innym niż Windows na ARM ABI regułom ARM dla przekazywanie parametru — dotyczy to również rozszerzenia VFP i SIMD zaawansowane. Wykonaj te reguły [standardowe wywołanie procedury dla architektury ARM](http://infocenter.arm.com/help/topic/com.arm.doc.ihi0042c/IHI0042C_aapcs.pdf)skonsolidowanego rozszerzenia VFP. Przez domyślny, pierwszy argumenty cztery liczby całkowitej i maksymalnie osiem zmiennoprzecinkowe lub wektorów argumenty są przekazywane w rejestrach, a dodatkowe argumenty są przekazywane na stosie. Argumenty są przypisane do rejestrów lub stosu przy użyciu tej procedury:  
  
### <a name="stage-ainitialization"></a>Etap A — inicjowanie  
 Inicjowanie jest wykonywane tylko raz, przed rozpoczęciem przetwarzania argumentu:  
  
1.  Następny Core zarejestrować numer (NCRN) ma ustawioną wartość r0.  
  
2.  Rejestruje VFP są oznaczone jako nieprzydzielony.  
  
3.  Następny skumulowany Argument adresu (NSAA) ma ustawioną wartość bieżącej SP.  
  
4.  Jeśli zostanie wywołana funkcja, która zwraca wynik w pamięci, adres dla wyniku jest umieszczany w r0 i NCRN ma ustawioną wartość r1.  
  
### <a name="stage-bpre-padding-and-extension-of-arguments"></a>Etap B — Pre uzupełnienie i rozszerzenie argumentów  
 Dla każdego argumentu na liście stosowane jest pierwsza reguła dopasowywania z poniższej listy:  
  
1.  Jeśli argument jest typu złożonego, którego rozmiar nie można ustalić statycznie przez wywołującego i wywoływany, argument jest kopiowany do pamięci i zastąpione przez wskaźnik do kopii.  
  
2.  Jeśli argument ma bajtów lub 16-bitowych połowie — word, następnie rozszerzony zero lub znakiem do pełnego wyrazu 32-bitowe i jest traktowane jako argument 4-bajtowych.  
  
3.  Jeśli argument ma typ złożony, jego rozmiar jest zaokrąglona w górę do najbliższej wielokrotności 4.  
  
### <a name="stage-cassignment-of-arguments-to-registers-and-stack"></a>Etap C — przypisanie argumentami rejestrów i stosu  
 Dla każdego argumentu na liście następujące reguły są stosowane z kolei, dopóki argument została przydzielona:  
  
1.  Jeśli argument ma typ VFP i brak jest wystarczającej liczby kolejnych nieprzydzielonego rejestrów VFP odpowiedniego typu, argument jest przydzielony do najniższy numer sekwencji takich rejestrów.  
  
2.  Jeśli argument jest typu VFP, wszystkich pozostałych nieprzydzielonych rejestrów są oznaczone jako niedostępne. NSAA zostanie przesunięty do góry, dopóki nie jest ustawione poprawnie dla typu argumentu i argument jest kopiowany do stosu w skorygowaną NSAA. NSAA jest zwiększana o rozmiar argumentu.  
  
3.  Jeśli argument wymaga wyrównanie 8-bajtowych, NCRN jest zostać zaokrąglona w górę do liczby całkowitej nawet rejestru.  
  
4.  Jeśli rozmiar argumentu w słowach 32-bitowych nie jest więcej niż r4 minus NCRN, argument jest kopiowana do rejestrów core, zaczynając od NCRN z bitami najmniej znaczący zajmujące rejestrów niższych numerach. NCRN jest zwiększany według liczby rejestrów używane.  
  
5.  NSAA jest równa PS NCRN jest mniejsza niż r4, argument jest podzielony między rejestrów rdzeni i stosu. Pierwsza część argumentu jest kopiowana do rejestrów core, zaczynając od NCRN, maksymalnie i, w tym r3. W pozostałej części argumentu jest kopiowana na stosie, zaczynając od NSAA. NCRN ma ustawioną wartość r4 i NSAA jest zwiększany o rozmiar argumentu minus kwota przekazywane w rejestrach.  
  
6.  Jeśli argument wymaga wyrównanie 8-bajtowych, NSAA jest zaokrąglona w górę do następnego adresu wyrównany 8-bajtowych.  
  
7.  Argument jest kopiowany do pamięci w NSAA. NSAA jest zwiększany o rozmiar argumentu.  
  
 Rejestry VFP nie są używane do funkcji ze zmienną liczbą argumentów, a zasady C etap 1 i 2 są ignorowane. To oznacza, że funkcja ze zmienną liczbą argumentów można rozpoczynać się od opcjonalne wypychania {r0 r3} dołączenie wartości rejestru argumenty wszelkie dodatkowe argumenty przekazany przez wywołującego, a następnie uzyskać dostęp do listy argumentów cały bezpośrednio ze stosu.  
  
 Wartości typu Liczba całkowita są zwracane w r0, opcjonalnie rozszerzony do r1 dla 64-bitowych wartości zwracanych. VFP/NEON zmiennoprzecinkowe lub SIMD typu wartości są zwracane w s0, d0 lub q0, zależnie od potrzeb.  
  
## <a name="stack"></a>Stos  
 Stos musi pozostać 4-bajtowych wyrównane przez cały czas, a musi być 8-bajtowych wyrównany na granicy żadnych funkcji. Jest to wymagane do obsługi częste użycie operacje blokowane na 64-bitowych stosu zmiennych. ARM EABI informujący o stosie 8-bajtowych wyrównane na dowolnym interfejs publiczny. Zgodność systemu Windows na ARM ABI uwzględnia żadnych granicy funkcji jako interfejsu publicznego.  
  
 Funkcje, które mają używać wskaźnika ramki — na przykład funkcje tego wywołania `alloca` lub zmienić wskaźnik stosu dynamicznie — należy zdefiniować wskaźnika ramki w r11 w prologu funkcji i pozostaw bez zmian go do epilogu. Funkcje, które nie wymagają wskaźnika ramki musi wykonać wszystkie aktualizacje stosu w prologu i pozostawić bez zmian do epilogu wskaźnik stosu.  
  
 Funkcje, które przydzielić 4 KB lub więcej informacji na temat stos musi zapewnić, że każdej stronie przed ostatnia strona jest dotknięciu w kolejności. Dzięki temu, że żaden kod nie może "leap za pośrednictwem" stron guard, używane w systemie Windows do rozszerzenia stosu. Zazwyczaj jest to realizowane `__chkstk` pomocnika, w której jest przekazywana alokacji stosu całkowita liczba bajtów rozdzielonych 4 w r4 i który zwraca kwota alokacji stosu końcowego w bajtach w r4.  
  
### <a name="red-zone"></a>Czerwony strefy  
 W obszarze 8-bajtowych natychmiast poniżej wskaźnika bieżącego stosu jest zarezerwowana dla analizy i stosowanie poprawek do dynamicznego. Pozwala to na dokładnie wygenerowany kod w celu wstawienia, służący do przechowywania 2 rejestrów na [sp # 8] i tymczasowo używa ich do celów dowolnego. Jądra systemu Windows gwarantuje, że te 8 bajtów nie zostaną zastąpione w przypadku przerwania lub wyjątek w zarówno w trybie użytkownika, jak i w trybie jądra.  
  
### <a name="kernel-stack"></a>Stos jądra  
 Stos domyślnego trybu jądra w systemie Windows jest trzy strony (12 KB). Uważaj, aby nie utworzyć funkcje, które mają duże stosu buforów w trybie jądra. Przerwania może pochodzić za pomocą bardzo mało wysokość stosu i spowodować operacji wykrywania błędów alarm stosu.  
  
## <a name="cc-specifics"></a>Szczegóły C/C++  
 Wyliczenia są typy 32-bitową liczbę całkowitą, chyba że co najmniej jedną wartość w wyliczeniu wymaga 64-bitowe o podwójnej precyzji word magazynu. W takim przypadku wyliczenia jest podwyższany do typu 64-bitową liczbę całkowitą.  
  
 `wchar_t` jest zdefiniowany jako równoważne `unsigned short`, aby zachować zgodność z innych platform.  
  
## <a name="stack-walking"></a>Stosie  
 Kod systemu Windows jest skompilowana przy użyciu wskaźniki ramek włączone ([/Oy (pominięcie wskaźnika ramki)](../build/reference/oy-frame-pointer-omission.md)) umożliwiające stosu szybkie przejście. Ogólnie rzecz biorąc, r11 zarejestrować punktów do następnego łącza w łańcuchu, czyli {r11, lr} pary określający wskaźnik do poprzedniej ramki stosu i adres zwrotny. Zaleca się, że kod również włączyć wskaźników ramek na lepsze profilowania i śledzenia.  
  
## <a name="exception-unwinding"></a>Odwijanie wyjątku  
 Odwijanie podczas obsługi wyjątków stosu jest włączona przy użyciu kodów unwind. Kody unwind są sekwencję bajtów przechowywanych w sekcji .xdata obrazu wykonywalnego. Opisano w nich operacji kod prologu i epilogu funkcji w sposób abstrakcyjny tak, aby skutków prologu funkcji można odwrócić w ramach przygotowania do rozwinięcia do ramki stosu obiektu wywołującego.  
  
 ARM EABI Określa kody operacji unwind odwijaniem model wyjątków, na którym jest używana. Jednak określenie tej wartości nie jest wystarczające do rozwinięcia w systemie Windows musi obsługiwać przypadki, w którym procesor jest w trakcie prologu lub epilogu funkcji. Aby uzyskać więcej informacji na temat systemu Windows na dane wyjątku ARM i odwijanie zobacz [obsługi wyjątków ARM](../build/arm-exception-handling.md).  
  
 Firma Microsoft zaleca opisana dynamicznie wygenerowanego kodu przy użyciu dynamicznych funkcji tabele określone w wywołaniach `RtlAddFunctionTable` wraz ze skojarzonymi funkcje, tak aby wygenerowanego kodu mogą uczestniczyć w obsługi wyjątków.  
  
## <a name="cycle-counter"></a>Licznik cyklu  
 Procesorów ARM z systemem Windows są wymagane do obsługi licznika cyklu, ale bezpośrednio za pomocą licznika może powodować problemy. Aby uniknąć tych problemów, na ARM z systemem Windows używa opcode Niezdefiniowany żądania znormalizowaną wartość licznika cyklu 64-bitowych. Z języka C lub C++ użyj `__rdpmccntr64` wewnętrznej do emisji odpowiedni kod operacji; z zestawu, użyj `__rdpmccntr64` instrukcji. Odczytywanie liczników cyklu trwa około 60 cykli na A9 Cortex.  
  
 Ten licznik jest licznikiem cyklu wartość true, nie zegara; w związku z tym częstotliwość zliczania zależy od częstotliwości procesora. Pomiar czasu czas zegara, należy użyć `QueryPerformanceCounter`.  
  
## <a name="see-also"></a>Zobacz też  
 [Typowe problemy przy migracji ARM Visual C++](../build/common-visual-cpp-arm-migration-issues.md)   
 [Obsługa wyjątków ARM](../build/arm-exception-handling.md)