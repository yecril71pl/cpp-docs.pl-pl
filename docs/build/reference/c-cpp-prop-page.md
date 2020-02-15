---
title: Właściwości CC++ /Project (Visual Studio)
description: Przewodnik referencyjny dotyczący właściwości strony właściwości programuC++ Visual Studio Microsoft C/Project.
ms.date: 02/09/2020
ms.topic: article
ms.assetid: 16375038-4917-4bd0-9a2a-26343c1708b7
ms.openlocfilehash: fdfcaaebe8394fedd160c6c02e8c938543f845e2
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257757"
---
# <a name="cc-property-pages"></a>Strony CC++ /właściwości

Poniższe strony właściwości są dostępne w obszarze **właściwości** > **projektu** > **Właściwości konfiguracji** > **C/C++** :

## <a name="cc-general-properties"></a>Właściwości CC++ /ogólne

### <a name="additional-include-directories"></a>Dodatkowe katalogi dołączane

Określa co najmniej jeden katalog do dodania do ścieżki dołączania; Oddzielaj średnikami, jeśli więcej niż jeden. Ustawia [/i (Dodatkowe katalogi dołączane)](i-additional-include-directories.md).

### <a name="additional-using-directories"></a>Dodatkowe katalogi #using

Określa co najmniej jeden katalog (Oddzielaj nazwy katalogów średnikiem) do przeszukania, aby rozpoznać nazwy przesłane do dyrektywy #using. Ustawia [/AI](ai-specify-metadata-directories.md).

### <a name="debug-information-format"></a>Format informacji o debugowaniu

Określa typ informacji o debugowaniu generowanych przez kompilator.  Ta właściwość wymaga zgodnych ustawień konsolidatora. Ustawia [/Z7,/Zi,/ZI (format informacji o debugowaniu)](z7-zi-zi-debug-information-format.md).

#### <a name="choices"></a>Decyzji

- **Brak** — nie tworzy informacji o debugowaniu, dzięki czemu kompilacja może być szybsza.
- **C7 Compatible** — wybierz typ informacji o debugowaniu utworzonych dla danego programu oraz informacje o tym, czy są one przechowywane w plikach obiektu (. obj) lub w bazie danych programu (PDB).
- **Baza danych programu** — tworzy bazę danych programu (PDB), która zawiera informacje o typie i symboliczne informacje o debugowaniu do użycia z debugerem. Symboliczne informacje debugowania obejmują nazwy i typy zmiennych i funkcji oraz numery wierszy.
- **Baza danych programu do edycji i kontynuowania** — tworzy bazę danych programu, jak opisano powyżej, w formacie, który obsługuje funkcję [Edytuj i Kontynuuj](/visualstudio/debugger/edit-and-continue) .

### <a name="support-just-my-code-debugging"></a>Obsługa Tylko mój kod debugowanie

Dodaje kod pomocniczy umożliwiający włączenie debugowania [tylko mój kod](/visualstudio/debugger/just-my-code) w tej jednostce kompilacji. Ustawia [/JMC](jmc.md).

### <a name="common-language-runtime-support"></a>Obsługa środowiska uruchomieniowego CLR

Użyj usługi środowiska uruchomieniowego platformy .NET.  Ten przełącznik jest niezgodny z innymi przełącznikami; Aby uzyskać szczegółowe informacje, zobacz dokumentację rodziny [/CLR](clr-common-language-runtime-compilation.md) Switches.

#### <a name="choices"></a>Decyzji

- **Brak obsługi środowiska uruchomieniowego** CLR — brak obsługi środowiska uruchomieniowego języka wspólnego
- **Obsługa środowiska uruchomieniowego języka wspólnego** — tworzy metadane dla aplikacji, które mogą być używane przez inne aplikacje CLR. Umożliwia również aplikacji używanie typów i danych w metadanych innych składników CLR.
- **Czysta obsługa środowiska uruchomieniowego** CLR — tworzy plik wyjściowy tylko w języku [MSIL](/dotnet/standard/managed-code)bez natywnego kodu wykonywalnego, chociaż może zawierać natywne typy skompilowane do MSIL.
- **Bezpieczna obsługa środowiska uruchomieniowego** CLR — tworzy tylko MSIL (bez natywnego kodu wykonywalnego) i możliwy do zweryfikowania plik wyjściowy.

### <a name="consume-windows-runtime-extension"></a>Korzystanie z rozszerzenia środowisko wykonawcze systemu Windows

Korzystaj z rozszerzeń języków uruchomieniowych systemu Windows. Ustawia [/zw](zw-windows-runtime-compilation.md).

### <a name="suppress-startup-banner"></a>Pomiń transparent startowy

Pomija wyświetlanie transparentu logowania podczas uruchamiania kompilatora i wyświetlania komunikatów informacyjnych podczas kompilacji.

### <a name="warning-level"></a>Poziom ostrzeżeń

Wybierz, jak ścisłość kompilator ma mieć wpływ na błędy kodu. Ustawia [/W0-/W4](compiler-option-warning-level.md).

#### <a name="choices"></a>Decyzji

- Wyłącz **wszystkie ostrzeżenia** — poziom 0 wyłącza wszystkie ostrzeżenia.
- **Level1** -Level 1 wyświetla poważne ostrzeżenia. Poziom 1 jest domyślnym poziomem ostrzeżeń w wierszu polecenia.
- **Level2** -Level 2 wyświetla wszystkie ostrzeżenia poziomu 1 i ostrzeżenia mniej surowe niż poziom 1.
- **LEVEL3** -Level 3 wyświetla wszystkie ostrzeżenia poziomu 2 i wszystkie inne ostrzeżenia zalecane do celów produkcyjnych.
- **Level4** -Level 4 wyświetla wszystkie ostrzeżenia poziomu 3 i ostrzeżenia informacyjne, które w większości przypadków można bezpiecznie zignorować.
- **Włącz wszystkie ostrzeżenia** — włącza wszystkie ostrzeżenia, w tym te, które są domyślnie wyłączone.

### <a name="treat-warnings-as-errors"></a>Traktuj ostrzeżenia jako błędy

Traktuje ostrzeżenia kompilatora jako błędy. W przypadku nowego projektu najlepiej jest używać [/WX](wx-treat-linker-warnings-as-errors.md) w każdej kompilacji. Usuń wszystkie ostrzeżenia, aby zminimalizować trudne do znalezienia wady kodu.

### <a name="warning-version"></a>Wersja ostrzegawcza

Ukryj ostrzeżenia wprowadzone po określonej wersji kompilatora. Ustawia [/WV: xx\[. yy\[. zzzzz\]\]](wx-treat-linker-warnings-as-errors.md).

### <a name="diagnostics-format"></a>Format diagnostyki

Umożliwia zaawansowaną diagnostykę, z informacjami o kolumnie i kontekstem źródłowym w komunikatach diagnostycznych.

#### <a name="choices"></a>Decyzji

- **Karetka** — zawiera informacje o kolumnie w komunikacie diagnostycznym. I, wyprowadza odpowiedni wiersz kodu źródłowego z karetką wskazującą kolumnę, której to dotyczy.
- **Informacje o kolumnie** — dodatkowo podaje numer kolumny w wierszu, w którym wydano diagnostykę, jeśli ma to zastosowanie.
- **Klasyczny** — wyprowadza tylko wcześniejsze, zwięzłe komunikaty diagnostyczne z numerem wiersza.

### <a name="sdl-checks"></a>Sprawdzanie SDL

Dodatkowe testy zalecane do rozwoju zabezpieczeń (SDL); obejmuje włączenie dodatkowych funkcji bezpiecznego generowania kodu i zapewnia dodatkowe ostrzeżenia związane z zabezpieczeniami jako błędy. Ustawia [/SDL,/SDL-](sdl-enable-additional-security-checks.md).

### <a name="multi-processor-compilation"></a>Kompilacja wieloprocesorowa

Kompilacja wieloprocesorowa.

## <a name="cc-optimization-properties"></a>Właściwości optymalizacjiC++ C/

### <a name="optimization"></a>Optymalizacja

Wybierz opcję optymalizacji kodu; Wybierz pozycję niestandardowa, aby użyć określonych opcji optymalizacji. Ustawia [/od](od-disable-debug.md), [/O1,/O2](o-options-optimize-code.md).

#### <a name="choices"></a>Decyzji

- Optymalizacja **niestandardowa** .
- **Wyłączone** — wyłączenie optymalizacji.
- **Maksymalna Optymalizacja (Preferuj rozmiar)** — odpowiednik/og/OS/Oy/Ob2/GS/GF/Gy
- **Maksymalna Optymalizacja (Preferuj szybkość)** — odpowiednik/og/Oi/OT/Oy/Ob2/GS/GF/Gy
- **Optymalizacje (Preferuj szybkość)** — odpowiednik/og/Oi/OT/Oy/Ob2

### <a name="inline-function-expansion"></a>Rozwinięcie funkcji wbudowanej

Wybierz poziom rozwinięcia [funkcji wbudowanej](../../cpp/inline-functions-cpp.md) dla kompilacji. Ustawia [/OB1,/Ob2](ob-inline-function-expansion.md).

#### <a name="choices"></a>Decyzji

- **Domyślne**
- **Wyłączone** — wyłącza rozszerzanie wbudowane, które jest domyślnie włączone.
- **Tylko __inline** -rozszerza tylko funkcje oznaczone jako **inline**, `__inline`, `__forceinline`lub `__inline`. Lub, w funkcji C++ składowej zdefiniowanej w deklaracji klasy.
- **Wszelkie odpowiednie** operacje rozszerzające funkcje oznaczone jako **inline** lub `__inline` i wszelkie inne funkcje, które kompilator wybiera. (Rozszerzenie występuje według uznania kompilatora, często nazywane *autozwijaniem*).

### <a name="enable-intrinsic-functions"></a>Włącz funkcje wewnętrzne

Włącza funkcje wewnętrzne.  Używanie funkcji wewnętrznych generuje szybsze, ale prawdopodobnie większy, kod. Ustawia [/Oi](oi-generate-intrinsic-functions.md).

### <a name="favor-size-or-speed"></a>Preferuj rozmiar lub szybkość

Czy preferujesz rozmiar kodu czy szybkość kodu; Musi być włączona opcja "Optymalizacja globalna". Ustawia [/OT,/OS](os-ot-favor-small-code-favor-fast-code.md).

#### <a name="choices"></a>Decyzji

- **Preferuj mały** kod — Preferuj mały kod. Minimalizuje rozmiar exe i bibliotek DLL, instruując kompilator, aby preferuje rozmiar przekraczający szybkość.
- **Preferuj szybki** kod szybkiego kodu. Maksymalizuje szybkość exe i bibliotek DLL, instruując kompilator, aby preferuje szybkość. (Jest to wartość domyślna).
- **Nie ma** żadnej optymalizacji rozmiaru i szybkości.

### <a name="omit-frame-pointers"></a>Pomiń wskaźniki ramki

Pomija tworzenie wskaźników ramek na stosie wywołań.

### <a name="enable-fiber-safe-optimizations"></a>Włącz optymalizacje bezpieczne dla włókna

Włącza optymalizację przestrzeni pamięci podczas korzystania z włókien i lokalnego magazynu wątków. Ustawia [/gt](gt-support-fiber-safe-thread-local-storage.md).

### <a name="whole-program-optimization"></a>Optymalizacja całego programu

Umożliwia optymalizacje między modułami przez opóźnione generowanie kodu w celu łączenia czasu. Wymaga opcji konsolidatora "Generowanie kodu w czasie konsolidacji". Ustawia [/GL](gl-whole-program-optimization.md).

## <a name="cc-preprocessor-properties"></a>Właściwości językaC++ C/preprocesora

### <a name="preprocessor-definitions"></a>Definicje preprocesora

Definiuje symbole przetwarzania wstępnego dla pliku źródłowego.

### <a name="undefine-preprocessor-definitions"></a>Usuń Definicje preprocesora

Określa co najmniej jedną definicję preprocesora. Ustawia [/u](u-u-undefine-symbols.md).

### <a name="undefine-all-preprocessor-definitions"></a>Usuń wszystkie Definicje preprocesora

Usuń wszystkie poprzednio zdefiniowane wartości preprocesora. Ustawia [/u](u-u-undefine-symbols.md).

### <a name="ignore-standard-include-paths"></a>Ignoruj standardowe ścieżki dołączania

Uniemożliwia kompilatorowi wyszukiwanie plików dołączanych w katalogach określonych w zmiennych środowiskowych INCLUDE.

### <a name="preprocess-to-a-file"></a>Przetwarzaj wstępnie do pliku

Wstępnie przetwarza pliki C i C++ Source oraz zapisuje wstępnie przetworzone dane wyjściowe do pliku. Ta opcja pomija kompilację i nie tworzy pliku *`.obj`* .

### <a name="preprocess-suppress-line-numbers"></a>Wstępnie przetwarzane numery wierszy pomijania

Przetwarzanie wstępne bez dyrektyw #line.

### <a name="keep-comments"></a>Zachowaj Komentarze

Pomija pasek komentarzy z kodu źródłowego; wymaga ustawienia jednej z opcji przetwarzania wstępnego. Ustawia [/c](c-preserve-comments-during-preprocessing.md).

## <a name="cc-code-generation-properties"></a>Właściwości generowaniaC++ kodu C/

### <a name="enable-string-pooling"></a>Włącz buforowanie ciągów

Kompilator tworzy tylko jedną kopię identycznych ciągów w obrazie programu. Powoduje to mniejsze programy, czyli optymalizację nazywaną *buforowaniem ciągów*. [/O1,/O2](o-options-optimize-code.md)i [/Zi](z7-zi-zi-debug-information-format.md) automatycznie ustawiają opcję [/GF](gf-eliminate-duplicate-strings.md) .

### <a name="enable-minimal-rebuild"></a>Włącz minimalną ponowną kompilację

Włącza minimalną ponowną kompilację, która określa C++ , czy ponownie kompilować pliki C++ źródłowe, które zawierają zmienione definicje klas, przechowywane w nagłówkach *`.h`* plików.

### <a name="enable-c-exceptions"></a>Włącz C++ wyjątki

Określa model obsługi wyjątków, który ma być używany przez kompilator.

#### <a name="choices"></a>Decyzji

- **Tak z wyjątkami SEH** — model obsługi wyjątków, który przechwytuje asynchroniczne (strukturalne) iC++synchroniczne () wyjątki. Ustawia [/EHa](eh-exception-handling-model.md).
- **Tak** — model obsługi wyjątków, który przechwytuje C++ tylko wyjątki i instruuje kompilator, aby założył, że zewnętrzne funkcje C C++ nigdy nie zgłaszają wyjątku. Ustawia [/EHsc](eh-exception-handling-model.md).
- **Tak, z funkcjami extern C** — model obsługi wyjątków, który przechwytuje tylko C++ wyjątki i instruuje kompilator, aby założył, że zewnętrzne funkcje C zgłaszają wyjątek. Ustawia [/EHS](eh-exception-handling-model.md).
- **Nie** — brak obsługi wyjątków.

### <a name="smaller-type-check"></a>Sprawdzenie mniejszego typu

Włącz sprawdzanie konwersji na mniejsze typy, niezgodne z typem optymalizacji innym niż debugowanie. Ustawia [/RTCc](rtc-run-time-error-checks.md).

### <a name="basic-runtime-checks"></a>Podstawowe testy środowiska uruchomieniowego

Włącz podstawowe testy błędów środowiska uruchomieniowego, niezgodne z typem optymalizacji innym niż debugowanie. Ustawia [/RTCs,/RTCu,/RTC1](rtc-run-time-error-checks.md).

#### <a name="choices"></a>Decyzji

- **Ramki stosu** — włącza sprawdzanie błędów czasu wykonywania ramki stosu.
- **Niezainicjowane zmienne** — umożliwia zgłaszanie, kiedy zmienna jest używana bez zainicjowania.
- **Oba (/RTC1, equiv. to/RTCsu)** — odpowiednik wartości/RTCsu.
- **Domyślne** — domyślne testy środowiska uruchomieniowego.

### <a name="runtime-library"></a>Biblioteka środowiska uruchomieniowego

Określ bibliotekę środowiska uruchomieniowego do konsolidacji. Ustawia [/MT,/MTD,/MD,/MDD](md-mt-ld-use-run-time-library.md).

#### <a name="choices"></a>Decyzji

- **Wielowątkowy** — powoduje, że aplikacja korzysta z wielowątkowejej, statycznej wersji biblioteki wykonawczej.
- **Debugowanie wielowątkowe** — definiuje _DEBUG i _MT. Ta opcja powoduje także, że kompilator umieszcza nazwę biblioteki *libcmtd. lib* w pliku *`.obj`* , dzięki czemu konsolidator będzie używać *libcmtd. lib* do rozpoznawania symboli zewnętrznych.
- **Wielowątkowa Biblioteka DLL** — powoduje, że aplikacja korzysta z wersji biblioteki wykonawczej określonej przez wielowątkowej i biblioteki DLL. Definiuje _MT i _DLL i powoduje, że kompilator umieszcza nazwę biblioteki *msvcrt. lib* w pliku *`.obj`* .
- **Wielowątkowa Biblioteka DLL debugowania** — definiuje _DEBUG, _MT i _DLL i powoduje, że aplikacja korzysta z biblioteki wykonawczej wielowątkowej-i z biblioteką DLL. Powoduje także, że kompilator umieszcza nazwę biblioteki *msvcrtd. lib* w pliku *`.obj`* .

### <a name="struct-member-alignment"></a>Wyrównanie elementu członkowskiego struktury

Określa 1, 2, 4 lub 8-bajtowe granice dla wyrównania elementu członkowskiego struktury. Ustawia [/ZP](zp-struct-member-alignment.md).

#### <a name="choices"></a>Decyzji

- 1, struktury pakietów **bajtowych** na granicach 1-bajtowych. Taki sam jak **`/Zp`** .
- **2 bajty** — struktury pakietów przy 2-bajtowych granicach.
- **4 bajty** — struktury pakietów przy 4-bajtowych granicach.
- **8 bajtów** — struktury pakietów na 8-bajtowych granicach (domyślnie).
- **16 bajtów** — struktury pakietów na 16-bajtowych granicach.
- **Domyślne** — domyślne ustawienia wyrównania.

### <a name="security-check"></a>Sprawdzanie zabezpieczeń

Kontrola zabezpieczeń pomaga wykrywać bufory stosu w trybie failover, typowy atak na zabezpieczenia programu.

#### <a name="choices"></a>Decyzji

- **Wyłącz sprawdzanie zabezpieczeń** — Wyłącz sprawdzanie zabezpieczeń. Ustawia [/GS-](gs-buffer-security-check.md).
- **Włącz sprawdzanie zabezpieczeń** — Włącz sprawdzanie zabezpieczeń. Ustawia [/GS](gs-buffer-security-check.md).

### <a name="control-flow-guard"></a>Ochrona przepływu sterowania

Kontrola zabezpieczeń funkcji Guard pomaga wykrywać próby wysłania do niedozwolonego bloku kodu.

#### <a name="choices"></a>Decyzji

- **Tak** — Włącz sprawdzanie zabezpieczeń przy użyciu zestawów Guard [/Guard: CF](guard-enable-control-flow-guard.md).
- **Nie**

### <a name="enable-function-level-linking"></a>Włącz łączenie na poziomie funkcji

Umożliwia kompilatorowi pakowanie poszczególnych funkcji w postaci spakowanych funkcji (COMDAT). Wymagane do edycji i kontynuowania pracy. Ustawia [/Gy](gy-enable-function-level-linking.md).

### <a name="enable-parallel-code-generation"></a>Włącz równoległe generowanie kodu

Umożliwia kompilatorowi generowanie równoległego kodu dla pętli zidentyfikowanych przy użyciu `#pragma loop(hint_parallel[(n)])`, gdy Optymalizacja jest włączona.

### <a name="enable-enhanced-instruction-set"></a>Włącz rozszerzony zestaw instrukcji

Umożliwia korzystanie z instrukcji znalezionych na procesorach, które obsługują ulepszone zestawy instrukcji. Na przykład rozszerzenia SSE, SSE2, AVX i AVX2 na IA-32. I rozszerzenia AVX i AVX2 do wersji x64. Obecnie **`/arch:SSE`** i **`/arch:SSE2`** są dostępne tylko podczas kompilowania dla architektury x86. Jeśli żadna opcja nie zostanie określona, kompilator będzie używać instrukcji znalezionych na procesorach, które obsługują SSE2. Korzystanie z ulepszonych instrukcji można wyłączyć za pomocą **`/arch:IA32`** . Aby uzyskać więcej informacji, zobacz [/arch (x86)](arch-x86.md), [/arch (x64)](arch-x64.md) i [/arch (ARM)](arch-arm.md).

#### <a name="choices"></a>Decyzji

- **Streaming SIMD Extensions** -Streaming SIMD Extensions. Ustawia **`/arch:SSE`**
- **Streaming SIMD Extensions 2** — Streaming SIMD Extensions 2. Ustawia **`/arch:SSE2`**
- **Zaawansowane rozszerzenia wektorów** — zaawansowane rozszerzenia wektorów. Ustawia **`/arch:AVX`**
- **Zaawansowane rozszerzenia wektorów 2** — zaawansowane rozszerzenia wektorów 2. Ustawia **`/arch:AVX2`**
- **Brak rozszerzonych instrukcji** — brak rozszerzonych instrukcji. Ustawia **`/arch:IA32`**
- **Nie ustawiono** — nie ustawiono.

### <a name="floating-point-model"></a>Model zmiennoprzecinkowy

Ustawia model zmiennoprzecinkowy. Ustawia [/FP: precyzyjne,/FP: Strict,/FP: Fast](fp-specify-floating-point-behavior.md).

#### <a name="choices"></a>Decyzji

- **Precyzyjne** — wartość domyślna. Zwiększa spójność testów zmiennoprzecinkowych pod kątem równości i nierówności.
- **Rygorystyczne** — najdokładniejszy model zmiennoprzecinkowy. **`/fp:strict`** powoduje, że **`fp_contract`** być wyłączone i **`fenv_access`** . **`/fp:except`** jest implikowana i można ją wyłączyć przez jawne określenie **`/fp:except-`** . Gdy jest używany z **`/fp:except-`** , **`/fp:strict`** wymusza ścisłą semantykę liczb zmiennoprzecinkowych, ale bez przestrzegania wyjątkowych zdarzeń.
- **Fast** — tworzy najszybszy kod w większości przypadków.

### <a name="enable-floating-point-exceptions"></a>Włącz wyjątki zmiennoprzecinkowe

Wiarygodny model wyjątków zmiennopozycyjnych. Wyjątki będą wywoływane natychmiast po ich wyzwoleniu. Ustawia [/FP: z wyjątkiem](fp-specify-floating-point-behavior.md).

### <a name="create-hotpatchable-image"></a>Tworzenie obrazu możliwy do poprawiania

Gdy Funkcja HotPatching jest włączona, kompilator zapewnia, że pierwsza instrukcja każdej funkcji wynosi dwa bajty, co jest wymagane w przypadku stosowania poprawek na gorąco. Ustawia [/hotpatch](hotpatch-create-hotpatchable-image.md).

### <a name="spectre-mitigation"></a>Spectre środki zaradcze

Spectre środki zaradcze dla CVE 2017-5753. Ustawia [/Qspectre](qspectre.md).

#### <a name="choices"></a>Decyzji

- **Włączone** — Włącz funkcję łagodzenia Spectre dla CVE 2017-5753
- **Wyłączone** — nie ustawiono.

## <a name="cc-language-properties"></a>Właściwości językaC++ C/Language

### <a name="disable-language-extensions"></a>Wyłącz rozszerzenia językowe

Pomija lub włącza rozszerzenia językowe. Ustawia [/za](za-ze-disable-language-extensions.md).

### <a name="conformance-mode"></a>Tryb zgodności

Włącza lub wyłącza tryb zgodności. Ustawia [/permissive-](permissive-standards-conformance.md).

### <a name="treat-wchar_t-as-built-in-type"></a>Traktuj WChar_t jako typ wbudowany

Gdy jest określony, typ **wchar_t** jest typem natywnym, który mapuje do `__wchar_t` w taki sam sposób, jak **krótkie** mapy do `__int16`. [/Zc: wchar_t](zc-wchar-t-wchar-t-is-native-type.md) jest domyślnie włączona.

### <a name="force-conformance-in-for-loop-scope"></a>Wymuś zgodność w zakresie pętli for

Używane do implementowania C++ standardowego zachowania dla instrukcji for z rozszerzeniami Microsoft. Ustawia [/za,/ze (Wyłącz rozszerzenia językowe](za-ze-disable-language-extensions.md)). [/Zc: forScope](zc-forscope-force-conformance-in-for-loop-scope.md) jest domyślnie włączona.

### <a name="remove-unreferenced-code-and-data"></a>Usuń kod i dane, do których nie istnieją odwołania

Gdy jest określony, kompilator nie generuje już informacji o symbolach dla kodu i danych bez odwołań.

### <a name="enforce-type-conversion-rules"></a>Wymuszanie zasad konwersji typów

Służy do identyfikowania typu odwołania rvalue jako wyniku operacji rzutowania zgodnie ze standardem C++ 11.

### <a name="enable-run-time-type-information"></a>Włącz informacje o typie w czasie wykonywania

Dodaje kod do sprawdzania C++ typów obiektów w czasie wykonywania (informacje o typie środowiska uruchomieniowego). Ustawia [/gr,/gr-](gr-enable-run-time-type-information.md).

### <a name="open-mp-support"></a>Obsługa otwartych pakietów MP

Włącza rozszerzenia języka OpenMP 2,0. Ustawia [/OpenMP](openmp-enable-openmp-2-0-support.md).

### <a name="c-language-standard"></a>C++Standard języka

Określa standard C++ języka włączanego przez kompilator. Użyj najnowszej wersji, gdy jest to możliwe. Ustawia [/std: c++ 14,/std: c++ 17,/std: c + + Najnowsza](std-specify-language-standard-version.md).

#### <a name="choices"></a>Decyzji

- **Domyślne**
- **Standard ISO C++ 14**
- **Standard ISO C++ 17**
- **Wersja zapoznawcza — funkcje C++ z najnowszego roboczej wersji roboczej**

### <a name="enable-c-modules-experimental"></a>Włącz C++ moduły (eksperymentalne)

Eksperymentalna obsługa C++ modułów TS i biblioteki standardowej.

## <a name="cc-precompiled-headers-properties"></a>Właściwości prekompilowanego nagłówka C/C++

### <a name="createuse-precompiled-header"></a>Utwórz/Użyj prekompilowanego nagłówka

Umożliwia utworzenie lub użycie prekompilowanego nagłówka podczas kompilowania. Ustawia [/YC](yc-create-precompiled-header-file.md), [/Yu](yu-use-precompiled-header-file.md).

#### <a name="choices"></a>Decyzji

- **Create** — instruuje kompilator, aby utworzył prekompilowany plik nagłówkowy (. pch), który reprezentuje stan kompilacji w określonym punkcie.
- **Użyj** — instruuje kompilator, aby korzystał z istniejącego prekompilowanego pliku nagłówkowego (. pch) w bieżącej kompilacji.
- **Nie używa prekompilowanych nagłówków** — nie używa prekompilowanych nagłówków.

### <a name="precompiled-header-file"></a>Prekompilowany plik nagłówkowy

Określa nazwę pliku nagłówkowego, który ma być używany podczas tworzenia lub używania prekompilowanego pliku nagłówkowego. Ustawia [/YC](yc-create-precompiled-header-file.md), [/Yu]] (Yu-use-prekompilowany-header-File.MD).

### <a name="precompiled-header-output-file"></a>Plik wyjściowy prekompilowanego nagłówka

Określa ścieżkę lub nazwę wygenerowanego prekompilowanego pliku nagłówkowego. Ustawia [/FP](fp-name-dot-pch-file.md).

## <a name="cc-output-files-properties"></a>Właściwości plikówC++ C/Output

### <a name="expand-attributed-source"></a>Rozwiń źródło z atrybutami

Utwórz plik listy z rozwiniętymi atrybutami, które zostały dodane do pliku źródłowego. Ustawia [/FX](fx-merge-injected-code.md).

### <a name="assembler-output"></a>Dane wyjściowe asemblera

Określa zawartość pliku wyjściowego języka asemblera. Ustawia [/FA,/FAc,/FAS,/FACS](fa-fa-listing-file.md).

#### <a name="choices"></a>Decyzji

- **Brak listy** — brak listy.
- **Listing tylko dla zestawu** — kod asemblera; *`.asm`*
- **Zestaw z kodem maszynowym** i kodem modułu; *`.cod`*
- **Zestaw ze źródłem kodu źródłowego** i kodem zestawu; *`.asm`*
- **Zestaw, kod maszynowy i zestaw źródłowy** , kod maszynowy i kod źródłowy; *`.cod`*

### <a name="use-unicode-for-assembler-listing"></a>Użyj Unicode dla list asemblera

Powoduje, że plik wyjściowy zostanie utworzony w formacie UTF-8.

### <a name="asm-list-location"></a>Lokalizacja listy ASM

Określa ścieżkę względną lub nazwę pliku listy ASM; może to być nazwa pliku lub katalogu. Ustawia [/FA](fa-fa-listing-file.md).

### <a name="object-file-name"></a>Nazwa pliku obiektu

Określa nazwę do przesłaniania domyślnej nazwy pliku obiektu; może to być nazwa pliku lub katalogu. Ustawia [/fo](fo-object-file-name.md).

### <a name="program-database-file-name"></a>Nazwa pliku bazy danych programu

Określa nazwę pliku PDB wygenerowanego przez kompilator; określa również nazwę podstawową dla wymaganego pliku IDB generowanego przez kompilator; może to być nazwa pliku lub katalogu. Ustawia [/FD](fd-program-database-file-name.md).

### <a name="generate-xml-documentation-files"></a>Generuj pliki dokumentacji XML

Określa, że kompilator ma generować pliki komentarzy dokumentacji XML (. XDC). Ustawia [/doc](doc-process-documentation-comments-c-cpp.md).

### <a name="xml-documentation-file-name"></a>Nazwa pliku dokumentacji XML

Określa nazwę wygenerowanego pliku dokumentacji XML; może to być nazwa pliku lub katalogu. Ustawia [/doc: > nazwa\<](doc-process-documentation-comments-c-cpp.md).

## <a name="cc-browse-information-properties"></a>Właściwości informacjiC++ o języku C/Browse

### <a name="enable-browse-information"></a>Włącz informacje o przeglądaniu

Określa poziom informacji o przeglądaniu w pliku *`.bsc`* . Ustawia [/fr](fr-fr-create-dot-sbr-file.md).

### <a name="browse-information-file"></a>Przeglądaj plik informacji

Określa opcjonalną nazwę pliku informacji o przeglądarce. Ustawia [nazwę/FR\<>](fr-fr-create-dot-sbr-file.md).

## <a name="cc-advanced-properties"></a>Właściwości CC++ /Advanced

### <a name="calling-convention"></a>Konwencja wywoływania

Wybierz domyślną konwencję wywoływania dla aplikacji (może być zastąpiona przez funkcję). Ustawia [/GD,/gr,/GZ,/GV](gd-gr-gv-gz-calling-convention.md).

#### <a name="choices"></a>Decyzji

- **__cdecl** — określa __cdecl konwencji wywoływania dla wszystkich funkcji, z C++ wyjątkiem funkcji składowych i funkcji oznaczonych jako __stdcall lub __fastcall.
- **__fastcall** — określa __fastcall konwencji wywoływania dla wszystkich funkcji, z C++ wyjątkiem funkcji składowych i funkcji oznaczonych jako __cdecl lub __stdcall. Wszystkie funkcje __fastcall muszą mieć prototypy.
- **__stdcall** — określa __stdcall Konwencji wywoływania dla wszystkich funkcji, z C++ wyjątkiem funkcji składowych i funkcji oznaczonych jako __cdecl lub __fastcall. Wszystkie funkcje __stdcall muszą mieć prototypy.
- **__vectorcall** — określa __vectorcall konwencji wywoływania dla wszystkich funkcji, z C++ wyjątkiem funkcji składowych i funkcji oznaczonych jako __cdecl, __fastcall lub __stdcall. Wszystkie funkcje __vectorcall muszą mieć prototypy.

### <a name="compile-as"></a>Kompiluj jako

Wybierz opcję języka kompilowania dla plików *`.c`* i *`.cpp`* . Ustawia [/TC,/TP](tc-tp-tc-tp-specify-source-file-type.md).

#### <a name="choices"></a>Decyzji

- **Domyślne** — domyślnie.
- **Kompiluj jako kod c** Kompiluj jako kod c.
- **Kompiluj jako C++**  kod Kompiluj jako C++ kod.

### <a name="disable-specific-warnings"></a>Wyłącz określone ostrzeżenia

Wyłącz określone numery ostrzegawcze. Numery ostrzeżeń należy umieścić na liście rozdzielanej średnikami. Ustawia [/wd\<num >](compiler-option-warning-level.md).

### <a name="forced-include-file"></a>Wymuszony plik dyrektywy include

co najmniej jeden wymuszony plik dyrektywy include. Ustawia [/fi\<nazw >](fi-name-forced-include-file.md).

### <a name="forced-using-file"></a>Wymuszony plik #using

Określa co najmniej jeden wymuszony #using plików. Ustawia [nazwę/FU\<>](fu-name-forced-hash-using-file.md).

### <a name="show-includes"></a>Pokaż zawiera

Generuje listę plików dołączanych z danymi wyjściowymi kompilatora. Ustawia [/showIncludes](showincludes-list-include-files.md).

### <a name="use-full-paths"></a>Użyj pełnych ścieżek

Używaj pełnych ścieżek w komunikatach diagnostycznych. Ustawia [/FC](fc-full-path-of-source-code-file-in-diagnostics.md).

### <a name="omit-default-library-name"></a>Pomiń domyślną nazwę biblioteki

Nie zawiera domyślnych nazw bibliotek w plikach *`.obj`* . Ustawia [/zl](zl-omit-default-library-name.md).

### <a name="internal-compiler-error-reporting"></a>Raportowanie wewnętrznego błędu kompilatora

> [!NOTE]
> Ta opcja jest przestarzała. Począwszy od systemu Windows Vista, raportowanie błędów jest kontrolowane przez ustawienia [raportowanie błędów systemu Windows (wer)](/windows/win32/wer/windows-error-reporting) .

### <a name="treat-specific-warnings-as-errors"></a>Traktuj konkretne ostrzeżenia jako błędy

Traktuje określone Ostrzeżenie kompilatora jako błąd, gdzie n to ostrzeżenie kompilatora.

### <a name="additional-options"></a>Opcje dodatkowe

Opcje dodatkowe.
