---
title: Pobrać, zainstalować i skonfigurować obciążenie systemu Linux | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/16/2016
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
ms.openlocfilehash: 1d28f0db0ff91dbdb08c9ca88dfe197e8942a7f4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="download-install-and-setup-the-linux-workload"></a>Pobrać, zainstalować i skonfigurować obciążenie systemu Linux

## <a name="visual-studio-setup"></a>Instalator programu Visual Studio
1. Uruchom Instalator programu Visual Studio i wybierz **Linux Programowanie w języku C++** obciążenia.

   ![Dla rozszerzenia Visual C++](media/linuxworkload.png)

2. Kliknij przycisk **zainstalować** aby kontynuować instalację.

## <a name="linux-setup"></a>Konfiguracja w systemie Linux
Linux komputer docelowy musi mieć **serwera openssh**, **g ++**, **gdb**, i **gdbserver** zainstalowany i ssh demon musi być uruchomiona.  Jeśli te nie są już zainstalowane, można je zainstalować w następujący sposób:
 
1. W wierszu polecenia powłoki na komputer z systemem Linux Uruchom polecenie:

   `sudo apt-get install openssh-server g++ gdb gdbserver`

   Może zostać wyświetlony monit o podanie hasła głównego z powodu polecenie sudo.  Jeśli tak, wprowadź go i kontynuować.  Po zakończeniu tych usług i narzędzi zostanie zainstalowana.

1. Upewnij się, ssh jest uruchomiona na komputerze z systemem Linux, uruchamiając:

   `sudo service ssh start`
   
   Spowoduje to uruchomienie usługi i uruchom go w tle, gotowy do akceptowania połączeń.
