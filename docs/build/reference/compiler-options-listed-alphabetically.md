---
title: Opcje kompilatora w porządku alfabetycznym
ms.date: 05/06/2019
helpviewer_keywords:
- compiler options, C++
ms.openlocfilehash: 7e69aa501dd0a7dbf2af51b6fa2c5bf4339eb416
ms.sourcegitcommit: 07b34ca1c1fecced9fadc95de15dc5fee4f31e5a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693432"
---
# <a name="compiler-options-listed-alphabetically"></a>Opcje kompilatora w porządku alfabetycznym

Oto kompleksowa Alfabetyczna lista opcji kompilatora. Aby uzyskać listę kategorii, zobacz [opcje kompilatora wymienione według kategorii](compiler-options-listed-by-category.md).

|Opcja|Cel|
|------------|-------------|
|[@](at-specify-a-compiler-response-file.md)|Określa plik odpowiedzi.|
|[/?](help-compiler-command-line-help.md)|Wyświetla listę opcji kompilatora.|
|[/AI](ai-specify-metadata-directories.md)|Określa katalog do przeszukania w celu rozpoznania odwołań do plików przekazywanych do [#using](../../preprocessor/hash-using-directive-cpp.md) dyrektywy.|
|[/ analyze](analyze-code-analysis.md)|Włącz analizę kodu.|
|[/ arch](arch-minimum-cpu-architecture.md)|Określa architekturę do generowania kodu.|
|[/await](await-enable-coroutine-support.md)|Włącz rozszerzenia w koprocedury (z funkcji wznawialnych).|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|Zwiększa liczbę możliwych do adresowania sekcji w pliku .obj.|
|[/C](c-preserve-comments-during-preprocessing.md)|Zachowuje komentarze podczas przetwarzania wstępnego.|
|[/c](c-compile-without-linking.md)|Kompiluje bez konsolidacji.|
|[/cgthreads](cgthreads-code-generation-threads.md)|Określa liczbę wątków cl.exe na potrzeby optymalizacji i generowania kodu.|
|[/clr](clr-common-language-runtime-compilation.md)|Tworzy plik wyjściowy do uruchomienia w środowisku uruchomieniowym języka wspólnego.|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|Szacowanie kontrolki constexpr w czasie kompilacji.|
|[/D](d-preprocessor-definitions.md)|Definiuje stałe i makra.|
|[/ Diagnostics](diagnostics-compiler-diagnostic-options.md)|Kontroluje format komunikatów diagnostycznych.|
|[/doc](doc-process-documentation-comments-c-cpp.md)|Przetwarzanie komentarzy dokumentacji do pliku XML.|
|[/E](e-preprocess-to-stdout.md)|Kopiuje dane wyjściowe preprocesora do wyjścia standardowego.|
|[/EH](eh-exception-handling-model.md)|Określa model obsługi wyjątków.|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|Kopiuje dane wyjściowe preprocesora do wyjścia standardowego.|
|[/errorReport](errorreport-report-internal-compiler-errors.md)|Pozwala na dostarczenie wewnętrznych kompilatora-informacje o błędzie (ICE) bezpośrednio do firmy Microsoft C++ zespołu.|
|[/ Execution-Charset](execution-charset-set-execution-character-set.md)|Ustaw zestaw znaków wykonywania.|
|[/F](f-set-stack-size.md)|Ustawia rozmiar stosu.|
|[/favor](favor-optimize-for-architecture-specifics.md)|Generuje kod, który jest zoptymalizowany pod kątem x64 określonej architektury lub dla określonych micro architekturach AMD64 oraz Extended Memory 64 Technology (EM64T) architektury.|
|[/FA](fa-fa-listing-file.md)|Tworzy plik listingu.|
|[/Fa](fa-fa-listing-file.md)|Ustawia nazwę pliku listingu.|
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|Wyświetla pełną ścieżkę do plików kodu źródłowego jest przekazywana do cl.exe w tekście diagnostycznym.|
|[/Fd](fd-program-database-file-name.md)|Zmienia nazwę pliku bazy danych programu.|
|[/Fe](fe-name-exe-file.md)|Zmienia nazwę pliku wykonywalnego.|
|[/FI](fi-name-forced-include-file.md)|Wstępnie przetwarza określony plik do dołączenia.|
|[/Fi](fi-preprocess-output-file-name.md)|Ustawia nazwę pliku wstępnie przetworzone produkty wyjściowe.|
|[/Fm](fm-name-mapfile.md)|Tworzy plik mapy.|
|[/Fo](fo-object-file-name.md)|Tworzy plik obiektu.|
|[/fp](fp-specify-floating-point-behavior.md)|Określenie zachowania zmiennoprzecinkowego.|
|[/ FP](fp-name-dot-pch-file.md)|Określa nazwę prekompilowanego pliku nagłówka.|
|[/FR](fr-fr-create-dot-sbr-file.md)<br /><br /> [/FR](fr-fr-create-dot-sbr-file.md)|Generuje pliki przeglądarki. **/FR** jest przestarzała.|
|[/FS](fs-force-synchronous-pdb-writes.md)|Wymusza zapisanie do pliku bazy danych (PDB) programu w celu serializowana za pośrednictwem MSPDBSRV. PLIK EXE.|
|[/FU](fu-name-forced-hash-using-file.md)|Wymusza użycie nazwy pliku tak jakby została przekazana do [#using](../../preprocessor/hash-using-directive-cpp.md) dyrektywy.|
|[/Fx](fx-merge-injected-code.md)|Scala wprowadzony kod z plikiem źródłowym.|
|[/GA](ga-optimize-for-windows-application.md)|Optymalizuje kod dla aplikacji Windows.|
|[/Gd](gd-gr-gv-gz-calling-convention.md)|Używa `__cdecl` (tylko x86) konwencji wywoływania.|
|[/Ge](ge-enable-stack-probes.md)|Przestarzałe. Uaktywnia sondy stosu.|
|[/GF](gf-eliminate-duplicate-strings.md)|Włącza buforowanie ciągów.|
|[/GH](gh-enable-pexit-hook-function.md)|Wywołuje funkcję podłączania `_pexit`.|
|[/Gh](gh-enable-penter-hook-function.md)|Wywołuje funkcję podłączania `_penter`.|
|[/GL](gl-whole-program-optimization.md)|Włącza optymalizację całego programu.|
|[/Gm](gm-enable-minimal-rebuild.md)|Przestarzałe. Włącza minimalną ponowną kompilację.|
|[/GR](gr-enable-run-time-type-information.md)|Włącza informacje typu run-time (RTTI).|
|[/Gr](gd-gr-gv-gz-calling-convention.md)|Używa `__fastcall` (tylko x86) konwencji wywoływania.|
|[/GS](gs-buffer-security-check.md)|Sprawdzanie zabezpieczeń buforów.|
|[/ GS](gs-control-stack-checking-calls.md)|Kontroluje sondy stosu.|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|Obsługuje bezpieczeństwo włókien dla danych przydzielonych przy użyciu statycznego magazynu wątków lokalnych.|
|[/ GUARD: CF](guard-enable-control-flow-guard.md)|Dodaje kontrole zabezpieczeń Ochrona przepływu sterowania.|
|[/Gv](gd-gr-gv-gz-calling-convention.md)|Używa `__vectorcall` konwencji wywoływania. (x86 i x64 tylko)|
|[/Gw](gw-optimize-global-data.md)|Umożliwia optymalizację danych globalnych całego programu.|
|[/GX](gx-enable-exception-handling.md)|Przestarzałe. Włącza synchroniczną obsługę wyjątków. Użyj [/EH](eh-exception-handling-model.md) zamiast tego.|
|[/Gy](gy-enable-function-level-linking.md)|Włącza funkcję łączenie na poziomie.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Przestarzałe. Taki sam jak [rtc1](rtc-run-time-error-checks.md).|
|[/Gz](gd-gr-gv-gz-calling-convention.md)|Używa `__stdcall` (tylko x86) konwencji wywoływania.|
|[/H](h-restrict-length-of-external-names.md)|Przestarzałe. Ogranicza długość nazw zewnętrznych (publicznych).|
|[/HELP](help-compiler-command-line-help.md)|Wyświetla listę opcji kompilatora.|
|[/ homeparams](homeparams-copy-register-parameters-to-stack.md)|Wymusza zapisanie parametrów przekazanych w rejestrach były zapisywane do ich lokalizacji na stosie wejściu do funkcji. Ta opcja kompilatora jest tylko w przypadku x64 kompilatory (kompilacja natywna i krzyżowa).|
|[/hotpatch](hotpatch-create-hotpatchable-image.md)|Tworzy obraz hot-patchable.|
|[/I](i-additional-include-directories.md)|Przeszukuje katalog plików dołączanych.|
|[/J](j-default-char-type-is-unsigned.md)|Zmienia domyślny `char` typu.|
|[/JMC](jmc.md)|Obsługuje debugowanie natywne C++ tylko mój kod.|
|[/kernel](kernel-create-kernel-mode-binary.md)|Kompilator i konsolidator utworzą plik binarny, który może zostać wykonany w jądrze Windows.|
|[/LD](md-mt-ld-use-run-time-library.md)|Tworzy bibliotekę DLL.|
|[/LDd](md-mt-ld-use-run-time-library.md)|Tworzy bibliotekę DLL debugowania.|
|[/link](link-pass-options-to-linker.md)|Przekazuje określoną opcję do łącza.|
|[/LN](ln-create-msil-module.md)|Tworzy moduł MSIL.|
|[/MD](md-mt-ld-use-run-time-library.md)|Tworzy wielowątkową bibliotekę DLL używającą biblioteki MSVCRT.lib.|
|[/MDd](md-mt-ld-use-run-time-library.md)|Tworzy debugowania wielowątkową bibliotekę DLL używającą biblioteki MSVCRTD.lib.|
|[/MP](mp-build-with-multiple-processes.md)|Kompiluje wiele plików źródłowych przy użyciu wielu procesów.|
|[/MT](md-mt-ld-use-run-time-library.md)|Tworzy wielowątkowy plik wykonywalny używający biblioteki LIBCMT.lib.|
|[/MTd](md-mt-ld-use-run-time-library.md)|Tworzy wielowątkowy plik wykonywalny debugowania używający biblioteki LIBCMTD.lib.|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|Pomija wyświetlanie transparentu logowania.|
|[/O1](o1-o2-minimize-size-maximize-speed.md)|Tworzy mały kod.|
|[/O2](o1-o2-minimize-size-maximize-speed.md)|Tworzy szybki kod.|
|[/Ob](ob-inline-function-expansion.md)|Kontroluje wbudowane rozwijanie.|
|[/Od](od-disable-debug.md)|Wyłącza optymalizację.|
|[/Og](og-global-optimizations.md)|Przestarzałe. Używa globalnych optymalizacji.|
|[/Oi](oi-generate-intrinsic-functions.md)|Generuje funkcje wewnętrzne.|
|[/ OpenMP](openmp-enable-openmp-2-0-support.md)|Włącza [ `#pragma omp` ](../../preprocessor/omp.md) dyrektywę w kodzie źródłowym.|
|[/ OS](os-ot-favor-small-code-favor-fast-code.md)|Preferuje mały kod.|
|[/OT](os-ot-favor-small-code-favor-fast-code.md)|Preferuje szybki kod.|
|[/Ox](ox-full-optimization.md)|Używa maksymalnej optymalizacji (/ Ob2gity/GS).|
|[/Oy](oy-frame-pointer-omission.md)|Pomija wskaźnik ramki (tylko x86).|
|[/P](p-preprocess-to-a-file.md)|Zapisuje dane wyjściowe preprocesora do pliku.|
|[/ permissive-](permissive-standards-conformance.md)|Ustaw tryb zgodności standard.|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|Generuje fast transcendentals.|
|[/QIfist](qifist-suppress-ftol.md)|Przestarzałe. Pomija `_ftol` podczas konwersji z typu zmiennoprzecinkowego na typ całkowity jest wymagana (tylko x86).|
|[/Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|Usuwa `fwait` polecenia wewnątrz `try` bloków.|
|[/Qpar (Automatyczny paralelizator)](qpar-auto-parallelizer.md)|Włącza automatyczne przetwarzanie równoległe pętli, które są oznaczone [#pragma loop()](../../preprocessor/loop.md) dyrektywy.|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|Używa całkowitoliczbowych instrukcji przeniesienia dla wartości zmiennopozycyjnych i wyłącza niektóre ładowania zmiennopozycyjnego.|
|[/Qvec-report (Poziom raportowania automatycznej wektoryzacji)](qvec-report-auto-vectorizer-reporting-level.md)|Włącza poziomy raportowania dla automatycznej wektoryzacji.|
|[/RTC](rtc-run-time-error-checks.md)|Włącza sprawdzanie błędów czasu wykonywania.|
|[/sdl](sdl-enable-additional-security-checks.md)|Umożliwia dodatkowe funkcje zabezpieczeń i ostrzeżenia.|
|[/showIncludes](showincludes-list-include-files.md)|Wyświetla listę wszystkich plików dołączanych podczas kompilacji.|
|[/ Source-Charset](source-charset-set-source-character-set.md)|Ustaw źródłowy zestaw znaków.|
|[/ STD](std-specify-language-standard-version.md)|Selektor zgodności wersję standardu języka C++.|
|[/Tc](tc-tp-tc-tp-specify-source-file-type.md)|Określa plik źródłowy C.|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|Określa, że wszystkie pliki źródłowe znajdują się C.|
|[/Tp](tc-tp-tc-tp-specify-source-file-type.md)|Określa plik źródłowy języka C++.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Określa, że wszystkie pliki źródłowe C++.|
|[/U](u-u-undefine-symbols.md)|Usuwa wstępnie zdefiniowane makro.|
|[/u](u-u-undefine-symbols.md)|Usuwa wszystkie wstępnie zdefiniowane makra.|
|[/utf-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|Ustawia zestaw znaków źródła i wykonania na UTF-8.|
|[/V](v-version-number.md)|Przestarzałe. Ustawia ciąg wersji pliku .obj.|
|[/validate-charset](validate-charset-validate-for-compatible-characters.md)|Sprawdź poprawność plików UTF-8 tylko zgodność znaków.|
|[/vd](vd-disable-construction-displacements.md)|Wyłącza lub włącza elementy członkowskie klasy vtordisp ukryte.|
|[/vmb](vmb-vmg-representation-method.md)|Używa najlepszej podstawy dla wskaźników do elementów członkowskich.|
|[/vmg](vmb-vmg-representation-method.md)|Używa pełnej ogólności dla wskaźników do elementów członkowskich.|
|[/vmm](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje wielokrotne dziedziczenie.|
|[/vms](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje pojedyncze dziedziczenie.|
|[/vmv](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje wirtualne dziedziczenie.|
|[/volatile](volatile-volatile-keyword-interpretation.md)|Wybiera, jaki volatile — słowo kluczowe jest interpretowany.|
|[/w](compiler-option-warning-level.md)|Wyłącza wszystkie ostrzeżenia.|
|[/W0, /W1, /W2, /W3, /W4](compiler-option-warning-level.md)|Ustawia poziom ostrzeżeń, które w danych wyjściowych.|
|[/w1, /w2, /w3, /w4](compiler-option-warning-level.md)|Ustawia poziom ostrzeżeń dla określonego ostrzeżenia.|
|[/Wall](compiler-option-warning-level.md)|Włącza wszystkie ostrzeżenia, łącznie z ostrzeżeniami, które są domyślnie wyłączone.|
|[/wd](compiler-option-warning-level.md)|Wyłącza określone ostrzeżenie.|
|[/we](compiler-option-warning-level.md)|Traktuje określone ostrzeżenie jako błąd.|
|[/WL](wl-enable-one-line-diagnostics.md)|Włącza diagnostykę dla błędów i komunikaty ostrzegawcze podczas kompilowania kodu źródłowego języka C++ z poziomu wiersza polecenia.|
|[/wo](compiler-option-warning-level.md)|Wyświetla określoną ostrzeżenie tylko raz.|
|[/Wp64](wp64-detect-64-bit-portability-issues.md)|Nieaktualne. Wykrywa problemy przenośności w programowaniu 64-bitowych.|
|[/Wv](compiler-option-warning-level.md)|Wyświetlane żadne ostrzeżenia wprowadzone po określonej wersji kompilatora.|
|[/WX](compiler-option-warning-level.md)|Traktuje wszystkie ostrzeżenia jako błędy.|
|[/X](x-ignore-standard-include-paths.md)|Ignoruje Standardowy katalog plików dołączanych.|
|[/Y-](y-ignore-precompiled-header-options.md)|Ignoruje wszystkie inne opcje kompilatora wstępnie skompilowanego nagłówka w bieżącej kompilacji.|
|[/Yc](yc-create-precompiled-header-file.md)|Tworzy prekompilowany plik nagłówka.|
|[/YD](yd-place-debug-information-in-object-file.md)|Przestarzałe. Umieszcza pełne informacje debugowania we wszystkich plikach obiektu. Użyj [/zi](z7-zi-zi-debug-information-format.md) zamiast tego.|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|Wstawia odwołanie kompilatora PCH podczas tworzenia biblioteki debugowania|
|[/Yu](yu-use-precompiled-header-file.md)|Używa prekompilowanego pliku nagłówkowego podczas kompilacji.|
|[/Z7](z7-zi-zi-debug-information-format.md)|Generuje informacje debugowania zgodne 7.0 C.|
|[/Za](za-ze-disable-language-extensions.md)|Wyłącza rozszerzenia językowe.|
|[/Zc](zc-conformance.md)|Określa standardowe zachowanie dla opcji [/Ze](za-ze-disable-language-extensions.md).[ / Za, /Ze (Wyłącz rozszerzenia językowe)](za-ze-disable-language-extensions.md)|
|[/Ze](za-ze-disable-language-extensions.md)|Przestarzałe. Włącza rozszerzenia językowe.|
|[/Zf](zf.md)|Poprawia PDB czas generowania w kompilacjach równoległych.|
|[/Zg](zg-generate-function-prototypes.md)|Usunięto w programie Visual Studio 2015. Generuje prototypy funkcji.|
|[/ZI](z7-zi-zi-debug-information-format.md)|Zawiera informacje o debugowaniu w bazie danych programu zgodne z funkcją Edytuj i Kontynuuj.|
|[/Zi](z7-zi-zi-debug-information-format.md)|Generuje kompletne informacje debugowania.|
|[/Zl](zl-omit-default-library-name.md)|Usuwa domyślną nazwę biblioteki z pliku .obj (tylko x86).|
|[/Zm](zm-specify-precompiled-header-memory-allocation-limit.md)|Określa limit alokacji pamięci prekompilowanego nagłówka.|
|[/Zo](zo-enhance-optimized-debugging.md)|Generuje rozszerzone informacje debugowania dla zoptymalizowanego kodu.|
|[/Zp](zp-struct-member-alignment.md)|Pakuje elementy członkowskie struktury.|
|[/Zs](zs-syntax-check-only.md)|Sprawdza tylko składnię.|
|[/ZW](zw-windows-runtime-compilation.md)|Tworzy plik wyjściowy do uruchomienia na środowiska wykonawczego Windows.|

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
