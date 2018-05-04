---
title: Opcje kompilatora rozbiciu na kategorie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiler options, C++
ms.assetid: c4750dcf-dba0-4229-99b6-45cdecc11729
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fff661bf573ca30a5b0e7550c2e53b00a7ff3d8f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="compiler-options-listed-by-category"></a>Opcje kompilatora w rozbiciu na kategorie

Ten artykuł zawiera listę kategorii opcji kompilatora. Aby uzyskać alfabetyczną listę, zobacz [kompilatora wymienione opcje alfabetycznie](compiler-options-listed-alphabetically.md).

### <a name="optimization"></a>Optymalizacja

|Opcja|Cel|
|------------|-------------|
|[/O1](o1-o2-minimize-size-maximize-speed.md)|Tworzy mały kod.|
|[/O2](o1-o2-minimize-size-maximize-speed.md)|Tworzy szybki kod.|
|[/Ob](ob-inline-function-expansion.md)|Określa rozszerzenie funkcji wbudowanej.|
|[/Od](od-disable-debug.md)|Wyłącza optymalizacji.|
|[/Og](og-global-optimizations.md)|Przestarzałe. Używa optymalizacje globalne.|
|[/OI](oi-generate-intrinsic-functions.md)|Generuje funkcje wewnętrzne.|
|[/ OS](os-ot-favor-small-code-favor-fast-code.md)|Preferuje mały kod.|
|[/OT](os-ot-favor-small-code-favor-fast-code.md)|Pełne szybki kod.|
|[/Ox](ox-full-optimization.md)|Używa optymalizacji maksymalną (/ Ob2gity/GS).|
|[/Oy](oy-frame-pointer-omission.md)|Umożliwia pominięcie wskaźnika ramki. (tylko x86)|
|[/favor](favor-optimize-for-architecture-specifics.md)|Generuje kod, który jest zoptymalizowana dla określonej architektury lub różnych architektur.|

### <a name="code-generation"></a>Generowanie kodu

|Opcja|Cel|
|------------|-------------|
|[/ arch](arch-x86.md)|Użyj instrukcji SSE i SSE2 podczas generowania kodu. (tylko x86)|
|[/clr](clr-common-language-runtime-compilation.md)|Tworzy plik wyjściowy do uruchamiania na środowisko uruchomieniowe języka wspólnego.|
|[/EH](eh-exception-handling-model.md)|Określa model obsługi wyjątków.|
|[/ FP](fp-specify-floating-point-behavior.md)|Określa zachowanie zmiennoprzecinkowych.|
|[/GA](ga-optimize-for-windows-application.md)|Optymalizuje dla aplikacji systemu Windows.|
|[/Gd](gd-gr-gv-gz-calling-convention.md)|Używa `__cdecl` konwencji wywoływania. (tylko x86)|
|[/Ge](ge-enable-stack-probes.md)|Przestarzałe. Aktywuje sondy stosu.|
|[/GF](gf-eliminate-duplicate-strings.md)|Włącza buforowanie ciągów.|
|[/Gh](gh-enable-penter-hook-function.md)|Wywołania funkcji utworzenie punktu zaczepienia `_penter`.|
|[/GH](gh-enable-pexit-hook-function.md)|Wywołania funkcji utworzenie punktu zaczepienia `_pexit`.|
|[/GL](gl-whole-program-optimization.md)|Włącza optymalizację całego programu.|
|[/Gm](gm-enable-minimal-rebuild.md)|Umożliwia minimalnego ponownie.|
|[/GR](gr-enable-run-time-type-information.md)|Umożliwia informacje typu run-time (RTTI).|
|[/Gr](gd-gr-gv-gz-calling-convention.md)|Używa `__fastcall` konwencji wywoływania. (tylko x86)|
|[/GS](gs-buffer-security-check.md)|Sprawdzanie buforu zabezpieczeń.|
|[/ GS](gs-control-stack-checking-calls.md)|Sondy stosu kontrolki.|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|Obsługuje bezpieczeństwa włókien danych przydzielone za pomocą statycznego magazynu wątków lokalnych.|
|[/ GUARD: CF](guard-enable-control-flow-guard.md)|Dodaje kontroli zabezpieczeń guard przepływu sterowania.|
|[/Gv](gd-gr-gv-gz-calling-convention.md)|Używa `__vectorcall` konwencji wywoływania. (x86 i x64 tylko)|
|[/Gw](gw-optimize-global-data.md)|Włącza optymalizację całego programu danych globalnych.|
|[/GX](gx-enable-exception-handling.md)|Przestarzałe. Włącza obsługę synchronicznych wyjątku. Użyj [/EH](eh-exception-handling-model.md) zamiast tego.|
|[/Gy](gy-enable-function-level-linking.md)|Umożliwia poziomie funkcji łączenia.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Przestarzałe. Umożliwia szybkie sprawdzenie. (Taki sam jak [rtc1](rtc-run-time-error-checks.md))|
|[/Gz](gd-gr-gv-gz-calling-convention.md)|Używa `__stdcall` konwencji wywoływania. (tylko x86)|
|[/ homeparams](homeparams-copy-register-parameters-to-stack.md)|Wymusza parametry przekazywane w rejestrach były zapisywane miejsca na stosie wejścia funkcji. Ta opcja kompilatora jest tylko w przypadku [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] kompilatory (natywne i Międzyplatformowe kompilacji).|
|[/hotpatch](hotpatch-create-hotpatchable-image.md)|Tworzy obraz możliwych.|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|Generuje fast transcendentals.|
|[QIfist](qifist-suppress-ftol.md)|Przestarzałe. Pomija wywołanie funkcji Pomocnik `_ftol` podczas konwersji z typu zmiennoprzecinkowego na typ całkowity jest wymagana. (tylko x86)|
|[/Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|Usuwa `fwait` poleceniach wewnątrz `try` bloków.|
|[/Qpar](qpar-auto-parallelizer.md)|Umożliwia automatyczne paralelizacja pętli.|
|[/ Qpar raport](qpar-report-auto-parallelizer-reporting-level.md)|Włącza raportowanie poziomy automatyczna paralelizacja.|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|Instrukcje przenoszenia całkowitą używa wartości zmiennoprzecinkowych i wyłącza niektórych zmiennoprzecinkową optymalizacje obciążenia punktu.|
|[/Qspectre](qspectre.md)|Włącz środki zaradcze dla CVE 2017-5753 dla klasy Spectre ataków.|
|[/Qvec-report](qvec-report-auto-vectorizer-reporting-level.md)|Włącza raportowanie poziomy vectorization automatycznego.|
|[/RTC](rtc-run-time-error-checks.md)|Włącza sprawdzanie błędów czasu wykonywania.|
|[/volatile](volatile-volatile-keyword-interpretation.md)|Wybiera interpretacji volatile — słowo kluczowe.|

### <a name="output-files"></a>Pliki wyjściowe

|Opcja|Cel|
|------------|-------------|
|[/doc](doc-process-documentation-comments-c-cpp.md)|Przetwarza komentarzy do dokumentacji do pliku XML.|
|[/FA](fa-fa-listing-file.md)|Konfiguruje plik listy zestawu.|
|[/Fa](fa-fa-listing-file.md)|Tworzy plik listy zestawu.|
|[/FD](fd-program-database-file-name.md)|Zmienia nazwę pliku bazy danych programu.|
|[/Fe](fe-name-exe-file.md)|Zmienia nazwę pliku wykonywalnego.|
|[/Fi](fi-preprocess-output-file-name.md)|Określa nazwę pliku wstępnie przetworzonych danych wyjściowych.|
|[/Fm](fm-name-mapfile.md)|Tworzy plik mapowania.|
|[/FO](fo-object-file-name.md)|Tworzy plik obiektu.|
|[/ FP](fp-name-dot-pch-file.md)|Określa nazwę pliku prekompilowanego nagłówka.|
|[/ FR, /Fr](fr-fr-create-dot-sbr-file.md)|Wygenerowana nazwa plików SBR przeglądarki.|

### <a name="preprocessor"></a>Preprocesor

|Opcja|Cel|
|------------|-------------|
|[/AI](ai-specify-metadata-directories.md)|Określa katalog wyszukiwania można rozpoznać odwołania do pliku przekazany do [#using](../../preprocessor/hash-using-directive-cpp.md) dyrektywy.|
|[/C](c-preserve-comments-during-preprocessing.md)|Zachowanie komentarzy podczas przetwarzania wstępnego.|
|[/D](d-preprocessor-definitions.md)|Określa stałe i makr.|
|[/E](e-preprocess-to-stdout.md)|Kopiuje dane wyjściowe preprocesora do wyjścia standardowego.|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|Kopiuje dane wyjściowe preprocesora do wyjścia standardowego.|
|[/FI](fi-name-forced-include-file.md)|Przetwarza wstępnie dołączanego określonego pliku.|
|[/FU](fu-name-forced-hash-using-file.md)|Wymusza stosowanie nazwy pliku, tak jakby były został przekazany do [#using](../../preprocessor/hash-using-directive-cpp.md) dyrektywy.|
|[/Fx](fx-merge-injected-code.md)|Wprowadzony kod scalenia z plikiem źródłowym.|
|[/I](i-additional-include-directories.md)|Wyszukuje katalog dla plików dołączanych.|
|[/P](p-preprocess-to-a-file.md)|Zapisuje dane wyjściowe preprocesora do pliku.|
|[/U](u-u-undefine-symbols.md)|Usuwa wstępnie zdefiniowanego makra.|
|[/u](u-u-undefine-symbols.md)|Usuwa wszystkie predefiniowane makra.|
|[/X](x-ignore-standard-include-paths.md)|Ignoruje standardowego katalog dołączania.|

### <a name="language"></a>Język

|Opcja|Cel|
|------------|-------------|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|Formant oceny specyfikatora constexpr w czasie kompilacji.|
|[/ OpenMP](openmp-enable-openmp-2-0-support.md)|Umożliwia [#pragma omp](../../preprocessor/omp.md) w kodzie źródłowym.|
|[/vd](vd-disable-construction-displacements.md)|Włącza lub wyłącza ukryte `vtordisp` klasy elementów członkowskich.|
|[/vmb](vmb-vmg-representation-method.md)|Używa najlepiej podstawowej dla wskaźników do elementów członkowskich.|
|[/vmg](vmb-vmg-representation-method.md)|Używa pełnych odpisy dla wskaźników do elementów członkowskich.|
|[/vmm](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje dziedziczenie wielokrotne.|
|[/vms](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje pojedyncze dziedziczenie.|
|[/vmv](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje wirtualnego dziedziczenia.|
|[/Z7](z7-zi-zi-debug-information-format.md)|Generuje C 7.0 zgodnego informacji o debugowaniu.|
|[/Za](za-ze-disable-language-extensions.md)|Wyłącza rozszerzenia języka.|
|[/Zc](zc-conformance.md)|Określa zachowanie standardowe w obszarze [/Ze](za-ze-disable-language-extensions.md).|
|[/Ze](za-ze-disable-language-extensions.md)|Przestarzałe. Włącza rozszerzenia języka.|
|[/Zf](zf.md)|Poprawia czas generowania w równoległej kompilacji pliku PDB.|
|[/ZI](z7-zi-zi-debug-information-format.md)|Zawiera informacje o debugowaniu w bazie danych programu zgodne z opcją Edytuj i Kontynuuj. (tylko x86)|
|[/Zi](z7-zi-zi-debug-information-format.md)|Generuje pełne informacje debugowania.|
|[/Zl](zl-omit-default-library-name.md)|Usuwa domyślną nazwę biblioteki z pliku .obj.|
|[/ZP](zp-struct-member-alignment.md) *n*|Pakiety struktury elementów członkowskich.|
|[/Zs](zs-syntax-check-only.md)|Sprawdza, czy tylko składni.|
|[/ZW](zw-windows-runtime-compilation.md)|Tworzy plik wyjściowy do uruchamiania na środowiska uruchomieniowego systemu Windows.|

### <a name="linking"></a>Konsolidacja

|Opcja|Cel|
|------------|-------------|
|[/F](f-set-stack-size.md)|Ustawia rozmiar stosu.|
|[/LD](md-mt-ld-use-run-time-library.md)|Tworzy bibliotekę DLL.|
|[/LDd](md-mt-ld-use-run-time-library.md)|Tworzy bibliotekę DLL debugowania.|
|[/link](link-pass-options-to-linker.md)|Przekazuje określona opcja łącza.|
|[/LN](ln-create-msil-module.md)|Tworzy moduł MSIL.|
|[/MD](md-mt-ld-use-run-time-library.md)|Kompiluje, aby utworzyć wielowątkowe biblioteki DLL przy użyciu MSVCRT.lib.|
|[/MDd](md-mt-ld-use-run-time-library.md)|Kompiluje się do tworzenia debugowania wielowątkowe biblioteki DLL, za pomocą MSVCRTD.lib.|
|[/MT](md-mt-ld-use-run-time-library.md)|Kompiluje, aby utworzyć wielowątkowe plik wykonywalny przy użyciu LIBCMT.lib.|
|[/ MTd](md-mt-ld-use-run-time-library.md)|Kompiluje, aby utworzyć wielowątkowe plik wykonywalny debugowania, za pomocą biblioteki LIBCMTD.lib.|

### <a name="miscellaneous"></a>Różne

|Opcja|Cel|
|------------|-------------|
|[/?](help-compiler-command-line-help.md)|Wyświetla listę opcji kompilatora.|
|[@](at-specify-a-compiler-response-file.md)|Określa plik odpowiedzi.|
|[/ analyze](analyze-code-analysis.md)|Umożliwia analizy kodu.|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|Zwiększa liczbę adresowanego sekcji w pliku .obj.|
|[/c](c-compile-without-linking.md)|Kompiluje bez konsolidacji.|
|[/cgthreads](cgthreads-code-generation-threads.md)|Określa liczbę wątków cl.exe do użycia na potrzeby optymalizacji i generowania kodu.|
|[/errorReport](errorreport-report-internal-compiler-errors.md)|Umożliwia podanie wewnętrznych kompilatora informacje o błędzie (ICE) bezpośrednio do zespołu Visual C++.|
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|Wyświetla pełną ścieżkę diagnostyczny przekazano cl.exe plików kodu źródłowego.|
|[/FS](fs-force-synchronous-pdb-writes.md)|Wymusza zapisuje do pliku programu (PDB) bazy danych za pośrednictwem MSPDBSRV szeregowanie. WYWOŁANIE PLIKU EXE.|
|[/H](h-restrict-length-of-external-names.md)|Przestarzałe. Ogranicza długość nazw zewnętrznych (publicznych).|
|[/HELP](help-compiler-command-line-help.md)|Wyświetla listę opcji kompilatora.|
|[/J](j-default-char-type-is-unsigned.md)|Zmienia domyślny `char` typu.|
|[/kernel](kernel-create-kernel-mode-binary.md)|Kompilatorze i konsolidatorze spowoduje utworzenie pliku binarnego, który może zostać wykonany jądra systemu Windows.|
|[/MP](mp-build-with-multiple-processes.md)|Tworzy jednocześnie wiele plików źródłowych.|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|Pomija wyświetlanie banera logowania jednokrotnego.|
|[/ SDL](sdl-enable-additional-security-checks.md)|Włącza dodatkowe funkcje zabezpieczeń i ostrzeżenia.|
|[/ showincludes](showincludes-list-include-files.md)|Wyświetla listę wszystkich pliki dołączane podczas kompilacji.|
|[/Tc](tc-tp-tc-tp-specify-source-file-type.md)|Określa plik źródłowy C.|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|Określa, że wszystkie pliki źródłowe pakietu to C.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Określa plik źródłowy języka C++.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Określa, że wszystkie pliki źródłowe C++.|
|[/V](v-version-number.md)|Przestarzałe. Ustawia ciąg wersji.|
|[/w](compiler-option-warning-level.md)|Wyłącza wszystkie ostrzeżenia.|
|[/W0, /W1, /W2, /W3, /W4](compiler-option-warning-level.md)|Zestawy danych wyjściowych poziom ostrzeżeń.|
|[/w1, /w2, /w3, /w4](compiler-option-warning-level.md)|Ustawia poziom ostrzeżenia określonego ostrzeżenia.|
|[/Wall](compiler-option-warning-level.md)|Włącza wszystkie ostrzeżenia, w tym ostrzeżenia, które są domyślnie wyłączone.|
|[/WD](compiler-option-warning-level.md)|Wyłącza określony ostrzeżenie.|
|[/we](compiler-option-warning-level.md)|Traktuje określony ostrzeżenie jako błąd.|
|[/WL](wl-enable-one-line-diagnostics.md)|Umożliwia diagnostykę dla błędów i ostrzeżeń podczas kompilowania kodu źródłowego języka C++ z wiersza polecenia.|
|[/WO](compiler-option-warning-level.md)|Wyświetla określony ostrzeżenie tylko raz.|
|[/Wv](compiler-option-warning-level.md)|Wyłącza ostrzeżenia wprowadzone przy użyciu nowszej wersji kompilatora.|
|[/WX](compiler-option-warning-level.md)|Traktuje ostrzeżenia jako błędy.|
|[/Yc](yc-create-precompiled-header-file.md)|Utwórz. Plik PCH.|
|[/YD](yd-place-debug-information-in-object-file.md)|Przestarzałe. Miejsca ukończyć informacji o debugowaniu we wszystkich plikach obiektu. Użyj [/zi](z7-zi-zi-debug-information-format.md) zamiast tego.|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|Injects Odnośnik PCH podczas tworzenia biblioteki debugowania.|
|[/Yu](yu-use-precompiled-header-file.md)|Używa prekompilowanego pliku nagłówkowego podczas kompilacji.|
|[/Y-](y-ignore-precompiled-header-options.md)|Ignoruje wszystkie inne opcje kompilatora prekompilowanego nagłówka w bieżącej kompilacji.|
|[/Zm](zm-specify-precompiled-header-memory-allocation-limit.md)|Określa limit alokacji pamięci prekompilowanego nagłówka.|
|[/await](await-enable-coroutine-support.md)|Włącz rozszerzenia koprocedurach (funkcji wznawialnych).|
|[/ Source-Charset](source-charset-set-source-character-set.md)|Ustaw zestaw znaków źródła.|
|[/ Execution-Charset](execution-charset-set-execution-character-set.md)|Zestaw znaków wykonania zestawu.|
|[/utf-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|Ustawia zestaw znaków źródła i wykonania na UTF-8.|
|[/validate-charset](validate-charset-validate-for-compatible-characters.md)|Sprawdź poprawność plików UTF-8 tylko zgodne znaków.|
|[/Diagnostics](diagnostics-compiler-diagnostic-options.md)|Określa format komunikaty diagnostyczne.|
|[/ ograniczająca-](permissive-standards-conformance.md)|Ustaw tryb standardowy zgodność.|
|[/STD](std-specify-language-standard-version.md)|Selektor zgodność wersji standard C++.|

### <a name="deprecated-and-removed-compiler-options"></a>Opcje kompilatora przestarzałe i usunięte

|Opcja|Cel|
|------------|-------------|
|[/CLR:noAssembly](clr-common-language-runtime-compilation.md)|Przestarzałe. Użyj [/LN (Utwórz moduł MSIL)](ln-create-msil-module.md) zamiast tego.|
|[/FR](fr-fr-create-dot-sbr-file.md)|Przestarzałe. Tworzy plik informacji przeglądania bez zmiennych lokalnych.|
|[/Ge](ge-enable-stack-probes.md)|Przestarzałe. Aktywuje sondy stosu. Na domyślnie.|
|[/GX](gx-enable-exception-handling.md)|Przestarzałe. Włącza obsługę synchronicznych wyjątku. Użyj [/EH](eh-exception-handling-model.md) zamiast tego.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Przestarzałe. Umożliwia szybkie sprawdzenie. Użyj [rtc1](rtc-run-time-error-checks.md) zamiast tego.|
|[/H](h-restrict-length-of-external-names.md)|Przestarzałe. Ogranicza długość nazw zewnętrznych (publicznych).|
|[/Og](og-global-optimizations.md)|Przestarzałe. Używa optymalizacje globalne.|
|[QIfist](qifist-suppress-ftol.md)|Przestarzałe. Raz używany do określenia sposobu konwertować z typu zmiennoprzecinkowego na typ całkowity.|
|[/V](v-version-number.md)|Przestarzałe. Ustawia ciąg wersji pliku .obj.|
|[/Wp64](wp64-detect-64-bit-portability-issues.md)|Nieaktualne. Wykrywa problemów związanych z przenośnością 64-bitowych.|
|[/YD](yd-place-debug-information-in-object-file.md)|Przestarzałe. Miejsca ukończyć informacji o debugowaniu we wszystkich plikach obiektu. Użyj [/zi](z7-zi-zi-debug-information-format.md) zamiast tego.|
|[/Zc:forScope-](zc-forscope-force-conformance-in-for-loop-scope.md)|Przestarzałe. Wyłącza zgodność w zakresie pętli for.|
|[/Ze](za-ze-disable-language-extensions.md)|Przestarzałe. Włącza rozszerzenia języka.|
|[/Zg](zg-generate-function-prototypes.md)|Usunięte w programie Visual C++ 2015. Generuje prototypy funkcji.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja kompilacji w języku C/C++](c-cpp-building-reference.md)<br/>
[Opcje kompilatora](compiler-options.md)<br/>
[Ustawianie opcji kompilatora](setting-compiler-options.md)<br/>
