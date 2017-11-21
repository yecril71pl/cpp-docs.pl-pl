---
title: "CompareStringOrdinal — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
dev_langs: C++
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 17415efa6519d8e3538f869168db2040ed6e73dc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|-1|`lhs`jest mniejsza niż `rhs`.|  
|0|`lhs`Equals `rhs`.|  
|1|`lhs`jest większa niż `rhs`.|  
  
## <a name="remarks"></a>Uwagi  
 Porównuje dwa obiekty HSTRING określonego i zwraca liczbę całkowitą wskazującą ich względne położenie w kolejności sortowania.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace Microsoft::WRL::Wrappers::details](../windows/microsoft-wrl-wrappers-details-namespace.md)