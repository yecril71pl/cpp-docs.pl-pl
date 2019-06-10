---
title: Konfigurowanie projektu systemu Linux w języku C++ w programie Visual Studio
ms.date: 06/07/2019
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
ms.openlocfilehash: 5acd9edeef8f09f86c394c39939d8408821dd691
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821570"
---
# <a name="configure-a-linux-project"></a>Konfigurowanie projektu systemu Linux

::: moniker range="vs-2015"

Pomoc techniczna Linux support jest dostępne w programie Visual Studio 2017 i nowszych wersjach.

::: moniker-end

W tym temacie opisano sposób konfigurowania C++ projektu systemu Linux, zgodnie z opisem w [Utwórz nową C++ projektu systemu Linux w programie Visual Studio](create-a-new-linux-project.md). Dla projektów CMake systemu Linux, zobacz [Konfigurowanie projektu CMake systemu Linux ](cmake-linux-project.md). 

Można skonfigurować projektu systemu Linux pod kątem fizycznych maszyny z systemem Linux, maszyny wirtualnej lub [podsystem Windows dla systemu Linux](/windows/wsl/about) (WSL). 

::: moniker range="vs-2019"

**Visual Studio 2019 wersji 16.1**:

- Podczas określania wartości WSL, możesz uniknąć operacji kopiowania, które są niezbędne do kompilowania i technologii IntelliSense podczas określania wartości zdalnych systemów Linux.

- Można określić oddzielne elementów w systemie Linux do tworzenia i debugowania.

::: moniker-end

## <a name="general-settings"></a>Ustawienia ogólne

Aby wyświetlić opcje konfiguracji, wybierz **projektu > właściwości** menu lub kliknij prawym przyciskiem projekt w **Eksploratora rozwiązań** i wybierz **właściwości** z kontekstu menu. **Ogólne** pojawią się ustawienia.

![Konfiguracja ogólna](media/settings_general.png)

Domyślnie plik wykonywalny (.out) została stworzona za pomocą narzędzia. Do tworzenia biblioteki statycznej lub dynamicznej lub użyć istniejącego pliku reguł programu make, użyj **typu konfiguracji** ustawienie.

Aby uzyskać więcej informacji na temat ustawień na stronach właściwości, zobacz [dokumentacja strony właściwości projektu systemu Linux](prop-pages-linux.md).

## <a name="remote-settings"></a>Ustawienia zdalnego

Aby zmienić ustawienia odnoszących się do komputera zdalnego systemu Linux, należy skonfigurować ustawienia zdalnego, które są wyświetlane w obszarze [ogólne](prop-pages/general-linux.md).

- Aby określić komputera z systemem Linux zdalnego docelowego, użyj **maszyny zdalnej kompilacji** wpisu. Pozwoli to wybranie jednego z utworzonych wcześniej połączeń. Aby utworzyć nowy wpis, zobacz [nawiązywanie połączeń z Twojej zdalny komputer z systemem Linux](connect-to-your-remote-linux-computer.md) sekcji.

   ![Utwórz maszynę](media/remote-build-machine-vs2019.png)

   ::: moniker range="vs-2019"

   **Visual Studio 2019 wersji 16.1**: Docelowe podsystemu Windows dla systemu Linux, kliknij strzałkę w dół, aby uzyskać **zestawu narzędzi platformy** i wybierz polecenie **WSL_1_0**. Inne opcje zdalnego zniknie i ścieżkę do domyślnej powłoki WSL pojawi się w ich miejsce:

   ![WSL maszynę kompilacji](media/wsl-remote-vs2019.png)

   W przypadku instalacji WSL side-by-side można określić inną ścieżkę. Aby uzyskać więcej informacji na temat zarządzania wieloma dystrybucje, zobacz [zarządzanie i Konfigurowanie podsystemu Windows dla systemu Linux](/windows/wsl/wsl-config#set-a-default-distribution).

   Możesz określić inny element docelowy do debugowania na **właściwości konfiguracji** > **debugowanie** strony.

   ::: moniker-end

- **Katalog główny kompilacji zdalnej** Określa lokalizację katalogu głównego, z której projekt jest kompilowany na zdalnym komputerze z systemem Linux. To domyślnie zostanie **~/projects** chyba że zmieniony.

- **Zdalny katalog projektu kompilacji** jest, gdzie tego określonego projektu zostanie utworzona na zdalnym komputerze z systemem Linux. To domyślnie zostanie **$(RemoteRootDir)/$(ProjectName)** , które rozszerzy się do katalogu o nazwie po bieżącym projekcie, w katalogu głównym powyżej.

> [!NOTE]
> Aby zmienić domyślne C i Kompilatory języka C++ lub konsolidatora i programu archiwizującego, używany do tworzenia projektu, należy użyć odpowiednie wpisy w **C/C++ > Ogólne** sekcji i **Konsolidator > Ogólne** sekcji. Można określić określonej wersji kompilatora GCC lub Clang, na przykład. Aby uzyskać więcej informacji, zobacz [właściwości języka C/C++ (Linux C++)](prop-pages/c-cpp-linux.md) i [właściwości konsolidatora (Linux C++)](prop-pages/linker-linux.md).

## <a name="copy-sources-remote-systems-only"></a>Kopiuj źródła (tylko w przypadku systemów zdalnych)

::: moniker range="vs-2019"

Ta sekcja nie ma zastosowania, gdy WSL.

::: moniker-end

Podczas kompilowania w systemach zdalnych, pliki źródłowe na komputerze są skopiowane na komputer z systemem Linux i kompilowane istnieje. Domyślnie wszystkie źródła w projekcie programu Visual Studio są kopiowane do lokalizacji, w oknie Ustawienia powyżej. Dodatkowe źródła mogą być również dodawane do listy lub kopiowania źródeł można wyłączyć całkowicie, co jest ustawieniem domyślnym dla projektu pliku reguł programu make.

- **Źródła do skopiowania** Określa, jakie źródła są kopiowane do komputera zdalnego. Domyślnie  **\@(SourcesToCopyRemotely)** wartość domyślna to wszystkich plikach kodu źródłowego w projekcie, ale nie ma żadnych plików zasobów lub zasobu, taką jak obrazy.

- **Kopiuj źródła** można włączyć i wyłączyć pozwala włączać i wyłączać, skopiowanie plików źródłowych do komputera zdalnego.

- **Dodatkowe źródła do skopiowania** pozwala na dodawanie dodatkowych plików źródłowych, które zostaną skopiowane do systemu zdalnego. Można określić listy podzielonej średnikami, lub możesz użyć **: =** składni, aby określić nazwę lokalne i zdalne do użycia:

`C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>Zdarzenia kompilacji

Ponieważ wszystkie kompilacji dzieje się na komputerze zdalnym (lub WSL), kilka dodatkowych zdarzeń kompilacji zostały dodane do sekcji zdarzenia kompilacji we właściwościach projektu. Są to **zdalne zdarzenie Prekompilacyjne**, **zdalne zdarzenie poprzedzające Link**, i **zdalne zdarzenie Pokompilacyjne**i na komputerze zdalnym przed lub po poszczególnych kroków w proces.

![Zdarzenia kompilacji](media/settings_buildevents.png)

## <a name="remote_intellisense"></a> Funkcja IntelliSense dla nagłówków w systemach zdalnych

::: moniker range="vs-2019"

Ta sekcja nie ma zastosowania, gdy WSL.

::: moniker-end

Po dodaniu nowego połączenia **Menedżera połączeń**, Visual Studio automatycznie wykrywa katalogi dołączania dla kompilatora w systemie zdalnym. Visual Studio, a następnie pakuje, jak i kopiuje pliki do katalogu na komputerze lokalnym Windows. Po tym zawsze gdy używasz tego połączenia w projekcie programu Visual Studio lub narzędzia CMake nagłówków w tych katalogach służą do zapewniania funkcji IntelliSense.

Tej funkcji zależy od konieczności zip zainstalowane maszyny z systemem Linux. Za pomocą tego polecenia apt-get, można zainstalować pliku zip:

```cmd
apt install zip
```

Do zarządzania pamięcią podręczną usługi nagłówka, przejdź do **Narzędzia > Opcje, wiele Platform > Menedżer połączeń > Menedżer IntelliSense nagłówki zdalnego**. Aby zaktualizować pamięci podręcznych nagłówków po wprowadzeniu zmian na maszynie z systemem Linux, wybierz połączenia zdalnego, a następnie wybierz **aktualizacji**. Wybierz **Usuń** usunąć nagłówki bez usuwania samo połączenie. Wybierz **Eksploruj** można otworzyć lokalnego katalogu w **Eksploratora plików**. Ten folder należy traktować jako tylko do odczytu. Aby pobrać nagłówki dla istniejącego połączenia, który został utworzony przed Visual Studio 2017 w wersji 15.3, wybierz połączenie a następnie wybierz pozycję **Pobierz**.

::: moniker range="vs-2017"

![Nagłówek zdalny IntelliSense](media/remote-header-intellisense.png)

::: moniker-end

::: moniker range="vs-2019"

![Nagłówek zdalny IntelliSense](media/connection-manager-vs2019.png)

Można włączyć rejestrowanie, aby ułatwić rozwiązywanie problemów:

![Rejestrowanie zdalne](media/remote-logging-vs2019.png)

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Ustaw kompilatora i właściwości kompilacji](../build/working-with-project-properties.md)<br/>
[Właściwości ogólne C++ (Linux C++)](../linux/prop-pages/general-linux.md)<br/>
[Katalogi VC ++ (Linux C++)](../linux/prop-pages/directories-linux.md)<br/>
[Kopiuj źródła właściwości projektu (Linux C++)](../linux/prop-pages/copy-sources-project.md)<br/>
[Tworzenie właściwości zdarzenia (Linux C++)](../linux/prop-pages/build-events-linux.md)
