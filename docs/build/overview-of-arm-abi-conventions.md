---
title: Przegląd Konwencji ABI ARM
ms.date: 07/11/2018
ms.assetid: 23f4ae8c-3148-4657-8c47-e933a9f387de
ms.openlocfilehash: 17f2598912879d0eb54fd189e1fae541ba2f874f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295245"
---
# <a name="overview-of-arm32-abi-conventions"></a>Przegląd Konwencji ABI ARM32

Interfejsem binarnym aplikacji (ABI) dla kodu skompilowane dla Windows na procesorach ARM opiera się na standardowych EABI ARM. W tym artykule opisano podstawowe różnice między Windows na ARM i standard. W tym dokumencie opisano ARM32 ABI. Aby uzyskać informacji na temat interfejsu ABI ARM64, zobacz [Konwencji ABI Przegląd architektury ARM64](arm64-windows-abi-conventions.md). Aby uzyskać więcej informacji na temat standardowych EABI ARM, zobacz [aplikacji binarny interfejsu (ABI) dla architektury ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (link zewnętrzny).

## <a name="base-requirements"></a>Wymagania dotyczące podstawowej

Windows na ARM zakłada, że działa on architektury ARMv7 przez cały czas. Obsługa modelu zmiennoprzecinkowego w postaci VFPv3 D32 lub nowszy musi być obecny w sprzęcie. Visual FOXPRO musi obsługiwać zarówno pojedynczej precyzji, jak i podwójnej precyzji zmiennoprzecinkowych sprzętu. Środowisko wykonawcze Windows nie obsługuje emulację zmiennoprzecinkową, aby umożliwić wykonywanie na sprzęcie, inne niż Visual FOXPRO.

Zaawansowana obsługa rozszerzenia SIMD (NEON) — obejmuje to liczba całkowita i operacji zmiennoprzecinkowych — musi być obecny w sprzęcie. Brak obsługi środowiska wykonawczego emulacji podano.

Obsługa dzielenia liczby całkowitej (UDIV/SDIV) jest zdecydowanie zaleca się, ale nie jest wymagane. Platformy, które nie obsługują dzielenie liczby całkowitej może spowodować zmniejszenie wydajności, ponieważ te operacje mają być zablokował i ewentualnie zastosować poprawki.

## <a name="endianness"></a>Kolejność bajtów

Windows na ARM wykonuje się w trybie little-endian. Kompilator MSVC i środowisko wykonawcze Windows oczekiwać, że dane little-endian przez cały czas. Chociaż ustawić SETEND instrukcji w instrukcji ARM architektura (ISA) umożliwia kod nawet trybu użytkownika, aby zmienić bieżący kolejność bajtów, wykonanie tej tak nie jest zalecane jest niebezpieczny dla aplikacji. Jeśli wyjątek jest generowany w trybie big-endian zachowanie jest nieprzewidywalne i może prowadzić do błędów aplikacji w trybie użytkownika lub operacji wykrywania błędów w trybie jądra.

## <a name="alignment"></a>Wyrównanie

Mimo że Windows umożliwia sprzętu ARM do obsługi liczby całkowitej niewyrównane uzyskuje dostęp do przejrzysty, wyrównanie, które błędy nadal mogą być generowane w niektórych sytuacjach. Należy wykonać następujące czynności dla wyrównania:

- Połowa word o rozmiarze (16-bitowy) o rozmiarze word liczby całkowitej (32-bitowy), ładuje i magazyny nie muszą być wyrównane. Sprzęt obsługuje je, wydajne i w sposób niewidoczny dla użytkownika.

- Zmiennoprzecinkowe obciążeń i magazynów, powinno być wyrównane. Jądro obsługuje niewyrównanych obciążenia i są przechowywane w sposób niewidoczny dla użytkownika, ale z znaczne obciążenie.

- Ładowanie lub przechowywać podwójnej precyzji (LDRD/STRD) i wiele operacji (LDM/STM) powinno być wyrównane. Jądro obsługuje większość z nich w sposób niewidoczny dla użytkownika, ale z znaczne obciążenie.

- Wszystkie dostępy do pamięci bez buforowania muszą być wyrównane, nawet w przypadku uzyskuje dostęp do liczby całkowitej. Niewyrównane dostępy spowodować błąd wyrównania.

## <a name="instruction-set"></a>Zestaw instrukcji

Instrukcja dla Windows na ARM jest ograniczone do Thumb-2. Cały kod wykonywany na tej platformie oczekuje się, aby uruchomić i pozostają w trybie podglądu przez cały czas. Próba przełączenia się do starszej wersji zestaw instrukcji ARM może się powieść, ale jeśli tak, wszystkie wyjątki lub przerwania występujących może prowadzić do błędów aplikacji w trybie użytkownika lub operacji wykrywania błędów w trybie jądra.

Efektem ubocznym tego wymagania jest wszystkie wskaźniki kod musi bit niski, wartość. Jest to tak, aby podczas są ładowane i rozgałęziony do za pośrednictwem BLX lub BX, procesor będzie pozostawać w trybie podglądu, a nie podejmie próby wykonania kodu docelowego jako 32-bitowe instrukcje ARM.

### <a name="it-instructions"></a>Instrukcje IT

Użycie IT zgodnie z instrukcjami w kod Thumb-2 jest niedozwolone z wyjątkiem tych określonych przypadków:

- Instrukcja IT należy używać tylko do modyfikowania jednej instrukcji docelowej.

- Instrukcji docelowej musi być instrukcja 16-bitowych.

- Instrukcji docelowej musi mieć jedną z nich:

   |Rozkazów 16-bitowych|Class|Ograniczenia|
   |---------------------|-----------|------------------|
   |MOV, MVN|Przenieś|Menedżer zasobów! = PC, usług pulpitu zdalnego! = PC|
   |LDR, LDR[S]B, LDR[S]H|Ładowanie z pamięci|Ale nie LDR literału formularzy|
   |STR, STRB, STRH|Store pamięci||
   |ADD, ADC, RSB, SBC, SUB|Dodaj lub Odejmij|Ale nie SP ADD/SUBSKRYBOWANIA, PS, imm7 formularzy<br /><br /> Menedżer zasobów! = PC, Rdn! = PC, od Rdm! = PC|
   |CMP, CMN|{1&gt;Compare&lt;1}|Menedżer zasobów! = PC, Rn! = PC|
   |MUL|Mnożenie||
   |ASR, LSL, LSR, ROR|Przesunięcie bitu||
   |AND, BIC, EOR, ORR, TST|Bitowe operacje arytmetyczne||
   |BX|Gałąź do zarejestrowania|Menedżer zasobów! = PC|

Mimo że bieżący ARMv7 procesorów CPU, nie można zgłosić użycia formularzy niedozwoloną instrukcję, przyszłych generacji powinny. W przypadku wykrycia tych postaci dowolnego programu, który używa tych może zostać zakończona z powodu wyjątku niezdefiniowane instrukcji.

### <a name="sdivudiv-instructions"></a>Instrukcje SDIV/UDIV

Korzystanie z liczbą całkowitą podzielić SDIV i UDIV jest w pełni obsługiwane, nawet na platformach bez natywnego sprzętu do obsługi tych instrukcji. Koszt pojedynczego SDIV lub UDIV dzielenia na procesorze Cortex A9 jest około 80 cykle, oprócz całkowity czas dzielenia 20-250 cykli, w zależności od danych wejściowych.

## <a name="integer-registers"></a>Rejestruje liczbę całkowitą

Procesor ARM obsługuje 16 rejestrów liczbą całkowitą:

|Rejestruj|Nietrwałe?|Rola|
|--------------|---------------|----------|
|r0|Volatile|Parametr, wynik, pliki tymczasowe rejestr 1|
|r1|Volatile|Parametr, wynik, pliki tymczasowe rejestru 2|
|r2|Volatile|Parametr, pliki tymczasowe rejestru 3|
|r3|Volatile|Parametr, pliki tymczasowe rejestru 4|
|R4|Non-volatile||
|r5|Non-volatile||
|r6|Non-volatile||
|r7|Non-volatile||
|R8|Non-volatile||
|r9|Non-volatile||
|R10|Non-volatile||
|r11|Non-volatile|Wskaźnik ramki|
|r12|Volatile|Zarejestruj się wewnątrz procedury wywołania pliki tymczasowe|
|r13 (SP)|Non-volatile|Wskaźnik stosu|
|R14 (LR)|Non-volatile|Zarejestruj się łącze|
|r15 (PC)|Non-volatile|Licznik programu|

Aby uzyskać szczegółowe informacje o sposobie używania parametrów i zwracanej wartości w rejestrach, zobacz sekcję przekazywania parametru, w tym artykule.

Windows używa r11 zalet fast ramki stosu. Aby uzyskać więcej informacji zobacz sekcję stos. Ze względu na to wymaganie r11 musi wskazywać na łącze znajdujące się najwyżej w łańcuchu przez cały czas. Nie używaj r11 do ogólnych celów — kod nie wygeneruje przeszukiwań stosu poprawny podczas analizy.

## <a name="vfp-registers"></a>Rejestruje Visual FOXPRO

Windows obsługuje tylko wariantów ARM, które mają Koprocesor VFPv3 D32 pomocy technicznej. Oznacza to rejestrów zmiennoprzecinkowych są zawsze obecne i może polegać na przekazywanie parametru i że pełny zestaw rejestrów 32 jest dostępny do użytku. Rejestruje Visual FOXPRO i podsumowanie ich użycia można znaleźć w tej tabeli:

|Wybiera|podwojenia|Quads|Nietrwałe?|Rola|
|-------------|-------------|-----------|---------------|----------|
|s0 s3|d0-d1|q0|Volatile|Parametry, wyniku scratch rejestru|
|S7 — S4|d2 d3|q1|Volatile|Rejestrowanie parametrów, pliki tymczasowe|
|s8 s11|D4 d5|q2|Volatile|Rejestrowanie parametrów, pliki tymczasowe|
|s12-s15|D6 d7|q3|Volatile|Rejestrowanie parametrów, pliki tymczasowe|
|s16-s19|D8 d9|q4|Non-volatile||
|s20-s23|D10 d11|q5|Non-volatile||
|s24-s27|D12 d13|q6|Non-volatile||
|S28 s31|D14 d15|q7|Non-volatile||
||D16 d31|q8-q15|Volatile||

W następnej tabeli przedstawiono stanu zmiennoprzecinkowego i kontroli zarejestrować pola bitów (FPSCR):

|Bity|Znaczenie|Nietrwałe?|Rola|
|----------|-------------|---------------|----------|
|31-28|NZCV|Volatile|Flagi stanu|
|27|QC|Volatile|Nasycenie zbiorcza|
|26|AHP|Non-volatile|Alternatywne formant precyzji połowie|
|25|NAZWA WYRÓŻNIAJĄCA|Non-volatile|Domyślny formant tryb NaN|
|24|FZ|Non-volatile|Kontrolka trybu opróżniania do zera.|
|23-22|RMode|Non-volatile|Tryb formant zaokrąglenia|
|21-20|Pobieżne|Non-volatile|Vector — Stride, zawsze musi mieć wartość 0|
|18-16|Len|Non-volatile|Długość wektora, zawsze musi mieć wartość 0|
|15, 12-8|IDE, IXE, etc.|Non-volatile|Wyjątek przechwytywania włączenie usługi bits, zawsze musi mieć wartość 0|
|7, 4-0|IDC, IXC, etc.|Volatile|Flagi zbiorczą wyjątku|

## <a name="floating-point-exceptions"></a>Wyjątki zmiennoprzecinkowe

Większość sprzętu ARM nie obsługuje wyjątki zmiennoprzecinkowe IEEE. Na wariantów procesora, które mają wyjątków zmiennoprzecinkowych sprzętu jądra Windows zostaje niezauważenie przechwycony wyjątek i niejawnie wyłącza je do rejestru FPSCR. Dzięki temu znormalizowane zachowanie różnych wariantów procesora. W przeciwnym razie kod opracowany na platformie, która nie ma obsługi wyjątków może otrzymać nieoczekiwane wyjątki uruchamianego na platformie, która ma obsługiwać wyjątek.

## <a name="parameter-passing"></a>Przekazywanie parametru

W przypadku innych zmiennych funkcji Windows na ARM ABI regułom ARM dla parametru, przekazując — w tym rozszerzenia Visual FOXPRO i SIMD zaawansowane. Wykonaj te reguły [standardowe wywołanie procedury dla architektury ARM](http://infocenter.arm.com/help/topic/com.arm.doc.ihi0042c/IHI0042C_aapcs.pdf)skonsolidowanego z rozszerzeniem Visual FOXPRO. Przez domyślne pierwsze cztery liczby całkowitej argumentów i maksymalnie osiem zmiennoprzecinkowego lub vector argumenty są przekazywane w rejestrach, a dodatkowe argumenty są przekazywane na stosie. Argumenty są przypisane do rejestrów lub stosu przy użyciu tej procedury:

### <a name="stage-a-initialization"></a>Etap Odp.: Inicjalizacja

Inicjalizacja jest wykonywana tylko raz, przed rozpoczęciem przetwarzania argumentu:

1. Dalej Core zarejestrować numer (NCRN) jest ustawiona na r0.

1. Visual FOXPRO rejestrów, które są oznaczone jako nieprzydzielony.

1. Dalej skumulowany Argument adresu (NSAA) jest ustawiona na bieżącą SP.

1. Jeśli zostanie wywołana funkcja, która zwraca wynik w pamięci, adres wynik jest umieszczany w r0 i NCRN jest równa r1.

### <a name="stage-b-pre-padding-and-extension-of-arguments"></a>Etap B: Rozszerzenie argumentów i wstępne wypełnienie

Dla każdego argumentu na liście jest stosowane pierwsza pasująca reguła z następującej listy:

1. Jeśli argument jest typu złożonego, którego rozmiar nie można ustalić statycznie przez obiekt wywołujący i obiekt wywoływany, argument jest kopiowany do pamięci i zastąpione przez wskaźnik do skopiowania.

1. Jeśli argument jest bajt lub 16-bitowe pół słowo, następnie jest rozszerzony zero lub znak rozszerzony do programu word pełną 32-bitowe i traktowany jako argument 4-bajtowe.

1. Jeśli argument jest typu złożonego, jego rozmiar jest zaokrąglana w górę do najbliższej wielokrotności 4.

### <a name="stage-c-assignment-of-arguments-to-registers-and-stack"></a>Etap C: Przypisanie argumenty do rejestrów i stosu

Dla każdego argumentu na liście stosowane są następujące reguły z kolei, dopóki nie została przydzielona argument:

1. Jeśli argument jest typu Visual FOXPRO i następujących po sobie nieprzydzielone rejestry Visual FOXPRO odpowiedniego typu, argument jest przydzielany do najniższego numerowane sekwencji takich rejestrów.

1. Jeśli argument jest typu Visual FOXPRO, wszystkich pozostałych nieprzydzielonych rejestrów zostaną oznaczone jako czas niedostępności. NSAA jest dostosowywany do góry, dopóki nie jest prawidłowo wyrównany dla typu argumentu, a argument jest kopiowany do stosu na skorygowany NSAA. NSAA jest zwiększana o rozmiar argumentu.

1. Jeśli argument wymaga 8-bajtowe wyrównanie, NCRN jest zaokrąglana w górę do najbliższej liczby nawet rejestru.

1. Jeśli rozmiar argumentu w 32-bitowych słów nie jest więcej niż r4 minus NCRN, argument jest kopiowana do rejestrów core, w NCRN, począwszy od najmniej znaczące bity zajmuje niższych numerach rejestrów. NCRN jest zwiększany przez liczbę rejestry używane.

1. Jeśli NCRN jest mniejsza niż r4 NSAA jest równy PS, argument jest podzielony między rejestrów podstawowych i stosu. Pierwsza część argument jest kopiowana do rejestrów core, począwszy od NCRN, do i łącznie r3. W pozostałej części argument jest kopiowana na stosie, zaczynając od NSAA. NCRN ustawiono r4 a NSAA jest zwiększany o rozmiar argumentu, minus kwota przekazywane w rejestrach.

1. Jeśli argument wymaga 8-bajtowe wyrównanie, NSAA jest zaokrąglana w górę do następnego adresu wyrównany 8-bajtowych.

1. Argument jest kopiowana do pamięci na NSAA. NSAA jest zwiększany o rozmiar argumentu.

Visual FOXPRO rejestrów, które nie są używane do funkcji ze zmienną liczbą argumentów, a zasady C etap 1 i 2 są ignorowane. Oznacza to, czy funkcji ze zmienną liczbą argumentów można zaczynają się od opcjonalne wypychania {r0 r3} można poprzedzić argumenty Zarejestruj wszelkie dodatkowe argumenty przekazane przez obiekt wywołujący, a następnie przejść do listy argumentów całego bezpośrednio ze stosu.

Liczba całkowita typu wartości są zwracane w r0, opcjonalnie rozszerzony do r1 dla 64-bitowych wartości zwracanych. Visual FOXPRO/NEON zmiennoprzecinkowego lub SIMD typu wartości są zwracane w s0, d0 lub q0 zgodnie z potrzebami.

## <a name="stack"></a>Stos

Stos musi pozostać 4-bajtowego wyrównania przez cały czas i musi być 8-bajtowych wyrównany na granicy żadnych funkcji. Jest to wymagane w celu obsługi często są używane operacje blokowane w zmiennych stosu 64-bitowych. ARM EABI stanów, że stos jest 8-bajtowych wyrównane na dowolnego interfejsu publicznego. W celu zapewnienia spójności Windows na ARM ABI uwzględnia wszystkie granicę funkcji jako interfejsu publicznego.

Funkcje, które trzeba użyć wskaźnika ramki — na przykład funkcje to wywołanie `alloca` lub wskaźnik stosu, zmieniać dynamicznie — należy zdefiniować wskaźnik ramki w r11 w prologu funkcji i pozostaw je bez zmian do momentu epilogu. Funkcje, które nie wymagają wskaźnik ramki, należy wykonać wszystkie aktualizacje stosu w prologu i pozostaw bez zmian do momentu epilogu wskaźnik stosu.

Funkcje, które alokują 4 KB lub więcej informacji na temat stosu należy się upewnić, że każda strona przed ostatnią stronę jest dotknięciu w kolejności. Daje to gwarancję, że żaden kod nie może "przeć za pośrednictwem" stron ochrony, używane przez program Windows do rozwijania stosu. Zazwyczaj jest to realizowane `__chkstk` pomocnika, która jest przekazywana Alokacja całkowita stosu w bajtach podzielona przez 4 w r4 i zwraca kwoty alokacji stosu końcowe w bajtach w r4.

### <a name="red-zone"></a>Czerwony strefy

8-bajtowych obszar bezpośrednio pod bieżący wskaźnik stosu jest zarezerwowany dla analizy i dynamiczne poprawek. Pozwala to na dokładnie wygenerowany kod w celu wstawienia, która przechowuje 2 rejestrów w [sp # 8] oraz tymczasowo są one używane do celów dowolnego. Jądra Windows gwarantuje, że te 8 bajtów nie zostaną zastąpione, jeśli wystąpi wyjątek lub przerwania występuje zarówno w trybie użytkownika, jak i w trybie jądra.

### <a name="kernel-stack"></a>Stos jądra

Stosu domyślnego trybu jądra w Windows to trzy strony (12 KB). Uważaj, aby nie tworzyć funkcje, które mają duże stosu buforów w trybie jądra. Przerwania może pochodzić za pomocą bardzo mało stosu sporo miejsca i spowodować, że wyniki operacji alarm stosu.

## <a name="cc-specifics"></a>Szczegóły języka C/C++

Wyliczenia są typów 32-bitowej liczby całkowitej, chyba że co najmniej jednej wartości w wyliczeniu, wymaga 64-bitowych podwójne słowo magazynu. W takim przypadku wyliczenia jest podnoszony do typu 64-bitową liczbę całkowitą.

`wchar_t` są zdefiniowane jako równoważne `unsigned short`, w celu zachowania zgodności z innymi platformami.

## <a name="stack-walking"></a>Przechodzenie po stosie

Windows kod jest kompilowany za pomocą wskaźników ramek włączone ([/Oy (pominięcie wskaźnika ramki)](reference/oy-frame-pointer-omission.md)) umożliwiające szybkie stos. Ogólnie rzecz biorąc, r11 zarejestrować wskazuje następny link w łańcuchu, czyli {r11, lr} pary, który określa wskaźnik do poprzedniej ramki stosu i adres zwrotny. Zaleca się, że Twój kod również włączyć wskaźników ramek na lepsze profilowania i śledzenia.

## <a name="exception-unwinding"></a>Odwijanie wyjątków

Odwijanie podczas obsługi wyjątku stosu jest włączona przy użyciu kodów unwind. Kody unwind to sekwencja bajtów przechowywanych w sekcji .xdata obrazu pliku wykonywalnego. Opisano w nich wykonać kod prologu i epilogu funkcji w sposób abstrakcyjne tak, aby skutki prologu funkcji można cofnąć w ramach przygotowania do rozwinięcia do obiektu wywołującego ramki stosu.

ARM EABI określa odwijania model wyjątków, który używa kodów odwinięcia. Jednak ta specyfikacja nie wystarcza do rozwinięcia w Windows, który musi obsługiwać przypadki, w którym procesor jest w trakcie prologu i epilogu funkcji. Aby uzyskać więcej informacji na temat Windows na dane wyjątków ARM i odwinięcie zobacz [obsługi wyjątków ARM](arm-exception-handling.md).

Zaleca się, że dynamicznie generowanego kodu można uznać za pomocą funkcji dynamicznego tabel określone w wywołaniach `RtlAddFunctionTable` i skojarzone funkcje, tak aby wygenerowanego kodu mogą uczestniczyć w programie obsługi wyjątków.

## <a name="cycle-counter"></a>Licznik cyklu

Procesory ARM z systemem Windows są wymagane do obsługi licznika cyklu, ale bezpośrednio przy użyciu licznik mogą powodować problemy. Aby uniknąć tych problemów, Windows na ARM używa niezdefiniowanego opcode żądania znormalizowaną wartość licznika cyklu 64-bitowych. Z C lub C++, użyj `__rdpmccntr64` nierozerwalnie związane emitować odpowiedni kod operacji; z zestawu, należy użyć `__rdpmccntr64` instrukcji. Odczytywanie licznika cyklu zajmuje około 60 cykli na Cortex – A9.

Ten licznik jest licznikiem true cyklu, nie zegara; w związku z tym zliczania częstotliwość zależy od częstotliwości procesora. Aby zmierzyć zegara Upłynęło czasu, należy użyć `QueryPerformanceCounter`.

## <a name="see-also"></a>Zobacz także

[Typowe problemy przy migracji Visual C++ ARM](common-visual-cpp-arm-migration-issues.md)<br/>
[Obsługa wyjątków ARM](arm-exception-handling.md)
