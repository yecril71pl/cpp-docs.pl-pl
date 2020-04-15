---
title: Strony właściwości konsolidatora
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
ms.openlocfilehash: 2f2068c6c51fc6bf4e4104213e946e243fc6df2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336587"
---
# <a name="linker-property-pages"></a>Strony właściwości konsolidatora

Następujące właściwości znajdują się w obszarze**Konsolidator****właściwości** > konfiguracji**właściwości** >  **projektu** > . Aby uzyskać więcej informacji na temat konsolidatora, zobacz [CL wywołuje opcje konsolidatora](cl-invokes-the-linker.md) i [konsolidatora](linker-options.md).

## <a name="general-property-page"></a>Strona właściwości ogólnych

### <a name="output-file"></a>Plik wyjściowy

Opcja [/OUT](out-output-file-name.md) zastępuje domyślną nazwę i lokalizację programu tworzonego przez konsolidator.

### <a name="show-progress"></a>Pokaż postęp

Drukuje komunikaty postępu konsolidatora

**Choices**

- **Not Set** - Brak szczegółowości.
- **Wyświetl wszystkie komunikaty o postępie** — wyświetla wszystkie komunikaty o postępie.
- **W przypadku przeszukiwanych bibliotek** — wyświetla komunikaty o postępie wskazujące tylko przeszukiwane biblioteki.
- **Informacje o składaniu COMDAT podczas optymalizowanego łączenia** — wyświetla informacje o składaniu COMDAT podczas zoptymalizowanego łączenia.
- **Informacje o danych usuniętych podczas optymalizacji łączenia** — wyświetla informacje o funkcjach i danych usuniętych podczas optymalizacji łączenia.
- **Informacje o modułach niezgodnych z SEH** — wyświetla informacje o modułach niezgodnych z obsługą bezpiecznych wyjątków.
- **O aktywności konsolidatora związane z kodem zarządzanym** — wyświetlanie informacji o aktywności konsolidatora związane z kodem zarządzanym.

### <a name="version"></a>Wersja

Opcja [/VERSION](version-version-information.md) informuje konsolidatora o umieszczeniu numeru wersji w nagłówku pliku .exe lub .dll. Użyj DUMPBIN /HEADERS, aby wyświetlić pole wersji obrazu OPCJONALNYCH WARTOŚCI NAGŁÓWKA, aby zobaczyć efekt **/VERSION**.

### <a name="enable-incremental-linking"></a>Włączanie łączenia przyrostowego

Umożliwia łączenie przyrostowe. ([/INCREMENTAL](incremental-link-incrementally.md), /INCREMENTAL:NO)

### <a name="suppress-startup-banner"></a>Pomijanie banera startowego

Opcja [/NOLOGO](nologo-suppress-startup-banner-linker.md) uniemożliwia wyświetlanie wiadomości o prawach autorskich i numeru wersji.

### <a name="ignore-import-library"></a>Ignoruj bibliotekę importu

Ta właściwość informuje konsolidatora, aby nie łączyć żadnych danych wyjściowych .lib generowanych z tej kompilacji do dowolnego projektu zależnego. Umożliwia systemowi projektu obsługę plików dll, które nie generują pliku lib po zbudowaniu. Jeśli projekt zależy od innego projektu, który tworzy bibliotekę DLL, system projektu automatycznie łączy plik lib produkowane przez ten projekt podrzędny. Ta właściwość może być niepotrzebne w projektach, które produkują biblioteki DLL com lub biblioteki DLL tylko do zasobów, ponieważ te biblioteki DLL nie mają żadnych znaczących eksportu. Jeśli biblioteka DLL nie ma eksportu, konsolidator nie generuje pliku lib. Jeśli nie ma pliku eksportu lib, a system projektu nakazuje konsolidatorowi łącze z brakującą biblioteką DLL, łącze zakończy się niepowodzeniem. Użyj **właściwości Ignoruj bibliotekę importu,** aby rozwiązać ten problem. Po ustawieniu na **Tak**system projektu ignoruje obecność lub brak pliku lib i powoduje, że każdy projekt, który zależy od tego projektu, nie łączy się z nieistniejącym plikiem lib.

Aby programowo uzyskać dostęp <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>do tej właściwości, zobacz .

### <a name="register-output"></a>Zarejestruj dane wyjściowe

Działa `regsvr32.exe /s $(TargetPath)` na dane wyjściowe kompilacji, który jest prawidłowy tylko w projektach .dll. W projektach plików .exe właściwość jest ignorowana. Aby zarejestrować dane wyjściowe programu .exe, ustaw zdarzenie postbuild w konfiguracji, aby wykonać niestandardową rejestrację, która jest zawsze wymagana dla zarejestrowanych plików exe.

Aby programowo uzyskać dostęp <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>do tej właściwości, zobacz .

### <a name="per-user-redirection"></a>Przekierowanie na użytkownika

Rejestracja w programie Visual Studio tradycyjnie odbywa się w HKEY_CLASSES_ROOT (HKCR). W systemach Windows Vista i nowszych systemach operacyjnych, aby uzyskać dostęp do HKCR, należy uruchomić program Visual Studio w trybie podwyższonego poziomu. Deweloperzy nie zawsze chcą działać w trybie podwyższonego poziomu, ale nadal muszą pracować z rejestracją. Przekierowanie na użytkownika umożliwia rejestrację bez konieczności uruchamiania w trybie podwyższonego poziomu.

Przekierowanie na użytkownika wymusza wszelkie zapisy do HKCR zostać przekierowane do HKEY\_CURRENT\_USER (HKCU). Jeśli przekierowanie na użytkownika jest wyłączone, może to spowodować [błąd kompilacji projektu PRJ0050,](../../error-messages/tool-errors/project-build-error-prj0050.md) gdy program próbuje zapisać do HKCR.

### <a name="additional-library-directories"></a>Dodatkowe katalogi bibliotek

Umożliwia użytkownikowi zastąpienie ścieżki biblioteki środowiskowej. ([/LIBPATH](libpath-additional-libpath.md):folder)

### <a name="link-library-dependencies"></a>Zależności biblioteki łączy

Określa, czy pliki lib mają być tworzone przez projekty zależne. Zazwyczaj chcesz połączyć się w plikach lib, ale może nie być tak w przypadku niektórych bibliotek DLL.

Można również określić plik obj, podając nazwę pliku i ścieżkę względną, na przykład ".. \\.. \MyLibProject\MyObjFile.obj". Jeśli kod źródłowy pliku obj #includes wstępnie skompilowany nagłówek, na przykład pch.h, plik pch.obj znajduje się w tym samym folderze co MyObjFile.obj. Należy również dodać pch.obj jako dodatkową zależność.

### <a name="use-library-dependency-inputs"></a>Korzystanie z danych wejściowych zależności biblioteki

Określa, czy dane wejściowe mają być używane do narzędzia bibliotekarza, a nie do samego pliku biblioteki podczas łączenia w danych wyjściowych biblioteki zależności projektu. W dużym projekcie, gdy projekt zależny tworzy plik .lib, łączenie przyrostowe jest wyłączone. Jeśli istnieje wiele projektów zależnych generujących pliki .lib, kompilowanie aplikacji może trwać długo. Gdy ta właściwość jest ustawiona na **Tak,** system projektu łączy w plikach obj dla .libs produkowanych przez projekty zależne, umożliwiając łączenie przyrostowe.

Aby uzyskać informacje dotyczące uzyskiwania dostępu do strony właściwości **konsolidatora ogólnego,** zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

### <a name="link-status"></a>Stan łącza

Określa, czy konsolidator ma wyświetlać wskaźnik postępu pokazujący, jaki procent łącza został ukończony. Domyślnie nie wyświetla się te informacje o stanie. ([/LTCG](ltcg-link-time-code-generation.md):STATUS| LTCG:NOSTATUS)

### <a name="prevent-dll-binding"></a>Zapobieganie wiązaniu biblioteki DLL

[/ALLOWBIND](allowbind-prevent-dll-binding.md):NO ustawia nieco w nagłówku biblioteki DLL, który wskazuje Bind.exe, że obraz nie może być powiązany. Nie można wiązać biblioteki DLL, jeśli została podpisana cyfrowo (powiązanie unieważnia podpis).

### <a name="treat-linker-warning-as-errors"></a>Traktuj ostrzeżenie konsolidatora jako błędy

[/WX](wx-treat-linker-warnings-as-errors.md) powoduje, że nie plik wyjściowy do wygenerowania, jeśli konsolidator generuje ostrzeżenie.

### <a name="force-file-output"></a>Wymuń wyjście pliku

Opcja [/FORCE](force-force-file-output.md) informuje konsolidatora o utworzeniu pliku exe lub biblioteki DLL, nawet jeśli symbol jest określany, ale nie jest zdefiniowany lub jest zdefiniowany jako mnożona. Może utworzyć nieprawidłowy plik exe.

**Choices**

- **Enabled** - /FORCE bez argumentów oznacza zarówno wiele, jak i nierozwiązane.
- **Multiply Defined Symbol Only** - Użyj /FORCE:MULTIPLE, aby utworzyć plik wyjściowy, nawet jeśli LINK znajdzie więcej niż jedną definicję symbolu.
- **Tylko niezdefiniowany symbol** — użyj /FORCE:UNRESOLVED, aby utworzyć plik wyjściowy, niezależnie od tego, czy link znajdzie niezdefiniowany symbol. /FORCE:UNRESOLVED jest ignorowany, jeśli symbol punktu wejścia jest nierozwiązany.

### <a name="create-hot-patchable-image"></a>Tworzenie gorącego obrazu patchable

Przygotowuje obraz do hotpatching.

**Choices**

- **Włączone** — przygotowuje obraz do hotpatching.
- **Tylko obraz X86** — przygotowuje obraz X86 do napawania.
- **Tylko obraz X64** — przygotowuje obraz X64 do napawania.
- **Itanium Image Only** - Przygotowuje obraz Itanium do hotpatching.

### <a name="specify-section-attributes"></a>Określanie atrybutów sekcji

Opcja [/SECTION](section-specify-section-attributes.md) zmienia atrybuty sekcji, zastępując atrybuty ustawione podczas kompilowania pliku obj dla sekcji.

## <a name="input-property-page"></a>Strona właściwości wejściowej

### <a name="additional-dependencies"></a>Dodatkowe zależności

Określa dodatkowe elementy, które należy dodać do wiersza polecenia łącza, na przykład *kernel32.lib*.

### <a name="ignore-all-default-libraries"></a>Ignoruj wszystkie biblioteki domyślne

Opcja [/NODEFAULTLIB](nodefaultlib-ignore-libraries.md) informuje konsolidatora o usunięciu jednej lub więcej bibliotek domyślnych z listy bibliotek, które wyszukuje podczas rozpoznawania odwołań zewnętrznych.

### <a name="ignore-specific-default-libraries"></a>Ignoruj określone biblioteki domyślne

Określa jedną lub więcej nazw bibliotek domyślnych do zignorowania. Oddziel wiele bibliotek średnikami. (/NODEFAULTLIB:[nazwa, nazwa, ...])

### <a name="module-definition-file"></a>Plik definicji modułu

Opcja [/DEF](def-specify-module-definition-file.md) przekazuje plik definicji modułu (def) do konsolidatora. Tylko jeden plik def można określić do LINK.

### <a name="add-module-to-assembly"></a>Dodawanie modułu do zestawu

Opcja [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md) umożliwia dodanie odwołania do modułu do złożenia. Informacje o typie w module nie będą dostępne dla programu złożenia, który dodał odwołanie do modułu. Jednak informacje o typie w module będą dostępne dla każdego programu, który odwołuje się do zestawu.

### <a name="embed-managed-resource-file"></a>Osadzanie pliku zasobu zarządzanego

[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) osadza plik zasobu w pliku wyjściowym.

### <a name="force-symbol-references"></a>Wymusz odniesienia do symboli

Opcja [/INCLUDE](include-force-symbol-references.md) informuje konsolidator o dodaniu określonego symbolu do tabeli symboli.

### <a name="delay-loaded-dlls"></a>Opóźnione biblioteki DLL załadowane

Opcja [/DELAYLOAD](delayload-delay-load-import.md) powoduje opóźnione ładowanie bibliotek DLL. Nazwa biblioteki DLL określa bibliotekę DLL, aby opóźnić ładowanie.

### <a name="assembly-link-resource"></a>Zasób łącza zestawu

Opcja [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md) tworzy łącze do zasobu .NET Framework w pliku wyjściowym; plik zasobu nie jest umieszczany w pliku wyjściowym.

## <a name="manifest-file-property-page"></a>Strona właściwości pliku manifestu

### <a name="generate-manifest"></a>Generowanie manifestu

[/MANIFEST](manifest-create-side-by-side-assembly-manifest.md) określa, że konsolidator powinien utworzyć plik manifestu obok siebie.

### <a name="manifest-file"></a>Plik manifestu

[/MANIFESTFILE](manifestfile-name-manifest-file.md) umożliwia zmianę domyślnej nazwy pliku manifestu. Domyślną nazwą pliku manifestu jest nazwa pliku z dołączona do manifestu.

### <a name="additional-manifest-dependencies"></a>Dodatkowe zależności manifestu

[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md) umożliwia określenie atrybutów, które zostaną umieszczone w sekcji zależności pliku manifestu.

### <a name="allow-isolation"></a>Zezwalaj na izolację

Określa zachowanie wyszukiwania manifestu. ([/ALLOWISOLATION](allowisolation-manifest-lookup.md):NO)

### <a name="enable-user-account-control-uac"></a>Włącz kontrolę konta użytkownika

Określa, czy kontrola konta użytkownika jest włączona.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md), /MANIFESTUAC:NO)

### <a name="uac-execution-level"></a>Poziom wykonania konta UAC

Określa żądany poziom wykonania dla aplikacji podczas uruchamiania z kontrolą konta użytkownika.  (/MANIFESTUAC:level=[wartość])

**Choices**

- **asInvoker** - Poziom wykonania UAC: jako invoker.
- **najwyższyDostępny** - Poziom wykonania UAC: najwyższy dostępny.
- **requireAdministrator** - Poziom wykonania UAC: wymagaj administratora.

### <a name="uac-bypass-ui-protection"></a>Ochrona interfejsu użytkownika obejścia UAC

Określa, czy należy pominąć poziomy ochrony interfejsu użytkownika dla innych okien na pulpicie.  Ustaw tę właściwość na "Tak" tylko dla aplikacji ułatwień dostępu.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md):uiAccess=[true | false])

## <a name="debugging-property-page"></a>Strona właściwości debugowania

### <a name="generate-debug-info"></a>Generowanie informacji o debugowaniu

Ta opcja umożliwia tworzenie informacji debugowania dla pliku .exe lub biblioteki DLL.

**Choices**

- **Nie** — nie generuje żadnych informacji debugowania.
- **Generowanie informacji debugowania** — tworzenie pełnej bazy danych programu (PDB) idealnej do dystrybucji na serwerze Microsoft Symbol Server.
- **Generowanie informacji debugowania zoptymalizowanych pod kątem szybszych łączy** — tworzy bazę danych programu (PDB) idealną do cyklu edit-link-debug.
- **Generowanie informacji debugowania zoptymalizowanych pod kątem udostępniania i publikowania** — tworzy bazę danych programu (PDB) idealną do cyklu edit-link-debug.

### <a name="generate-program-database-file"></a>Generowanie pliku bazy danych programu

Domyślnie po określeniu [/DEBUG](debug-generate-debug-info.md) konsolidator tworzy bazę danych programu (PDB), która przechowuje informacje debugowania. Domyślna nazwa pliku PDB ma podstawową nazwę programu i rozszerzenie .pdb.

### <a name="strip-private-symbols"></a>Rozbieraj symbole prywatne

Opcja [/PDBSTRIPPED](pdbstripped-strip-private-symbols.md) tworzy drugi plik bazy danych programu (PDB) podczas tworzenia obrazu programu z dowolną z opcji kompilatora lub konsolidatora, które generują plik PDB (/DEBUG, /Z7, /Zd lub /Zi).

### <a name="generate-map-file"></a>Generowanie pliku mapy

Opcja [/MAP](map-generate-mapfile.md) informuje konsolidatora o utworzeniu pliku map.

### <a name="map-file-name"></a>Nazwa pliku mapy

Nazwa pliku mapy określona przez użytkownika. Zastępuje nazwę domyślną.

### <a name="map-exports"></a>Eksport map

Opcja [/MAPINFO](mapinfo-include-information-in-mapfile.md) informuje konsolidatora o dołączeniu określonych informacji do pliku mapy, który jest tworzony po określeniu opcji /MAP. EXPORTS informuje konsolidatora, aby uwzględnić wyeksportowane funkcje.

### <a name="debuggable-assembly"></a>Debugowany zestaw

[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md) emituje atrybut DebuggableAttribute z śledzeniem informacji debugowania i wyłącza optymalizacje JIT.

## <a name="system-property-page"></a>Strona właściwości systemu

### <a name="subsystem"></a>Podsystemu

Opcja [/SUBSYSTEM](subsystem-specify-subsystem.md) informuje system operacyjny, jak uruchomić plik exe. Wybór podsystemu wpływa na symbol punktu wejścia (lub funkcję punktu wejścia), który wybierze konsolidator.

**Choices**

- **Not Set** - Brak zestawu podsystemów.
- **Konsola** - aplikacja w trybie znaków Win32. Aplikacje konsoli są podane konsoli przez system operacyjny. Jeśli definicja jest zdefiniowana jako główna lub wmain, konsola jest wartością domyślną.
- **Windows** — aplikacja nie wymaga konsoli, prawdopodobnie dlatego, że tworzy własne okna do interakcji z użytkownikiem. Jeśli jest zdefiniowany program WinMain lub wWinMain, domyślnym ustawieniem jest system WINDOWS.
- **Natywne** — sterowniki urządzeń dla systemu Windows NT. Jeśli /DRIVER:WDM jest określony, NATIVE jest ustawieniem domyślnym.
- **Aplikacja EFI** — aplikacja EFI.
- **Sterownik usługi rozruchu EFI** — sterownik usługi rozruchu EFI.
- **EFI ROM** - EFI ROM.
- **Środowisko wykonawcze EFI** — środowisko wykonawcze EFI.
- **POSIX** — aplikacja uruchamiana z podsystemem POSIX w systemie Windows NT.

### <a name="minimum-required-version"></a>Minimalna wymagana wersja

Określ minimalną wymaganą wersję podsystemu. Argumenty są liczbami dziesiętnymi w zakresie od 0 do 65 535.

### <a name="heap-reserve-size"></a>Rozmiar rezerwy sterty

Określa całkowity rozmiar alokacji sterty w pamięci wirtualnej. Wartość domyślna to 1 MB.    ([/HEAP](heap-set-heap-size.md):rezerwa)

### <a name="heap-commit-size"></a>Rozmiar zatwierdzania sterty

Określa całkowity rozmiar alokacji sterty w pamięci fizycznej. Wartość domyślna to 4 KB.    ([/HEAP](heap-set-heap-size.md):reserve,commit)

### <a name="stack-reserve-size"></a>Rozmiar rezerwy stosu

Określa całkowity rozmiar alokacji stosu w pamięci wirtualnej. Wartość domyślna to 1 MB.     ([/STACK](stack-stack-allocations.md):rezerwa)

### <a name="stack-commit-size"></a>Rozmiar zatwierdzania stosu

Określa całkowity rozmiar alokacji stosu w pamięci fizycznej. Wartość domyślna to 4 KB.     ([/STACK](stack-stack-allocations.md):reserve,commit)

### <a name="enable-large-addresses"></a>Włączanie dużych adresów

Opcja [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md) informuje konsolidator, że aplikacja może obsługiwać adresy większe niż 2 gigabajty. Domyślnie /LARGEADDRESSAWARE:NO jest włączona, jeśli /LARGEADDRESSAWARE nie jest inaczej określony w wierszu konsolidatora.

### <a name="terminal-server"></a>Serwer terminali

Opcja [/TSAWARE](tsaware-create-terminal-server-aware-application.md) ustawia flagę w polu IMAGE_OPTIONAL_HEADER DllCharacteristics w opcjonalnym nagłówku obrazu programu. Po ustawieniu tej flagi serwer terminali nie wprowadza pewnych zmian w aplikacji.

### <a name="swap-run-from-cd"></a>Swap Run Z płyty CD

Opcja [/SWAPRUN](swaprun-load-linker-output-to-swap-file.md) informuje system operacyjny, aby najpierw skopiował dane wyjściowe konsolidatora do pliku wymiany, a następnie uruchomić obraz stamtąd. Ta opcja jest funkcją systemu Windows NT 4.0 (i nowszą). Po określeniu **dysku CD** system operacyjny skopiuje obraz na dysku wymiennym do pliku stronicowa, a następnie załaduje go.

### <a name="swap-run-from-network"></a>Swap Run z sieci

Opcja [/SWAPRUN](swaprun-load-linker-output-to-swap-file.md) informuje system operacyjny, aby najpierw skopiował dane wyjściowe konsolidatora do pliku wymiany, a następnie uruchomić obraz stamtąd. Ta opcja jest funkcją systemu Windows NT 4.0 (i nowszą). Jeśli **net** jest określony, system operacyjny najpierw skopiuje obraz binarny z sieci do pliku wymiany i załadować go stamtąd. Ta opcja jest przydatna do uruchamiania aplikacji za pośrednictwem sieci.

### <a name="driver"></a>Sterownik

Użyj opcji [/DRIVER](driver-windows-nt-kernel-mode-driver.md) linker, aby zbudować sterownik trybu jądra systemu Windows NT.

**Choices**

- **Nie ustawiono** — domyślne ustawienie sterownika.
- **Kierowca** - Kierowca
- **Tylko UP** - /DRIVER:UPONLY powoduje, że konsolidator, aby dodać bit IMAGE_FILE_UP_SYSTEM_ONLY do charakterystyki w nagłówku wyjściowym, aby określić, że jest to sterownik jednoprocesora (UP). System operacyjny odmówi załadowania sterownika UP do systemu wieloprocesorowego (MP).
- **WDM** - /DRIVER:WDM powoduje, że konsolidator ustawić bit IMAGE_DLLCHARACTERISTICS_WDM_DRIVER w opcjonalnym nagłówku DllCharacteristics pola.

## <a name="optimization-property-page"></a>Strona właściwości optymalizacji

### <a name="references"></a>Dokumentacja

[/OPT:REF](opt-optimizations.md)eliminuje funkcje i/lub dane, o których nigdy nie odwołuje się /OPT:NOREF zachowuje funkcje i/lub dane, które nigdy nie są przywoływane.

### <a name="enable-comdat-folding"></a>Włącz zwijanie COMDAT

Użyj [/OPT](opt-optimizations.md):ICF\[=iteracji], aby wykonać identyczne składane COMDAT.

### <a name="function-order"></a>Kolejność funkcji

Opcja [/ORDER](order-put-functions-in-order.md)informuje LINK, aby zoptymalizować program, umieszczając niektóre COMDATs na obrazie w określonej kolejności. LINK umieszcza funkcje w określonej kolejności w każdej sekcji obrazu.

### <a name="profile-guided-database"></a>Baza danych z przewodnikiem profilu

Określ plik pgd dla optymalizacji z przewodnikiem profilu. ([/PGD](pgd-specify-database-for-profile-guided-optimizations.md))

### <a name="link-time-code-generation"></a>Generowanie kodu czasu łącza

Określa generowanie kodu w czasie łącza. ([/LTCG](ltcg-link-time-code-generation.md))

**Choices**

- **Domyślne** — domyślne ustawienie LTCG.
- **Użyj generowania kodu czasu szybkiego łącza** — użyj generowania kodu czasu łącza z [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md).
- **Użyj generowania kodu czasu łącza** — użyj [generowania kodu czasu łącza](ltcg-link-time-code-generation.md).
- **Optymalizacja z przewodnikiem profilu - Instrument** - Użyj [optymalizacji z przewodnikiem profilu](../profile-guided-optimizations.md) z :PGINSTRUMENT.
- **Optymalizacja z przewodnikiem profilu — optymalizacja** — określa, że konsolidator powinien używać danych profilu utworzonych po uruchomieniu instrumentowanego pliku binarnego w celu utworzenia zoptymalizowanego obrazu.
- **Optymalizacja z przewodnikiem profilu — aktualizacja** — umożliwia i śledzi listę plików wejściowych, które mają być dodawane lub modyfikowane z tego, co zostało określone w fazie :PGINSTRUMENT.

## <a name="embedded-idl-property-page"></a>Strona właściwości IDL osadzonego

### <a name="midl-commands"></a>Polecenia MIDL

Określ opcje wiersza polecenia MIDL. ([/MIDL](midl-specify-midl-command-line-options.md):@responsefile)

### <a name="ignore-embedded-idl"></a>Ignoruj osadzony IDL

Opcja [/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md) określa, że żadne atrybuty IDL w kodzie źródłowym nie powinny być przetwarzane w pliku .idl.

### <a name="merged-idl-base-file-name"></a>Scalona nazwa pliku podstawowego IDL

Opcja [/IDLOUT](idlout-name-midl-output-files.md) określa nazwę i rozszerzenie pliku .idl.

### <a name="type-library"></a>Biblioteka typów

Opcja [/TLBOUT](tlbout-name-dot-tlb-file.md) określa nazwę i rozszerzenie pliku .tlb.

### <a name="typelib-resource-id"></a>Identyfikator zasobu TypeLib

Umożliwia określenie identyfikatora zasobu biblioteki typów wygenerowanych przez konsolidatora. ([/TLBID](tlbid-specify-resource-id-for-typelib.md):id)

## <a name="windows-metadata-property-page"></a>Strona właściwości metadanych systemu Windows

### <a name="generate-windows-metadata"></a>Generowanie metadanych systemu Windows

Włącza lub wyłącza generowanie metadanych systemu Windows.

**Choices**

- **Tak** — umożliwia generowanie plików metadanych systemu Windows.
- **Nie** - Wyłącz generowanie plików metadanych systemu Windows.

### <a name="windows-metadata-file"></a>Plik metadanych systemu Windows

Przełącznik opcji [/WINMDFILE.](winmdfile-specify-winmd-file.md)

### <a name="windows-metadata-key-file"></a>Plik klucza metadanych systemu Windows

Określ parę kluczy lub kluczy, aby podpisać metadane systemu Windows. ([/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md):nazwa pliku)

### <a name="windows-metadata-key-container"></a>Kontener kluczy metadanych systemu Windows

Określ kontener kluczy, aby podpisać metadane systemu Windows. ([/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md):name)

### <a name="windows-metadata-delay-sign"></a>Znak opóźnienia metadanych systemu Windows

Częściowo podpisać metadane systemu Windows. Użyj [/WINMDDELAYSIGN,](winmddelaysign-partially-sign-a-winmd.md) jeśli chcesz umieścić tylko klucz publiczny w metadanych systemu Windows. Wartość domyślna to /WINMDDELAYSIGN:NO.

## <a name="advanced-property-page"></a>Strona właściwości zaawansowanej

### <a name="entry-point"></a>Punkt wejścia

Opcja [/ENTRY](entry-entry-point-symbol.md) określa funkcję punktu wejścia jako adres początkowy pliku exe lub biblioteki DLL.

### <a name="no-entry-point"></a>Brak punktu wejścia

Opcja [/NOENTRY](noentry-no-entry-point.md)jest wymagana do tworzenia biblioteki DLL tylko do zasobów. Użyj tej opcji, aby uniemożliwić `_main` linkowi łączenie odwołania do biblioteki DLL.

### <a name="set-checksum"></a>Ustawianie sumy kontrolnej

Opcja [/RELEASE](release-set-the-checksum.md) ustawia sumę kontrolną w nagłówku pliku exe.

### <a name="base-address"></a>Adres podstawowy

Ustawia adres podstawowy programu. ([/BASE](base-base-address.md):{address\[,size] | @filename,key})

### <a name="randomized-base-address"></a>Randomizowany adres podstawowy

Randomizowanym adresem podstawowym. ([/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)\[:NO])

### <a name="fixed-base-address"></a>Stały adres podstawowy

Tworzy program, który można załadować tylko pod preferowanym adresem podstawowym. ([/FIXED](fixed-fixed-base-address.md)\[:NO])

### <a name="data-execution-prevention-dep"></a>Zapobieganie wykonywaniu danych (DEP)

Oznacza plik wykonywalny jako testowany jako zgodny z funkcją zapobiegania wykonywaniu danych systemu Windows. ([/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)\[:NO])

### <a name="turn-off-assembly-generation"></a>Wyłącz generowanie zespołu

Opcja [/NOASSEMBLY](noassembly-create-a-msil-module.md) informuje konsolidatora o utworzeniu obrazu dla bieżącego pliku wyjściowego bez zestawu .NET Framework.

### <a name="unload-delay-loaded-dll"></a>Opóźnienie rozładunku załadowanej biblioteki DLL

Moduł kwalifikator **UNLOAD** informuje funkcję pomocnika ładowania opóźnienia do obsługi jawnego zwalniania biblioteki DLL. ([/DELAY](delay-delay-load-import-settings.md):UNLOAD)

### <a name="nobind-delay-loaded-dll"></a>Opóźnienie nobind załadowany DLL

Kwalifikator **NOBIND** informuje konsolidatora, aby nie dołączał wiązania IAT do ostatecznego obrazu. Domyślnie jest utworzenie powiązania IAT dla bibliotek DLL załadowanych opóźnieniem. ([/DELAY](delay-delay-load-import-settings.md):NOBIND)

### <a name="import-library"></a>Importowanie biblioteki

Zastępuje domyślną nazwę biblioteki importu. ([/IMPLIB](implib-name-import-library.md):nazwa pliku)

### <a name="merge-sections"></a>Scalanie sekcji

Opcja [/MERGE](merge-combine-sections.md) łączy pierwszą sekcję (od) z drugą sekcją (do), nazywając wynikową sekcję. Na przykład /merge:.rdata=.text.

### <a name="target-machine"></a>Maszyna docelowa

Opcja [/MACHINE](machine-specify-target-platform.md) określa platformę docelową dla programu.

**Choices**

- **Nie ustawiono**
- **MachineARM (MaszynaARM)**
- **MachineARM64 (MaszynaARM64)**
- **MachineEBC (MachineEBC)**
- **MaszynaIA64**
- **MachineMIPS (MachineMIPS)**
- **MaszynaMIPS16**
- **MachineMIPSFPU**
- **MachineMIPSFPU16**
- **MachineSH4**
- **MachineTHUMB (MASZYNATHUMB)**
- **MaszynaX64**
- **MaszynaX86**

### <a name="profile"></a>Profil

Tworzy plik wyjściowy, który może być używany z profilera narzędzi wydajności. Wymaga GenerateDebugInformation (/[/DEBUG](debug-generate-debug-info.md)). ([/PROFIL](profile-performance-tools-profiler.md))

### <a name="clr-thread-attribute"></a>Atrybut wątku CLR

Jawnie określ atrybut wątków dla punktu wejścia programu CLR.

**Choices**

- **Atrybut wątków MTA** — stosuje atrybut MTAThreadAttribute do punktu wejścia programu.
- **Atrybut wątków STA** — stosuje atrybut STAThreadAttribute do punktu wejścia programu.
- **Domyślny atrybut wątków** — taki sam, jak nieokreślenie [pliku /CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md). Umożliwia wspólnemu językowi wykonawczemu (CLR) ustawienie domyślnego atrybutu wątkowania.

### <a name="clr-image-type"></a>Typ obrazu CLR

Ustawia typ (IJW, czysty lub bezpieczny) obrazu CLR.

**Choices**

- **Wymuszanie obrazu IJW**
- **Wymusz czysty obraz IL**
- **Wymusz bezpieczny obraz IL**
- **Domyślny typ obrazu**

### <a name="key-file"></a>Plik klucza

Określ parę kluczy lub klawiszy, aby podpisać zestaw. ([/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md):nazwa pliku)

### <a name="key-container"></a>Kontener kluczy

Określ kontener kluczy, aby podpisać zestaw. ([/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md):name)

### <a name="delay-sign"></a>Znak opóźnienia

Częściowo podpisać zespół. Użyj [/DELAYSIGN,](delaysign-partially-sign-an-assembly.md) jeśli chcesz umieścić tylko klucz publiczny w zestawie. Wartość domyślna to /DELAYSIGN:NO.

### <a name="clr-unmanaged-code-check"></a>Sprawdzanie kodu niezarządzanego przez CLR

[/CLRUNMANAGEDCODECHECK określa,](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md) czy konsolidator zastosuje SuppressUnmanagedCodeSecurityAttribute do wywołań PInvoke generowanych przez linkatora z kodu zarządzanego do natywnych bibliotek DLL.

### <a name="error-reporting"></a>Raportowanie błędów

Umożliwia podanie informacji o błędzie kompilatora wewnętrznego (ICE) bezpośrednio do zespołu języka Visual C++.

**Choices**

- **PromptImmediately** — monituj natychmiast.
- **Kolejka do następnego logowania** - Kolejka do następnego logowania.
- **Wyślij raport o błędach** — wyślij raport o błędzie.
- **Brak raportu o błędach** — brak raportu o błędach.

### <a name="sectionalignment"></a>Wyrównanie sekcji

Opcja [/ALIGN](align-section-alignment.md) określa wyrównanie każdej sekcji w liniowej przestrzeni adresowej programu. Argument liczby jest w bajtach i musi być potęgą dwóch.

### <a name="preserve-last-error-code-for-pinvoke-calls"></a>Zachowaj kod ostatniego błędu dla wywołań PInvoke

[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md), który jest domyślnie włączony, zachowuje ostatni kod błędu funkcji wywoływanych za pośrednictwem mechanizmu P/Invoke, który umożliwia wywoływanie funkcji natywnych w DLLS, z kodu skompilowanego z /clr.

**Choices**

- **Włączone** — włącz funkcję CLRSupportLastError.
- **Wyłączone** — wyłącznik CLRSupportLastError.
- **Tylko biblioteki Dll systemu** — włącz funkcję CLRSupportLastError tylko dla bibliotek DLL systemu.

### <a name="image-has-safe-exception-handlers"></a>Obraz ma bezpieczne programy obsługi wyjątków

Gdy [/SAFESEH](safeseh-image-has-safe-exception-handlers.md) jest określony, konsolidator będzie produkować tylko obraz, jeśli może również tworzyć tabelę programu obsługi wyjątków bezpiecznego obrazu. Ta tabela określa dla systemu operacyjnego, które programy obsługi wyjątków są prawidłowe dla obrazu.
