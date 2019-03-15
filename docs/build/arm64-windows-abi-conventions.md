---
title: Przegląd Konwencji ARM64 ABI
ms.date: 07/11/2018
ms.openlocfilehash: 537f8cf5bb8db61854bea7f4624e3dd3176c6a59
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816545"
---
# <a name="overview-of-arm64-abi-conventions"></a>Przegląd Konwencji ARM64 ABI

Podstawowa ABI dla Windows podczas kompilowania i uruchamiania w procesorach ARM w trybie 64-bitowych (ARMv8 lub nowszej architektury), w przeważającej części następuje standardowa EABI AArch64 firmy ARM. W tym artykule opisano niektóre kluczowe założenia i zmiany z dokumentacji w EABI. Aby uzyskać informacji na temat interfejsu ABI 32-bitowych, zobacz [Konwencji ABI Przegląd ARM](overview-of-arm-abi-conventions.md). Aby uzyskać więcej informacji na temat standardowych EABI ARM, zobacz [aplikacji binarny interfejsu (ABI) dla architektury ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (link zewnętrzny).

## <a name="definitions"></a>Definicje

Wraz z wprowadzeniem Obsługa 64-bitowego ARM został zdefiniowany wiele warunków:

- **AArch32** — starszej wersji 32-bitowych rozkazów architektury (ISA) zdefiniowane przez ARM, w tym wykonywania w trybie Thumb.
- **AArch64** — nowe 64-bitowych rozkazów architektury (ISA) zdefiniowane przez ARM.
- **ARMv7** — Specyfikacja "generacja 7" ARM sprzętu, co obejmuje tylko obsługę AArch32. To jest wersja pierwszą wersję Windows dla ARM obsługiwany sprzęt ARM.
- **ARMv8** — Specyfikacja pokolenia"8" ARM sprzętu, co obejmuje obsługę zarówno AArch32, jak i AArch64.

Oprócz tych definicji w Windows używamy tych terminów:

- **ARM** — odnosi się do 32-bitowa architektura ARM (AArch32). Jest to czasami nazywane podają (Windows na ARM).
- **ARM32** — jest to taka sama jak ARM, powyżej; używanych w tym dokumencie w celu uściślenia.
- **ARM64** — odnosi się do architektury ARM 64-bitowych (AArch64). Brak coś takiego jak WoA64.

Na koniec przy odwoływaniu się do typów danych, następujące definicje z ARM do których istnieją odwołania:

- **Krótki wektor** — jest to typ danych, który jest bezpośrednio reprezentowanych w SIMD; czyli wektor pomagają w zrealizowaniu 8 lub 16 bajtów elementów wyrównane do rozmiaru (8 lub 16 bajtów), gdzie każdy element może być 1, 2, 4 lub 8 bajtów
- **HFA (jednorodnych zmiennopozycyjna agregacji)** — jest to typ danych członkom 2 – 4 identyczne zmiennoprzecinkowych (wartości zmiennoprzecinkowe lub wartości podwójnej precyzji)
- **HVA (jednorodnych krótki wektor agregacji)** — typ danych, z identycznymi członkami krótki wektor 2 – 4

## <a name="base-requirements"></a>Wymagania dotyczące podstawowej

Wersja architektury ARM64 Windows zakłada, że działa on ARMv8 lub nowszej architektury przez cały czas. Zarówno zmiennoprzecinkowe i pomocy technicznej NEON jest uznawana za tę obecny w sprzęcie.

Chociaż specyfikacji ARMv8 umożliwia pełną obsługę aplikacji AArch32, istnieją obecnie nie obsługuje uruchamiania istniejących aplikacji ARM32 w wersji ARM64 Windows (tj. nie plany dotyczące WOW64) jest planowane. Będzie zależała od ponownej oceny w przyszłości, ale jest bieżącym założeń pracy.

Specyfikacja ARMv8 opis nowego crypto opcjonalne i sumy kontrolnej pomocnika rozkazów AArch32 i AArch64. Pomoc techniczną dla tych jest obecnie opcjonalne, ale zalecane. Kod, które chcą korzystać z zalet tych rozkazów należy wykonywać testy środowiska uruchomieniowego dla ich istnienia.

## <a name="endianness"></a>Kolejność bajtów

Jak za pomocą ARM32 wersji systemu Windows na Windows ARM64 wykonuje w trybie little-endian. Przełączanie kolejność bajtów jest trudny do osiągnięcia bez obsługi trybu jądra w AArch64, dzięki czemu łatwiej jest je wymuszania.

## <a name="alignment"></a>Wyrównanie

Uruchomione dla procesorów ARM64 Windows umożliwia sprzętu Procesora do obsługi niewyrównane dostępy do w sposób niewidoczny dla użytkownika. W poprawę AArch32 ta obsługa również działa teraz dla wszystkich dostępów całkowitą (w tym uzyskuje dostęp do wielu słów) i zmiennoprzecinkowych uzyskuje dostęp do.

Jednak dostęp do pamięci bez buforowania (urządzenia) nadal muszą zawsze być wyrównane. Oznacza to, że jeśli występuje kod, który może być wywołana na do odczytu/zapisu niewyrównanych danych z pamięci bez buforowania, należy ją odtworzyć rzeczy, bezpieczne i upewnij się, że wszystkie dostępy do są wyrównane.

## <a name="integer-registers"></a>Rejestruje liczbę całkowitą

Architektura AArch64 obsługuje 32 rejestrów liczby całkowitej, podsumowano poniżej:

|Rejestruj|Nietrwałe?|Rola|
|-|-|-|
x0|Volatile|Parametr/podstaw Zarejestruj 1, zarejestruj się wynik
x1-x7|Volatile|Parametr/podstaw rejestru od 2 do 8
x8-x15|Volatile|Rejestruje pliki tymczasowe
x16-x17|Volatile|Rejestruje pliki tymczasowe wewnątrz procedury wywołania
x18|Non-volatile|Rejestr platformy: w trybie jądra wskazuje KPCR dla bieżącego procesora; w trybie użytkownika wskazuje TEB
x19-x28|Non-volatile|Rejestruje pliki tymczasowe
x29/fp|Non-volatile|Wskaźnik ramki
x30/lr|Non-volatile|Rejestruje łącza

Każdego rejestru można uzyskać dostęp, jako wartość pełnej 64-bitowych (za pośrednictwem x0 x30) lub jako 32-bitową wartość (za pośrednictwem w0 w30). 32-bitowe operacje zero — rozszerzenie osiągnęli maksymalnie 64-bitowy.

Zobacz przekazywanie sekcji, aby uzyskać szczegółowe informacje związane z użyciem rejestrów parametr parametru.

Pamiętaj, że w przeciwieństwie do AArch32, komputer i PS nie są indeksowane rejestrów i dlatego są ograniczone w jaki sposób można uzyskać dostęp. Zwróć uwagę, że nie x31 rejestrują (który kodowanie jest używane do specjalnych celów).

Korzystanie z wskaźnik ramki (x29) jest wymagane dla zachowania zgodności z szybkie przechodzenie po stosie posługują się zdarzeń systemu Windows i innych usług. Musi wskazywać na poprzednim {x29, x 30} pary na stosie.

## <a name="floating-pointsimd-registers"></a>Rejestruje Floating point/SIMD

Architektura AArch64 obsługuje również 32 rejestrów floating point/SIMD, podsumowano poniżej:

Rejestruj|Nietrwałe?|Rola
|-|-|-|
v0|Volatile|Parametr/podstaw Zarejestruj 1, zarejestruj się wynik
v1-v7|Volatile|Parametr/podstaw rejestruje od 2 do 8
v8-v15|Non-volatile|Pliki tymczasowe rejestrów (należy pamiętać, że niski 64 bity są trwałej)
v16-v31|Volatile|Rejestruje pliki tymczasowe

Każdego rejestru można uzyskać dostęp jako pełna wartość 128-bitowego (za pośrednictwem v0 v31 lub q0 q31), jako wartość 64-bitowa (za pośrednictwem d0-d31) jako 32-bitową wartość (za pośrednictwem s0-s31), jako wartość 16-bitowych (za pośrednictwem h0 h31) lub jako wartości 8-bitowa (za pośrednictwem b0 b31). Uzyskuje dostęp do mniejszy niż 128 bitów dostęp tylko niższe bitów rejestru 128 bitów i pozostawienie pozostałych bitów w charakterze, chyba że określono inaczej. (Zwróć uwagę, że to znacznie różnią się od AArch32, gdzie mniejszych rejestrów umieszczono je na podstawie rejestrów większy).

Oprócz rejestrów danych na różne pola bitów w nim rejestrowanie sterowania zmiennoprzecinkowego (FPCR) wiążą się pewne wymagania:

Bity|Znaczenie|Nietrwałe?|Rola
|-|-|-|-|
26|AHP|-Volatile|Alternatywne formant precyzji połowie
25|NAZWA WYRÓŻNIAJĄCA|-Volatile|Domyślny formant tryb NaN
24|FZ|Non-volatile|Kontrolka trybu opróżniania do zera.
23-22|RMode|Non-volatile|Tryb formant zaokrąglenia
15,12-8|IDE/IXE/etc|-Volatile|Wyjątek przechwytywania włączenie usługi bits, zawsze musi mieć wartość 0

## <a name="system-registers"></a>System rejestrów

Jak AArch32 Specyfikacja AArch64 zawiera trzy kontrolowane przez system "identyfikator wątku" rejestrów, które są używane przydzielone następujące:

Rejestruj|Rola
|-|-|
TPIDR_EL0|Zarezerwowany
TPIDRRO_EL0|Zawiera numer procesora CPU dla bieżącego procesora
TPIDR_EL1|Wskazuje strukturę KPCR dla bieżącego procesora

## <a name="floating-point-exceptions"></a>Wyjątki zmiennoprzecinkowe

Obsługa wyjątków zmiennoprzecinkowych IEEE jest opcjonalny w systemach AArch64. Wariantów procesora, które mają wyjątków zmiennoprzecinkowych sprzętu jądra Windows zostaje niezauważenie przechwycony wyjątek i niejawnie wyłącza je w rejestrze FPCR. Zapewnia zachowanie znormalizowane różnych wariantów procesora to (w przeciwnym razie kod opracowany na platformie bez Obsługa wyjątków może się okazać się biorąc nieoczekiwane wyjątki podczas uruchamiania na wielu platform z obsługą).

## <a name="parameter-passing"></a>Przekazywanie parametru

W przypadku funkcji innych zmiennych Windows ABI jest zgodna z regułami określonymi przez ARM dla parametru, przekazując. Te reguły pochodzą bezpośrednio ze standardowego wywołania procedury dla architektury AArch64:

### <a name="stage-a--initialization"></a>Etap A — inicjowanie

Ten etap jest wykonywane tylko raz, przed rozpoczęciem przetwarzania argumentów.

1. Następny General-purpose zarejestrować numer (NGRN) jest równa zero.

1. Dalej SIMD i zmiennopozycyjna zarejestrować numer (NSRN) jest równa zero.

1. Adres następnego skumulowany argumentu (NSAA) jest równa bieżąca wartość wskaźnika stosu (SP).

### <a name="stage-b--pre-padding-and-extension-of-arguments"></a>Etap B — wstępne wypełnienie i rozszerzenie argumentów

W każdy argument na liście jest stosowane pierwsza pasująca reguła z poniższej listy. Jeśli nie reguły dopasowania argument jest używany w niezmienionej postaci.

1. Jeśli typ argumentu jest typu złożonego, którego rozmiar nie można ustalić statycznie przez obiekt wywołujący i obiekt wywoływany, argument jest kopiowany do pamięci, a argument jest zastępowany przez wskaźnik do skopiowania. (Nie ma żadnych takich typów, jak w języku C/C++, ale istnieją one w innych językach lub rozszerzenia językowe).

1. Jeśli typ argumentu jest HFA lub HVA, a następnie jest używany argument zostały zmodyfikowane.

1. Jeśli typ argumentu jest typ złożony, który jest większy niż 16-bajtowy, argument jest kopiowany do pamięci przydzielonej przez obiekt wywołujący i argument jest zastępowany przez wskaźnik do skopiowania.

1. Jeśli typ argumentu jest typem złożonym rozmiar argumentu jest zaokrąglana w górę do najbliższej wielokrotności 8 bajtów.

### <a name="stage-c--assignment-of-arguments-to-registers-and-stack"></a>Etap C — przypisanie argumenty do rejestrów i stosu

Dla każdego argumentu na liście następujące reguły są stosowane z kolei, dopóki nie została przydzielona argument. Jeśli argument jest przypisana do rejestru nieużywane wszystkie bity, które są dostępne w rejestrze ma nie określono tego parametru wartości. Gdy argument jest przypisany do miejsca na stosie wszelkie bajtów uzupełniających nieużywane mają nie określono tego parametru wartości.

1. Jeśli argument jest pół-, jedno-, Double - lub cztery precyzji zmiennoprzecinkowego lub typu krótkiego wektora i NSRN jest mniejsze niż 8, a następnie argument jest przydzielany do najmniej znaczących bitów v rejestru [NSRN]. NSRN jest zwiększany o jeden. Argument została przydzielona.

1. Jeśli argument jest HFA lub HVA są wystarczające nieprzydzielone SIMD i rejestrów zmiennoprzecinkowych (NSRN + liczba elementów członkowskich ≤ 8), argument jest przydzielany SIMD i zmiennopozycyjna rejestruje (za pomocą jednego rejestru poszczególnych członków HFA lub HVA). NSRN jest zwiększany przez liczbę rejestry używane. Argument została przydzielona.

1. Jeśli argument jest HFA lub HVA NSRN jest równa 8, a rozmiar argumentu jest zaokrąglana w górę do najbliższej wielokrotności 8 bajtów.

1. Jeśli argument jest HFA HVA cztery precyzji zmiennoprzecinkowego lub krótki wektor wpisz NSAA jest zaokrąglany do większego z 8 lub naturalnego wyrównania składowej typu argumentu.

1. Jeśli argument jest typem zmiennoprzecinkowej połowie lub pojedynczej precyzji, rozmiar argumentu jest ustawiony na 8 bajtów. Efekt tak, jakby było argument został skopiowany do najmniej znaczące bity 64-bitowego rejestru i pozostałych bitów wypełnione wartościami nieokreślony.

1. Jeśli argument jest HFA, HVA, pół-, jedno-, Double - lub cztery precyzji zmiennoprzecinkowego lub typu krótkiego wektora, a następnie argument jest kopiowany do pamięci na skorygowany NSAA. NSAA jest zwiększany o rozmiar argumentu. Argument została przydzielona.

1. Jeśli argument jest całkowitego lub typu wskaźnika, rozmiar argumentu jest większa niż 8 bajtów i NGRN jest mniejsze niż 8, argument jest kopiowany do najmniej znaczących bitów w x [NGRN]. NGRN jest zwiększany o jeden. Argument została przydzielona.

1. Jeśli argument ma wyrównanie 16 NGRN jest zaokrąglana w górę do najbliższej parzystej liczby.

1. Jeśli argument jest typem całkowitym, rozmiar argumentu jest równy 16 i NGRN jest mniejszy niż 7, argument jest kopiowany do x [NGRN] i x [NGRN + 1]. x [NGRN] zawiera niższe zaadresowane double — słowo pamięci reprezentacji w postaci argumentu. NGRN jest zwiększany przez dwa. Argument została przydzielona.

1. Jeśli argument jest typem złożonym i rozmiar w słowa podwójne argumentu nie jest więcej niż 8 minus NGRN, a następnie argument jest kopiowana do kolejnych rejestrów ogólnego przeznaczenia, począwszy od stawki x [NGRN]. Argument jest przekazywany tak, jakby został załadowany do rejestrów z adresu wyrównane do słowa podwójne przy użyciu odpowiedniej sekwencji instrukcji LDR ładowanie kolejnych rejestrów z pamięci (zawartość częściami nieużywanych rejestrów są nieokreślone przez ten standard). NGRN jest zwiększany przez liczbę rejestry używane. Argument została przydzielona.

1. NGRN jest ustawiony na 8.

1. NSAA jest zaokrąglana do większego z 8 lub naturalnego wyrównania składowej typu argumentu...

1. Jeśli argument jest typu złożonego argument jest kopiowany do pamięci na skorygowany NSAA. NSAA jest zwiększany o rozmiar argumentu. Argument została przydzielona.

1. Jeśli rozmiar argumentu jest mniejsza niż 8 bajtów rozmiar argumentu jest ustawiony na 8 bajtów. Efekt jest tak, jakby argument został skopiowany do najmniej znaczące bity 64-bitowego rejestru i pozostałych bitów wypełnione wartościami nieokreślony.

1. Argument jest kopiowany do pamięci na skorygowany NSAA. NSAA jest zwiększany o rozmiar argumentu. Argument została przydzielona.

### <a name="addendum-variadic-functions"></a>Dodatek: Funkcje ze zmienną liczbą argumentów

Funkcje, które przyjmują zmienną liczbę argumentów są obsługiwane inaczej niż powyżej, w następujący sposób:

1. Wszystkie złożone są traktowane jako konta; nie specjalnego traktowania HFAs lub HVAs.

1. SIMD i rejestruje zmiennopozycyjna nie są używane.

Skutecznie równa to następujące reguły C.12–C.15 przydzielić argumenty urojone stosu, gdzie pierwszy 64 bajtów stosu są ładowane do x0 x7 i wszelkie pozostałe argumenty stosu są umieszczane w zwykły sposób.

## <a name="return-values"></a>Zwracane wartości

Wartości całkowitych są zwracane w x0. Wartości zmiennoprzecinkowe są zwracane w s0/d0/v0 zgodnie z potrzebami.

Do zwrócenia przez wartość, nie mogą być przekazywane za pośrednictwem rejestrów obiekt wywołujący zachowuje blok pamięci w procentach wystarczający rozmiar i wyrównanie na potrzeby przechowywania wyniku. Adres bloku pamięci jest przekazywany jako dodatkowy argument do funkcji w x8 dla typu POD lub x0 (lub x1 Jeśli $te informacje są przekazywane w x0) dla typu non-POD. Obiekt wywoływany może modyfikować blok pamięci wynik w dowolnym momencie podczas wykonywania procedury podrzędnej (jest wymagane dla / / wywoływany zachować wartość przechowywaną w x8, ale dla non-POD, adres tego buforu również musi być zwracane w x0 przez wywoływanego).

## <a name="stack"></a>Stos

Następujące ABI ogłoszonym przez ARM stos musi pozostać 16-bajtowy dostosowane przez cały czas. AArch64 zawiera funkcja sprzętowa, która generuje wyrównania stosu błędów zawsze wtedy, gdy jest wykonywane względem SP obciążenia lub magazynu i PS jest nie 16-bajtowy wyrównane. Windows działa z tą funkcją włączone przez cały czas.

Funkcje, które przydzielić 4k co najmniej warte stosu należy się upewnić, że jest korzysta z każdej strony przed ostatnią stronę w kolejności, co pozwala na zapewnienie żaden kod nie może "przeć za pośrednictwem" stron ochrony, używane przez program Windows do rozwijania stosu. Zazwyczaj jest to realizowane przez `__chkstk` pomocnika, która ma niestandardowy Konwencja wywoływania spełniającą alokacji stosu całkowita podzielona przez 16 w x8.

## <a name="red-zone"></a>Czerwony strefy

16-bajtowy obszar bezpośrednio pod bieżący wskaźnik stosu jest zarezerwowany do użycia podczas analizy i dynamiczne, poprawianie scenariuszy. Pozwala to na dokładnie wygenerowany kod ma zostać wstawiony, która przechowuje 2 rejestrów w [sp nr 16] oraz tymczasowo są one używane do celów dowolnego. Jądra Windows gwarantuje, że te 16-bajtowy nie zostaną zastąpione, jeśli wystąpi wyjątek lub przerwania jest pobierana w trybie użytkownika i jądra.

## <a name="kernel-stack"></a>Stos jądra

Stosu trybu jądra domyślne w Windows to sześć stron (24k). W trybie jądra, należy zwracać szczególną uwagę do funkcji ze stosu dużych buforów. Ill-timed przerwania może pochodzić za pomocą bardzo mało sporo miejsca i Utwórz wyniki operacji alarm stosu.

## <a name="stack-walking"></a>Przechodzenie po stosie

Kod w Windows jest kompilowany za pomocą wskaźników ramek włączone ([/Oy-](reference/oy-frame-pointer-omission.md)) umożliwiające szybkie stos. Upshot to to, że x29 (fp) zwykle wskazuje łącze do następnej w łańcuchu, czyli {fp, lr} pary wskazujący wskaźnik do poprzedniej ramki na stosie i adres zwrotny. Zaleca się kodu innych firm również włączyć wskaźników ramek w celu umożliwienia ulepszone profilowania i śledzenia.

## <a name="exception-unwinding"></a>Odwijanie wyjątków

Odwijanie podczas obsługi wyjątków jest wspierana przy użyciu kodów unwind. Kody unwind to sekwencja bajtów przechowywanych w sekcji .xdata pliku wykonywalnego, które opisują działania prologu i epilogu w sposób abstrakcyjne w taki sposób, że efekty prologu funkcji mogą zostać cofnięte w ramach przygotowania do kopie zapasowe na Ramka stosu obiektu wywołującego. Aby uzyskać więcej informacji o kodach unwind zobacz [obsługi wyjątków ARM64](arm64-exception-handling.md).

ARM EABI określa również model odwijania wyjątków wykorzystuje kodów odwinięcia. Jednak specyfikacji prezentowany jest niewystarczająca do rozwinięcia w Windows, który musi obsługiwać przypadki, w której komputer jest w trakcie prologu i epilogu funkcji.

Powinny być opisane kod, który jest generowana dynamicznie przy użyciu funkcji dynamicznej tabel za pomocą `RtlAddFunctionTable` i skojarzone funkcje, tak aby wygenerowanego kodu mogą uczestniczyć w programie obsługi wyjątków.

## <a name="cycle-counter"></a>Licznik cyklu

Wszystkie procesory ARMv8 są wymagane do obsługi cyklu licznika rejestru. Jest to rejestru 64-bitowym, który konfiguruje Windows, aby można było odczytać na dowolnym poziomie wyjątku (w tym trybie użytkownika). Jest możliwy za pośrednictwem specjalnego PMCCNTR_EL0 zarejestrować, przy użyciu MSR opcode w kodzie zestawu lub `_ReadStatusReg` wewnętrzne w kodzie języka C/C++.

Zwróć uwagę, że wartość licznika cyklu licznika cyklu wartość true, nie zegara tablicy i związku z tym zliczania częstotliwości będą się różnić z częstotliwością procesora. Jeśli uważasz, że musisz wiedzieć, częstotliwości licznika cyklu, możesz nie powinny używać licznika cyklu. Zamiast tego chcesz zmierzyć czas zegarowy, dla którego należy używać `QueryPerformanceCounter`.

## <a name="see-also"></a>Zobacz także

[Typowe problemy przy migracji Visual C++ ARM](common-visual-cpp-arm-migration-issues.md)<br/>
[Obsługa wyjątków ARM64](arm64-exception-handling.md)
