---
title: vcpkg — Menedżer C++ pakietów dla systemów Windows, Linux i MacOS
description: vcpkg to Menedżer pakietów wiersza polecenia, który znacznie upraszcza pozyskiwanie i instalację bibliotek typu "Open Source C++ " w systemie Windows.
author: mikeblome
ms.author: mblome
ms.date: 05/16/2019
ms.technology: cpp-ide
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.openlocfilehash: ce28d42fd3452a5e8195f3ced6bbbb06430b1d14
ms.sourcegitcommit: 27d9db019f6d84c94de9e6aff0170d918cee6738
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/06/2020
ms.locfileid: "75676954"
---
# <a name="vcpkg-a-c-package-manager-for-windows-linux-and-macos"></a>vcpkg: Menedżer C++ pakietów dla systemów Windows, Linux i MacOS

vcpkg to Menedżer pakietów wiersza polecenia, który znacznie upraszcza pozyskiwanie i instalację bibliotek innych firm w systemach Windows, Linux i MacOS. Jeśli projekt korzysta z bibliotek innych firm, zaleca się zainstalowanie ich przy użyciu programu vcpkg. vcpkg obsługuje zarówno biblioteki Open Source, jak i zastrzeżone. Wszystkie biblioteki w wykazie systemu Windows vcpkg zostały przetestowane pod kątem zgodności z programem Visual Studio 2015, Visual Studio 2017 i Visual Studio 2019. Od maja 2018 w wykazie systemu Windows istnieje ponad 900 bibliotek i ponad 350 w katalogu Linux/MacOS. C++ Społeczność w bieżąco dodaje do obu wykazów biblioteki.

## <a name="simple-yet-flexible"></a>Proste jeszcze elastyczne

Za pomocą jednego polecenia można pobrać źródła i utworzyć bibliotekę. vcpkg jest samym projektem "open source", który jest dostępny w witrynie GitHub. Możesz dostosować swoje prywatne klony w dowolny sposób. Można na przykład określić różne biblioteki lub różne wersje bibliotek niż te, które znajdują się w wykazie publicznym. Można mieć wiele klonów vcpkg na jednej maszynie, każdy z nich wytwarza niestandardowe zestawy bibliotek i/lub przełączniki kompilacji itp. Każdy klon jest środowiskiem niezależnym z własną kopią programu vcpkg. exe, która działa tylko w odniesieniu do własnej hierarchii. vcpkg nie jest dodawany do żadnych zmiennych środowiskowych i nie ma zależności w rejestrze systemu Windows ani w programie Visual Studio.

## <a name="sources-not-binaries"></a>Źródła nie są plikami binarnymi

W przypadku bibliotek w wykazie systemu Windows vcpkg pobiera źródła zamiast plików binarnych [1]. Kompiluje te źródła przy użyciu najnowszej wersji programu Visual Studio, którą może znaleźć. W C++programie bardzo ważne jest, aby wszystkie używane biblioteki były zgodne z tym samym kompilatorem i wersją kompilatora, jak kod aplikacji, który łączy się z nim. Za pomocą vcpkg, eliminujesz lub co najmniej znacznie zmniejszasz potencjalną niezgodność plików binarnych i problemy, które mogą być przyczyną. W zespołach, które są ustandaryzowane w określonej wersji kompilatora, jeden członek zespołu może używać vcpkg do pobierania źródeł i kompilowania zestawu plików binarnych, a następnie użyć polecenia eksportu do przechowywania plików binarnych i nagłówków dla innych członków zespołu. Aby uzyskać więcej informacji, zobacz [Eksportuj skompilowane pliki binarne i nagłówki](#export_binaries_per_project) poniżej.

Jeśli utworzysz klon vcpkg z bibliotekami prywatnymi w kolekcji Ports, możesz dodać port, który pobiera wstępnie skompilowane pliki binarne i nagłówki i piszą plik Portfile. cmake, który po prostu kopiuje te pliki do żądanej lokalizacji.

[1] *Uwaga: w przypadku niektórych nieopatentowanych bibliotek źródła nie są dostępne. Program Vcpkg będzie pobierać zgodne wstępnie skompilowane pliki binarne w takich przypadkach.*

## <a name="installation"></a>Instalacja programu

Sklonuj repozytorium vcpkg z witryny GitHub: [https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg). Możesz pobrać do dowolnej preferowanej lokalizacji folderów.

Uruchom program inicjujący w folderze głównym:

- **Bootstrap-vcpkg. bat** (system Windows)
- **./Bootstrap-vcpkg.sh** (Linux, MacOS)

## <a name="search-the-list-of-available-libraries"></a>Przeszukaj listę dostępnych bibliotek

Aby zobaczyć, jakie pakiety są dostępne, w wierszu polecenia wpisz: **vcpkg Search**

To polecenie wylicza pliki kontrolki w podfolderach vcpkg/ports. Zobaczysz listę w następujący sposób:

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

Można filtrować według wzorca, na przykład **vcpkg Search**:

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-local-machine"></a>Instalowanie biblioteki na komputerze lokalnym

Po otrzymaniu nazwy biblioteki przy użyciu funkcji **wyszukiwania vcpkg**należy użyć **instalacji vcpkg** , aby pobrać bibliotekę i skompilować ją. vcpkg używa biblioteki Portfile w katalogu portów. Jeśli tryplet nie zostanie określony, vcpkg zainstaluje i skompiluje dla domyślnego tryplet dla platformy docelowej: x86-Windows, x64-Linux. CMAKE lub x64-OSX. CMAKE.

W przypadku bibliotek systemu Linux vcpkg zależy od instalacji programu na komputerze lokalnym. W MacOS, vcpkg używa Clang.

Jeśli Portfile określa zależności, program vcpkg pobiera i instaluje je. Po pobraniu vcpkg kompiluje bibliotekę przy użyciu dowolnego systemu kompilacji, którego używa biblioteka. Projekty programu MSBuild CMake i (w systemie Windows) są preferowane, ale jest obsługiwane wraz z jakimkolwiek innym systemem kompilacji. Jeśli vcpkg nie może znaleźć określonego systemu kompilacji na maszynie lokalnej, pobiera i instaluje go.

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

W przypadku projektów CMAKE należy używać CMAKE_TOOLCHAIN_FILE do udostępniania bibliotek `find_package()`. Na przykład:

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg/scripts/buildsystems/vcpkg.cmake (Linux/MacOS)
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg\scripts\buildsystems\vcpkg.cmake (Windows)
```

## <a name="list-the-libraries-already-installed"></a>Lista bibliotek zainstalowanych już

Po zainstalowaniu niektórych bibliotek możesz użyć **listy vcpkg** , aby zobaczyć, co posiadasz:

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

Uruchom **vcpkg integrację instalacji** , aby skonfigurować program Visual Studio do lokalizowania wszystkich plików nagłówkowych vcpkg i danych binarnych dla poszczególnych użytkowników, bez konieczności ręcznej edycji ścieżek katalogów VC + +. Jeśli masz wiele klonów, klon, z którego jest uruchamiane to polecenie, będzie nową lokalizacją domyślną.

Teraz można #include nagłówki, wpisując folder/nagłówek, a funkcja autouzupełniania pomaga. Żadne dodatkowe kroki nie są wymagane do łączenia się z libs lub dodawania odwołań do projektu. Na poniższej ilustracji przedstawiono, jak program Visual Studio znajduje nagłówki Azure-Storage-cpp. vcpkg umieszcza swoje nagłówki w podfolderze **/installed** , partycjonowane według platformy docelowej. Na poniższym diagramie przedstawiono listę plików dołączanych w podfolderze **/was** biblioteki:

![vcpkg integracja IntelliSense](media/vcpkg-intellisense.png "vcpkg i IntelliSense")

### <a name="per-project"></a>Na projekt

Jeśli potrzebujesz użyć określonej wersji biblioteki, która różni się od wersji w aktywnym wystąpieniu usługi vcpkg, wykonaj następujące kroki:

1. Tworzenie nowego klonu vcpkg
1. Zmodyfikuj Portfile biblioteki, aby uzyskać wymaganą wersję
1. Uruchom **vcpkg zainstaluj > biblioteki \<** .
1. Użyj **vcpkg Zintegruj projekt** , aby utworzyć pakiet NuGet, który odwołuje się do tej biblioteki na podstawie projektu.

## <a name="integrate-with-visual-studio-code-linuxmacos"></a>Integracja z usługą Visual Studio Code (Linux/MacOS)

Uruchom **vcpkg integrację instalacji** , aby skonfigurować Visual Studio Code w systemie Linux/MacOS przy użyciu lokalizacji rejestracji vcpkg i włączyć funkcję IntelliSense w plikach źródłowych.

## <a name="target-linux-from-windows-via-wsl"></a>Ukierunkowane na system Linux z systemu Windows za pośrednictwem WSL

Pliki binarne systemu Linux można tworzyć z poziomu komputera z systemem Windows przy użyciu podsystemu Windows for Linux (WSL). Postępuj zgodnie z instrukcjami, aby [skonfigurować WSL w systemie Windows 10](/windows/wsl/install-win10)i skonfigurować go przy użyciu [rozszerzenia programu Visual Studio dla systemu Linux](https://blogs.msdn.microsoft.com/vcblog/2017/02/08/targeting-windows-subsystem-for-linux-from-visual-studio/). Wszystkie skompilowane biblioteki dla systemów Windows i Linux można umieścić w tym samym folderze i uzyskać do nich dostęp zarówno z systemu Windows, jak i WSL.

## <a name="export_binaries_per_project"></a>Eksportuj skompilowane pliki binarne i nagłówki

Konieczność pobierania i kompilowania bibliotek przez wszystkich członków zespołu może być nieskuteczna. Jeden członek zespołu może wykonać tę czynność, a następnie użyć **eksportu vcpkg** do utworzenia pliku zip plików binarnych i nagłówków lub pakietu NuGet (dostępnego w różnych formatach), który może być łatwo udostępniony innym członkom zespołu.

## <a name="updateupgrade-installed-libraries"></a>Aktualizowanie/uaktualnianie zainstalowanych bibliotek

Wykaz publiczny jest bieżąco z najnowszymi wersjami bibliotek. Aby określić, które biblioteki lokalne są nieaktualne, użyj **aktualizacji vcpkg**. Gdy wszystko jest gotowe do zaktualizowania kolekcji portów do najnowszej wersji wykazu publicznego, uruchom polecenie **vcpkg upgrade** , aby automatycznie pobrać i skompilować wszystkie zainstalowane biblioteki lub wszystkie z nich, które są nieaktualne.

Domyślnie polecenie **upgrade** wyświetla tylko te biblioteki, które są nieaktualne; nie są one uaktualniane. Aby przeprowadzić uaktualnienie, użyj opcji **--no-sucho-Run** .

```cmd
  vcpkg upgrade --no-dry-run
```

### <a name="upgrade-options"></a>Opcje uaktualniania

- **--no-osuszyć-Run**  Wykonaj uaktualnienie; gdy nie zostanie określony, polecenie wyświetla tylko listę nieaktualnych pakietów.
- **--Keeping**  Kontynuuj Instalowanie pakietów nawet wtedy, gdy jeden z nich nie powiedzie się.
- **--tryplet \<t >**  Ustaw wartość domyślną tryplet dla niekwalifikowanych pakietów.
- **--vcpkg-główne ścieżki \<**  Określ katalog vcpkg, który ma być używany zamiast bieżącego katalogu lub katalogu narzędzi.

### <a name="upgrade-example"></a>Przykład uaktualnienia

Poniższy przykład pokazuje, jak uaktualnić tylko określone biblioteki. Należy pamiętać, że w razie potrzeby vcpgk automatycznie ściąga w zależności.

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

Wpisz **vcpkg Usuń** , aby usunąć zainstalowaną bibliotekę. Jeśli zależą od niej inne biblioteki, zostanie wyświetlony monit o ponowne uruchomienie polecenia z poleceniem **--rekursywnie**, co spowoduje usunięcie wszystkich bibliotek podrzędnych.

## <a name="customize-vcpkg"></a>Customize vcpkg

Klon vcpkg można modyfikować w dowolny sposób. Można utworzyć wiele klonów vcpkg i zmodyfikować portfiles w każdym z nich w celu uzyskania określonych wersji bibliotek lub określić parametry wiersza polecenia. Na przykład w przedsiębiorstwie jedna grupa deweloperów może pracować nad oprogramowaniem, które ma jeden zestaw zależności, a inna może mieć inny zestaw. Można skonfigurować dwa klony vcpkg i zmodyfikować każdy z nich, aby pobrać wersje bibliotek i przełączników kompilacji itd., zgodnie z potrzebami.

## <a name="uninstall-vcpkg"></a>Odinstaluj vcpkg

Po prostu Usuń katalog vcpkg. Usunięcie tego katalogu spowoduje odinstalowanie dystrybucji vcpkg oraz wszystkich bibliotek, które vcpkg zainstalowane.

## <a name="send-feedback-about-vcpkg"></a>Wyślij opinię na temat vcpkg

Aby wysłać opinię do firmy Microsoft dotyczącej vcpkg, w tym raportów o błędach i sugestii dotyczących funkcji, użyj polecenia **vcpkg Contact--Survey** .

## <a name="the-vcpkg-folder-hierarchy"></a>Hierarchia folderów vcpkg

Wszystkie funkcje i dane vcpkg są samodzielne w jednej hierarchii katalogów, nazywanej "wystąpieniem". Brak ustawień rejestru lub zmiennych środowiskowych. Na komputerze może być dowolna liczba wystąpień vcpkg i nie zakłócają one siebie nawzajem.

Zawartość wystąpienia vcpkg:

- buildtrees--zawiera podfoldery źródeł, z których jest skompilowana każda biblioteka
- docs — dokumentacja i przykłady
- pliki do pobrania — zbuforowane kopie pobranych narzędzi lub źródeł. vcpkg Przeszukuj tutaj najpierw po uruchomieniu polecenia install.
- zainstalowane — zawiera nagłówki i pliki binarne dla każdej zainstalowanej biblioteki. Gdy integrujesz się z programem Visual Studio, oznacza to, że zostanie on dodany do ścieżki wyszukiwania.
- pakiety — wewnętrzny folder do przemieszczania między instalacjami.
- porty — pliki opisujące każdą bibliotekę w wykazie, jej wersję i lokalizację, w której należy ją pobrać. W razie konieczności możesz dodać własne porty.
- Skrypty — skrypty (cmake, PowerShell) używane przez vcpkg.
- toolsrc — kod C++ źródłowy dla vcpkg i powiązanych składników
- Triplets--zawiera ustawienia dla każdej obsługiwanej platformy docelowej (na przykład x86-Windows lub x64-platformy UWP).

## <a name="command-line-reference"></a>Dokumentacja wiersza polecenia

|Polecenie|Opis|
|---------|---------|
|**vcpkg — wyszukiwanie [moja]**|Wyszukaj pakiety dostępne do zainstalowania|
|**vcpkg > Zainstaluj \<pkg...**|Zainstaluj pakiet|
|**vcpkg Usuń > \<pkg...**|Odinstalowywanie pakietu|
|**vcpkg Usuń--przestarzałe**|Odinstaluj wszystkie nieaktualne pakiety|
|**vcpkg list**|Wyświetl listę zainstalowanych pakietów|
|**vcpkg update**|Wyświetl listę pakietów do zaktualizowania|
|**vcpkg uaktualnienie**|Kompiluj ponownie wszystkie nieaktualne pakiety|
|**> pliku \<skrótu vcpkg [alg]**|Mieszanie pliku przez określony algorytm, domyślny SHA512|
|**Instalacja integracji vcpkg**|Udostępnienie zainstalowanych pakietów dla użytkownika. Wymaga uprawnień administratora przy pierwszym użyciu|
|**vcpkg integracja z usługą Remove**|Usuń integrację na poziomie użytkownika|
|**vcpkg integrację projektu**|Generuj pakiet NuGet odwołującego się do użytku dla poszczególnych projektów programu VS|
|**vcpkg eksportu > \<pkg... [opt]...**|Eksportowanie pakietu|
|**vcpkg Edytuj \<pkg >**|Otwórz port do edycji (używa edytora%, domyślnego "Code")|
|**vcpkg utworzyć \<pkg > \<URL > [archiwalnname]**|Utwórz nowy pakiet|
|**vcpkg cache**|Wyświetlanie listy buforowanych pakietów|
|**vcpkg version**|Wyświetl informacje o wersji|
|**kontakt z vcpkg — przegląd**|Wyświetlanie informacji kontaktowych w celu wysłania opinii.|

### <a name="options"></a>Opcje

|Opcja|Opis|
|---------|---------|
|**--tryplet \<t >**|Określ tryplet architektury docelowej. (domyślnie: `%VCPKG_DEFAULT_TRIPLET%`, zobacz też **vcpkg help tryplet**)|
|**--vcpkg-root \<path>**|Określ katalog główny vcpkg (domyślnie: `%VCPKG_ROOT%`)|
