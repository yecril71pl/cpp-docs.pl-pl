---
title: 'Serwery: Implementowanie serwera | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- servers, implementing
- OLE server applications [MFC], implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4ed4ca1b131e56b2735b3a6e4ba408f3ad79b8de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="servers-implementing-a-server"></a>Serwery: implementowanie serwera
W tym artykule opisano kod, który tworzy Kreator aplikacji MFC visual edytowania aplikacji serwera. Jeśli nie używasz Kreatora aplikacji, w tym artykule wymieniono obszarów, gdzie należy napisać kod do implementacji aplikacji serwera.  
  
 Jeśli używasz Kreatora aplikacji do tworzenia nowej aplikacji serwera, zapewnia znaczną ilość kodu specyficzne dla serwera dla Ciebie. Jeśli dodajesz visual edycji funkcje serwera do istniejącej aplikacji, należy skopiować kod Kreatora aplikacji czy zostały podane przed dodaniem reszty kod serwera niezbędne.  
  
 Kod serwera, który udostępnia Kreatora aplikacji znajduje się na kilka kategorii:  
  
-   Definiowanie zasobów serwera:  
  
    -   Używany, gdy serwer edytuje element osadzony w osobnym oknie zasobu menu.  
  
    -   Menu i paska narzędzi zasoby używane, gdy serwer jest aktywny w miejscu.  
  
     Aby uzyskać więcej informacji o tych zasobów, zobacz [menu i zasoby: dodatki do serwera](../mfc/menus-and-resources-server-additions.md).  
  
-   Definiowanie klasy element pochodny `COleServerItem`. Aby uzyskać więcej szczegółowych informacji o serwerze elementów, zobacz [serwery: elementy serwera](../mfc/servers-server-items.md).  
  
-   Zmiana klasy podstawowej klasy dokumentu, aby `COleServerDoc`. Aby uzyskać szczegółowe informacje, zobacz [serwery: Implementowanie dokumentów serwera](../mfc/servers-implementing-server-documents.md).  
  
-   Definiowanie klasy okien ramowych pochodną `COleIPFrameWnd`. Aby uzyskać szczegółowe informacje, zobacz [serwery: Implementowanie okien ramowych w miejscu](../mfc/servers-implementing-in-place-frame-windows.md).  
  
-   Tworzenie wpis dla aplikacji serwera w bazie danych rejestracji systemu Windows i rejestrowanie nowego wystąpienia serwera w systemie OLE. Aby uzyskać informacje na ten temat, zobacz [rejestracji](../mfc/registration.md).  
  
-   Inicjowanie i uruchamianie aplikacji serwera. Aby uzyskać informacje na ten temat, zobacz [rejestracji](../mfc/registration.md).  
  
 Aby uzyskać więcej informacji, zobacz [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerDoc](../mfc/reference/coleserverdoc-class.md), i [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md) w *informacje dotyczące biblioteki klas*.  
  
## <a name="see-also"></a>Zobacz też  
 [Serwery](../mfc/servers.md)   
 [Kontenery](../mfc/containers.md)   
 [Menu i zasoby (OLE)](../mfc/menus-and-resources-ole.md)   
 [Rejestracji](../mfc/registration.md)

