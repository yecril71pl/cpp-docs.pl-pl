---
title: Opcje kompilatora w porządku alfabetycznym
description: Lista odwołań w kolejności alfabetycznej opcji wiersza polecenia kompilatora Microsoft C/C++.
ms.date: 07/08/2020
helpviewer_keywords:
- compiler options, C++
ms.openlocfilehash: 46c6f7009c840c83db2f945de2e504f08172fca2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223892"
---
# <a name="compiler-options-listed-alphabetically"></a>Opcje kompilatora w porządku alfabetycznym

Ta tabela zawiera alfabetyczną listę opcji kompilatora. Aby zapoznać się z listą opcji kompilatora według kategorii, zobacz [Opcje kompilatora wymienione według kategorii](compiler-options-listed-by-category.md) .

## <a name="compiler-options"></a>Opcje kompilatora

| Opcja | Przeznaczenie |
|--|--|
| [`@`](at-specify-a-compiler-response-file.md) | Określa plik odpowiedzi. |
| [`/?`](help-compiler-command-line-help.md) | Wyświetla listę opcji kompilatora. |
| [`/AI`](ai-specify-metadata-directories.md) | Określa katalog do przeszukania w celu rozpoznania odwołań do plików przekazaną do [`#using`](../../preprocessor/hash-using-directive-cpp.md) dyrektywy. |
| [`/analyze`](analyze-code-analysis.md) | Włącz analizę kodu. |
| [`/arch`](arch-minimum-cpu-architecture.md) | Określa architekturę generowania kodu. |
| [`/await`](await-enable-coroutine-support.md) | Włącz rozszerzenia procedur wspólnych (możliwością wznowienia Functions). |
| [`/bigobj`](bigobj-increase-number-of-sections-in-dot-obj-file.md) | Zwiększa liczbę sekcji adresowanych w pliku. obj. |
| [`/C`](c-preserve-comments-during-preprocessing.md) | Zachowuje komentarze podczas przetwarzania wstępnego. |
| [`/c`](c-compile-without-linking.md) | Kompiluje bez konsolidacji. |
| [`/cgthreads`](cgthreads-code-generation-threads.md) | Określa liczbę cl.exe wątków do użycia na potrzeby optymalizacji i generowania kodu. |
| [`/clr`](clr-common-language-runtime-compilation.md) | Tworzy plik wyjściowy do uruchomienia w środowisku uruchomieniowym języka wspólnego. |
| [`/constexpr`](constexpr-control-constexpr-evaluation.md) | Ocena kontrolki **`constexpr`** w czasie kompilacji. |
| [`/D`](d-preprocessor-definitions.md) | Definiuje stałe i makra. |
| [`/diagnostics`](diagnostics-compiler-diagnostic-options.md) | Kontroluje Format komunikatów diagnostycznych. |
| [`/doc`](doc-process-documentation-comments-c-cpp.md) | Przetwarzaj komentarze dokumentacji do pliku XML. |
| [`/E`](e-preprocess-to-stdout.md) | Kopiuje dane wyjściowe preprocesora do wyjścia standardowego. |
| [`/EH`](eh-exception-handling-model.md) | Określa model obsługi wyjątków. |
| [`/EP`](ep-preprocess-to-stdout-without-hash-line-directives.md) | Kopiuje dane wyjściowe preprocesora do wyjścia standardowego. |
| [`/errorReport`](errorreport-report-internal-compiler-errors.md) | Przestarzałe. Raportowanie błędów jest kontrolowane przez ustawienia [raportowanie błędów systemu Windows (wer)](/windows/win32/wer/windows-error-reporting) . |
| [`/execution-charset`](execution-charset-set-execution-character-set.md) | Ustaw zestaw znaków wykonania. |
| [`/experimental:module`](experimental-module.md) | Umożliwia obsługę modułów eksperymentalnych. |
| [`/experimental:preprocessor`](experimental-preprocessor.md) | Włącza eksperymentalną obsługę preprocesora. |
| [`/F`](f-set-stack-size.md) | Ustawia rozmiar stosu. |
| [`/favor`](favor-optimize-for-architecture-specifics.md) | Tworzy kod zoptymalizowany pod kątem określonej architektury x64. Lub dla określonych mikroarchitektur w architekturze AMD64 i EM64T. |
| [`/FA`](fa-fa-listing-file.md) | Tworzy plik listy. |
| [`/Fa`](fa-fa-listing-file.md) | Ustawia nazwę pliku listy. |
| [`/FC`](fc-full-path-of-source-code-file-in-diagnostics.md) | Wyświetl pełną ścieżkę plików kodu źródłowego przekazaną do cl.exe w tekście diagnostycznym. |
| [`/Fd`](fd-program-database-file-name.md) | Zmienia nazwę pliku bazy danych programu. |
| [`/Fe`](fe-name-exe-file.md) | Zmienia nazwę pliku wykonywalnego. |
| [`/FI`](fi-name-forced-include-file.md) | Przetwarza wstępnie określony plik dołączany. |
| [`/Fi`](fi-preprocess-output-file-name.md) | Ustawia nazwę wstępnie przetworzonego pliku wyjściowego. |
| [`/Fm`](fm-name-mapfile.md) | Tworzy plik mapy. |
| [`/Fo`](fo-object-file-name.md) | Tworzy plik obiektu. |
| [`/fp`](fp-specify-floating-point-behavior.md) | Określ zachowanie zmiennoprzecinkowe. |
| [`/Fp`](fp-name-dot-pch-file.md) | Określa nazwę prekompilowanego pliku nagłówkowego. |
| [`/FR`](fr-fr-create-dot-sbr-file.md)<br /><br /> [`/Fr`](fr-fr-create-dot-sbr-file.md) | Generuje pliki przeglądarki. **`/Fr`** jest przestarzały. |
| [`/FS`](fs-force-synchronous-pdb-writes.md) | Wymusza serializację wszystkich zapisów do pliku bazy danych programu (PDB) za pomocą MSPDBSRV.EXE. |
| [`/FU`](fu-name-forced-hash-using-file.md) | Wymusza użycie nazwy pliku, tak jakby została przeniesiona do [`#using`](../../preprocessor/hash-using-directive-cpp.md) dyrektywy. |
| [`/Fx`](fx-merge-injected-code.md) | Scala wprowadzony kod z plikiem źródłowym. |
| [`/GA`](ga-optimize-for-windows-application.md) | Optymalizuje kod dla aplikacji systemu Windows. |
| [`/Gd`](gd-gr-gv-gz-calling-convention.md) | Używa **`__cdecl`** konwencji wywoływania (tylko x86). |
| [`/Ge`](ge-enable-stack-probes.md) | Przestarzałe. Aktywuje sondy stosu. |
| [`/GF`](gf-eliminate-duplicate-strings.md) | Włącza buforowanie ciągów. |
| [`/GH`](gh-enable-pexit-hook-function.md) | Wywołuje funkcję haka `_pexit` . |
| [`/Gh`](gh-enable-penter-hook-function.md) | Wywołuje funkcję haka `_penter` . |
| [`/GL`](gl-whole-program-optimization.md) | Włącza optymalizację całego programu. |
| [`/Gm`](gm-enable-minimal-rebuild.md) | Przestarzałe. Włącza minimalną ponowną kompilację. |
| [`/GR`](gr-enable-run-time-type-information.md) | Włącza informacje o typach w czasie wykonywania (RTTI). |
| [`/Gr`](gd-gr-gv-gz-calling-convention.md) | Używa **`__fastcall`** konwencji wywoływania (tylko x86). |
| [`/GS`](gs-buffer-security-check.md) | Bufory kontroli zabezpieczeń. |
| [`/Gs`](gs-control-stack-checking-calls.md) | Kontroluje sondy stosu. |
| [`/GT`](gt-support-fiber-safe-thread-local-storage.md) | Obsługuje zabezpieczenia włókna danych przydzielonych przy użyciu statycznego magazynu wątków lokalnych. |
| [`/guard:cf`](guard-enable-control-flow-guard.md) | Dodaje testy zabezpieczeń funkcji Ochrona przepływu sterowania. |
| [`/guard:ehcont`](guard-enable-eh-continuation-metadata.md) | Włącza metadane kontynuacji EH. |
| [`/Gv`](gd-gr-gv-gz-calling-convention.md) | Używa **`__vectorcall`** konwencji wywoływania. (tylko x86 i x64) |
| [`/Gw`](gw-optimize-global-data.md) | Włącza optymalizację danych globalnych całego programu. |
| [`/GX`](gx-enable-exception-handling.md) | Przestarzałe. Włącza synchroniczną obsługę wyjątków. Użyj [`/EH`](eh-exception-handling-model.md) zamiast tego. |
| [`/Gy`](gy-enable-function-level-linking.md) | Włącza łączenie na poziomie funkcji. |
| [`/GZ`](gz-enable-stack-frame-run-time-error-checking.md) | Przestarzałe. Analogicznie jak [`/RTC1`](rtc-run-time-error-checks.md) . |
| [`/Gz`](gd-gr-gv-gz-calling-convention.md) | Używa **`__stdcall`** konwencji wywoływania (tylko x86). |
| [`/H`](h-restrict-length-of-external-names.md) | Przestarzałe. Ogranicza długość nazw zewnętrznych (publicznych). |
| [`/HELP`](help-compiler-command-line-help.md) | Wyświetla listę opcji kompilatora. |
| [`/homeparams`](homeparams-copy-register-parameters-to-stack.md) | Wymusza, aby parametry przesyłane w rejestrach były zapisywane do ich lokalizacji na stosie przy wejściu do funkcji. Ta opcja kompilatora jest tylko dla kompilatorów x64 (kompilacja natywna i krzyżowa). |
| [`/hotpatch`](hotpatch-create-hotpatchable-image.md) | Tworzy obraz z poprawkami na gorąco. |
| [`/I`](i-additional-include-directories.md) | Wyszukuje pliki dołączane w katalogu. |
| [`/J`](j-default-char-type-is-unsigned.md) | Zmienia typ domyślny **`char`** . |
| [`/JMC`](jmc.md) | Obsługuje natywne debugowanie Tylko mój kod języka C++. |
| [`/kernel`](kernel-create-kernel-mode-binary.md) | Kompilator i konsolidator utworzy plik binarny, który może być wykonywany w jądrze systemu Windows. |
| [`/LD`](md-mt-ld-use-run-time-library.md) | Tworzy bibliotekę dołączaną dynamicznie. |
| [`/LDd`](md-mt-ld-use-run-time-library.md) | Tworzy bibliotekę dołączaną dynamicznie do debugowania. |
| [`/link`](link-pass-options-to-linker.md) | Przekazuje określoną opcję do LINKu. |
| [`/LN`](ln-create-msil-module.md) | Tworzy moduł MSIL. |
| [`/MD`](md-mt-ld-use-run-time-library.md) | Tworzy wielowątkową bibliotekę DLL przy użyciu MSVCRT. lib. |
| [`/MDd`](md-mt-ld-use-run-time-library.md) | Utworzenie wielowątkowej biblioteki DLL debugowania za pomocą MSVCRTD. lib. |
| [`/MP`](mp-build-with-multiple-processes.md) | Kompiluje wiele plików źródłowych przy użyciu wielu procesów. |
| [`/MT`](md-mt-ld-use-run-time-library.md) | Tworzy wielowątkowy plik wykonywalny za pomocą LIBCMT. lib. |
| [`/MTd`](md-mt-ld-use-run-time-library.md) | Tworzy wielowątkowy plik wykonywalny debugowania za pomocą LIBCMTD. lib. |
| [`/nologo`](nologo-suppress-startup-banner-c-cpp.md) | Pomija wyświetlanie transparentu logowania. |
| [`/O1`](o1-o2-minimize-size-maximize-speed.md) | Tworzy mały kod. |
| [`/O2`](o1-o2-minimize-size-maximize-speed.md) | Tworzy szybki kod. |
| [`/Ob`](ob-inline-function-expansion.md) | Steruje rozwinięciem w tekście. |
| [`/Od`](od-disable-debug.md) | Wyłącza optymalizację. |
| [`/Og`](og-global-optimizations.md) | Przestarzałe. Używa globalnych optymalizacji. |
| [`/Oi`](oi-generate-intrinsic-functions.md) | Generuje funkcje wewnętrzne. |
| [`/openmp`](openmp-enable-openmp-2-0-support.md) | Włącza [`#pragma omp`](../../preprocessor/omp.md) dyrektywę w kodzie źródłowym. |
| [`/Os`](os-ot-favor-small-code-favor-fast-code.md) | Preferuje mały kod. |
| [`/Ot`](os-ot-favor-small-code-favor-fast-code.md) | Preferuje szybki kod. |
| [`/Ox`](ox-full-optimization.md) | Podzbiór elementu/O2, który nie zawiera/GF lub/Gy. |
| [`/Oy`](oy-frame-pointer-omission.md) | Pomija wskaźnik ramki (tylko x86). |
| [`/P`](p-preprocess-to-a-file.md) | Zapisuje dane wyjściowe preprocesora do pliku. |
| [`/permissive-`](permissive-standards-conformance.md) | Ustaw tryb zgodności ze standardem. |
| [`/Qfast_transcendentals`](qfast-transcendentals-force-fast-transcendentals.md) | Generuje szybki transcendentals. |
| [`/QIfist`](qifist-suppress-ftol.md) | Przestarzałe. Pomija `_ftol` , gdy wymagana jest konwersja z typu zmiennoprzecinkowego na typ całkowity (tylko x86). |
| [`/Qimprecise_fwaits`](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md) | Usuwa `fwait` polecenia wewnątrz **`try`** bloków. |
| [`/QIntel-jcc-erratum`](qintel-jcc-erratum.md) | Zmniejsza wpływ na wydajność aktualizacji włączenia mikrokodu firmy Intel JCC sprawdzenia erraty. |
| [/Qpar (autoparalelizacji)](qpar-auto-parallelizer.md) | Włącza automatyczne przetwarzanie równoległe pętle, które są oznaczone za pomocą dyrektywy [pętli #pragma ()](../../preprocessor/loop.md) . |
| [`/Qsafe_fp_loads`](qsafe-fp-loads.md) | Używa instrukcji przenoszenia liczb całkowitych dla wartości zmiennoprzecinkowych i wyłącza pewne optymalizacje ładowania zmiennoprzecinkowego. |
| [`/Qspectre`](qspectre.md) | Określa generowanie kompilatora instrukcji w celu ograniczenia niektórych luk w zabezpieczeniach Spectre Variant 1. |
| [`/Qspectre-load`](qspectre-load.md) | Określa generowanie kompilatora serializacji instrukcji, aby ograniczyć Spectre luki w zabezpieczeniach na podstawie instrukcji ładowania. |
| [`/Qspectre-load-cf`](qspectre-load-cf.md) | Określa generowanie kompilatora serializacji instrukcji, aby wyeliminować luki w zabezpieczeniach Spectre w oparciu o instrukcje przepływu sterowania, które ładują pamięć. |
| [`/Qvec-report`(Poziom raportowania autowektoryzator)](qvec-report-auto-vectorizer-reporting-level.md) | Włącza poziomy raportowania dla automatycznej wektoryzacji. |
| [`/RTC`](rtc-run-time-error-checks.md) | Włącza sprawdzanie błędów czasu wykonywania. |
| [`/sdl`](sdl-enable-additional-security-checks.md) | Umożliwia korzystanie z dodatkowych funkcji zabezpieczeń i ostrzeżeń. |
| [`/showIncludes`](showincludes-list-include-files.md) | Wyświetla listę plików dołączanych podczas kompilacji. |
| [`/source-charset`](source-charset-set-source-character-set.md) | Ustaw zestaw znaków źródła. |
| [`/std`](std-specify-language-standard-version.md) | Selektor zgodności wersji standardowej języka C++. |
| [`/Tc`](tc-tp-tc-tp-specify-source-file-type.md) | Określa plik źródłowy w języku C. |
| [`/TC`](tc-tp-tc-tp-specify-source-file-type.md) | Określa wszystkie pliki źródłowe to C. |
| [`/Tp`](tc-tp-tc-tp-specify-source-file-type.md) | Określa plik źródłowy języka C++. |
| [`/TP`](tc-tp-tc-tp-specify-source-file-type.md) | Określa wszystkie pliki źródłowe w języku C++. |
| [`/U`](u-u-undefine-symbols.md) | Usuwa wstępnie zdefiniowane makro. |
| [`/u`](u-u-undefine-symbols.md) | Usuwa wszystkie wstępnie zdefiniowane makra. |
| [`/utf-8`](utf-8-set-source-and-executable-character-sets-to-utf-8.md) | Ustaw zestaw znaków źródła i wykonania na UTF-8. |
| [`/V`](v-version-number.md) | Przestarzałe. Ustawia ciąg wersji pliku. obj. |
| [`/validate-charset`](validate-charset-validate-for-compatible-characters.md) | Weryfikowanie plików UTF-8 tylko pod kątem zgodnych znaków. |
| [`/vd`](vd-disable-construction-displacements.md) | Pomija lub włącza ukryte elementy członkowskie klasy vtordisp. |
| [`/vmb`](vmb-vmg-representation-method.md) | Używa najlepszych podstaw dla wskaźników do elementów członkowskich. |
| [`/vmg`](vmb-vmg-representation-method.md) | Używa pełnej ogólnej wskaźników do elementów członkowskich. |
| [`/vmm`](vmm-vms-vmv-general-purpose-representation.md) | Deklaruje wielokrotne dziedziczenie. |
| [`/vms`](vmm-vms-vmv-general-purpose-representation.md) | Deklaruje pojedyncze dziedziczenie. |
| [`/vmv`](vmm-vms-vmv-general-purpose-representation.md) | Deklaruje wirtualne dziedziczenie. |
| [`/volatile`](volatile-volatile-keyword-interpretation.md) | Wybiera sposób interpretowania nietrwałego słowa kluczowego. |
| [`/w`](compiler-option-warning-level.md) | Wyłącza wszystkie ostrzeżenia. |
| [`/W0`, `/W1`, `/W2`, `/W3`, `/W4`](compiler-option-warning-level.md) | Ustawia poziom ostrzeżeń dla danych wyjściowych. |
| [`/w1`, `/w2`, `/w3`, `/w4`](compiler-option-warning-level.md) | Ustawia poziom ostrzeżeń dla określonego ostrzeżenia. |
| [`/Wall`](compiler-option-warning-level.md) | Włącza wszystkie ostrzeżenia, w tym ostrzeżenia, które są domyślnie wyłączone. |
| [`/wd`](compiler-option-warning-level.md) | Wyłącza określone ostrzeżenie. |
| [`/we`](compiler-option-warning-level.md) | Traktuje określone ostrzeżenie jako błąd. |
| [`/WL`](wl-enable-one-line-diagnostics.md) | Włącza diagnostykę jednowierszową dla komunikatów o błędach i ostrzeżeniach podczas kompilowania kodu źródłowego języka C++ z wiersza polecenia. |
| [`/wo`](compiler-option-warning-level.md) | Wyświetla określone ostrzeżenie tylko raz. |
| [`/Wp64`](wp64-detect-64-bit-portability-issues.md) | Nieaktualne. Wykrywa 64-bitowe problemy z przenośnością. |
| [`/Wv`](compiler-option-warning-level.md) | Nie zawiera żadnych ostrzeżeń wprowadzonych po określonej wersji kompilatora. |
| [`/WX`](compiler-option-warning-level.md) | Traktuje wszystkie ostrzeżenia jako błędy. |
| [`/X`](x-ignore-standard-include-paths.md) | Ignoruje standardowy katalog dołączania. |
| [`/Y-`](y-ignore-precompiled-header-options.md) | Ignoruje wszystkie inne opcje kompilatora prekompilowanego nagłówka w bieżącej kompilacji. |
| [`/Yc`](yc-create-precompiled-header-file.md) | Tworzy prekompilowany plik nagłówkowy. |
| [`/Yd`](yd-place-debug-information-in-object-file.md) | Przestarzałe. Umieszcza pełne informacje o debugowaniu we wszystkich plikach obiektów. Użyj [`/Zi`](z7-zi-zi-debug-information-format.md) zamiast tego. |
| [`/Yl`](yl-inject-pch-reference-for-debug-library.md) | Wstawia odwołanie PCH podczas tworzenia biblioteki debugowania |
| [`/Yu`](yu-use-precompiled-header-file.md) | Używa prekompilowanego pliku nagłówkowego podczas kompilowania. |
| [`/Z7`](z7-zi-zi-debug-information-format.md) | Generuje informacje o debugowaniu zgodne z C 7,0. |
| [`/Za`](za-ze-disable-language-extensions.md) | Wyłącza rozszerzenia językowe. |
| [`/Zc`](zc-conformance.md) | Określa zachowania standardowe. |
| [`/Ze`](za-ze-disable-language-extensions.md) | Przestarzałe. Włącza rozszerzenia językowe. |
| [`/Zf`](zf.md) | Skraca czas generowania pliku PDB w kompilacjach równoległych. |
| [`/Zg`](zg-generate-function-prototypes.md) | Usunięto w programie Visual Studio 2015. Generuje prototypy funkcji. |
| [`/ZH`](zh.md) | Określa MD5, SHA-1 lub SHA-256 dla sum kontrolnych w informacjach debugowania. |
| [`/ZI`](z7-zi-zi-debug-information-format.md) | Zawiera informacje o debugowaniu w programie bazy danych programu zgodne z funkcją Edytuj i Kontynuuj. |
| [`/Zi`](z7-zi-zi-debug-information-format.md) | Generuje pełne informacje o debugowaniu. |
| [`/Zl`](zl-omit-default-library-name.md) | Usuwa domyślną nazwę biblioteki z pliku. obj (tylko x86). |
| [`/Zm`](zm-specify-precompiled-header-memory-allocation-limit.md) | Określa limit alokacji pamięci prekompilowanego nagłówka. |
| [`/Zo`](zo-enhance-optimized-debugging.md) | Generuje ulepszone informacje o debugowaniu dla zoptymalizowanego kodu. |
| [`/Zp`](zp-struct-member-alignment.md) | Elementy członkowskie struktury pakietów. |
| [`/Zs`](zs-syntax-check-only.md) | Sprawdza tylko składnię. |
| [`/ZW`](zw-windows-runtime-compilation.md) | Tworzy plik wyjściowy do uruchomienia na środowisko wykonawcze systemu Windows. |

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)\
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
