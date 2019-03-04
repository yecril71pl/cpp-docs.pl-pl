---
title: Trackery
ms.date: 11/04/2016
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
ms.openlocfilehash: 6dffb5b4326d08daf59098e1888169c2353dafe2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262717"
---
# <a name="trackers"></a>Trackery

[CRectTracker](../mfc/reference/crecttracker-class.md) klasa udostępnia interfejs użytkownika między elementami prostokątny w aplikacji i użytkowników poprzez zapewnienie różnych stylów wyświetlania. Te style zawierają granice stały, kreskowanym lub kreskowane; kreskowane wzorzec, który obejmuje element; i uchwytami zmiany rozmiaru, które mogą być umieszczone na zewnątrz lub wewnątrz obramowania. Trackery są często używane w połączeniu z elementów OLE, oznacza to, że obiekty pochodzące z `COleClientItem`. Prostokąty tracker zapewniają podpowiedzi wizualne z bieżącym stanem elementu.

Przykładowe MFC OLE [OCLIENT](../visual-cpp-samples.md) pokazuje wspólny interfejs, za pomocą trackery i elementy klienckie OLE z punktu widzenia aplikacji kontenera. Pokaz różne style i możliwości śledzenia obiektu, zobacz przykład ogólne MFC [TRACKER](../visual-cpp-samples.md).

Aby uzyskać więcej informacji na temat Implementowanie trackerów w aplikacji OLE, zobacz [Trackery: Implementowanie Trackerów w aplikacji OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

## <a name="see-also"></a>Zobacz także

[OLE](../mfc/ole-in-mfc.md)<br/>
[Klasa COleClientItem](../mfc/reference/coleclientitem-class.md)
