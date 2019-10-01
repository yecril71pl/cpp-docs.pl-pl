---
title: Opcje kompilatora w porządku alfabetycznym
ms.date: 08/08/2019
helpviewer_keywords:
- compiler options, C++
ms.openlocfilehash: 39dd11245ef88d1d59d3eda8cbeaa5fc4494b9a8
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685322"
---
# <a name="compiler-options-listed-alphabetically"></a>Opcje kompilatora w porządku alfabetycznym

Poniżej znajduje się kompleksowa Alfabetyczna lista opcji kompilatora. Aby uzyskać listę kategorii, zapoznaj się z [opcjami kompilatora wymienionymi na liście według kategorii](compiler-options-listed-by-category.md).

|Opcja|Przeznaczenie|
|------------|-------------|
|[@](at-specify-a-compiler-response-file.md)|Określa plik odpowiedzi.|
|[/?](help-compiler-command-line-help.md)|Wyświetla listę opcji kompilatora.|
|[/AI](ai-specify-metadata-directories.md)|Określa katalog do przeszukania w celu rozpoznania odwołań do plików przesłanych do dyrektywy [#using](../../preprocessor/hash-using-directive-cpp.md) .|
|[/analyze](analyze-code-analysis.md)|Włącz analizę kodu.|
|[/Arch](arch-minimum-cpu-architecture.md)|Określa architekturę generowania kodu.|
|[/await](await-enable-coroutine-support.md)|Włącz rozszerzenia procedur wspólnych (możliwością wznowienia Functions).|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|Zwiększa liczbę sekcji adresowanych w pliku. obj.|
|[/C](c-preserve-comments-during-preprocessing.md)|Zachowuje komentarze podczas przetwarzania wstępnego.|
|[/c](c-compile-without-linking.md)|Kompiluje bez konsolidacji.|
|[/CGTHREADS](cgthreads-code-generation-threads.md)|Określa liczbę wątków CL. exe do użycia na potrzeby optymalizacji i generowania kodu.|
|[/CLR](clr-common-language-runtime-compilation.md)|Tworzy plik wyjściowy do uruchomienia w środowisku uruchomieniowym języka wspólnego.|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|Kontrolowanie wartości wyrażenia constexpr w czasie kompilacji.|
|[Parametr](d-preprocessor-definitions.md)|Definiuje stałe i makra.|
|[/Diagnostics](diagnostics-compiler-diagnostic-options.md)|Kontroluje Format komunikatów diagnostycznych.|
|[/doc](doc-process-documentation-comments-c-cpp.md)|Przetwarzaj komentarze dokumentacji do pliku XML.|
|[/E](e-preprocess-to-stdout.md)|Kopiuje dane wyjściowe preprocesora do wyjścia standardowego.|
|[/EH](eh-exception-handling-model.md)|Określa model obsługi wyjątków.|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|Kopiuje dane wyjściowe preprocesora do wyjścia standardowego.|
|[/errorReport](errorreport-report-internal-compiler-errors.md)|Umożliwia dostarczenie informacji o wewnętrznym błędzie kompilatora (lodem) bezpośrednio do zespołu firmy C++ Microsoft.|
|[/Execution-charset](execution-charset-set-execution-character-set.md)|Ustaw zestaw znaków wykonania.|
|[/Experimental: moduł](experimental-module.md)|Umożliwia obsługę modułów eksperymentalnych.|
|[/Experimental: preprocesor](experimental-preprocessor.md)|Włącza eksperymentalną obsługę preprocesora.|
|[Opcją](f-set-stack-size.md)|Ustawia rozmiar stosu.|
|[/Favor](favor-optimize-for-architecture-specifics.md)|Produkuje kod, który jest zoptymalizowany pod kątem określonej architektury x64 lub dla określonych mikroarchitektur w architekturze AMD64 i Extended Memory 64 Technology (EM64T).|
|[/FA](fa-fa-listing-file.md)|Tworzy plik listy.|
|[/FA](fa-fa-listing-file.md)|Ustawia nazwę pliku listy.|
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|Wyświetl pełną ścieżkę plików kodu źródłowego przekazaną do CL. exe w tekście diagnostycznym.|
|[/FD](fd-program-database-file-name.md)|Zmienia nazwę pliku bazy danych programu.|
|[/Fe](fe-name-exe-file.md)|Zmienia nazwę pliku wykonywalnego.|
|[/FI](fi-name-forced-include-file.md)|Przetwarza wstępnie określony plik dołączany.|
|[/Fi](fi-preprocess-output-file-name.md)|Ustawia nazwę wstępnie przetworzonego pliku wyjściowego.|
|[/FM](fm-name-mapfile.md)|Tworzy plik mapy.|
|[/FO](fo-object-file-name.md)|Tworzy plik obiektu.|
|[/FP](fp-specify-floating-point-behavior.md)|Określ zachowanie zmiennoprzecinkowe.|
|[/FP](fp-name-dot-pch-file.md)|Określa nazwę prekompilowanego pliku nagłówkowego.|
|[/FR](fr-fr-create-dot-sbr-file.md)<br /><br /> [/Fr](fr-fr-create-dot-sbr-file.md)|Generuje pliki przeglądarki. **/Fr** jest przestarzała.|
|[/FS](fs-force-synchronous-pdb-writes.md)|Wymusza zapis do pliku bazy danych programu (PDB) do serializacji za pomocą MSPDBSRV. EXE.|
|[/FU](fu-name-forced-hash-using-file.md)|Wymusza użycie nazwy pliku, tak jakby została przeniesiona do dyrektywy [#using](../../preprocessor/hash-using-directive-cpp.md) .|
|[/FX](fx-merge-injected-code.md)|Scala wprowadzony kod z plikiem źródłowym.|
|[/GA](ga-optimize-for-windows-application.md)|Optymalizuje kod dla aplikacji systemu Windows.|
|[/GD](gd-gr-gv-gz-calling-convention.md)|Używa konwencji wywoływania `__cdecl` (tylko x86).|
|[/GE](ge-enable-stack-probes.md)|Przestarzałe. Aktywuje sondy stosu.|
|[/GF](gf-eliminate-duplicate-strings.md)|Włącza buforowanie ciągów.|
|[/GH](gh-enable-pexit-hook-function.md)|Wywołuje funkcję Hook `_pexit`.|
|[/GH](gh-enable-penter-hook-function.md)|Wywołuje funkcję Hook `_penter`.|
|[/GL](gl-whole-program-optimization.md)|Włącza optymalizację całego programu.|
|[/GM](gm-enable-minimal-rebuild.md)|Przestarzałe. Włącza minimalną ponowną kompilację.|
|[/GR](gr-enable-run-time-type-information.md)|Włącza informacje o typach w czasie wykonywania (RTTI).|
|[/Gr](gd-gr-gv-gz-calling-convention.md)|Używa konwencji wywoływania `__fastcall` (tylko x86).|
|[/GS](gs-buffer-security-check.md)|Bufory kontroli zabezpieczeń.|
|[/GS](gs-control-stack-checking-calls.md)|Kontroluje sondy stosu.|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|Obsługuje zabezpieczenia włókna danych przydzielonych przy użyciu statycznego magazynu wątków lokalnych.|
|[/Guard: CF](guard-enable-control-flow-guard.md)|Dodaje testy zabezpieczeń funkcji Ochrona przepływu sterowania.|
|[/GV](gd-gr-gv-gz-calling-convention.md)|Używa konwencji wywoływania `__vectorcall`. (tylko x86 i x64)|
|[/GW](gw-optimize-global-data.md)|Włącza optymalizację danych globalnych całego programu.|
|[/GX](gx-enable-exception-handling.md)|Przestarzałe. Włącza synchroniczną obsługę wyjątków. Zamiast tego użyj [/EH](eh-exception-handling-model.md) .|
|[/Gy](gy-enable-function-level-linking.md)|Włącza łączenie na poziomie funkcji.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Przestarzałe. Analogicznie jak [/RTC1](rtc-run-time-error-checks.md).|
|[/GZ](gd-gr-gv-gz-calling-convention.md)|Używa konwencji wywoływania `__stdcall` (tylko x86).|
|[/H](h-restrict-length-of-external-names.md)|Przestarzałe. Ogranicza długość nazw zewnętrznych (publicznych).|
|[/HELP](help-compiler-command-line-help.md)|Wyświetla listę opcji kompilatora.|
|[/homeparams](homeparams-copy-register-parameters-to-stack.md)|Wymusza, aby parametry przesyłane w rejestrach były zapisywane do ich lokalizacji na stosie przy wejściu do funkcji. Ta opcja kompilatora jest tylko dla kompilatorów x64 (kompilacja natywna i krzyżowa).|
|[/hotpatch](hotpatch-create-hotpatchable-image.md)|Tworzy obraz z poprawkami na gorąco.|
|[/I](i-additional-include-directories.md)|Wyszukuje pliki dołączane w katalogu.|
|[/J](j-default-char-type-is-unsigned.md)|Zmienia domyślny typ `char`.|
|[/JMC](jmc.md)|Obsługuje natywne C++ debugowanie tylko mój kod.|
|[/Kernel](kernel-create-kernel-mode-binary.md)|Kompilator i konsolidator utworzy plik binarny, który może być wykonywany w jądrze systemu Windows.|
|[/LD](md-mt-ld-use-run-time-library.md)|Tworzy bibliotekę dołączaną dynamicznie.|
|[/LDd](md-mt-ld-use-run-time-library.md)|Tworzy bibliotekę dołączaną dynamicznie do debugowania.|
|[/Link](link-pass-options-to-linker.md)|Przekazuje określoną opcję do LINKu.|
|[/LN](ln-create-msil-module.md)|Tworzy moduł MSIL.|
|[/MD](md-mt-ld-use-run-time-library.md)|Tworzy wielowątkową bibliotekę DLL przy użyciu MSVCRT. lib.|
|[/MDd](md-mt-ld-use-run-time-library.md)|Utworzenie wielowątkowej biblioteki DLL debugowania za pomocą MSVCRTD. lib.|
|[/MP](mp-build-with-multiple-processes.md)|Kompiluje wiele plików źródłowych przy użyciu wielu procesów.|
|[/MT](md-mt-ld-use-run-time-library.md)|Tworzy wielowątkowy plik wykonywalny za pomocą LIBCMT. lib.|
|[/MTd](md-mt-ld-use-run-time-library.md)|Tworzy wielowątkowy plik wykonywalny debugowania za pomocą LIBCMTD. lib.|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|Pomija wyświetlanie transparentu logowania.|
|[/O1](o1-o2-minimize-size-maximize-speed.md)|Tworzy mały kod.|
|[/O2](o1-o2-minimize-size-maximize-speed.md)|Tworzy szybki kod.|
|[/Ob](ob-inline-function-expansion.md)|Steruje rozwinięciem w tekście.|
|[/Od](od-disable-debug.md)|Wyłącza optymalizację.|
|[/Og](og-global-optimizations.md)|Przestarzałe. Używa globalnych optymalizacji.|
|[/Oi](oi-generate-intrinsic-functions.md)|Generuje funkcje wewnętrzne.|
|[/OpenMP](openmp-enable-openmp-2-0-support.md)|Włącza dyrektywę [`#pragma omp`](../../preprocessor/omp.md) w kodzie źródłowym.|
|[/OS](os-ot-favor-small-code-favor-fast-code.md)|Preferuje mały kod.|
|[/OT](os-ot-favor-small-code-favor-fast-code.md)|Preferuje szybki kod.|
|[/OX](ox-full-optimization.md)|Podzbiór elementu/O2, który nie zawiera/GF lub/Gy.|
|[/Oy](oy-frame-pointer-omission.md)|Pomija wskaźnik ramki (tylko x86).|
|[/P](p-preprocess-to-a-file.md)|Zapisuje dane wyjściowe preprocesora do pliku.|
|[/permissive-](permissive-standards-conformance.md)|Ustaw tryb zgodności ze standardem.|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|Generuje szybki transcendentals.|
|[/QIfist](qifist-suppress-ftol.md)|Przestarzałe. Pomija `_ftol`, gdy wymagana jest konwersja typu zmiennoprzecinkowego na typ całkowity (tylko x86).|
|[/Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|Usuwa polecenia `fwait` w blokach `try`.|
|[/Qpar (autoparalelizacji)](qpar-auto-parallelizer.md)|Włącza automatyczne przetwarzanie równoległe pętle, które są oznaczone za pomocą dyrektywy [pętli #pragma ()](../../preprocessor/loop.md) .|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|Używa instrukcji przenoszenia liczb całkowitych dla wartości zmiennoprzecinkowych i wyłącza pewne optymalizacje ładowania zmiennoprzecinkowego.|
|[/Qspectre](qspectre.md)|Określa generowanie kompilatora instrukcji w celu ograniczenia niektórych luk w zabezpieczeniach Spectre Variant 1.|
|[/Qvec-Report (poziom raportowania autowektoryzator)](qvec-report-auto-vectorizer-reporting-level.md)|Włącza poziomy raportowania dla automatycznej wektoryzacji.|
|[/RTC](rtc-run-time-error-checks.md)|Włącza sprawdzanie błędów czasu wykonywania.|
|[/SDL](sdl-enable-additional-security-checks.md)|Umożliwia korzystanie z dodatkowych funkcji zabezpieczeń i ostrzeżeń.|
|[/showIncludes](showincludes-list-include-files.md)|Wyświetla listę plików dołączanych podczas kompilacji.|
|[określono element/source-charset](source-charset-set-source-character-set.md)|Ustaw zestaw znaków źródła.|
|[/STD](std-specify-language-standard-version.md)|C++Selektor zgodności wersji standardowej.|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|Określa plik źródłowy w języku C.|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|Określa wszystkie pliki źródłowe to C.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Określa plik C++ źródłowy.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Określa wszystkie pliki źródłowe C++.|
|[Określ](u-u-undefine-symbols.md)|Usuwa wstępnie zdefiniowane makro.|
|[Określ](u-u-undefine-symbols.md)|Usuwa wszystkie wstępnie zdefiniowane makra.|
|[/UTF-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|Ustaw zestaw znaków źródła i wykonania na UTF-8.|
|[Przełącznika](v-version-number.md)|Przestarzałe. Ustawia ciąg wersji pliku. obj.|
|[/Validate-charset](validate-charset-validate-for-compatible-characters.md)|Weryfikowanie plików UTF-8 tylko pod kątem zgodnych znaków.|
|[/VD](vd-disable-construction-displacements.md)|Pomija lub włącza ukryte elementy członkowskie klasy vtordisp.|
|[/VMB](vmb-vmg-representation-method.md)|Używa najlepszych podstaw dla wskaźników do elementów członkowskich.|
|[/VMG](vmb-vmg-representation-method.md)|Używa pełnej ogólnej wskaźników do elementów członkowskich.|
|[/VMM](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje wielokrotne dziedziczenie.|
|[/VMS](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje pojedyncze dziedziczenie.|
|[/VMV](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje wirtualne dziedziczenie.|
|[/volatile](volatile-volatile-keyword-interpretation.md)|Wybiera sposób interpretowania nietrwałego słowa kluczowego.|
|[/w](compiler-option-warning-level.md)|Wyłącza wszystkie ostrzeżenia.|
|[/W0,/W1,/W2,/W3,/W4](compiler-option-warning-level.md)|Ustawia poziom ostrzeżeń dla danych wyjściowych.|
|[/W1,/W2,/W3,/W4](compiler-option-warning-level.md)|Ustawia poziom ostrzeżeń dla określonego ostrzeżenia.|
|[/Wall](compiler-option-warning-level.md)|Włącza wszystkie ostrzeżenia, w tym ostrzeżenia, które są domyślnie wyłączone.|
|[/WD](compiler-option-warning-level.md)|Wyłącza określone ostrzeżenie.|
|[/we](compiler-option-warning-level.md)|Traktuje określone ostrzeżenie jako błąd.|
|[/WL](wl-enable-one-line-diagnostics.md)|Włącza diagnostykę jednowierszową dla komunikatów o błędach i C++ ostrzeżeniach podczas kompilowania kodu źródłowego z wiersza polecenia.|
|[/wo](compiler-option-warning-level.md)|Wyświetla określone ostrzeżenie tylko raz.|
|[/Wp64](wp64-detect-64-bit-portability-issues.md)|Zbędn. Wykrywa 64-bitowe problemy z przenośnością.|
|[/WV](compiler-option-warning-level.md)|Nie zawiera żadnych ostrzeżeń wprowadzonych po określonej wersji kompilatora.|
|[/WX](compiler-option-warning-level.md)|Traktuje wszystkie ostrzeżenia jako błędy.|
|[/X](x-ignore-standard-include-paths.md)|Ignoruje standardowy katalog dołączania.|
|[/Y-](y-ignore-precompiled-header-options.md)|Ignoruje wszystkie inne opcje kompilatora prekompilowanego nagłówka w bieżącej kompilacji.|
|[/YC](yc-create-precompiled-header-file.md)|Tworzy prekompilowany plik nagłówkowy.|
|[/YD](yd-place-debug-information-in-object-file.md)|Przestarzałe. Umieszcza pełne informacje o debugowaniu we wszystkich plikach obiektów. Zamiast tego użyj [/Zi](z7-zi-zi-debug-information-format.md) .|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|Wstawia odwołanie PCH podczas tworzenia biblioteki debugowania|
|[/Yu](yu-use-precompiled-header-file.md)|Używa prekompilowanego pliku nagłówkowego podczas kompilowania.|
|[/Z7](z7-zi-zi-debug-information-format.md)|Generuje informacje o debugowaniu zgodne z C 7,0.|
|[/Za](za-ze-disable-language-extensions.md)|Wyłącza rozszerzenia językowe.|
|[/Zc](zc-conformance.md)|Określa standardowe zachowanie w obszarze [/ze](za-ze-disable-language-extensions.md). [/Za,/ze (Wyłącz rozszerzenia językowe)](za-ze-disable-language-extensions.md)|
|[/Ze](za-ze-disable-language-extensions.md)|Przestarzałe. Włącza rozszerzenia językowe.|
|[/ZF](zf.md)|Skraca czas generowania pliku PDB w kompilacjach równoległych.|
|[/Zg](zg-generate-function-prototypes.md)|Usunięto w programie Visual Studio 2015. Generuje prototypy funkcji.|
|[/ZH](zh.md)|Określa MD5, SHA-1 lub SHA-256 dla sum kontrolnych w informacjach debugowania.|
|[/ZI](z7-zi-zi-debug-information-format.md)|Zawiera informacje o debugowaniu w programie bazy danych programu zgodne z funkcją Edytuj i Kontynuuj.|
|[/Zi](z7-zi-zi-debug-information-format.md)|Generuje pełne informacje o debugowaniu.|
|[/Zl](zl-omit-default-library-name.md)|Usuwa domyślną nazwę biblioteki z pliku. obj (tylko x86).|
|[/Zm](zm-specify-precompiled-header-memory-allocation-limit.md)|Określa limit alokacji pamięci prekompilowanego nagłówka.|
|[/Zo](zo-enhance-optimized-debugging.md)|Generuje ulepszone informacje o debugowaniu dla zoptymalizowanego kodu.|
|[/ZP](zp-struct-member-alignment.md)|Elementy członkowskie struktury pakietów.|
|[/ZS](zs-syntax-check-only.md)|Sprawdza tylko składnię.|
|[/ZW](zw-windows-runtime-compilation.md)|Tworzy plik wyjściowy do uruchomienia na środowisko wykonawcze systemu Windows.|

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
