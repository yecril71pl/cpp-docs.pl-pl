---
title: Klasy punktów połączenia (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.connection
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d458fb5805b99c8dcc5cc25abc9f85f88f08e92
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957659"
---
# <a name="connection-points-classes"></a>Klasy punktów połączenia
Następujące klasy obsługi punkty połączeń:  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implementuje kontener punktu połączenia.  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementuje punkt połączenia.  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implementuje reprezentujący punkt połączenia [ipropertynotifysink —](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfejsu.  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) zarządza nieograniczone połączenia między punktem połączenia i jego ujścia.  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md) zarządza stałą liczbą połączeń między punktem połączenia i jego ujścia.  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) powiadamia zbiornikiem klienta, który do właściwości obiektu został zmieniony lub zostanie zmienione.  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md) zapewnia obsługę punkty połączenia dla obiektu ATL COM. Punkty połączenia są mapowane z mapą obiekt sink zdarzenia są dostarczane przez obiekt COM.  
  
-   [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) działa w połączeniu z obiektu sink zdarzenia mapy w swojej klasie w celu kierowanie zdarzeń do funkcji odpowiedni program obsługi.  
  
## <a name="related-articles"></a>Powiązane artykuły  
 [Punkty połączenia](../atl/atl-connection-points.md)  
  
 [Obsługa zdarzeń i ATL](../atl/event-handling-and-atl.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa — Przegląd](../atl/atl-class-overview.md)   
 [Makra punktów połączenia](../atl/reference/connection-point-macros.md)   
 [Funkcje globalne punktu połączenia](../atl/reference/connection-point-global-functions.md)

