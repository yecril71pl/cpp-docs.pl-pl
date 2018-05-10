---
title: CompareStringOrdinal — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
dev_langs:
- C++
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e3abf87340671d1ac4851b055a57896e340d0c20
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
inline INT32 CompareStringOrdinal(  
   HSTRING lhs,   
   HSTRING rhs)  
```  
  
#### <a name="parameters"></a>Parametry  
 `lhs`  
 Pierwszy HSTRING do porównania.  
  
 `rhs`  
 Drugi HSTRING do porównania.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|Wartość|Warunek|  
|-----------|---------------|  
|-1|`lhs` jest mniejsza niż `rhs`.|  
|0|`lhs` Equals `rhs`.|  
|1|`lhs` jest większa niż `rhs`.|  
  
## <a name="remarks"></a>Uwagi  
 Porównuje dwa obiekty HSTRING określonego i zwraca liczbę całkowitą wskazującą ich względne położenie w kolejności sortowania.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers::Details, przestrzeń nazw](../windows/microsoft-wrl-wrappers-details-namespace.md)