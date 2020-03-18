---
title: Konfigurowanie projektu C++ systemu Linux w programie Visual Studio
ms.date: 06/11/2019
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
ms.openlocfilehash: 5d42ca587946d3b5adcbd3b6fe35a6c1e1bb9ae8
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419386"
---
# <a name="configure-a-linux-project"></a>Konfigurowanie projektu systemu Linux

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

W tym temacie opisano sposób konfigurowania projektu C++ systemu Linux zgodnie z opisem w artykule [Tworzenie C++ nowego projektu systemu Linux w programie Visual Studio](create-a-new-linux-project.md). W przypadku projektów CMake Linux zobacz [Configure a Linux CMAKE Project ](cmake-linux-project.md). 

Istnieje możliwość skonfigurowania projektu systemu Linux, który będzie przeznaczony dla fizycznego komputera z systemem Linux, maszyny wirtualnej lub [podsystemu Windows for Linux](/windows/wsl/about) (WSL). 

::: moniker range="vs-2019"

**Program Visual Studio 2019 w wersji 16,1**:

- W przypadku kierowania WSL można uniknąć operacji kopiowania, które są niezbędne do kompilowania i IntelliSense w przypadku kierowania zdalnego systemu Linux.

- Można określić oddzielne elementy docelowe systemu Linux na potrzeby kompilowania i debugowania.

::: moniker-end

## <a name="general-settings"></a>Ustawienia ogólne

Aby wyświetlić opcje konfiguracji, wybierz menu **właściwości > projektu** lub kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości** z menu kontekstowego. Pojawią się ustawienia **Ogólne** .

![Konfiguracja ogólna](media/settings_general.png)

Domyślnie tworzony jest plik wykonywalny (. out). Aby utworzyć bibliotekę statyczną lub dynamiczną lub użyć istniejącego pliku reguł programu make, użyj ustawienia **typu konfiguracji** .

Aby uzyskać więcej informacji na temat ustawień na stronach właściwości, zobacz temat [Informacje o stronie właściwości projektu systemu Linux](prop-pages-linux.md).

## <a name="remote-settings"></a>Ustawienia zdalne

Aby zmienić ustawienia odnoszące się do zdalnego komputera z systemem Linux, skonfiguruj ustawienia zdalne, które są wyświetlane w obszarze [Ogólne](prop-pages/general-linux.md).

- Aby określić zdalny docelowy komputer z systemem Linux, użyj wpisu **zdalnego komputera kompilacji** . Umożliwi to wybranie jednego z utworzonych wcześniej połączeń. Aby utworzyć nowy wpis, zobacz sekcję [łączenie się z komputerem zdalnym z systemem Linux](connect-to-your-remote-linux-computer.md) .

   ![Maszyna kompilacji](media/remote-build-machine-vs2019.png)

   ::: moniker range="vs-2019"

   **Visual Studio 2019 w wersji 16,1**: aby kierować podsystem Windows dla systemu Linux, kliknij strzałkę w dół dla zestawu **narzędzi platformy** i wybierz **WSL_1_0**. Inne opcje zdalne znikną, a ścieżka do domyślnej powłoki WSL pojawi się w ich miejscu:

   ![Maszyna kompilacji WSL](media/wsl-remote-vs2019.png)

   W przypadku równoległych instalacji WSL można tutaj określić inną ścieżkę. Więcej informacji o zarządzaniu wieloma dystrybucjemi znajduje się w temacie [Zarządzanie i Konfigurowanie podsystemu systemu Windows w systemie Linux](/windows/wsl/wsl-config#set-a-default-distribution).

   Możesz określić inny cel dla debugowania na stronie **Właściwości konfiguracji** > **debugowanie** .

   ::: moniker-end

- **Katalog główny kompilacji zdalnej** określa lokalizację główną, w której projekt jest skompilowany na komputerze zdalnego systemu Linux. Wartość domyślna to **~/projects** , chyba że zostanie zmieniona.

- **Zdalny katalog projektu kompilacji** to miejsce, w którym ten konkretny projekt zostanie skompilowany na zdalnym komputerze z systemem Linux. Spowoduje to przekroczenie wartości **$ (RemoteRootDir)/$ (ProjectName)** , która zostanie rozszerzona do katalogu o nazwie po bieżącym projekcie, w katalogu głównym powyższego.

> [!NOTE]
> Aby zmienić domyślny język C i C++ kompilatory albo konsolidator i archiwum używane do kompilowania projektu, należy użyć odpowiednich wpisów w sekcji **Ogólne C/C++ >** i **konsolidatora > Ogólne** . Możesz na przykład określić określoną wersję programu w ramach usługi lub Clang. Aby uzyskać więcej informacji, zobacz [CC++ /właściwości C++(Linux)](prop-pages/c-cpp-linux.md) i [Właściwości konsolidatora (Linux C++)](prop-pages/linker-linux.md).

## <a name="copy-sources-remote-systems-only"></a>Kopiuj źródła (tylko systemy zdalne)

::: moniker range="vs-2019"

Ta sekcja nie ma zastosowania, jeśli celem jest WSL.

::: moniker-end

Podczas kompilowania w systemach zdalnych pliki źródłowe na komputerze deweloperskim są kopiowane do komputera z systemem Linux i kompilowane w tym miejscu. Domyślnie wszystkie źródła w projekcie programu Visual Studio są kopiowane do lokalizacji ustawionych w powyższych ustawieniach. Można jednak również dodać do listy dodatkowe źródła lub skopiować źródła, które są domyślnie wyłączone dla projektu reguł programu make.

- **Źródła do skopiowania** określają, które źródła są kopiowane do komputera zdalnego. Domyślnie **\@(SourcesToCopyRemotely)** jest wartością domyślną dla wszystkich plików kodu źródłowego w projekcie, ale nie zawiera żadnych plików zasobów/zasobu, takich jak obrazy.

- **Źródła kopiowania** można włączać i wyłączać w celu włączenia i wyłączenia kopiowania plików źródłowych na komputer zdalny.

- **Dodatkowe źródła do skopiowania** umożliwiają dodanie dodatkowych plików źródłowych, które zostaną skopiowane do systemu zdalnego. Można określić listę rozdzielaną średnikami lub użyć składni **: =** , aby określić nazwę lokalną i zdalną do użycia:

`C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>Zdarzenia kompilacji

Ponieważ cała kompilacja odbywa się na komputerze zdalnym (lub WSL), kilka dodatkowych zdarzeń kompilacji zostało dodanych do sekcji zdarzenia kompilacji we właściwościach projektu. Są to **zdalne zdarzenie poprzedzające kompilację**, **zdalne zdarzenie poprzedzające konsolidację**i **zdalne zdarzenie po kompilacji**, które nastąpi na komputerze zdalnym przed lub po poszczególnych krokach procesu.

![Zdarzenia kompilacji](media/settings_buildevents.png)

## <a name="remote_intellisense"></a>Funkcja IntelliSense dla nagłówków w systemach zdalnych

Po dodaniu nowego połączenia w **Menedżerze połączeń**program Visual Studio automatycznie wykrywa katalogi dołączania dla kompilatora w systemie zdalnym. Program Visual Studio następnie Zips pliki i skopiuje je do katalogu na lokalnym komputerze z systemem Windows. Po wykonaniu tej operacji, za każdym razem, gdy korzystasz z tego połączenia w projekcie programu Visual Studio lub CMake, nagłówki w tych katalogach są używane do udostępniania technologii IntelliSense.

> [!NOTE]
> W programie Visual Studio 2019 w wersji 16,5 lub nowszej, zdalna kopia nagłówka została zoptymalizowana. Nagłówki są teraz kopiowane na żądanie podczas otwierania projektu systemu Linux lub konfigurowania CMake dla docelowego systemu Linux. Kopia odbywa się w tle dla każdego projektu, na podstawie określonych kompilatorów projektu. Aby uzyskać więcej informacji, zobacz [ulepszenia dokładności i wydajności funkcji IntelliSense systemu Linux](https://devblogs.microsoft.com/cppblog/improvements-to-accuracy-and-performance-of-linux-intellisense/).

Ta funkcja jest zależna od komputera z systemem Linux z zainstalowanym zip. Plik zip można zainstalować za pomocą tego polecenia apt-get:

```cmd
sudo apt install zip
```

Aby zarządzać pamięcią podręczną nagłówków, przejdź do **opcji narzędzia > opcje, Międzyplatformowe > Menedżer połączeń > zdalnych nagłówków programu IntelliSense**. Aby zaktualizować pamięć podręczną nagłówka po wprowadzeniu zmian na komputerze z systemem Linux, wybierz połączenie zdalne, a następnie wybierz pozycję **Aktualizuj**. Wybierz pozycję **Usuń** , aby usunąć nagłówki bez usuwania samego połączenia. Wybierz pozycję **Eksploruj** , aby otworzyć katalog lokalny w **Eksploratorze plików**. Traktuj ten folder jako tylko do odczytu. Aby pobrać nagłówki dla istniejącego połączenia, które zostało utworzone przed program Visual Studio 2017 w wersji 15,3, wybierz połączenie, a następnie wybierz pozycję **Pobierz**.

::: moniker range="vs-2017"

![Funkcja IntelliSense nagłówka zdalnego](media/remote-header-intellisense.png)

::: moniker-end

::: moniker range="vs-2019"

![Funkcja IntelliSense nagłówka zdalnego](media/connection-manager-vs2019.png)

Możesz włączyć rejestrowanie, aby pomóc w rozwiązywaniu problemów:

![Rejestrowanie zdalne](media/remote-logging-vs2019.png)

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Ustawianie właściwości kompilatora i Build](../build/working-with-project-properties.md)<br/>
[C++Właściwości ogólne (Linux C++)](../linux/prop-pages/general-linux.md)<br/>
[Katalogi VC + + (Linux C++)](../linux/prop-pages/directories-linux.md)<br/>
[Właściwości projektu kopiowania źródeł (Linux C++)](../linux/prop-pages/copy-sources-project.md)<br/>
[Właściwości zdarzenia kompilacji (Linux C++)](../linux/prop-pages/build-events-linux.md)
