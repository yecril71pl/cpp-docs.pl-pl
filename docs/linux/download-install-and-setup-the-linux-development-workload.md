---
title: Zainstaluj obciążenie systemu Linux w języku C++ w programie Visual Studio
description: W tym artykule opisano, jak pobrać, zainstalować i skonfigurować obciążenia systemu Linux dla języka C++ w programie Visual Studio.
ms.date: 02/06/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: c01c8ddeeb8439a7610c0f6c7c11b608ab3675d8
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2019
ms.locfileid: "55763892"
---
# <a name="download-install-and-setup-the-linux-workload"></a>Pobieranie, instalowanie i konfigurowanie obciążeń systemu Linux

Visual Studio IDE w Windows służy do tworzenia, edytowania i debugowania projektów w języku C++, które są wykonywane na komputerze fizycznym Linux maszyny wirtualnej lub [podsystem Windows dla systemu Linux](/windows/wsl/about). Dla każdego z tych scenariuszy, należy najpierw zainstalować **programowanie dla systemu Linux przy użyciu języka C++** obciążenia.

## <a name="visual-studio-setup"></a>Instalator programu Visual Studio

1. Wpisz "Instalator programu Visual Studio" w polu wyszukiwania Windows: ![Pole wyszukiwania Windows](media/visual-studio-installer-search.png)
2. Wyszukaj Instalatora w obszarze **aplikacje** wyniki, a następnie kliknij go dwukrotnie. Po otwarciu Instalatora wybierz **Modyfikuj**, a następnie kliknij polecenie **obciążeń** kartę. Przewiń w dół do **inne zestawy narzędzi** i wybierz **programowanie dla systemu Linux przy użyciu języka C++** obciążenia.

   ![Visual C++ dla obciążenia programowanie dla systemu Linux](media/linuxworkload.png)

1. Jeśli używasz narzędzia CMake lub są przeznaczone dla platformy osadzonych i IoT, przejdź do strony **szczegółowe informacje dotyczące instalacji** w okienku po prawej stronie w obszarze **programowanie dla systemu Linux przy użyciu języka C++**, rozwiń węzeł **składniki opcjonalne** i wybierz potrzebne składniki.

1. Kliknij przycisk **Modyfikuj** do kontynuowania instalacji.

## <a name="options-for-creating-a-linux-environment"></a>Opcje tworzenia środowiska systemu Linux

Jeśli nie masz jeszcze maszyny z systemem Linux, możesz utworzyć maszynę wirtualną z systemem Linux na platformie Azure. Aby uzyskać więcej informacji, zobacz [Szybki Start: Utwórz maszynę wirtualną systemu Linux w witrynie Azure portal](/azure/virtual-machines/linux/quick-create-portal).

Innym rozwiązaniem, w systemie Windows 10 jest aktywacja podsystemu Windows dla systemu Linux. Aby uzyskać więcej informacji, zobacz [Przewodnik instalacji systemu Windows 10](/windows/wsl/install-win10).

## <a name="linux-setup-ubuntu"></a>Konfiguracja w systemie Linux: Ubuntu

Komputer docelowy z systemem Linux muszą mieć **openssh-server**, **g ++**, **gdb**, i **serwera gdbserver** zainstalowane i ssh demona musi być uruchomiona. **ZIP** jest wymagany do automatycznej synchronizacji zdalnych nagłówków z komputerze lokalnym, aby uzyskać obsługę technologii Intellisense. Jeśli te aplikacje nie są już obecne, możesz zainstalować je w następujący sposób:

1. W wierszu polecenia powłoki na komputerze z systemem Linux Uruchom polecenie:

   `sudo apt-get install openssh-server g++ gdb gdbserver zip`

   Może zostać wyświetlony o podanie hasła głównego ze względu na polecenia "sudo".  Jeśli tak, wprowadź go i kontynuować. Po wykonaniu tych czynności, wymagane usługi i narzędzia są zainstalowane.

1. Upewnij się, ssh jest uruchomiona na komputerze z systemem Linux, uruchamiając:

   `sudo service ssh start`

   Spowoduje to uruchomienie usługi i działa w tle, gotowy do akceptowania połączeń.

## <a name="linux-setup-fedora"></a>Konfiguracja w systemie Linux: Fedora

Używa docelowej maszynie Fedora **dnf** pakiet Instalatora. Aby pobrać **openssh-server**, **g ++**, **gdb**, **serwera gdbserver** i **zip**i uruchom ponownie ssh demon, wykonaj te instrukcje:

1. W wierszu polecenia powłoki na komputerze z systemem Linux Uruchom polecenie:

   `sudo dnf install openssh-server gcc-g++ gdb gdb-gdbserver zip`

   Może zostać wyświetlony o podanie hasła głównego ze względu na polecenia "sudo".  Jeśli tak, wprowadź go i kontynuować. Po wykonaniu tych czynności, wymagane usługi i narzędzia są zainstalowane.

1. Upewnij się, ssh jest uruchomiona na komputerze z systemem Linux, uruchamiając:

   `sudo systemctl start sshd`

   Spowoduje to uruchomienie usługi i działa w tle, gotowy do akceptowania połączeń.

