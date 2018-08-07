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
ms.openlocfilehash: de7ffb304a8b2f1567ed5510c276c454903ec930
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608407"
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
 *Lewa strona reguły przepisywania*  
 Pierwszy parametr do porównania. *Lewa strona reguły przepisywania* może być odwołaniem do **HString**.  
  
 *RHS*  
 Drugi parametr do porównania. *RHS* może być odwołaniem do **HString**.  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli *lhs* parametr jest mniejsza niż *rhs* parametru; w przeciwnym razie **false**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [HString, klasa](../windows/hstring-class.md)