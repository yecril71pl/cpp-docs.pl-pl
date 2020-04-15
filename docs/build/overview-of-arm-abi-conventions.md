---
title: Omówienie konwencji ARM ABI
ms.date: 07/11/2018
ms.assetid: 23f4ae8c-3148-4657-8c47-e933a9f387de
ms.openlocfilehash: 8737f7b1cbe0651b43eb3b9990a4035b60bd01b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320728"
---
# <a name="overview-of-arm32-abi-conventions"></a>Omówienie konwencji ARM32 ABI

Interfejs binarny aplikacji (ABI) dla kodu skompilowanego dla systemu Windows na procesorach ARM jest oparty na standardowym ARM EABI. W tym artykule przedstawiono kluczowe różnice między systemem Windows na ARM i standard. Niniejszy dokument obejmuje ARM32 ABI. Aby uzyskać informacje na temat arm64 ABI, zobacz [Omówienie konwencji ARM64 ABI](arm64-windows-abi-conventions.md). Aby uzyskać więcej informacji na temat standardowego systemu ARM EABI, zobacz [Interfejs binarny aplikacji (ABI) dla architektury ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (łącze zewnętrzne).

## <a name="base-requirements"></a>Wymagania podstawowe

Windows na ARM zakłada, że jest uruchomiony na architekturze ARMv7 przez cały czas. Obsługa zmiennoprzecinkowa w postaci VFPv3-D32 lub nowszej musi być obecna w sprzęcie. VFP musi obsługiwać zarówno pojedynczej precyzji i podwójnej precyzji zmiennoprzecinkowych w sprzęcie. Środowisko wykonawcze systemu Windows nie obsługuje emulacji zmiennoprzecinkowego, aby włączyć uruchamianie na sprzęcie innych niż VFP.

Obsługa zaawansowanych rozszerzeń SIMD (NEON) — obejmujących zarówno operacje całkowite, jak i zmiennoprzecinowe — musi być również obecna w sprzęcie. Nie jest dostępna obsługa czasu wykonywania emulacji.

Obsługa dzielenia całkowitych (UDIV/SDIV) jest zdecydowanie zalecana, ale nie jest wymagana. Platformy, które nie mają obsługi podziału liczby całkowitej może ponieść karę wydajności, ponieważ te operacje muszą być uwięzione i ewentualnie poprawione.

## <a name="endianness"></a>Endianness (Endianness)

Windows na ARM jest wykonywany w trybie mało-endian. Zarówno kompilator MSVC, jak i środowisko wykonawcze systemu Windows oczekują danych o niewiele endianach przez cały czas. Chociaż instrukcja SETEND w architekturze zestawu instrukcji ARM (ISA) umożliwia nawet kod trybu użytkownika, aby zmienić bieżącą endianness, robi to jest odradzane, ponieważ jest to niebezpieczne dla aplikacji. Jeśli wyjątek jest generowany w trybie big-endian, zachowanie jest nieprzewidywalne i może prowadzić do błędu aplikacji w trybie użytkownika lub bugcheck w trybie jądra.

## <a name="alignment"></a>Wyrównanie

Mimo że system Windows umożliwia sprzęt ARM do obsługi niewyrównane liczby całkowitej uzyskuje dostęp w sposób przezroczysty, błędy wyrównania nadal mogą być generowane w niektórych sytuacjach. Postępuj zgodnie z tymi regułami dostosowania:

- Półsłowne obciążenia i magazyny o rozmiarze półsłownym (16-bitowe) i słowu (32-bitowe) nie muszą być wyrównane. Sprzęt obsługuje je wydajnie i przejrzyście.

- Obciążenia zmiennoprzecinowe i magazyny powinny być wyrównane. Jądro obsługuje niewyrównane obciążenia i przechowuje je w sposób przejrzysty, ale ze znacznym obciążeniem.

- Należy wyrównać operacje ładowania lub przechowywania podwójnej (LDRD/STRD) i wielu operacji (LDM/STM). Jądro obsługuje większość z nich w sposób przejrzysty, ale ze znacznym obciążeniem.

- Wszystkie niebukowane dostępy do pamięci muszą być wyrównane, nawet w przypadku dostępu do liczby całkowitej. Niewyrównane dostępy powodują błąd wyrównania.

## <a name="instruction-set"></a>Zestaw instrukcji

Zestaw instrukcji dla systemu Windows na ARM jest ściśle ograniczona do Thumb-2. Oczekuje się, że cały kod wykonany na tej platformie zostanie uruchomiony i pozostanie w trybie thumb przez cały czas. Próba przełączenia się do starszego zestawu instrukcji ARM może zakończyć się pomyślnie, ale jeśli tak, wszelkie wyjątki lub przerwania, które występują, mogą prowadzić do błędu aplikacji w trybie użytkownika lub kontroli błędów w trybie jądra.

Efektem ubocznym tego wymagania jest to, że wszystkie wskaźniki kodu muszą mieć zestaw bitów niskich. Jest to tak, że gdy są one ładowane i rozgałęzione przez BLX lub BX, procesor pozostanie w trybie thumb i nie spróbuje wykonać kod docelowy jako 32-bitowe instrukcje ARM.

### <a name="it-instructions"></a>Instrukcje IT

Korzystanie z instrukcji IT w kodzie Thumb-2 jest niedozwolone, z wyjątkiem tych szczególnych przypadków:

- Instrukcji IT można użyć tylko do modyfikowania jednej instrukcji docelowej.

- Instrukcja docelowa musi być instrukcją 16-bitową.

- Instrukcja docelowa musi być jedną z następujących:

   |16-bitowe kody opcode|Klasa|Ograniczenia|
   |---------------------|-----------|------------------|
   |MOV, MVN|Move|Rm != PC, Rd != PC|
   |LDR, LDR[S]B, LDR[S]H|Obciążenie z pamięci|Ale nie dosłowne formy LDR|
   |STR, STRB, STRH|Przechowywanie do pamięci||
   |ADD, ADC, RSB, SBC, SUB|Dodawanie lub odejmowanie|Ale nie ADD/SUB SP, SP, formularze imm7<br /><br /> Rm != PC, Rdn != PC, Rdm != PC|
   |CMP, CMN|Porównanie|Rm != PC, Rn != PC|
   |Mul|Mnożenie||
   |ASR, LSL, LSR, ROR|Przesunięcie bitowe||
   |I, BIC, EOR, ORR, TST|Arytmetyka bitowa||
   |Bx|Oddział do rejestracji|Rm != PC|

Chociaż obecne procesory ARMv7 nie mogą zgłaszać użycia niedozwolonych formularzy instrukcji, oczekuje się, że przyszłe pokolenia. Jeśli te formularze zostaną wykryte, każdy program, który z nich korzysta, może zostać zakończony niezdefiniowanym wyjątkiem instrukcji.

### <a name="sdivudiv-instructions"></a>Instrukcje SDIV/UDIV

Korzystanie z instrukcji podziału liczby całkowitej SDIV i UDIV jest w pełni obsługiwane, nawet na platformach bez natywnego sprzętu do ich obsługi. Obciążenie na podział SDIV lub UDIV na procesorze Cortex-A9 wynosi około 80 cykli, oprócz całkowitego czasu podziału 20-250 cykli, w zależności od wejść.

## <a name="integer-registers"></a>Rejestry całkowite

Procesor ARM obsługuje 16 rejestrów całkowitych:

|Zarejestruj|Lotnych?|Rola|
|--------------|---------------|----------|
|r0|Lotnych|Parametr, wynik, rejestr zarysowań 1|
|r1|Lotnych|Parametr, wynik, rejestr zarysowań 2|
|R2|Lotnych|Parametr, rejestr zarysowań 3|
|r3|Lotnych|Parametr, rejestr zarysowań 4|
|R4|Nielotne||
|r5|Nielotne||
|r6|Nielotne||
|r7|Nielotne||
|R8|Nielotne||
|r9|Nielotne||
|r10|Nielotne||
|r11|Nielotne|Wskaźnik ramki|
|r12|Lotnych|Rejestr zdrapek połączeń wewnątrz procedury|
|r13 (SP)|Nielotne|Wskaźnik stosu|
|r14 (LR)|Nielotne|Rejestr linków|
|r15 (PC)|Nielotne|Licznik programu|

Aby uzyskać szczegółowe informacje na temat używania parametrów i zwracanie wartości rejestrów, zobacz parametr przekazywania sekcji w tym artykule.

System Windows używa r11 do szybkiego chodzenia po ramie stosu. Aby uzyskać więcej informacji, zobacz sekcję Spacery z stosem. Z tego powodu r11 musi zawsze wskazywać najwyższe ogniwo w łańcuchu. Nie należy używać r11 do ogólnych celów — kod nie wygeneruje poprawne spacery stosu podczas analizy.

## <a name="vfp-registers"></a>Rejestry VFP

System Windows obsługuje tylko warianty ARM, które obsługują koprocsor VFPv3-D32. Oznacza to, że rejestry zmiennoprzecinowe są zawsze obecne i mogą być oparte na przekazywaniu parametrów i że pełny zestaw 32 rejestrów jest dostępny do użycia. Rejestry VFP i ich użycie są podsumowane w tej tabeli:

|Singli|podwojenia|Quady|Lotnych?|Rola|
|-------------|-------------|-----------|---------------|----------|
|s0-s3|d0-d1|w kw.|Lotnych|Parametry, wynik, rejestr zarysowań|
|s4-s7|d2-d3|Q1|Lotnych|Parametry, rejestr zarysowań|
|s8-s11|d4-d5|W II kw.|Lotnych|Parametry, rejestr zarysowań|
|s12-s15|d6-d7|W III kw.|Lotnych|Parametry, rejestr zarysowań|
|s16-s19|d8-d9|w IV kw.|Nielotne||
|s20-s23|d10-d11|w 5.|Nielotne||
|s24-s27|d12-d13|w 16.|Nielotne||
|s28-s31|d14-d15|Q7|Nielotne||
||d16-d31|Q8-q15|Lotnych||

Następna tabela przedstawia pola bitowe stanu zmiennoprzecinowego i kontroli (FPSCR):

|Bity|Znaczenie|Lotnych?|Rola|
|----------|-------------|---------------|----------|
|31-28|NZCV ( NZCV )|Lotnych|Flagi stanu|
|27|QC|Lotnych|Skumulowane nasycenie|
|26|Ahp|Nielotne|Alternatywna kontrola półprecyzyjne|
|25|Dn|Nielotne|Domyślna kontrolka trybu NaN|
|24|Fz|Nielotne|Sterowanie trybem równo do zera|
|23-22|Tryb R|Nielotne|Sterowanie trybem zaokrąglania|
|21-20|Kroku|Nielotne|Wektor Stride, musi być zawsze 0|
|18-16|Len|Nielotne|Długość wektora, musi być zawsze 0|
|15, 12-8|IDE, IXE itp.|Nielotne|Bity włączania podlewki wyjątków, muszą być zawsze 0|
|7, 4-0|IDC, IXC itp.|Lotnych|Skumulowane flagi wyjątków|

## <a name="floating-point-exceptions"></a>Wyjątki zmiennoprzecinkowe

Większość sprzętu ARM nie obsługuje wyjątków zmiennoprzecinkowych IEEE. W przypadku wariantów procesora, które mają sprzętowe wyjątki zmiennoprzecinkowe, jądro systemu Windows po cichu łapie wyjątki i niejawnie wyłącza je w rejestrze FPSCR. Zapewnia to znormalizowane zachowanie między wariantami procesora. W przeciwnym razie kod opracowany na platformie, która nie ma obsługi wyjątków może otrzymać nieoczekiwane wyjątki, gdy jest uruchomiony na platformie, która ma obsługę wyjątków.

## <a name="parameter-passing"></a>Przekazywanie parametrów

W przypadku funkcji nierozewidujących system Windows na ARM ABI jest zgodny z regułami ARM dotyczącymi przekazywania parametrów — obejmuje to rozszerzenia VFP i Advanced SIMD. Reguły te są zgodne ze [standardem procedury wywołania architektury ARM,](http://infocenter.arm.com/help/topic/com.arm.doc.ihi0042c/IHI0042C_aapcs.pdf)skonsolidowanym z rozszerzeniami VFP. Domyślnie pierwsze cztery argumenty całkowite i maksymalnie osiem argumentów zmiennoprzecinkowych lub wektorowych są przekazywane w rejestrach, a dodatkowe argumenty są przekazywane na stosie. Argumenty są przypisywane do rejestrów lub stosu przy użyciu tej procedury:

### <a name="stage-a-initialization"></a>Etap A: Inicjowanie

Inicjowanie jest wykonywane dokładnie raz, przed rozpoczęciem przetwarzania argumentów:

1. Następny numer rejestru rdzenia (NCRN) jest ustawiony na r0.

1. Rejestry VFP są oznaczone jako nieprzydzielone.

1. Następny skumulowany adres argumentu (NSAA) jest ustawiony na bieżący SP.

1. Jeśli wywoływana jest funkcja zwracająca wynik w pamięci, adres wyniku jest umieszczany w r0, a NCRN jest ustawiony na r1.

### <a name="stage-b-pre-padding-and-extension-of-arguments"></a>Etap B: Wstępne wyściółka i rozszerzenie argumentów

Dla każdego argumentu na liście stosowana jest pierwsza reguła dopasowania z poniższej listy:

1. Jeśli argument jest typem złożonym, którego rozmiar nie może być statycznie określony zarówno przez wywołującego, jak i wywoływanego, argument jest kopiowany do pamięci i zastępowany wskaźnikiem do kopii.

1. Jeśli argument jest bajtem lub 16-bitowym półsłowem, to jest on rozszerzony lub znak rozszerzony na 32-bitowe pełne słowo i traktowany jako argument 4-bajtowy.

1. Jeśli argument jest typem złożonym, jego rozmiar jest zaokrąglany w górę do najbliższej wielokrotności 4.

### <a name="stage-c-assignment-of-arguments-to-registers-and-stack"></a>Etap C: Przypisywanie argumentów do rejestrów i stosów

Dla każdego argumentu na liście następujące reguły są stosowane po kolei, dopóki argument nie został przydzielony:

1. Jeśli argument jest typem VFP i istnieje wystarczająco dużo kolejnych nieprzydzielonych rejestrów VFP odpowiedniego typu, argument jest przydzielany do najniższej numeracji sekwencji takich rejestrów.

1. Jeśli argument jest typem VFP, wszystkie pozostałe nieprzydzielone rejestry są oznaczone jako niedostępne. NSAA jest korygowana w górę, dopóki nie jest poprawnie wyrównany dla typu argumentu i argument jest kopiowany do stosu w skorygowanej NSAA. NSAA jest następnie zwiększany o rozmiar argumentu.

1. Jeśli argument wymaga wyrównania 8-bajtowego, NCRN jest zaokrąglana w górę do następnego parzystego numeru rejestru.

1. Jeśli rozmiar argumentu w słowach 32-bitowych nie jest większy niż r4 minus NCRN, argument jest kopiowany do rejestrów podstawowych, począwszy od NCRN, z najmniej znaczącymi bitami zajmującymi rejestry o niższym numerze. NCRN jest zwiększana o liczbę używanych rejestrów.

1. Jeśli NCRN jest mniejsza niż r4 i NSAA jest równa SP, argument jest podzielony między rejestrów podstawowych i stosu. Pierwsza część argumentu jest kopiowana do rejestrów podstawowych, począwszy od NCRN, do r3 włącznie. Pozostała część argumentu jest kopiowana na stos, począwszy od NSAA. NCRN jest ustawiona na r4 i NSAA jest zwiększany o rozmiar argumentu minus kwota przekazywana w rejestrach.

1. Jeśli argument wymaga wyrównania 8-bajtowego, NSAA jest zaokrąglana w górę do następnego adresu wyrównanego 8 bajtów.

1. Argument jest kopiowany do pamięci w NSAA. NSAA jest zwiększany o rozmiar argumentu.

Rejestry VFP nie są używane dla funkcji zmiennych, a reguły etapu C 1 i 2 są ignorowane. Oznacza to, że funkcja zmiennorozwista może rozpocząć się od opcjonalnego wypychania {r0-r3}, aby dołączyć argumenty rejestru do dodatkowych argumentów przekazanych przez obiekt wywołujący, a następnie uzyskać dostęp do całej listy argumentów bezpośrednio ze stosu.

Wartości typu liczby całkowitej są zwracane w r0, opcjonalnie rozszerzone do r1 dla 64-bitowych wartości zwracanych. Wartości typu zmiennoprzecinkowego lub SIMD VFP/NEON są zwracane odpowiednio w s0, d0 lub q0.

## <a name="stack"></a>Stos

Stos musi pozostać 4-bajtowy wyrównany przez cały czas i musi być 8-bajtowy wyrównany na dowolnej granicy funkcji. Jest to wymagane do obsługi częstego używania zablokowanych operacji na zmiennych stosu 64-bitowego. ARM EABI stwierdza, że stos jest 8-bajtowy wyrównany w dowolnym interfejsie publicznym. Dla spójności systemu Windows na ARM ABI uznaje wszelkie granice funkcji za interfejs publiczny.

Funkcje, które muszą używać wskaźnika ramki `alloca` — na przykład funkcje, które dynamicznie się zmieniają lub zmieniają wskaźnik stosu — muszą skonfigurować wskaźnik ramki w r11 w prologu funkcji i pozostawić go bez zmian do epilogu. Funkcje, które nie wymagają wskaźnik ramki należy wykonać wszystkie aktualizacje stosu w prologu i pozostawić wskaźnik stosu bez zmian, aż do epilogu.

Funkcje, które przydzielają 4 KB lub więcej na stosie, muszą upewnić się, że każda strona przed ostatnią stroną jest dotykana w kolejności. Dzięki temu żaden kod nie może "przeskakiwać" stron straży, których używa system Windows do rozszerzenia stosu. Zazwyczaj jest to wykonywane `__chkstk` przez pomocnika, który jest przekazywany alokacji stosu całkowitej w bajtach podzielona przez 4 w r4 i który zwraca ostateczną kwotę alokacji stosu w bajtach z powrotem w r4.

### <a name="red-zone"></a>Czerwona strefa

Obszar 8 bajtów bezpośrednio poniżej bieżącego wskaźnika stosu jest zarezerwowany do analizy i dynamicznego łatania. Pozwala to na wstawienie starannie wygenerowanego kodu, który przechowuje 2 rejestry w [sp, #-8] i tymczasowo używa ich do dowolnych celów. Jądro systemu Windows gwarantuje, że te 8 bajtów nie zostanie zastąpione, jeśli wystąpi wyjątek lub przerwanie zarówno w trybie użytkownika, jak i w trybie jądra.

### <a name="kernel-stack"></a>Stos jądra

Domyślny stos w trybie jądra w systemie Windows to trzy strony (12 KB). Należy uważać, aby nie tworzyć funkcje, które mają duże bufory stosu w trybie jądra. Przerwanie może przyjść z bardzo mało headroom stosu i spowodować stos paniki bugcheck.

## <a name="cc-specifics"></a>Specyfika C/C++

Wyliczenia są 32-bitowe typy całkowite, chyba że co najmniej jedna wartość w wyliczeniu wymaga 64-bitowego magazynu dwuwyrazowego. W takim przypadku wyliczenie jest promowane do 64-bitowego typu liczby całkowitej.

`wchar_t`jest definiowana jako `unsigned short`równoważna , aby zachować zgodność z innymi platformami.

## <a name="stack-walking"></a>Spacery w stosie

Kod systemu Windows jest kompilowany ze wskaźnikami ramki włączone ([/Oy (Frame-Pointer O pominięcie)](reference/oy-frame-pointer-omission.md)), aby umożliwić szybkie chodzenie stosu. Ogólnie rzecz biorąc r11 rejestru wskazuje na następne łącze w łańcuchu, który jest {r11, lr} pary, która określa wskaźnik do poprzedniej ramki na stosie i adres zwrotny. Zaleca się, aby kod również włączyć wskaźniki ramki dla lepszego profilowania i śledzenia.

## <a name="exception-unwinding"></a>Odwijanie wyjątków

Odwijanie stosu podczas obsługi wyjątków jest włączona przez użycie kodów unwind. Kody unwind są sekwencją bajtów przechowywanych w sekcji .xdata obrazu wykonywalnego. Opisują one działanie funkcji prologu i epilogu kodu w sposób abstrakcyjny, tak aby skutki prologu funkcji można cofnąć w ramach przygotowań do odwijania do ramki stosu wywołującego.

ARM EABI określa model odwijania wyjątków, który używa kodów unwind. Jednak ta specyfikacja nie jest wystarczająca do odwijania w systemie Windows, który musi obsługiwać przypadki, gdy procesor znajduje się w środku prologu lub epilogu funkcji. Aby uzyskać więcej informacji na temat systemu Windows dotyczących danych wyjątków ARM i odwijania, zobacz [Obsługa wyjątków ARM](arm-exception-handling.md).

Zaleca się, aby dynamicznie generowany kod był opisywany `RtlAddFunctionTable` przy użyciu dynamicznych tabel funkcji określonych w wywołaniach i skojarzonych z nimi funkcjach, dzięki czemu wygenerowany kod może uczestniczyć w obsłudze wyjątków.

## <a name="cycle-counter"></a>Licznik cyklu

Procesory ARM z systemem Windows są wymagane do obsługi licznika cyklu, ale korzystanie z licznika bezpośrednio może powodować problemy. Aby uniknąć tych problemów, system Windows na ARM używa niezdefiniowanego kodu operacyjnego, aby zażądać znormalizowanej 64-bitowej wartości licznika cyklu. Z języka C lub C++użyj `__rdpmccntr64` wewnętrznej do emitowania odpowiedniego kodu opcode; z montażu, `__rdpmccntr64` należy skorzystać z instrukcji. Odczyt licznika cyklu trwa około 60 cykli na Cortex-A9.

Licznik jest prawdziwym licznikiem cyklu, a nie zegarem; w związku z tym częstotliwość liczenia różni się w zależności od częstotliwości procesora. Jeśli chcesz zmierzyć czas zegara, który `QueryPerformanceCounter`upłynął, użyj programu .

## <a name="see-also"></a>Zobacz też

[Typowe problemy przy migracji Visual C++ ARM](common-visual-cpp-arm-migration-issues.md)<br/>
[Obsługa wyjątków ARM](arm-exception-handling.md)
