---
title: "Klasy punkty połączenia (ATL) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.atl.connection
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aa0ef8139c659b5085b20709e0c96ab2bf821ce4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="connection-points-classes"></a>Klasy punkty połączenia
Następujące klasy zapewniają obsługę punkty połączeń:  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implementuje kontener punktu połączenia.  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementuje punkt połączenia.  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implementuje punkt połączenia reprezentującą [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfejsu.  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) zarządza nieograniczoną liczbę połączeń między punktem połączenia i jego sink.  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md) zarządza stała liczba połączeń między punktu połączenia i jego sink.  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) powiadamia zbiornika klienta, który właściwości obiektu został zmieniony lub ma zostać zmieniona.  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md) zapewnia obsługę punktów połączeń dla obiekt ATL COM. Punkty połączenia są mapowane z map obiekt sink zdarzenia, które są dostarczane przez obiekt COM.  
  
-   [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) mapy działa w połączeniu z obiektu sink zdarzenia w klasie zdarzeń trasy do funkcji odpowiedni program obsługi.  
  
## <a name="related-articles"></a>Powiązane artykuły  
 [Punkty połączenia](../atl/atl-connection-points.md)  
  
 [Obsługa zdarzeń i ATL](../atl/event-handling-and-atl.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../atl/atl-class-overview.md)   
 [Makra punktu połączenia](../atl/reference/connection-point-macros.md)   
 [Funkcje globalne punktu połączenia](../atl/reference/connection-point-global-functions.md)

