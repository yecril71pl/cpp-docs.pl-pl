---
title: Instalowanie obciążenia C++ systemu Linux w programie Visual Studio
description: Opisuje sposób pobierania, instalowania i konfigurowania obciążenia systemu Linux dla C++ programu Visual Studio.
ms.date: 06/11/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 68e347a4f90fc15f9d3846c82c3392213e1bd7bc
ms.sourcegitcommit: eb254b4462a58d219376ff501bf768bd1adc07ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2019
ms.locfileid: "73912906"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Pobieranie, Instalowanie i Konfigurowanie obciążenia systemu Linux

::: moniker range="vs-2015"

Projekty systemu Linux są obsługiwane w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

Możesz użyć środowiska IDE programu Visual Studio w systemie Windows, aby tworzyć, edytować C++ i debugować projekty wykonywane w zdalnym systemie Linux, maszynie wirtualnej lub [podsystemie Windows dla systemu Linux](/windows/wsl/about). 

Możesz korzystać z istniejącej bazy kodu, która używa CMake bez konieczności konwertowania jej na projekt programu Visual Studio. Jeśli baza kodu jest międzyplatformowa, można wskazać zarówno system Windows, jak i Linux z poziomu programu Visual Studio. Na przykład można edytować, kompilować i debugować kod w systemie Windows przy użyciu programu Visual Studio, a następnie szybko przekierować projekt dla systemu Linux w celu kompilowania i debugowania w środowisku z systemem Linux. Pliki nagłówkowe systemu Linux są automatycznie kopiowane na komputer lokalny, gdzie program Visual Studio używa ich do zapewnienia pełnej obsługi technologii IntelliSense (uzupełnianie instrukcji, przejdź do definicji itd.). 
 
W przypadku każdego z tych scenariuszy wymagane jest **Programowanie przy C++ użyciu systemu Linux z** obciążeniem. 

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Instalator programu Visual Studio

1. W polu wyszukiwania systemu Windows wpisz "Instalator programu Visual Studio":

   ![Pole wyszukiwania systemu Windows](media/visual-studio-installer-search.png)

2. Poszukaj Instalatora w obszarze wyniki **aplikacji** i kliknij go dwukrotnie. Po otwarciu Instalatora wybierz pozycję **Modyfikuj**, a następnie kliknij kartę **obciążenia** . Przewiń w dół do **innych zestawów narzędzi** i wybierz pozycję Programowanie dla systemu **Linux za pomocą C++**  obciążenia.

   ![Tworzenie C++ aplikacji Visual for Linux](media/linuxworkload.png)

1. Jeśli celem są platformy IoT lub Embedded, przejdź do okienka **szczegóły instalacji** po prawej stronie. W obszarze **Programowanie na C++platformie Linux za pomocą** programu rozwiń węzeł **składniki opcjonalne**i wybierz potrzebne składniki. Obsługa CMake dla systemu Linux jest domyślnie zaznaczona.

1. Kliknij przycisk **Modyfikuj** , aby kontynuować instalację.

## <a name="options-for-creating-a-linux-environment"></a>Opcje tworzenia środowiska systemu Linux

Jeśli nie masz jeszcze maszyny z systemem Linux, możesz utworzyć maszynę wirtualną z systemem Linux na platformie Azure. Aby uzyskać więcej informacji, zobacz [Szybki Start: Tworzenie maszyny wirtualnej z systemem Linux w Azure Portal](/azure/virtual-machines/linux/quick-create-portal).

W systemie Windows 10 można zainstalować i wskazać Ulubione dystrybucji z systemem Linux w podsystemie Windows dla systemu Linux (WSL). Aby uzyskać więcej informacji, zobacz [Przewodnik instalacji systemu Windows w systemie Linux dla systemu Windows 10](/windows/wsl/install-win10). Jeśli nie możesz uzyskać dostępu do sklepu Windows, możesz [ręcznie pobrać pakiety WSL dystrybucji](/windows/wsl/install-manual). WSL to wygodne środowisko konsoli, ale nie jest zalecane w przypadku aplikacji graficznych. 

::: moniker-end

::: moniker range="vs-2019"

Projekty systemu Linux w programie Visual Studio wymagają zainstalowania następujących zależności w zdalnym systemie Linux lub WSL: 
- **Kompilator programu** Visual Studio 2019 ma wbudowaną obsługę programu do obsługi i [Clang](https://docs.microsoft.com/en-us/cpp/build/clang-support-cmake?view=vs-2019). 
- **GDB** — program Visual Studio automatycznie uruchamia GDB w systemie Linux i używa frontonu debugera programu Visual Studio, aby zapewnić środowisko debugowania pełnej wierności w systemie Linux. 
- **rsync** i **zip** — włączenie funkcji rsync i zip umożliwia programowi Visual Studio wyodrębnienie plików nagłówkowych z systemu Linux do systemu plików Windows w celu użycia przez funkcję IntelliSense.
- **SprawdY**
- **OpenSSH — serwer** (tylko systemy zdalnego systemu Linux) — program Visual Studio nawiązuje połączenie ze zdalnymi systemami Linux za pośrednictwem bezpiecznego połączenia SSH.
- **CMAKE** (tylko projekty CMAKE) — można zainstalować [statycznie połączone pliki binarne](https://github.com/microsoft/CMake/releases)firmy Microsoft dla systemu Linux.

W poniższych poleceniach przyjęto założenie, że używany jest program g + + zamiast Clang. 

::: moniker-end

::: moniker range="vs-2017"

Projekty systemu Linux w programie Visual Studio wymagają zainstalowania następujących zależności w zdalnym systemie Linux lub WSL: 
- w ramach **programu z działem IT — program** Visual Studio 2017 oferuje wbudowaną pomoc techniczną dla programu z działem IT.
- **GDB** — program Visual Studio automatycznie uruchamia GDB w systemie Linux i używa frontonu debugera programu Visual Studio, aby zapewnić środowisko debugowania pełnej wierności w systemie Linux. 
- **rsync** i **zip** — dołączenie rsync i zip umożliwia programowi Visual Studio wyodrębnienie plików nagłówkowych z systemu Linux do systemu plików Windows, aby można było korzystać z funkcji IntelliSense.
- **SprawdY**
- **OpenSSH — serwer** — program Visual Studio nawiązuje połączenie ze zdalnym systemem Linux za pośrednictwem bezpiecznego połączenia SSH.
- **CMAKE** (tylko projekty CMAKE) — można zainstalować [statycznie połączone pliki binarne](https://github.com/microsoft/CMake/releases)firmy Microsoft dla systemu Linux.

::: moniker-end

::: moniker range="vs-2019" 

## <a name="linux-setup-ubuntu-on-wsl"></a>Konfiguracja systemu Linux: Ubuntu on WSL

W przypadku określania wartości docelowej WSL nie ma potrzeby dodawania połączenia zdalnego ani konfigurowania protokołu SSH w celu kompilowania i debugowania. Elementy **zip** i **rsync** są wymagane do automatycznej synchronizacji nagłówków systemu Linux z programem Visual Studio na potrzeby obsługi technologii IntelliSense. Jeśli wymagane aplikacje nie są jeszcze zainstalowane, można je zainstalować w następujący sposób:

```bash
sudo apt-get install g++ gdb make rsync zip
```

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>Ubuntu w zdalnych systemach Linux

W docelowym systemie Linux musi być zainstalowany program **OpenSSH-Server**, **g + +** , **GDB**i **Make** , a demon SSH musi być uruchomiony. elementy **zip** i **rsync** są wymagane do automatycznej synchronizacji nagłówków zdalnych z maszyną lokalną na potrzeby obsługi technologii IntelliSense. Jeśli te aplikacje nie są jeszcze zainstalowane, można je zainstalować w następujący sposób:

1. W wierszu polecenia powłoki na komputerze z systemem Linux Uruchom polecenie:

   ```bash
   sudo apt-get install openssh-server g++ gdb make rsync zip
   ```

   Może zostać wyświetlony monit o podanie hasła głównego ze względu na polecenie sudo.  Jeśli tak, wprowadź ją i Kontynuuj. Po zakończeniu wymagane usługi i narzędzia zostaną zainstalowane.

1. Upewnij się, że usługa SSH jest uruchomiona na komputerze z systemem Linux, uruchamiając następujące instrukcje:

   ```bash
   sudo service ssh start
   ```

   Spowoduje to uruchomienie usługi i uruchomienie jej w tle, gotowy do akceptowania połączeń.

::: moniker-end

::: moniker range="vs-2019"

## <a name="fedora-on-wsl"></a>Fedora na WSL

Fedora korzysta z Instalatora pakietu **DNF** . Aby pobrać plik **g + +** , **GDB**, **Marka**, **rsync** i **zip**, uruchom polecenie:

   ```bash
   sudo dnf install gcc-g++ gdb rsync make zip
   ```

Elementy **zip** i **rsync** są wymagane do automatycznej synchronizacji nagłówków systemu Linux z programem Visual Studio na potrzeby obsługi technologii IntelliSense.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>Fedora w zdalnych systemach Linux

Maszyna docelowa z systemem Fedora korzysta z Instalatora pakietu **DNF** . Aby pobrać **OpenSSH-Server**, **g + +** , **GDB**, **Make**, **rsync**i **zip**, a następnie ponownie uruchomić demona SSH, wykonaj następujące instrukcje:

1. W wierszu polecenia powłoki na komputerze z systemem Linux Uruchom polecenie:

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb make rsync zip
   ```

   Może zostać wyświetlony monit o podanie hasła głównego ze względu na polecenie sudo.  Jeśli tak, wprowadź ją i Kontynuuj. Po zakończeniu wymagane usługi i narzędzia zostaną zainstalowane.

1. Upewnij się, że usługa SSH jest uruchomiona na komputerze z systemem Linux, uruchamiając następujące instrukcje:

   ```bash
   sudo systemctl start sshd
   ```

   Spowoduje to uruchomienie usługi i uruchomienie jej w tle, gotowy do akceptowania połączeń.

::: moniker-end

::: moniker range="vs-2015"

Obsługa opracowywania C++ systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

## <a name="next-steps"></a>Następne kroki

Teraz można przystąpić do utworzenia lub otwarcia projektu systemu Linux i skonfigurowania go do uruchamiania w systemie docelowym. Aby uzyskać więcej informacji, zobacz:

- [Tworzenie nowego projektu systemu Linux](create-a-new-linux-project.md)
- [Konfigurowanie projektu CMake systemu Linux](cmake-linux-project.md)
