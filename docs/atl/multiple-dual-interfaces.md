---
title: "Podwójne interfejsy wielu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- multiple dual interfaces
- COM_INTERFACE_ENTRY2 macro
- dual interfaces, exposing multiple
- multiple dual interfaces, exposing with ATL
- IDispatchImpl class, multiple dual interfaces
- COM_INTERFACE_ENTRY_IID macro
ms.assetid: 7fea86e6-247f-4063-be6e-85588a9e3719
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01d87164439a4128ff6205ea6bc3ee3d9cc5573a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="multiple-dual-interfaces"></a>Wiele podwójne interfejsy
Możesz połączyć korzyści wynikające z dwoma interfejsami (to znaczy elastyczność vtable i późne powiązania, w związku z tym udostępnienie klasy języków skryptów, a także C++) techniki dziedziczenie wielokrotne.  
  
 Chociaż jest możliwe do udostępnienia wielu podwójne interfejsy na pojedynczy obiekt COM, nie zaleca. Jeśli istnieje wiele podwójne interfejsy, musi istnieć tylko jeden `IDispatch` interfejsu widoczne. Metody dostępne upewnić się, że jest to przenoszenia kary, takich jak utraty funkcji lub złożoność zwiększona kodu. Developer, biorąc pod uwagę takie podejście dokładnie należy porównać zalety i wady.  
  
## <a name="exposing-a-single-idispatch-interface"></a>Udostępnianie jednego interfejsu IDispatch  
 Można udostępnić wielu podwójne interfejsy na pojedynczy obiekt wywodzące się z dwóch lub więcej specjalizacjach `IDispatchImpl`. Jednak jeśli Zezwalaj klientom na wykonanie kwerendy `IDispatch` interfejsu, należy użyć [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) makro (lub [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid))) do określenia, które klasy podstawowej dla Implementacja `IDispatch`.  
  
 [!code-cpp[NVC_ATL_COM#23](../atl/codesnippet/cpp/multiple-dual-interfaces_1.h)]  
  
 Ponieważ tylko jeden `IDispatch` interfejsu jest narażony, klientów, którzy mogą uzyskiwać dostęp tylko do obiektów za pomocą `IDispatch` interfejsu nie będzie można uzyskać dostępu do metody lub właściwości w inny interfejs.  
  
## <a name="combining-multiple-dual-interfaces-into-a-single-implementation-of-idispatch"></a>Łączenie wielu podwójne interfejsy w pojedynczej implementacji interfejsu IDispatch  
 ATL nie ma żadnych pomocy technicznej dla łączenie wielu podwójne interfejsy w pojedynczej implementacji właściwości `IDispatch`. Jednak jest kilka metod znane, aby ręcznie łączenie interfejsów, takich jak tworzenie szablonu klasy, która zawiera Unię szczegółowych `IDispatch` interfejsy tworzenia nowego obiektu w celu wykonania `QueryInterface` funkcji lub przy użyciu na podstawie informacji o typach wdrożenia zagnieżdżonych obiektów, aby utworzyć `IDispatch` interfejsu.  
  
 Te metody występują problemy z potencjalnych konfliktów nazw, a także kod złożoności i łatwości konserwacji. Nie zaleca się utworzenie wielu podwójne interfejsy.  
  
## <a name="see-also"></a>Zobacz też  
 [Podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md)

