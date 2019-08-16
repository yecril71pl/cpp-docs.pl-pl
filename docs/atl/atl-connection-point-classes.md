---
title: Klasy punktów połączenia ATL
ms.date: 11/04/2016
helpviewer_keywords:
- CFirePropNotifyEvent class, connection point classes
- connection points [C++], ATL classes
- ATL, connection points
- CComDynamicUnkArray class, connection point classes
- CFirePropNotifyEvent class
- CComUnkArray class, connection point classes
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
ms.openlocfilehash: 8644fc087d7f0a651724c40d2868e96c9b6ec96a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491827"
---
# <a name="atl-connection-point-classes"></a>Klasy punktów połączenia ATL

ATL używa następujących klas do obsługi punktów połączenia:

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementuje punkt połączenia. Identyfikator IID interfejsu wychodzącego, który reprezentuje, jest przesyłany jako parametr szablonu.

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implementuje kontener punktu połączenia i zarządza listą `IConnectionPointImpl` obiektów.

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implementuje punkt połączenia reprezentujący Interfejs [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) .

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) zarządza dowolną liczbą połączeń między punktem połączenia a jego ujściam.

- [CComUnkArray](../atl/reference/ccomunkarray-class.md) zarządza wstępnie zdefiniowaną liczbą połączeń określoną przez parametr szablonu.

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) powiadamia ujścia klienta, że właściwość obiektu została zmieniona lub jest zmieniana.

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md) zapewnia obsługę punktów połączenia dla obiektu com ATL. Te punkty połączenia są mapowane na mapę ujścia zdarzeń, która jest dostarczana przez obiekt COM.

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) działa w połączeniu z mapą ujścia zdarzeń w klasie w celu kierowania zdarzeń do odpowiedniej funkcji obsługi.

## <a name="see-also"></a>Zobacz także

[Punkt połączenia](../atl/atl-connection-points.md)
