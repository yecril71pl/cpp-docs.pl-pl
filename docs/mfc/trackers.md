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
ms.openlocfilehash: 74e70f989d3803b11f05150f9b55c6dfe79ed876
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481955"
---
# <a name="trackers"></a>Trackery

[CRectTracker](../mfc/reference/crecttracker-class.md) klasa udostępnia interfejs użytkownika między elementami prostokątny w aplikacji i użytkowników poprzez zapewnienie różnych stylów wyświetlania. Te style zawierają granice stały, kreskowanym lub kreskowane; kreskowane wzorzec, który obejmuje element; i uchwytami zmiany rozmiaru, które mogą być umieszczone na zewnątrz lub wewnątrz obramowania. Trackery są często używane w połączeniu z elementów OLE, oznacza to, że obiekty pochodzące z `COleClientItem`. Prostokąty tracker zapewniają podpowiedzi wizualne z bieżącym stanem elementu.

Przykładowe MFC OLE [OCLIENT](../visual-cpp-samples.md) pokazuje wspólny interfejs, za pomocą trackery i elementy klienckie OLE z punktu widzenia aplikacji kontenera. Pokaz różne style i możliwości śledzenia obiektu, zobacz przykład ogólne MFC [TRACKER](../visual-cpp-samples.md).

Aby uzyskać więcej informacji na temat Implementowanie trackerów w aplikacji OLE, zobacz [Trackery: Implementowanie Trackerów w OLE aplikacji](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

## <a name="see-also"></a>Zobacz też

[OLE](../mfc/ole-in-mfc.md)<br/>
[Klasa COleClientItem](../mfc/reference/coleclientitem-class.md)
