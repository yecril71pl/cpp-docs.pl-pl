---
title: Opcje konsolidatora MSVC
ms.date: 08/20/2018
f1_keywords:
- link
helpviewer_keywords:
- linker [C++]
- linker [C++], options listed
- libraries [C++], linking to COFF
- LINK tool [C++], linker options
ms.assetid: c1d51b8a-bd23-416d-81e4-900e02b2c129
ms.openlocfilehash: 7ff8ecd6a607aac59fca6d32fa2784e7e3e4268f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817359"
---
# <a name="linker-options"></a>Opcje konsolidatora

LINK.exe łączy pliki obiektu Common Object File Format (COFF) i biblioteki, aby utworzyć plik wykonywalny (.exe) lub biblioteki dołączanej (dynamicznie DLL).

W poniższej tabeli wymieniono opcje dla LINK.exe. Aby uzyskać więcej informacji o bibliotece LINK zobacz:

- [Opcje LINK kontrolowane przez kompilator](compiler-controlled-link-options.md)

- [Pliki wejściowe LINK](link-input-files.md)

- [Dane wyjściowe LINK](link-output.md)

- [Słowa zastrzeżone](reserved-words.md)

W wierszu polecenia Opcje konsolidatora nie jest rozróżniana wielkość liter; na przykład/base i uwzględniają oznaczają to samo. Aby uzyskać szczegółowe informacje na temat sposobu określ każdą opcję w wierszu polecenia lub w programie Visual Studio zobacz dokumentację dla tej opcji.

Możesz użyć [komentarz](../../preprocessor/comment-c-cpp.md) pragma może określić niektóre opcje konsolidatora.

|Opcja|Cel|
|------------|-------------|
|[@](at-specify-a-linker-response-file.md)|Określa plik odpowiedzi.|
|[/ ALIGN](align-section-alignment.md)|Określa wyrównanie każdej sekcji.|
|[/ALLOWBIND](allowbind-prevent-dll-binding.md)|Określa, czy biblioteka DLL nie może być powiązane.|
|[/ALLOWISOLATION](allowisolation-manifest-lookup.md)|Określa zachowanie wyszukiwania plików manifestu.|
|[/APPCONTAINER](appcontainer-windows-store-app.md)|Określa, czy aplikacja musi pracować w środowisku procesu kontenera aplikacji.|
|[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)|Dodaje <xref:System.Diagnostics.DebuggableAttribute> do zarządzanego obrazu.|
|[/ ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)|Tworzy łącze do zarządzanego zasobem.|
|[/ ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)|Określa, czy moduł Microsoft intermediate language (MSIL) powinien zostać zaimportowany do zestawu.|
|[/ ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)|Osadza plik zasobów zarządzanych w zestawie.|
|[/ BASE](base-base-address.md)|Ustawia adres bazowy programu.|
|[/ CGTHREADS](cgthreads-compiler-threads.md)|Ustawia liczbę wątków cl.exe na potrzeby generowania optymalizacji i kodu, gdy określono Generowanie łączonych kodów czasowych.|
|[/ CLRIMAGETYPE](clrimagetype-specify-type-of-clr-image.md)|Ustawia typ (IJW, czysty lub bezpieczny) obrazu CLR.|
|[/ CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)|Zachowuje kod ostatniego błędu funkcji, które są wywoływane za pośrednictwem mechanizmu P/Invoke.|
|[/ CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md)|Określa atrybut wątków do zastosowania do punktu wejścia programu CLR.|
|[/ CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md)|Określa, czy konsolidator zastosuje atrybut SuppressUnmanagedCodeSecurity do wygenerowanych przez konsolidator odcinków kodu PInvoke, które wywołują z kodu zarządzanego do macierzystych bibliotek DLL.|
|[/DEBUG](debug-generate-debug-info.md)|Tworzenie informacji debugowania.|
|[/ DEBUGTYPE](debugtype-debug-info-options.md)|Określa, które dane do dołączenia informacji o debugowaniu.|
|[/DEF](def-specify-module-definition-file.md)|Przekazuje plik definicji modułu (.def) do konsolidatora.|
|[/DEFAULTLIB](defaultlib-specify-default-library.md)|Przeszukuje określoną bibliotekę, gdy odwołania zewnętrzne są rozwiązane.|
|[/DELAY](delay-delay-load-import-settings.md)|Steruje opóźnionym ładowaniem bibliotek DLL.|
|[/ DELAYLOAD](delayload-delay-load-import.md)|Powoduje opóźnione ładowanie określonej biblioteki dll.|
|[/ DELAYSIGN](delaysign-partially-sign-an-assembly.md)|Częściowo podpisuje zestaw.|
|[/ DEPENDENTLOADFLAG](dependentloadflag.md)|Ustawia flagi domyślne zależne ładowania biblioteki DLL.|
|[/DLL](dll-build-a-dll.md)|Kompiluje bibliotekę DLL.|
|[/DRIVER](driver-windows-nt-kernel-mode-driver.md)|Tworzy sterownik trybu jądra.|
|[/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)|Określa, czy ma być generowany obraz wykonywalny, który może być losowo przebazowanych w czasie ładowania przy użyciu funkcji randomizacji (ASLR) układu przestrzeni adresów.|
|[/ ENTRY](entry-entry-point-symbol.md)|Ustawia adres początkowy.|
|[/errorReport](errorreport-report-internal-linker-errors.md)|Zgłasza błędy wewnętrzne konsolidatora do firmy Microsoft.|
|[/EXPORT](export-exports-a-function.md)|Eksportuje funkcję.|
|[/ FILEALIGN](filealign.md)|Powoduje wyrównanie sekcji w pliku danych wyjściowych na wielokrotności określonej wartości.|
|[/FIXED](fixed-fixed-base-address.md)|Tworzy program, który może zostać załadowany tylko pod swoim preferowanym adresem bazowym.|
|[/FORCE](force-force-file-output.md)|Wymusza linku pozwalającego ukończyć nawet w przypadku nieznanych symboli i symboli zdefiniowanych więcej niż jeden raz.|
|[/FUNCTIONPADMIN](functionpadmin-create-hotpatchable-image.md)|Tworzy obraz, który może być poprawiony na gorąco.|
|[/ GENPROFILE, / FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)|Określ obie te opcje generowania pliku .pgd przez konsolidator, aby obsługiwać profilowana Optymalizacja (PGO). / Różne domyślne parametry, z których można użyć GENPROFILE i/fastgenprofile.|
|[/ GUARD](guard-enable-guard-checks.md)|Włącza ochronę ochrony przepływu sterowania.|
|[/HEAP](heap-set-heap-size.md)|Ustawia rozmiar stosu w bajtach.|
|[/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)|Określa obsługę z randomizacji układu przestrzeni adresowej 64-bitowej o wysokiej entropii (ASLR).|
|[/ IDLOUT](idlout-name-midl-output-files.md)|Określa nazwę pliku .idl i inne pliki wyjściowe MIDL.|
|[/ IGNORE](ignore-ignore-specific-warnings.md)|Pomija wyjście określonego konsolidatora ostrzeżeniami.|
|[/ IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md)|Zapobiega przetwarzaniu informacji o atrybutach do pliku .idl.|
|[/IMPLIB](implib-name-import-library.md)|Zastępuje domyślną nazwą biblioteki importu.|
|[/INCLUDE](include-force-symbol-references.md)|Wymusza odwołania do symbolu.|
|[/INCREMENTAL](incremental-link-incrementally.md)|Formanty przyrostowe łączenia.|
|[/INTEGRITYCHECK](integritycheck-require-signature-check.md)|Określa, czy moduł wymaga sprawdzenia podpisu w czasie ładowania.|
|[/ KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)|Określa kontener klucza do podpisywania zestawu.|
|[/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)|Określa kontener klucza lub pary kluczy do podpisywania zestawu.|
|[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)|Informuje kompilator, że aplikacja obsługuje adresy większe niż dwa gigabajty|
|[/ LIBPATH](libpath-additional-libpath.md)|Określa ścieżkę wyszukiwania przed ścieżki środowiskowej biblioteki.|
|[/LTCG](ltcg-link-time-code-generation.md)|Określa Generowanie łączonych kodów czasowych.|
|[/ MACHINE](machine-specify-target-platform.md)|Określa platformę docelową.|
|[PARAMETR / MANIFEST](manifest-create-side-by-side-assembly-manifest.md)|Tworzy plik manifestu side-by-side i opcjonalnie osadzenie go w pliku binarnym.|
|[/ MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md)|Określa \<dependentAssembly > sekcji w pliku manifestu.|
|[/ MANIFESTFILE](manifestfile-name-manifest-file.md)|Zmienia nazwę domyślnego pliku manifestu.|
|[/ MANIFESTINPUT](manifestinput-specify-manifest-input.md)|Określa wejściowy plik manifestu dla programu łączącego do przetwarzania i osadzenia w pliku binarnym. Aby określić więcej niż jednego pliku wejściowego manifestu, można użyć tej opcji wiele razy.|
|[/ MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md)|Określa, czy informacje kontroli konta użytkownika (UAC) są osadzone w manifeście programu.|
|[/MAP](map-generate-mapfile.md)|Tworzy plik mapy.|
|[/MAPINFO](mapinfo-include-information-in-mapfile.md)|Zawiera określone informacje w pliku mapfile.|
|[/MERGE](merge-combine-sections.md)|Łączy sekcje.|
|[/ MIDL](midl-specify-midl-command-line-options.md)|Określa opcje wiersza polecenia MIDL.|
|[/ NATVIS](natvis-add-natvis-to-pdb.md)|Dodaje wizualizatory debugera z pliku Natvis do PDB.|
|[/ NOASSEMBLY](noassembly-create-a-msil-module.md)|Pomija Tworzenie zestawu .NET Framework.|
|[/NODEFAULTLIB](nodefaultlib-ignore-libraries.md)|Ignoruje wszystkie (lub określone) domyślne biblioteki, gdy odwołania zewnętrzne są rozwiązane.|
|[/ NOENTRY](noentry-no-entry-point.md)|Tworzy bibliotekę DLL z samymi zasobami.|
|[/NOLOGO](nologo-suppress-startup-banner-linker.md)|Wyłącza transparent startowy.|
|[/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)|Oznacza plik wykonywalny jako zweryfikowany w celu uzyskania zgodności z funkcją zapobiegania wykonywaniu danych Windows.|
|[/OPT](opt-optimizations.md)|Optymalizacje formantów łącza.|
|[/ ORDER](order-put-functions-in-order.md)|Umieszcza funkcje Comdat na obrazie w ustalonej kolejności.|
|[/ OUT](out-output-file-name.md)|Określa nazwę pliku wyjściowego.|
|[/PDB](pdb-use-program-database.md)|Tworzy plik bazy danych (PDB) programu.|
|[/PDBALTPATH](pdbaltpath-use-alternate-pdb-path.md)|Używa następującej kolejno lokalizacji można zapisać pliku PDB.|
|[/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)|Tworzy plik bazy danych (PDB) program, który ma żadnych prywatnych symboli.|
|[/ PGD](pgd-specify-database-for-profile-guided-optimizations.md)|Określa plik .pgd dla optymalizacji sterowanej profilem.|
|[/POGOSAFEMODE](pogosafemode-linker-option.md)|**Przestarzałe** tworzy nieobsługująca bezpieczeństwa wątków kompilacja PGO instrumentacji.|
|[/ PROFILE](profile-performance-tools-profiler.md)|Tworzy plik wyjściowy, który może służyć z profilerem narzędzi wydajności.|
|[/RELEASE](release-set-the-checksum.md)|Ustawia sumę kontrolną w nagłówku .exe.|
|[/ SAFESEH](safeseh-image-has-safe-exception-handlers.md)|Określa, czy obraz będzie zawierać tabeli obsługi bezpiecznych wyjątków.|
|[/ SECTION](section-specify-section-attributes.md)|Zastępuje atrybuty sekcji.|
|[/ SOURCELINK](sourcelink.md)|Określa plik SourceLink, aby dodać do pliku PDB.|
|[/STACK](stack-stack-allocations.md)|Ustawia rozmiar stosu w bajtach.|
|[/STUB](stub-ms-dos-stub-file-name.md)|Dołącza program szczątkowy systemu MS-DOS do programu systemu Win32.|
|[/SUBSYSTEM](subsystem-specify-subsystem.md)|Informuje system operacyjny, jak uruchomić plik .exe.|
|[/SWAPRUN](swaprun-load-linker-output-to-swap-file.md)|Informuje system operacyjny, aby skopiować dane wyjściowe programu łączącego do pliku wymiany przed uruchomieniem.|
|[/TLBID](tlbid-specify-resource-id-for-typelib.md)|Określa identyfikator zasobu biblioteki typów generowanych przez konsolidator.|
|[/ TLBOUT](tlbout-name-dot-tlb-file.md)|Określa nazwę pliku .tlb i inne pliki wyjściowe MIDL.|
|[/TSAWARE](tsaware-create-terminal-server-aware-application.md)|Tworzy aplikację, która jest przeznaczona specjalnie do serwerze terminali.|
|[/USEPROFILE](useprofile.md)|Używa profilowanej optymalizacji danych szkoleniowych do utworzenia zoptymalizowanego obrazu.|
|[/VERBOSE](verbose-print-progress-messages.md)|Drukuje wiadomości dotyczące postępu konsolidatora.|
|[/VERSION](version-version-information.md)|Przypisuje numer wersji.|
|[/ WHOLEARCHIVE](wholearchive-include-all-library-object-files.md)|Zawiera każdy plik obiektu z określonym bibliotek statycznych.|
|[/ WINMD](winmd-generate-windows-metadata.md)|Umożliwia generowanie pliku metadanych środowiska wykonawczego Windows.|
|[/ WINMDFILE](winmdfile-specify-winmd-file.md)|Określa nazwę pliku dla pliku wyjściowego metadanych środowiska wykonawczego Windows (winmd), który jest generowany przez [/WINMD](winmd-generate-windows-metadata.md) — opcja konsolidatora.|
|[/ WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md)|Określa kontener klucza lub pary kluczy do podpisania pliku metadanych środowiska wykonawczego Windows.|
|[/ WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md)|Określa kontener klucza do podpisania pliku metadanych Windows.|
|[/ WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md)|Częściowo podpisuje plik metadanych środowiska wykonawczego Windows (.winmd) poprzez umieszczenie klucza publicznego w pliku winmd.|
|[/WX](wx-treat-linker-warnings-as-errors.md)|Traktuj ostrzeżenia konsolidatora jako błędy.|

Aby uzyskać więcej informacji, zobacz [opcje łącza Compiler-Controlled](compiler-controlled-link-options.md).

## <a name="see-also"></a>Zobacz także

[Dokumentacja kompilacji w języku C/C++](c-cpp-building-reference.md)<br/>
[Odwołania konsolidatora MSVC](linking.md)
