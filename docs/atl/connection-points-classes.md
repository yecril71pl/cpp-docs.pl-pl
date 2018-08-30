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
ms.openlocfilehash: b3f866d56d0c0ab89a91b13e238d9503c1ca9e02
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205078"
---
# <a name="connection-points-classes"></a>Klasy punktów połączenia
Następujące klasy obsługi punkty połączeń:  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implementuje kontener punktu połączenia.  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementuje punkt połączenia.  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implementuje reprezentujący punkt połączenia [ipropertynotifysink —](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) interfejsu.  
  
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

