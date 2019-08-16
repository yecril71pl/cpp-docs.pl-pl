---
title: Klasy punktów połączenia (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
ms.openlocfilehash: 0dba06b072e1e9ca545ccbea196fcfe371b02157
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492446"
---
# <a name="connection-points-classes"></a>Klasy punktów połączenia

Następujące klasy zapewniają obsługę punktów połączenia:

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) Implementuje kontener punktu połączenia.

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) Implementuje punkt połączenia.

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) Implementuje punkt połączenia reprezentujący Interfejs [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) .

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) Zarządza nieograniczoną liczbą połączeń między punktem połączenia a jego ujściam.

- [CComUnkArray](../atl/reference/ccomunkarray-class.md) Zarządza stałą liczbą połączeń między punktem połączenia a jego ujściam.

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) Powiadamia ujścia klienta o zmianie właściwości obiektu lub o zmianie.

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md) Zapewnia obsługę punktów połączenia dla obiektu ATL COM. Te punkty połączenia są mapowane na mapę ujścia zdarzeń, która jest dostarczana przez obiekt COM.

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) Działa w połączeniu z mapą ujścia zdarzeń w klasie w celu kierowania zdarzeń do odpowiedniej funkcji obsługi.

## <a name="related-articles"></a>Powiązane artykuły

[Punkty połączenia](../atl/atl-connection-points.md)

[Obsługa zdarzeń i ATL](../atl/event-handling-and-atl.md)

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../atl/atl-class-overview.md)<br/>
[Makra punktów połączenia](../atl/reference/connection-point-macros.md)<br/>
[Funkcje globalne punktu połączenia](../atl/reference/connection-point-global-functions.md)
