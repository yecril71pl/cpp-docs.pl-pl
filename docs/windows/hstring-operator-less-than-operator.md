---
title: HString::Operator&lt; Operator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HString::operator<
dev_langs: C++
ms.assetid: 48a051cb-4609-42be-b48c-d35fc99d1eab
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4cbb21e34255d5350702d949792656bdf0a849a8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="hstringoperatorlt-operator"></a>HString::Operator&lt; — Operator
Wskazuje, czy pierwszy parametr jest mniejszy od drugiego parametru.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
inline bool operator<(  
    const HString& lhs,   
    const HString& rhs) throw()  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `lhs`  
 Pierwszy parametr do porównania. `lhs`może być odwołaniem do HString.  
  
 `rhs`  
 Drugi parametr do porównania. `rhs`może być odwołaniem do HString.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli `lhs` parametr jest mniejsza niż `rhs` parametru; w przeciwnym razie `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [HString, klasa](../windows/hstring-class.md)