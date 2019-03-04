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
ms.openlocfilehash: f3794b5c9e4f6297cca6611929c75d0b0133557e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265239"
---
# <a name="atl-connection-point-classes"></a>Klasy punktów połączenia ATL

ATL używa następujących klas do obsługi punkty połączeń:

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementuje punkt połączenia. IID interfejsu wychodzącego, który reprezentuje jest przekazywany jako parametr szablonu.

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implementuje kontener punktu połączenia i służą do zarządzania listą `IConnectionPointImpl` obiektów.

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implementuje reprezentujący punkt połączenia [ipropertynotifysink —](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) interfejsu.

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) zarządza dowolną liczbę połączeń między punktem połączenia i jego ujścia.

- [CComUnkArray](../atl/reference/ccomunkarray-class.md) zarządza wstępnie zdefiniowanej liczby połączeń określony przez parametr szablonu.

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) powiadamia zbiornikiem klienta, który do właściwości obiektu został zmieniony lub zostanie zmienione.

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md) zapewnia obsługę punkty połączenia dla obiektu ATL COM. Punkty połączenia są mapowane z mapą obiekt sink zdarzenia są dostarczane przez obiekt COM.

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) działa w połączeniu z mapą obiekt sink zdarzenia w klasie do kierowanie zdarzeń do funkcji odpowiedni program obsługi.

## <a name="see-also"></a>Zobacz także

[Punkt połączenia](../atl/atl-connection-points.md)
