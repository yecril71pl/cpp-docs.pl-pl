---
title: Menu i zasoby (OLE) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- OLE visual editing servers [MFC]
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- string tables [MFC], visual editing applications
- OLE containers [MFC], menus and resources
- OLE applications [MFC], menus and resources
- OLE server applications [MFC], menus and resources
- toolbars [MFC], OLE document applications
- string editing [MFC], visual editing applications
- server applications [MFC], OLE menus and resources
- applications [OLE], menus and resources
- menus [MFC], OLE document applications
- in-place activation [MFC], OLE menus and resources
- containers [MFC], OLE container applications
- OLE menus and resources [MFC]
ms.assetid: 52bfa086-7d3d-466f-94c7-c7061f3bdb3a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: efe0a5f6dae2cece571eddabc4094ebb87df175b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="menus-and-resources-ole"></a>Menu i zasoby (OLE)
Ta grupa artykułów wyjaśnienia dotyczące korzystania z menu i zasoby w aplikacji MFC OLE dokumentu.  
  
 OLE edycja wizualna umieszcza dodatkowe wymagania w menu i innych zasobów udostępnianych przez dokumenty i aplikacje OLE, ponieważ istnieją różne tryby w obu kontenera i aplikacji serwera (składnik) można uruchomić i używane. Na przykład aplikacji pełny serwer można uruchomić w jednym z tych trzech metod:  
  
-   Autonomiczne.  
  
-   W miejscu do edycji elementu w ramach kontenera.  
  
-   Otwórz do edycji elementu poza kontekstem swojego kontenera, często w osobnym oknie.  
  
 Wymaga to trzy układy oddzielne menu, po jednej dla każdego możliwe trybu aplikacji. Tabele akceleratora również są niezbędne dla każdego nowego trybu. Aplikacji kontenera mogą lub nie mogą obsługiwać Aktywacja w miejscu; Jeśli tak, wymaga nowej struktury menu i skojarzone tabele akceleratora.  
  
 Aktywacja w miejscu wymaga, aby kontenera i serwera aplikacji, muszą uzgodnić miejsce paska menu, paska narzędzi i stan. Wszystkie zasoby muszą być zaprojektowane z tym pamiętać. Artykuł [menu i zasoby: scalanie Menu](../mfc/menus-and-resources-menu-merging.md) opisano w tym temacie szczegółowo.  
  
 Z powodu problemów z te dokumenty i aplikacje OLE utworzonych za pomocą Kreatora aplikacji może mieć maksymalnie cztery oddzielne menu i zasoby tabeli akceleratora. Są one używane w następujących sytuacjach:  
  
|Nazwa zasobu|Zastosowanie|  
|-------------------|---------|  
|**IDR_MAINFRAME**|Używane w aplikacji MDI, jeśli plik nie jest otwarty lub w aplikacji SDI niezależnie od otwartych plików. Jest to standardowe menu używany w aplikacjach innych niż OLE.|  
|**IDR_\<projektu > typu**|Jeśli pliki są otwarte, należy użyć w aplikacji MDI. Używany, gdy aplikacja jest uruchomiona jako autonomiczna. Jest to standardowe menu używany w aplikacjach innych niż OLE.|  
|**IDR_\<projektu > TYPE_SRVR_IP**|Używane przez serwer lub kontenera, gdy obiekt jest otwarty w miejscu.|  
|**IDR_\<projektu > TYPE_SRVR_EMB**|Używany przez aplikację serwer, jeśli obiekt został otwarty bez użycia Aktywacja w miejscu.|  
  
 Każda z tych nazw zasobów reprezentuje menu i zazwyczaj tabeli akceleratora. Schemat podobne należy używać w aplikacjach MFC, które nie są tworzone przy użyciu Kreatora aplikacji.  
  
 W następujących artykułach omówiono tematów związanych z kontenerów, serwerów i menu scalanie niezbędne do zaimplementowania Aktywacja w miejscu:  
  
-   [Menu i zasoby: dodatki do kontenera](../mfc/menus-and-resources-container-additions.md)  
  
-   [Menu i zasoby: dodatki do serwera](../mfc/menus-and-resources-server-additions.md)  
  
-   [Menu i zasoby: scalanie menu](../mfc/menus-and-resources-menu-merging.md)  
  
## <a name="see-also"></a>Zobacz też  
 [OLE](../mfc/ole-in-mfc.md)

