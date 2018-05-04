---
title: Klasy punktu połączenia ATL | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 49acd19fcb25751ac9223b557b068383556f63f3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="atl-connection-point-classes"></a>Klasy punktu połączenia ATL
ATL używa następujących klas do obsługi punkty połączeń:  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementuje punkt połączenia. Uzyskanie identyfikatora IID interfejsu wychodzącego, który reprezentuje jest przekazywana jako parametr szablonu.  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implementuje kontener punktu połączenia i służą do zarządzania listą `IConnectionPointImpl` obiektów.  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implementuje punkt połączenia reprezentującą [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfejsu.  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) zarządza dowolnej liczby połączeń między punktem połączenia i jego sink.  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md) zarządza liczbę połączeń określony przez parametr szablonu.  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) powiadamia zbiornika klienta, który właściwości obiektu został zmieniony lub ma zostać zmieniona.  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md) zapewnia obsługę punktów połączeń dla obiekt ATL COM. Punkty połączenia są mapowane z map obiekt sink zdarzenia, które są dostarczane przez obiekt COM.  
  
-   [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) działa w połączeniu z mapą obiekt sink zdarzenia w klasie zdarzeń trasy do funkcji obsługi odpowiednie.  
  
## <a name="see-also"></a>Zobacz też  
 [Punkt połączenia](../atl/atl-connection-points.md)

