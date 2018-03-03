---
title: Opcje konsolidatora | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- linker [C++]
- linker [C++], options listed
- libraries [C++], linking to COFF
- LINK tool [C++], linker options
ms.assetid: c1d51b8a-bd23-416d-81e4-900e02b2c129
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f64f9bb94f6809ecfa189cd012dd0494506a3ca4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-options"></a>Opcje konsolidatora

LINK.exe łączy pliki obiektów wspólnej obiektu pliku formatu (COFF) i biblioteki, aby utworzyć plik wykonywalny (.exe) lub biblioteki dołączanej (dynamicznie DLL).

W poniższej tabeli wymieniono opcje LINK.exe. Aby uzyskać więcej informacji na temat LINK zobacz:

- [Opcje LINK kontrolowane przez kompilator](../../build/reference/compiler-controlled-link-options.md)

- [Pliki wejściowe LINK](../../build/reference/link-input-files.md)

- [Dane wyjściowe LINK](../../build/reference/link-output.md)

- [Słowa zastrzeżone](../../build/reference/reserved-words.md)

W wierszu polecenia nie jest rozróżniana; opcje konsolidatora na przykład/base i /BASE oznaczają to samo. Aby uzyskać więcej informacji dotyczących sposobu określania poszczególnych opcji, w wierszu polecenia lub w programie Visual Studio zobacz dokumentację dla tej opcji.

Można użyć [komentarz](../../preprocessor/comment-c-cpp.md) pragma, aby określić niektóre opcje konsolidatora.

|Opcja|Cel|
|------------|-------------|
|[@](../../build/reference/at-specify-a-linker-response-file.md)|Określa plik odpowiedzi.|
|[/ ALIGN](../../build/reference/align-section-alignment.md)|Określa wyrównanie każdej sekcji.|
|[/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md)|Określa, czy biblioteki DLL nie może być powiązany.|
|[/ALLOWISOLATION](../../build/reference/allowisolation-manifest-lookup.md)|Określa zachowanie wyszukiwania manifestu.|
|[/APPCONTAINER](../../build/reference/appcontainer-windows-store-app.md)|Określa, czy uruchomić aplikację w środowisku procesu appcontainer.|
|[/ ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)|Dodaje <xref:System.Diagnostics.DebuggableAttribute> do zarządzanego obrazu.|
|[/ ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)|Tworzy łącze do zasobów zarządzanych.|
|[/ ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)|Określa, że moduł język pośredni (MSIL) firmy Microsoft, należy zaimportować do zestawu.|
|[/ ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)|Osadza plik zasobu zarządzanego w zespole.|
|[/ BASE](../../build/reference/base-base-address.md)|Ustawia adres podstawowy dla programu.|
|[/ CGTHREADS](../../build/reference/cgthreads-compiler-threads.md)|Ustawia liczbę wątków używanych podczas generowania optymalizacji i kod, gdy określona jest generowanie łączonych kodów czasowych cl.exe.|
|[/ CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md)|Ustawia typ (IJW, czysty lub bezpieczny) obrazu CLR.|
|[/ CLRSUPPORTLASTERROR](../../build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)|Zachowuje ostatni kod błędu funkcji wywołanych za pomocą mechanizmu P/Invoke.|
|[/ CLRTHREADATTRIBUTE](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md)|Określa atrybut wątku do zastosowania do punktu wejścia programu CLR.|
|[/ CLRUNMANAGEDCODECHECK](../../build/reference/clrunmanagedcodecheck-add-supressunmanagedcodesecurityattribute.md)|Określa, czy konsolidator użyje atrybutu atrybutu SuppressUnmanagedCodeSecurity generowanych przez konsolidator PInvoke klas zastępczych wywołujące z kodu zarządzanego do natywnych bibliotek DLL.|
|[/ DEBUG](../../build/reference/debug-generate-debug-info.md)|Tworzy informacji o debugowaniu.|
|[/ DEBUGTYPE](../../build/reference/debugtype-debug-info-options.md)|Określa, które dane do dołączenia informacji o debugowaniu.|
|[/ DEF](../../build/reference/def-specify-module-definition-file.md)|Przekazuje plik definicji modułu (.def) do konsolidatora.|
|[/ DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md)|Wyszukuje określony biblioteki, gdy odwołań zewnętrznych zostały rozwiązane.|
|[/ DELAY](../../build/reference/delay-delay-load-import-settings.md)|Steruje opóźnione ładowanie bibliotek DLL.|
|[/ DELAYLOAD](../../build/reference/delayload-delay-load-import.md)|Powoduje opóźnione ładowanie określonej biblioteki DLL.|
|[/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)|Częściowo podpisuje zestawu.|
|[/ DLL](../../build/reference/dll-build-a-dll.md)|Tworzy bibliotekę DLL.|
|[/ DRIVER](../../build/reference/driver-windows-nt-kernel-mode-driver.md)|Tworzy sterownik trybu jądra.|
|[/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md)|Określa, czy Generuj obraz wykonywalny, który może być losowo przebazowanych w czasie obciążenia za pomocą funkcji losowe (ASLR) układu przestrzeni adresów.|
|[/ ENTRY](../../build/reference/entry-entry-point-symbol.md)|Ustawia adres początkowy.|
|[/ errorreport](../../build/reference/errorreport-report-internal-linker-errors.md)|Wewnętrzne błędy konsolidatora raporty do firmy Microsoft.|
|[/ EXPORT](../../build/reference/export-exports-a-function.md)|Eksportuje funkcję.|
|[/ FILEALIGN](../../build/reference/filealign.md)|Wyrównuje sekcji w pliku wyjściowego na wielokrotności określoną wartość.|
|[/ FIXED](../../build/reference/fixed-fixed-base-address.md)|Tworzy program, który może zostać załadowany tylko na jego preferowany adres podstawowy.|
|[/ FORCE](../../build/reference/force-force-file-output.md)|Wymusza linku pozwalającego ukończyć nawet w przypadku nierozpoznane symbole lub symbole zdefiniowane więcej niż raz.|
|[/ FUNCTIONPADMIN](../../build/reference/functionpadmin-create-hotpatchable-image.md)|Tworzy obraz, który można serwisować gorąco.|
|[/ OPCJĘ GENPROFILE, /FASTGENPROFILE](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)|Określ obie te opcje generowania pliku .pgd przez konsolidator, aby obsługiwać Optymalizacja sterowana profilem — (PGO). / Opcję GENPROFILE i /FASTGENPROFILE parametry różne domyślne.|
|[/ GUARD](../../build/reference/guard-enable-guard-checks.md)|Umożliwia sterowania przepływem ochrona.|
|[/HEAP](../../build/reference/heap-set-heap-size.md)|Ustawia rozmiar sterty w bajtach.|
|[/HIGHENTROPYVA](../../build/reference/highentropyva-support-64-bit-aslr.md)|Określa obsługę randomizacji układu przestrzeni adresowej 64-bitowych wysokiej entropii (ASLR).|
|[/ IDLOUT](../../build/reference/idlout-name-midl-output-files.md)|Określa nazwę pliku .idl i inne pliki wyjściowe MIDL.|
|[/ IGNORE](../../build/reference/ignore-ignore-specific-warnings.md)|Pomija dane wyjściowe konsolidatora określonych ostrzeżeń.|
|[/ IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)|Zapobiega przetwarzania atrybutu informacji w pliku .idl.|
|[/ IMPLIB](../../build/reference/implib-name-import-library.md)|Przesłania domyślną nazwę biblioteki importu.|
|[/ INCLUDE](../../build/reference/include-force-symbol-references.md)|Wymusza symbolu odwołań.|
|[/ INCREMENTAL](../../build/reference/incremental-link-incrementally.md)|Formanty konsolidowania przyrostowego.|
|[/INTEGRITYCHECK](../../build/reference/integritycheck-require-signature-check.md)|Określa, że moduł wymaga sprawdzanie podpisu w czasie ładowania.|
|[/ KEYCONTAINER.](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)|Określa klucz kontenera, aby podpisać zestaw.|
|[/ KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)|Określa klucz lub parę kluczy, aby podpisać zestaw.|
|[/LARGEADDRESSAWARE](../../build/reference/largeaddressaware-handle-large-addresses.md)|Informuje kompilator, że aplikacja obsługuje adresy większe niż dwa gigabajty|
|[/ LIBPATH](../../build/reference/libpath-additional-libpath.md)|Określa ścieżkę wyszukiwania przed ścieżki środowiskowej biblioteki.|
|[/ LTCG](../../build/reference/ltcg-link-time-code-generation.md)|Określa Generowanie łączonych kodów czasowych.|
|[/ MACHINE](../../build/reference/machine-specify-target-platform.md)|Określa platformę docelową.|
|[/ MANIFEST](../../build/reference/manifest-create-side-by-side-assembly-manifest.md)|Tworzy plik manifestu side-by-side i opcjonalnie osadza w danych binarnych.|
|[/ MANIFESTDEPENDENCY](../../build/reference/manifestdependency-specify-manifest-dependencies.md)|Określa \<dependentAssembly > sekcji w pliku manifestu.|
|[/ MANIFESTFILE](../../build/reference/manifestfile-name-manifest-file.md)|Zmienia nazwę domyślnego pliku manifestu.|
|[/ MANIFESTINPUT](../../build/reference/manifestinput-specify-manifest-input.md)|Określa plik wejściowy manifestu dla konsolidatora do przetwarzania i osadzić w danych binarnych. Tę opcję wiele razy służy do określenia więcej niż jeden plik wejściowy manifestu.|
|[/ MANIFESTUAC](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md)|Określa, czy informacje o kontroli konta użytkownika (UAC) jest osadzony w manifeście program.|
|[/ MAP](../../build/reference/map-generate-mapfile.md)|Tworzy plik mapowania.|
|[/ MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)|Zawiera informacje podane w pliku mapowania.|
|[/ MERGE](../../build/reference/merge-combine-sections.md)|Scala sekcje.|
|[/ MIDL](../../build/reference/midl-specify-midl-command-line-options.md)|Określa opcje wiersza polecenia MIDL.|
|[/ NATVIS](../../build/reference/natvis-add-natvis-to-pdb.md)|Dodaje do pliku PDB wizualizatory debugera z pliku Natvis.|
|[/ NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)|Pomija Tworzenie zestawu .NET Framework.|
|[/ NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)|Ignoruje wszystkie (lub określonego) domyślne biblioteki podczas odwołań zewnętrznych zostały rozwiązane.|
|[/ NOENTRY](../../build/reference/noentry-no-entry-point.md)|Tworzy bibliotekę DLL tylko z zasobami.|
|[/ NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md)|Pomijaj transparent startowy.|
|[/NXCOMPAT](../../build/reference/nxcompat-compatible-with-data-execution-prevention.md)|Oznacza plik wykonywalny jako zweryfikowany jako zgodny z funkcją zapobiegania wykonywaniu danych systemu Windows.|
|[/ OPT](../../build/reference/opt-optimizations.md)|Określa optymalizacje łącza.|
|[/ ORDER](../../build/reference/order-put-functions-in-order.md)|Umieszcza Comdat w obrazie w ustalonej kolejności.|
|[/ OUT](../../build/reference/out-output-file-name.md)|Określa nazwę pliku wyjściowego.|
|[/ PDB](../../build/reference/pdb-use-program-database.md)|Tworzy plik programu (PDB) bazy danych.|
|[/ PDBALTPATH](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)|Używa alternatywną lokalizację do zapisania pliku PDB.|
|[/ PDBSTRIPPED](../../build/reference/pdbstripped-strip-private-symbols.md)|Tworzy plik bazy danych (PDB) program, którego niemającym symboli prywatnych.|
|[/ PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md)|Określa plik .pgd do optymalizacji sterowanych profilem.|
|[PROFIL](../../build/reference/profile-performance-tools-profiler.md)|Tworzy plik wyjściowy, który może być używany z profilerem narzędzi wydajności.|
|[/RELEASE](../../build/reference/release-set-the-checksum.md)|Ustawia sumę kontrolną w nagłówku .exe.|
|[/ SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)|Określa, czy obraz będzie zawierać tabeli bezpieczną obsługę wyjątków.|
|[/ SECTION](../../build/reference/section-specify-section-attributes.md)|Zastępuje atrybuty sekcji.|
|[/STACK](../../build/reference/stack-stack-allocations.md)|Ustawia rozmiar stosu w bajtach.|
|[/ STUB](../../build/reference/stub-ms-dos-stub-file-name.md)|Dołącza program szczątkowy systemu MS-DOS do programu systemu Win32.|
|[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)|Informuje system operacyjny, jak uruchomić plik .exe.|
|[/SWAPRUN](../../build/reference/swaprun-load-linker-output-to-swap-file.md)|Informuje system operacyjny, aby skopiować dane wyjściowe konsolidatora do pliku wymiany, przed uruchomieniem.|
|[/ TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md)|Określa identyfikator zasobu biblioteki typów generowanych przez konsolidator.|
|[/ TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)|Określa nazwę pliku .tlb i inne pliki wyjściowe MIDL.|
|[/TSAWARE](../../build/reference/tsaware-create-terminal-server-aware-application.md)|Tworzy aplikację, której celem jest przeznaczony do uruchamiania serwera terminali.|
|[/ VERBOSE](../../build/reference/verbose-print-progress-messages.md)|Drukuje wiadomości dotyczące postępu konsolidatora.|
|[/VERSION](../../build/reference/version-version-information.md)|Przypisuje numeru wersji.|
|[/ WHOLEARCHIVE](../../build/reference/wholearchive-include-all-library-object-files.md)|Zawiera wszystkie pliki obiektu z określonej biblioteki statyczne.|
|[/ WINMD.](../../build/reference/winmd-generate-windows-metadata.md)|Włącza generowanie pliku metadanych środowiska wykonawczego systemu Windows.|
|[/ WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md)|Określa nazwę pliku dla pliku wyjściowego metadane środowiska wykonawczego systemu Windows (winmd), który jest generowany przez [/WINMD](../../build/reference/winmd-generate-windows-metadata.md) — opcja konsolidatora.|
|[/ WINMDKEYFILE](../../build/reference/winmdkeyfile-specify-winmd-key-file.md)|Określa klucz lub parę kluczy do podpisywania pliku metadanych środowiska wykonawczego systemu Windows.|
|[/ WINMDKEYCONTAINER](../../build/reference/winmdkeycontainer-specify-key-container.md)|Określa kontener klucza do podpisywania pliku metadanych systemu Windows.|
|[/ WINMDDELAYSIGN](../../build/reference/winmddelaysign-partially-sign-a-winmd.md)|Częściowo podpisuje plik metadanych środowiska wykonawczego systemu Windows (.winmd) przez umieszczenie klucza publicznego w pliku winmd.|
|[WX](../../build/reference/wx-treat-linker-warnings-as-errors.md)|Traktuje ostrzeżenia konsolidatora jako błędy.|

Aby uzyskać więcej informacji, zobacz [opcje łącza Compiler-Controlled](../../build/reference/compiler-controlled-link-options.md).

## <a name="see-also"></a>Zobacz też

[Dokumentacja kompilacji w języku C/C++](../../build/reference/c-cpp-building-reference.md)  
[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)  