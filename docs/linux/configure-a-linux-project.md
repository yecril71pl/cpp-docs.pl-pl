---
title: Konfigurowanie projektu C++ Linux w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2017
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 799eb17ec5cb34cdd0e266f389ad77cb427c7577
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="configure-a-linux-project"></a>Konfigurowanie projektu systemu Linux
W tym temacie opisano sposób konfigurowania projektu programu Visual Studio systemu Linux. Informacje CMake projekty systemu Linux, zobacz [Konfigurowanie projektu CMake Linux ](cmake-linux-project.md).

## <a name="general-settings"></a>Ustawienia ogólne
Można skonfigurować różne opcje dla projektu systemu Linux przy użyciu programu Visual Studio.  Aby wyświetlić te opcje, wybierz **projektu > właściwości** menu lub kliknij prawym przyciskiem projekt w myszy **Eksploratora rozwiązań** i wybierz **właściwości** z menu kontekstowego. **Ogólne** pojawią się ustawienia.

![Konfiguracja ogólna](media/settings_general.png)

Domyślnie plik wykonywalny (.out) jest tworzone za pomocą narzędzia.  Do tworzenia biblioteki statycznej lub dynamicznej lub użyć istniejącego pliku reguł programu make, należy użyć **typu konfiguracji** zaznaczenia.

## <a name="remote-settings"></a>Ustawienia zdalnego
Aby zmienić ustawienia odnoszące się do komputera zdalnego systemu Linux, należy skonfigurować opcje zdalnego, które są widoczne w **ogólne** ustawienia:

* Aby zmienić na komputerze docelowym z systemem Linux, użyj **maszyny zdalnej kompilacji** wpisu.  Dzięki temu można wybrać jedno z połączeń utworzone wcześniej.  Aby utworzyć nowy wpis, zobacz [nawiązywania połączenia zdalnego komputer Linux](connect-to-your-remote-linux-computer.md) sekcji.

* **Zdalnego katalogu głównego kompilacji** Określa lokalizację katalogu głównego, w którym projekt jest budowany na zdalnym komputerze z systemem Linux.  To domyślnie zostanie ustawiona **~/projects** chyba, że zmienione.

* **Zdalnego katalogu kompilacji projektu** jest, gdzie to określonego projektu zostanie utworzona na zdalnym komputerze z systemem Linux.  To domyślnie zostanie ustawiona **$(RemoteRootDir)/$(ProjectName)**, które rozszerzą na katalog o nazwie po bieżącego projektu, w katalogu głównym powyżej.

> [!NOTE]
> Aby zmienić domyślne C i kompilatory C++ lub konsolidatora i Archiver używany do tworzenia projektu, należy użyć odpowiednie wpisy w **C/C++ > Ogólne** sekcji i **konsolidatora > Ogólne** sekcji.  Te mogą być skonfigurowane do niektórych wersji GCC lub nawet kompilatora Clang, np.

## <a name="vc-directories"></a>Katalogi VC ++
Domyślnie program Visual Studio nie ma żadnych plików dołączanych poziom systemu z komputera z systemem Linux.  Na przykład elementów w **/usr/include** katalogu nie są dostępne w programie Visual Studio.  Aby uzyskać pełne [IntelliSense](/visualstudio/ide/using-intellisense) pomocy technicznej, należy skopiować te pliki do określonej lokalizacji na komputerze deweloperskim, a następnie wskaż Visual Studio z tej lokalizacji.  Jedną z opcji jest skopiować pliki przy użyciu punktu połączenia usługi (Secure kopii).  W systemie Windows 10 można użyć [Bash w systemie Windows](https://msdn.microsoft.com/commandline/wsl/about) do uruchomienia punktu połączenia usługi.  W poprzednich wersjach systemu Windows, można użyć ciągu [PSCP (kopia Secure PuTTY)](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html).

Można skopiować pliki przy użyciu polecenia podobny do następującego:

`scp -r linux_username@remote_host:/usr/include .`

Oczywiście, Zastąp **linux_username** i **remote_host** wartości powyżej co to jest odpowiednie w środowisku.

Kiedy pliki są kopiowane, za pomocą **katalogi VC ++** elementu we właściwościach projektu programu Visual Studio stwierdzić, gdzie można znaleźć plików dołączanych dodatkowe, które właśnie zostały skopiowane.

![Katalogi VC ++](media/settings_directories.png)

## <a name="copy-sources"></a>Skopiuj źródeł
Podczas kompilowania, plików źródłowych na komputerze, zostały skopiowane na komputerze z systemem Linux i kompilowane istnieje.  Domyślnie wszystkie źródła w projekcie programu Visual Studio są kopiowane do lokalizacji w powyższym ustawienia.  Dodatkowe źródła można również dodać do listy lub kopiowanie źródła można wyłączyć całkowicie, jest to wartość domyślna dla projektu pliku reguł programu make.

* **Źródła, aby skopiować** Określa, jakie źródła są kopiowane z komputerem zdalnym.  Domyślnie **@(SourcesToCopyRemotely)** domyślnie wszystkich plików kodu źródłowego w projekcie, ale nie zawiera żadnych plików zasobów/zasobów, takich jak obrazy.

* **Skopiuj źródeł** może być włączona i Wyłącz pozwala włączać i wyłączać kopiowanie plików źródłowych z komputerem zdalnym.

* **Dodatkowe źródła, aby skopiować** umożliwia dodanie dodatkowych plików źródłowych, które zostaną skopiowane do systemu zdalnego.  Można określić listy rozdzielanej średnikami lub skorzystać z **: =** składni, aby określić nazwę lokalnych i zdalnych do użycia:

  `C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>Zdarzenia kompilacji
Ponieważ wszystkie kompilacji jest przeprowadzana na komputerze zdalnym, kilka dodatkowych zdarzeń kompilacji zostały dodane do sekcji Tworzenie zdarzenia we właściwościach projektu.  Są to **zdalnego zdarzenia Prekompilacyjnego**, **zdalnego zdarzenia Prekonsolidacyjnego**, i **zdalnego zdarzenia Postkompilacyjnego**i zostanie przeprowadzona na komputerze zdalnym przed lub po poszczególne kroki opisane w temacie proces.

![Zdarzenia kompilacji](media/settings_buildevents.png)

## <a name="see-also"></a>Zobacz też
[Praca z właściwościami projektu](../ide/working-with-project-properties.md)  
[Właściwości ogólne C++ (Linux C++)](../linux/prop-pages/general-linux.md)  
[Katalogi VC ++ (Linux C++)](../linux/prop-pages/directories-linux.md)  
[Kopiuj źródła właściwości projektu (Linux C++)](../linux/prop-pages/copy-sources-project.md)  
[Tworzenie właściwości zdarzenia (Linux C++)](../linux/prop-pages/build-events-linux.md)