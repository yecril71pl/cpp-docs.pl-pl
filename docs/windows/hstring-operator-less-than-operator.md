---
title: HString::Operator&lt; Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
dev_langs:
- C++
ms.assetid: 48a051cb-4609-42be-b48c-d35fc99d1eab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8fae7195f048cd680be513bd54b635e2e1e9bbf7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875113"
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
 Pierwszy parametr do porównania. `lhs` może być odwołaniem do HString.  
  
 `rhs`  
 Drugi parametr do porównania. `rhs` może być odwołaniem do HString.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli `lhs` parametr jest mniejsza niż `rhs` parametru; w przeciwnym razie `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [HString, klasa](../windows/hstring-class.md)