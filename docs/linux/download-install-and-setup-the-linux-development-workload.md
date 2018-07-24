---
title: Zainstaluj obciążenie systemu Linux w języku C++ w programie Visual Studio | Dokumentacja firmy Microsoft
description: W tym artykule opisano, jak pobrać, zainstalować i skonfigurować obciążenia systemu Linux dla języka C++ w programie Visual Studio.
ms.custom: ''
ms.date: 07/20/2018
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
ms.openlocfilehash: e33b9ac72ca7691ccbb80a9a30349d3a1e31e194
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207562"
---
# <a name="download-install-and-setup-the-linux-workload"></a>Pobieranie, instalowanie i konfigurowanie obciążeń systemu Linux

Aby użyć środowiska IDE programu Visual Studio do tworzenia i debugowania projektów w języku C++ w systemie Linux, należy zainstalować **programowanie dla systemu Linux przy użyciu języka C++** obciążenia.

## <a name="visual-studio-setup"></a>Instalator programu Visual Studio
1. Uruchom Instalatora programu Visual Studio i wybierz **programowanie dla systemu Linux przy użyciu języka C++** obciążenia.

   ![Rozszerzenie programowanie dla systemu Linux w języku Visual C++](media/linuxworkload.png)

2. Kliknij przycisk **zainstalować** do kontynuowania instalacji.

## <a name="linux-setup"></a>Konfiguracja w systemie Linux
Komputer docelowy z systemem Linux muszą mieć **openssh-server**, **g ++**, **gdb**, i **serwera gdbserver** zainstalowane i ssh demona musi być uruchomiona.  Jeśli te nie są już obecne, możesz zainstalować je w następujący sposób:
 
1. W wierszu polecenia powłoki na komputerze z systemem Linux Uruchom polecenie:

   `sudo apt-get install openssh-server g++ gdb gdbserver`

   Może zostać wyświetlony o podanie hasła głównego ze względu na polecenia "sudo".  Jeśli tak, wprowadź go i kontynuować.  Po wykonaniu tych czynności, zostanie zainstalowana tych usług i narzędzi.

1. Upewnij się, ssh jest uruchomiona na komputerze z systemem Linux, uruchamiając:

   `sudo service ssh start`
   
   Spowoduje to uruchom usługę i uruchom go w tle, gotowy do akceptowania połączeń.
