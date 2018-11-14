---
title: Opcje kompilatora w rozbiciu na kategorie
ms.date: 11/12/2018
helpviewer_keywords:
- compiler options, C++
ms.assetid: c4750dcf-dba0-4229-99b6-45cdecc11729
ms.openlocfilehash: aa93158e518950efa9d1f2f8092aeabbc3c7724c
ms.sourcegitcommit: 99437d7da4528ce72cabe6b6a65a9be5dfd090f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2018
ms.locfileid: "51598824"
---
# <a name="compiler-options-listed-by-category"></a>Opcje kompilatora w rozbiciu na kategorie

Ten artykuł zawiera podzieloną na kategorie listę opcji kompilatora. Aby uzyskać alfabetyczną listę, zobacz [kompilatora wymienione opcje alfabetycznie](compiler-options-listed-alphabetically.md).

### <a name="optimization"></a>Optymalizacja

|Opcja|Cel|
|------------|-------------|
|[/O1](o1-o2-minimize-size-maximize-speed.md)|Tworzy mały kod.|
|[/O2](o1-o2-minimize-size-maximize-speed.md)|Tworzy szybki kod.|
|[/Ob](ob-inline-function-expansion.md)|Kontroluje wbudowane rozwijanie.|
|[/Od](od-disable-debug.md)|Wyłącza optymalizację.|
|[/Og](og-global-optimizations.md)|Przestarzałe. Używa globalnych optymalizacji.|
|[/OI](oi-generate-intrinsic-functions.md)|Generuje funkcje wewnętrzne.|
|[/ OS](os-ot-favor-small-code-favor-fast-code.md)|Preferuje mały kod.|
|[/OT](os-ot-favor-small-code-favor-fast-code.md)|Preferuje szybki kod.|
|[/Ox](ox-full-optimization.md)|Używa maksymalnej optymalizacji (/ Ob2gity/GS).|
|[/Oy](oy-frame-pointer-omission.md)|Pomija wskaźnik ramki. (tylko x86)|
|[/favor](favor-optimize-for-architecture-specifics.md)|Generuje kod, który jest zoptymalizowany dla określonej architektury lub dla zakresu architektur.|

### <a name="code-generation"></a>Generowanie kodu

|Opcja|Cel|
|------------|-------------|
|[/ arch](arch-x86.md)|Użyj instrukcji SSE lub SSE2 przy generowaniu kodu. (tylko x86)|
|[/clr](clr-common-language-runtime-compilation.md)|Tworzy plik wyjściowy do uruchomienia w środowisku uruchomieniowym języka wspólnego.|
|[/EH](eh-exception-handling-model.md)|Określa model obsługi wyjątków.|
|[/ FP](fp-specify-floating-point-behavior.md)|Określa zachowanie liczb zmiennopozycyjnych.|
|[/GA](ga-optimize-for-windows-application.md)|Optymalizuje dla aplikacji Windows.|
|[/Gd](gd-gr-gv-gz-calling-convention.md)|Używa `__cdecl` konwencji wywoływania. (tylko x86)|
|[/Ge](ge-enable-stack-probes.md)|Przestarzałe. Uaktywnia sondy stosu.|
|[/GF](gf-eliminate-duplicate-strings.md)|Włącza buforowanie ciągów.|
|[/Gh](gh-enable-penter-hook-function.md)|Wywołuje funkcję podłączania `_penter`.|
|[/GH](gh-enable-pexit-hook-function.md)|Wywołuje funkcję podłączania `_pexit`.|
|[/GL](gl-whole-program-optimization.md)|Włącza optymalizację całego programu.|
|[/Gm](gm-enable-minimal-rebuild.md)|Przestarzałe. Włącza minimalną ponowną kompilację.|
|[/GR](gr-enable-run-time-type-information.md)|Włącza informacje typu run-time (RTTI).|
|[/Gr](gd-gr-gv-gz-calling-convention.md)|Używa `__fastcall` konwencji wywoływania. (tylko x86)|
|[/GS](gs-buffer-security-check.md)|Sprawdza zabezpieczenia buforu.|
|[/ GS](gs-control-stack-checking-calls.md)|Kontroluje sondy stosu.|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|Obsługuje bezpieczeństwo włókien dla danych przydzielonych przy użyciu statycznego magazynu wątków lokalnych.|
|[/ GUARD: CF](guard-enable-control-flow-guard.md)|Dodaje kontrole zabezpieczeń Ochrona przepływu sterowania.|
|[/Gv](gd-gr-gv-gz-calling-convention.md)|Używa `__vectorcall` konwencji wywoływania. (x86 i x64 tylko)|
|[/Gw](gw-optimize-global-data.md)|Umożliwia optymalizację danych globalnych całego programu.|
|[/GX](gx-enable-exception-handling.md)|Przestarzałe. Włącza synchroniczną obsługę wyjątków. Użyj [/EH](eh-exception-handling-model.md) zamiast tego.|
|[/Gy](gy-enable-function-level-linking.md)|Włącza funkcję łączenie na poziomie.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Przestarzałe. Umożliwia szybkie testy. (Taka sama jak [rtc1](rtc-run-time-error-checks.md))|
|[/Gz](gd-gr-gv-gz-calling-convention.md)|Używa `__stdcall` konwencji wywoływania. (tylko x86)|
|[/ homeparams](homeparams-copy-register-parameters-to-stack.md)|Wymusza zapisanie parametrów przekazanych w rejestrach były zapisywane do ich lokalizacji na stosie wejściu do funkcji. Ta opcja kompilatora jest tylko w przypadku x64 kompilatory (kompilacja natywna i krzyżowa).|
|[/hotpatch](hotpatch-create-hotpatchable-image.md)|Tworzy obraz hotpatchable.|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|Generuje fast transcendentals.|
|[QIfist](qifist-suppress-ftol.md)|Przestarzałe. Pomija wywołanie funkcji pomocnika `_ftol` podczas konwersji z typu zmiennoprzecinkowego na typ całkowity jest wymagany. (tylko x86)|
|[/Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|Usuwa `fwait` polecenia wewnątrz `try` bloków.|
|[/Qpar](qpar-auto-parallelizer.md)|Włącza automatyczne przetwarzanie równoległe pętli.|
|[/ Qpar raport](qpar-report-auto-parallelizer-reporting-level.md)|Włącza poziomy raportowania dla automatycznego przetwarzania równoległego.|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|Używa całkowitoliczbowych instrukcji przeniesienia dla wartości zmiennopozycyjnych i wyłącza niektóre ładowania zmiennopozycyjnego.|
|[/Qspectre](qspectre.md)|Włącz spectre dla CVE 2017-5753 dla klasy z krokami zaradczymi dla luki ataków.|
|[/Qvec-report](qvec-report-auto-vectorizer-reporting-level.md)|Włącza poziomy raportowania dla automatycznej wektoryzacji.|
|[/RTC](rtc-run-time-error-checks.md)|Włącza sprawdzanie błędów czasu wykonywania.|
|[/volatile](volatile-volatile-keyword-interpretation.md)|Wybiera, jaki volatile — słowo kluczowe jest interpretowany.|

### <a name="output-files"></a>Pliki wyjściowe

|Opcja|Cel|
|------------|-------------|
|[/doc](doc-process-documentation-comments-c-cpp.md)|Przetwarza komentarze dokumentacji do pliku XML.|
|[/FA](fa-fa-listing-file.md)|Konfiguruje plik listy zestawu.|
|[/Fa](fa-fa-listing-file.md)|Tworzy plik listy zestawu.|
|[/FD](fd-program-database-file-name.md)|Zmienia nazwę pliku bazy danych programu.|
|[/Fe](fe-name-exe-file.md)|Zmienia nazwę pliku wykonywalnego.|
|[/Fi](fi-preprocess-output-file-name.md)|Określa nazwę pliku wstępnie przetworzone produkty wyjściowe.|
|[/Fm](fm-name-mapfile.md)|Tworzy plik mapy.|
|[/FO](fo-object-file-name.md)|Tworzy plik obiektu.|
|[/ FP](fp-name-dot-pch-file.md)|Określa nazwę prekompilowanego pliku nagłówka.|
|[/ FR, /Fr](fr-fr-create-dot-sbr-file.md)|Wygenerowana nazwa SBR, pliki przeglądarki.|

### <a name="preprocessor"></a>Preprocesor

|Opcja|Cel|
|------------|-------------|
|[/AI](ai-specify-metadata-directories.md)|Określa katalog do przeszukania w celu rozpoznania odwołań do plików przekazywanych do [#using](../../preprocessor/hash-using-directive-cpp.md) dyrektywy.|
|[/C](c-preserve-comments-during-preprocessing.md)|Zachowuje komentarze podczas przetwarzania wstępnego.|
|[/D](d-preprocessor-definitions.md)|Definiuje stałe i makra.|
|[/E](e-preprocess-to-stdout.md)|Kopiuje dane wyjściowe preprocesora do wyjścia standardowego.|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|Kopiuje dane wyjściowe preprocesora do wyjścia standardowego.|
|[/FI](fi-name-forced-include-file.md)|Wstępnie przetwarza określony plik do dołączenia.|
|[/FU](fu-name-forced-hash-using-file.md)|Wymusza użycie nazwy pliku, tak jakby została przekazana do [#using](../../preprocessor/hash-using-directive-cpp.md) dyrektywy.|
|[/Fx](fx-merge-injected-code.md)|Scala wprowadzony kod z plikiem źródłowym.|
|[/I](i-additional-include-directories.md)|Przeszukuje katalog plików dołączanych.|
|[/P](p-preprocess-to-a-file.md)|Zapisuje dane wyjściowe preprocesora do pliku.|
|[/U](u-u-undefine-symbols.md)|Usuwa wstępnie zdefiniowane makro.|
|[/u](u-u-undefine-symbols.md)|Usuwa wszystkie wstępnie zdefiniowane makra.|
|[/X](x-ignore-standard-include-paths.md)|Ignoruje Standardowy katalog plików dołączanych.|

### <a name="language"></a>Język

|Opcja|Cel|
|------------|-------------|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|Szacowanie kontrolki constexpr w czasie kompilacji.|
|[/ OpenMP](openmp-enable-openmp-2-0-support.md)|Włącza [#pragma omp](../../preprocessor/omp.md) w kodzie źródłowym.|
|[/vd](vd-disable-construction-displacements.md)|Wyłącza lub włącza ukryte `vtordisp` składowych klasy.|
|[/vmb](vmb-vmg-representation-method.md)|Używa najlepszej podstawy dla wskaźników do elementów członkowskich.|
|[/vmg](vmb-vmg-representation-method.md)|Używa pełnej ogólności dla wskaźników do elementów członkowskich.|
|[/vmm](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje wielokrotne dziedziczenie.|
|[/vms](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje pojedyncze dziedziczenie.|
|[/vmv](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje wirtualne dziedziczenie.|
|[/Z7](z7-zi-zi-debug-information-format.md)|Generuje informacje debugowania zgodne 7.0 C.|
|[/Za](za-ze-disable-language-extensions.md)|Wyłącza rozszerzenia językowe.|
|[/Zc](zc-conformance.md)|Określa standardowe zachowanie dla opcji [/Ze](za-ze-disable-language-extensions.md).|
|[/Ze](za-ze-disable-language-extensions.md)|Przestarzałe. Włącza rozszerzenia językowe.|
|[/Zf](zf.md)|Poprawia PDB czas generowania w kompilacjach równoległych.|
|[/ZI](z7-zi-zi-debug-information-format.md)|Zawiera informacje o debugowaniu w bazie danych programu zgodne z funkcją Edytuj i Kontynuuj. (tylko x86)|
|[/Zi](z7-zi-zi-debug-information-format.md)|Generuje kompletne informacje debugowania.|
|[/Zl](zl-omit-default-library-name.md)|Usuwa domyślną nazwę biblioteki z pliku .obj.|
|[/ ZP](zp-struct-member-alignment.md) *n*|Pakuje elementy członkowskie struktury.|
|[/Zs](zs-syntax-check-only.md)|Sprawdza tylko składnię.|
|[/ZW](zw-windows-runtime-compilation.md)|Tworzy plik wyjściowy do uruchomienia na środowiska wykonawczego Windows.|

### <a name="linking"></a>Konsolidacja

|Opcja|Cel|
|------------|-------------|
|[/F](f-set-stack-size.md)|Ustawia rozmiar stosu.|
|[/LD](md-mt-ld-use-run-time-library.md)|Tworzy bibliotekę DLL.|
|[/LDd](md-mt-ld-use-run-time-library.md)|Tworzy bibliotekę DLL debugowania.|
|[/link](link-pass-options-to-linker.md)|Przekazuje określoną opcję do łącza.|
|[/LN](ln-create-msil-module.md)|Tworzy moduł MSIL.|
|[/MD](md-mt-ld-use-run-time-library.md)|Kompiluje, aby utworzyć wielowątkową bibliotekę DLL przy użyciu biblioteki MSVCRT.lib.|
|[/MDd](md-mt-ld-use-run-time-library.md)|Kompiluje, aby utworzyć debugowania wielowątkową bibliotekę DLL przy użyciu biblioteki MSVCRTD.lib.|
|[/MT](md-mt-ld-use-run-time-library.md)|Kompiluje, aby utworzyć wielowątkowy plik wykonywalny przy użyciu biblioteki LIBCMT.lib.|
|[/ MTd](md-mt-ld-use-run-time-library.md)|Kompiluje, aby utworzyć wielowątkowy plik wykonywalny debugowania, przy użyciu biblioteki LIBCMTD.lib.|

### <a name="miscellaneous"></a>Różne

|Opcja|Cel|
|------------|-------------|
|[/?](help-compiler-command-line-help.md)|Wyświetla listę opcji kompilatora.|
|[@](at-specify-a-compiler-response-file.md)|Określa plik odpowiedzi.|
|[/ analyze](analyze-code-analysis.md)|Włącza analizę kodu.|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|Zwiększa liczbę możliwych do adresowania sekcji w pliku .obj.|
|[/c](c-compile-without-linking.md)|Kompiluje bez konsolidacji.|
|[/cgthreads](cgthreads-code-generation-threads.md)|Określa liczbę wątków cl.exe na potrzeby optymalizacji i generowania kodu.|
|[/errorReport](errorreport-report-internal-compiler-errors.md)|Pozwala na dostarczenie informacji o błędzie (ICE) na wewnętrznych kompilatora bezpośrednio do zespołu Visual C++.|
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|Wyświetla pełną ścieżkę plików kodu źródłowego przekazanych do cl.exe w tekście diagnostycznym.|
|[/FS](fs-force-synchronous-pdb-writes.md)|Wymusza zapisanie do pliku bazy danych (PDB) programu w celu serializowana za pośrednictwem MSPDBSRV. PLIK EXE.|
|[/H](h-restrict-length-of-external-names.md)|Przestarzałe. Ogranicza długość nazw zewnętrznych (publicznych).|
|[/HELP](help-compiler-command-line-help.md)|Wyświetla listę opcji kompilatora.|
|[/J](j-default-char-type-is-unsigned.md)|Zmienia domyślny `char` typu.|
|[/ JMC](jmc.md)|Obsługuje debugowanie natywne C++ tylko mój kod.|
|[/kernel](kernel-create-kernel-mode-binary.md)|Kompilator i konsolidator utworzą plik binarny, który może zostać wykonany w jądrze Windows.|
|[/MP](mp-build-with-multiple-processes.md)|Kompiluje jednocześnie wiele plików źródłowych.|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|Pomija wyświetlanie transparentu logowania.|
|[/ SDL](sdl-enable-additional-security-checks.md)|Umożliwia dodatkowe funkcje zabezpieczeń i ostrzeżenia.|
|[/ showincludes](showincludes-list-include-files.md)|Wyświetla listę wszystkich obejmują pliki, podczas kompilacji.|
|[/Tc](tc-tp-tc-tp-specify-source-file-type.md)|Określa plik źródłowy C.|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|Określa, że wszystkie pliki źródłowe znajdują się C.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Określa plik źródłowy języka C++.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Określa, że wszystkie pliki źródłowe C++.|
|[/V](v-version-number.md)|Przestarzałe. Ustawia ciąg wersji.|
|[/w](compiler-option-warning-level.md)|Wyłącza wszystkie ostrzeżenia.|
|[/W0, /W1, /W2, /W3, /W4](compiler-option-warning-level.md)|Zestawy danych wyjściowych poziom ostrzeżeń.|
|[/w1, /w2, /w3, /w4](compiler-option-warning-level.md)|Ustawia poziom ostrzeżeń dla określone ostrzeżenie.|
|[/Wall](compiler-option-warning-level.md)|Włącza wszystkie ostrzeżenia, łącznie z ostrzeżeniami, które są domyślnie wyłączone.|
|[/WD](compiler-option-warning-level.md)|Wyłącza określone ostrzeżenie.|
|[/we](compiler-option-warning-level.md)|Traktuje określone ostrzeżenie jako błąd.|
|[/WL](wl-enable-one-line-diagnostics.md)|Włącza diagnostykę dla błędów i komunikaty ostrzegawcze podczas kompilowania kodu źródłowego języka C++ z poziomu wiersza polecenia.|
|[/WO](compiler-option-warning-level.md)|Wyświetla określoną ostrzeżenie tylko raz.|
|[/Wv](compiler-option-warning-level.md)|Wyłącza ostrzeżenia wprowadzone w nowszych wersjach kompilatora.|
|[/WX](compiler-option-warning-level.md)|Traktuje ostrzeżeń jako błędy.|
|[/Yc](yc-create-precompiled-header-file.md)|Utwórz. Plik PCH.|
|[/YD](yd-place-debug-information-in-object-file.md)|Przestarzałe. Umieszcza pełne informacje debugowania we wszystkich plikach obiektu. Użyj [/zi](z7-zi-zi-debug-information-format.md) zamiast tego.|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|Wstawia odwołanie kompilatora PCH podczas tworzenia biblioteki debugowania.|
|[/Yu](yu-use-precompiled-header-file.md)|Używa prekompilowanego pliku nagłówkowego podczas kompilacji.|
|[/Y-](y-ignore-precompiled-header-options.md)|Ignoruje wszystkie inne opcje kompilatora wstępnie skompilowanego nagłówka w bieżącej kompilacji.|
|[/Zm](zm-specify-precompiled-header-memory-allocation-limit.md)|Określa limit alokacji pamięci prekompilowanego nagłówka.|
|[/await](await-enable-coroutine-support.md)|Włącz rozszerzenia w koprocedury (z funkcji wznawialnych).|
|[/ Source-Charset](source-charset-set-source-character-set.md)|Ustaw źródłowy zestaw znaków.|
|[/ Execution-Charset](execution-charset-set-execution-character-set.md)|Ustaw zestaw znaków wykonywania.|
|[/utf-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|Ustawia zestaw znaków źródła i wykonania na UTF-8.|
|[/validate-charset](validate-charset-validate-for-compatible-characters.md)|Sprawdź poprawność plików UTF-8 tylko zgodność znaków.|
|[/ Diagnostics](diagnostics-compiler-diagnostic-options.md)|Kontroluje format komunikatów diagnostycznych.|
|[/ permissive-](permissive-standards-conformance.md)|Ustaw tryb zgodności standard.|
|[/ STD](std-specify-language-standard-version.md)|Selektor zgodności wersję standardu języka C++.|

### <a name="deprecated-and-removed-compiler-options"></a>Opcje kompilatora przestarzałe i usunięte

|Opcja|Cel|
|------------|-------------|
|[/CLR:noAssembly](clr-common-language-runtime-compilation.md)|Przestarzałe. Użyj [/LN (Utwórz moduł MSIL)](ln-create-msil-module.md) zamiast tego.|
|[/FR](fr-fr-create-dot-sbr-file.md)|Przestarzałe. Tworzy plik przeglądania informacji bez zmiennych lokalnych.|
|[/Ge](ge-enable-stack-probes.md)|Przestarzałe. Uaktywnia sondy stosu. Na domyślnie.|
|[/Gm](gm-enable-minimal-rebuild.md)|Przestarzałe. Włącza minimalną ponowną kompilację.|
|[/GX](gx-enable-exception-handling.md)|Przestarzałe. Włącza synchroniczną obsługę wyjątków. Użyj [/EH](eh-exception-handling-model.md) zamiast tego.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Przestarzałe. Umożliwia szybkie testy. Użyj [rtc1](rtc-run-time-error-checks.md) zamiast tego.|
|[/H](h-restrict-length-of-external-names.md)|Przestarzałe. Ogranicza długość nazw zewnętrznych (publicznych).|
|[/Og](og-global-optimizations.md)|Przestarzałe. Używa globalnych optymalizacji.|
|[QIfist](qifist-suppress-ftol.md)|Przestarzałe. Gdy jest używany do określenia jak konwertować z typu zmiennoprzecinkowego na typ całkowity.|
|[/V](v-version-number.md)|Przestarzałe. Ustawia ciąg wersji pliku .obj.|
|[/Wp64](wp64-detect-64-bit-portability-issues.md)|Nieaktualne. Wykrywa problemy przenośności w programowaniu 64-bitowych.|
|[/YD](yd-place-debug-information-in-object-file.md)|Przestarzałe. Umieszcza pełne informacje debugowania we wszystkich plikach obiektu. Użyj [/zi](z7-zi-zi-debug-information-format.md) zamiast tego.|
|[/Zc:forScope-](zc-forscope-force-conformance-in-for-loop-scope.md)|Przestarzałe. Wyłącza zgodność w zakresie pętli for.|
|[/Ze](za-ze-disable-language-extensions.md)|Przestarzałe. Włącza rozszerzenia językowe.|
|[/Zg](zg-generate-function-prototypes.md)|Usunięte w programie Visual C++ 2015. Generuje prototypy funkcji.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja kompilacji w języku C/C++](c-cpp-building-reference.md)<br/>
[Opcje kompilatora](compiler-options.md)<br/>
[Ustawianie opcji kompilatora](setting-compiler-options.md)<br/>
