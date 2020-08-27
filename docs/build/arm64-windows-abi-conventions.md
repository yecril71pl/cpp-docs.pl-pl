---
title: Przegląd konwencji ABI ARM64
ms.date: 03/27/2019
ms.openlocfilehash: bfe55513ffd24175dbe62efc6d5afcfd82f71e4c
ms.sourcegitcommit: 7f378314c5692d897ead10b7f6c96d4cb2abd266
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2020
ms.locfileid: "88972676"
---
# <a name="overview-of-arm64-abi-conventions"></a>Przegląd konwencji ABI ARM64

Podstawowy interfejs binarny aplikacji (ABI) dla systemu Windows podczas kompilowania i uruchamiania na procesorach ARM w trybie 64-bitowym (ARMv8 lub nowsza), w większości przypadków, zgodnie z standardowym EABI AArch64. W tym artykule przedstawiono niektóre z najważniejszych założeń i zmian z tego, co opisano w EABI. Aby uzyskać informacje o 32-bitowym ABI, zobacz [Omówienie Konwencji usługi ARM ABI](overview-of-arm-abi-conventions.md). Aby uzyskać więcej informacji na temat standardowego ARM EABI, zobacz [Application Binary Interface (ABI) dla architektury ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (Link zewnętrzny).

## <a name="definitions"></a>Definicje

Wraz z wprowadzeniem 64-bitowego wsparcia ARM definiuje kilka warunków:

- **AArch32** — starsza niż 32-bitowa architektura zestawu instrukcji (ISA) zdefiniowana przez ARM, w tym wykonywanie trybu przewijania.
- **AArch64** — Nowa 64-bitowa architektura zestawu instrukcji (ISA) zdefiniowana przez ARM.
- **Architektury ARMv7** — specyfikacja sprzętu ARM "siódma generacja", który obejmuje tylko obsługę AArch32. Ta wersja sprzętu ARM to pierwsza wersja systemu Windows dla usługi ARM.
- **ARMv8** — specyfikacja sprzętu ARM "ósmy generacja", który obejmuje obsługę zarówno AArch32, jak i AArch64.

System Windows używa również następujących warunków:

- **ARM** — oznacza 32-bitową architekturę ARM (AArch32), czasami nazywaną WoA (Windows on ARM).
- **ARM32** — taka sama jak ARM, powyżej; używany w tym dokumencie do przejrzystości.
- **Arm64** — dotyczy architektury ARM 64-bitowego (AArch64). Nie ma takiej WoA64.

Na koniec podczas odwoływania się do typów danych są odwoływane następujące definicje z usługi ARM:

- **Short-Vector** — typ danych, które można bezpośrednio przedstawić w SIMD, wektor 8 bajtów lub 16 bajtów elementów. Jest on wyrównany do jego rozmiaru, 8 bajtów lub 16 bajtów, gdzie każdy element może mieć wartość 1, 2, 4 lub 8 bajtów.
- **HFA (jednorodna agregacja zmiennoprzecinkowa)** — typ danych z 2 do 4 identycznych elementów członkowskich zmiennoprzecinkowych, wartości zmiennoprzecinkowe lub podwójne.
- **HVA (jednorodna funkcja globalnej agregacji wektorowej)** — typ danych z 2 do 4 identycznych elementów członkowskich krótkich wektorów.

## <a name="base-requirements"></a>Wymagania podstawowe

Wersja ARM64 systemu Windows zakłada, że jest uruchomiona w architekturze ARMv8 lub nowszej. Założenie, że obsługa zmiennoprzecinkowa i NEON jest obecna na sprzęcie.

Specyfikacja ARMv8 zawiera opis nowych opcjonalnych kodów operacji dla pomocników kryptograficznych i CRC zarówno dla AArch32, jak i AArch64. Obsługa dla nich jest obecnie opcjonalna, ale zalecana. Aby móc korzystać z tych kodów, aplikacje powinny najpierw przeprowadzić testy w czasie wykonywania.

## <a name="endianness"></a>Endian

Podobnie jak w przypadku wersji ARM32 systemu Windows, w programie ARM64 system Windows jest wykonywany w trybie little-endian. Nie ma potrzeby obsługi trybu jądra w AArch64, dzięki czemu można łatwiej wymusić przełączanie endian.

## <a name="alignment"></a>Wyrównanie

System Windows działający w systemie ARM64 umożliwia sprzętowe użycie procesora CPU w sposób niewidoczny dla użytkownika. W wyniku ulepszeń z AArch32 ta obsługa jest teraz również dostępna dla wszystkich dostępu do liczby całkowitej (w tym dostępu do tekstów) i dla dostępu zmiennoprzecinkowego.

Jednak dostęp do pamięci podręcznej (urządzenia) nadal musi być zawsze wyrównany. Jeśli kod może spowodować odczytanie lub zapisanie niewyrównanych danych z pamięci niebuforowanej, należy upewnić się, że są wyrównane wszystkie dostępy.

Domyślne wyrównanie układu dla ustawień regionalnych:

| Rozmiar w bajtach | Wyrównanie w bajtach |
| - | - |
| 1 | 1 |
| 2 | 2 |
| 3, 4 | 4 |
| > 4 | 8 |

Domyślne wyrównanie układu dla Globals i statics:

| Rozmiar w bajtach | Wyrównanie w bajtach |
| - | - |
| 1 | 1 |
| 2 - 7 | 4 |
| 8 - 63 | 8 |
| >= 64 | 16 |

## <a name="integer-registers"></a>Rejestry całkowite

Architektura AArch64 obsługuje rejestry całkowite 32:

| Zarejestruj | Volatile? | Rola |
| - | - | - |
| kolumn | Volatile | Parametr/rejestr wyrejestrowania 1, rejestr wyników |
| x1 — 120 | Volatile | Rejestr/Wyrejestrowanie 2-8 |
| x8 — x15 | Volatile | Rejestry |
| x16 — x17 | Volatile | Wewnętrzne rejestry wywołań |
| x18 | Nietrwały | Rejestracja platformy: w trybie jądra wskazuje KPCR dla bieżącego procesora; w trybie użytkownika wskazuje TEB |
| x19-x28 | Nietrwały | Rejestry |
| x29/FP | Nietrwały | Wskaźnik ramki |
| X30/LR | Nietrwały | Rejestry linków |

Do każdej rejestracji można uzyskać dostęp jako pełna wartość 64-bitowa (za pośrednictwem x0-X30) lub jako wartość 32-bitowa (za pośrednictwem W0-W30). 32-bitowe operacje zero — zwiększają ich wyniki do 64 bitów.

Zobacz sekcję przekazywanie parametrów, aby uzyskać szczegółowe informacje na temat używania rejestrów parametrów.

W przeciwieństwie do AArch32, licznik programu (komputer) i wskaźnik stosu (SP) nie są indeksowane rejestrów. Są one ograniczone do uzyskiwania dostępu do nich. Należy również zauważyć, że nie ma żadnego rejestru x31. To kodowanie jest używane do celów specjalnych.

Wskaźnik ramki (x29) jest wymagany w celu zapewnienia zgodności z szybkim poramie stosu używanym przez funkcję ETW i inne usługi. Musi ona wskazywać na poprzednią parę {x29, X30} na stosie.

## <a name="floating-pointsimd-registers"></a>Rejestry zmiennoprzecinkowe/SIMD

Architektura AArch64 obsługuje również 32 rejestrów zmiennoprzecinkowych/SIMD, podsumowujących poniżej:

| Zarejestruj | Volatile? | Rola |
| - | - | - |
| VO | Volatile | Parametr/rejestr wyrejestrowania 1, rejestr wyników |
| V1 — wersji 7 | Volatile | Rejestry parametrów/rejestrowania 2-8 |
| V8 — 15 | Nietrwały | Rejestry wstępne (tylko niskie 64 bitów są nietrwałe) |
| v16-v31 | Volatile | Rejestry |

Do każdego rejestru można uzyskać dostęp jako pełna wartość 128-bitowa (za pośrednictwem VO-v31 lub Q0-q31). Dostęp do niego można uzyskać jako wartość 64-bitowa (za pośrednictwem d0-D31) jako wartość 32-bitowa (za pośrednictwem S0-S31) jako wartość 16-bitowa (za pośrednictwem H0-H31) lub jako wartość 8-bitowa (za pośrednictwem B0-B31). Dostęp mniejszy niż 128 bitów uzyskuje dostęp tylko do dolnych bitów pełnego rejestru 128-bitowego. Pozostałe bity pozostają bez zmian, o ile nie określono inaczej. (AArch64 różni się od AArch32, gdzie mniejsze rejestry zostały spakowane na wyższym poziomie rejestrów).

Rejestr kontroli zmiennoprzecinkowej (FPCR) ma pewne wymagania dotyczące różnych pola bitów w nim:

| Bity | Znaczenie | Volatile? | Rola |
| - | - | - | - |
| 26 | AHP | Nietrwały | Alternatywny formant o połówkowej precyzji. |
| 25 | WYRÓŻNIAJĄC | Nietrwały | Domyślna kontrolka trybu NaN. |
| 24 | FZ | Nietrwały | Kontrolka trybu opróżniania do zera. |
| 23-22 | RMode | Nietrwały | Kontrolka tryb zaokrąglania. |
| 15, 12 – 8 | IDE/IXE/etc | Nietrwały | W przypadku usługi BITS pułapki wyjątków musi być zawsze równa 0. |

## <a name="system-registers"></a>Rejestry systemu

Podobnie jak w przypadku AArch32, Specyfikacja AArch64 zawiera trzy rejestry "Identyfikator wątku" sterowane systemem:

| Zarejestruj | Rola |
| - | - |
| TPIDR_EL0 | Zarezerwowany. |
| TPIDRRO_EL0 | Zawiera liczbę procesorów dla bieżącego procesora. |
| TPIDR_EL1 | Wskazuje strukturę KPCR dla bieżącego procesora. |

## <a name="floating-point-exceptions"></a>Wyjątki zmiennoprzecinkowe

Obsługa wyjątków zmiennoprzecinkowych IEEE jest opcjonalna w systemach AArch64. W przypadku wariantów procesora, które mają sprzętowe wyjątki zmiennoprzecinkowe, jądro systemu Windows dyskretnie przechwytuje wyjątki i niejawnie wyłącza je w rejestrze FPCR. Ta pułapka zapewnia znormalizowane zachowanie dla różnych wariantów procesora. W przeciwnym razie kod opracowany na platformie bez obsługi wyjątków może być w trakcie uruchamiania na platformie z obsługą nieoczekiwanych wyjątków.

## <a name="parameter-passing"></a>Przekazywanie parametrów

W przypadku funkcji innych niż wariadyczne system Windows ABI stosuje się do zasad określonych przez ARM na potrzeby przekazywania parametrów. Te reguły są przedstawione bezpośrednio w standardowym wywołaniu procedury dla architektury AArch64:

### <a name="stage-a--initialization"></a>Etap A — Inicjalizacja

Ten etap jest wykonywany dokładnie raz, przed rozpoczęciem przetwarzania argumentów.

1. Następny numer rejestru ogólnego przeznaczenia (NGRN) jest ustawiony na zero.

1. W następnym SIMD i liczbie zmiennoprzecinkowej rejestru (NSRN) jest ustawiona wartość zero.

1. Następny skumulowany adres argumentu (NSAA) jest ustawiony na bieżącą wartość wskaźnika stosu (SP).

### <a name="stage-b--pre-padding-and-extension-of-arguments"></a>Etap B — wstępne uzupełnienie i rozszerzenie argumentów

Dla każdego argumentu na liście stosowana jest pierwsza reguła dopasowywania z poniższej listy. Jeśli żadna reguła nie pasuje, argument jest używany niemodyfikowany.

1. Jeśli typ argumentu jest typem złożonym, którego rozmiar nie może być statycznie określony przez obiekt wywołujący i wywoływany, argument jest kopiowany do pamięci, a argument jest zastępowany przez wskaźnik do kopii. (W języku C/C++ nie ma takich typów, ale istnieją one w innych językach lub rozszerzeniach języka).

1. Jeśli typ argumentu to HFA lub HVA, argument jest używany niemodyfikowany.

1. Jeśli typ argumentu jest typem złożonym większym niż 16 bajtów, argument jest kopiowany do pamięci przydzielonej przez obiekt wywołujący, a argument jest zastępowany przez wskaźnik do kopii.

1. Jeśli typ argumentu jest typem złożonym, rozmiar argumentu jest zaokrąglany do najbliższej wielokrotności 8 bajtów.

### <a name="stage-c--assignment-of-arguments-to-registers-and-stack"></a>Etap C — przypisanie argumentów do rejestrów i stosu

Dla każdego argumentu na liście są stosowane następujące reguły do momentu przydzielenia tego argumentu. Gdy argument jest przypisany do rejestru, wszystkie nieużywane bity w rejestrze mają nieokreśloną wartość. Jeśli argument jest przypisany do gniazda stosu, wszystkie nieużywane bajty uzupełniania mają nieokreśloną wartość.

1. Jeśli argument jest typu pół-lub o podwójnej precyzji zmiennoprzecinkowej lub krótkiej, a wartość NSRN jest mniejsza niż 8, argument jest przypisywany do najmniej znaczących bitów usługi Register v \[ NSRN]. NSRN jest zwiększana o jeden. Argument został przydzielony.

1. Jeśli argument jest HFA lub HVA, a istnieją wystarczające przydzielono rejestrów SIMD i zmiennoprzecinkowych (NSRN + liczba członków ≤ 8), argument jest przypisywany do i rejestrów zmiennoprzecinkowych, jeden rejestr na element członkowski SIMD lub HFA. NSRN jest zwiększana o liczbę używanych rejestrów. Argument został przydzielony.

1. Jeśli argument jest HFA lub HVA, wówczas NSRN jest ustawiona na 8, a rozmiar argumentu jest zaokrąglany do najbliższej wielokrotności 8 bajtów.

1. Jeśli argument jest HFA, HVA, typu zmiennoprzecinkowego o poczwórnej precyzji lub krótkiej wektora, a następnie NSAA jest zaokrąglana do większej liczby 8 lub naturalnego wyrównania typu argumentu.

1. Jeśli argument jest typu zmiennoprzecinkowego o połowie lub pojedynczej precyzji, wówczas rozmiar argumentu jest ustawiony na 8 bajtów. Jest to efekt, tak jakby argument został skopiowany do najmniej znaczących bitów rejestru 64-bitowego, a pozostałe bity zostały wypełnione nieokreślonymi wartościami.

1. Jeśli argument jest HFA, typu zmiennoprzecinkowego, pojedynczej, podwójnej precyzji lub krótkiej klasy wektora, to argument jest kopiowany do pamięci na dostosowaną NSAA. Wartość NSAA jest zwiększana o rozmiar argumentu. Argument został przydzielony.

1. Jeśli argument jest typem całkowitym lub wskaźnikowym, rozmiar argumentu jest mniejszy niż lub równy 8 bajtów, a NGRN jest mniejszy niż 8, argument jest kopiowany do najmniej znaczących bitów w x \[ NGRN]. NGRN jest zwiększana o jeden. Argument został przydzielony.

1. Jeśli argument ma wyrównanie 16, to NGRN jest zaokrąglana do następnej parzystej liczby.

1. Jeśli argument jest typem całkowitym, rozmiar argumentu jest równy 16, a NGRN jest mniejszy niż 7, argument jest kopiowany do x \[ NGRN] i x \[ NGRN + 1]. x \[ NGRN] musi zawierać dolną, rozstawioną dwuwyrazową reprezentację pamięci argumentu. NGRN jest zwiększana o dwa. Argument został przydzielony.

1. Jeśli argument jest typu złożonego, a rozmiar w podwójnych słowach argumentu nie przekracza 8 minus NGRN, argument jest kopiowany do kolejnych rejestrów ogólnego przeznaczenia, zaczynając od x \[ NGRN]. Argument jest przesyłany tak, jakby został załadowany do rejestrów z adresu wyrównanego do podwójnego tekstu, z odpowiednią sekwencją instrukcji LDR, które ładują kolejne rejestry z pamięci. Zawartość wszelkich nieużywanych części rejestrów nie jest określona przez ten standard. NGRN jest zwiększana o liczbę używanych rejestrów. Argument został przydzielony.

1. NGRN jest ustawiona na 8.

1. NSAA jest zaokrąglana do większej liczby 8 lub naturalnego wyrównania typu argumentu.

1. Jeśli argument jest typu złożonego, wówczas argument jest kopiowany do pamięci pod dostosowaną NSAA. Wartość NSAA jest zwiększana o rozmiar argumentu. Argument został przydzielony.

1. Jeśli rozmiar argumentu jest mniejszy niż 8 bajtów, rozmiar argumentu jest ustawiony na 8 bajtów. Ma to wpływ na to, czy argument został skopiowany do najmniej znaczących bitów rejestru 64-bitowego, a pozostałe bity zostały wypełnione nieokreślonymi wartościami.

1. Argument jest kopiowany do pamięci po dostosowaniu NSAA. Wartość NSAA jest zwiększana o rozmiar argumentu. Argument został przydzielony.

### <a name="addendum-variadic-functions"></a>Uzupełnienie: funkcje wariadyczne

Funkcje, które przyjmują zmienną liczbę argumentów, są obsługiwane inaczej niż powyżej, w następujący sposób:

1. Wszystkie złożone są traktowane jak takie jak: Brak specjalnego traktowania HFAs lub HVAs.

1. SIMD i rejestry zmiennoprzecinkowe nie są używane.

Efektywnie jest to taka sama jak następująca reguła C. 12 – C. 15 do przydzielania argumentów do wielobajtowego stosu, gdzie pierwsze 64 bajtów stosu są ładowane do x0-120 i wszystkie pozostałe argumenty stosu są zwykle umieszczane.

## <a name="return-values"></a>Wartości zwracane

Wartości całkowite są zwracane w x0.

Wartości zmiennoprzecinkowe są zwracane w S0, d0 lub v0, zgodnie z potrzebami.

Wartości HFA i HVA są zwracane w S0-S3, d0-D3 lub v0-v3, zgodnie z potrzebami.

Typy zwracane przez wartość są obsługiwane w różny sposób w zależności od tego, czy mają pewne właściwości, oraz czy funkcja jest niestatyczną funkcją składową. Typy, które mają wszystkie te właściwości,

- są one *agregowane* przez standardową definicję języka c++ 14, czyli nie mają konstruktorów dostarczonych przez użytkownika, żadnych prywatnych lub chronionych niestatycznych elementów członkowskich danych, nie klas bazowych ani żadnych funkcji wirtualnych, a także
- mają operator przypisywania prostej kopii i
- mają prosty destruktor,

i są zwracane przez funkcje nieczłonkowskie lub statyczne funkcje członkowskie, użyj następującego stylu powrotu:

- W x0 nie są zwracane typy mniejsze niż lub równe 8 bajtów.
- Typy mniejsze niż lub równe 16 bajty są zwracane w x0 i x1 z parametrem x0 zawierającym mniej niż 8 bajtów.
- W przypadku typów o wartości większej niż 16 bajtów obiekt wywołujący rezerwuje blok pamięci o wystarczającym rozmiarze i wyrównaniu, aby pomieścić wynik. Adres bloku pamięci jest przenoszona jako dodatkowy argument do funkcji w x8. Wywoływany może zmodyfikować blok pamięci wynikowej w dowolnym momencie wykonywania procedury podrzędnej. Wartość parametru wywoływanego nie jest wymagana w celu zachowania wartości przechowywanej w x8.

Wszystkie inne typy używają tej Konwencji:

- Obiekt wywołujący rezerwuje blok pamięci o wystarczającym rozmiarze i wyrównaniu, aby pomieścić wynik. Adres bloku pamięci jest przenoszona jako dodatkowy argument do funkcji w x0 lub x1, jeśli $this jest przenoszona w x0. Wywoływany może zmodyfikować blok pamięci wynikowej w dowolnym momencie wykonywania procedury podrzędnej. Wywoływany zwraca adres bloku pamięci w x0.

## <a name="stack"></a>Stos

Po ABI przez ARM stos musi pozostać 16-bajtowy. AArch64 zawiera funkcję sprzętową, która generuje błędy wyrównania stosu za każdym razem, gdy SP nie jest wyrównany 16-bajtowe i jest wykonywane względnie obciążenie lub przechowywanie zależne od SP. System Windows jest uruchamiany z włączoną tą funkcją przez cały czas.

Funkcje, które przydzielą 4K lub więcej informacji o stosie, muszą mieć pewność, że każda strona przed ostatnią stroną jest w porządku. Ta akcja zapewnia, że żaden kod nie może "przekroczyć" stron ochrony, które są używane przez system Windows do rozszerzenia stosu. Zwykle dotknięcie odbywa się przez `__chkstk` pomocnika, który ma niestandardową konwencję wywoływania, która przekazuje całkowitą alokację stosu podzieloną przez 16 w x15.

## <a name="red-zone"></a>Czerwona strefa

Obszar 16-bajtowy bezpośrednio poniżej bieżącego wskaźnika stosu jest zarezerwowany do użytku w scenariuszach analizy i stosowania poprawek dynamicznych. Ten obszar pozwala na wstawienie dokładnie wygenerowanego kodu, który przechowuje dwa rejestry w [SP, #-16] i tymczasowo używa ich do dowolnych celów. Jądro systemu Windows gwarantuje, że te 16 bajtów nie są zastępowane w przypadku wykonania wyjątku lub przerwania w trybie użytkownika i jądra.

## <a name="kernel-stack"></a>Stos jądra

Domyślny stos trybu jądra w systemie Windows to sześć stron (24k). Zwróć szczególną uwagę na funkcje z dużymi buforami stosu w trybie jądra. Niewłaściwie przekroczenie czasu przerwanie może następować przy niewielkim stopniu i utworzyć kontrolę błędów awaryjnego stosu.

## <a name="stack-walking"></a>Idący stos

Kod w systemie Windows jest kompilowany z włączonymi wskaźnikami ramki ([/Oy-](reference/oy-frame-pointer-omission.md)), aby umożliwić szybkie przechodzenie na stosie. Ogólnie rzecz biorąc, x29 (FP) wskazuje następne łącze w łańcuchu, czyli parę {FP, LR}, wskazującą wskaźnik do poprzedniej ramki na stosie i adresie zwrotnym. Kod innej firmy zachęca się również do włączania wskaźników ramki, aby umożliwić lepsze profilowanie i śledzenie.

## <a name="exception-unwinding"></a>Odwracanie wyjątku

Odwinięcie podczas obsługi wyjątków jest wspomagane za pomocą kodów wyłączania. Kody operacji unwind są sekwencją bajtów przechowywanych w sekcji. xdata pliku wykonywalnego. Opisują one operacje prologu i epilogu w sposób abstrakcyjny, w taki sposób, że efekty prologu funkcji można cofnąć, aby utworzyć kopię zapasową do ramki stosu wywołującego. Aby uzyskać więcej informacji na temat kodów unwind, zobacz [arm64 exceptioning](arm64-exception-handling.md).

EABI ARM określa również wyjątek, który odwraca model, który używa kodów unwind. Jednakże specyfikacja przedstawiona jest niewystarczająca do odwinięcia w systemie Windows, co musi obsługiwać przypadki, w których komputer znajduje się w środku funkcji prologu lub epilogu.

Dynamicznie generowany kod powinien zostać opisany przy użyciu tabel funkcji dynamicznych za pomocą `RtlAddFunctionTable` i skojarzonych funkcji, tak aby wygenerowany kod mógł uczestniczyć w obsłudze wyjątków.

## <a name="cycle-counter"></a>Licznik cyklu

Wszystkie procesory ARMv8 są wymagane do obsługi rejestru licznika cykl, rejestr 64-bitowy, który system Windows konfiguruje do odczytu na dowolnym poziomie wyjątku, w tym w trybie użytkownika. Dostęp do niego można uzyskać za pośrednictwem specjalnego rejestru PMCCNTR_EL0 przy użyciu kodu w kodzie zestawu lub `_ReadStatusReg` wewnętrznej w kodzie C/C++.

W tym miejscu licznik cyklu jest wartością prawda, a nie zegarem ściany. Częstotliwość zliczania zależy od częstotliwości procesora. Jeśli uważasz, że musisz znać częstotliwość licznika cykl, nie należy używać licznika cykli. Zamiast tego należy mierzyć czas zegara ściany, którego należy użyć `QueryPerformanceCounter` .

## <a name="see-also"></a>Zobacz też

[Typowe problemy przy migracji Visual C++ ARM](common-visual-cpp-arm-migration-issues.md)<br/>
[Obsługa wyjątków ARM64](arm64-exception-handling.md)
