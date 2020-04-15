---
title: 'vcpkg: menedżer pakietów C++ dla systemów Windows, Linux i MacOS'
description: vcpkg to menedżer pakietów wiersza polecenia, który znacznie upraszcza nabywanie i instalowanie bibliotek C++ typu open source w systemach Windows, MacOS i Linux.
ms.date: 01/10/2020
ms.technology: cpp-ide
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.openlocfilehash: 9dbeba1f55164ace01fb8bb26155dd9319ba62db
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335408"
---
# <a name="vcpkg-a-c-package-manager-for-windows-linux-and-macos"></a>vcpkg: menedżer pakietów C++ dla systemów Windows, Linux i MacOS

vcpkg jest menedżerem pakietów wiersza polecenia dla języka C++. Znacznie upraszcza to nabywanie i instalowanie bibliotek innych firm w systemach Windows, Linux i MacOS. Jeśli projekt używa bibliotek innych firm, zaleca się użycie vcpkg, aby je zainstalować. vcpkg obsługuje zarówno biblioteki typu open source, jak i zastrzeżone. Wszystkie biblioteki w katalogu systemu Windows vcpkg zostały przetestowane pod kątem zgodności z programami Visual Studio 2015, Visual Studio 2017 i Visual Studio 2019. Między katalogami systemu Windows i Linux/MacOS vcpkg obsługuje obecnie ponad 1900 bibliotek. Społeczność języka C++ na bieżąco dodaje więcej bibliotek do obu katalogów.

## <a name="simple-yet-flexible"></a>Proste, ale elastyczne

Za pomocą jednego polecenia można pobierać źródła i tworzyć bibliotekę. vcpkg jest sam w sobie projekt open-source, dostępny na GitHub. Możliwe jest dostosowanie prywatnych klonów vcpkg w dowolny sposób. Na przykład określ różne biblioteki lub inne wersje bibliotek niż te znalezione w katalogu publicznym. Na jednym komputerze może być dostępnych wiele klonów vcpkg. Każdy z nich może być ustawiony do tworzenia niestandardowej kolekcji bibliotek, z preferowanymi przełącznikami kompilacji. Każdy klon jest samodzielnym środowiskiem z własną kopią programu vcpkg.exe, która działa tylko w swojej hierarchii. vcpkg nie jest dodawany do żadnych zmiennych środowiskowych i nie ma zależności od rejestru systemu Windows lub programu Visual Studio.

## <a name="sources-not-binaries"></a>Źródła, a nie pliki binarne

W przypadku bibliotek w katalogu systemu Windows program vcpkg pobiera źródła zamiast plików binarnych<sup>1</sup>. Kompiluje te źródła przy użyciu najnowszej wersji programu Visual Studio, który można znaleźć. W języku C++ ważne jest, aby kod aplikacji i wszystkie biblioteki, których używasz, były kompilowane przez ten sam kompilator i wersję kompilatora. Za pomocą vcpkg, można wyeliminować lub przynajmniej znacznie zmniejszyć potencjał niedopasowanych plików binarnych i problemów, które mogą powodować. W zespołach, które są standaryzowane w określonej wersji kompilatora, jeden członek zespołu może używać vcpkg do pobierania źródeł i kompilowania zestawu plików binarnych. Następnie mogą użyć polecenia eksportu, aby skompresować pliki binarne i nagłówki dla innych członków zespołu. Aby uzyskać więcej informacji, zobacz [Eksportowanie skompilowanych plików binarnych i nagłówków](#export_binaries_per_project) poniżej.

Można również utworzyć klon vcpkg, który ma biblioteki prywatne w kolekcji portów. Dodaj port, który pobiera wstępnie utworzone pliki binarne i nagłówki. Następnie napisz plik portfile.cmake, który po prostu kopiuje te pliki do preferowanej lokalizacji.

<sup>1</sup> *Uwaga: źródła są niedostępne dla niektórych zastrzeżonych bibliotek. W takich przypadkach vcpkg pobiera zgodne wstępnie utworzone pliki binarne.*

## <a name="installation"></a>Instalacja

Klonuj repozytorium vcpkg [https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg)z GitHub: . Możesz pobrać do dowolnej lokalizacji folderu.

Uruchom program inichowania w folderze głównym:

- **bootstrap-vcpkg.bat** (Windows)
- **./bootstrap-vcpkg.sh** (Linux, MacOS)

## <a name="search-the-list-of-available-libraries"></a>Wyszukiwanie na liście dostępnych bibliotek

Aby zobaczyć, jakie pakiety są dostępne, w wierszu polecenia wpisz: **wyszukiwanie vcpkg**

To polecenie wylicza pliki kontrolne w podfolderach vcpkg/ports. Zobaczysz następującą aukcję:

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

Można filtrować na wzorze, na przykład **vcpkg search ta**:

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-local-machine"></a>Instalowanie biblioteki na komputerze lokalnym

Po pobraniu nazwy biblioteki przy użyciu **wyszukiwania vcpkg**można użyć **instalacji vcpkg,** aby pobrać bibliotekę i skompilować ją. vcpkg używa pliku portowego biblioteki w katalogu portów. Jeśli nie określono trójki, vcpkg zainstaluje i skompiluje dla domyślnej trójki dla platformy docelowej: x86-windows, x64-linux.cmake lub x64-osx.cmake.

W przypadku bibliotek systemu Linux vcpkg zależy od gcc instalowane na komputerze lokalnym. W systemie MacOS vcpkg używa clang.

Gdy plik portowy określa zależności, vcpkg pobiera je i instaluje. Po pobraniu vcpkg tworzy bibliotekę przy użyciu tego samego systemu kompilacji, którego używa biblioteka. CMake i (w systemie Windows) MSBuild projekty są preferowane, ale MAKE jest obsługiwany, wraz z każdym innym systemem kompilacji. Jeśli vcpkg nie może znaleźć określonego systemu kompilacji na komputerze lokalnym, pobiera go i instaluje.

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

W przypadku projektów CMAKE użyj CMAKE_TOOLCHAIN_FILE, aby `find_package()`udostępnić biblioteki za pomocą programu . Przykład:

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg/scripts/buildsystems/vcpkg.cmake (Linux/MacOS)
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg\scripts\buildsystems\vcpkg.cmake (Windows)
```

## <a name="list-the-libraries-already-installed"></a>Wyświetlanie listy już zainstalowanych bibliotek

Po zainstalowaniu niektórych bibliotek można użyć **listy vcpkg,** aby zobaczyć, co masz:

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

### <a name="per-user"></a>Na użytkownika

Uruchom **instalację integracji vcpkg,** aby skonfigurować program Visual Studio, aby zlokalizować wszystkie pliki nagłówkowe i pliki binarne vcpkg na podstawie dla użytkownika. Nie ma potrzeby ręcznej edycji ścieżek katalogów VC++. Jeśli masz wiele klonów, klon, z którego uruchamiasz to polecenie, staje się nową lokalizacją domyślną.

Teraz możesz #include nagłówki po prostu wpisując folder / nagłówek, a autouzupełnianie pomaga. Żadne dodatkowe kroki nie są wymagane do łączenia libs lub dodawanie odwołań do projektu. Na poniższej ilustracji pokazano, jak visual studio znajduje nagłówki azure-storage-cpp. vcpkg umieszcza swoje nagłówki w **/zainstalowanym** podfolderze, podzielonych na partycje według platformy docelowej. Na poniższym diagramie przedstawiono listę plików dołączanych w podfolderze **/was** dla biblioteki:

![vcpkg i IntelliSense](media/vcpkg-intellisense.png "vcpkg i IntelliSense")

### <a name="per-project"></a>Na projekt

Jeśli chcesz użyć określonej wersji biblioteki, która różni się od wersji w aktywnym wystąpieniu vcpkg, wykonaj następujące kroki:

1. Zrób nowy klon vcpkg
1. Zmodyfikuj plik portowy biblioteki, aby uzyskać potrzebną wersję
1. Uruchom **>biblioteki instalacji \<vcpkg **.
1. Użyj **projektu integracji vcpkg,** aby utworzyć pakiet NuGet, który odwołuje się do tej biblioteki na podstawie projektu.

## <a name="integrate-with-visual-studio-code-linuxmacos"></a>Integracja z programem Visual Studio Code (Linux/MacOS)

Uruchom **instalację integracji vcpkg,** aby skonfigurować kod programu Visual Studio w systemie Linux/MacOS. To polecenie ustawia lokalizację rejestracji vcpkg i włącza intellisense na plikach źródłowych.

## <a name="target-linux-from-windows-via-wsl"></a>Target Linux z systemu Windows za pośrednictwem WSL

Pliki binarne systemu Linux można tworzyć na komputerze z systemem Windows przy użyciu podsystemu Windows dla systemu Linux lub WSL. Postępuj zgodnie z instrukcjami, aby [skonfigurować WSL w systemie Windows 10](/windows/wsl/install-win10)i skonfigurować go z [rozszerzeniem Visual Studio dla systemu Linux](https://blogs.msdn.microsoft.com/vcblog/2017/02/08/targeting-windows-subsystem-for-linux-from-visual-studio/). To jest w porządku, aby umieścić wszystkie zbudowane biblioteki dla Windows i Linux w tym samym folderze. Są one dostępne zarówno z systemu Windows, jak i WSL.

## <a name="export-compiled-binaries-and-headers"></a><a name="export_binaries_per_project"></a>Eksportowanie skompilowanych plików binarnych i nagłówków

Nieefektywne jest pobieranie i tworzenie wspólnych bibliotek przez wszystkich pracowników zespołu. Jeden członek zespołu może użyć polecenia **eksportu vcpkg** do utworzenia wspólnego pliku zip plików binarnych i nagłówków lub pakietu NuGet. Następnie łatwo jest podzielić się nim z innymi członkami zespołu.

## <a name="updateupgrade-installed-libraries"></a>Aktualizacja/uaktualnienie zainstalowanych bibliotek

Katalog publiczny jest aktualizowany z najnowszymi wersjami bibliotek. Aby ustalić, które z bibliotek lokalnych są nieaktualne, należy użyć **funkcji vcpkg update**. Gdy będziesz gotowy do zaktualizowania kolekcji portów do najnowszej wersji katalogu publicznego, uruchom polecenie **uaktualnienia vcpkg.** Automatycznie pobiera i przebudowuje wszystkie lub wszystkie zainstalowane biblioteki, które są nieaktualne.

Domyślnie polecenie **uaktualnienia** zawiera tylko biblioteki, które są nieaktualne; nie uaktualnia ich. Aby faktycznie uaktualnić biblioteki, należy użyć opcji **--no-dry-run.**

```cmd
  vcpkg upgrade --no-dry-run
```

### <a name="upgrade-options"></a>Opcje uaktualnienia

- **--no-dry-run**  Wykonaj uaktualnienie; jeśli nie zostanie określony, polecenie zawiera tylko nieaktualne pakiety.
- **--keep-going**  Kontynuuj instalowanie pakietów, nawet jeśli jeden nie powiedzie się.
- **--triplet \<t>**  Ustaw domyślną trójkę dla pakietów niekwalifikowanych.
- **Ścieżka --vcpkg-root \<>**  Określ katalog vcpkg, który ma być używany zamiast bieżącego katalogu lub katalogu narzędzi.

### <a name="upgrade-example"></a>Przykład uaktualnienia

W poniższym przykładzie pokazano, jak uaktualnić tylko określone biblioteki. w razie potrzeby vcpkg automatycznie pobiera zależności.

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

## <a name="contribute-new-libraries"></a>Współtworzenie nowych bibliotek

Do kolekcji portów prywatnych można uwzględnić dowolne biblioteki. Aby zaproponować nową bibliotekę dla katalogu publicznego, otwórz problem na [stronie wydania programu GitHub vcpkg](https://github.com/Microsoft/vcpkg/issues).

## <a name="remove-a-library"></a>Usuwanie biblioteki

Wpisz **polecenie vcpkg remove,** aby usunąć zainstalowaną bibliotekę. Jeśli inne biblioteki są od niego zależne, zostaniesz poproszony o ponowne uruchomienie polecenia za pomocą **--recurse**, co powoduje usunięcie wszystkich bibliotek podrzędnych.

## <a name="customize-vcpkg"></a>Dostosowywanie vcpkg

Klon vcpkg można zmodyfikować w dowolny sposób. Można nawet utworzyć wiele klonów vcpkg, a następnie zmodyfikować pliki portowe w każdym z nich. Jest to prosty sposób uzyskania określonych wersji biblioteki lub określenia określonych parametrów wiersza polecenia. Na przykład w przedsiębiorstwie poszczególne grupy deweloperów mogą pracować nad oprogramowaniem, które ma zestaw zależności specyficznych dla ich grupy. Rozwiązaniem jest skonfigurowanie klonu vcpkg dla każdej drużyny. Następnie zmodyfikuj klony, aby pobrać wersje biblioteki i ustaw przełączniki kompilacji, których potrzebuje każdy zespół.

## <a name="uninstall-vcpkg"></a>Odinstalowywanie vcpkg

Wystarczy usunąć katalog vcpkg. Usunięcie tego katalogu powoduje odinstalowanie dystrybucji vcpkg i wszystkich bibliotek zainstalowanych przez vcpkg.

## <a name="send-feedback-about-vcpkg"></a>Wysyłanie opinii na temat vcpkg

Użyj polecenia **kontakt vcpkg --survey,** aby wysłać do firmy Microsoft opinię dotyczącą vcpkg, w tym raporty o błędach i sugestie dotyczące funkcji.

## <a name="the-vcpkg-folder-hierarchy"></a>Hierarchia folderów vcpkg

Wszystkie funkcje i dane vcpkg są samodzielne w hierarchii pojedynczego katalogu, zwanego "wystąpieniem". Nie ma żadnych ustawień rejestru ani zmiennych środowiskowych. Na komputerze może być dowolna liczba wystąpień vcpkg i nie będą one kolidować ze sobą.

Zawartość wystąpienia vcpkg to:

- buildtrees - zawiera podfoldery źródeł, z których zbudowana jest każda biblioteka
- dokumenty - dokumentacja i przykłady
- pliki do pobrania — buforowane kopie pobranych narzędzi lub źródeł. vcpkg najpierw przeszukuje tutaj po uruchomieniu polecenia install.
- zawiera nagłówki i pliki binarne dla każdej zainstalowanej biblioteki. Podczas integracji z programem Visual Studio, jesteś zasadniczo informując go dodać ten folder do swoich ścieżek wyszukiwania.
- pakiety -- Wewnętrzny folder do przemieszczania między instalacjami.
- ports -- Pliki opisujące każdą bibliotekę w katalogu, jej wersję i gdzie ją pobrać. W razie potrzeby można dodać własne porty.
- skrypty -- Skrypty (cmake, powershell) używane przez vcpkg.
- toolsrc -- Kod źródłowy C++ dla vcpkg i powiązanych składników
- trojaczki - Zawiera ustawienia dla każdej obsługiwanej platformy docelowej (na przykład x86-windows lub x64-uwp).

## <a name="command-line-reference"></a>Dokumentacja wiersza polecenia

|Polecenie|Opis|
|---------|---------|
|**vcpkg \[szukaj pat]**|Wyszukiwanie pakietów dostępnych do zainstalowania|
|**vcpkg \<zainstalować pkg>...**|Instalowanie pakietu|
|**vcpkg \<usunąć pkg>...**|Odinstalowywanie pakietu|
|**vcpkg usunąć --przestarzałe**|Odinstalowywanie wszystkich nieaktualnych pakietów|
|**lista vcpkg**|Lista zainstalowanych pakietów|
|**aktualizacja vcpkg**|Wyświetlanie listy pakietów do aktualizacji|
|**uaktualnienie vcpkg**|Odbuduj wszystkie przestarzałe pakiety|
|**plik skrótu \<vcpkg> \[alg]**|Skrót pliku według określonego algorytmu, domyślny SHA512|
|**instalacja integracji vcpkg**|Udostępnij zainstalowane pakiety dla całego użytkownika. Wymaga uprawnień administratora przy pierwszym użyciu|
|**vcpkg integracja usunąć**|Usuwanie integracji całego użytkownika|
|**projekt integracji vcpkg**|Generowanie pakietu NuGet odwołującego się do indywidualnego użycia projektu VS|
|**vcpkg \<eksport pkg>... \[opt]...**|Eksportowanie pakietu|
|**vcpkg \<edytuj pkg>**|Otwórz port do edycji (używa %EDITOR%, domyślny "kod")|
|**vcpkg \<tworzenie pkg> \<adres URL \[> nazwa archiwum]**|Tworzenie nowego pakietu|
|**pamięć podręczna vcpkg**|Lista buforowanych skompilowanych pakietów|
|**wersja vcpkg**|Wyświetlanie informacji o wersji|
|**vcpkg kontakt --survey**|Wyświetlaj informacje kontaktowe, aby wysłać opinię.|

### <a name="options"></a>Opcje

|Opcja|Opis|
|---------|---------|
|**--triplet \<t>**|Określ trójkę architektury docelowej. (domyślnie: `%VCPKG_DEFAULT_TRIPLET%`, zobacz także **vcpkg help triplet**)|
|**Ścieżka --vcpkg-root \<>**|Określ katalog główny vcpkg `%VCPKG_ROOT%`(domyślnie: )|
