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
ms.openlocfilehash: 06f8db4c713feb69e0037d10879383411ea07007
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606266"
---
# <a name="makeallocatorallocate-method"></a>MakeAllocator::Allocate — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [Makeallocator — klasa](../windows/makeallocator-class.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)