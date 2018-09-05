---
title: Klasy punktów połączenia ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CFirePropNotifyEvent class, connection point classes
- connection points [C++], ATL classes
- ATL, connection points
- CComDynamicUnkArray class, connection point classes
- CFirePropNotifyEvent class
- CComUnkArray class, connection point classes
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 141142db5dff185cf4f8a0ad42c4b322e7d7739a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763883"
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

## <a name="see-also"></a>Zobacz też

[Punkt połączenia](../atl/atl-connection-points.md)

