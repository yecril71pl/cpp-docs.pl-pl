---
title: MakeAllocator::Detach — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: 78012634-2dda-4ea2-9ffe-40f105d2fe47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 50afca04492c29aa526f7a004c6e0f725022e9ba
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="makeallocatordetach-method"></a>MakeAllocator::Detach — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
__forceinline void Detach();  
```  
  
## <a name="remarks"></a>Uwagi  
 Usuwa skojarzenia pamięci przydzielonej przez [przydziel](../windows/makeallocator-allocate-method.md) metody z bieżącego obiektu makeallocator —.  
  
 Jeśli wywołujesz Detach() jest odpowiedzialny za usuwanie udostępniane przez metodę przydziel pamięć.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Makeallocator — klasa](../windows/makeallocator-class.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)