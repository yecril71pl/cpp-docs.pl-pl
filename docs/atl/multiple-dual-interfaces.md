---
title: Wiele podwójnych interfejsów
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- multiple dual interfaces
- COM_INTERFACE_ENTRY2 macro
- dual interfaces, exposing multiple
- multiple dual interfaces, exposing with ATL
- IDispatchImpl class, multiple dual interfaces
- COM_INTERFACE_ENTRY_IID macro
ms.assetid: 7fea86e6-247f-4063-be6e-85588a9e3719
ms.openlocfilehash: 2ed0e9e8c74e02917e852b8f95ebff1b048afaef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261582"
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

## <a name="see-also"></a>Zobacz także

[Podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md)
