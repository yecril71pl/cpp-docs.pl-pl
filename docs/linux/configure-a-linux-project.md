---
title: Konfigurowanie projektu systemu Linux w języku C++ w programie Visual Studio
ms.date: 06/11/2019
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
ms.openlocfilehash: 50d5df0e25e82238297458ec7fedb955654e525b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "80150969"
---
# <a name="configure-a-linux-project"></a>Konfigurowanie projektu systemu Linux

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

W tym temacie opisano sposób konfigurowania projektu systemu Linux w języku C++ zgodnie z [opisem w artykule Tworzenie nowego projektu systemu Linux w programie Visual Studio.](create-a-new-linux-project.md) Zobacz też: Konfigurowanie projektu CMake dla systemu Windows w programie [CMake .](cmake-linux-project.md)

Można skonfigurować projekt systemu Linux do docelowej fizycznej maszyny Linux, maszyny wirtualnej lub [podsystemu windows dla systemu Linux](/windows/wsl/about) (WSL).

::: moniker range="vs-2019"

**Visual Studio 2019 w wersji 16.1**:

- Podczas kierowania na WSL można uniknąć operacji kopiowania, które są niezbędne do tworzenia i IntelliSense podczas kierowania zdalnych systemów Linux.

- Można określić oddzielne cele systemu Linux do tworzenia i debugowania.

::: moniker-end

## <a name="general-settings"></a>Ustawienia ogólne

Aby wyświetlić opcje konfiguracji, wybierz menu **Właściwości projektu >** lub kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierz polecenie **Właściwości** z menu kontekstowego. Zostaną wyświetlone ustawienia **ogólne.**

![Konfiguracja ogólna](media/settings_general.png)

Domyślnie jest zbudowany plik wykonywalny (.out). Aby utworzyć bibliotekę statyczną lub dynamiczną lub użyć istniejącego pliku Makefile, należy użyć ustawienia **Typ konfiguracji.**

Aby uzyskać więcej informacji na temat ustawień na stronach właściwości, zobacz [Odwołanie do strony właściwości projektu Linux](prop-pages-linux.md).

## <a name="remote-settings"></a>Ustawienia zdalne

Aby zmienić ustawienia dotyczące zdalnego komputera z systemem Linux, skonfiguruj ustawienia zdalne wyświetlane w obszarze [Ogólne](prop-pages/general-linux.md).

- Aby określić zdalny docelowy komputer z systemem Linux, użyj wpisu **Maszyna kompilacji zdalnej.** Umożliwi to wybranie jednego z połączeń utworzonych wcześniej. Aby utworzyć nowy wpis, zobacz sekcję [Łączenie z komputerem z systemem Linux.](connect-to-your-remote-linux-computer.md)

   ![Zbuduj maszynę](media/remote-build-machine-vs2019.png)

   ::: moniker range="vs-2019"

   **Visual Studio 2019 w wersji 16.1**: Aby kierować podsystem windows dla systemu Linux, kliknij strzałkę w dół dla **zestawu narzędzi platformy** i wybierz **WSL_1_0**. Inne opcje zdalnego znikną, a ścieżka do domyślnej powłoki WSL pojawi się w ich miejsce:

   ![Maszyna do budowania WSL](media/wsl-remote-vs2019.png)

   Jeśli masz instalacje WSL obok siebie, możesz określić inną ścieżkę w tym miejscu. Aby uzyskać więcej informacji na temat zarządzania wieloma dystrybucjami, zobacz [Zarządzanie podsystemem Windows i konfigurowanie go dla systemu Linux](/windows/wsl/wsl-config#set-a-default-distribution).

   Można określić inny obiekt docelowy do debugowania na stronie > **Debugowanie** **właściwości konfiguracji.**

   ::: moniker-end

- **Katalog główny kompilacji zdalnej** określa główną lokalizację, w której projekt jest zbudowany na zdalnym komputerze z systemem Linux. Domyślnie będzie to **~/projekty,** chyba że zostaną zmienione.

- **Remote Build Project Directory jest,** gdzie ten konkretny projekt zostanie zbudowany na zdalnym komputerze z systemem Linux. Domyślnie wartość **$(RemoteRootDir)/$(ProjectName)** zostanie rozwinięta do katalogu nazwanego po bieżącym projekcie w katalogu głównym ustawionym powyżej.

> [!NOTE]
> Aby zmienić domyślne kompilatory C i C++ lub konsolidator i archiver używany do tworzenia projektu, należy użyć odpowiednich wpisów w sekcji **C/C++ > Ogólne** i **Linker > Ogólne** sekcji. Można określić pewną wersję GCC lub Clang, na przykład. Aby uzyskać więcej informacji, zobacz [Właściwości C/C++ (Linux C++)](prop-pages/c-cpp-linux.md) i [Właściwości konsolidatora (Linux C++)](prop-pages/linker-linux.md).

## <a name="copy-sources-remote-systems-only"></a>Źródła kopiowania (tylko systemy zdalne)

::: moniker range="vs-2019"

Ta sekcja nie ma zastosowania podczas kierowania na WSL.

::: moniker-end

Podczas tworzenia na systemach zdalnych pliki źródłowe na komputerze deweloperskim są kopiowane na komputer z systemem Linux i tam kompilowane. Domyślnie wszystkie źródła w projekcie programu Visual Studio są kopiowane do lokalizacji ustawionych w powyższych ustawieniach. Jednak dodatkowe źródła można również dodać do listy lub kopiowanie źródeł można całkowicie wyłączyć, co jest ustawieniem domyślnym dla projektu Makefile.

- **Źródła do kopiowania** określa, które źródła są kopiowane na komputer zdalny. Domyślnie ** \@(SourcesToCopyRemotely) domyślnie** wszystkie pliki kodu źródłowego w projekcie, ale nie zawiera żadnych plików zasobów/zasobów, takich jak obrazy.

- **Źródła kopiowania** można włączać i wyłączać, aby włączyć i wyłączyć kopiowanie plików źródłowych na komputer zdalny.

- **Dodatkowe źródła do kopiowania** umożliwia dodanie dodatkowych plików źródłowych, które zostaną skopiowane do systemu zdalnego. Można określić listę rozdzielaną średnika lub użyć składni **:=** do określenia nazwy lokalnej i zdalnej do użycia:

`C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>Tworzenie zdarzeń

Ponieważ cała kompilacja odbywa się na komputerze zdalnym (lub WSL), kilka dodatkowych zdarzeń kompilacji zostały dodane do sekcji Zdarzenia kompilacji we właściwościach projektu. Są to **zdarzenie zdalnego wstępnego budowania,** **zdalne zdarzenie przedłączem**i **zdalne zdarzenie po kompilacji**i będą występować na komputerze zdalnym przed lub po poszczególnych krokach procesu.

![Tworzenie zdarzeń](media/settings_buildevents.png)

## <a name="intellisense-for-headers-on-remote-systems"></a><a name="remote_intellisense"></a>IntelliSense dla nagłówków w systemach zdalnych

Po dodaniu nowego połączenia w **Menedżerze połączeń**program Visual Studio automatycznie wykrywa katalogi dołączane dla kompilatora w systemie zdalnym. Program Visual Studio następnie skompresuje i kopiuje te pliki do katalogu na lokalnym komputerze z systemem Windows. Po tym, gdy używasz tego połączenia w programie Visual Studio lub CMake projektu, nagłówki w tych katalogach są używane do zapewnienia IntelliSense.

> [!NOTE]
> W programie Visual Studio 2019 w wersji 16.5 lub nowszej zoptymalizowano zdalną kopię nagłówka. Nagłówki są teraz kopiowane na żądanie podczas otwierania projektu systemu Linux lub konfigurowania CMake dla obiektu docelowego systemu Linux. Kopia występuje w tle na podstawie projektu, na podstawie określonych kompilatorów projektu. Aby uzyskać więcej informacji, zobacz [Ulepszenia dokładności i wydajności systemu Linux IntelliSense](https://devblogs.microsoft.com/cppblog/improvements-to-accuracy-and-performance-of-linux-intellisense/).

Ta funkcja zależy od maszyny Linux po zainstalowaniu zip. Zip można zainstalować za pomocą tego polecenia apt-get:

```cmd
sudo apt install zip
```

Aby zarządzać pamięcią podręczną nagłówka, przejdź do **pozycji Narzędzia > Options, Menedżer połączeń między platformami > > Menedżer zdalnego sterowania IntelliSense .** Aby zaktualizować pamięć podręczną nagłówka po wyrobieniu zmian na komputerze z systemem Linux, wybierz połączenie zdalne, a następnie wybierz pozycję **Aktualizuj**. Wybierz **pozycję Usuń,** aby usunąć nagłówki bez usuwania samego połączenia. Wybierz **eksploruj,** aby otworzyć katalog lokalny w **Eksploratorze plików**. Potraktuj ten folder jako tylko do odczytu. Aby pobrać nagłówki dla istniejącego połączenia utworzonego przed programem Visual Studio 2017 w wersji 15.3, wybierz połączenie, a następnie wybierz pozycję **Pobierz**.

::: moniker range="vs-2017"

![Zdalny nagłówek IntelliSense](media/remote-header-intellisense.png)

::: moniker-end

::: moniker range="vs-2019"

![Zdalny nagłówek IntelliSense](media/connection-manager-vs2019.png)

Rejestrowanie można włączyć, aby ułatwić rozwiązywanie problemów:

![Zdalne rejestrowanie](media/remote-logging-vs2019.png)

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Ustawianie właściwości kompilatora i kompilacji](../build/working-with-project-properties.md)<br/>
[Właściwości ogólne języka C++ (Linux C++)](../linux/prop-pages/general-linux.md)<br/>
[Katalogi VC++ (Linux C++)](../linux/prop-pages/directories-linux.md)<br/>
[Właściwości projektu Kopiuj źródła (Linux C++)](../linux/prop-pages/copy-sources-project.md)<br/>
[Właściwości zdarzenia kompilacji (Linux C++)](../linux/prop-pages/build-events-linux.md)
