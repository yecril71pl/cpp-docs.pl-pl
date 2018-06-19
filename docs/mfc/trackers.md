---
title: Trackery | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f0a0cc52e3a5150702af4acd293def38df758fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381540"
---
# <a name="trackers"></a>Trackery
[Crecttracker —](../mfc/reference/crecttracker-class.md) klasy udostępnia interfejs użytkownika między elementami prostokątne w aplikacji i użytkownika, podając różnych stylów wyświetlania. Te style zawierają stały, kreskowanym lub przerywane obramowania; kreskowane wzorzec, który obejmuje pozycję; i uchwytów zmiany rozmiaru, które mogą znajdować się na zewnątrz lub wewnątrz obramowania. Trackery są często używane w połączeniu z elementami OLE, czyli obiekty pochodne `COleClientItem`. Prostokąty tracker nadaj wizualnych na bieżący stan elementu.  
  
 Przykładowe MFC OLE [OCLIENT](../visual-cpp-samples.md) przedstawiono wspólny interfejs przy użyciu trackerów i elementy klienckie OLE z punktu widzenia aplikacji kontenera. Pokaz różnych stylach i możliwości obiekt śledzący dla przykładowych ogólne MFC [TRACKER](../visual-cpp-samples.md).  
  
 Aby uzyskać więcej informacji dotyczących Implementowanie trackerów w aplikacji OLE, zobacz [Trackery: Implementowanie Trackerów w tym OLE aplikacji](../mfc/trackers-implementing-trackers-in-your-ole-application.md)  
  
## <a name="see-also"></a>Zobacz też  
 [OLE](../mfc/ole-in-mfc.md)   
 [Klasa COleClientItem](../mfc/reference/coleclientitem-class.md)
