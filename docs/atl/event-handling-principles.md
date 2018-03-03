---
title: "Obsługa zasad (ATL) zdarzeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6ec61751e16bd67686a983b43c79fea138b3fa4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="event-handling-principles"></a>Zasady obsługi zdarzeń
Istnieją trzy kroki wspólne dla wszystkich obsługi zdarzeń. Konieczne będzie:  
  
-   Implementowanie interfejsu zdarzenia na obiekt.  
  
-   Zalecamy źródła zdarzeń obiektu chce odbierać zdarzenia.  
  
-   Unadvise źródła zdarzeń, gdy obiekt nie będzie już potrzebował do odbierania zdarzeń.  
  
 Sposób, że będzie implementować interfejsu zdarzenia zależy od jego typu. Interfejs zdarzeń może być vtable, podwójnie lub dispinterface. Jest projektanta źródła zdarzeń, aby zdefiniować interfejs; to można zaimplementować ten interfejs.  
  
> [!NOTE]
>  Mimo że nie ma żadnych powodów technicznych, które interfejs zdarzeń nie mogą być dwa, istnieją istnieje wiele możliwych przyczyn dobry projekt, aby uniknąć użycia duals. Jest to jednak decyzji przez projektanta/implementujący zdarzenia *źródła*. Ponieważ pracy z punktu widzenia zdarzenia `sink`, konieczne jest zezwolenie na możliwość utracić wszelkie wyboru, ale implementuje interfejs dwa zdarzenia. Aby uzyskać więcej informacji na podwójne interfejsy, zobacz [podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md).  
  
 Udzielanie porad źródło zdarzenia mogą być podzielone na trzy kroki:  
  
-   Zapytania do obiektu źródłowego [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857).  
  
-   Wywołanie [IConnectionPointContainer::FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476) przekazywanie uzyskanie identyfikatora IID interfejsu zdarzenia, które można omawiać. W przypadku powodzenia to zwraca [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318) interfejsu dla obiektu punktu połączenia.  
  
-   Wywołanie [IConnectionPoint::Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815) przekazywanie **IUnknown** dla obiekt sink zdarzenia. W przypadku powodzenia to zwraca `DWORD` połączenia reprezentującą pliku cookie.  
  
 Po pomyślnym zarejestrowaniu zainteresowanie odbieranie zdarzeń, zostanie wywołana metody interfejsu zdarzenia do obiektu zgodnie z zdarzenia wywoływane przez obiekt źródłowy. Jeśli potrzebne jest już odbierać zdarzenia, można przekazać pliku cookie do punktu połączenia za pośrednictwem [IConnectionPoint::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608). Spowoduje to przerwanie połączenia między źródłowy i odbiorczy.  
  
 Należy zachować ostrożność uniknąć odwołania cykli podczas obsługi zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa zdarzeń](../atl/event-handling-and-atl.md)

