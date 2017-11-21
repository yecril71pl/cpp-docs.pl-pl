---
title: Instalacja automatyzacji zdalnej | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Remote Automation [MFC], installation
- installing Remote Automation [MFC]
ms.assetid: 9a02c9f6-dfc6-4489-b240-a1afe25fa0c5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3908176b6fba46aa9675ac7aa61bb617f1bfa00a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="remote-automation-installation"></a>Instalacja automatyzacji zdalnej
Automatyzacja zdalna ma względnie mało składniki:  
  
-   Automatyzacja zdalna klienta serwera proxy, AUTPRX32. BIBLIOTEKI DLL.  
  
-   Automatyzacja zdalna po stronie serwera składnik, Menedżer automatyzacji AUTMGR32. WYWOŁANIE PLIKU EXE.  
  
-   Menedżer RAC RACMGR32. EXE z jego RACREG32 dopasowania. BIBLIOTEKI DLL.  
  
 Z nich Menedżera RAC napisano w języku Visual Basic i dlatego środowiska wykonawczego Visual Basic musi obsługiwać. Te i inne pliki automatyzacji zdalnej są zainstalowane przez Instalatora podczas instalowania programu Visual C++ Enterprise Edition.  
  
 Po skopiowaniu składniki automatyzacji zdalnej na komputerze, na wersję Visual C++ w wersji Enterprise nie jest zainstalowany, upewnij się, że REGSRV32. EXE znajduje się w ścieżce komputera i zarejestruj RACREG32. Biblioteki DLL przy użyciu następującego polecenia:  
  
 REGSRVR32 RACREG32. BIBLIOTEKI DLL  
  
> [!NOTE]
>  Wersje Menedżera RAC przed Visual C++ 5.0 wymagane GUAGE32. OCX i TABCTL32. OCX. Oba te jest wymagany dla używanej wersji programu RAC Manager, która jest dostarczany z programu Visual C++ Enterprise Edition w wersji 5.0 lub nowszej.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Menedżer automatyzacji](../mfc/automation-manager-mfc.md)  
  
 [Menedżer połączeń automatyzacji zdalnej](../mfc/remote-automation-connection-manager.md)  
  
 [Składniki użytkownika automatyzacji zdalnej](../mfc/remote-automation-user-components.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyzacja zdalna](../mfc/remote-automation.md)

