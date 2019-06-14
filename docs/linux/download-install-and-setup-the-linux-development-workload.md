---
title: Zainstaluj obciążenie systemu Linux w języku C++ w programie Visual Studio
description: W tym artykule opisano, jak pobrać, zainstalować i skonfigurować obciążenia systemu Linux dla języka C++ w programie Visual Studio.
ms.date: 06/11/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: d5c099794f781fa9e6217f3796d24d1a63fd7b53
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042745"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Pobieranie, instalowanie i konfigurowanie obciążeń systemu Linux

::: moniker range="vs-2015"

Projektów systemu Linux są obsługiwane w programie Visual Studio 2017 i nowszych wersjach.

::: moniker-end

::: moniker range=">=vs-2017"

Visual Studio IDE w Windows służy do tworzenia, edytowania i debugowania projektów w języku C++, które są wykonywane na komputerze fizycznym Linux maszyny wirtualnej lub [podsystem Windows dla systemu Linux](/windows/wsl/about). 

Można pracować na istniejącej bazie kodu używającej narzędzia CMake lub innego systemu kompilacji bez konieczności konwertowania go do projektu programu Visual Studio. Jeśli baza kodu jest dla wielu platform, mogą kierować zarówno Windows, jak i Linux z poziomu programu Visual Studio. Na przykład, można edytować, debugowania i profilowania kodu na Windows przy użyciu programu Visual Studio. następnie szybko rzekieruj projekt dla systemu Linux w celu dalszego badania. Pliki nagłówkowe systemu Linux są automatycznie kopiowane do komputera lokalnego, gdzie program Visual Studio są one używane do zapewnienia pełną obsługą technologii IntelliSense (uzupełnianie, przejdź do definicji i tak dalej) pomocy technicznej. 
 
Dla każdego z tych scenariuszy **programowanie dla systemu Linux przy użyciu języka C++** obciążenie jest wymagane. 

::: moniker-end

::: moniker range="vs-2019"

W Visual Studio 2019 r można określić oddzielne obiekty docelowe do kompilowania i debugowania. Podczas określania wartości WSL, należy już do dodawania połączenia zdalnego, lub skonfiguruj protokół SSH.

Obsługa [AddressSanitizer (ASan)](https://github.com/google/sanitizers/wiki/AddressSanitizer) jest zintegrowana w programie Visual Studio dla projektów systemu Linux.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Instalator programu Visual Studio

1. Wpisz "Instalator programu Visual Studio" w polu wyszukiwania Windows:

   ![Pole wyszukiwania Windows](media/visual-studio-installer-search.png)

2. Wyszukaj Instalatora w obszarze **aplikacje** wyniki, a następnie kliknij go dwukrotnie. Po otwarciu Instalatora wybierz **Modyfikuj**, a następnie kliknij polecenie **obciążeń** kartę. Przewiń w dół do **inne zestawy narzędzi** i wybierz **programowanie dla systemu Linux przy użyciu języka C++** obciążenia.

   ![Visual C++ dla obciążenia programowanie dla systemu Linux](media/linuxworkload.png)

1. Jeśli docelowej platformy osadzonych i IoT, przejdź do strony **szczegółowe informacje dotyczące instalacji** w okienku po prawej stronie, w obszarze **Linux development przy użyciu C++** , rozwiń węzeł **składniki opcjonalne**i wybierz potrzebne składniki. Obsługa CMake dla systemu Linux jest domyślnie zaznaczone.

1. Kliknij przycisk **Modyfikuj** do kontynuowania instalacji.

## <a name="options-for-creating-a-linux-environment"></a>Opcje tworzenia środowiska systemu Linux

Jeśli nie masz jeszcze maszyny z systemem Linux, możesz utworzyć maszynę wirtualną z systemem Linux na platformie Azure. Aby uzyskać więcej informacji, zobacz [Szybki Start: Utwórz maszynę wirtualną systemu Linux w witrynie Azure portal](/azure/virtual-machines/linux/quick-create-portal).

W systemie Windows 10 można zainstalować i docelowa swoje ulubione dystrybucja systemu Linux w podsystemie Windows dla systemu Linux (WSL). Aby uzyskać więcej informacji, zobacz [podsystemu Windows dla systemu Linux instalacji Guide for Windows 10](/windows/wsl/install-win10). WSL to środowisko konsoli wygodne, ale nie jest zalecane w przypadku aplikacji graficznych. 

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Konfiguracja w systemie Linux: Ubuntu na WSL

Gdy są one ukierunkowane WSL, nie ma potrzeby dodać połączenie zdalne lub skonfiguruj protokół SSH, aby można było kompilowanie i debugowanie. **ZIP** i **rsync** są wymagane do automatycznej synchronizacji nagłówków systemu Linux przy użyciu programu Visual Studio do obsługi technologii Intellisense. Jeśli wymagane aplikacje nie są już obecne, możesz zainstalować je w następujący sposób:

```bash
sudo apt-get install g++ gdb make rsync zip
```
::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>Ubuntu w systemach zdalnych systemu Linux

Docelowy Linux system muszą mieć **openssh-server**, **g ++** , **gdb**, i **serwera gdbserver** zainstalowane i ssh demona musi być uruchomiona. **ZIP** jest wymagany do automatycznej synchronizacji zdalnych nagłówków z komputerze lokalnym, aby uzyskać obsługę technologii Intellisense. Jeśli te aplikacje nie są już obecne, możesz zainstalować je w następujący sposób:

1. W wierszu polecenia powłoki na komputerze z systemem Linux Uruchom polecenie:

   ```bash
   sudo apt-get install openssh-server g++ gdb gdbserver zip
   ```

   Może zostać wyświetlony o podanie hasła głównego ze względu na polecenia "sudo".  Jeśli tak, wprowadź go i kontynuować. Po wykonaniu tych czynności, wymagane usługi i narzędzia są zainstalowane.

1. Upewnij się, ssh jest uruchomiona na komputerze z systemem Linux, uruchamiając:

   ```bash
   sudo service ssh start
   ```
   Spowoduje to uruchomienie usługi i działa w tle, gotowy do akceptowania połączeń.

::: moniker-end

::: moniker range="vs-2019"

## <a name="fedora-on-wsl"></a>Fedora on WSL

Używa fedora **dnf** pakiet Instalatora. Aby pobrać **g ++** , **gdb**, **rsync** i **zip**Uruchom:

   ```bash
   sudo dnf install gcc-g++ gdb rsync zip
   ```

**ZIP** i **rsync** są wymagane do automatycznej synchronizacji nagłówków systemu Linux przy użyciu programu Visual Studio do obsługi technologii Intellisense.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>Fedora w systemach zdalnych systemu Linux

Używa docelowej maszynie Fedora **dnf** pakiet Instalatora. Aby pobrać **openssh-server**, **g ++** , **gdb**, **serwera gdbserver** i **zip**i uruchom ponownie ssh demon, wykonaj te instrukcje:

1. W wierszu polecenia powłoki na komputerze z systemem Linux Uruchom polecenie:

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb gdb-gdbserver zip
   ```
   Może zostać wyświetlony o podanie hasła głównego ze względu na polecenia "sudo".  Jeśli tak, wprowadź go i kontynuować. Po wykonaniu tych czynności, wymagane usługi i narzędzia są zainstalowane.

1. Upewnij się, ssh jest uruchomiona na komputerze z systemem Linux, uruchamiając:

   ```bash
   sudo systemctl start sshd
   ```

   Spowoduje to uruchomienie usługi i działa w tle, gotowy do akceptowania połączeń.

::: moniker-end

::: moniker range="vs-2015"

Obsługa systemu Linux C++ tworzenia jest dostępne w programie Visual Studio 2017 i nowszych wersjach.

::: moniker-end

## <a name="next-steps"></a>Następne kroki

Teraz można przystąpić do tworzenia lub otwierania projektu systemu Linux i skonfigurowanie pod kątem uruchamiania w systemie docelowym. Aby uzyskać więcej informacji, zobacz:

- [Tworzenie nowego projektu systemu Linux](create-a-new-linux-project.md)
- [Konfigurowanie projektu CMake systemu Linux](cmake-linux-project.md)
