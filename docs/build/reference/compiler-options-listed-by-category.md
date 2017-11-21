---
title: Opcje kompilatora rozbiciu na kategorie | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: compiler options, C++
ms.assetid: c4750dcf-dba0-4229-99b6-45cdecc11729
caps.latest.revision: "64"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 50589e18914ed452381a416cfb0f59d87b4be6a3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-options-listed-by-category"></a>Opcje kompilatora w rozbiciu na kategorie
Ten artykuł zawiera listę kategorii opcji kompilatora. Aby uzyskać alfabetyczną listę, zobacz [kompilatora wymienione opcje alfabetycznie](../../build/reference/compiler-options-listed-alphabetically.md).  
  
### <a name="optimization"></a>Optymalizacja  
  
|Opcja|Cel|  
|------------|-------------|  
|[/ O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md)|Tworzy mały kod.|  
|[/ O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)|Tworzy szybki kod.|  
|[/OB](../../build/reference/ob-inline-function-expansion.md)|Określa rozszerzenie funkcji wbudowanej.|  
|[/Od](../../build/reference/od-disable-debug.md)|Wyłącza optymalizacji.|  
|[/Og](../../build/reference/og-global-optimizations.md)|Przestarzałe. Używa optymalizacje globalne.|  
|[/OI](../../build/reference/oi-generate-intrinsic-functions.md)|Generuje funkcje wewnętrzne.|  
|[/ OS](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)|Preferuje mały kod.|  
|[/OT](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)|Pełne szybki kod.|  
|[OX](../../build/reference/ox-full-optimization.md)|Używa optymalizacji maksymalną (/ Ob2gity/GS).|  
|[/Oy](../../build/reference/oy-frame-pointer-omission.md)|Umożliwia pominięcie wskaźnika ramki. (tylko x86)|  
|[/ favor pod](../../build/reference/favor-optimize-for-architecture-specifics.md)|Generuje kod, który jest zoptymalizowana dla określonej architektury lub różnych architektur.|  
  
### <a name="code-generation"></a>Generowanie kodu  
  
|Opcja|Cel|  
|------------|-------------|  
|[/ arch](../../build/reference/arch-x86.md)|Użyj instrukcji SSE i SSE2 podczas generowania kodu. (tylko x86)|  
|[/ CLR](../../build/reference/clr-common-language-runtime-compilation.md)|Tworzy plik wyjściowy do uruchamiania na środowisko uruchomieniowe języka wspólnego.|  
|[/EH](../../build/reference/eh-exception-handling-model.md)|Określa model obsługi wyjątków.|  
|[/ FP](../../build/reference/fp-specify-floating-point-behavior.md)|Określa zachowanie zmiennoprzecinkowych.|  
|[/GA](../../build/reference/ga-optimize-for-windows-application.md)|Optymalizuje dla aplikacji systemu Windows.|  
|[/GD](../../build/reference/gd-gr-gv-gz-calling-convention.md)|Używa `__cdecl` konwencji wywoływania. (tylko x86)|  
|[/GE](../../build/reference/ge-enable-stack-probes.md)|Przestarzałe. Aktywuje sondy stosu.|  
|[/GF](../../build/reference/gf-eliminate-duplicate-strings.md)|Włącza buforowanie ciągów.|  
|[/GH](../../build/reference/gh-enable-penter-hook-function.md)|Wywołania funkcji utworzenie punktu zaczepienia `_penter`.|  
|[/GH](../../build/reference/gh-enable-pexit-hook-function.md)|Wywołania funkcji utworzenie punktu zaczepienia `_pexit`.|  
|[/GL](../../build/reference/gl-whole-program-optimization.md)|Włącza optymalizację całego programu.|  
|[/GM ponowną](../../build/reference/gm-enable-minimal-rebuild.md)|Umożliwia minimalnego ponownie.|  
|[GR](../../build/reference/gr-enable-run-time-type-information.md)|Umożliwia informacje typu run-time (RTTI).|  
|[Gr](../../build/reference/gd-gr-gv-gz-calling-convention.md)|Używa `__fastcall` konwencji wywoływania. (tylko x86)|  
|[/ GS](../../build/reference/gs-buffer-security-check.md)|Sprawdzanie buforu zabezpieczeń.|  
|[/ GS](../../build/reference/gs-control-stack-checking-calls.md)|Sondy stosu kontrolki.|  
|[/GT](../../build/reference/gt-support-fiber-safe-thread-local-storage.md)|Obsługuje bezpieczeństwa włókien danych przydzielone za pomocą statycznego magazynu wątków lokalnych.|  
|[/ GUARD: CF](../../build/reference/guard-enable-control-flow-guard.md)|Dodaje kontroli zabezpieczeń guard przepływu sterowania.|  
|[GV](../../build/reference/gd-gr-gv-gz-calling-convention.md)|Używa `__vectorcall` konwencji wywoływania. (x86 i x64 tylko)|  
|[/GW](../../build/reference/gw-optimize-global-data.md)|Włącza optymalizację całego programu danych globalnych.|  
|[/GX](../../build/reference/gx-enable-exception-handling.md)|Przestarzałe. Włącza obsługę synchronicznych wyjątku. Użyj [/EH](../../build/reference/eh-exception-handling-model.md) zamiast tego.|  
|[/GY](../../build/reference/gy-enable-function-level-linking.md)|Umożliwia poziomie funkcji łączenia.|  
|[GZ](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md)|Przestarzałe. Umożliwia szybkie sprawdzenie. (Taki sam jak [rtc1](../../build/reference/rtc-run-time-error-checks.md))|  
|[GZ](../../build/reference/gd-gr-gv-gz-calling-convention.md)|Używa `__stdcall` konwencji wywoływania. (tylko x86)|  
|[/ homeparams](../../build/reference/homeparams-copy-register-parameters-to-stack.md)|Wymusza parametry przekazywane w rejestrach były zapisywane miejsca na stosie wejścia funkcji. Ta opcja kompilatora jest tylko w przypadku [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] kompilatory (natywne i Międzyplatformowe kompilacji).|  
|[/ hotpatch](../../build/reference/hotpatch-create-hotpatchable-image.md)|Tworzy obraz możliwych.|  
|[/ Qfast_transcendentals](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md)|Generuje fast transcendentals.|  
|[QIfist](../../build/reference/qifist-suppress-ftol.md)|Przestarzałe. Pomija wywołanie funkcji Pomocnik `_ftol` podczas konwersji z typu zmiennoprzecinkowego na typ całkowity jest wymagana. (tylko x86)|  
|[/ Qimprecise_fwaits](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)|Usuwa `fwait` poleceniach wewnątrz `try` bloków.|  
|[/ Qpar](../../build/reference/qpar-auto-parallelizer.md)|Umożliwia automatyczne paralelizacja pętli.|  
|[/ Qpar raport](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)|Włącza raportowanie poziomy automatyczna paralelizacja.|  
|[/ Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md)|Instrukcje przenoszenia całkowitą używa wartości zmiennoprzecinkowych i wyłącza niektórych zmiennoprzecinkową optymalizacje obciążenia punktu.|  
|[/ Qvec raport (raportowania automatycznej Wektoryzacji poziomu)](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md)|Włącza raportowanie poziomy vectorization automatycznego.|  
|[/ RTC](../../build/reference/rtc-run-time-error-checks.md)|Włącza sprawdzanie błędów czasu wykonywania.|  
|[/ volatile](../../build/reference/volatile-volatile-keyword-interpretation.md)|Wybiera interpretacji volatile — słowo kluczowe.|  
  
### <a name="output-files"></a>Pliki wyjściowe  
  
|Opcja|Cel|  
|------------|-------------|  
|[/ doc](../../build/reference/doc-process-documentation-comments-c-cpp.md)|Przetwarza komentarzy do dokumentacji do pliku XML.|  
|[/FA](../../build/reference/fa-fa-listing-file.md)|Konfiguruje plik listy zestawu.|  
|[/FA](../../build/reference/fa-fa-listing-file.md)|Tworzy plik listy zestawu.|  
|[/FD](../../build/reference/fd-program-database-file-name.md)|Zmienia nazwę pliku bazy danych programu.|  
|[/Fe](../../build/reference/fe-name-exe-file.md)|Zmienia nazwę pliku wykonywalnego.|  
|[/Fi](../../build/reference/fi-preprocess-output-file-name.md)|Określa nazwę pliku wstępnie przetworzonych danych wyjściowych.|  
|[/FM](../../build/reference/fm-name-mapfile.md)|Tworzy plik mapowania.|  
|[/FO](../../build/reference/fo-object-file-name.md)|Tworzy plik obiektu.|  
|[/ FP](../../build/reference/fp-name-dot-pch-file.md)|Określa nazwę pliku prekompilowanego nagłówka.|  
|[/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md)|Generuje pliki przeglądarki.|  
  
### <a name="preprocessor"></a>Preprocesor  
  
|Opcja|Cel|  
|------------|-------------|  
|[/AI](../../build/reference/ai-specify-metadata-directories.md)|Określa katalog wyszukiwania można rozpoznać odwołania do pliku przekazany do [#using](../../preprocessor/hash-using-directive-cpp.md) dyrektywy.|  
|[/C](../../build/reference/c-preserve-comments-during-preprocessing.md)|Zachowanie komentarzy podczas przetwarzania wstępnego.|  
|[/D](../../build/reference/d-preprocessor-definitions.md)|Określa stałe i makr.|  
|[/E](../../build/reference/e-preprocess-to-stdout.md)|Kopiuje dane wyjściowe preprocesora do wyjścia standardowego.|  
|[/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)|Kopiuje dane wyjściowe preprocesora do wyjścia standardowego.|  
|[/FI](../../build/reference/fi-name-forced-include-file.md)|Przetwarza wstępnie dołączanego określonego pliku.|  
|[/FU](../../build/reference/fu-name-forced-hash-using-file.md)|Wymusza stosowanie nazwy pliku, tak jakby były został przekazany do [#using](../../preprocessor/hash-using-directive-cpp.md) dyrektywy.|  
|[/FX](../../build/reference/fx-merge-injected-code.md)|Wprowadzony kod scalenia z plikiem źródłowym.|  
|[/I](../../build/reference/i-additional-include-directories.md)|Wyszukuje katalog dla plików dołączanych.|  
|[/P](../../build/reference/p-preprocess-to-a-file.md)|Zapisuje dane wyjściowe preprocesora do pliku.|  
|[/U](../../build/reference/u-u-undefine-symbols.md)|Usuwa wstępnie zdefiniowanego makra.|  
|[/u](../../build/reference/u-u-undefine-symbols.md)|Usuwa wszystkie predefiniowane makra.|  
|[/X](../../build/reference/x-ignore-standard-include-paths.md)|Ignoruje standardowego katalog dołączania.|  
  
### <a name="language"></a>Język  
  
|Opcja|Cel|  
|------------|-------------|  
|[/constexpr](constexpr-control-constexpr-evaluation.md)|Formant oceny specyfikatora constexpr w czasie kompilacji.|  
|[/ OpenMP](../../build/reference/openmp-enable-openmp-2-0-support.md)|Umożliwia [#pragma omp](../../preprocessor/omp.md) w kodzie źródłowym.|  
|[/VD](../../build/reference/vd-disable-construction-displacements.md)|Włącza lub wyłącza ukryte `vtordisp` klasy elementów członkowskich.|  
|[/ vmb](../../build/reference/vmb-vmg-representation-method.md)|Używa najlepiej podstawowej dla wskaźników do elementów członkowskich.|  
|[/ vmg](../../build/reference/vmb-vmg-representation-method.md)|Używa pełnych odpisy dla wskaźników do elementów członkowskich.|  
|[/ VMM](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)|Deklaruje dziedziczenie wielokrotne.|  
|[/ VMS](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)|Deklaruje pojedyncze dziedziczenie.|  
|[/ vmv](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)|Deklaruje wirtualnego dziedziczenia.|  
|[/ Z7](../../build/reference/z7-zi-zi-debug-information-format.md)|Generuje C 7.0 zgodnego informacji o debugowaniu.|  
|[/Za](../../build/reference/za-ze-disable-language-extensions.md)|Wyłącza rozszerzenia języka.|  
|[/Zc](../../build/reference/zc-conformance.md)|Określa zachowanie standardowe w obszarze [/Ze](../../build/reference/za-ze-disable-language-extensions.md).|  
|[/Ze](../../build/reference/za-ze-disable-language-extensions.md)|Przestarzałe. Włącza rozszerzenia języka.|  
|[/ ZI](../../build/reference/z7-zi-zi-debug-information-format.md)|Zawiera informacje o debugowaniu w bazie danych programu zgodne z opcją Edytuj i Kontynuuj. (tylko x86)|  
|[/ Zi](../../build/reference/z7-zi-zi-debug-information-format.md)|Generuje pełne informacje debugowania.|  
|[/ZL](../../build/reference/zl-omit-default-library-name.md)|Usuwa domyślną nazwę biblioteki z pliku .obj.|  
|[/ZP](../../build/reference/zp-struct-member-alignment.md)*n*|Pakiety struktury elementów członkowskich.|  
|[/ZS](../../build/reference/zs-syntax-check-only.md)|Sprawdza, czy tylko składni.|  
|[/ZW](../../build/reference/zw-windows-runtime-compilation.md)|Tworzy plik wyjściowy do uruchamiania na środowiska uruchomieniowego systemu Windows.|  
  
### <a name="linking"></a>Konsolidacja  
  
|Opcja|Cel|  
|------------|-------------|  
|[/F](../../build/reference/f-set-stack-size.md)|Ustawia rozmiar stosu.|  
|[/LD](../../build/reference/md-mt-ld-use-run-time-library.md)|Tworzy bibliotekę DLL.|  
|[/ LDd](../../build/reference/md-mt-ld-use-run-time-library.md)|Tworzy bibliotekę DLL debugowania.|  
|[/ Link](../../build/reference/link-pass-options-to-linker.md)|Przekazuje określona opcja łącza.|  
|[/LN](../../build/reference/ln-create-msil-module.md)|Tworzy moduł MSIL.|  
|[/ / MD](../../build/reference/md-mt-ld-use-run-time-library.md)|Kompiluje, aby utworzyć wielowątkowe biblioteki DLL przy użyciu MSVCRT.lib.|  
|[/ MDd](../../build/reference/md-mt-ld-use-run-time-library.md)|Kompiluje się do tworzenia debugowania wielowątkowe biblioteki DLL, za pomocą MSVCRTD.lib.|  
|[/ MT](../../build/reference/md-mt-ld-use-run-time-library.md)|Kompiluje, aby utworzyć wielowątkowe plik wykonywalny przy użyciu LIBCMT.lib.|  
|[/ MTd](../../build/reference/md-mt-ld-use-run-time-library.md)|Kompiluje, aby utworzyć wielowątkowe plik wykonywalny debugowania, za pomocą biblioteki LIBCMTD.lib.|  
  
### <a name="miscellaneous"></a>Inne  
  
|Opcja|Cel|  
|------------|-------------|  
|[/?](../../build/reference/help-compiler-command-line-help.md)|Wyświetla listę opcji kompilatora.|  
|[@](../../build/reference/at-specify-a-compiler-response-file.md)|Określa plik odpowiedzi.|  
|[/ analyze](../../build/reference/analyze-code-analysis.md)|Umożliwia analizy kodu.|  
|[/ bigobj](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md)|Zwiększa liczbę adresowanego sekcji w pliku .obj.|  
|[/c](../../build/reference/c-compile-without-linking.md)|Kompiluje bez konsolidacji.|  
|[/ cgthreads](../../build/reference/cgthreads-code-generation-threads.md)|Określa liczbę wątków cl.exe do użycia na potrzeby optymalizacji i generowania kodu.|  
|[/ errorreport](../../build/reference/errorreport-report-internal-compiler-errors.md)|Umożliwia podanie wewnętrznych kompilatora informacje o błędzie (ICE) bezpośrednio do zespołu Visual C++.|  
|[/FC](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)|Wyświetla pełną ścieżkę diagnostyczny przekazano cl.exe plików kodu źródłowego.|  
|[/FS](../../build/reference/fs-force-synchronous-pdb-writes.md)|Wymusza zapisuje do pliku programu (PDB) bazy danych za pośrednictwem MSPDBSRV szeregowanie. WYWOŁANIE PLIKU EXE.|  
|[/H](../../build/reference/h-restrict-length-of-external-names.md)|Przestarzałe. Ogranicza długość nazw zewnętrznych (publicznych).|  
|[/ HELP](../../build/reference/help-compiler-command-line-help.md)|Wyświetla listę opcji kompilatora.|  
|[/J](../../build/reference/j-default-char-type-is-unsigned.md)|Zmienia domyślny `char` typu.|  
|[/ Kernel](../../build/reference/kernel-create-kernel-mode-binary.md)|Kompilatorze i konsolidatorze spowoduje utworzenie pliku binarnego, który może zostać wykonany jądra systemu Windows.|  
|[/MP](../../build/reference/mp-build-with-multiple-processes.md)|Tworzy jednocześnie wiele plików źródłowych.|  
|[/ nologo](../../build/reference/nologo-suppress-startup-banner-c-cpp.md)|Pomija wyświetlanie banera logowania jednokrotnego.|  
|[/ SDL](../../build/reference/sdl-enable-additional-security-checks.md)|Włącza dodatkowe funkcje zabezpieczeń i ostrzeżenia.|  
|[/ showincludes](../../build/reference/showincludes-list-include-files.md)|Wyświetla listę wszystkich pliki dołączane podczas kompilacji.|  
|[/ TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)|Określa plik źródłowy C.|  
|[/ TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)|Określa, że wszystkie pliki źródłowe pakietu to C.|  
|[/TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)|Określa plik źródłowy języka C++.|  
|[/TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)|Określa, że wszystkie pliki źródłowe C++.|  
|[/V](../../build/reference/v-version-number.md)|Przestarzałe. Ustawia ciąg wersji.|  
|[/w](../../build/reference/compiler-option-warning-level.md)|Wyłącza wszystkie ostrzeżenia.|  
|[/ W0, /W1, /W2, /W3, / W4](../../build/reference/compiler-option-warning-level.md)|Zestawy danych wyjściowych poziom ostrzeżeń.|  
|[/W1, /w2, /w3, / W4](../../build/reference/compiler-option-warning-level.md)|Ustawia poziom ostrzeżenia określonego ostrzeżenia.|  
|[/ Wall](../../build/reference/compiler-option-warning-level.md)|Włącza wszystkie ostrzeżenia, w tym ostrzeżenia, które są domyślnie wyłączone.|  
|[/WD](../../build/reference/compiler-option-warning-level.md)|Wyłącza określony ostrzeżenie.|  
|[/we](../../build/reference/compiler-option-warning-level.md)|Traktuje określony ostrzeżenie jako błąd.|  
|[/WL](../../build/reference/wl-enable-one-line-diagnostics.md)|Umożliwia diagnostykę dla błędów i ostrzeżeń podczas kompilowania kodu źródłowego języka C++ z wiersza polecenia.|  
|[/WO](../../build/reference/compiler-option-warning-level.md)|Wyświetla określony ostrzeżenie tylko raz.|  
|[/WV](../../build/reference/compiler-option-warning-level.md)|Wyłącza ostrzeżenia wprowadzone przy użyciu nowszej wersji kompilatora.|  
|[WX](../../build/reference/compiler-option-warning-level.md)|Traktuje ostrzeżenia jako błędy.|  
|[/Yc](../../build/reference/yc-create-precompiled-header-file.md)|Utwórz. Plik PCH.|  
|[/YD](../../build/reference/yd-place-debug-information-in-object-file.md)|Przestarzałe. Miejsca ukończyć informacji o debugowaniu we wszystkich plikach obiektu. Użyj [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) zamiast tego.|  
|[/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md)|Injects Odnośnik PCH podczas tworzenia biblioteki debugowania.|  
|[/YU](../../build/reference/yu-use-precompiled-header-file.md)|Używa prekompilowanego pliku nagłówkowego podczas kompilacji.|  
|[/Y-](../../build/reference/y-ignore-precompiled-header-options.md)|Ignoruje wszystkie inne opcje kompilatora prekompilowanego nagłówka w bieżącej kompilacji.|  
|[/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)|Określa limit alokacji pamięci prekompilowanego nagłówka.|  
|[/ await](await-enable-coroutine-support.md)|Włącz rozszerzenia koprocedurach (funkcji wznawialnych).|  
|[/ Source-Charset](source-charset-set-source-character-set.md)|Ustaw zestaw znaków źródła.|
|[/ Execution-Charset](execution-charset-set-execution-character-set.md)|Zestaw znaków wykonania zestawu.|
|[/ UTF-8](utf-8-set-source-and-executable-character-sets-to-utf-8.md)|Ustawia zestaw znaków źródła i wykonania na UTF-8.|
|[Charset](validate-charset-validate-for-compatible-characters.md)|Sprawdź poprawność plików UTF-8 tylko zgodne znaków.|
|[/Diagnostics](diagnostics-compiler-diagnostic-options.md)|Określa format komunikaty diagnostyczne.|
|[/ ograniczająca-](permissive-standards-conformance.md)|Ustaw tryb standardowy zgodność.|
|[/STD](std-specify-language-standard-version.md)|Selektor zgodność wersji standard C++.|
  
### <a name="deprecated-and-removed-compiler-options"></a>Opcje kompilatora przestarzałe i usunięte  
  
|Opcja|Cel|  
|------------|-------------|  
|[/CLR:noAssembly](../../build/reference/clr-common-language-runtime-compilation.md)|Przestarzałe. Użyj [/LN (Utwórz moduł MSIL)](../../build/reference/ln-create-msil-module.md) zamiast tego.|  
|[/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)|Przestarzałe. Tworzy plik informacji przeglądania bez zmiennych lokalnych.|  
|[/GE](../../build/reference/ge-enable-stack-probes.md)|Przestarzałe. Aktywuje sondy stosu. Na domyślnie.|  
|[/GX](../../build/reference/gx-enable-exception-handling.md)|Przestarzałe. Włącza obsługę synchronicznych wyjątku. Użyj [/EH](../../build/reference/eh-exception-handling-model.md) zamiast tego.|  
|[GZ](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md)|Przestarzałe. Umożliwia szybkie sprawdzenie. Użyj [rtc1](../../build/reference/rtc-run-time-error-checks.md) zamiast tego.|  
|[/H](../../build/reference/h-restrict-length-of-external-names.md)|Przestarzałe. Ogranicza długość nazw zewnętrznych (publicznych).|  
|[/Og](../../build/reference/og-global-optimizations.md)|Przestarzałe. Używa optymalizacje globalne.|  
|[QIfist](../../build/reference/qifist-suppress-ftol.md)|Przestarzałe. Raz używany do określenia sposobu konwertować z typu zmiennoprzecinkowego na typ całkowity.|  
|[/V](../../build/reference/v-version-number.md)|Przestarzałe. Ustawia ciąg wersji pliku .obj.|  
|[/ Wp64](../../build/reference/wp64-detect-64-bit-portability-issues.md)|Nieaktualne. Wykrywa problemów związanych z przenośnością 64-bitowych.|  
|[/YD](../../build/reference/yd-place-debug-information-in-object-file.md)|Przestarzałe. Miejsca ukończyć informacji o debugowaniu we wszystkich plikach obiektu. Użyj [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) zamiast tego.|  
|[/Zc:forScope-](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)|Przestarzałe. Wyłącza zgodność w zakresie pętli for.|  
|[/Ze](../../build/reference/za-ze-disable-language-extensions.md)|Przestarzałe. Włącza rozszerzenia języka.|  
|[/ZG](../../build/reference/zg-generate-function-prototypes.md)|Usunięte w programie Visual C++ 2015. Generuje prototypy funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie kompilacji C/C++](../../build/reference/c-cpp-building-reference.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)