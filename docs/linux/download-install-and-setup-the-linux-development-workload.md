---
title: Instalowanie obciążenia C++ systemu Linux w programie Visual Studio
description: Opisuje sposób pobierania, instalowania i konfigurowania obciążenia systemu Linux dla C++ programu Visual Studio.
ms.date: 06/11/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 5df7b323d202f398059e92abaeeeedbf73439fa4
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299794"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Pobieranie, Instalowanie i Konfigurowanie obciążenia systemu Linux

::: moniker range="vs-2015"

Projekty systemu Linux są obsługiwane w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

Możesz użyć środowiska IDE programu Visual Studio w systemie Windows, aby tworzyć, edytować C++ i debugować projekty wykonywane na komputerze fizycznym z systemem Linux, maszynie wirtualnej lub podsystemie [Windows dla systemu Linux](/windows/wsl/about). 

Można korzystać z istniejącej bazy kodu, która używa CMake lub innego systemu kompilacji bez konieczności konwertowania go do projektu programu Visual Studio. Jeśli baza kodu jest międzyplatformowa, można wskazać zarówno system Windows, jak i Linux z poziomu programu Visual Studio. Na przykład można edytować, debugować i profilować kod w systemie Windows przy użyciu programu Visual Studio, a następnie szybko przekierować projekt dla systemu Linux w celu przeprowadzenia dalszych testów. Pliki nagłówkowe systemu Linux są automatycznie kopiowane na komputer lokalny, na którym program Visual Studio używa ich do zapewnienia pełnej obsługi technologii IntelliSense (uzupełnianie instrukcji, przejdź do definicji itd.). 
 
W przypadku każdego z tych scenariuszy wymagane jest **Programowanie przy C++ użyciu systemu Linux z** obciążeniem. 

::: moniker-end

::: moniker range="vs-2019"

W programie Visual Studio 2019 można określić oddzielne elementy docelowe do kompilowania i debugowania. W przypadku określania wartości docelowej WSL nie jest już konieczne Dodawanie połączenia zdalnego ani Konfigurowanie protokołu SSH.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Instalator programu Visual Studio

1. W polu wyszukiwania systemu Windows wpisz "Instalator programu Visual Studio":

   ![Pole wyszukiwania systemu Windows](media/visual-studio-installer-search.png)

2. Poszukaj Instalatora w obszarze wyniki **aplikacji** i kliknij go dwukrotnie. Po otwarciu Instalatora wybierz pozycję **Modyfikuj**, a następnie kliknij kartę **obciążenia** . Przewiń w dół do **innych zestawów narzędzi** i wybierz pozycję Programowanie dla systemu **Linux przy C++ użyciu** obciążenia.

   ![Tworzenie C++ aplikacji Visual for Linux](media/linuxworkload.png)

1. Jeśli chcesz uzyskać dostęp do platform IoT lub Embedded, przejdź do okienka **szczegóły instalacji** po prawej stronie, w obszarze **programowanie systemu C++Linux za pomocą** , rozwiń węzeł **składniki opcjonalne** i wybierz potrzebne składniki. Obsługa CMake dla systemu Linux jest domyślnie zaznaczona.

1. Kliknij przycisk **Modyfikuj** , aby kontynuować instalację.

## <a name="options-for-creating-a-linux-environment"></a>Opcje tworzenia środowiska systemu Linux

Jeśli nie masz jeszcze maszyny z systemem Linux, możesz utworzyć maszynę wirtualną z systemem Linux na platformie Azure. Aby uzyskać więcej informacji, [zobacz Szybki Start: Utwórz maszynę wirtualną z systemem Linux w](/azure/virtual-machines/linux/quick-create-portal)Azure Portal.

W systemie Windows 10 można zainstalować i wskazać Ulubione dystrybucji z systemem Linux w podsystemie Windows dla systemu Linux (WSL). Aby uzyskać więcej informacji, zobacz [Przewodnik instalacji systemu Windows w systemie Linux dla systemu Windows 10](/windows/wsl/install-win10). WSL to wygodne środowisko konsoli, ale nie jest zalecane w przypadku aplikacji graficznych. 

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Konfiguracja systemu Linux: Ubuntu na WSL

W przypadku określania wartości docelowej WSL nie ma potrzeby dodawania połączenia zdalnego ani konfigurowania protokołu SSH w celu kompilowania i debugowania. Elementy **zip** i **rsync** są wymagane do automatycznej synchronizacji nagłówków systemu Linux z programem Visual Studio na potrzeby obsługi technologii IntelliSense. Jeśli wymagane aplikacje nie są jeszcze zainstalowane, można je zainstalować w następujący sposób:

```bash
sudo apt-get install g++ gdb make rsync zip
```
::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>Ubuntu w zdalnych systemach Linux

Docelowy system Linux musi mieć zainstalowaną **OpenSSH-Server**, **g + +** , **GDB**i **serwera gdbserver** , a demon SSH musi być uruchomiony. plik **zip** jest wymagany do automatycznej synchronizacji nagłówków zdalnych z maszyną lokalną na potrzeby obsługi technologii IntelliSense. Jeśli te aplikacje nie są jeszcze zainstalowane, można je zainstalować w następujący sposób:

1. W wierszu polecenia powłoki na komputerze z systemem Linux Uruchom polecenie:

   ```bash
   sudo apt-get install openssh-server g++ gdb gdbserver zip
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

Fedora korzysta z Instalatora pakietu **DNF** . Aby pobrać plik **g + +** , **GDB**, **rsync** i **zip**, uruchom polecenie:

   ```bash
   sudo dnf install gcc-g++ gdb rsync zip
   ```

Elementy **zip** i **rsync** są wymagane do automatycznej synchronizacji nagłówków systemu Linux z programem Visual Studio na potrzeby obsługi technologii IntelliSense.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>Fedora w zdalnych systemach Linux

Maszyna docelowa z systemem Fedora korzysta z Instalatora pakietu **DNF** . Aby pobrać **OpenSSH-Server**, **g + +** , **GDB**, **serwera gdbserver** i **zip**, a następnie ponownie uruchomić demona SSH, wykonaj następujące instrukcje:

1. W wierszu polecenia powłoki na komputerze z systemem Linux Uruchom polecenie:

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb gdb-gdbserver zip
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
