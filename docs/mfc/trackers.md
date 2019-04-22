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
ms.openlocfilehash: b71eb0e5d46a790b01ec12f12043af783bdfcf27
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58771451"
---
# <a name="trackers"></a>Trackery

[CRectTracker](../mfc/reference/crecttracker-class.md) klasa udostępnia interfejs użytkownika między elementami prostokątny w aplikacji i użytkowników poprzez zapewnienie różnych stylów wyświetlania. Te style zawierają granice stały, kreskowanym lub kreskowane; kreskowane wzorzec, który obejmuje element; i uchwytami zmiany rozmiaru, które mogą być umieszczone na zewnątrz lub wewnątrz obramowania. Trackery są często używane w połączeniu z elementów OLE, oznacza to, że obiekty pochodzące z `COleClientItem`. Prostokąty tracker zapewniają podpowiedzi wizualne z bieżącym stanem elementu.

Przykładowe MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) pokazuje wspólny interfejs, za pomocą trackery i elementy klienckie OLE z punktu widzenia aplikacji kontenera. Pokaz różne style i możliwości śledzenia obiektu, zobacz przykład ogólne MFC [TRACKER](../overview/visual-cpp-samples.md).

Aby uzyskać więcej informacji na temat Implementowanie trackerów w aplikacji OLE, zobacz [Trackery: Implementowanie Trackerów w aplikacji OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

## <a name="see-also"></a>Zobacz także

[OLE](../mfc/ole-in-mfc.md)<br/>
[Klasa COleClientItem](../mfc/reference/coleclientitem-class.md)
