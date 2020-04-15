---
title: Instalowanie obciążenia systemu Linux w programie Visual Studio w programie Visual Studio
description: W tym artykule opisano sposób pobierania, instalowania i konfigurowania obciążenia systemu Linux dla języka C++ w programie Visual Studio.
ms.date: 06/11/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 8e10521ab35f3d85ced8bffd771b4e101d4d4fe6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364341"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Pobieranie, instalowanie i konfigurowanie obciążenia systemu Linux

::: moniker range="vs-2015"

Projekty systemu Linux są obsługiwane w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

Ide programu Visual Studio w systemie Windows służy do tworzenia, edytowania i debugowania projektów C++, które są wykonywane na zdalnym systemie Linux, maszynie wirtualnej lub [podsystemie Windows dla systemu Linux.](/windows/wsl/about)

Można pracować na istniejącej bazy kodu, który używa CMake bez konieczności konwertowania go do projektu programu Visual Studio. Jeśli baza kodu jest wieloplatformowa, można kierować zarówno windows i linux z poziomu programu Visual Studio. Na przykład można edytować, tworzyć i debugować kod w systemie Windows za pomocą programu Visual Studio, a następnie szybko przekierować projekt dla systemu Linux do tworzenia i debugowania w środowisku systemu Linux. Pliki nagłówkowe systemu Linux są automatycznie kopiowane na komputerze lokalnym, gdzie visual studio używa ich do zapewnienia pełnej obsługi IntelliSense (zakończenie instrukcji, Przejdź do definicji i tak dalej).

W każdym z tych scenariuszy wymagane jest tworzenie systemu Linux z obciążeniem **języka C++.**

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Konfiguracja programu Visual Studio

1. Wpisz "Instalator programu Visual Studio" w polu wyszukiwania systemu Windows:

   ![Pole wyszukiwania systemu Windows](media/visual-studio-installer-search.png)

1. Poszukaj instalatora w obszarze Wyniki **aplikacji** i kliknij go dwukrotnie. Po otwarciu instalatora wybierz pozycję **Modyfikuj**, a następnie kliknij kartę **Obciążenia.** Przewiń w dół do **innych zestawów narzędzi** i wybierz programowanie systemu Linux z obciążeniem **języka C++.**

   ![Obciążenie programu Visual C++ dla programu Linux Development](media/linuxworkload.png)

1. Jeśli kierujesz reklamy na IoT lub platformy osadzone, przejdź do okienka **Szczegóły instalacji** po prawej stronie. W obszarze **Rozwoju Linuksa z C++** rozwiń **opcjonalne komponenty**i wybierz składniki, których potrzebujesz. CMake wsparcie dla Linuksa jest zaznaczone domyślnie.

1. Kliknij **przycisk Modyfikuj,** aby kontynuować instalację.

## <a name="options-for-creating-a-linux-environment"></a>Opcje tworzenia środowiska systemu Linux

Jeśli nie masz jeszcze komputera z systemem Linux, możesz utworzyć maszynę wirtualną systemu Linux na platformie Azure. Aby uzyskać więcej informacji, zobacz [Szybki start: Tworzenie maszyny wirtualnej systemu Linux w witrynie Azure portal](/azure/virtual-machines/linux/quick-create-portal).

W systemie Windows 10 możesz zainstalować i kierować swoją ulubioną dystrybucję Linuksa na podsystem windowsowy dla systemu Linux (WSL). Aby uzyskać więcej informacji, zobacz [Podręcznik instalacji systemu Windows dla systemu Linux dla systemu Windows 10](/windows/wsl/install-win10). Jeśli nie możesz uzyskać dostępu do Sklepu Windows, możesz [ręcznie pobrać pakiety dystrybucji WSL](/windows/wsl/install-manual). WSL jest wygodnym środowiskiem konsoli, ale nie jest zalecane dla aplikacji graficznych.

::: moniker-end

::: moniker range="vs-2019"

Projekty systemu Linux w programie Visual Studio wymagają zainstalowania następujących zależności w zdalnym systemie Linux lub WSL:

- **Kompilator** — Visual Studio 2019 ma nieszablonową obsługę GCC i [Clang](/cpp/build/clang-support-cmake?view=vs-2019).
- **gdb** — Visual Studio automatycznie uruchamia gdb w systemie Linux i używa front-end debugera Visual Studio, aby zapewnić pełną wierność debugowania środowiska w systemie Linux.
- **rsync** i **zip** - włączenie rsync i zip pozwala Visual Studio wyodrębnić pliki nagłówkowe z systemu Linux do systemu plików Windows do użytku przez IntelliSense.
- **make**
- **openssh-server** (tylko zdalne systemy Linux) — Visual Studio łączy się ze zdalnymi systemami Linux za pomocą bezpiecznego połączenia SSH.
- **CMake** (CMake projektów tylko) - Można zainstalować [statycznie połączone binarki Microsoft CMake dla Linuksa](https://github.com/microsoft/CMake/releases).
- **ninja-build** (tylko projekty CMake)- [Ninja](https://ninja-build.org/) jest domyślnym generatorem konfiguracji Linuksa i WSL w programie Visual Studio 2019 w wersji 16.6 lub nowszej.

Następujące polecenia zakładają, że używasz g++ zamiast clang.

::: moniker-end

::: moniker range="vs-2017"

Projekty systemu Linux w programie Visual Studio wymagają zainstalowania następujących zależności w zdalnym systemie Linux lub WSL:

- **gcc** — Visual Studio 2017 ma gotowe wsparcie dla GCC.
- **gdb** — Visual Studio automatycznie uruchamia gdb w systemie Linux i używa front-end debugera Visual Studio, aby zapewnić pełną wierność debugowania środowiska w systemie Linux.
- **rsync** i **zip** - włączenie rsync i zip pozwala Visual Studio wyodrębnić pliki nagłówkowe z systemu Linux do systemu plików Windows do wykorzystania dla IntelliSense.
- **make**
- **openssh-server** — visual studio łączy się ze zdalnymi systemami Linux za pomocą bezpiecznego połączenia SSH.
- **CMake** (CMake projektów tylko) - Można zainstalować [statycznie połączone binarki Microsoft CMake dla Linuksa](https://github.com/microsoft/CMake/releases).

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Konfiguracja Linuksa: Ubuntu na WSL

Podczas kierowania WSL, nie ma potrzeby, aby dodać połączenie zdalne lub skonfigurować SSH w celu tworzenia i debugowania. **zip** i **rsync** są wymagane do automatycznej synchronizacji nagłówków linuksa z programem Visual Studio dla obsługi intellisense. Jeśli wymagane aplikacje nie są jeszcze obecne, można je zainstalować w następujący sposób. **ninja-build** jest wymagany tylko dla projektów CMake.

```bash
sudo apt-get install g++ gdb make ninja-build rsync zip
```

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>Ubuntu na zdalnych systemach Linux

Docelowy system Linux musi mieć **openssh-server**, **g++**, **gdb**, **ninja-build** (tylko projekty CMake), i **zrobić** zainstalowany, a demon ssh musi być uruchomiony. **zip** i **rsync** są wymagane do automatycznej synchronizacji zdalnych nagłówków z lokalnym komputerem w celu uzyskania obsługi intellisense. Jeśli te aplikacje nie są jeszcze obecne, można je zainstalować w następujący sposób:

1. W wierszu polecenia powłoki na komputerze z systemem Linux uruchom:

   ```bash
   sudo apt-get install openssh-server g++ gdb make ninja-build rsync zip
   ```

   Może zostać wyświetlony monit o podanie hasła głównego z powodu polecenia sudo.  Jeśli tak, wprowadź go i kontynuuj. Po zakończeniu, wymagane usługi i narzędzia są instalowane.

1. Upewnij się, że usługa ssh jest uruchomiona na komputerze z systemem Linux, uruchamiając:

   ```bash
   sudo service ssh start
   ```

   Spowoduje to uruchomienie usługi i uruchomienie jej w tle, gotowe do zaakceptowania połączeń.

::: moniker-end

::: moniker range="vs-2019"

## <a name="fedora-on-wsl"></a>Fedora na WSL

Fedora używa instalatora pakietu **dnf.** Aby pobrać **g ++**, **gdb**, **make**, **rsync**, **ninja-build**i **zip**, uruchom:

   ```bash
   sudo dnf install gcc-g++ gdb rsync ninja-build make zip
   ```

**zip** i **rsync** są wymagane do automatycznej synchronizacji nagłówków linuksa z programem Visual Studio dla obsługi intellisense. **ninja-build** jest wymagany tylko dla projektów CMake.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>Fedora na zdalnych systemach Linux

Komputer docelowy z uruchomioną Fedorą używa instalatora pakietu **dnf.** Aby pobrać **openssh-server**, **g ++**, **gdb**, **make**, **ninja-build**, **rsync**, i **zip**, i ponownie uruchomić demona ssh, postępuj zgodnie z tymi instrukcjami. **ninja-build** jest wymagany tylko dla projektów CMake.

1. W wierszu polecenia powłoki na komputerze z systemem Linux uruchom:

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb ninja-build make rsync zip
   ```

   Może zostać wyświetlony monit o podanie hasła głównego z powodu polecenia sudo.  Jeśli tak, wprowadź go i kontynuuj. Po zakończeniu, wymagane usługi i narzędzia są instalowane.

1. Upewnij się, że usługa ssh jest uruchomiona na komputerze z systemem Linux, uruchamiając:

   ```bash
   sudo systemctl start sshd
   ```

   Spowoduje to uruchomienie usługi i uruchomienie jej w tle, gotowe do zaakceptowania połączeń.

::: moniker-end

::: moniker range="vs-2015"

Obsługa programowania języka C++ dla systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

## <a name="next-steps"></a>Następne kroki

Teraz możesz utworzyć lub otworzyć projekt systemu Linux i skonfigurować go do uruchamiania w systemie docelowym. Aby uzyskać więcej informacji, zobacz:

- [Tworzenie nowego projektu systemu Linux](create-a-new-linux-project.md)
- [Konfigurowanie projektu CMake systemu Linux](cmake-linux-project.md)
