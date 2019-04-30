---
title: Konfigurowanie projektu systemu Linux w języku C++ w programie Visual Studio
ms.date: 11/12/2018
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
ms.openlocfilehash: 84b9242ad5af79ed48d716fb5a35db56428e9a98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389854"
---
# <a name="configure-a-linux-project"></a>Konfigurowanie projektu systemu Linux

W tym temacie opisano sposób konfigurowania projektu systemu Linux w języku C++, który jest oparty na szablonie projektu systemu Linux w programie Visual Studio. Aby uzyskać informacji na temat narzędzia CMake projektów systemu Linux w programie Visual Studio, zobacz [Konfigurowanie projektu CMake systemu Linux ](cmake-linux-project.md).

## <a name="general-settings"></a>Ustawienia ogólne

Dla projektu systemu Linux przy użyciu programu Visual Studio można skonfigurować różne opcje.  Zaznacz, aby wyświetlić te opcje **projektu > właściwości** menu lub kliknij prawym przyciskiem projekt w **Eksploratora rozwiązań** i wybierz **właściwości** z menu kontekstowego. **Ogólne** pojawią się ustawienia.

![Konfiguracja ogólna](media/settings_general.png)

Domyślnie plik wykonywalny (.out) została stworzona za pomocą narzędzia.  Do tworzenia biblioteki statycznej lub dynamicznej lub użyć istniejącego pliku reguł programu make, użyj **typu konfiguracji** zaznaczenia.

Aby uzyskać więcej informacji na temat opcji dostępnych na stronach właściwości, zobacz [dokumentacja strony właściwości projektu systemu Linux](prop-pages-linux.md).

## <a name="remote-settings"></a>Ustawienia zdalnego

Aby zmienić ustawienia odnoszących się do komputera zdalnego systemu Linux, należy skonfigurować opcje zdalnego, które pojawiają się w [ogólne](prop-pages/general-linux.md) ustawienia:

- Aby zmienić komputer docelowy z systemem Linux, użyj **maszyny zdalnej kompilacji** wpisu.  Pozwoli to wybranie jednego z utworzonych wcześniej połączeń.  Aby utworzyć nowy wpis, zobacz [nawiązywanie połączeń z Twojej zdalny komputer z systemem Linux](connect-to-your-remote-linux-computer.md) sekcji.

- **Katalog główny kompilacji zdalnej** Określa lokalizację katalogu głównego, z której projekt jest kompilowany na zdalnym komputerze z systemem Linux.  To domyślnie zostanie **~/projects** chyba że zmieniony.

- **Zdalny katalog projektu kompilacji** jest, gdzie tego określonego projektu zostanie utworzona na zdalnym komputerze z systemem Linux.  To domyślnie zostanie **$(RemoteRootDir)/$(ProjectName)**, które rozszerzy się do katalogu o nazwie po bieżącym projekcie, w katalogu głównym powyżej.

> [!NOTE]
> Aby zmienić domyślne C i Kompilatory języka C++ lub konsolidatora i programu archiwizującego, używany do tworzenia projektu, należy użyć odpowiednie wpisy w **C/C++ > Ogólne** sekcji i **Konsolidator > Ogólne** sekcji.  Te opcje można można ustawić, aby użyć określonej wersji kompilatora GCC lub nawet kompilatora Clang, na przykład. Aby uzyskać więcej informacji, zobacz [właściwości języka C/C++ (Linux C++)](prop-pages/c-cpp-linux.md) i [właściwości konsolidatora (Linux C++)](prop-pages/linker-linux.md).

## <a name="include-directories-and-intellisense-support"></a>Katalogi i obsługę funkcji IntelliSense

**Visual Studio 2017 w wersji 15.6 i starszych:**<br/>
Domyślnie program Visual Studio nie zawiera wszystkie pliki dołączane w poziomie systemu, z komputera z systemem Linux.  Na przykład, elementy w **/usr/obejmują** katalogu nie są obecne w programie Visual Studio.
Aby uzyskać pełne [IntelliSense](/visualstudio/ide/using-intellisense) pomocy technicznej, należy skopiować te pliki do lokalizacji na komputerze deweloperskim i wskaż programu Visual Studio do tej lokalizacji.  Jedną z opcji jest kopiowanie plików za pomocą punktu połączenia usługi (Secure Copy).  W systemie Windows 10, możesz użyć [Bash on Windows](https://msdn.microsoft.com/commandline/wsl/about) do uruchomienia punktu połączenia usługi.  Dla starszych wersji systemu Windows, można użyć ciągu [narzędzia PSCP (PuTTY Secure Copy)](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html).

Aby skopiować pliki, używając polecenia podobnego do następującego:

`scp -r linux_username@remote_host:/usr/include .`

Oczywiście zastąpić **linux_username** i **remote_host** wartości powyżej co to jest odpowiednie w Twoim własnym środowisku.

Gdy pliki są kopiowane, użyć **katalogi VC ++** elementu we właściwościach projektu programu Visual Studio stwierdzić, gdzie można znaleźć plików dołączanych dodatkowe, które właśnie zostały skopiowane.

![Katalogi VC ++](media/settings_directories.png)

**Visual Studio 2017 w wersji 15.7 lub nowszej:**<br/>
Zobacz [zarządzać zdalnych nagłówków funkcji IntelliSense](#remote_intellisense).

## <a name="copy-sources"></a>Kopiuj źródła

Podczas kompilowania, pliki źródłowe na komputerze są skopiowane na komputer z systemem Linux i kompilowane istnieje.  Domyślnie wszystkie źródła w projekcie programu Visual Studio są kopiowane do lokalizacji, w oknie Ustawienia powyżej.  Dodatkowe źródła mogą być również dodawane do listy lub kopiowania źródeł można wyłączyć całkowicie, co jest ustawieniem domyślnym dla projektu pliku reguł programu make.

- **Źródła do skopiowania** Określa, jakie źródła są kopiowane do komputera zdalnego.  Domyślnie  **\@(SourcesToCopyRemotely)** wartość domyślna to wszystkich plikach kodu źródłowego w projekcie, ale nie ma żadnych plików zasobów lub zasobu, taką jak obrazy.

- **Kopiuj źródła** można włączyć i wyłączyć pozwala włączać i wyłączać, skopiowanie plików źródłowych do komputera zdalnego.

- **Dodatkowe źródła do skopiowania** pozwala na dodawanie dodatkowych plików źródłowych, które zostaną skopiowane do systemu zdalnego.  Można określić listy podzielonej średnikami, lub możesz użyć **: =** składni, aby określić nazwę lokalne i zdalne do użycia:

`C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>Zdarzenia kompilacji

Ponieważ wszystkie kompilacji dzieje się na komputerze zdalnym, kilka dodatkowych zdarzeń kompilacji zostały dodane do sekcji zdarzenia kompilacji we właściwościach projektu.  Są to **zdalne zdarzenie Prekompilacyjne**, **zdalne zdarzenie poprzedzające Link**, i **zdalne zdarzenie Pokompilacyjne**i na komputerze zdalnym przed lub po poszczególnych kroków w proces.

![Zdarzenia kompilacji](media/settings_buildevents.png)

## <a name="remote_intellisense"></a> Funkcja IntelliSense dla zdalnych nagłówków (Visual Studio 2017 wersji 15.7 lub nowszej)

Po dodaniu nowego połączenia **Menedżera połączeń**, Visual Studio automatycznie wykrywa katalogi dołączania dla kompilatora w systemie zdalnym. Visual Studio, a następnie pakuje, jak i kopiuje pliki do katalogu na komputerze lokalnym Windows. Po tym zawsze gdy używasz tego połączenia w projekcie programu Visual Studio lub narzędzia CMake nagłówków w tych katalogach służą do zapewniania funkcji IntelliSense.

Tej funkcji zależy od konieczności zip zainstalowane maszyny z systemem Linux. Za pomocą tego polecenia apt-get, można zainstalować pliku zip:

```cmd
apt install zip
```

Do zarządzania pamięcią podręczną usługi nagłówka, przejdź do **Narzędzia > Opcje, wiele Platform > Menedżer połączeń > Menedżer IntelliSense nagłówki zdalnego**. Aby zaktualizować pamięci podręcznych nagłówków po wprowadzeniu zmian na maszynie z systemem Linux, wybierz połączenia zdalnego, a następnie wybierz **aktualizacji**. Wybierz **Usuń** usunąć nagłówki bez usuwania samo połączenie. Wybierz **Eksploruj** można otworzyć lokalnego katalogu w **Eksploratora plików**. Ten folder należy traktować jako tylko do odczytu. Aby pobrać nagłówki dla istniejącego połączenia, który został utworzony przed w wersji 15.3, wybierz pozycję Połącz, a następnie wybierz pozycję **Pobierz**.

![Nagłówek zdalny IntelliSense](media/remote-header-intellisense.png)

## <a name="see-also"></a>Zobacz także

[Ustaw kompilatora i właściwości kompilacji](../build/working-with-project-properties.md)<br/>
[Właściwości ogólne C++ (Linux C++)](../linux/prop-pages/general-linux.md)<br/>
[Katalogi VC ++ (Linux C++)](../linux/prop-pages/directories-linux.md)<br/>
[Kopiuj źródła właściwości projektu (Linux C++)](../linux/prop-pages/copy-sources-project.md)<br/>
[Tworzenie właściwości zdarzenia (Linux C++)](../linux/prop-pages/build-events-linux.md)
