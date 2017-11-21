---
title: Trackery | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- trackers [MFC]
- OLE applications [MFC], trackers
- applications [OLE], trackers
- tracking OLE items [MFC]
- OLE containers [MFC], trackers
- CDC class [MFC], trackers
- CRectTracker class [MFC], implementing trackers
- OLE server applications [MFC], trackers
ms.assetid: dcd09399-6637-4621-80e5-d12670429787
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a36a327bcf2a1beb46119c9b6c2947d95473cbaf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="trackers"></a>Trackery
[Crecttracker —](../mfc/reference/crecttracker-class.md) klasy udostępnia interfejs użytkownika między elementami prostokątne w aplikacji i użytkownika, podając różnych stylów wyświetlania. Te style zawierają stały, kreskowanym lub przerywane obramowania; kreskowane wzorzec, który obejmuje pozycję; i uchwytów zmiany rozmiaru, które mogą znajdować się na zewnątrz lub wewnątrz obramowania. Trackery są często używane w połączeniu z elementami OLE, czyli obiekty pochodne `COleClientItem`. Prostokąty tracker nadaj wizualnych na bieżący stan elementu.  
  
 Przykładowe MFC OLE [OCLIENT](../visual-cpp-samples.md) przedstawiono wspólny interfejs przy użyciu trackerów i elementy klienckie OLE z punktu widzenia aplikacji kontenera. Pokaz różnych stylach i możliwości obiekt śledzący dla przykładowych ogólne MFC [TRACKER](../visual-cpp-samples.md).  
  
 Aby uzyskać więcej informacji dotyczących Implementowanie trackerów w aplikacji OLE, zobacz [Trackery: Implementowanie Trackerów w tym OLE aplikacji](../mfc/trackers-implementing-trackers-in-your-ole-application.md)  
  
## <a name="see-also"></a>Zobacz też  
 [OLE](../mfc/ole-in-mfc.md)   
 [Klasa COleClientItem](../mfc/reference/coleclientitem-class.md)
