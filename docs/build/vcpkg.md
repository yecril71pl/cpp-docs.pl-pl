---
title: 'vcpkg: Menedżer pakietów języka C++ dla systemów Windows, Linux i macOS'
description: vcpkg to Menedżer pakietów wiersza polecenia, który znacznie upraszcza pozyskiwanie i instalację bibliotek języka C++ typu open source w systemach Windows, macOS i Linux.
ms.date: 07/06/2020
ms.technology: cpp-ide
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.openlocfilehash: 7131f301a22b2834b04ef932f3cee426b04dc7e5
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373635"
---
# <a name="vcpkg-a-c-package-manager-for-windows-linux-and-macos"></a>vcpkg: Menedżer pakietów języka C++ dla systemów Windows, Linux i macOS

vcpkg to Menedżer pakietów wiersza polecenia dla języka C++. Znacznie upraszcza to pozyskiwanie i instalację bibliotek innych firm w systemach Windows, Linux i macOS. Jeśli projekt korzysta z bibliotek innych firm, zaleca się zainstalowanie ich przy użyciu programu vcpkg. vcpkg obsługuje zarówno biblioteki Open Source, jak i zastrzeżone. Wszystkie biblioteki w wykazie systemu Windows vcpkg zostały przetestowane pod kątem zgodności z programem Visual Studio 2015, Visual Studio 2017 i Visual Studio 2019. Między katalogami systemów Windows i Linux/macOS program vcpkg obsługuje teraz ponad 1900 bibliotek. Społeczność języka C++ jednocześnie dodaje więcej bibliotek do obu wykazów.

## <a name="simple-yet-flexible"></a>Proste jeszcze elastyczne

Za pomocą jednego polecenia można pobrać źródła i utworzyć bibliotekę. vcpkg jest samym projektem "open source", który jest dostępny w witrynie GitHub. Istnieje możliwość dostosowania prywatnych klonów vcpkg w dowolny sposób. Na przykład określ różne biblioteki lub różne wersje bibliotek niż te, które znajdują się w wykazie publicznym. Na jednej maszynie można mieć wiele klonów vcpkg. Każdy z nich może być ustawiony do tworzenia niestandardowej kolekcji bibliotek z preferowanymi przełącznikami kompilacji. Każdy klon jest środowiskiem niezależnym z własną kopią vcpkg.exe, która działa tylko w odniesieniu do własnej hierarchii. vcpkg nie jest dodawany do żadnych zmiennych środowiskowych i nie ma zależności w rejestrze systemu Windows ani w programie Visual Studio.

## <a name="sources-not-binaries"></a>Źródła, nie pliki binarne

W przypadku bibliotek w wykazie systemu Windows vcpkg pobiera źródła zamiast plików binarnych<sup>1</sup>. Kompiluje te źródła przy użyciu najnowszej wersji programu Visual Studio, którą może znaleźć. W języku C++ należy pamiętać, że zarówno kod aplikacji, jak i wszystkie używane biblioteki są kompilowane przez ten sam kompilator i wersję kompilatora. Za pomocą vcpkg, eliminujesz lub co najmniej znacznie zmniejszasz potencjalną niezgodność plików binarnych i problemy, które mogą być przyczyną. W zespołach, które są ustandaryzowane w określonej wersji kompilatora, jeden członek zespołu może używać vcpkg do pobierania źródeł i kompilowania zestawu plików binarnych. Następnie mogą użyć polecenia eksportu, aby uzupełnić dane binarne i nagłówki dla innych członków zespołu. Aby uzyskać więcej informacji, zobacz [Eksportuj skompilowane pliki binarne i nagłówki](#export_binaries_per_project) poniżej.

Można również utworzyć klon vcpkg z bibliotekami prywatnymi w kolekcji ports. Dodaj port, który pobiera wstępnie skompilowane pliki binarne i nagłówki. Następnie napisz plik *Portfile. CMAKE* , który po prostu kopiuje te pliki do preferowanej lokalizacji.

<sup>1</sup> *Uwaga: źródła są niedostępne dla niektórych bibliotek własnościowych. W takich przypadkach vcpkg pobiera zgodne ze wstępnie skompilowanych plików binarnych.*

## <a name="installation"></a>Instalacja

Klonuj repozytorium vcpkg z usługi GitHub: [https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg) . Możesz pobrać do dowolnej preferowanej lokalizacji folderów. Ta lokalizacja jest *katalogiem głównym*vcpkg. Po zakończeniu pobierania przejdź do tego katalogu w powłoce poleceń.

W katalogu głównym vcpkg Uruchom program inicjujący vcpkg:

- **`bootstrap-vcpkg.bat`** Systemy
- **`./bootstrap-vcpkg.sh`**(Linux, macOS)

W systemie Linux lub macOS może być konieczne odtworzenie prefiksu poleceń vcpkg przy użyciu **`./`** w następujących przykładach. Pamiętaj, aby uruchomić te polecenia w katalogu głównym vcpkg.

## <a name="search-the-list-of-available-libraries"></a>Przeszukaj listę dostępnych bibliotek

Aby zobaczyć, jakie pakiety są dostępne, wpisz **`vcpkg search`** w wierszu polecenia.

To polecenie wylicza pliki kontrolki w podfolderach *vcpkg/Ports* . Zobaczysz listę w następujący sposób:

```cmd
ace       6.4.3   The ADAPTIVE Communication Environment
anax      2.1.0-1 An open source C++ entity system. \<https://github...
antlr4    4.6-1   ANother Tool for Language Recognition
apr       1.5.2   The Apache Portable Runtime (APR) is a C library ...
asio      1.10.8  Asio is a cross-platform C++ library for network ...
assimp    3.3.1   The Open Asset import library
atk       2.24.0  GNOME Accessibility Toolkit
...
```

Można filtrować według wzorca, na przykład **`vcpkg search ta`** :

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-local-machine"></a>Instalowanie biblioteki na komputerze lokalnym

Po otrzymaniu nazwy biblioteki przy użyciu programu **`vcpkg search`** można **`vcpkg install`** pobrać bibliotekę i skompilować ją. vcpkg używa biblioteki Portfile w katalogu *portów* . Jeśli tryplet nie jest określony, vcpkg instaluje i kompiluje dla domyślnego tryplet dla platformy docelowej: x86-Windows, x64-Linux. CMAKE lub x64-OSX. CMAKE.

W przypadku bibliotek systemu Linux vcpkg zależy od instalacji programu na komputerze lokalnym. W macOS, vcpkg używa Clang.

Gdy Portfile określa zależności, vcpkg pobiera i instaluje je. Po pobraniu vcpkg kompiluje bibliotekę przy użyciu tego samego systemu kompilacji, w którym jest używana biblioteka. Projekty programu MSBuild CMake i (w systemie Windows) są preferowane, ale jest obsługiwane wraz z jakimkolwiek innym systemem kompilacji. Jeśli vcpkg nie może znaleźć określonego systemu kompilacji na maszynie lokalnej, pobiera i instaluje go.

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

W przypadku projektów CMake Użyj, `CMAKE_TOOLCHAIN_FILE` Aby udostępnić biblioteki z `find_package()` . Na przykład w systemie Linux lub macOS:

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg/scripts/buildsystems/vcpkg.cmake
```

W systemie Windows:

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg\scripts\buildsystems\vcpkg.cmake
```

Niektóre biblioteki obejmują opcje instalowalne. Na przykład podczas wyszukiwania biblioteki zwinięcie zostanie również wyświetlona lista obsługiwanych opcji w nawiasach kwadratowych:

```cmd
> vcpkg search curl
curl                 7.68.0-3         A library for transferring data with URLs
curl[tool]                            Builds curl executable
curl[non-http]                        Enables protocols beyond HTTP/HTTPS/HTTP2
curl[http2]                           HTTP2 support
curl[ssl]                             Default SSL backend
curl[ssh]                             SSH support via libssh2
curl[openssl]                         SSL support (OpenSSL)
curl[winssl]                          SSL support (Secure Channel / "WinSSL")
curl[mbedtls]                         SSL support (mbedTLS)
curl[sectransp]                       SSL support (sectransp)
curl[c-ares]                          c-ares support
curl[sspi]                            SSPI support
curl[brotli]                          brotli support (brotli)
curlpp               2018-06-15-3     C++ wrapper around libcURL
```

W tym przypadku nawiasy kwadratowe **`[`** i **`]`** są literałami, a nie metaznakami.

W wierszu polecenia można określić konkretną opcję instalacji. Aby na przykład zainstalować biblioteki dla programu zwinięcie przy użyciu domyślnego zaplecza protokołu SSL dla systemu Windows, użyj **`vcpkg install curl[ssl]:x86-windows`** polecenia. Polecenie instaluje wszystkie wymagane wymagania wstępne, w tym bibliotekę podstawową, w razie potrzeby:

```cmd
> vcpkg list
curl:x86-windows            7.68.0-3   A library for transferring data with URLs
curl[non-http]:x86-windows             Enables protocols beyond HTTP/HTTPS/HTTP2
curl[ssl]:x86-windows                  Default SSL backend
curl[sspi]:x86-windows                 SSPI support
curl[winssl]:x86-windows               SSL support (Secure Channel / "WinSSL")
zlib:x86-windows            1.2.11-6   A compression library
```

## <a name="list-the-libraries-already-installed"></a>Lista bibliotek zainstalowanych już

Po zainstalowaniu niektórych bibliotek możesz użyć **`vcpkg list`** programu, aby zobaczyć, co posiadasz:

```cmd
> vcpkg list

boost:x86-windows       1.64-3   Peer-reviewed portable C++ source libraries
bzip2:x86-windows       1.0.6-1  High-quality data compressor.
cpprestsdk:x86-windows  2.9.0-2  C++11 JSON, REST, and OAuth library The C++ REST ...
openssl:x86-windows     1.0.2k-2 OpenSSL is an open source project that provides a...
websocketpp:x86-windows 0.7.0    Library that implements RFC6455 The WebSocket Pro...
zlib:x86-windows        1.2.11   A compression library
```

## <a name="integrate-with-visual-studio-windows"></a>Integracja z programem Visual Studio (Windows)

### <a name="per-user"></a>Według użytkownika

Uruchom **`vcpkg integrate install`** , aby skonfigurować program Visual Studio do lokalizowania wszystkich plików nagłówka vcpkg i danych binarnych dla poszczególnych użytkowników. Nie ma potrzeby ręcznej edycji ścieżek katalogów VC + +. Jeśli masz wiele klonów vcpkg, klon uruchamiający to polecenie otrzymuje nową lokalizację domyślną.

Teraz można #include nagłówki, wpisując folder/nagłówek, a funkcja autouzupełniania pomaga. Żadne dodatkowe kroki nie są wymagane do łączenia się z libs lub dodawania odwołań do projektu. Na poniższej ilustracji przedstawiono, jak program Visual Studio znajduje nagłówki Azure-Storage-cpp. vcpkg umieszcza swoje nagłówki w podfolderze */installed* , partycjonowane według platformy docelowej. Na poniższym diagramie przedstawiono listę plików dołączanych w podfolderze */was* biblioteki:

![vcpkg i IntelliSense](media/vcpkg-intellisense.png "vcpkg i IntelliSense")

### <a name="per-project"></a>Na projekt

Jeśli potrzebujesz użyć określonej wersji biblioteki, która różni się od wersji w aktywnym wystąpieniu usługi vcpkg, wykonaj następujące kroki:

1. Tworzenie nowego klonu vcpkg
1. Zmodyfikuj Portfile biblioteki, aby uzyskać wymaganą wersję
1. Uruchom **`vcpkg install <library>`** .
1. Użyj, **`vcpkg integrate project`** Aby utworzyć pakiet NuGet, który odwołuje się do tej biblioteki na podstawie projektu.

## <a name="integrate-with-visual-studio-code-linuxmacos"></a>Integracja z usługą Visual Studio Code (Linux/macOS)

Uruchom **`vcpkg integrate install`** , aby skonfigurować Visual Studio Code w systemie Linux/macOS. To polecenie ustawia lokalizację rejestracji vcpkg i włącza funkcję IntelliSense w plikach źródłowych.

## <a name="target-linux-from-windows-via-wsl"></a>Ukierunkowane na system Linux z systemu Windows za pośrednictwem WSL

Pliki binarne systemu Linux można tworzyć na komputerze z systemem Windows za pomocą podsystemu Windows dla systemów Linux lub WSL. Postępuj zgodnie z instrukcjami, aby [skonfigurować WSL w systemie Windows 10](/windows/wsl/install-win10). Następnie skonfiguruj go za pomocą [rozszerzenia programu Visual Studio dla systemu Linux](https://devblogs.microsoft.com/cppblog/targeting-windows-subsystem-for-linux-from-visual-studio/). Można umieścić wszystkie skompilowane biblioteki dla systemów Windows i Linux w tym samym folderze. Są one dostępne zarówno w systemie Windows, jak i w WSL.

## <a name="export-compiled-binaries-and-headers"></a><a name="export_binaries_per_project"></a>Eksportuj skompilowane pliki binarne i nagłówki

Wszyscy członkowie zespołu mogą pobierać i kompilować wspólne biblioteki. Pojedynczy członek zespołu może użyć polecenia, **`vcpkg export`** Aby utworzyć wspólny plik zip plików binarnych i nagłówków lub pakiet NuGet. Następnie można łatwo udostępnić go innym członkom zespołu.

## <a name="updateupgrade-installed-libraries"></a>Aktualizowanie/uaktualnianie zainstalowanych bibliotek

Wykaz publiczny jest bieżąco z najnowszymi wersjami bibliotek. Aby określić, które biblioteki lokalne są nieaktualne, użyj programu **`vcpkg update`** . Gdy wszystko będzie gotowe do zaktualizowania kolekcji portów do najnowszej wersji wykazu publicznego, uruchom **`vcpkg upgrade`** polecenie. Automatycznie pobiera i odtwarza wszystkie zainstalowane biblioteki, które są nieaktualne.

Domyślnie **`vcpkg upgrade`** polecenie wyświetla tylko te biblioteki, które są nieaktualne; nie uaktualnia ich. Aby faktycznie uaktualnić biblioteki, użyj **`--no-dry-run`** opcji.

```cmd
> vcpkg upgrade --no-dry-run
```

### <a name="upgrade-options"></a>Opcje uaktualniania

- **`--no-dry-run`** Wykonaj uaktualnienie; gdy nie zostanie określony, polecenie wyświetla tylko listę nieaktualnych pakietów.
- **`--keep-going`** Kontynuuj Instalowanie pakietów nawet wtedy, gdy jeden z nich nie powiedzie się.
- **`--triplet <t>`** Ustaw wartość domyślną tryplet dla niekwalifikowanych pakietów.
- **`--vcpkg-root <path>`** Określ katalog vcpkg, który ma być używany zamiast bieżącego katalogu lub katalogu narzędzi.

### <a name="upgrade-example"></a>Przykład uaktualnienia

Poniższy przykład pokazuje, jak uaktualnić tylko określone biblioteki. vcpkg automatycznie ściąga w zależności od potrzeb.

```cmd
c:\users\satyan\vcpkg> vcpkg upgrade tiny-dnn:x86-windows zlib
The following packages are up-to-date:
   tiny-dnn:x86-windows

The following packages will be rebuilt:
    * libpng[core]:x86-windows
    * tiff[core]:x86-windows
      zlib[core]:x86-windows
Additional packages (*) will be modified to complete this operation.
If you are sure you want to rebuild the above packages, run this command with the --no-dry-run option.
```

## <a name="contribute-new-libraries"></a>Tworzenie nowych bibliotek

Możesz dołączyć wszystkie biblioteki, które lubisz w swojej kolekcji portów prywatnych. Aby zasugerować nową bibliotekę wykazu publicznego, Otwórz problem na [stronie problemu vcpkg usługi GitHub](https://github.com/Microsoft/vcpkg/issues).

## <a name="remove-a-library"></a>Usuwanie biblioteki

Wpisz **`vcpkg remove`** , aby usunąć zainstalowaną bibliotekę. Jeśli zależą od niej inne biblioteki, zostanie wyświetlony monit o ponowne uruchomienie polecenia z **`--recurse`** , co spowoduje usunięcie wszystkich bibliotek podrzędnych.

## <a name="customize-vcpkg"></a>Dostosuj vcpkg

Klon vcpkg można modyfikować w dowolny sposób. Można nawet utworzyć wiele klonów vcpkg, a następnie zmodyfikować portfiles w każdym z nich. Jest to prosty sposób uzyskiwania określonych wersji biblioteki lub do określenia określonych parametrów wiersza polecenia. Na przykład poszczególne grupy deweloperów w przedsiębiorstwie mogą korzystać z oprogramowania, które ma zależności specyficzne dla swojej grupy. Rozwiązaniem jest skonfigurowanie klonu vcpkg dla każdego zespołu. Następnie zmodyfikuj klony, aby pobrać wersje biblioteki i ustawić przełączniki kompilacji, które każdy zespół potrzebuje.

## <a name="update-vcpkg"></a>Aktualizacja vcpkg

Menedżer pakietów vcpkg jest regularnie aktualizowany w serwisie GitHub. Aby zaktualizować klon vcpkg do najnowszej wersji, w katalogu głównym vcpkg Uruchom polecenie **`git pull`** . To polecenie synchronizuje kopię vcpkg z wersją w serwisie GitHub. Po zakończeniu pobierania ponownie uruchom program inicjujący. Program inicjujący ponownie kompiluje programu vcpkg, ale pozostawia zainstalowane biblioteki na miejscu.

## <a name="uninstall-vcpkg"></a>Odinstaluj vcpkg

Aby odinstalować vcpkg, po prostu Usuń katalog vcpkg. Usunięcie tego katalogu spowoduje odinstalowanie dystrybucji vcpkg oraz wszystkich bibliotek, które vcpkg zainstalowane.

## <a name="send-feedback-about-vcpkg"></a>Wyślij opinię na temat vcpkg

Użyj **`vcpkg contact --survey`** polecenia, aby wysłać opinię do firmy Microsoft dotyczącej vcpkg, w tym raportów o błędach i sugestii dotyczących funkcji.

## <a name="the-vcpkg-folder-hierarchy"></a>Hierarchia folderów vcpkg

Wszystkie funkcje i dane vcpkg są samodzielne w jednej hierarchii katalogów, nazywanej "wystąpieniem". Brak ustawień rejestru lub zmiennych środowiskowych. Na komputerze może być dowolna liczba wystąpień vcpkg i nie będą one zakłócać działania siebie.

Zawartość wystąpienia vcpkg:

- buildtrees-zawiera podfoldery źródeł, z których jest skompilowana każda biblioteka
- docs — dokumentacja i przykłady
- pliki do pobrania — buforowane kopie pobranych narzędzi lub źródeł. vcpkg Przeszukuj tutaj najpierw po uruchomieniu polecenia install.
- zainstalowane — zawiera nagłówki i pliki binarne dla każdej zainstalowanej biblioteki. Gdy integrujesz się z programem Visual Studio, oznacza to, że zostanie on dodany do ścieżki wyszukiwania.
- pakiety — wewnętrzny folder do przemieszczania między instalacjami.
- porty — pliki opisujące każdą bibliotekę w wykazie, jej wersję i lokalizację, w której należy ją pobrać. W razie konieczności możesz dodać własne porty.
- Skrypty — skrypty (CMake, PowerShell) używane przez vcpkg.
- kod źródłowy toolsrc-C++ dla vcpkg i powiązanych składników
- Triplets — zawiera ustawienia dla każdej obsługiwanej platformy docelowej (na przykład x86-Windows lub x64-platformy UWP).

## <a name="command-line-reference"></a>Dokumentacja wiersza polecenia

|Polecenie|Opis|
|---------|---------|
|**`vcpkg search [pat]`**|Wyszukaj pakiety dostępne do zainstalowania|
|**`vcpkg install <pkg>...`**|Zainstaluj pakiet|
|**`vcpkg remove <pkg>...`**|Odinstalowywanie pakietu|
|**`vcpkg remove --outdated`**|Odinstaluj wszystkie nieaktualne pakiety|
|**`vcpkg list`**|Wyświetl listę zainstalowanych pakietów|
|**`vcpkg update`**|Wyświetl listę pakietów do zaktualizowania|
|**`vcpkg upgrade`**|Kompiluj ponownie wszystkie nieaktualne pakiety|
|**`vcpkg hash <file> [alg]`**|Mieszanie pliku przez określony algorytm, domyślny SHA512|
|**`vcpkg integrate install`**|Udostępnienie zainstalowanych pakietów dla użytkownika. Wymaga uprawnień administratora przy pierwszym użyciu|
|**`vcpkg integrate remove`**|Usuń integrację na poziomie użytkownika|
|**`vcpkg integrate project`**|Generuj pakiet NuGet odwołującego się do użytku dla poszczególnych projektów programu VS|
|**`vcpkg export <pkg>... [opt]...`**|Eksportowanie pakietu|
|**`vcpkg edit <pkg>`**|Otwórz port do edycji (używa edytora%, domyślnego "Code")|
|**`vcpkg create <pkg> <url> [archivename]`**|Utwórz nowy pakiet|
|**`vcpkg cache`**|Wyświetlanie listy buforowanych pakietów|
|**`vcpkg version`**|Wyświetl informacje o wersji|
|**`vcpkg contact --survey`**|Wyświetlanie informacji kontaktowych w celu wysłania opinii.|

### <a name="options"></a>Opcje

|Opcja|Opis|
|---------|---------|
|**`--triplet <t>`**|Określ tryplet architektury docelowej. (domyślnie: `%VCPKG_DEFAULT_TRIPLET%` , zobacz również **`vcpkg help triplet`** )|
|**`--vcpkg-root <path>`**|Określ katalog główny vcpkg (domyślnie: `%VCPKG_ROOT%` )|
