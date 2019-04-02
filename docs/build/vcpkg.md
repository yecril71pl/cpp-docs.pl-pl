---
title: vcpkg — C++ Menedżer pakietów dla Windows, Linux i MacOS
description: vcpkg to Menedżer pakietów wiersza polecenia, które znacząco upraszcza pozyskiwanie i Instalacja bibliotek C++ typu open source na Windows.
author: mikeblome
ms.author: mblome
ms.date: 03/18/2019
ms.technology: cpp-ide
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.openlocfilehash: 2ca1b88f492d96f8a08d296cab7f35f3b72409c9
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787235"
---
# <a name="vcpkg-a-c-package-manager-for-windows-linux-and-macos"></a>vcpkg: Menedżer pakietów języka C++ dla Windows, Linux i MacOS

vcpkg to Menedżer pakietów wiersza polecenia, które znacząco upraszcza pozyskiwanie i instalacji na Windows, Linux i MacOS przy użyciu biblioteki innej firmy. Jeśli projekt używa bibliotek innych firm, zaleca się używać vcpkg je zainstalować. vcpkg obsługuje bibliotek typu open source i własnościowych. Wszystkie biblioteki w katalogu Windows vcpkg zostały przetestowane na zgodność z programu Visual Studio 2015 i Visual Studio 2017. Począwszy od maja 2018 roku istnieją ponad 900 bibliotek w katalogu Windows i za pośrednictwem 350 w wykazie systemu Linux/MacOS. Społeczność C++ dodaje do obu katalogów w sposób ciągły nad dodatkowymi bibliotekami.

## <a name="simple-yet-flexible"></a>Proste, a elastyczne

Za pomocą jednego polecenia możesz pobrać źródeł i tworzenie biblioteki. vcpkg to projekt typu open source dostępnych w witrynie GitHub. Można dostosować swoje prywatne clone(s) w jakikolwiek sposób, który chcesz. Na przykład można określić różne biblioteki lub różne wersje bibliotek niż co znajdują się w katalogu publicznych. Może mieć wielu klonach vcpkg na jednym komputerze, każdy z nich tworzyć niestandardowe zestawy bibliotek i/lub przełączniki kompilacji itd. Każdego klonu jest niezależnym środowisku z własną kopię vcpkg.exe operuje tylko na własnej hierarchii. vcpkg nie została dodana do zmiennych środowiskowych i nie jest zależny w rejestrze Windows lub programu Visual Studio.

## <a name="sources-not-binaries"></a>Źródła nie dane binarne

W przypadku bibliotek w katalogu Windows vcpkg pobiera źródeł zamiast plików binarnych [1]. Kompiluje tych źródeł przy użyciu programu Visual Studio 2017 lub Visual Studio 2015, jeśli nie zainstalowano 2017. W języku C++, bardzo ważne jest zgodności przy użyciu tego samego środowiska kompilatora, a wersja kompilatora wszystkie biblioteki, którego używasz jako aplikacji kodu, który stanowi łącze do niego. Za pomocą vcpkg, wyeliminuj lub co najmniej znacznie zmniejszyć ryzyko niedopasowanych danych binarnych oraz problemy, które może spowodować, że. W zespołach, które są standaryzowane do określonej wersji kompilatora jednego członka zespołu umożliwia vcpkg pobieranie źródeł i Skompiluj zestaw plików binarnych, a następnie zip pliki binarne i nagłówki dla innych członków zespołu za pomocą polecenia eksportu. Aby uzyskać więcej informacji, zobacz [eksportu skompilowane pliki binarne i nagłówki](#export_binaries_per_project) poniżej.

Jeśli tworzysz klonowania vcpkg prywatne biblioteki w kolekcji portów można dodać portu, która pobiera wstępnie utworzone pliki binarne i nagłówki i zapisać pliku portfile.cmake, który po prostu kopiuje pliki do żądanej lokalizacji.

[1] *Uwaga: niektóre zastrzeżone biblioteki źródeł nie są dostępne. Vcpkg pobierze zgodny ze wstępnie utworzonych plików binarnych w tych przypadkach.*

## <a name="installation"></a>Instalacja

Sklonuj repozytorium vcpkg z witryny GitHub: [ https://github.com/Microsoft/vcpkg ](https://github.com/Microsoft/vcpkg). Możesz pobrać do dowolnej lokalizacji folderu, który użytkownik sobie tego życzy.

Uruchom program inicjujący w folderze głównym:

- **bootstrap-vcpkg.bat** (Windows)
- **./bootstrap-vcpkg.sh** (Linux, MacOS)

## <a name="search-the-list-of-available-libraries"></a>Przeszukaj listę dostępnych bibliotek

Aby zobaczyć, jakie pakiety są dostępne, wpisz w wierszu polecenia: **vcpkg wyszukiwania**

To polecenie wylicza pliki kontroli w podfolderach vcpkg/portów. Zobaczysz listę następująco:

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

Można filtrować przy użyciu wzorca, na przykład **-wyszukiwanie vcpkg**:

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-local-machine"></a>Zainstaluj bibliotekę na komputerze lokalnym

Po otrzymaniu nazwy biblioteki, za pomocą **wyszukiwania vcpkg**, możesz użyć **zainstalować vcpkg** pobierania biblioteki i skompiluj go. vcpkg używa biblioteki portfile w katalogu portów. Jeśli trójkę nie zostanie określony, zainstaluje i Kompiluj trójkę domyślny dla platformy docelowej vcpkg: x86 windows, x64 linux.cmake lub x64 osx.cmake.

W przypadku bibliotek systemu Linux vcpkg zależy od gcc instalowane na komputerze lokalnym. W systemie MacOS vcpkg używa Clang.

Jeśli portfile określa zależności, vcpkg pobiera i instaluje te również. Po pobraniu vcpkg kompilacje biblioteki za pomocą kompilacji niezależnie od systemu, który korzysta z biblioteki. CMake i (Windows) projektów MSBuild są preferowane, ale upewnij jest obsługiwany razem z każdym systemem kompilacji. Jeśli vcpkg nie może odnaleźć określonej kompilacji systemu na maszynie lokalnej, pobiera i instaluje go.

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

Dla projektów CMAKE umożliwia CMAKE_TOOLCHAIN_FILE udostępnić za pomocą biblioteki `find_package()`. Na przykład:

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg/scripts/buildsystems/vcpkg.cmake (Linux/MacOS)
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg\scripts\buildsystems\vcpkg.cmake (Windows)
```

## <a name="list-the-libraries-already-installed"></a>Wyświetlanie bibliotek już zainstalowane

Po zainstalowaniu niektóre biblioteki można używać **listy vcpkg** aby zobaczyć, jakie masz:

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

### <a name="per-user"></a>Per-user

Uruchom **vcpkg integracji instalacji** skonfigurować program Visual Studio, aby zlokalizować wszystkie vcpkg pliki nagłówkowe i pliki binarne na poszczególnych użytkowników, bez konieczności ręcznej edycji ścieżek katalogi VC ++. W przypadku wielu klonach klonowania, w którym jest Uruchom to polecenie staje się nową lokalizację domyślną.

Teraz możesz #include nagłówki po prostu wpisując folderu/nagłówka i automatycznego uzupełniania pomaga. Żadne dodatkowe kroki są wymagane do łączenia z biblioteki lub dodanie odwołania do projektu. Poniższa ilustracja przedstawia, jak program Visual Studio znajdzie nagłówki azure-storage-cpp. vcpkg umieszcza jego nagłówków w **/ zainstalowane** podfolder, dzielone według platformy docelowej. Na poniższym diagramie przedstawiono listę dołączonych plików w **/ was** podfolderu w bibliotece:

![vcpkg integracji IntelliSense](media/vcpkg-intellisense.png "vcpkg i technologii IntelliSense")

### <a name="per-project"></a>Według projektu

Jeśli musisz użyć określonej wersji biblioteki, która jest inna niż wersja w wystąpieniu usługi active vcpkg, wykonaj następujące czynności:

1. Wprowadź nowy klon vcpkg
1. Modyfikowanie portfile dla biblioteki w celu uzyskania wersji, których potrzebujesz
1. Uruchom **zainstalować vcpkg \<biblioteki >**.
1. Użyj **vcpkg integracji projektu** do utworzenia pakietu NuGet, który odwołuje się do tej biblioteki, na poszczególnych projektów.

## <a name="integrate-with-visual-studio-code-linuxmacos"></a>Integracja z usługą Visual Studio Code (Linux/MacOS)

Uruchom **vcpkg integracji instalacji** skonfigurować Visual Studio Code w systemie Linux/MacOS przy użyciu lokalizacji vcpkg enlistement i włączyć funkcję IntelliSense w plikach źródłowych.

## <a name="target-linux-from-windows-via-wsl"></a>Wyceluj Linux, od Windows za pośrednictwem WSL

Może tworzyć pliki binarne systemu Linux, na komputerze Windows za pomocą podsystemu Windows dla systemu Linux (WSL). Postępuj zgodnie z instrukcjami, aby [Konfigurowanie WSL w systemie Windows 10](/windows/wsl/install-win10)i skonfiguruj ją za pomocą [rozszerzenia programu Visual Studio dla systemu Linux](https://blogs.msdn.microsoft.com/vcblog/2017/02/08/targeting-windows-subsystem-for-linux-from-visual-studio/). Można umieścić wszystkie utworzone biblioteki dla systemów Windows i Linux w tym samym folderze, a do niego dostęp z WSL i Windows.

## <a name="export_binaries_per_project"></a> Eksportowanie skompilowane pliki binarne i nagłówki

Wymaganie wszyscy w zespole, pobieranie i tworzenie bibliotek może być mało wydajne. Można wykonać pracę pojedynczego członka zespołu, a następnie użyj **eksportu vcpkg** utworzyć plik zip, pliki binarne i nagłówków lub pakietu NuGet (różne formatowania dostępne), który można łatwo udostępniać innym członkom zespołu.

## <a name="updateupgrade-installed-libraries"></a>Biblioteki zaktualizować/uaktualnić zainstalowany

Publiczne wykazu jest aktualizowane przy użyciu najnowszej wersji bibliotek. Aby określić, które z lokalnych bibliotek są nieaktualne, użyj **aktualizacji vcpkg**. Gdy wszystko będzie gotowe, można zaktualizować kolekcji portów do najnowszej wersji publicznej wykazu, uruchom **uaktualnienia vcpkg** polecenie, aby automatycznie pobierać i Odbuduj wybranych lub wszystkich zainstalowanych bibliotek, które są nieaktualne.

Domyślnie **uaktualnienia** polecenie wyświetla listę tylko bibliotek, które są nieaktualne; nie go uaktualnić. Aby przeprowadzić uaktualnienie, użyj **--nie--przebiegu** opcji.

```cmd
  vcpkg upgrade --no-dry-run
```

### <a name="upgrade-options"></a>Opcje uaktualniania

- **--nie--przebiegu** uaktualnienia; Jeśli nie zostanie określony, polecenie znajduje się tylko nieaktualne pakiety.
- **--Zachowaj będzie** kontynuuj instalowanie pakietów, nawet wtedy, gdy zawiedzie.
- **--trójkę \<t >** Ustaw trójkę domyślne niekwalifikowanej pakietów.
- **vcpkg — główny \<ścieżka >** określ katalog vcpkg zamiast bieżącego katalogu lub katalog narzędzi.

### <a name="upgrade-example"></a>Przykład uaktualnienia

Poniższy przykład pokazuje, jak uaktualnić tylko określonej biblioteki. Pamiętaj, że vcpgk automatycznie pobiera w zależnościach zgodnie z potrzebami.

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

## <a name="contribute-new-libraries"></a>Współtworzenie nowe biblioteki

Może zawierać żadnych bibliotek, które chcesz w kolekcji prywatnych portów. Zaproponuj nową biblioteką dla publicznego katalogu, otwórz problem w [strony problem usługi GitHub vcpkg](https://github.com/Microsoft/vcpkg/issues).

## <a name="remove-a-library"></a>Usuwanie biblioteki

Typ **Usuń vcpkg** Aby usunąć bibliotekę zainstalowane. Jeśli od niej zależnych innych bibliotek, zostanie wyświetlony monit Uruchom ponownie polecenie **--recurse**, co powoduje, że wszystkie podrzędne biblioteki do usunięcia.

## <a name="customize-vcpkg"></a>Customize vcpkg

Można zmodyfikować klonie vcpkg w jakikolwiek sposób, który chcesz. Można tworzyć wielu klonach vcpkg i modyfikować portfiles w każdej z nich do uzyskania określonych wersji biblioteki lub określić parametry wiersza polecenia. Na przykład w przedsiębiorstwie, być może pracujesz jedna grupa deweloperów oprogramowania, który ma jeden zestaw zależności, a inna grupa może mieć inny zestaw. Można skonfigurować dwa klony vcpkg i zmodyfikować każdy z nich można pobrać wersji bibliotek i przełączników kompilacji, itd., zgodnie z potrzebami.

## <a name="uninstall-vcpkg"></a>Odinstaluj vcpkg

Po prostu Usuń katalog.

## <a name="send-feedback-about-vcpkg"></a>Wyślij opinię o vcpkg

Użyj **vcpkg skontaktuj się z pomocą — udział w ankiecie** polecenie, aby wysłać opinię do firmy Microsoft dotyczącą vcpkg, łącznie z raportami usterki i sugestie dotyczące funkcji.

## <a name="the-vcpkg-folder-hierarchy"></a>Vcpkg hierarchii folderów

Wszystkie funkcje vcpkg i danych stanowi odrębną całość, w hierarchii jeden katalog o nazwie "wystąpienie". Brak ustawienia rejestru i zmiennych środowiskowych. Może mieć dowolną liczbę wystąpień vcpkg na maszynie, a nie przeszkadzają ze sobą.

Zawartość wystąpienia vcpkg jest:

- buildtrees — zawiera podfoldery, źródeł, z których każda biblioteka jest skompilowana
- Dokumentacja — dokumentacja i przykłady
- pliki do pobrania — zbuforowane kopie pobranego narzędzia lub źródeł. vcpkg wyszukuje tutaj najpierw po uruchomieniu polecenia instalacji.
- zainstalowano — zawiera nagłówki i pliki binarne dla każdej zainstalowanej biblioteki. W ramach integracji z programem Visual Studio, można zasadniczo sprawi, że jej Dodaj ten folder do swojej ścieżki wyszukiwania.
- Instaluje pakiety — wewnętrzne folder przemieszczania między.
- porty — pliki, które opisują każdej biblioteki w katalogu, jego wersja i gdzie można go pobrać. Jeśli to konieczne, można dodawać własne porty.
- skrypty — skrypty (cmake, programu powershell) używane przez vcpkg.
- toolsrc — kod źródłowy C++ vcpkg i powiązane składniki
- triplets — zawiera ustawienia dla każdej platformy docelowej (na przykład x86 windows lub x64 uwp).

## <a name="command-line-reference"></a>Dokumentacja wiersza polecenia

|Polecenie|Opis|
|---------|---------|
|**vcpkg wyszukiwania [Paweł]**|Wyszukaj pakiety dostępne do zainstalowania|
|**Zainstaluj vcpkg \<pkg >...**|Zainstaluj pakiet|
|**Usuń vcpkg \<pkg >...**|Odinstaluj pakiet|
|**Usuń vcpkg — przestarzałe**|Odinstaluj wszystkie pakiety nieaktualne|
|**vcpkg list**|Wyświetlanie listy zainstalowanych pakietów|
|**vcpkg update**|Wyświetlanie listy pakietów aktualizacji|
|**vcpkg uaktualnienia**|Ponownie skompiluj wszystkie pakiety nieaktualne|
|**Skrót vcpkg \<Plik > [algorytmu]**|Wyznaczania wartości skrótu pliku, określonego algorytmu, domyślnie SHA512|
|**vcpkg integracji instalacji**|Marka zainstalowane pakiety użytkownika dostępne na poziomie. Wymaga uprawnień administratora przy pierwszym użyciu|
|**vcpkg integracja remove**|Usuń integrację na poziomie użytkownika|
|**vcpkg integracji projektu**|Wygeneruj pakiet NuGet odwołujący się do użytku osobistego projektu programu VS|
|**Eksportowanie vcpkg \<pkg >... [zoptymalizowany pod kątem]...**|Eksportowanie pakietu|
|**Edytuj vcpkg \<pkg >**|Otwórz port do edycji (używa edytora %, domyślny kod)|
|**Tworzenie vcpkg \<pkg > \<adresu url > [archivename]**|Tworzenie nowego pakietu|
|**vcpkg cache**|Lista pamięci podręcznej skompilowanych pakietów|
|**vcpkg version**|Wyświetl informacje o wersji|
|**Skontaktuj się z vcpkg — udział w ankiecie**|Wyświetl informacje kontaktowe, aby wysłać opinię.|

### <a name="options"></a>Opcje

|Opcja|Opis|
|---------|---------|
|**--trójkę \<t >**|Określ trójkę architektury docelowej. (domyślne: `%VCPKG_DEFAULT_TRIPLET%`, zobacz też **trójkę pomocy vcpkg**)|
|**--vcpkg-root \<path>**|Określ katalog główny vcpkg (domyślne: `%VCPKG_ROOT%`)|
