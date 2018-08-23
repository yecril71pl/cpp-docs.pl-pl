---
title: MakeAllocator::Allocate, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
dev_langs:
- C++
helpviewer_keywords:
- Allocate method
ms.assetid: a01997bc-4ff1-4ed0-9def-e4aaa15b0598
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4422dea0b0bfb07904d0c4defad8f33281a51bec
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609865"
---
# <a name="makeallocatorallocate-method"></a>MakeAllocator::Allocate — Metoda

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
__forceinline void* Allocate();
```

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, wskaźnik do przydzielonego pamięci. w przeciwnym razie **nullptr**.

## <a name="remarks"></a>Uwagi

Przydziela pamięć i kojarzy ją z bieżącymi **MakeAllocator** obiektu.

Rozmiar alokacji pamięci jest rozmiar o typie określonym przez bieżącą **MakeAllocator** parametru szablonu.

Deweloper musi zastąpić tylko **Allocate()** metodę, aby wdrożyć model przydzielania pamięci różnych.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[MakeAllocator, klasa](../windows/makeallocator-class.md)  
[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)