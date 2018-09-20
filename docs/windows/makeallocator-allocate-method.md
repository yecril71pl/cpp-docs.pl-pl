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
ms.openlocfilehash: c4dd68a3c678b7877db63167fd2c0d48a1daa7ad
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411836"
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

[MakeAllocator, klasa](../windows/makeallocator-class.md)<br/>
[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)