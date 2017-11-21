---
title: "Pobrać, zainstalować i skonfigurować obciążenie systemu Linux | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d2e19ee03483dce82846e7e7bbb0ab103e01203f
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
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
