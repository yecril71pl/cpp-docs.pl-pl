---
title: Opcje kompilatora w rozbiciu na kategorie
ms.date: 08/08/2019
helpviewer_keywords:
- compiler options, C++
ms.assetid: c4750dcf-dba0-4229-99b6-45cdecc11729
ms.openlocfilehash: bfc9bb17100a3ee5c662062963c71ee532487239
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273718"
---
# <a name="compiler-options-listed-by-category"></a>Opcje kompilatora w rozbiciu na kategorie

Ten artykuł zawiera listę kategorii opcji kompilatora. Aby zapoznać się z listą alfabetyczną, zobacz [Opcje kompilatora w porządku alfabetycznym](compiler-options-listed-alphabetically.md).

## <a name="optimization"></a>optymalizacja

|Opcja|Cel|
|------------|-------------|
|[/O1](o1-o2-minimize-size-maximize-speed.md)|Tworzy mały kod.|
|[/O2](o1-o2-minimize-size-maximize-speed.md)|Tworzy szybki kod.|
|[/Ob](ob-inline-function-expansion.md)|Steruje rozwinięciem w tekście.|
|[/Od](od-disable-debug.md)|Wyłącza optymalizację.|
|[/Og](og-global-optimizations.md)|Przestarzałe. Używa globalnych optymalizacji.|
|[/Oi](oi-generate-intrinsic-functions.md)|Generuje funkcje wewnętrzne.|
|[/OS](os-ot-favor-small-code-favor-fast-code.md)|Preferuje mały kod.|
|[/OT](os-ot-favor-small-code-favor-fast-code.md)|Preferuje szybki kod.|
|[/Ox](ox-full-optimization.md)|Podzbiór elementu/O2, który nie zawiera/GF lub/Gy.|
|[/Oy](oy-frame-pointer-omission.md)|Pomija wskaźnik ramki. (tylko x86)|
|[/favor](favor-optimize-for-architecture-specifics.md)|Tworzy kod, który jest zoptymalizowany pod kątem określonej architektury lub dla różnych architektur.|

## <a name="code-generation"></a>Generowanie kodu

|Opcja|Cel|
|------------|-------------|
|[/Arch](arch-x86.md)|Użyj instrukcji SSE lub SSE2 w przypadku generowania kodu. (tylko x86)|
|[/clr](clr-common-language-runtime-compilation.md)|Tworzy plik wyjściowy do uruchomienia w środowisku uruchomieniowym języka wspólnego.|
|[/EH](eh-exception-handling-model.md)|Określa model obsługi wyjątków.|
|[/FP](fp-specify-floating-point-behavior.md)|Określa zachowanie zmiennoprzecinkowe.|
|[/GA](ga-optimize-for-windows-application.md)|Optymalizuje dla aplikacji systemu Windows.|
|[/Gd](gd-gr-gv-gz-calling-convention.md)|Używa konwencji `__cdecl` wywoływania. (tylko x86)|
|[/Ge](ge-enable-stack-probes.md)|Przestarzałe. Aktywuje sondy stosu.|
|[/GF](gf-eliminate-duplicate-strings.md)|Włącza buforowanie ciągów.|
|[/Gh](gh-enable-penter-hook-function.md)|Wywołuje funkcję `_penter`haka.|
|[/GH](gh-enable-pexit-hook-function.md)|Wywołuje funkcję `_pexit`haka.|
|[/GL](gl-whole-program-optimization.md)|Włącza optymalizację całego programu.|
|[/Gm](gm-enable-minimal-rebuild.md)|Przestarzałe. Włącza minimalną ponowną kompilację.|
|[/GR](gr-enable-run-time-type-information.md)|Włącza informacje o typach w czasie wykonywania (RTTI).|
|[/Gr](gd-gr-gv-gz-calling-convention.md)|Używa konwencji `__fastcall` wywoływania. (tylko x86)|
|[/GS](gs-buffer-security-check.md)|Sprawdza zabezpieczenia bufora.|
|[/GS](gs-control-stack-checking-calls.md)|Kontroluje sondy stosu.|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|Obsługuje zabezpieczenia włókna danych przydzielone przy użyciu statycznego magazynu wątków lokalnych.|
|[/Guard: CF](guard-enable-control-flow-guard.md)|Dodaje testy zabezpieczeń funkcji Ochrona przepływu sterowania.|
|[/Gv](gd-gr-gv-gz-calling-convention.md)|Używa konwencji `__vectorcall` wywoływania. (tylko x86 i x64)|
|[/Gw](gw-optimize-global-data.md)|Włącza optymalizację danych globalnych całego programu.|
|[/GX](gx-enable-exception-handling.md)|Przestarzałe. Włącza synchroniczną obsługę wyjątków. Zamiast tego użyj [/EH](eh-exception-handling-model.md) .|
|[/Gy](gy-enable-function-level-linking.md)|Włącza łączenie na poziomie funkcji.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Przestarzałe. Umożliwia szybkie sprawdzanie. (Analogicznie jak [/RTC1](rtc-run-time-error-checks.md))|
|[/Gz](gd-gr-gv-gz-calling-convention.md)|Używa konwencji `__stdcall` wywoływania. (tylko x86)|
|[/homeparams](homeparams-copy-register-parameters-to-stack.md)|Wymusza, aby parametry przesyłane w rejestrach były zapisywane do ich lokalizacji na stosie przy wejściu do funkcji. Ta opcja kompilatora jest tylko dla kompilatorów x64 (kompilacja natywna i krzyżowa).|
|[/hotpatch](hotpatch-create-hotpatchable-image.md)|Tworzy obraz możliwy do poprawiania.|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|Generuje szybki transcendentals.|
|[/QIfist](qifist-suppress-ftol.md)|Przestarzałe. Pomija wywołanie funkcji `_ftol` pomocnika, gdy wymagana jest konwersja z typu zmiennoprzecinkowego na typ całkowity. (tylko x86)|
|[/Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|Usuwa `fwait` polecenia wewnątrz `try` bloków.|
|[/Qpar](qpar-auto-parallelizer.md)|Włącza automatyczne przetwarzanie równoległe pętli.|
|[/Qpar-report](qpar-report-auto-parallelizer-reporting-level.md)|Włącza poziomy raportowania dla automatycznej przetwarzanie równoległe.|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|Używa instrukcji przenoszenia liczb całkowitych dla wartości zmiennoprzecinkowych i wyłącza pewne optymalizacje ładowania zmiennoprzecinkowego.|
|[/Qspectre](qspectre.md)|Włącz środki zaradcze dla CVE 2017-5753 dla klasy ataków Spectre.|
|[/Qvec-report](qvec-report-auto-vectorizer-reporting-level.md)|Włącza poziomy raportowania dla automatycznej wektoryzacji.|
|[/RTC](rtc-run-time-error-checks.md)|Włącza sprawdzanie błędów czasu wykonywania.|
|[/volatile](volatile-volatile-keyword-interpretation.md)|Wybiera sposób interpretowania nietrwałego słowa kluczowego.|

## <a name="output-files"></a>Pliki wyjściowe

|Opcja|Cel|
|------------|-------------|
|[/doc](doc-process-documentation-comments-c-cpp.md)|Przetwarza komentarze dokumentacji do pliku XML.|
|[/FA](fa-fa-listing-file.md)|Konfiguruje plik listy zestawu.|
|[/Fa](fa-fa-listing-file.md)|Tworzy plik listy zestawu.|
|[/FD](fd-program-database-file-name.md)|Zmienia nazwę pliku bazy danych programu.|
|[/Fe](fe-name-exe-file.md)|Zmienia nazwę pliku wykonywalnego.|
|[/Fi](fi-preprocess-output-file-name.md)|Określa nazwę wstępnie przetworzonego pliku wyjściowego.|
|[/Fm](fm-name-mapfile.md)|Tworzy element mapfile.|
|[/FO](fo-object-file-name.md)|Tworzy plik obiektu.|
|[/FP](fp-name-dot-pch-file.md)|Określa nazwę prekompilowanego pliku nagłówkowego.|
|[/FR,/fr](fr-fr-create-dot-sbr-file.md)|Nazwa wygenerowana przez pliki przeglądarki SBR.|

## <a name="preprocessor"></a>Preprocesor

|Opcja|Cel|
|------------|-------------|
|[/AI](ai-specify-metadata-directories.md)|Określa katalog do przeszukania w celu rozpoznania odwołań do plików przesłanych do dyrektywy [#using](../../preprocessor/hash-using-directive-cpp.md) .|
|[/C](c-preserve-comments-during-preprocessing.md)|Zachowuje komentarze podczas przetwarzania wstępnego.|
|[/D](d-preprocessor-definitions.md)|Definiuje stałe i makra.|
|[/E](e-preprocess-to-stdout.md)|Kopiuje dane wyjściowe preprocesora do wyjścia standardowego.|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|Kopiuje dane wyjściowe preprocesora do wyjścia standardowego.|
|[/FI](fi-name-forced-include-file.md)|Przetwarza wstępnie określony plik dołączany.|
|[/FU](fu-name-forced-hash-using-file.md)|Wymusza użycie nazwy pliku, tak jakby była przenoszona do dyrektywy [#using](../../preprocessor/hash-using-directive-cpp.md) .|
|[/Fx](fx-merge-injected-code.md)|Scala wprowadzony kod z plikiem źródłowym.|
|[/I](i-additional-include-directories.md)|Wyszukuje pliki dołączane w katalogu.|
|[/P](p-preprocess-to-a-file.md)|Zapisuje dane wyjściowe preprocesora do pliku.|
|[/U](u-u-undefine-symbols.md)|Usuwa wstępnie zdefiniowane makro.|
|[/u](u-u-undefine-symbols.md)|Usuwa wszystkie wstępnie zdefiniowane makra.|
|[/X](x-ignore-standard-include-paths.md)|Ignoruje standardowy katalog dołączania.|

## <a name="language"></a>Język

|Opcja|Cel|
|------------|-------------|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|Kontrolowanie wartości wyrażenia constexpr w czasie kompilacji.|
|[/OpenMP](openmp-enable-openmp-2-0-support.md)|Włącza [#pragma OMP](../../preprocessor/omp.md) w kodzie źródłowym.|
|[/vd](vd-disable-construction-displacements.md)|Pomija lub włącza ukryte `vtordisp` elementy członkowskie klasy.|
|[/vmb](vmb-vmg-representation-method.md)|Używa najlepszych podstaw dla wskaźników do elementów członkowskich.|
|[/vmg](vmb-vmg-representation-method.md)|Używa pełnej ogólnej wskaźników do elementów członkowskich.|
|[/vmm](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje wielokrotne dziedziczenie.|
|[/vms](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje pojedyncze dziedziczenie.|
|[/vmv](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje wirtualne dziedziczenie.|
|[/Z7](z7-zi-zi-debug-information-format.md)|Generuje informacje o debugowaniu zgodne z C 7,0.|
|[/Za](za-ze-disable-language-extensions.md)|Wyłącza rozszerzenia języka c89.|
|[/Zc](zc-conformance.md)|Określa standardowe zachowanie w obszarze [/ze](za-ze-disable-language-extensions.md).|
|[/Ze](za-ze-disable-language-extensions.md)|Przestarzałe. Włącza rozszerzenia języka c89.|
|[/Zf](zf.md)|Skraca czas generowania pliku PDB w kompilacjach równoległych.|
|[/ZI](z7-zi-zi-debug-information-format.md)|Zawiera informacje o debugowaniu w programie bazy danych programu zgodne z funkcją Edytuj i Kontynuuj. (tylko x86)|
|[/Zi](z7-zi-zi-debug-information-format.md)|Generuje pełne informacje o debugowaniu.|
|[/Zl](zl-omit-default-library-name.md)|Usuwa domyślną nazwę biblioteki z pliku. obj.|
|[/ZP](zp-struct-member-alignment.md) *n*|Elementy członkowskie struktury pakietów.|
|[/Zs](zs-syntax-check-only.md)|Sprawdza tylko składnię.|
|[/ZW](zw-windows-runtime-compilation.md)|Tworzy plik wyjściowy do uruchomienia na środowisko wykonawcze systemu Windows.|

## <a name="linking"></a>Konsolidacja

|Opcja|Cel|
|------------|-------------|
|[/F](f-set-stack-size.md)|Ustawia rozmiar stosu.|
|[/LD](md-mt-ld-use-run-time-library.md)|Tworzy bibliotekę dołączaną dynamicznie.|
|[/LDd](md-mt-ld-use-run-time-library.md)|Tworzy bibliotekę dołączaną dynamicznie do debugowania.|
|[/link](link-pass-options-to-linker.md)|Przekazuje określoną opcję do LINKu.|
|[/LN](ln-create-msil-module.md)|Tworzy moduł MSIL.|
|[/MD](md-mt-ld-use-run-time-library.md)|Kompiluje, aby utworzyć wielowątkową bibliotekę DLL, za pomocą MSVCRT. lib.|
|[/MDd](md-mt-ld-use-run-time-library.md)|Kompiluje, aby utworzyć wielowątkową bibliotekę DLL debugowania za pomocą MSVCRTD. lib.|
|[/MT](md-mt-ld-use-run-time-library.md)|Kompiluje, aby utworzyć wielowątkowy plik wykonywalny przy użyciu LIBCMT. lib.|
|[/MTd](md-mt-ld-use-run-time-library.md)|Kompiluje, aby utworzyć plik wykonywalny wielowątkowego debugowania za pomocą LIBCMTD. lib.|

## <a name="miscellaneous"></a>Różne

|Opcja|Cel|
|------------|-------------|
|[/?](help-compiler-command-line-help.md)|Wyświetla listę opcji kompilatora.|
|[@](at-specify-a-compiler-response-file.md)|Określa plik odpowiedzi.|
|[/analyze](analyze-code-analysis.md)|Włącza analizę kodu.|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|Zwiększa liczbę sekcji adresowanych w pliku. obj.|
|[/c](c-compile-without-linking.md)|Kompiluje bez konsolidacji.|
|[/cgthreads](cgthreads-code-generation-threads.md)|Określa liczbę wątków CL. exe do użycia na potrzeby optymalizacji i generowania kodu.|
|[/errorReport](errorreport-report-internal-compiler-errors.md)|Umożliwia dostarczenie informacji o wewnętrznym błędzie kompilatora (lodem) bezpośrednio do zespołu firmy C++ Microsoft.|
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|Wyświetla pełną ścieżkę do plików kodu źródłowego przekazaną do CL. exe w tekście diagnostycznym.|
|[/FS](fs-force-synchronous-pdb-writes.md)|Wymusza zapis do pliku bazy danych programu (PDB) do serializacji za pomocą MSPDBSRV. EXE.|
|[/H](h-restrict-length-of-external-names.md)|Przestarzałe. Ogranicza długość nazw zewnętrznych (publicznych).|
|[/HELP](help-compiler-command-line-help.md)|Wyświetla listę opcji kompilatora.|
|[/J](j-default-char-type-is-unsigned.md)|Zmienia typ domyślny `char` .|
|[/JMC](jmc.md)|Obsługuje natywne C++ debugowanie tylko mój kod.|
|[/kernel](kernel-create-kernel-mode-binary.md)|Kompilator i konsolidator utworzy plik binarny, który może być wykonywany w jądrze systemu Windows.|
|[/MP](mp-build-with-multiple-processes.md)|Kompiluje jednocześnie wiele plików źródłowych.|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|Pomija wyświetlanie transparentu logowania.|
|[/SDL](sdl-enable-additional-security-checks.md)|Umożliwia korzystanie z dodatkowych funkcji zabezpieczeń i ostrzeżeń.|
|[/showIncludes](showincludes-list-include-files.md)|Wyświetla listę wszystkich plików dołączanych podczas kompilacji.|
|[/Tc](tc-tp-tc-tp-specify-source-file-type.md)|Określa plik źródłowy w języku C.|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|Określa wszystkie pliki źródłowe to C.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Określa plik C++ źródłowy.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Określa wszystkie pliki źródłowe C++.|
|[/V](v-version-number.md)|Przestarzałe. Ustawia ciąg wersji.|
|[/w](compiler-option-warning-level.md)|Wyłącza wszystkie ostrzeżenia.|
|[/W0, /W1, /W2, /W3, /W4](compiler-option-warning-level.md)|Ustawia poziom ostrzeżeń wyjściowych.|
|[/w1, /w2, /w3, /w4](compiler-option-warning-level.md)|Ustawia poziom ostrzeżeń dla określonego ostrzeżenia.|
|[/Wall](compiler-option-warning-level.md)|Włącza wszystkie ostrzeżenia, w tym ostrzeżenia, które są domyślnie wyłączone.|
|[/WD](compiler-option-warning-level.md)|Wyłącza określone ostrzeżenie.|
|[/we](compiler-option-warning-level.md)|Traktuje określone ostrzeżenie jako błąd.|
|[/WL](wl-enable-one-line-diagnostics.md)|Włącza diagnostykę jednowierszową dla komunikatów o błędach i C++ ostrzeżeniach podczas kompilowania kodu źródłowego z wiersza polecenia.|
|[/wo](compiler-option-warning-level.md)|Wyświetla określone ostrzeżenie tylko raz.|
|[/Wv](compiler-option-warning-level.md)|Wyłącza ostrzeżenia wprowadzone przez nowsze wersje kompilatora.|
|[/WX](compiler-option-warning-level.md)|Traktuje ostrzeżenia jako błędy.|
|[/YC](yc-create-precompiled-header-file.md)|Create. Plik PCH.|
|[/YD](yd-place-debug-information-in-object-file.md)|Przestarzałe. Umieszcza pełne informacje o debugowaniu we wszystkich plikach obiektów. Zamiast tego użyj [/Zi](z7-zi-zi-debug-information-format.md) .|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|Wstawia odwołanie do PCH podczas tworzenia biblioteki debugowania.|
|[/Yu](yu-use-precompiled-header-file.md)|Używa prekompilowanego pliku nagłówkowego podczas kompilowania.|
|[/Y-](y-ignore-precompiled-header-options.md)|Ignoruje wszystkie inne opcje kompilatora prekompilowanego nagłówka w bieżącej kompilacji.|
|[/Zm](zm-specify-precompiled-header-memory-allocation-limit.md)|Określa limit alokacji pamięci prekompilowanego nagłówka.|
|[/await](await-enable-coroutine-support.md)|Włącz rozszerzenia procedur wspólnych (możliwością wznowienia Functions).|
|[określono element/source-charset](source-charset-set-source-character-set.md)|Ustaw zestaw znaków źródła.|
|[/Execution-charset](execution-charset-set-execution-character-set.md)|Ustaw zestaw znaków wykonania.|
|[/utf-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|Ustaw zestaw znaków źródła i wykonania na UTF-8.|
|[/validate-charset](validate-charset-validate-for-compatible-characters.md)|Weryfikowanie plików UTF-8 tylko pod kątem zgodnych znaków.|
|[/Diagnostics](diagnostics-compiler-diagnostic-options.md)|Kontroluje Format komunikatów diagnostycznych.|
|[/permissive-](permissive-standards-conformance.md)|Ustaw tryb zgodności ze standardem.|
|[/STD](std-specify-language-standard-version.md)|C++Selektor zgodności wersji standardowej.|

## <a name="experimental-options"></a>Opcje eksperymentalne

Opcje eksperymentalne mogą być obsługiwane tylko przez niektóre wersje kompilatora i mogą zachowywać się inaczej w różnych wersjach kompilatora. Często Najlepsza lub tylko dokumentacja opcji eksperymentalnych znajduje się w [blogu zespołu firmy Microsoft C++ ](https://devblogs.microsoft.com/cppblog/).

|Opcja|Cel|
|------------|-------------|
|[/Experimental: moduł](experimental-module.md)|Umożliwia obsługę modułów eksperymentalnych.|
|[/Experimental: preprocesor](experimental-preprocessor.md)|Włącza eksperymentalną obsługę preprocesora.|

## <a name="deprecated-and-removed-compiler-options"></a>Przestarzałe i usunięte opcje kompilatora

|Opcja|Cel|
|------------|-------------|
|[/CLR: noAssembly](clr-common-language-runtime-compilation.md)|Przestarzałe. Zamiast tego użyj [/ln (Utwórz moduł MSIL)](ln-create-msil-module.md) .|
|[/Fr](fr-fr-create-dot-sbr-file.md)|Przestarzałe. Tworzy plik informacji o przeglądaniu bez zmiennych lokalnych.|
|[/Ge](ge-enable-stack-probes.md)|Przestarzałe. Aktywuje sondy stosu. Domyślnie włączone.|
|[/Gm](gm-enable-minimal-rebuild.md)|Przestarzałe. Włącza minimalną ponowną kompilację.|
|[/GX](gx-enable-exception-handling.md)|Przestarzałe. Włącza synchroniczną obsługę wyjątków. Zamiast tego użyj [/EH](eh-exception-handling-model.md) .|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Przestarzałe. Umożliwia szybkie sprawdzanie. Zamiast tego użyj [/RTC1](rtc-run-time-error-checks.md) .|
|[/H](h-restrict-length-of-external-names.md)|Przestarzałe. Ogranicza długość nazw zewnętrznych (publicznych).|
|[/Og](og-global-optimizations.md)|Przestarzałe. Używa globalnych optymalizacji.|
|[/QIfist](qifist-suppress-ftol.md)|Przestarzałe. Po użyciu, aby określić sposób konwersji z typu zmiennoprzecinkowego na typ całkowity.|
|[/V](v-version-number.md)|Przestarzałe. Ustawia ciąg wersji pliku. obj.|
|[/Wp64](wp64-detect-64-bit-portability-issues.md)|Nieaktualne. Wykrywa 64-bitowe problemy z przenośnością.|
|[/YD](yd-place-debug-information-in-object-file.md)|Przestarzałe. Umieszcza pełne informacje o debugowaniu we wszystkich plikach obiektów. Zamiast tego użyj [/Zi](z7-zi-zi-debug-information-format.md) .|
|[/Zc:forScope-](zc-forscope-force-conformance-in-for-loop-scope.md)|Przestarzałe. Wyłącza zgodność w zakresie pętli for.|
|[/Ze](za-ze-disable-language-extensions.md)|Przestarzałe. Włącza rozszerzenia językowe.|
|[/Zg](zg-generate-function-prototypes.md)|Usunięto w programie Visual Studio 2015. Generuje prototypy funkcji.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja kompilacji w języku C/C++](c-cpp-building-reference.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
