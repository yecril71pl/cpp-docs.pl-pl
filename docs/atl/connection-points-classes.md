---
title: Punkty połączenia klasy (ATL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.atl.connection
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
ms.openlocfilehash: 4965e5e371bd96903cad4d7f1e2b0ce3216107ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593976"
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

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../atl/atl-class-overview.md)<br/>
[Makra punktów połączenia](../atl/reference/connection-point-macros.md)<br/>
[Funkcje globalne punktu połączenia](../atl/reference/connection-point-global-functions.md)

