---
title: Wiele podwójnych interfejsów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ace347148f3a339c75fd9a1069be368c7373d351
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38952932"
---
# <a name="multiple-dual-interfaces"></a>Wiele podwójnych interfejsów
Możesz chcieć połączyć zalety podwójnego interfejsu (czyli elastyczność zarówno vtable, jak i późne powiązania, w związku z tym udostępnia klasy do języków skryptów, a także C++) za pomocą metod wielokrotnego dziedziczenia.  
  
 Chociaż jest to możliwe do udostępnienia wiele podwójnych interfejsów na pojedynczy obiekt COM, nie jest zalecane. Jeśli istnieje wiele podwójnych interfejsów, musi istnieć tylko jeden `IDispatch` interfejsu widoczne. Metody dostępne upewnić się, że jest to możliwe wykonania kary, takie jak utrata funkcji lub kod zwiększenia złożoności. Dla deweloperów, biorąc pod uwagę podejście to dokładnie porównać zalety i wady.  
  
## <a name="exposing-a-single-idispatch-interface"></a>Udostępnianie jednego interfejsu IDispatch  
 Można udostępnić wiele podwójnych interfejsów na pojedynczy obiekt z co najmniej dwóch specjalizacje `IDispatchImpl`. Jednak w przypadku zezwalania klientom na wykonanie kwerendy `IDispatch` interfejsu, należy użyć [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) — makro (lub [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid))) aby określić, która klasa bazowa dla Implementacja `IDispatch`.  
  
 [!code-cpp[NVC_ATL_COM#23](../atl/codesnippet/cpp/multiple-dual-interfaces_1.h)]  
  
 Ponieważ tylko jeden `IDispatch` interfejsu jest widoczna, klienci, którzy mają dostęp tylko do obiektów za pomocą `IDispatch` interfejsu nie będzie można uzyskać dostępu do metody lub właściwości w innym interfejsie.  
  
## <a name="combining-multiple-dual-interfaces-into-a-single-implementation-of-idispatch"></a>Łącząc wiele podwójnych interfejsów w pojedynczej implementacji interfejsu IDispatch  
 ATL nie świadczenia pomocy technicznej dla łącząc wiele podwójnych interfejsów w pojedynczej implementacji właściwości `IDispatch`. Istnieją różne techniki znanych ręcznie łączenie interfejsów, takich jak tworzenie oparte na szablonach klasę, która zawiera sumę oddzielne `IDispatch` interfejsów, utworzenie nowego obiektu do wykonania `QueryInterface` funkcji lub przy użyciu na podstawie informacji o typach wdrożenia obiekty zagnieżdżone, aby utworzyć `IDispatch` interfejsu.  
  
 Te metody występują problemy z potencjalnych konfliktów nazw, a także kod złożoności i łatwości konserwacji. Nie zaleca się, że utworzono wiele podwójnych interfejsów.  
  
## <a name="see-also"></a>Zobacz też  
 [Podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md)

