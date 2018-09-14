---
title: Zainstaluj obciążenie systemu Linux w języku C++ w programie Visual Studio | Dokumentacja firmy Microsoft
description: W tym artykule opisano, jak pobrać, zainstalować i skonfigurować obciążenia systemu Linux dla języka C++ w programie Visual Studio.
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 403f1bcd8634c3f471f34ff1266501de5bf05d52
ms.sourcegitcommit: 87d317ac62620c606464d860aaa9e375a91f4c99
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45601395"
---
# <a name="download-install-and-setup-the-linux-workload"></a>Pobieranie, instalowanie i konfigurowanie obciążeń systemu Linux

Visual Studio IDE w Windows służy do tworzenia, edytowania i debugowania projektów w języku C++, które są wykonywane na komputerze fizycznym Linux maszyny wirtualnej lub [podsystem Windows dla systemu Linux](/windows/wsl/about). Dla każdego z tych scenariuszy, należy najpierw zainstalować **programowanie dla systemu Linux przy użyciu języka C++** obciążenia.

## <a name="visual-studio-setup"></a>Instalator programu Visual Studio

1. Wpisz "Instalator programu Visual Studio" w menu wyszukiwania Windows; Wyszukaj go w folderze **aplikacje** wyniki, a następnie kliknij go dwukrotnie. Po otwarciu Instalatora wybierz **Modyfikuj**, a następnie kliknij polecenie **obciążeń** kartę. Przewiń w dół do **inne zestawy narzędzi** i wybierz **programowanie dla systemu Linux przy użyciu języka C++** obciążenia.

   ![Visual C++ dla obciążenia programowanie dla systemu Linux](media/linuxworkload.png)

1. Jeśli używasz narzędzia CMake lub są przeznaczone dla platformy osadzonych i IoT, przejdź do strony **szczegółowe informacje dotyczące instalacji** w okienku po prawej stronie w obszarze **programowanie dla systemu Linux przy użyciu języka C++**, rozwiń węzeł **składniki opcjonalne** i wybierz potrzebne składniki. 

1. Kliknij przycisk **Modyfikuj** do kontynuowania instalacji.


## <a name="options-for-creating-a-linux-environment"></a>Opcje tworzenia środowiska systemu Linux

Jeśli nie masz jeszcze maszyny z systemem Linux, możesz utworzyć maszynę wirtualną z systemem Linux na platformie Azure. Aby uzyskać więcej informacji, zobacz [Szybki Start: tworzenie maszyny wirtualnej systemu Linux w witrynie Azure portal](/azure/virtual-machines/linux/quick-create-portal).

Innym rozwiązaniem, w systemie Windows 10 jest aktywacja podsystemu Windows dla systemu Linux. Aby uzyskać więcej informacji, zobacz [Przewodnik instalacji systemu Windows 10](/windows/wsl/install-win10).

## <a name="linux-setup"></a>Konfiguracja w systemie Linux

Komputer docelowy z systemem Linux muszą mieć **openssh-server**, **g ++**, **gdb**, i **serwera gdbserver** zainstalowane i ssh demona musi być uruchomiona. **ZIP** jest wymagany do automatycznej synchronizacji zdalnych nagłówków z komputerze lokalnym, aby uzyskać obsługę technologii Intellisense. Jeśli te aplikacje nie są już obecne, możesz zainstalować je w następujący sposób:

1. W wierszu polecenia powłoki na komputerze z systemem Linux Uruchom polecenie:

   `sudo apt-get install openssh-server g++ gdb gdbserver zip`

   Może zostać wyświetlony o podanie hasła głównego ze względu na polecenia "sudo".  Jeśli tak, wprowadź go i kontynuować.  Po wykonaniu tych czynności, zostanie zainstalowana tych usług i narzędzi.

1. Upewnij się, ssh jest uruchomiona na komputerze z systemem Linux, uruchamiając:

   `sudo service ssh start`

   Spowoduje to uruchom usługę i uruchom go w tle, gotowy do akceptowania połączeń.
