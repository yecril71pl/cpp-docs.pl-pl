---
title: MSVC Opcje konsolidatora
description: Lista opcji obsługiwanych przez konsolidator linków firmy Microsoft.
ms.date: 09/24/2019
f1_keywords:
- link
helpviewer_keywords:
- linker [C++]
- linker [C++], options listed
- libraries [C++], linking to COFF
- LINK tool [C++], linker options
ms.assetid: c1d51b8a-bd23-416d-81e4-900e02b2c129
ms.openlocfilehash: 23cd1c3ce767cf8046e3439432db795f032dc370
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685590"
---
# <a name="linker-options"></a>Opcje konsolidatora

LINK. exe łączy pliki i biblioteki obiektów Common Object File Format (COFF), aby utworzyć plik wykonywalny (exe) lub bibliotekę dołączaną dynamicznie (DLL).

W poniższej tabeli wymieniono opcje LINK. exe. Aby uzyskać więcej informacji na temat łącza, zobacz:

- [Opcje łączy sterowane kompilatorem](compiler-controlled-link-options.md)

- [Połącz pliki wejściowe](link-input-files.md)

- [Połącz dane wyjściowe](link-output.md)

- [Słowa zastrzeżone](reserved-words.md)

W wierszu polecenia Opcje konsolidatora nie uwzględniają wielkości liter. na przykład/Base i/BASE oznaczają to samo. Aby uzyskać szczegółowe informacje na temat sposobu określania każdej opcji w wierszu polecenia lub w programie Visual Studio, zapoznaj się z dokumentacją dla tej opcji.

Aby określić Opcje konsolidatora, można użyć dyrektywy pragma [komentarza](../../preprocessor/comment-c-cpp.md) .

## <a name="linker-options-listed-alphabetically"></a>Opcje konsolidatora w porządku alfabetycznym

|Opcja|Przeznaczenie|
|------------|-------------|
|[@](at-specify-a-linker-response-file.md)|Określa plik odpowiedzi.|
|[/ALIGN](align-section-alignment.md)|Określa wyrównanie każdej sekcji.|
|[/ALLOWBIND](allowbind-prevent-dll-binding.md)|Określa, że nie można powiązać biblioteki DLL.|
|[/ALLOWISOLATION](allowisolation-manifest-lookup.md)|Określa zachowanie wyszukiwania manifestu.|
|[/APPCONTAINER](appcontainer-windows-store-app.md)|Określa, czy aplikacja musi działać w środowisku procesu kontenera aplikacji.|
|[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)|Dodaje <xref:System.Diagnostics.DebuggableAttribute> do obrazu zarządzanego.|
|[/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)|Tworzy łącze do zarządzanego zasobu.|
|[/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)|Określa, że moduł języka pośredniego (MSIL) firmy Microsoft powinien zostać zaimportowany do zestawu.|
|[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)|Osadza plik zasobów zarządzanych w zestawie.|
|[/BASE](base-base-address.md)|Ustawia adres podstawowy dla programu.|
|[/CGTHREADS](cgthreads-compiler-threads.md)|Ustawia liczbę wątków CL. exe do użycia na potrzeby optymalizacji i generowania kodu, gdy jest określone generowanie kodu w czasie konsolidacji.|
|[/CLRIMAGETYPE](clrimagetype-specify-type-of-clr-image.md)|Ustawia typ (IJW, czysty lub bezpieczny) obrazu CLR.|
|[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)|Zachowuje kod ostatniego błędu funkcji, które są wywoływane za pomocą mechanizmu P/Invoke.|
|[/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md)|Określa atrybut wątkowości, który ma zostać zastosowany do punktu wejścia programu CLR.|
|[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md)|Określa, czy konsolidator będzie stosował atrybut SuppressUnmanagedCodeSecurity do wygenerowanych przez konsolidatora obiektów PInvoke, które wywołują z kodu zarządzanego do natywnych bibliotek DLL.|
|[Opcją](debug-generate-debug-info.md)|Tworzy informacje debugowania.|
|[/DEBUGTYPE](debugtype-debug-info-options.md)|Określa, które dane mają być zawarte w informacjach o debugowaniu.|
|[/DEF](def-specify-module-definition-file.md)|Przekazuje plik definicji modułu (. def) do konsolidatora.|
|[/DEFAULTLIB](defaultlib-specify-default-library.md)|Wyszukuje określoną bibliotekę, gdy odwołania zewnętrzne są rozwiązane.|
|[/DELAY](delay-delay-load-import-settings.md)|Steruje opóźnionym ładowaniem bibliotek DLL.|
|[/DELAYLOAD](delayload-delay-load-import.md)|Powoduje opóźnione ładowanie podanej biblioteki DLL.|
|[/DELAYSIGN](delaysign-partially-sign-an-assembly.md)|Częściowo podpisuje zestaw.|
|[/DEPENDENTLOADFLAG](dependentloadflag.md)|Ustawia domyślne flagi dla zależnych obciążeń biblioteki DLL.|
|[/DLL](dll-build-a-dll.md)|Kompiluje bibliotekę DLL.|
|[/DRIVER](driver-windows-nt-kernel-mode-driver.md)|Tworzy sterownik trybu jądra.|
|[/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)|Określa, czy generować obraz wykonywalny, który może być losowo zmieniany w czasie ładowania przy użyciu funkcji losowego układu przestrzeni adresowej (ASLR).|
|[/ENTRY](entry-entry-point-symbol.md)|Ustawia adres początkowy.|
|[/errorReport](errorreport-report-internal-linker-errors.md)|Raportuje wewnętrzne błędy konsolidatora do firmy Microsoft.|
|[/EXPORT](export-exports-a-function.md)|Eksportuje funkcję.|
|[/FILEALIGN](filealign.md)|Wyrównuje sekcje w pliku wyjściowym do wielokrotności określonej wartości.|
|[/FIXED](fixed-fixed-base-address.md)|Tworzy program, który można załadować tylko przy użyciu preferowanego adresu podstawowego.|
|[/FORCE](force-force-file-output.md)|Wymusza zakończenie łącza nawet z nierozpoznanymi symbolami lub symbolami zdefiniowanymi więcej niż raz.|
|[/FUNCTIONPADMIN](functionpadmin-create-hotpatchable-image.md)|Tworzy obraz, który można zainstalować na gorąco.|
|[/GENPROFILE,/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)|Obie te opcje określają generowanie pliku. PGD przez konsolidator do obsługi optymalizacji opartej na profilach (PGO). /GENPROFILE i/FASTGENPROFILE używają różnych parametrów domyślnych.|
|[/GUARD](guard-enable-guard-checks.md)|Włącza ochronę za pomocą ochrony przepływu sterowania.|
|[/HEAP](heap-set-heap-size.md)|Ustawia rozmiar sterty w bajtach.|
|[/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)|Określa obsługę losowego generowania układu przestrzeni adresowej o wysokiej entropii 64 (ASLR).|
|[/IDLOUT](idlout-name-midl-output-files.md)|Określa nazwę pliku. idl i inne pliki wyjściowe MIDL.|
|[/IGNORE](ignore-ignore-specific-warnings.md)|Pomija dane wyjściowe określonych ostrzeżeń konsolidatora.|
|[/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md)|Zapobiega przetwarzaniu informacji o atrybutach do pliku. idl.|
|[/IMPLIB](implib-name-import-library.md)|Zastępuje domyślną nazwę biblioteki importu.|
|[/INCLUDE](include-force-symbol-references.md)|Wymusza odwołania do symboli.|
|[/INCREMENTAL](incremental-link-incrementally.md)|Kontroluje łączenie przyrostowe.|
|[/INTEGRITYCHECK](integritycheck-require-signature-check.md)|Określa, że moduł wymaga sprawdzenia podpisu w czasie ładowania.|
|[/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)|Określa kontener klucza do podpisania zestawu.|
|[/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)|Określa klucz lub parę kluczy, aby podpisać zestaw.|
|[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)|Informuje kompilator, że aplikacja obsługuje adresy większe niż dwa gigabajty|
|[/LIBPATH](libpath-additional-libpath.md)|Określa ścieżkę do wyszukania przed ścieżką biblioteki środowiska.|
|[/LINKREPRO](linkrepro.md)|Określa ścieżkę, w której mają zostać wygenerowane artefakty Odtwórz linku.|
|[/LINKREPROTARGET](linkreprotarget.md)|Generuje link Odtwórz tylko podczas tworzenia określonego elementu docelowego.|
|[/LTCG](ltcg-link-time-code-generation.md)|Określa generowanie kodu w czasie konsolidacji.|
|[/MACHINE](machine-specify-target-platform.md)|Określa platformę docelową.|
|[/MANIFEST](manifest-create-side-by-side-assembly-manifest.md)|Tworzy plik manifestu Side-by-Side i opcjonalnie osadza go w danych binarnych.|
|[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md)|Określa \<dependentAssembly > sekcji w pliku manifestu.|
|[/MANIFESTFILE](manifestfile-name-manifest-file.md)|Zmienia domyślną nazwę pliku manifestu.|
|[/MANIFESTINPUT](manifestinput-specify-manifest-input.md)|Określa plik wejściowy manifestu dla konsolidatora do przetworzenia i osadzenia w pliku binarnym. Można użyć tej opcji wiele razy, aby określić więcej niż jeden plik wejściowy manifestu.|
|[/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md)|Określa, czy informacje kontroli konta użytkownika (UAC) są osadzone w manifeście programu.|
|[/MAP](map-generate-mapfile.md)|Tworzy element mapfile.|
|[/MAPINFO](mapinfo-include-information-in-mapfile.md)|Zawiera określone informacje w mapfile.|
|[/MERGE](merge-combine-sections.md)|Łączy sekcje.|
|[/MIDL](midl-specify-midl-command-line-options.md)|Określa opcje wiersza polecenia MIDL.|
|[/NATVIS](natvis-add-natvis-to-pdb.md)|Dodaje Wizualizatory debugera z pliku Natvis do PDB.|
|[/NOASSEMBLY](noassembly-create-a-msil-module.md)|Pomija Tworzenie zestawu .NET Framework.|
|[/NODEFAULTLIB](nodefaultlib-ignore-libraries.md)|Ignoruje wszystkie (lub określone) domyślne biblioteki, gdy odwołania zewnętrzne są rozwiązane.|
|[/NOENTRY](noentry-no-entry-point.md)|Tworzy bibliotekę DLL tylko do zasobów.|
|[/NOLOGO](nologo-suppress-startup-banner-linker.md)|Pomija transparent startowy.|
|[/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)|Oznacza plik wykonywalny jako zweryfikowany pod kątem zgodności z funkcją zapobiegania wykonywaniu danych systemu Windows.|
|[/OPT](opt-optimizations.md)|Formanty łączy optymalizacje.|
|[/ORDER](order-put-functions-in-order.md)|Umieszcza COMDAT w obrazie we wstępnie określonej kolejności.|
|[/OUT](out-output-file-name.md)|Określa nazwę pliku wyjściowego.|
|[/PDB](pdb-use-program-database.md)|Tworzy plik bazy danych programu (PDB).|
|[/PDBALTPATH](pdbaltpath-use-alternate-pdb-path.md)|Używa alternatywnej lokalizacji do zapisania pliku PDB.|
|[/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)|Tworzy plik bazy danych programu (PDB), który nie ma prywatnych symboli.|
|[/PGD](pgd-specify-database-for-profile-guided-optimizations.md)|Określa plik PGD dla optymalizacji z przewodnikiem.|
|[/POGOSAFEMODE](pogosafemode-linker-option.md)|**Przestarzałe** Tworzy bezpieczną wielowątkową kompilację PGO.|
|[/PROFILE](profile-performance-tools-profiler.md)|Tworzy plik wyjściowy, który może być używany z profilerem narzędzi wydajności.|
|[/RELEASE](release-set-the-checksum.md)|Ustawia sumę kontrolną w nagłówku exe.|
|[/SAFESEH](safeseh-image-has-safe-exception-handlers.md)|Określa, czy obraz będzie zawierać tabelę bezpiecznych procedur obsługi wyjątków.|
|[/SECTION](section-specify-section-attributes.md)|Zastępuje atrybuty sekcji.|
|[/SOURCELINK](sourcelink.md)|Określa plik SourceLink do dodania do pliku PDB.|
|[/STACK](stack-stack-allocations.md)|Ustawia rozmiar stosu w bajtach.|
|[/STUB](stub-ms-dos-stub-file-name.md)|Dołącza program zastępczy systemu MS-DOS do programu systemu Win32.|
|[/SUBSYSTEM](subsystem-specify-subsystem.md)|Informuje system operacyjny, jak uruchomić plik. exe.|
|[/SWAPRUN](swaprun-load-linker-output-to-swap-file.md)|Informuje system operacyjny, aby skopiował dane wyjściowe konsolidatora do pliku wymiany przed jego uruchomieniem.|
|[/TLBID](tlbid-specify-resource-id-for-typelib.md)|Określa identyfikator zasobu biblioteki typów generowanych przez konsolidator.|
|[/TLBOUT](tlbout-name-dot-tlb-file.md)|Określa nazwę pliku. tlb i inne pliki wyjściowe MIDL.|
|[/TSAWARE](tsaware-create-terminal-server-aware-application.md)|Tworzy aplikację, która jest przeznaczona specjalnie do uruchamiania na serwerze terminali.|
|[/USEPROFILE](useprofile.md)|W celu utworzenia zoptymalizowanego obrazu są stosowane dane szkoleniowe dotyczące optymalizacji opartej na profilach.|
|[/VERBOSE](verbose-print-progress-messages.md)|Drukuje wiadomości dotyczące postępu konsolidatora.|
|[/VERSION](version-version-information.md)|Przypisuje numer wersji.|
|[/WHOLEARCHIVE](wholearchive-include-all-library-object-files.md)|Obejmuje każdy plik obiektu z określonych bibliotek statycznych.|
|[/WINMD](winmd-generate-windows-metadata.md)|Włącza generowanie pliku metadanych środowisko wykonawcze systemu Windows.|
|[/WINMDFILE](winmdfile-specify-winmd-file.md)|Określa nazwę pliku wyjściowego środowisko wykonawcze systemu Windows metadanych (WinMD), który jest generowany przez opcję konsolidatora [/winmd](winmd-generate-windows-metadata.md) .|
|[/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md)|Określa klucz lub parę kluczy do podpisania środowisko wykonawcze systemu Windows pliku metadanych.|
|[/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md)|Określa kontener klucza do podpisania pliku metadanych systemu Windows.|
|[/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md)|Częściowo podpisuje plik metadanych środowisko wykonawcze systemu Windows (WinMD), umieszczając klucz publiczny w pliku winmd.|
|[/WX](wx-treat-linker-warnings-as-errors.md)|Traktuje ostrzeżenia konsolidatora jako błędy.|

Aby uzyskać więcej informacji, zobacz [Opcje łącza kontrolowane przez kompilator](compiler-controlled-link-options.md).

## <a name="see-also"></a>Zobacz także

[Odwołanie doC++ budynku C/](c-cpp-building-reference.md)\
[Odwołanie konsolidatora MSVC](linking.md)
