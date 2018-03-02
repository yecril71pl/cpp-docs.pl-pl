---
title: Opcje kompilatora alfabetycznym | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 02/22/2018
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- compiler options, C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7906893c1dce20344a9da805ad508a7836b1291d
ms.sourcegitcommit: d24de38f9da844f824acb9d200a3f263077145fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="compiler-options-listed-alphabetically"></a>Opcje kompilatora w porządku alfabetycznym

Oto kompleksowe alfabetyczną listę opcji kompilatora. Lista kategorii, [kompilatora opcje rozbiciu na kategorie](compiler-options-listed-by-category.md).

|Opcja|Cel|
|------------|-------------|
|[@](at-specify-a-compiler-response-file.md)|Określa plik odpowiedzi.|
|[/?](help-compiler-command-line-help.md)|Wyświetla listę opcji kompilatora.|
|[/AI](ai-specify-metadata-directories.md)|Określa katalog wyszukiwania można rozpoznać odwołania do pliku przekazany do [#using](../../preprocessor/hash-using-directive-cpp.md) dyrektywy.|
|[/analyze](analyze-code-analysis.md)|Włącz analizę kodu.|
|[/ arch](arch-minimum-cpu-architecture.md)|Określa architektury dla generowania kodu.|
|[/await](await-enable-coroutine-support.md)|Włącz rozszerzenia koprocedurach (funkcji wznawialnych).|
|[/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md)|Zwiększa liczbę adresowanego sekcji w pliku .obj.|
|[/C](c-preserve-comments-during-preprocessing.md)|Zachowanie komentarzy podczas przetwarzania wstępnego.|
|[/c](c-compile-without-linking.md)|Kompiluje bez konsolidacji.|
|[/cgthreads](cgthreads-code-generation-threads.md)|Określa liczbę wątków cl.exe do użycia na potrzeby optymalizacji i generowania kodu.|
|[/clr](clr-common-language-runtime-compilation.md)|Tworzy plik wyjściowy do uruchamiania na środowisko uruchomieniowe języka wspólnego.|
|[/constexpr](constexpr-control-constexpr-evaluation.md)|Formant oceny specyfikatora constexpr w czasie kompilacji.|
|[/D](d-preprocessor-definitions.md)|Określa stałe i makr.|
|[/Diagnostics](diagnostics-compiler-diagnostic-options.md)|Określa format komunikaty diagnostyczne.|
|[/doc](doc-process-documentation-comments-c-cpp.md)|Komentarze dokumentacji procesów do pliku XML.|
|[/E](e-preprocess-to-stdout.md)|Kopiuje dane wyjściowe preprocesora do wyjścia standardowego.|
|[/EH](eh-exception-handling-model.md)|Określa model obsługi wyjątków.|
|[/EP](ep-preprocess-to-stdout-without-hash-line-directives.md)|Kopiuje dane wyjściowe preprocesora do wyjścia standardowego.|
|[/errorReport](errorreport-report-internal-compiler-errors.md)|Umożliwia podanie wewnętrznych kompilatora informacje o błędzie (ICE) bezpośrednio do zespołu Visual C++.|
|[/ Execution-Charset](execution-charset-set-execution-character-set.md)|Zestaw znaków wykonania zestawu.|
|[/F](f-set-stack-size.md)|Ustawia rozmiar stosu.|
|[/favor](favor-optimize-for-architecture-specifics.md)|Generuje kod, który jest zoptymalizowana pod kątem określonego [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] architektura lub kątem specyfiki architektury micro w zarówno AMD64, jak i pamięci rozszerzony 64 architektury technologii (EM64T).|
|[/FA](fa-fa-listing-file.md)|Tworzy plik listy.|
|[/Fa](fa-fa-listing-file.md)|Ustawia nazwę pliku listy.|
|[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)|Wyświetl pełną ścieżkę diagnostyczny przekazano cl.exe plików kodu źródłowego.|
|[/FD](fd-program-database-file-name.md)|Zmienia nazwę pliku bazy danych programu.|
|[/Fe](fe-name-exe-file.md)|Zmienia nazwę pliku wykonywalnego.|
|[/FI](fi-name-forced-include-file.md)|Przetwarza wstępnie dołączanego określonego pliku.|
|[/Fi](fi-preprocess-output-file-name.md)|Ustawia nazwę pliku wstępnie przetworzonych danych wyjściowych.|
|[/Fm](fm-name-mapfile.md)|Tworzy plik mapowania.|
|[/Fo](fo-object-file-name.md)|Tworzy plik obiektu.|
|[/ FP](fp-specify-floating-point-behavior.md)|Określenie zachowania zmiennoprzecinkowego.|
|[/ FP](fp-name-dot-pch-file.md)|Określa nazwę pliku prekompilowanego nagłówka.|
|[/FR](fr-fr-create-dot-sbr-file.md)<br /><br /> [/FR](fr-fr-create-dot-sbr-file.md)|Generuje pliki przeglądarki. **/FR** jest przestarzały.|
|[/FS](fs-force-synchronous-pdb-writes.md)|Wymusza zapisuje do pliku programu (PDB) bazy danych za pośrednictwem MSPDBSRV szeregowanie. WYWOŁANIE PLIKU EXE.|
|[/FU](fu-name-forced-hash-using-file.md)|Wymusza stosowanie nazwy pliku, tak jakby były został przekazany do [#using](../../preprocessor/hash-using-directive-cpp.md) dyrektywy.|
|[/Fx](fx-merge-injected-code.md)|Wprowadzony kod scalenia z pliku źródłowego.|
|[/GA](ga-optimize-for-windows-application.md)|Optymalizuje kod dla aplikacji systemu Windows.|
|[/Gd](gd-gr-gv-gz-calling-convention.md)|Używa `__cdecl` (tylko x86) konwencji wywoływania.|
|[/Ge](ge-enable-stack-probes.md)|Przestarzałe. Aktywuje sondy stosu.|
|[/GF](gf-eliminate-duplicate-strings.md)|Włącza buforowanie ciągów.|
|[/GH](gh-enable-pexit-hook-function.md)|Wywołania funkcji utworzenie punktu zaczepienia `_pexit`.|
|[/Gh](gh-enable-penter-hook-function.md)|Wywołania funkcji utworzenie punktu zaczepienia `_penter`.|
|[/GL](gl-whole-program-optimization.md)|Włącza optymalizację całego programu.|
|[/Gm](gm-enable-minimal-rebuild.md)|Umożliwia minimalnego ponownie.|
|[/GR](gr-enable-run-time-type-information.md)|Umożliwia informacje typu run-time (RTTI).|
|[/Gr](gd-gr-gv-gz-calling-convention.md)|Używa `__fastcall` (tylko x86) konwencji wywoływania.|
|[/GS](gs-buffer-security-check.md)|Buforuje sprawdzanie zabezpieczeń.|
|[/ GS](gs-control-stack-checking-calls.md)|Sondy stosu kontrolki.|
|[/GT](gt-support-fiber-safe-thread-local-storage.md)|Obsługuje bezpieczeństwa włókien przydzielony przy użyciu statycznego magazynu wątków lokalnych danych.|
|[/ GUARD: CF](guard-enable-control-flow-guard.md)|Dodaje kontroli zabezpieczeń guard przepływu sterowania.|
|[/Gv](gd-gr-gv-gz-calling-convention.md)|Używa `__vectorcall` konwencji wywoływania. (x86 i x64 tylko)|
|[/Gw](gw-optimize-global-data.md)|Włącza optymalizację całego programu danych globalnych.|
|[/GX](gx-enable-exception-handling.md)|Przestarzałe. Włącza obsługę synchronicznych wyjątku. Użyj [/EH](eh-exception-handling-model.md) zamiast tego.|
|[/Gy](gy-enable-function-level-linking.md)|Umożliwia poziomie funkcji łączenia.|
|[/GZ](gz-enable-stack-frame-run-time-error-checking.md)|Przestarzałe. Taki sam jak [rtc1](rtc-run-time-error-checks.md).|
|[/Gz](gd-gr-gv-gz-calling-convention.md)|Używa `__stdcall` (tylko x86) konwencji wywoływania.|
|[/H](h-restrict-length-of-external-names.md)|Przestarzałe. Ogranicza długość nazw zewnętrznych (publicznych).|
|[/HELP](help-compiler-command-line-help.md)|Wyświetla listę opcji kompilatora.|
|[/ homeparams](homeparams-copy-register-parameters-to-stack.md)|Wymusza parametry przekazywane w rejestrach były zapisywane miejsca na stosie wejścia funkcji. Ta opcja kompilatora jest tylko w przypadku [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] kompilatory (natywne i Międzyplatformowe kompilacji).|
|[/hotpatch](hotpatch-create-hotpatchable-image.md)|Tworzy obraz możliwych.|
|[/I](i-additional-include-directories.md)|Wyszukuje katalog dla plików dołączanych.|
|[/J](j-default-char-type-is-unsigned.md)|Zmienia domyślny `char` typu.|
|[/kernel](kernel-create-kernel-mode-binary.md)|Kompilatorze i konsolidatorze spowoduje utworzenie pliku binarnego, który może zostać wykonany jądra systemu Windows.|
|[/LD](md-mt-ld-use-run-time-library.md)|Tworzy bibliotekę DLL.|
|[/LDd](md-mt-ld-use-run-time-library.md)|Tworzy bibliotekę DLL debugowania.|
|[/link](link-pass-options-to-linker.md)|Przekazuje określona opcja łącza.|
|[/LN](ln-create-msil-module.md)|Tworzy moduł MSIL.|
|[/MD](md-mt-ld-use-run-time-library.md)|Tworzy wielowątkowe biblioteki DLL przy użyciu MSVCRT.lib.|
|[/MDd](md-mt-ld-use-run-time-library.md)|Tworzy Debuguj wielowątkowe biblioteki DLL przy użyciu MSVCRTD.lib.|
|[/MP](mp-build-with-multiple-processes.md)|Kompiluje wiele plików źródłowych przy użyciu wielu procesów.|
|[/MT](md-mt-ld-use-run-time-library.md)|Tworzy plik wykonywalny wielowątkowe przy użyciu LIBCMT.lib.|
|[/ MTd](md-mt-ld-use-run-time-library.md)|Tworzy Debuguj wielowątkowe plik wykonywalny przy użyciu biblioteki LIBCMTD.lib.|
|[/nologo](nologo-suppress-startup-banner-c-cpp.md)|Pomija wyświetlanie banera logowania jednokrotnego.|
|[/O1](o1-o2-minimize-size-maximize-speed.md)|Tworzy mały kod.|
|[/O2](o1-o2-minimize-size-maximize-speed.md)|Tworzy szybki kod.|
|[/Ob](ob-inline-function-expansion.md)|Określa rozszerzenie funkcji wbudowanej.|
|[/Od](od-disable-debug.md)|Wyłącza optymalizacji.|
|[/Og](og-global-optimizations.md)|Przestarzałe. Używa optymalizacje globalne.|
|[/Oi](oi-generate-intrinsic-functions.md)|Generuje funkcje wewnętrzne.|
|[/ OpenMP](openmp-enable-openmp-2-0-support.md)|Umożliwia [#pragma omp](../../preprocessor/omp.md) w kodzie źródłowym.|
|[/ OS](os-ot-favor-small-code-favor-fast-code.md)|Preferuje mały kod.|
|[/OT](os-ot-favor-small-code-favor-fast-code.md)|Pełne szybki kod.|
|[/Ox](ox-full-optimization.md)|Używa optymalizacji maksymalną (/ Ob2gity/GS).|
|[/Oy](oy-frame-pointer-omission.md)|Umożliwia pominięcie wskaźnika ramki (tylko x86).|
|[/P](p-preprocess-to-a-file.md)|Zapisuje dane wyjściowe preprocesora do pliku.|
|[/ ograniczająca-](permissive-standards-conformance.md)|Ustaw tryb standardowy zgodność.|
|[/Qfast_transcendentals](qfast-transcendentals-force-fast-transcendentals.md)|Generuje fast transcendentals.|
|[/QIfist](qifist-suppress-ftol.md)|Przestarzałe. Pomija `_ftol` podczas konwersji z typu zmiennoprzecinkowego na typ całkowity jest wymagana (tylko x86).|
|[/Qimprecise_fwaits](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|Usuwa `fwait` poleceniach wewnątrz `try` bloków.|
|[/Qpar (Automatyczny paralelizator)](qpar-auto-parallelizer.md)|Umożliwia automatyczne paralelizacja pętli, które są oznaczone ikoną z [#pragma loop()](../../preprocessor/loop.md) dyrektywy.|
|[/Qsafe_fp_loads](qsafe-fp-loads.md)|Instrukcje przenoszenia całkowitą używa wartości zmiennoprzecinkowych i wyłącza niektórych zmiennoprzecinkową optymalizacje obciążenia punktu.|
|[/Qvec-report (Poziom raportowania automatycznej wektoryzacji)](qvec-report-auto-vectorizer-reporting-level.md)|Włącza raportowanie poziomy vectorization automatycznego.|
|[/RTC](rtc-run-time-error-checks.md)|Włącza sprawdzanie błędów czasu wykonywania.|
|[/ SDL](sdl-enable-additional-security-checks.md)|Włącza dodatkowe funkcje zabezpieczeń i ostrzeżenia.|
|[/showIncludes](showincludes-list-include-files.md)|Wyświetlanie listy plików dołączanych podczas kompilacji.|
|[/ Source-Charset](source-charset-set-source-character-set.md)|Ustaw zestaw znaków źródła.|
|[/STD](std-specify-language-standard-version.md)|Selektor zgodność wersji standard C++.|
|[/Tc](tc-tp-tc-tp-specify-source-file-type.md)|Określa plik źródłowy C.|
|[/TC](tc-tp-tc-tp-specify-source-file-type.md)|Określa, że wszystkie pliki źródłowe pakietu to C.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Określa plik źródłowy języka C++.|
|[/TP](tc-tp-tc-tp-specify-source-file-type.md)|Określa, że wszystkie pliki źródłowe C++.|
|[/U](u-u-undefine-symbols.md)|Usuwa wstępnie zdefiniowanego makra.|
|[/u](u-u-undefine-symbols.md)|Usuwa wszystkie predefiniowane makra.|
|[/utf-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|Ustawia zestaw znaków źródła i wykonania na UTF-8.|
|[/V](v-version-number.md)|Przestarzałe. Ustawia ciąg wersji pliku .obj.|
|[/validate-charset](validate-charset-validate-for-compatible-characters.md)|Sprawdź poprawność plików UTF-8 tylko zgodne znaków.|
|[/vd](vd-disable-construction-displacements.md)|Włącza lub wyłącza vtordisp ukrytych elementów członkowskich klasy.|
|[/vmb](vmb-vmg-representation-method.md)|Używa najlepiej podstawowej dla wskaźników do elementów członkowskich.|
|[/vmg](vmb-vmg-representation-method.md)|Używa pełnych odpisy dla wskaźników do elementów członkowskich.|
|[/vmm](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje dziedziczenie wielokrotne.|
|[/vms](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje pojedyncze dziedziczenie.|
|[/vmv](vmm-vms-vmv-general-purpose-representation.md)|Deklaruje wirtualnego dziedziczenia.|
|[/volatile](volatile-volatile-keyword-interpretation.md)|Wybiera interpretacji volatile — słowo kluczowe.|
|[/w](compiler-option-warning-level.md)|Wyłącza wszystkie ostrzeżenia.|
|[/W0, /W1, /W2, /W3, /W4](compiler-option-warning-level.md)|Ustawia poziom ostrzeżeń do danych wyjściowych.|
|[/w1, /w2, /w3, /w4](compiler-option-warning-level.md)|Ustawia poziom ostrzeżeń dla określonego ostrzeżenie.|
|[/Wall](compiler-option-warning-level.md)|Włącza wszystkie ostrzeżenia, w tym ostrzeżenia, które są domyślnie wyłączone.|
|[/WD](compiler-option-warning-level.md)|Wyłącza określony ostrzeżenie.|
|[/we](compiler-option-warning-level.md)|Traktuje określony ostrzeżenie jako błąd.|
|[/WL](wl-enable-one-line-diagnostics.md)|Umożliwia diagnostykę dla błędów i ostrzeżeń podczas kompilowania kodu źródłowego języka C++ z wiersza polecenia.|
|[/WO](compiler-option-warning-level.md)|Wyświetla określony ostrzeżenie tylko raz.|
|[/Wp64](wp64-detect-64-bit-portability-issues.md)|Nieaktualne. Wykrywa problemów związanych z przenośnością 64-bitowych.|
|[/Wv](compiler-option-warning-level.md)|Wyświetlane nie ostrzeżenia wprowadzone po określonej wersji kompilatora.|
|[/WX](compiler-option-warning-level.md)|Traktuje wszystkie ostrzeżenia jako błędy.|
|[/X](x-ignore-standard-include-paths.md)|Ignoruje standardowego katalog dołączania.|
|[/Y-](y-ignore-precompiled-header-options.md)|Ignoruje wszystkie inne opcje kompilatora prekompilowanego nagłówka w bieżącej kompilacji.|
|[/Yc](yc-create-precompiled-header-file.md)|Tworzy plik prekompilowanego nagłówka.|
|[/YD](yd-place-debug-information-in-object-file.md)|Przestarzałe. Miejsca ukończyć informacji o debugowaniu we wszystkich plikach obiektu. Użyj [/zi](z7-zi-zi-debug-information-format.md) zamiast tego.|
|[/Yl](yl-inject-pch-reference-for-debug-library.md)|Injects Odnośnik PCH podczas tworzenia biblioteki debugowania|
|[/Yu](yu-use-precompiled-header-file.md)|Używa prekompilowanego pliku nagłówkowego podczas kompilacji.|
|[/Z7](z7-zi-zi-debug-information-format.md)|Generuje C 7.0 zgodnego informacji o debugowaniu.|
|[/Za](za-ze-disable-language-extensions.md)|Wyłącza rozszerzenia języka.|
|[/Zc](zc-conformance.md)|Określa zachowanie standardowe w obszarze [/Ze](za-ze-disable-language-extensions.md).[ / Za, /Ze (Wyłącz rozszerzenia językowe)](za-ze-disable-language-extensions.md)|
|[/Ze](za-ze-disable-language-extensions.md)|Przestarzałe. Włącza rozszerzenia języka.|
|[/Zf](zf.md)|Poprawia czas generowania w równoległej kompilacji pliku PDB.|
|[/Zg](zg-generate-function-prototypes.md)|Usunięte w programie Visual C++ 2015. Generuje prototypy funkcji.|
|[/ZI](z7-zi-zi-debug-information-format.md)|Zawiera informacje o debugowaniu w bazie danych programu zgodne z opcją Edytuj i Kontynuuj.|
|[/Zi](z7-zi-zi-debug-information-format.md)|Generuje pełne informacje debugowania.|
|[/Zl](zl-omit-default-library-name.md)|Usuwa domyślną nazwę biblioteki z pliku obj. (tylko x86).|
|[/Zm](zm-specify-precompiled-header-memory-allocation-limit.md)|Określa limit alokacji pamięci prekompilowanego nagłówka.|
|[/Zp](zp-struct-member-alignment.md)|Pakiety struktury elementów członkowskich.|
|[/Zs](zs-syntax-check-only.md)|Sprawdza, czy tylko składni.|
|[/ZW](zw-windows-runtime-compilation.md)|Tworzy plik wyjściowy do uruchamiania na środowiska uruchomieniowego systemu Windows.|

## <a name="see-also"></a>Zobacz też
 [Odwołanie kompilacji C/C++](c-cpp-building-reference.md) [— opcje kompilatora](compiler-options.md) [Ustawianie opcji kompilatora](setting-compiler-options.md)