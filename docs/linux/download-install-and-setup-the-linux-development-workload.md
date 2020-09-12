---
title: Instalowanie obciążenia C++ w systemie Linux w programie Visual Studio
description: Jak pobrać, zainstalować i skonfigurować obciążenie systemu Linux dla języka C++ w programie Visual Studio.
ms.date: 05/03/2020
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 3f8e6eb8285652078e5f26ca58601bc6ccfa80d1
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040980"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Pobieranie, Instalowanie i Konfigurowanie obciążenia systemu Linux

::: moniker range="vs-2015"

Projekty systemu Linux są obsługiwane w programie Visual Studio 2017 i nowszych. Aby zapoznać się z dokumentacją tych wersji, ustaw kontrolkę selektora **wersji** programu Visual Studio dla tego artykułu na visual Studio 2017 lub visual Studio 2019. Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end

::: moniker range=">=vs-2017"

Za pomocą środowiska IDE programu Visual Studio w systemie Windows można tworzyć, edytować i debugować projekty w języku C++, które są wykonywane w zdalnym systemie Linux, maszynie wirtualnej lub [podsystemie Windows dla systemu Linux](/windows/wsl/about).

Możesz korzystać z istniejącej bazy kodu, która używa CMake bez konieczności konwertowania jej na projekt programu Visual Studio. Jeśli baza kodu jest międzyplatformowa, można wskazać zarówno system Windows, jak i Linux z poziomu programu Visual Studio. Na przykład można edytować, kompilować i debugować kod w systemie Windows przy użyciu programu Visual Studio. Następnie szybko Przekieruj projekt dla systemu Linux do kompilowania i debugowania w środowisku systemu Linux. Pliki nagłówkowe systemu Linux są automatycznie kopiowane na komputer lokalny. Program Visual Studio używa ich do zapewnienia pełnej obsługi technologii IntelliSense (uzupełniania instrukcji, przejdź do definicji itd.).

W przypadku każdego z tych scenariuszy wymagane jest programowanie dla systemu **Linux przy użyciu języka C++** .

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Instalator programu Visual Studio

1. W polu wyszukiwania systemu Windows wpisz "Instalator programu Visual Studio":

   ![Pole wyszukiwania systemu Windows](media/visual-studio-installer-search.png)

1. Poszukaj Instalatora w obszarze wyniki **aplikacji** i kliknij go dwukrotnie. Po otwarciu Instalatora wybierz pozycję **Modyfikuj**, a następnie kliknij kartę **obciążenia** . Przewiń w dół do **innych zestawów narzędzi** i wybierz pozycję Programowanie dla systemu **Linux za pomocą języka C++** .

   ![Obciążenie Visual C++ for Linux Development](media/linuxworkload.png)

1. Jeśli chcesz wybrać platformy IoT lub Embedded, przejdź do okienka **szczegóły instalacji** po prawej stronie. W obszarze **Programowanie dla systemu Linux przy użyciu języka C++** rozwiń węzeł **składniki opcjonalne**i wybierz potrzebne składniki. Obsługa CMake dla systemu Linux jest domyślnie zaznaczona.

1. Kliknij przycisk **Modyfikuj** , aby kontynuować instalację.

## <a name="options-for-creating-a-linux-environment"></a>Opcje tworzenia środowiska systemu Linux

Jeśli nie masz jeszcze maszyny z systemem Linux, możesz utworzyć maszynę wirtualną z systemem Linux na platformie Azure. Aby uzyskać więcej informacji, zobacz [Szybki Start: Tworzenie maszyny wirtualnej z systemem Linux w Azure Portal](/azure/virtual-machines/linux/quick-create-portal).

W systemie Windows 10 można zainstalować i wskazać Ulubione dystrybucji z systemem Linux w podsystemie Windows dla systemu Linux (WSL). Aby uzyskać więcej informacji, zobacz [Przewodnik instalacji systemu Windows w systemie Linux dla systemu Windows 10](/windows/wsl/install-win10). Jeśli nie możesz uzyskać dostępu do sklepu Windows, możesz [ręcznie pobrać pakiety WSL dystrybucji](/windows/wsl/install-manual). WSL to wygodne środowisko konsoli, ale nie jest to zalecane w przypadku aplikacji graficznych.

::: moniker-end

::: moniker range="vs-2019"

Projekty systemu Linux w programie Visual Studio wymagają zainstalowania następujących zależności w zdalnym systemie Linux lub WSL:

- **Kompilator programu** Visual Studio 2019 ma pełną pomoc techniczną dla programu i [Clang](../build/clang-support-cmake.md).
- **GDB** — program Visual Studio automatycznie uruchamia GDB w systemie Linux i używa frontonu debugera programu Visual Studio, aby zapewnić środowisko debugowania pełnej wierności w systemie Linux.
- **rsync** i **zip** — włączenie funkcji rsync i zip umożliwia programowi Visual Studio wyodrębnienie plików nagłówkowych z systemu Linux do systemu plików Windows w celu użycia przez funkcję IntelliSense.
- **make**
- **OpenSSH — serwer** (tylko systemy zdalnego systemu Linux) — program Visual Studio nawiązuje połączenie ze zdalnymi systemami Linux za pośrednictwem bezpiecznego połączenia SSH.
- **CMAKE** (tylko projekty CMAKE) — można zainstalować [statycznie połączone pliki binarne](https://github.com/microsoft/CMake/releases)firmy Microsoft dla systemu Linux.
- **Ninja-Build** (tylko projekty CMAKE) — [Ninja](https://ninja-build.org/) to domyślny generator dla konfiguracji systemów Linux i WSL w programie Visual Studio 2019 w wersji 16,6 lub nowszej.

W poniższych poleceniach przyjęto założenie, że używasz funkcji g + + zamiast Clang.

::: moniker-end

::: moniker range="vs-2017"

Projekty systemu Linux w programie Visual Studio wymagają zainstalowania następujących zależności w zdalnym systemie Linux lub WSL:

- **z** działem IT — program Visual Studio 2017 zapewnia pełną obsługę programu w zatoce.
- **GDB** — program Visual Studio automatycznie uruchamia GDB w systemie Linux i używa frontonu debugera programu Visual Studio, aby zapewnić obsługę debugowania w trybie pełnoekranowym w systemie Linux.
- **rsync** i **zip** — dołączenie rsync i zip umożliwia programowi Visual Studio wyodrębnienie plików nagłówkowych z systemu Linux do systemu plików Windows, aby można było korzystać z funkcji IntelliSense.
- **make**
- **OpenSSH — serwer** — program Visual Studio nawiązuje połączenie ze zdalnym systemem Linux za pośrednictwem bezpiecznego połączenia SSH.
- **CMAKE** (tylko projekty CMAKE) — można zainstalować [statycznie połączone pliki binarne](https://github.com/microsoft/CMake/releases)firmy Microsoft dla systemu Linux.

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Konfiguracja systemu Linux: Ubuntu on WSL

Gdy jesteś celem WSL, nie ma potrzeby dodawania połączenia zdalnego ani konfigurowania protokołu SSH do kompilowania i debugowania. Elementy **zip** i **rsync** są wymagane do automatycznej synchronizacji nagłówków systemu Linux z programem Visual Studio na potrzeby obsługi technologii IntelliSense. **Ninja — kompilacja** jest wymagana tylko dla projektów CMAKE. Jeśli wymagane aplikacje nie są jeszcze obecne, można je zainstalować przy użyciu tego polecenia:

```bash
sudo apt-get install g++ gdb make ninja-build rsync zip
```

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>Ubuntu w zdalnych systemach Linux

Docelowy system Linux musi **mieć zainstalowany program** **OpenSSH-Server**, **g + +**, **GDB**i. **Ninja — kompilacja** jest wymagana tylko dla projektów CMAKE. Demon **SSH** musi być uruchomiony. elementy **zip** i **rsync** są wymagane do automatycznej synchronizacji nagłówków zdalnych z maszyną lokalną na potrzeby obsługi technologii IntelliSense. Jeśli te aplikacje nie są jeszcze obecne, można je zainstalować w następujący sposób:

1. W wierszu polecenia powłoki na komputerze z systemem Linux Uruchom polecenie:

   ```bash
   sudo apt-get install openssh-server g++ gdb make ninja-build rsync zip
   ```

   Może zostać wyświetlony monit o hasło główne, aby uruchomić polecenie sudo. Jeśli tak, wprowadź ją i Kontynuuj. Po zakończeniu wymagane usługi i narzędzia zostaną zainstalowane.

1. Upewnij się, że usługa SSH jest uruchomiona na komputerze z systemem Linux, uruchamiając następujące instrukcje:

   ```bash
   sudo service ssh start
   ```

   To polecenie uruchamia usługę i uruchamia ją w tle, gotowy do akceptowania połączeń.

::: moniker-end

::: moniker range="vs-2019"

## <a name="fedora-on-wsl"></a>Fedora na WSL

Fedora korzysta z Instalatora pakietu **DNF** . Aby pobrać plik **g + +**, **GDB**, **Marka**, **rsync**, **Ninja-Build**i **zip**, uruchom polecenie:

   ```bash
   sudo dnf install gcc-g++ gdb rsync ninja-build make zip
   ```

Elementy **zip** i **rsync** są wymagane do automatycznej synchronizacji nagłówków systemu Linux z programem Visual Studio na potrzeby obsługi technologii IntelliSense. **Ninja — kompilacja** jest wymagana tylko dla projektów CMAKE.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>Fedora w zdalnych systemach Linux

Maszyna docelowa z systemem Fedora korzysta z Instalatora pakietu **DNF** . Aby pobrać **OpenSSH-Server**, **g + +**, **GDB**, **Make**, **Ninja-Build**, **rsync**i **zip**, a następnie ponownie uruchomić demona SSH, wykonaj te instrukcje. **Ninja — kompilacja** jest wymagana tylko dla projektów CMAKE.

1. W wierszu polecenia powłoki na komputerze z systemem Linux Uruchom polecenie:

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb ninja-build make rsync zip
   ```

   Może zostać wyświetlony monit o hasło główne, aby uruchomić polecenie sudo. Jeśli tak, wprowadź ją i Kontynuuj. Po zakończeniu wymagane usługi i narzędzia zostaną zainstalowane.

1. Upewnij się, że usługa SSH jest uruchomiona na komputerze z systemem Linux, uruchamiając następujące instrukcje:

   ```bash
   sudo systemctl start sshd
   ```

   To polecenie uruchamia usługę i uruchamia ją w tle, gotowy do akceptowania połączeń.

## <a name="next-steps"></a>Następne kroki

Teraz możesz utworzyć lub otworzyć projekt systemu Linux i skonfigurować go do uruchamiania w systemie docelowym. Aby uzyskać więcej informacji, zobacz:

- [Tworzenie nowego projektu systemu Linux](create-a-new-linux-project.md)
- [Konfigurowanie projektu CMake systemu Linux](cmake-linux-project.md)

::: moniker-end
