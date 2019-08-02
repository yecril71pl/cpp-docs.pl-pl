---
title: Strony właściwości konsolidatora
ms.date: 7/24/2019
ms.topic: article
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
ms.openlocfilehash: 17880d50ae012b640cb83f3766883ab2b1bcbe73
ms.sourcegitcommit: 7b039b5f32f6c59be6c6bb1cffafd69c3bfadd35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68537590"
---
# <a name="linker-property-pages"></a>Strony właściwości konsolidatora

W obszarze właściwości > **konfiguracji** > właściwościprojektukonsolidator znajduje się następujące właściwości. >  Aby uzyskać więcej informacji na temat konsolidatora, zobacz [CL wywołuje](cl-invokes-the-linker.md) opcje [](linker-options.md)konsolidatora i konsolidatora.

## <a name="general-property-page"></a>Ogólna strona właściwości

### <a name="output-file"></a>Plik wyjściowy

Opcja [/out](out-output-file-name.md) zastępuje domyślną nazwę i lokalizację programu tworzonego przez konsolidatora.

### <a name="show-progress"></a>Pokaż postęp

Drukuje wiadomości dotyczące postępu konsolidatora

**Decyzji**

- **Nie ustawiono** — brak szczegółowości.
- **Wyświetl wszystkie komunikaty** o postępie — wyświetla wszystkie komunikaty o postępie. 
- **W przypadku przeszukiwanych bibliotek** — wyświetla komunikaty o postępie wskazujące tylko przeszukiwane biblioteki.
- **Informacje o COMDAT składania podczas zoptymalizowanego łączenia** — wyświetla informacje na temat składania COMDAT podczas zoptymalizowanego łączenia.
- Informacje **o danych usuniętych podczas zoptymalizowanego łączenia** — wyświetla informacje o funkcjach i danych usuniętych podczas zoptymalizowanej konsolidacji.
- Informacje **o modułach niezgodnych z SEH** — wyświetla informacje o modułach niezgodnych z bezpieczną obsługą wyjątków.
- Informacje **o działaniu konsolidatora związanego z kodem zarządzanym** — wyświetlanie informacji na temat działania konsolidatora powiązanego z kodem zarządzanym.

### <a name="version"></a>Wersja

Opcja [/Version](version-version-information.md) nakazuje konsolidatorowi umieszczenie numeru wersji w nagłówku pliku. exe lub. dll. Użyj polecenia DUMPBIN/HEADERS, aby wyświetlić pole wersja obrazu OPCJONALNYch wartości nagłówka, aby zobaczyć efekt opcji **/Version**.

### <a name="enable-incremental-linking"></a>Włącz konsolidację przyrostową

Włącza łączenie przyrostowe. ([/INCREMENTAL](incremental-link-incrementally.md),/INCREMENTAL: NO)

### <a name="suppress-startup-banner"></a>Pomiń transparent startowy

Opcja [/nologo](nologo-suppress-startup-banner-linker.md) uniemożliwia wyświetlanie komunikatu o prawach autorskich i numeru wersji. 

### <a name="ignore-import-library"></a>Ignoruj bibliotekę importowaną

Ta właściwość nakazuje konsolidatorowi łączenie się z danymi wyjściowymi lib wygenerowanymi przez tę kompilację z dowolnym projektem zależnym. Dzięki temu system projektu może obsługiwać pliki .dll, które podczas kompilacji nie tworzą pliku .lib. Jeśli projekt jest zależny od innego projektu, który tworzy bibliotekę DLL, system projektu automatycznie łączy plik lib utworzony przez ten projekt podrzędny. Może to być niepotrzebne w projektach generujących pliki COM DLL lub pliki DLL z samymi zasobami, ponieważ te pliki DLL nie eksportują żadnych istotnych danych. Jeśli biblioteka DLL nie ma żadnych eksportów, konsolidator nie generuje pliku. lib. Jeśli na dysku nie ma pliku Export. lib, a system projektu nakazuje konsolidatorowi łączenie się z tą (brakującą) biblioteką DLL, łącze kończy się niepowodzeniem. Aby rozwiązać ten problem, użyj właściwości **Ignorowanie biblioteki importowanej** . W przypadku ustawienia **opcji tak**system projektu ignoruje obecność lub brak tego pliku. lib i powoduje, że każdy projekt, który zależy od tego projektu nie jest połączony z nieistniejącym plikiem. lib.

Aby programowo uzyskać dostęp do tej właściwości <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>, zobacz.

### <a name="register-output"></a>Rejestruj dane wyjściowe

Działa `regsvr32.exe /s $(TargetPath)` w danych wyjściowych kompilacji, które są prawidłowe tylko w projektach. dll. W projektach plików .exe właściwość jest ignorowana. Aby zarejestrować dane wyjściowe pliku. exe, należy ustawić zdarzenie postbuild w konfiguracji, aby wykonać rejestrację niestandardową, która jest zawsze wymagana dla zarejestrowanych plików. exe.

Aby programowo uzyskać dostęp do tej właściwości <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>, zobacz.

### <a name="per-user-redirection"></a>Przekierowanie na użytkownika

Rejestracja w programie Visual Studio tradycyjnie zakończyła się w KLUCZu HKEY_CLASSES_ROOT (HKCR). W systemach operacyjnych Windows Vista i nowszych w celu uzyskania dostępu do HKCR należy uruchomić program Visual Studio w trybie podniesionych uprawnień. Deweloperzy nie zawsze chcą pracować w trybie podwyższonych uprawnień, a mimo to muszą dokonywać rejestracji. Przekierowanie na użytkownika umożliwia rejestrowanie bez konieczności pracy w tym trybie.

Przekierowanie na użytkownika wymusza przekierowanie wszystkich zapisów do HKCR do HKEY\_bieżącego\_użytkownika (HKCU). Jeśli przekierowanie na użytkownika jest wyłączone, może to spowodować [błąd PRJ0050 kompilacji projektu](../../error-messages/tool-errors/project-build-error-prj0050.md) , gdy program próbuje wykonać zapis do HKCR.

### <a name="additional-library-directories"></a>Dodatkowe katalogi biblioteki

Zezwala użytkownikowi na przesłanianie ścieżki biblioteki środowiskowej. ([/LIBPATH](libpath-additional-libpath.md): folder)

### <a name="link-library-dependencies"></a>Połącz zależności biblioteki

Określa, czy mają być połączone pliki. lib, które są tworzone przez projekty zależne. Zazwyczaj chcesz połączyć w plikach lib, ale może to nie być przypadek niektórych bibliotek DLL.

Można również określić plik. obj, podając nazwę pliku i ścieżkę względną, na przykład ".. \\.. \MyLibProject\MyObjFile.obj". Jeśli kod źródłowy dla pliku. obj #includes prekompilowanego nagłówka, na przykład PCH. h, plik PCH. obj znajduje się w tym samym folderze co MyObjFile. obj i należy również dodać PCH. obj jako dodatkową zależność.

### <a name="use-library-dependency-inputs"></a>Użyj danych wejściowych zależności biblioteki

Określa, czy dane wejściowe narzędzia bibliotekarza są używane zamiast pliku biblioteki podczas łączenia w danych wyjściowych biblioteki zależności projektu. W dużym projekcie, gdy projekt zależny tworzy plik .lib, łączenie przyrostowe jest wyłączone. Jeśli istnieje wiele projektów zależnych generujących pliki .lib, kompilowanie aplikacji może trwać długo. Gdy ta właściwość ma wartość **Yes (tak**), system projektu łączy w plikach. obj dla. libs utworzonych przez projekty zależne, co umożliwia łączenie przyrostowe.

Aby uzyskać informacje na temat uzyskiwania dostępu do strony właściwości **Ogólne** konsolidatora, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

### <a name="link-status"></a>Stan łącza

Określa, czy konsolidator powinien wyświetlać wskaźnik postępu pokazujący, jaki procent łącza został ukończony. Wartość domyślna to nie wyświetlaj informacji o stanie. ([/LTCG](ltcg-link-time-code-generation.md): STATUS | LTCG: NOSTATUS)

### <a name="prevent-dll-binding"></a>Zapobiegaj powiązaniu biblioteki DLL

[/ALLOWBIND](allowbind-prevent-dll-binding.md): No ustawia bit w nagłówku dll, który wskazuje na powiązanie. exe, że obraz nie może być powiązany. Nie ma potrzeby powiązania DLL, jeśli został podpisany cyfrowo (powiązanie unieważnia sygnaturę).

### <a name="treat-linker-warning-as-errors"></a>Traktuj ostrzeżenia konsolidatora jako błędy

[/WX](wx-treat-linker-warnings-as-errors.md) powoduje, że plik wyjściowy nie zostanie wygenerowany, jeśli konsolidator generuje ostrzeżenie.

### <a name="force-file-output"></a>Wymuś dane wyjściowe pliku

Opcja [/Force](force-force-file-output.md) nakazuje konsolidatorowi utworzenie pliku. exe lub DLL nawet wtedy, gdy odwołanie do symbolu jest przywoływane, ale nie zdefiniowane lub jest zdefiniowane wielokrotnie. Może utworzyć nieprawidłowy plik. exe.

**Decyzji**

- **Funkcja Enabled** -/Force bez argumentów oznacza zarówno wielokrotne, jak i nierozwiązane.
- **Wielokrotnie zdefiniowany tylko symbol** — Użyj/Force: Multiple, aby utworzyć plik wyjściowy, niezależnie od tego, czy link znajduje więcej niż jedną definicję symbolu.
- **Tylko niezdefiniowany symbol** — Użyj/Force: nierozpoznany do utworzenia pliku wyjściowego, niezależnie od tego, czy link znajdzie niezdefiniowany symbol. /FORCE: nierozpoznany jest ignorowany, jeśli symbol punktu wejścia nie został rozpoznany.

### <a name="create-hot-patchable-image"></a>Tworzenie obrazu z poprawkami grzewczymi

Przygotowuje obraz do poprawiania.

**Decyzji**

- **Włączone** — przygotowuje obraz do poprawiania.
- **Tylko obraz x86** — przygotowuje obraz x86 na potrzeby funkcji HotPatching.
- **Tylko obraz x64** — przygotowuje obraz x64 na potrzeby funkcji HotPatching.
- **Tylko obraz Itanium** — przygotowuje obraz Itanium na potrzeby funkcji HotPatching.

### <a name="specify-section-attributes"></a>Określ atrybuty sekcji

Opcja [/Section](section-specify-section-attributes.md) zmienia atrybuty sekcji, zastępując atrybuty ustawione, gdy plik. obj sekcji został skompilowany.

## <a name="input-property-page"></a>Strona właściwości danych wejściowych

### <a name="additional-dependencies"></a>{1&gt;Dodatkowe zależności&lt;1}

Określa dodatkowe elementy do dodania do wiersza polecenia linku, na przykład *Kernel32. lib*.

### <a name="ignore-all-default-libraries"></a>Ignoruj wszystkie biblioteki domyślne

Opcja [/NODEFAULTLIB](nodefaultlib-ignore-libraries.md) informuje konsolidator, aby usunął co najmniej jedną domyślną bibliotekę z listy bibliotek przeszukiwanych podczas rozpoznawania odwołań zewnętrznych. 

### <a name="ignore-specific-default-libraries"></a>Ignoruj określone biblioteki domyślne

Określa co najmniej jedną nazwę bibliotek domyślnych do zignorowania; Rozdziel wiele bibliotek średnikami. (/NODEFAULTLIB: [nazwa, nazwa,...])

### <a name="module-definition-file"></a>Plik definicji modułu

Opcja [/def](def-specify-module-definition-file.md) przekazuje plik definicji modułu (. def) do konsolidatora. Tylko jeden plik. def może być określony do łączenia. 

### <a name="add-module-to-assembly"></a>Dodaj moduł do zestawu

Opcja [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md) umożliwia dodanie odwołania modułu do zestawu. Informacje o typie w module nie będą dostępne dla programu zestawu, który dodał odwołanie do modułu. Jednak informacje o typie w module będą dostępne dla każdego programu, który odwołuje się do zestawu.

### <a name="embed-managed-resource-file"></a>Osadź zarządzany plik zasobów

[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) osadza plik zasobów w pliku wyjściowym.

### <a name="force-symbol-references"></a>Wymuszaj odwołania do symboli

Opcja [/include](include-force-symbol-references.md) informuje konsolidator, aby dodał określony symbol do tabeli symboli.

### <a name="delay-loaded-dlls"></a>Opóźnienie załadowanych bibliotek DLL

Opcja [/DELAYLOAD](delayload-delay-load-import.md) powoduje opóźnione ładowanie bibliotek DLL. Nazwa biblioteki DLL określa plik DLL, aby opóźnić ładowanie. 

### <a name="assembly-link-resource"></a>Zasób linku zestawu

Opcja [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md) tworzy łącze do zasobu .NET Framework w pliku wyjściowym; plik zasobu nie jest umieszczany w pliku wyjściowym.

## <a name="manifest-file-property-page"></a>Strona właściwości pliku manifestu

### <a name="generate-manifest"></a>Generuj manifest

[/Manifest](manifest-create-side-by-side-assembly-manifest.md) określa, że konsolidator powinien utworzyć plik manifestu obok siebie.

### <a name="manifest-file"></a>Plik manifestu

[/MANIFESTFILE](manifestfile-name-manifest-file.md) pozwala zmienić domyślną nazwę pliku manifestu. Domyślną nazwą pliku manifestu jest nazwa pliku z dołączonym manifestem.

### <a name="additional-manifest-dependencies"></a>Dodatkowe zależności manifestu

[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md) umożliwia określenie atrybutów, które zostaną umieszczone w sekcji zależności pliku manifestu.

### <a name="allow-isolation"></a>Zezwalaj na izolację

Określa zachowanie wyszukiwania manifestu. ([/ALLOWISOLATION](allowisolation-manifest-lookup.md): NO)

### <a name="enable-user-account-control-uac"></a>Włącz kontrolę konta użytkownika (UAC)

Określa, czy kontrola konta użytkownika jest włączona.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md),/MANIFESTUAC: NO)

### <a name="uac-execution-level"></a>Poziom wykonywania kontroli konta użytkownika

Określa żądany poziom wykonywania aplikacji podczas uruchamiania z kontrolą konta użytkownika.  (/MANIFESTUAC: Level = [wartość])

**Decyzji**

- **jako źródło** — poziom wykonywania kontroli konta użytkownika: jako źródło.
- **najwyższe dostępne** — poziom wykonywania kontroli konta użytkownika: najwyższy dostępny.
- **wymaga administratora** — poziom wykonywania kontroli konta użytkownika: wymaga administratora.

### <a name="uac-bypass-ui-protection"></a>Ignorowanie ochrony interfejsu użytkownika funkcji Kontrola konta użytkownika

Określa, czy obejść poziomy ochrony interfejsu użytkownika dla innych okien na pulpicie.  Ustaw tę właściwość na wartość "tak" tylko dla aplikacji ułatwień dostępu.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md): UIAccess = [true | false])

## <a name="debugging-property-page"></a>Strona właściwości debugowania

### <a name="generate-debug-info"></a>Generuj informacje o debugowaniu

Ta opcja umożliwia tworzenie informacji debugowania dla pliku exe lub DLL.

**Decyzji**

- **Nie** — nie tworzy informacji o debugowaniu.
- **Generuj informacje o debugowaniu** — Utwórz kompletną bazę danych programu (PDB) idealny do dystrybucji na serwerze symboli firmy Microsoft.
- **Generuj informacje o debugowaniu zoptymalizowane pod kątem szybszych linków** — tworzy bazę danych programu (PDB) idealną dla cyklu Edit-link-Debug. 
- **Generuj informacje o debugowaniu zoptymalizowane pod kątem udostępniania i publikowania** — tworzy bazę danych programu (PDB) idealną dla cyklu Edit-link-Debug. 

### <a name="generate-program-database-file"></a>Generuj plik bazy danych programu

Domyślnie, gdy wartość [/Debug](debug-generate-debug-info.md) jest określona, konsolidator tworzy bazę danych programu (PDB), która przechowuje informacje debugowania. Domyślna nazwa pliku PDB ma nazwę podstawową programu i rozszerzenie. pdb.

### <a name="strip-private-symbols"></a>Osobiste symbole paska

Opcja [/PDBSTRIPPED](pdbstripped-strip-private-symbols.md) tworzy drugi plik bazy danych (PDB) podczas kompilowania obrazu programu przy użyciu dowolnego z opcji kompilatora lub konsolidatora, które generują plik PDB (/Debug,/Z7,/ZD lub/ZI).

### <a name="generate-map-file"></a>Generuj plik mapy

Opcja [/map](map-generate-mapfile.md) informuje konsolidator, aby utworzył mapfile.

### <a name="map-file-name"></a>Nazwa pliku mapy

Określona przez użytkownika nazwa mapfile. Zastępuje domyślną nazwę.

### <a name="map-exports"></a>Eksporty mapy

Opcja [/MapInfo](mapinfo-include-information-in-mapfile.md) nakazuje konsolidatorowi dołączenie określonych informacji do Mapfile, który jest tworzony w przypadku określenia opcji/map. EKSPORTy nakazuje konsolidatorowi uwzględnienie wyeksportowanych funkcji.

### <a name="debuggable-assembly"></a>Zestaw możliwością debugowania

[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md) emituje atrybut DebuggableAttribute z śledzeniem informacji debugowania i wyłącza optymalizacje JIT.

## <a name="system-property-page"></a>Strona właściwości systemu

### <a name="subsystem"></a>Wykonawc

Opcja [/Subsystem](subsystem-specify-subsystem.md) informuje system operacyjny, jak uruchomić plik. exe. Wybór podsystemu wpływa na symbol punktu wejścia (lub funkcję punktu wejścia), który zostanie wybrany przez konsolidator.

**Decyzji**

- **Nie ustawiono** — nie ustawiono podsystemu.
- Aplikacja w trybie znakowym w systemie Win32. Aplikacje konsolowe uzyskują konsolę przez system operacyjny. Jeśli jest zdefiniowany główny lub wmain, konsola jest wartością domyślną.
- **Windows** -aplikacja nie wymaga konsoli, prawdopodobnie dlatego, że tworzy własne okna do interakcji z użytkownikiem. Jeśli zdefiniowano WinMain lub wWinMain, System WINDOWS jest wartością domyślną.
- Sterowniki urządzeń natywnych dla systemu Windows NT. Jeśli jest określony wartość parametru//lub, natywny jest tryb macierzysty.
- Aplikacja **EFI Application** -EFI.
- **Sterownik usługi rozruchu EFI** — sterownik usługi rozruchu interfejsu EFI.
- **EFI ROM** -EFI ROM.
- **Środowisko uruchomieniowe EFI** — środowisko uruchomieniowe EFI.
- **POSIX** — aplikacja uruchamiana z podsystemem POSIX w systemie Windows NT.

### <a name="minimum-required-version"></a>Minimalna wymagana wersja

Określ minimalną wymaganą wersję podsystemu. Argumenty są liczbami dziesiętnymi z zakresu od 0 do 65 535.

### <a name="heap-reserve-size"></a>Rozmiar rezerwy sterty

Określa całkowity rozmiar sterty w pamięci wirtualnej. Wartość domyślna to 1 MB.    ([/Heap](heap-set-heap-size.md): Reserve)

### <a name="heap-commit-size"></a>Rozmiar zatwierdzenia sterty

Określa całkowity rozmiar sterty w pamięci fizycznej. Wartość domyślna to 4 KB.    ([/Heap](heap-set-heap-size.md): Reserve, commit)

### <a name="stack-reserve-size"></a>Rozmiar rezerwy stosu

Określa całkowity rozmiar alokacji stosu w pamięci wirtualnej. Wartość domyślna to 1 MB.     ([/Stack](stack-stack-allocations.md): Reserve)

### <a name="stack-commit-size"></a>Rozmiar zatwierdzenia stosu

Określa całkowity rozmiar alokacji stosu w pamięci fizycznej. Wartość domyślna to 4 KB.     ([/Stack](stack-stack-allocations.md): Reserve, commit)

### <a name="enable-large-addresses"></a>Włącz duże adresy

Opcja [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md) informuje konsolidator, że aplikacja może obsłużyć adresy większe niż 2 gigabajty. Domyślnie/LARGEADDRESSAWARE: nie jest włączone, jeśli w linii konsolidatora nie określono/LARGEADDRESSAWARE.

### <a name="terminal-server"></a>Serwer terminali

Opcja [/TSAWARE](tsaware-create-terminal-server-aware-application.md) ustawia flagę w polu IMAGE_OPTIONAL_HEADER DllCharacteristics w opcjonalnym nagłówku obrazu programu. Po ustawieniu tej flagi serwer terminali nie wprowadza pewnych zmian do aplikacji.

### <a name="swap-run-from-cd"></a>Zamień przebieg z dysku CD

Opcja [/SWAPRUN](swaprun-load-linker-output-to-swap-file.md) informuje system operacyjny, aby najpierw skopiował dane wyjściowe konsolidatora do pliku wymiany, a następnie uruchomił obraz stamtąd. Jest to funkcja systemu Windows NT 4,0 (i nowszych). Gdy jest określony **dysk CD** , system operacyjny skopiuje obraz na dysk wymienny do pliku stronicowania, a następnie załaduje go.

### <a name="swap-run-from-network"></a>Zamień przebieg z sieci

Opcja [/SWAPRUN](swaprun-load-linker-output-to-swap-file.md) informuje system operacyjny, aby najpierw skopiował dane wyjściowe konsolidatora do pliku wymiany, a następnie uruchomił obraz stamtąd. Jest to funkcja systemu Windows NT 4,0 (i nowszych). Jeśli zostanie określona wartość **net** , system operacyjny najpierw skopiuje obraz binarny z sieci do pliku wymiany i załaduje go stamtąd. Ta opcja jest przydatna do uruchamiania aplikacji za pośrednictwem sieci.

### <a name="driver"></a>Sterownik

Aby skompilować sterownik trybu jądra systemu Windows NT, użyj opcji [/konsolidatora](driver-windows-nt-kernel-mode-driver.md) .

**Decyzji**

- **Nie ustawiono** domyślnego ustawienia sterownika.
- Sterownik **-Sterownik**
- **Tylko** do-///-//-/-//-tylko: powoduje, że KONSOLIDATOR dodaje IMAGE_FILE_UP_SYSTEM_ONLY bit do charakterystyki w nagłówku danych wyjściowych, aby określić, że jest to sterownik jednoprocesorowy. System operacyjny odmówi załadowania sterownika w systemie wieloprocesorowym (MP).
- **WDM** -IMAGE_DLLCHARACTERISTICS_WDM_DRIVER: WDM powoduje, że konsolidator ustawia bit w polu DLLCHARACTERISTICS opcjonalnego nagłówka.

## <a name="optimization-property-page"></a>Strona właściwości optymalizacji

### <a name="references"></a>Odwołania

[/Opt](opt-optimizations.md): ref eliminuje funkcje i/lub dane, które nigdy nie są przywoływane, podczas gdy/OPT: NOREF utrzymuje funkcje i/lub dane, które nigdy nie są przywoływane. 

### <a name="enable-comdat-folding"></a>Włącz zwijanie COMDAT

Użyj [/opt](opt-optimizations.md): ICF\[= iteracje], aby wykonać identyczne składanie COMDAT. 

### <a name="function-order"></a>Kolejność funkcji

Opcja [/Order](order-put-functions-in-order.md)informuje link, aby zoptymalizować program przez umieszczenie niektórych COMDAT w obrazie we wstępnie określonej kolejności. LINK umieszcza funkcje w określonej kolejności w poszczególnych sekcjach obrazu.

### <a name="profile-guided-database"></a>Baza danych z przewodnikiem

Określ plik PGD dla optymalizacji profilowanej. ([/PGD](pgd-specify-database-for-profile-guided-optimizations.md))

### <a name="link-time-code-generation"></a>Generowanie kodu w czasie konsolidacji

Określa generowanie kodu w czasie konsolidacji. ([/LTCG](ltcg-link-time-code-generation.md))

**Decyzji**

- **Domyślne** — domyślne ustawienie LTCG.
- **Użyj szybkiego generowania kodu w czasie konsolidacji** — Użyj generowania kodu w czasie konsolidacji przy użyciu [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md).
- **Użyj generowania kodu w czasie konsolidacji** — Użyj [generowania kodu w czasie konsolidacji](ltcg-link-time-code-generation.md).
- **Optymalizacja z przewodnikiem —** Optymalizacja profilu z [przewodnikiem](../profile-guided-optimizations.md) z użyciem:P ginstrument.
- **Optymalizacja profilowa — Optymalizacja** — określa, że konsolidator powinien użyć danych profilu utworzonych po uruchomieniu pliku binarnego instrumentacji do utworzenia zoptymalizowanego obrazu.
- **Optymalizacja profilowa-Update** -umożliwia i śledzi listę plików wejściowych do dodania lub zmodyfikowania z co zostało określone w fazie:P ginstrument.

## <a name="embedded-idl-property-page"></a>Strona właściwości osadzonego IDL

### <a name="midl-commands"></a>Polecenia MIDL

Określ opcje wiersza polecenia MIDL. ([/MIDL](midl-specify-midl-command-line-options.md):@responsefile)

### <a name="ignore-embedded-idl"></a>Ignoruj osadzone IDL

Opcja [/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md) określa, że żadne atrybuty IDL w kodzie źródłowym nie powinny być przetwarzane do pliku. idl.

### <a name="merged-idl-base-file-name"></a>Nazwa pliku bazowego Scaled IDL

Opcja [/IDLOUT](idlout-name-midl-output-files.md) określa nazwę i rozszerzenie pliku. idl.

### <a name="type-library"></a>Biblioteka typów

Opcja [/TLBOUT](tlbout-name-dot-tlb-file.md) określa nazwę i rozszerzenie pliku. tlb.

### <a name="typelib-resource-id"></a>Identyfikator zasobu biblioteki typów

Pozwala określić identyfikator zasobu biblioteki typów generowanych przez konsolidator. ([/TLBID](tlbid-specify-resource-id-for-typelib.md): ID)

## <a name="windows-metadata-property-page"></a>Strona właściwości metadanych systemu Windows

### <a name="generate-windows-metadata"></a>Generuj metadane systemu Windows

Włącza lub wyłącza generowanie metadanych systemu Windows.

**Decyzji**

- **Tak** — Włącz generowanie plików metadanych systemu Windows.
- **Nie** — Wyłącz generowanie plików metadanych systemu Windows.

### <a name="windows-metadata-file"></a>Plik metadanych systemu Windows

Przełącznik opcji [/WINMDFILE](winmdfile-specify-winmd-file.md) .

### <a name="windows-metadata-key-file"></a>Plik klucza metadanych systemu Windows

Określ klucz lub parę kluczy, aby podpisać metadane systemu Windows. ([/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md): filename)

### <a name="windows-metadata-key-container"></a>Kontener klucza metadanych systemu Windows

Określ kontener klucza do podpisania metadanych systemu Windows. ([/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md): nazwa)

### <a name="windows-metadata-delay-sign"></a>Znak opóźnienia metadanych systemu Windows

Częściowo podpisz metadane systemu Windows. Użyj [/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md) , jeśli chcesz umieścić klucz publiczny w metadanych systemu Windows. Wartość domyślna to/WINMDDELAYSIGN: NO.

## <a name="advanced-property-page"></a>Zaawansowana Strona właściwości

### <a name="entry-point"></a>Punkt wejścia

Opcja [/entry](entry-entry-point-symbol.md) określa funkcję punktu wejścia jako adres początkowy dla pliku. exe lub dll.

### <a name="no-entry-point"></a>Brak punktu wejścia

Opcja [/NOENTRY](noentry-no-entry-point.md)jest wymagana do utworzenia biblioteki DLL tylko dla zasobów. Użyj tej opcji, aby zapobiec łączeniu łącza z odwołaniem `_main` do biblioteki DLL.

### <a name="set-checksum"></a>Ustaw sumę kontrolną

Opcja [/Release](release-set-the-checksum.md) ustawia sumę kontrolną w nagłówku pliku. exe.

### <a name="base-address"></a>Adres podstawowy

Ustawia adres podstawowy dla programu. ([/Base](base-base-address.md): {Address\[, size] | @filename, klucz})

### <a name="randomized-base-address"></a>Losowy adres podstawowy

Losowy adres podstawowy. ([/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)\[: NO])

### <a name="fixed-base-address"></a>Stały adres podstawowy

Tworzy program, który można załadować tylko przy użyciu preferowanego adresu podstawowego. ([/FIXED](fixed-fixed-base-address.md)\[: NO])

### <a name="data-execution-prevention-dep"></a>Zapobieganie wykonywaniu danych (DEP)

Oznacza plik wykonywalny, który został przetestowany pod kątem zgodności z funkcją zapobiegania wykonywaniu danych systemu Windows. ([/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)\[: NO])

### <a name="turn-off-assembly-generation"></a>Wyłącz generowanie zestawu

Opcja [/NOASSEMBLY](noassembly-create-a-msil-module.md) informuje konsolidator, aby utworzył obraz dla bieżącego pliku wyjściowego bez zestawu .NET Framework.

### <a name="unload-delay-loaded-dll"></a>Ładowanie biblioteki DLL z opóźnieniem

Kwalifikator **Unload** informuje funkcję pomocnika ładowania opóźnień, aby obsługiwała jawne zwolnienie biblioteki DLL. ([/DELAY](delay-delay-load-import-settings.md): UNLOAD)

### <a name="nobind-delay-loaded-dll"></a>Biblioteka DLL załadowanej z opóźnieniem NOBIND

Kwalifikator **NOBIND** informuje konsolidator, aby nie zawierał IAT możliwego do powiązania w końcowym obrazie. Wartość domyślna to utworzenie IAT możliwego do powiązania dla bibliotek DLL ładowanych z opóźnieniem. ([/DELAY](delay-delay-load-import-settings.md): NOBIND)

### <a name="import-library"></a>Importuj bibliotekę

Zastępuje domyślną nazwę biblioteki importu. ([/IMPLIB](implib-name-import-library.md): filename)

### <a name="merge-sections"></a>Scal sekcje

Opcja [/merge](merge-combine-sections.md) łączy pierwszą sekcję (od) z drugą sekcją (do), nazywaną sekcją. Na przykład,/MERGE:. RDATA =. Text.

### <a name="target-machine"></a>Maszyna docelowa

Opcja [/Machine](machine-specify-target-platform.md) określa docelową platformę dla programu.

**Decyzji**

- **Nie ustawiono**
- **MachineARM**
- **MachineARM64**
- **MachineEBC**
- **MachineIA64**
- **MachineMIPS**
- **MachineMIPS16**
- **MachineMIPSFPU**
- **MachineMIPSFPU16**
- **MachineSH4**
- **MachineTHUMB**
- **MachineX64**
- **MachineX86**

### <a name="profile"></a>Profil

Tworzy plik wyjściowy, który może być używany z profilerem narzędzi wydajności. Wymaga ustawienia GenerateDebugInformation (/[/Debug](debug-generate-debug-info.md)). ([/PROFILE](profile-performance-tools-profiler.md))

### <a name="clr-thread-attribute"></a>Atrybut wątku CLR

Jawnie określ atrybut wątkowości dla punktu wejścia programu CLR.

**Decyzji**

- **Atrybut wątkowości MTA** — stosuje atrybut MTAThreadAttribute do punktu wejścia programu.
- **Atrybut wątkowości sta** — stosuje atrybut STAThreadAttribute do punktu wejścia programu.
- **Domyślny atrybut wątkowości** — taki sam jak nieokreślający [/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md). Umożliwia ustawienie domyślnego atrybutu Threading środowiska uruchomieniowego języka wspólnego (CLR).

### <a name="clr-image-type"></a>Typ obrazu CLR

Ustawia typ (IJW, czysty lub bezpieczny) obrazu CLR.

**Decyzji**

- **Wymuszaj obraz IJW**
- **Wymuszaj czysty obraz IL**
- **Wymuś bezpieczny obraz IL**
- **Domyślny typ obrazu**

### <a name="key-file"></a>Plik klucza

Określ klucz lub parę kluczy, aby podpisać zestaw. ([/KeyFile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md): filename)

### <a name="key-container"></a>Kontener kluczy

Określ kontener klucza do podpisania zestawu. ([/Keycontainer](keycontainer-specify-a-key-container-to-sign-an-assembly.md): nazwa)

### <a name="delay-sign"></a>Opóźnij znak

Częściowo podpisz zestaw. Użyj [/delaysign](delaysign-partially-sign-an-assembly.md) , jeśli chcesz umieścić klucz publiczny w zestawie. Wartość domyślna to/DELAYSIGN: NO.

### <a name="clr-unmanaged-code-check"></a>Sprawdzanie kodu niezarządzanego CLR

[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md) określa, czy konsolidator będzie stosować SuppressUnmanagedCodeSecurityAttribute do wywołań funkcji PInvoke generowanych przez konsolidator z kodu zarządzanego do natywnych bibliotek DLL.

### <a name="error-reporting"></a>Raportowanie błędów

Umożliwia dostarczenie informacji o wewnętrznym błędzie kompilatora (lodem) bezpośrednio do zespołu wizualnego C++ .

**Decyzji**

- **Monituj bezzwłocznie** .
- **Kolejka dla następnego** zalogowania do kolejki logowania.
- **Wyślij raport o błędach** — Wyślij raport o błędach.
- **Brak raportu o błędach** — raport o błędach.

### <a name="sectionalignment"></a>Wyrównanie sekcji

Opcja [/align](align-section-alignment.md) określa wyrównanie każdej sekcji w liniowej przestrzeni adresowej programu. Argument Number jest w bajtach i musi być potęgą liczby 2.

### <a name="preserve-last-error-code-for-pinvoke-calls"></a>Zachowaj kod ostatniego błędu dla wywołań PInvoke

[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md), która domyślnie jest włączona, zachowuje ostatni kod błędu funkcji wywoływanych za pośrednictwem mechanizmu P/Invoke, który umożliwia wywoływanie natywnych funkcji w bibliotekach DLL, z kodu skompilowanego za pomocą/CLR.

**Decyzji**

- **Włączone** — Włącz CLRSupportLastError.
- **Wyłączone** — Wyłącz CLRSupportLastError.
- **Tylko systemowe biblioteki DLL** — Włącz CLRSupportLastError tylko dla bibliotek DLL systemu.

### <a name="image-has-safe-exception-handlers"></a>Obraz ma bezpieczne procedury obsługi wyjątków

Gdy [/SAFESEH](safeseh-image-has-safe-exception-handlers.md) jest określony, konsolidator będzie generować tylko obraz, jeśli może również generować tabelę obsługi wyjątków bezpiecznego obrazu. Ta tabela określa dla systemu operacyjnego, które programy obsługi wyjątków są prawidłowe dla obrazu.
