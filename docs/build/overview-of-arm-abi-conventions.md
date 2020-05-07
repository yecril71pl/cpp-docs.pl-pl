---
title: Omówienie Konwencji ABI ARM
ms.date: 07/11/2018
ms.assetid: 23f4ae8c-3148-4657-8c47-e933a9f387de
ms.openlocfilehash: 8737f7b1cbe0651b43eb3b9990a4035b60bd01b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320728"
---
# <a name="overview-of-arm32-abi-conventions"></a>Omówienie Konwencji ABI ARM32

Interfejs binarny aplikacji (ABI) dla kodu skompilowanego dla systemu Windows w procesorach ARM jest oparty na standardowym EABI ARM. W tym artykule przedstawiono najważniejsze różnice między systemem Windows w systemie ARM a standardem. Ten dokument obejmuje ARM32 ABI. Aby uzyskać informacje na temat ARM64 ABI, zobacz [Omówienie Konwencji ABI arm64](arm64-windows-abi-conventions.md). Aby uzyskać więcej informacji na temat standardowego ARM EABI, zobacz [Application Binary Interface (ABI) dla architektury ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (Link zewnętrzny).

## <a name="base-requirements"></a>Wymagania podstawowe

System Windows on ARM zakłada, że działa on w architekturze architektury ARMv7 przez cały czas. Obsługa zmiennoprzecinkowa w formie VFPv3-D32 lub nowszej musi być obecna na sprzęcie. Visual FoxPro musi obsługiwać jednocześnie zmiennoprzecinkowe punkty o pojedynczej precyzji i podwójnej precyzji. Środowisko uruchomieniowe systemu Windows nie obsługuje emulacji zmiennoprzecinkowej, aby umożliwić uruchamianie na sprzęcie innym niż Visual FoxPro.

Obsługa zaawansowanych rozszerzeń SIMD (NEON) — obejmuje to zarówno liczbę całkowitą, jak i zmiennoprzecinkową — muszą także być obecne na sprzęcie. Nie podano obsługi emulacji w czasie wykonywania.

Obsługa dzielenia liczb całkowitych (UDIV/SDIV) jest silnie zalecana, ale nie jest wymagana. Platformy, które nie obsługują dzielenia liczb całkowitych, mogą powodować spadek wydajności, ponieważ te operacje muszą być zalewkowane i prawdopodobnie z poprawkami.

## <a name="endianness"></a>Endian

System Windows on ARM jest wykonywany w trybie little-endian. Zarówno kompilator MSVC, jak i środowisko uruchomieniowe systemu Windows oczekują, że dane są znacznie little-endian. Mimo że instrukcja SETEND w architekturze zestawu instrukcji ARM (ISA) umożliwia nawet kod trybu użytkownika, aby zmienić bieżącą endian, nie jest to zalecane, ponieważ jest niebezpieczne dla aplikacji. Jeśli wyjątek jest generowany w trybie big-endian, zachowanie jest nieprzewidywalne i może prowadzić do błędu aplikacji w trybie użytkownika lub operacji wykrywania błędów w trybie jądra.

## <a name="alignment"></a>Wyrównanie

Mimo że system Windows umożliwia sprzętowi ARM obsługę niewidocznych w sposób przezroczysty dostępu do liczby całkowitej, nadal mogą być generowane błędy wyrównania w niektórych sytuacjach. Postępuj zgodnie z następującymi regułami:

- Nie trzeba wyrównać liczby liczb całkowitych i magazynów o rozmiarze połówkowym (16-bitowym) i formacie (32-bitowym). Sprzęt obsługuje je wydajnie i w sposób przezroczysty.

- Obciążenia i magazyny zmiennoprzecinkowe powinny być wyrównane. Jądro obsługuje niewyrównane obciążenia i przechowuje je w sposób niewidoczny, ale z znaczącym obciążeniem.

- Należy wyrównać liczbę operacji ładowania lub zapisu podwójnego (LDRD/STRD) i wiele (LDM/STM). Jądro obsługuje większość z nich w sposób niewidoczny, ale z znaczącym obciążeniem.

- Wszystkie niebuforowane dostęp do pamięci muszą być wyrównane, nawet w przypadku dostępu do liczby całkowitej. Niewyrównane dostępy powodują błąd wyrównania.

## <a name="instruction-set"></a>Zestaw instrukcji

Zestaw instrukcji dla systemu Windows w usłudze ARM jest ściśle ograniczony do miniatury 2. Cały kod wykonywany na tej platformie powinien zostać uruchomiony i pozostanie w trybie przewijania przez cały czas. Próba przełączenia się do starszego zestawu instrukcji ARM może się nie powieść, ale jeśli tak się stało, wszelkie wyjątki lub przerwy mogą prowadzić do błędu aplikacji w trybie użytkownika lub operacji wykrywania błędów w trybie jądra.

Efektem ubocznym tego wymagania jest to, że wszystkie wskaźniki kodu muszą mieć ustawiony niski bit. Jest tak, że po załadowaniu i rozgałęzieniu do za pośrednictwem BLX lub BX, procesor pozostanie w trybie kciuka i nie spróbuje wykonać kodu docelowego jako 32-bitowe instrukcje ARM.

### <a name="it-instructions"></a>Instrukcje IT

Użycie instrukcji IT w kodzie kciuka 2 jest niedozwolone z wyjątkiem tych szczególnych przypadków:

- Instrukcji IT można użyć tylko w celu zmodyfikowania jednej instrukcji docelowej.

- Instrukcja Target musi być instrukcją 16-bitową.

- Docelowa instrukcja musi być jedną z następujących:

   |16-bitowe kod operacji|Klasa|Ograniczenia|
   |---------------------|-----------|------------------|
   |MOV, MVN|Move|RM! = PC, RD! = PC|
   |LDR, LDR [S] B, LDR [S] H|Ładowanie z pamięci|Ale nie są to formy literału LDR|
   |STR, STRB, STRH|Przechowywanie w pamięci||
   |ADD, ADC, RSB, SBC, SUB|Dodaj lub Odejmij|Ale nie Dodaj/SUB SP, SP, imm7 Forms<br /><br /> RM! = PC, RDN! = PC, RDM! = PC|
   |CMP, CMN|Porównanie|RM! = PC, RN! = PC|
   |MUL|Mnożenie||
   |ASR, SKRÓCONO, LSR, ROR|Bit Shift||
   |I, BIC, EOR, ORR, TST|Arytmetyka bitowa||
   |BX|Gałąź do zarejestrowania|RM! = komputer|

Chociaż bieżące procesory architektury ARMv7 nie mogą raportować użycia niedozwolonych formularzy instrukcji, oczekiwane są przyszłe generacje. W przypadku wykrycia tych formularzy każdy program, który z nich korzysta, może zostać zakończony niezdefiniowanym wyjątkiem instrukcji.

### <a name="sdivudiv-instructions"></a>Instrukcje SDIV/UDIV

Korzystanie z instrukcji dzielenia liczb całkowitych SDIV i UDIV jest w pełni obsługiwane nawet na platformach bez natywnego sprzętu do ich obsługi. Obciążenie przypadające na SDIV lub UDIV dzieli na Procesor Cortex-A9 ma około 80 cykli, a także do całkowitego czasu dzielenia 20-250 cykli, w zależności od danych wejściowych.

## <a name="integer-registers"></a>Rejestry całkowite

Procesor ARM obsługuje 16-całkowite rejestry:

|Zarejestruj|Volatile?|Rola|
|--------------|---------------|----------|
|R0|Volatile|Parametr, wynik, rejestr rejestru 1|
|R1|Volatile|Parametr, wynik, rejestr rejestru 2|
|wersji|Volatile|Parametr, rejestr o rejestracji 3|
|R3|Volatile|Parametr, rejestr Wyrejestrowanie 4|
|R4|Nietrwały||
|r5|Nietrwały||
|r6|Nietrwały||
|r7|Nietrwały||
|R8|Nietrwały||
|R9|Nietrwały||
|r10|Nietrwały||
|r11|Nietrwały|Wskaźnik ramki|
|r12|Volatile|Rejestr wywołujący wewnątrz procedury|
|R13 (SP)|Nietrwały|Wskaźnik stosu|
|R14 (LR)|Nietrwały|Połącz z rejestrem|
|R15 (komputer)|Nietrwały|Licznik programu|

Aby uzyskać szczegółowe informacje na temat korzystania z rejestrów i wartości zwracanych, zobacz sekcję przekazywanie parametrów w tym artykule.

System Windows używa R11 do szybkiego przechodzenia do ramki stosu. Aby uzyskać więcej informacji, zobacz sekcję przechodzenie stosu. Ze względu na to wymaganie R11 musi wskazywać górne łącze w łańcuchu przez cały czas. Nie używaj R11 do celów ogólnych — kod nie będzie generował poprawnych przeszukiwań stosu podczas analizy.

## <a name="vfp-registers"></a>Rejestry Visual FoxPro

System Windows obsługuje tylko warianty ARM z obsługą międzyprocesora VFPv3-D32. Oznacza to, że rejestry zmiennoprzecinkowe są zawsze obecne i mogą być używane do przekazywania parametrów oraz że pełny zestaw rejestrów 32 jest dostępny do użycia. Rejestry Visual FoxPro i ich użycie zostały podsumowane w tej tabeli:

|Zmiennoprzecinkowych|podwojenia|Cztery|Volatile?|Rola|
|-------------|-------------|-----------|---------------|----------|
|S0 — S3|d0 — D1|q0|Volatile|Parametry, wynik, rejestr Wyrejestrowanie|
|S4-S7|D2-D3|pierwszym|Volatile|Parametry, rejestr tymczasowy|
|S8 — S11|D4-ze|Q2|Volatile|Parametry, rejestr tymczasowy|
|S12 — S15|d6-d7|kwartał|Volatile|Parametry, rejestr tymczasowy|
|s16-s19|D8 — D9|kwartale|Nietrwały||
|S20 — S23|D10 — D11|q5|Nietrwały||
|s24-s27|D12 — D13|q6|Nietrwały||
|s28-s31|D14 — D15|q7|Nietrwały||
||D16 — D31|q8-q15|Volatile||

Następna tabela ilustruje stan zmiennoprzecinkowy i rejestr kontroli (rejestru FPSCR) pola bitów:

|Bity|Znaczenie|Volatile?|Rola|
|----------|-------------|---------------|----------|
|31-28|NZCV|Volatile|Flagi stanu|
|27|QC|Volatile|Nasycenie skumulowane|
|26|AHP|Nietrwały|Alternatywna kontrola połówkowa|
|25|WYRÓŻNIAJĄC|Nietrwały|Domyślna kontrolka trybu NaN|
|24|FZ|Nietrwały|Kontrolka trybu Flush-to-zero|
|23-22|RMode|Nietrwały|Kontrolka trybu zaokrąglania|
|21-20|Tabela|Nietrwały|Krok wektora, musi być zawsze równy 0|
|18-16|Len|Nietrwały|Długość wektora musi być zawsze równa 0.|
|15, 12-8|IDE, IXE itp.|Nietrwały|W przypadku usługi BITS pułapki wyjątków musi być zawsze równa 0.|
|7, 4-0|IDC, IXC itp.|Volatile|Flagi zbiorcze wyjątków|

## <a name="floating-point-exceptions"></a>Wyjątki zmiennoprzecinkowe

Większość sprzętu ARM nie obsługuje wyjątków zmiennoprzecinkowych IEEE. W przypadku wariantów procesora, które mają wyjątki zmiennoprzecinkowe sprzętowe, jądro systemu Windows dyskretnie przechwytuje wyjątki i niejawnie wyłącza je w rejestrze rejestru FPSCR. Zapewnia to normalne zachowanie różnych wariantów procesora. W przeciwnym razie kod opracowany na platformie, która nie ma obsługi wyjątków, może otrzymać nieoczekiwane wyjątki, gdy jest uruchomiona na platformie z obsługą wyjątków.

## <a name="parameter-passing"></a>Przekazywanie parametrów

W przypadku funkcji innych niż wariadyczne w systemie Windows w usłudze ARM ABI obowiązują reguły ARM dotyczące przekazywania parametrów — dotyczy to również rozszerzeń Visual FoxPro i Advanced SIMD. Reguły te są zgodne ze [standardowym wywołaniem procedury dla architektury ARM](http://infocenter.arm.com/help/topic/com.arm.doc.ihi0042c/IHI0042C_aapcs.pdf), skonsolidowanym z rozszerzeniami Visual FoxPro. Domyślnie w rejestrach są przesyłane pierwsze cztery argumenty całkowite i maksymalnie osiem argumentów zmiennoprzecinkowych lub wektorowych, a dodatkowe argumenty są przesyłane na stosie. Argumenty są przypisywane do rejestrów lub stosu przy użyciu tej procedury:

### <a name="stage-a-initialization"></a>Etap A: inicjalizacja

Inicjalizacja jest wykonywana dokładnie raz, przed rozpoczęciem przetwarzania argumentów:

1. Kolejny numer podstawowego rejestru (NCRN) jest ustawiony na R0.

1. Rejestry Visual FoxPro są oznaczone jako nieprzypisane.

1. Następny skumulowany adres argumentu (NSAA) jest ustawiony na bieżący SP.

1. Jeśli wywoływana jest funkcja zwracająca wynik w pamięci, adres wynikowy zostanie umieszczony w R0, a NCRN jest ustawiony na R1.

### <a name="stage-b-pre-padding-and-extension-of-arguments"></a>Etap B: wstępne uzupełnienie i rozszerzenie argumentów

Dla każdego argumentu na liście stosowana jest pierwsza reguła dopasowywania z następującej listy:

1. Jeśli argument jest typu złożonego, którego rozmiar nie może być statycznie określony przez obiekt wywołujący i wywoływany, argument jest kopiowany do pamięci i zastępowany przez wskaźnik do kopii.

1. Jeśli argument jest bajtem lub 16-bitową częścią wyrazu, jego wartość wynosi zero lub zostanie rozszerzona do 32-bitowego pełnego wyrazu i traktowana jako argument 4-bajtowy.

1. Jeśli argument jest typu złożonego, jego rozmiar jest zaokrąglany do najbliższej wielokrotności 4.

### <a name="stage-c-assignment-of-arguments-to-registers-and-stack"></a>Etap C: przypisanie argumentów do rejestrów i stosu

Dla każdego argumentu na liście są stosowane następujące reguły z kolei do momentu przydzielenia tego argumentu:

1. Jeśli argument jest typu Visual FoxPro i istnieje wystarczającą liczbę kolejnych przyznanych rejestrów Visual FoxPro odpowiedniego typu, argument jest przypisywany do najniższej numerowanej sekwencji takich rejestrów.

1. Jeśli argument jest typu Visual FoxPro, wszystkie pozostałe nieprzypisane rejestry są oznaczane jako niedostępne. NSAA jest dostosowywany w górę do momentu, aż zostanie prawidłowo wyrównany dla typu argumentu, a argument zostanie skopiowany do stosu w dopasowanym NSAA. Wartość NSAA jest zwiększana o rozmiar argumentu.

1. Jeśli argument wymaga 8-bajtowego wyrównania, NCRN jest zaokrąglany do następnego parzystego numeru rejestru.

1. Jeśli rozmiar argumentu w 32-bitowym słowie nie jest większy niż R4 minus NCRN, argument jest kopiowany do rejestrów podstawowych, rozpoczynając od NCRN, z najmniej znaczącymi bitami w przypadku rejestrów z niższymi numerami. NCRN jest zwiększana o liczbę używanych rejestrów.

1. Jeśli wartość NCRN jest mniejsza niż R4, a NSAA jest równa SP, argument jest dzielony między rejestrami podstawowymi a stosem. Pierwsza część argumentu jest kopiowana do rejestrów podstawowych, rozpoczynając od NCRN, w tym R3. Pozostała część argumentu jest kopiowana na stos, rozpoczynając od NSAA. NCRN jest ustawiona na R4, a wartość NSAA jest zwiększana o rozmiar argumentu minus kwota przeniesiona w rejestrach.

1. Jeśli argument wymaga 8-bajtowego wyrównania, NSAA jest zaokrąglany do następnego 8-bajtowego wyrównanego adresu.

1. Argument jest kopiowany do pamięci w NSAA. Wartość NSAA jest zwiększana o rozmiar argumentu.

Rejestry Visual FoxPro nie są używane dla funkcji wariadyczne, a zasady dotyczące etapu C i 2 są ignorowane. Oznacza to, że funkcja wariadyczne może rozpoczynać się od opcjonalnego wypychania {R0-R3}, aby dołączać argumenty rejestru do wszelkich dodatkowych argumentów przekazana przez obiekt wywołujący, a następnie uzyskiwać dostęp do całej listy argumentów bezpośrednio ze stosu.

Wartości typu integer są zwracane w R0, opcjonalnie rozszerzone do R1 dla 64-bitowych wartości zwracanych. Wartości typu zmiennoprzecinkowego Visual FoxPro/NEON lub SIMD są zwracane w S0, d0 lub Q0, zgodnie z potrzebami.

## <a name="stack"></a>Stos

Stos musi pozostać 4-bajtowy i musi być wyrównany 8-bajtowy w dowolnej granicy funkcji. Jest to wymagane do obsługi częstego używania operacji zablokowanych na 64-bitowych zmiennych stosu. EABI ARM wskazuje, że stos to 8-bajtowy wyrównany do dowolnego interfejsu publicznego. Aby zapewnić spójność, system Windows on ARM ABI traktuje wszystkie granice funkcji jako interfejs publiczny.

Funkcje, które muszą używać wskaźnika ramki — na przykład funkcje, które wywołają `alloca` lub które zmieniają Wskaźnik stosu dynamicznie — muszą skonfigurować wskaźnik klatki w R11 w funkcji prologu i pozostawić go bez zmian do epilogu. Funkcje, które nie wymagają wskaźnika ramki, muszą wykonać wszystkie aktualizacje stosu w prologu i pozostawić Wskaźnik stosu niezmieniony do epilogu.

Funkcje, które przydzielą 4 KB lub więcej na stosie, muszą mieć pewność, że każda strona przed ostatnią stroną jest w porządku. Gwarantuje to, że żaden kod nie może "przekroczyć" stron ochrony, które są używane przez system Windows do rozszerzenia stosu. Zwykle jest to wykonywane przez `__chkstk` pomocnika, który przekazuje całkowitą alokację stosu w bajtach podzieloną przez 4 w R4 i która zwraca końcową wartość przydziału stosu w bajtach z powrotem w R4.

### <a name="red-zone"></a>Czerwona strefa

8-bajtowy obszar bezpośrednio poniżej bieżącego wskaźnika stosu jest zarezerwowany do analizy i stosowania poprawek dynamicznych. Pozwala to na użycie dokładnie wygenerowanego kodu, w którym są przechowywane 2 rejestry w [SP, #-8], a tymczasowo używa ich do dowolnych celów. Jądro systemu Windows gwarantuje, że te 8 bajtów nie zostanie nadpisane, jeśli wystąpi wyjątek lub przerwa w trybie użytkownika i Tryb jądra.

### <a name="kernel-stack"></a>Stos jądra

Domyślny stos trybu jądra w systemie Windows to trzy strony (12 KB). Należy zachować ostrożność, aby nie tworzyć funkcji, które mają duże bufory stosu w trybie jądra. Przerwanie może potrwać z dużą ilością stosu i spowodować awarię stosu awaryjnego.

## <a name="cc-specifics"></a>Specyficzne dla języka C/C++

Wyliczenia są 32-bitowymi liczbami całkowitymi, chyba że co najmniej jedna wartość w wyliczeniu wymaga magazynu o wartości 64-bitowej podwójnego tekstu. W takim przypadku Wyliczenie zostanie podwyższone do 64-bitowej liczby całkowitej.

`wchar_t`jest zdefiniowane jako równoważne `unsigned short`, aby zachować zgodność z innymi platformami.

## <a name="stack-walking"></a>Idący stos

Kod systemu Windows jest kompilowany z włączonymi wskaźnikami ramki ([/Oy (pominięcie wskaźnika ramki)](reference/oy-frame-pointer-omission.md)), aby umożliwić szybkie przechodzenie na stosie. Ogólnie rzecz biorąc, rejestr R11 wskazuje następny link w łańcuchu, czyli parę {R11, LR}, która określa wskaźnik do poprzedniej klatki na stosie i adres zwrotny. Firma Microsoft zaleca, aby kod również włączał wskaźniki klatek do ulepszonego profilowania i śledzenia.

## <a name="exception-unwinding"></a>Odwracanie wyjątku

Odwinięcie stosu podczas obsługi wyjątków jest włączane przy użyciu kodów wywinięcia. Kody operacji unwind są sekwencją bajtów przechowywanych w sekcji. xdata obrazu wykonywalnego. Opisują one działanie funkcji prologu i epilogu Code w sposób abstrakcyjny, dzięki czemu efekty prologu funkcji mogą być cofnięte w celu odwinięcia ramki stosu obiektu wywołującego.

EABI ARM Określa model odwinięcia wyjątku, który używa kodów unwind. Jednakże Ta specyfikacja nie wystarcza do odwinięcia w systemie Windows, co musi obsługiwać przypadki, w których procesor znajduje się w środku prologu lub epilogu funkcji. Aby uzyskać więcej informacji o danych wyjątku ARM i rozwinięcia systemu Windows, zobacz temat [Obsługa wyjątków ARM](arm-exception-handling.md).

Zalecamy, aby kod wygenerowany dynamicznie został opisany przy użyciu tabel funkcji dynamicznych określonych w wywołaniach `RtlAddFunctionTable` i skojarzonych funkcjach, tak aby wygenerowany kod mógł uczestniczyć w obsłudze wyjątków.

## <a name="cycle-counter"></a>Licznik cyklu

Procesory ARM z systemem Windows są wymagane do obsługi licznika cykl, ale użycie licznika bezpośrednio może spowodować problemy. Aby uniknąć tych problemów, system Windows on ARM używa niezdefiniowanego kodu operacji do żądania znormalizowanej wartości licznika 64-bitowego cyklu. W języku C lub C++ Użyj `__rdpmccntr64` wewnętrznego, aby wyemitować odpowiedni opcode; z zestawu, użyj `__rdpmccntr64` instrukcji. Odczyt licznika cykl trwa około 60 cykli na Cortex-A9.

Licznik jest prawdziwym licznikiem cyklu, a nie zegarem; w związku z tym częstotliwość zliczania zależy od częstotliwości procesora. Jeśli chcesz zmierzyć czas, który upłynął, użyj `QueryPerformanceCounter`.

## <a name="see-also"></a>Zobacz też

[Typowe problemy przy migracji Visual C++ ARM](common-visual-cpp-arm-migration-issues.md)<br/>
[Obsługa wyjątków ARM](arm-exception-handling.md)
