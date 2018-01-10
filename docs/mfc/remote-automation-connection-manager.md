---
title: "Menedżer połączeń automatyzacji zdalnej | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Automation clients [MFC], configuring for Remote Automation
- registry [MFC], remote Automation
- Automation servers [MFC], configuring for Remote Automation
- Remote Automation Connection Manager [MFC]
- Remote Automation [MFC], configuring client and server machines
- RAC Manager tool [MFC]
ms.assetid: 562eb7bc-f95c-46ad-ac97-f0dfa98362af
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cf316653b2f968fd5373c6265bb4f3f3ef3b0ba4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="remote-automation-connection-manager"></a>Menedżer połączeń automatyzacji zdalnej
Aby skonfigurować klienta i na serwerze, należy wprowadzić zmiany w rejestrze. Zamiast ręcznie w ten sposób, znacznie łatwiej jest narzędzie Menedżer połączeń automatyzacji zdalnej (RAC). To narzędzie RACMGR32. EXE, wraz z RACREG32. Biblioteki DLL, musi ma zostać skopiowany do dowolnego katalogu, którą wybierzesz. Umieszczenie go w ŚCIEŻCE, można wykonać z poziomu paska zadań za pomocą polecenia Uruchom. Alternatywnie można utworzyć skrótu do niego, albo umieść odwołanie do niej w Start menu.  
  
 RACMGR32 jest napisany w języku Visual Basic i dlatego wymaga niektórych Visual Basic obsługują biblioteki dll. Te pliki są umieszczane w tym samym katalogu co RACMGR32. EXE na dysku CD. Wersje tych plików, które są zainstalowane przez Instalatora programu Visual C++ Enterprise Edition są równoważne lub nowszą niż te, które zostały wydane z Visual Basic Enterprise Edition w wersji 5.0. Instalator programu Visual C++ kopiuje nowych wersji plików programu Visual Basic do katalogu w systemie. W przypadku systemu Windows 9 x ten katalog jest zwykle C:\Windows\System. Dla systemu Windows NT i Windows 2000 jest zazwyczaj C:\WINNT\system32. Instalator rejestruje także tych plików w systemie operacyjnym. Można je usunąć z instalacji programu Visual Basic.  
  
## <a name="see-also"></a>Zobacz też  
 [Menedżer automatyzacji (MFC)](../mfc/automation-manager-mfc.md)   
 [Składniki użytkownika automatyzacji zdalnej](../mfc/remote-automation-user-components.md)   
 [Instalacja automatyzacji zdalnej](../mfc/remote-automation-installation.md)

