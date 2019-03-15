---
title: Punkty połączenia klasy (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
ms.openlocfilehash: 8e1ee67f75af1fa38693f7ddb487580ab733cc58
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819002"
---
# <a name="connection-points-classes"></a>Klasy punktów połączenia

Następujące klasy obsługi punkty połączeń:

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implementuje kontener punktu połączenia.

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementuje punkt połączenia.

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implementuje reprezentujący punkt połączenia [ipropertynotifysink —](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) interfejsu.

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) zarządza nieograniczone połączenia między punktem połączenia i jego ujścia.

- [CComUnkArray](../atl/reference/ccomunkarray-class.md) zarządza stałą liczbą połączeń między punktem połączenia i jego ujścia.

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) powiadamia zbiornikiem klienta, który do właściwości obiektu został zmieniony lub zostanie zmienione.

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md) zapewnia obsługę punkty połączenia dla obiektu ATL COM. Punkty połączenia są mapowane z mapą obiekt sink zdarzenia są dostarczane przez obiekt COM.

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) działa w połączeniu z obiektu sink zdarzenia mapy w swojej klasie w celu kierowanie zdarzeń do funkcji odpowiedni program obsługi.

## <a name="related-articles"></a>Powiązane artykuły

[Punkty połączenia](../atl/atl-connection-points.md)

[Obsługa zdarzeń i ATL](../atl/event-handling-and-atl.md)

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../atl/atl-class-overview.md)<br/>
[Makra punktów połączenia](../atl/reference/connection-point-macros.md)<br/>
[Funkcje globalne punktu połączenia](../atl/reference/connection-point-global-functions.md)
