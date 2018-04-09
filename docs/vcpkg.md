---
title: vcpkg — Menedżer pakietów C++ dla systemu Windows | Dokumentacja firmy Microsoft
description: vcpkg jest wiersza polecenia Menedżera pakietów, które znacząco upraszcza nabycie i instalację open source biblioteki języka C++ w systemie Windows.
keywords: vcpkg
author: mikeblome
ms.author: mblome
ms.date: 04/06/2018
ms.technology:
- cpp-ide
ms.tgt_pltfrm: windows
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.topic: article
dev_langs:
- C++
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 54d1f0cf2a6971435858a1a64bf3e163631822b5
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2018
---
# <a name="vcpkg-c-package-manager-for-windows"></a>vcpkg: Menedżer pakietów C++ dla systemu Windows

vcpkg jest Menedżer pakietów wiersza polecenia, które znacząco upraszcza nabycia i Instalacja bibliotek innych firm w systemie Windows. Jeśli projekt korzysta z bibliotek innych firm, firma Microsoft zaleca, użyj vcpkg mają być instalowane. vcpkg obsługuje zarówno open source i zastrzeżonych biblioteki. Wszystkie biblioteki w katalogu publicznego vcpkg zostały przetestowane na zgodność z programu Visual Studio 2015 i Visual Studio 2017 r. Począwszy od stycznia 2018 w katalogu są ponad 600 bibliotek i społecznością C++ jest dodanie więcej bibliotek w sposób ciągły.

## <a name="simple-yet-flexible"></a>Proste, ale elastyczne

Za pomocą jednego polecenia można pobrać źródeł i tworzenie biblioteki. vcpkg to projekt open source, dostępnej w witrynie GitHub. Twoje prywatne clone(s) w żaden sposób, który chcesz można dostosować. Na przykład można określić różne biblioteki lub różne wersje bibliotek niż co znajdują się w katalogu publicznego. Może mieć wielu klonach vcpkg na jednym komputerze, każda z nich Tworzenie niestandardowych zestawów bibliotek i/lub kompilacji przełączniki itd. Każdy klonowania jest środowiskiem samodzielnych, x copyable własną kopię vcpkg.exe które działa tylko na jego własnej hierarchii. vcpkg nie została dodana do zmiennych środowiskowych i ma nie zależności w rejestrze systemu Windows lub programu Visual Studio.

## <a name="sources-not-binaries"></a>Źródła nie plików binarnych

Dla bibliotek w katalogu publiczne vcpkg pobiera źródeł zamiast danych binarnych [1]. Kompiluje tych źródeł przy użyciu 2017 usługi Visual Studio lub Visual Studio 2015, jeśli nie zainstalowano 2017 r. W języku C++, bardzo ważne jest zgodności żadnych bibliotek, których można użyć z tym samym kompilatora i wersja kompilatora jako prowadzący do niego kodu aplikacji. Za pomocą vcpkg, wyeliminuj lub co najmniej znacznie zmniejszyć ryzyko niedopasowanych pliki binarne i problemów, które mogą powodować. W zespołach, które są standaryzowane do określonej wersji kompilatora Visual C++ jednego elementu członkowskiego zespołu można użyć vcpkg pobieranie źródeł i Skompiluj zestaw plików binarnych, a następnie użyć polecenia Eksportuj do pliku zip pliki binarne i nagłówki dla innych członków zespołu. Aby uzyskać więcej informacji zobacz się, że eksportu skompilowane pliki binarne i nagłówki poniżej. 

Jeśli tworzysz klonowania vcpkg z bibliotekami prywatnych w kolekcji portów, możesz dodać port, który pobiera wbudowane pliki binarne i nagłówki i zapisać pliku portfile.cmake, która po prostu kopiuje pliki do odpowiedniej lokalizacji.

[1] *Uwaga: niektóre zastrzeżone biblioteki źródła nie są dostępne. Vcpkg pobierze zgodne wbudowane plików binarnych w tych przypadkach.*

## <a name="installation"></a>Instalacja

Klonowanie repozytorium vcpkg z usługi GitHub: https://github.com/Microsoft/vcpkg. Możesz pobrać do dowolnej lokalizacji folderu, preferowany.

Uruchom program inicjujący w folderze głównym: **bootstrap vcpkg.bat**.

## <a name="basic-tasks"></a>Podstawowe zadania

## <a name="search-the-list-of-available-libraries"></a>Wyszukaj listę dostępnych bibliotek

Pakietów, które są dostępne, wpisz w wierszu polecenia: **vcpkg wyszukiwania**

To polecenie wylicza pliki kontroli w podfolderach vcpkg/portów. Wyświetlona zostanie lista następująco:

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

Można filtrować wzorca, na przykład **ta wyszukiwania vcpkg**:

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library

```

### <a name="install-a-library-on-your-local-machine"></a>Zainstaluj bibliotekę na komputerze lokalnym

Po uzyskaniu nazwy biblioteki za pomocą **wyszukiwania vcpkg**, możesz użyć **vcpkg zainstalować** pobrać biblioteki i skompiluj go. vcpkg używa biblioteki portfile w katalogu portów. Jeśli Trzykolumnowa nie zostanie określony, vcpkg zainstaluje i kompilacji systemu Windows x86. Jeśli portfile określa zależności, vcpkg pobiera i instaluje te również. Po pobraniu, vcpkg tworzy bibliotekę przy użyciu, niezależnie od systemu, który korzysta z biblioteki kompilacji. Pliki projektów CMake i MSBuild są preferowane, ale upewnij jest obsługiwane wraz z innymi system kompilacji. Jeśli vcpkg nie może znaleźć określonej kompilacji systemu na komputerze lokalnym, pobiera i instaluje je.

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

## <a name="list-the-libraries-already-installed"></a>Wyświetlanie bibliotek już zainstalowane
Po zainstalowaniu niektórych bibliotek, można użyć **listy vcpkg** co masz:

```cmd
> vcpkg list

boost:x86-windows       1.64-3   Peer-reviewed portable C++ source libraries
bzip2:x86-windows       1.0.6-1  High-quality data compressor.
cpprestsdk:x86-windows  2.9.0-2  C++11 JSON, REST, and OAuth library The C++ REST ...
openssl:x86-windows     1.0.2k-2 OpenSSL is an open source project that provides a...
websocketpp:x86-windows 0.7.0    Library that implements RFC6455 The WebSocket Pro...
zlib:x86-windows        1.2.11   A compression library
```

## <a name="integrate-with-visual-studio"></a>Integracja z programem Visual Studio

### <a name="per-user"></a>Na użytkownika

Uruchom **vcpkg integracji instalacji** skonfigurować Visual Studio, aby zlokalizować wszystkie pliki nagłówkowe vcpkg i pliki binarne w poszczególnych użytkowników, bez konieczności ręcznej edycji ścieżek katalogi VC ++. Jeśli masz wiele klony w klonowania, w którym możesz uruchomić tego polecenia staje się do nowej lokalizacji domyślnej.

Teraz możesz #include nagłówki po prostu, wpisując folderu/nagłówka i funkcja automatycznego uzupełniania pomaga. Żadne dodatkowe kroki są wymagane do łączenia z biblioteki lub dodanie odwołania do projektu. Na poniższej ilustracji przedstawiono sposób odnajdowania nagłówki azure magazynu cpp w Visual Studio. vcpkg umieszcza jego nagłówków w **/ zainstalowano** podfolder partycjonowanego platformy docelowej. Na poniższym diagramie przedstawiono listę plików dołączanych w **/ was** podfolderze biblioteki:

![vcpkg integracji Intellisense](media/vcpkg-intellisense.png "vcpkg i Intellisense")

### <a name="per-project"></a>W projekcie

Jeśli musisz użyć określonej wersji biblioteki, która jest inna niż wersja w wystąpieniu active vcpkg, wykonaj następujące kroki:

1. Wprowadź nowy klon vcpkg 
1. Modyfikowanie portfile dla biblioteki w celu uzyskania wersji, które są potrzebne
1. Uruchom **zainstalować vcpkg \<biblioteki >**.
1. Użyj **vcpkg integracji projektu** do utworzenia pakietu NuGet, który odwołuje się do tej biblioteki, na podstawie na projekt.

## <a name="export-compiled-binaries-and-headers"></a>Eksportuj skompilowane pliki binarne i nagłówki

Wymaganie wszyscy członkowie zespołu, aby pobrać i tworzenie bibliotek może być mało wydajne. Członek zespołu pojedynczego tej pracy, a następnie użyj **eksportu vcpkg** można utworzyć pliku zip, pliki binarne i nagłówki, które można łatwo udostępniać innych członków zespołu. 

## <a name="updateupgrade-installed-libraries"></a>Biblioteki zainstalować aktualizację/uaktualnienie

Publiczny katalogu jest zawsze na bieżąco najnowsze wersje bibliotek. Aby określić, które biblioteki lokalnych są nieaktualne, użyj **aktualizacji vcpkg**. Jeśli wszystko jest gotowy do aktualizacji do najnowszej wersji katalogu publicznego kolekcji portów, uruchom **uaktualnienia vcpkg** polecenia próbę automatycznego pobrania i Odbuduj wybranych lub wszystkich zainstalowanych bibliotek, które są nieaktualne.

Domyślnie **uaktualnienia** polecenie wyświetla tylko bibliotek, które są nieaktualne; nie uaktualnić ich. Aby przeprowadzić uaktualnienie, użyj **--przebiegu nie próbnego** opcji. 

```cmd
  vcpkg upgrade --no-dry-run 
```

### <a name="upgrade-options"></a>Opcje uaktualniania

- **--przebiegu nie próbnego** uaktualnienia; Jeśli nie zostanie określony, polecenie znajduje się tylko nieaktualnych opakowania. 
- **--Zachowaj będzie** kontynuuj instalowanie pakietów, nawet w przypadku awarii jednego. 
- **--Trzykolumnowa \<t >** ustawić Trzykolumnowa domyślne niekwalifikowane pakietów. 
- **główny — vcpkg \<ścieżka >** określ katalog vcpkg używany zamiast bieżącego katalogu lub katalogu narzędzia. 

### <a name="upgrade-example"></a>Przykład uaktualnienia

### <a name="per-project"></a>W projekcie
Jeśli musisz użyć określonej wersji biblioteki, która jest inna niż wersja w wystąpieniu active vcpkg, wykonaj następujące kroki:

1. Wprowadź nowy klon vcpkg 
1. Modyfikowanie portfile dla biblioteki w celu uzyskania wersji, które są potrzebne
1. Uruchom **zainstalować vcpkg \<biblioteki >**.
1. Użyj **vcpkg integracji projektu** do utworzenia pakietu NuGet, który odwołuje się do tej biblioteki, na podstawie na projekt.


## <a name="export-compiled-binaries-and-headers"></a>Eksportuj skompilowane pliki binarne i nagłówki
Wymaganie wszyscy członkowie zespołu, aby pobrać i tworzenie bibliotek może być mało wydajne. Członek zespołu pojedynczego tej pracy, a następnie użyj **eksportu vcpkg** można utworzyć pliku zip, pliki binarne i nagłówki, które można łatwo udostępniać innych członków zespołu. 

## <a name="updateupgrade-installed-libraries"></a>Biblioteki zainstalować aktualizację/uaktualnienie
Publiczny katalogu jest zawsze na bieżąco najnowsze wersje bibliotek. Aby określić, które biblioteki lokalnych są nieaktualne, użyj **aktualizacji vcpkg**. Jeśli wszystko jest gotowy do aktualizacji do najnowszej wersji katalogu publicznego kolekcji portów, uruchom **uaktualnienia vcpkg** polecenia próbę automatycznego pobrania i Odbuduj wybranych lub wszystkich zainstalowanych bibliotek, które są nieaktualne.

Domyślnie **uaktualnienia** polecenie wyświetla tylko bibliotek, które są nieaktualne; nie uaktualnić ich. Aby przeprowadzić uaktualnienie, użyj **--przebiegu nie próbnego** opcji. 

```cmd
  vcpkg upgrade --no-dry-run 
```

### <a name="upgrade-options"></a>Opcje uaktualniania

- **--przebiegu nie próbnego** uaktualnienia; Jeśli nie zostanie określony, polecenie znajduje się tylko nieaktualnych opakowania. 
- **--Zachowaj będzie** kontynuuj instalowanie pakietów, nawet w przypadku awarii jednego. 
- **--Trzykolumnowa \<t >** ustawić Trzykolumnowa domyślne niekwalifikowane pakietów. 
- **główny — vcpkg \<ścieżka >** określ katalog vcpkg używany zamiast bieżącego katalogu lub katalogu narzędzia. 

### <a name="upgrade-example"></a>Przykład uaktualnienia

Poniższy przykład pokazuje, jak uaktualnić tylko określonej biblioteki. Należy zauważyć, że ten vcpgk automatycznie pobiera w zależności w razie potrzeby.

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

## <a name="contribute-new-libraries"></a>Współtworzenia nowe biblioteki
Może zawierać żadnych bibliotek żądanych w kolekcji prywatnych portów. Sugerowanie nową biblioteką dla publicznych katalogu, należy otworzyć problemu na [GitHub vcpkg problem strony](https://github.com/Microsoft/vcpkg/issues).

## <a name="remove-a-library"></a>Usuwanie biblioteki
Typ **vcpkg Usuń** Aby usunąć zainstalowane biblioteki. Jeśli inne biblioteki zależą od niej, zostanie wyświetlona prośba o Uruchom ponownie polecenie **--recurse**, co powoduje, że wszystkie podrzędne biblioteki do usunięcia.

## <a name="customize-vcpkg"></a>Customize vcpkg
Można zmodyfikować z klonu vcpkg w żaden sposób, który chcesz. Można tworzyć wiele klony vcpkg i modyfikować portfiles w każdej z nich uzyskać określonych wersji biblioteki lub określić parametry wiersza polecenia. Na przykład w przedsiębiorstwie, jedna grupa deweloperów może działać na oprogramowanie, które ma jeden zestaw zależności, a inna grupa może mieć inny zestaw. Można skonfigurować dwie klonów vcpkg i zmodyfikować każdą z nich pobrać wersje bibliotek i przełączników kompilacji, itd., zgodnie z potrzebami. 

## <a name="uninstall-vcpkg"></a>Uninstall vcpkg
Po prostu Usuń katalog. 

## <a name="send-feedback-about-vcpkg"></a>Wyślij opinię o vcpkg
Użyj **--ankiety** polecenie, aby wysłać opinię do firmy Microsoft o vcpkg, łącznie z raportami usterek i sugestie dotyczące funkcji.

## <a name="the-vcpkg-folder-hierarchy"></a>Hierarchia folderów vcpkg
Wszystkie dane i funkcje vcpkg są niezależne w hierarchii jeden katalog o nazwie "instance". Nie ma żadnych ustawień rejestru lub zmiennych środowiskowych. Może mieć dowolną liczbę wystąpień vcpkg na maszynie, a nie przeszkadzają ze sobą. 

Zawartość wystąpienia vcpkg jest: 

- buildtrees — zawiera podfoldery źródeł, z których każda biblioteka jest wbudowana
- Dokumentacja — dokumentacja i przykłady
- pobiera — zbuforowane kopie pobrany narzędzia lub źródeł. vcpkg wyszukuje tutaj najpierw podczas uruchamiania polecenia install.
- zainstalowany — zawiera nagłówki i pliki binarne dla każdej zainstalowanej biblioteki. Integracja z programem Visual Studio zasadniczo informuje go dodać ten folder do jego ścieżki wyszukiwania.
- Instaluje pakiety — wewnętrzny folder przemieszczania między.
- porty--pliki, które opisują każdej biblioteki w katalogu, jego wersja i umożliwiające pobranie. W razie potrzeby można dodać własne portów.
- skrypty — skryptów (cmake, programu powershell) używanych przez vcpkg.
- toolsrc — kod źródłowy C++ vcpkg i powiązane składniki
- triplets — zawiera ustawienia dla każdej platformy docelowej (na przykład x86 windows lub platformy uwp x64).

## <a name="command-line-reference"></a>Dokumentacja wiersza polecenia

|Polecenie|Opis|
|---------|---------|
|**Wyszukiwanie vcpkg [Paweł]**|Wyszukaj można zainstalować pakietów|
|**Zainstaluj vcpkg \<pkg >...**|Instalowanie pakietu|
|**Usuń vcpkg \<pkg >...**|Odinstaluj pakiet|
|**Usuń vcpkg — przestarzałe**|Odinstaluj wszystkie pakiety nieaktualne|
|**vcpkg list**|Wyświetlanie listy zainstalowanych pakietów|
|**vcpkg update**|Wyświetl listę pakietów aktualizacji|
|**uaktualnienie vcpkg**|Skompiluj ponownie wszystkie pakiety nieaktualne|
|**Skrót vcpkg \<Plik > [alg]**|Wyznaczania wartości skrótu pliku przez algorytm określonych, domyślne SHA512|
|**vcpkg integracji instalacji**|Sprawdź zainstalowane pakiety dostępne całej użytkownika. Wymaga uprawnień administratora na pierwszym użyciem|
|**vcpkg integrację Usuń**|Usuń integrację na poziomie użytkownika|
|**vcpkg integracji projektu**|Generowanie pakietu NuGet odwołujący się do poszczególnych użycia projektu programu VS|
|**Eksport vcpkg \<pkg >... [opt...]**|Eksportowanie pakietu|
|**Edytuj vcpkg \<pkg >**|Otwórz port do edycji (używa edytora %, domyślny kod)|
|**Importuj vcpkg \<pkg >**|Importowanie biblioteki wbudowanych|
|**Utwórz vcpkg \<pkg > \<adres url > [archivename]**|Tworzenie nowego pakietu|
|**właścicielem vcpkg \<pat >**|Wyszukaj pliki w zainstalowanych pakietów|
|**vcpkg cache**|Lista pamięci podręcznej skompilowany pakietów|
|**vcpkg version**|Wyświetl informacje o wersji|
|**Skontaktuj się z vcpkg**|Wyświetlanie informacji kontaktowych wysyłanie opinii|

### <a name="options"></a>Opcje:
|Opcja|Opis|
|---------|---------|
|**--Trzykolumnowa \<t >**|Określ Trzykolumnowa architektury docelowej. (domyślne: `%VCPKG_DEFAULT_TRIPLET%`, zobacz też **vcpkg pomocy Trzykolumnowa**)|
|**--vcpkg-root \<path>**|Określ katalog główny vcpkg (domyślne: `%VCPKG_ROOT%`)|
