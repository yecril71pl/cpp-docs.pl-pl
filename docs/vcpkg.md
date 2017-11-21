---
title: "vcpkg — Menedżer pakietów C++ dla systemu Windows | Dokumentacja firmy Microsoft"
description: "vcpkg jest wiersza polecenia Menedżera pakietów, które znacząco upraszcza nabycie i instalację open source biblioteki języka C++ w systemie Windows."
keywords: vcpkg
author: mikeblome
ms.author: mblome
ms.date: 05/30/2017
ms.technology: cpp-ide
ms.tgt_pltfrm: windows
ms.assetid: f50d459a-e18f-4b4e-814b-913e444cedd6
ms.topic: article
dev_langs: C++
manager: ghogen
ms.openlocfilehash: de5825e64abac210561cb8cbe0dc3320a740cbee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="vcpkg-c-package-manager-for-windows"></a>vcpkg: Menedżer pakietów C++ dla systemu Windows 
vcpkg jest wiersza polecenia Menedżera pakietów, które znacząco upraszcza nabycia i Instalacja bibliotek innych firm w systemie Windows. Jeśli projekt korzysta z bibliotek innych firm, firma Microsoft zaleca, użyj vcpkg mają być instalowane. vcpkg obsługuje zarówno open source i zastrzeżonych biblioteki. Wszystkie biblioteki w katalogu publicznego vcpkg zostały przetestowane na zgodność z programu Visual Studio 2015 i Visual Studio 2017 r. Począwszy od 2017 maja w katalogu są ponad 238 bibliotek i społeczności C++ jest dodanie więcej bibliotek w sposób ciągły.

## <a name="simple-yet-flexible"></a>Proste, ale elastyczne
Za pomocą jednego polecenia można pobrać źródeł i tworzenie biblioteki. vcpkg to projekt open source, dostępnej w witrynie GitHub. Twoje prywatne clone(s) w dowolny sposób Ci się podoba, na przykład, określając różne biblioteki lub różne wersje bibliotek niż co znajdują się w katalogu publiczne można dostosować. Może mieć wielu klonach vcpkg na jednym komputerze, każda z nich Tworzenie niestandardowych zestawów bibliotek i/lub kompilacji przełączniki itd. Każdy klonowania jest środowiskiem całkowicie niezależne, x copyable własną kopię vcpkg.exe które działa tylko na jego własnej hierarchii. vcpkg nie została dodana do zmiennych środowiskowych i ma nie zależności w rejestrze systemu Windows lub programu Visual Studio.

## <a name="sources-not-binaries"></a>Źródła nie plików binarnych
Dla bibliotek w katalogu publiczne vcpkg pobiera źródeł zamiast danych binarnych [1]. Kompiluje tych źródeł przy użyciu 2017 usługi Visual Studio lub Visual Studio 2015, jeśli nie zainstalowano 2017 r. W języku C++, bardzo ważne jest zgodności żadnych bibliotek, których można użyć z tym samym kompilatora i wersja kompilatora jako prowadzący do niego kodu aplikacji. Za pomocą vcpkg wyeliminuj lub co najmniej znacznie zmniejszyć ryzyko niedopasowanych pliki binarne i problemów, które mogą powodować. W zespołach, które są standaryzowane do określonej wersji kompilatora Visual C++ jednego elementu członkowskiego zespołu można użyć vcpkg pobieranie źródeł i Skompiluj zestaw plików binarnych, a następnie użyć polecenia Eksportuj do pliku zip pliki binarne i nagłówki dla innych członków zespołu. Aby uzyskać więcej informacji zobacz się, że eksportu skompilowane pliki binarne i nagłówki poniżej. 

Jeśli tworzysz klonowania vcpkg z bibliotekami prywatnych w kolekcji portów, możesz dodać port, który pobiera wbudowane pliki binarne i nagłówki i zapisać pliku portfile.cmake, która po prostu kopiuje pliki do odpowiedniej lokalizacji.

[1] *Uwaga: niektóre zastrzeżone biblioteki źródła nie są dostępne. Vcpkg pobierze zgodne wbudowane plików binarnych w tych przypadkach.*

## <a name="installation"></a>Instalacja
Klonowanie repozytorium vcpkg z usługi GitHub: https://github.com/Microsoft/vcpkg. Możesz pobrać do dowolnej lokalizacji folderu, preferowany.

Uruchom program inicjujący w folderze głównym: vcpkg.bat ładowania początkowego.

## <a name="basic-tasks"></a>Podstawowe zadania
  
### <a name="search-the-list-of-available-libraries"></a>Wyszukaj listę dostępnych bibliotek
Aby zobaczyć, jakie pakiety są dostępne, wpisz w wierszu polecenia:`vcpkg search`

To polecenie wylicza pliki kontroli w podfolderach vcpkg/portów. Wyświetlona zostanie lista następująco:

```cmd
ace       6.4.3   The ADAPTIVE Communication Environment
anax      2.1.0-1 An open source C++ entity system. <https://github...
antlr4    4.6-1   ANother Tool for Language Recognition
apr       1.5.2   The Apache Portable Runtime (APR) is a C library ...
asio      1.10.8  Asio is a cross-platform C++ library for network ...
assimp    3.3.1   The Open Asset import library
atk       2.24.0  GNOME Accessibility Toolkit
...
```

  Można filtrować wzorca, na przykład `vcpkg search ta`:

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library

```

### <a name="install-a-library-on-your-local-machine"></a>Zainstaluj bibliotekę na komputerze lokalnym
Po uzyskaniu nazwy biblioteki za pomocą `vcpkg search`, możesz użyć `vcpkg install` pobrać biblioteki i go skompilować. vcpkg używa biblioteki portfile w katalogu portów. Jeśli Trzykolumnowa nie zostanie określony, vcpkg zainstaluje i kompilacji systemu Windows x86. Jeśli portfile określa zależności, vcpkg pobierze i zainstaluje te również. Po pobraniu, vcpkg tworzy bibliotekę przy użyciu, niezależnie od systemu, który korzysta z biblioteki kompilacji. Pliki projektów CMake i MSBuild są preferowane, ale upewnij jest obsługiwane wraz z innymi system kompilacji. Jeśli vcpkg nie może znaleźć określonej kompilacji systemu na komputerze lokalnym, jego pobierze i zainstaluje go.

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

### <a name="list-the-libraries-already-installed"></a>Wyświetlanie bibliotek już zainstalowane
Po zainstalowaniu niektórych bibliotek, można użyć `vcpkg list` co masz:

```cmd
> vcpkg list

boost:x86-windows       1.64-3   Peer-reviewed portable C++ source libraries
bzip2:x86-windows       1.0.6-1  High-quality data compressor.
cpprestsdk:x86-windows  2.9.0-2  C++11 JSON, REST, and OAuth library The C++ REST ...
openssl:x86-windows     1.0.2k-2 OpenSSL is an open source project that provides a...
websocketpp:x86-windows 0.7.0    Library that implements RFC6455 The WebSocket Pro...
zlib:x86-windows        1.2.11   A compression library
```

### <a name="integrate-with-visual-studio"></a>Integracja z programem Visual Studio
#### <a name="per-user"></a>Na użytkownika
Uruchom `vcpkg integrate install` skonfigurować Visual Studio, aby zlokalizować wszystkie pliki nagłówkowe vcpkg i pliki binarne w poszczególnych użytkowników, bez konieczności ręcznej edycji ścieżek katalogi VC ++. Jeśli masz wiele klony w klonowania, w którym możesz uruchomić tego polecenia staje się do nowej lokalizacji domyślnej.

Teraz możesz #include nagłówki po prostu, wpisując folderu/nagłówka, zostanie automatycznie uzupełniać pomóc. Żadne dodatkowe kroki są wymagane do łączenia z biblioteki lub dodanie odwołania do projektu. Na poniższej ilustracji przedstawiono sposób odnajdowania nagłówki azure magazynu cpp w Visual Studio. vcpkg umieszcza jego nagłówków w podfolderze \installed partycjonowanego platformy docelowej. Na poniższym diagramie przedstawiono listę plików dołączanych w `/was` podfolderze biblioteki:

 ![vcpkg integracji Intellisense](media/vcpkg-intellisense.png "vcpkg i Intellisense")  

#### <a name="per-project"></a>W projekcie
Jeśli należy użyć określonej wersji biblioteki, która jest inna niż wersja w wystąpieniu active vcpkg, możesz utworzyć nowy klon vcpkg, zmodyfikuj portfile biblioteki uzyskać wersję potrzebne, a następnie uruchom `vcpkg install <library>`. Następnie można użyć `vcpkg integrate project` do utworzenia pakietu NuGet, który odwołuje się do tej biblioteki, na podstawie na projekt.

### <a name="export-compiled-binaries-and-headers"></a>Eksportuj skompilowane pliki binarne i nagłówki
Wymaganie wszyscy członkowie zespołu, aby pobrać i tworzenie bibliotek może być mało wydajne. Członek zespołu pojedynczego tej pracy, a następnie użyj `vcpkg export` można utworzyć pliku zip, pliki binarne i nagłówki, które można łatwo udostępniać innych członków zespołu. 

### <a name="update-installed-libraries"></a>Biblioteki zainstalowano aktualizację
Publiczny katalogu jest zawsze na bieżąco najnowsze wersje bibliotek. Aby określić, które biblioteki lokalnych są nieaktualne, użyj `vcpkg update`. Po zakończeniu aktualizowanie kolekcji portów do najnowszej wersji katalogu publiczne, po prostu wykonania operacji ściągnięcia git względem repozytorium github lub utworzyć nowy klon i zachować stare hasło, jeśli jest nadal wymagana.

### <a name="contribute-new-libraries"></a>Współtworzenia nowe biblioteki
Może zawierać żadnych bibliotek żądanych w kolekcji prywatnych portów. Aby zasugerować nową biblioteką dla katalogu publiczne 


### <a name="remove-a-library"></a>Usuwanie biblioteki
Typ `vcpkg remove` Aby usunąć zainstalowane biblioteki. Jeśli inne biblioteki zależą od niej, zostanie wyświetlony monit o ponowne uruchomienie polecenia z `--recurse`, który spowoduje, że wszystkie podrzędne biblioteki do usunięcia.

### <a name="customize-vcpkg"></a>Dostosowywanie vcpkg
Można zmodyfikować z klonu vcpkg w żaden sposób, który chcesz. Można tworzyć wiele klony vcpkg i modyfikować portfiles w każdej z nich uzyskać określonych wersji biblioteki lub określić parametry wiersza polecenia. Na przykład w przedsiębiorstwie, jedna grupa deweloperów może działać na oprogramowanie, które ma jeden zestaw zależności, a inna grupa może mieć inny zestaw. Można skonfigurować dwie klonów vcpkg i zmodyfikować każdą z nich pobrać wersje bibliotek i przełączników kompilacji, itd., zgodnie z potrzebami. 

## <a name="the-vcpkg-folder-hierarchy"></a>Hierarchia folderów vcpkg
Wszystkie dane i vcpkg funkcji są całkowicie niezależne w hierarchii jednego katalogu; jest to "instance". Nie ma żadnych ustawień rejestru lub zmiennych środowiskowych. Może mieć dowolną liczbę wystąpień vcpkg na maszynie i będzie przeszkadzają ze sobą. 

Zawartość wystąpienia vcpkg jest: 
- buildtrees — zawiera podfoldery źródeł, z których każda biblioteka jest wbudowana
- Dokumentacja — dokumentacja i przykłady
- pobiera — zbuforowane kopie pobrany narzędzia lub źródeł. vcpkg wyszukuje tutaj najpierw podczas uruchamiania polecenia install.
- zainstalowany — zawiera nagłówki i pliki binarne dla każdej zainstalowanej biblioteki. Integracja z programem VIsual Studio zasadniczo informuje go dodać ten folder do jego ścieżki wyszukiwania.
- Instaluje pakiety — wewnętrzny folder przemieszczania między.
- porty--pliki, które opisują każdej biblioteki w katalogu, jego wersja i umożliwiające pobranie. W razie potrzeby można dodać własne portów.
- skrypty — skryptów (cmake, programu powershell) używanych przez vcpkg.
- toolsrc — kod źródłowy C++ vcpkg i powiązane składniki
- triplets — zawiera ustawienia dla każdej platformy docelowej (np. x86 windows lub platformy uwp x64).

## <a name="command-line-reference"></a>Informacje dotyczące wiersza polecenia
- Wyszukiwanie vcpkg [Paweł] Wyszukaj pakiety dostępne ma zostać utworzony.
- Zainstaluj vcpkg <pkg>...    Instalowanie pakietu
- Usuń vcpkg <pkg>...  Odinstaluj pakiet
- Usuń vcpkg — przestarzałe Odinstaluj wszystkie nieaktualnych opakowania
- vcpkg listy wyświetlanie listy zainstalowanych pakietów
- vcpkg zaktualizować listę pakietów aktualizacji
- Skrót vcpkg <file> [alg] skrótu pliku przez algorytm określonych, domyślne SHA512
- vcpkg integracji instalacji upewnij zainstalowane pakiety dostępne użytkownika na poziomie. Wymaga uprawnień administratora na pierwszym użyciem
- Usuń użytkownika całej Usuń integracji integracji vcpkg
- vcpkg integracji projektu generowanie pakietu nuget odwołujący się do poszczególnych użycia projektu programu VS
- Eksport vcpkg <pkg>... [opt...]    Eksportuje pakiet
- Edytuj vcpkg <pkg> Otwórz port do edycji (używa edytora %, domyślny kod)
- Importuj vcpkg <pkg> importowanie wbudowanych biblioteki
- Utwórz vcpkg <pkg> <url> [archivename] Utwórz nowy pakiet
- właścicielem vcpkg <pat> wyszukiwania plików z zainstalowanych pakietów
- vcpkg pamięci podręcznej listy skompilowanych pakiety w pamięci podręcznej
- Wersja vcpkg Wyświetl informacje o wersji
- vcpkg skontaktuj się z wyświetlania informacji kontaktowych, aby wysłać opinię

### <a name="options"></a>Opcje:
  **`--triplet <t>`**Określ Trzykolumnowa architektury docelowej. (domyślne: `%VCPKG_DEFAULT_TRIPLET%`, zobacz też `vcpkg help triplet`)

  **`--vcpkg-root <path>`**Określ katalog główny vcpkg (domyślne: `%VCPKG_ROOT%`)
