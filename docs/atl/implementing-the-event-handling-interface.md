---
title: "Implementowanie obsługi interfejsu zdarzeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ATL, event handling
- event handling, ATL
- interfaces, event and event sink
ms.assetid: eb2a5b33-88dc-4ce3-bee0-c5c38ea050d7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9226cf2630ad18651f9bda2f154f49b5b739a433
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-the-event-handling-interface"></a>Implementowanie obsługi interfejsu zdarzeń
ATL pomaga wszystkie trzy elementy wymagane do obsługi zdarzeń: implementacja interfejsu zdarzenia, udzielanie porad źródło zdarzenia i unadvising źródło zdarzenia. Dokładne kroki, które należy podjąć, zależą od typu interfejsu zdarzenia i wymagania dotyczące wydajności aplikacji.  
  
 Najbardziej typowe sposoby wdrażania interfejsu za pomocą biblioteki ATL są:  
  
-   Wyprowadzanie z niestandardowego interfejsu.  
  
-   Wyprowadzanie z [elementem IDispatchImpl](../atl/reference/idispatchimpl-class.md) dla dwóch interfejsów opisanych w bibliotece typów.  
  
-   Wyprowadzanie z [IDispEventImpl](../atl/reference/idispeventimpl-class.md) dla dispinterfaces opisanych w bibliotece typów.  
  
-   Wyprowadzanie z [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) dla dispinterfaces nie opisano w bibliotece typów lub umożliwia zwiększenie wydajności przez nie ładowanie informacji o typie w czasie wykonywania.  
  

 W przypadku wdrażania interfejsu niestandardowych lub Podwójna, należy poinformować źródło zdarzenia, przez wywołanie metody [AtlAdvise](reference/connection-point-global-functions.md#atladvise) lub [CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise). Należy do śledzenia plik cookie zwrócony przez wywołanie. Wywołanie [AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise) aby przerwać połączenie.  

  
 W przypadku wdrażania przy użyciu dispinterface `IDispEventImpl` lub `IDispEventSimpleImpl`, należy poinformować źródło zdarzenia, wywołując [IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise). Wywołanie [IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise) aby przerwać połączenie.  
  
 Jeśli używasz `IDispEventImpl` jako klasę podstawową złożonego formantu źródła zdarzeń mapy zbiornika na liście będzie zaleca i unadvised automatycznie za pomocą [CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).  
  
 `IDispEventImpl` i `IDispEventSimpleImpl` klasy zarządzać pliku cookie.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa zdarzeń](../atl/event-handling-and-atl.md)

