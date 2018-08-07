---
title: HStringReference::Operator&lt; Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
dev_langs:
- C++
ms.assetid: 55aa48e8-7c96-4123-9ebe-42b4cd8b9377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 489d97252dcb4d20b7ef2f8557991a4e6016743d
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605535"
---
# <a name="hstringreferenceoperatorlt-operator"></a>HStringReference::Operator&lt; — Operator
Wskazuje, czy pierwszy parametr jest mniejszy od drugiego parametru.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
inline bool operator<(  
    const HStringReference& lhs,   
    const HStringReference& rhs) throw()  
```  
  
### <a name="parameters"></a>Parametry  
 *Lewa strona reguły przepisywania*  
 Pierwszy parametr do porównania. *Lewa strona reguły przepisywania* może być odwołaniem do **HStringReference**.  
  
 *RHS*  
 Drugi parametr do porównania.  *RHS* może być odwołaniem do **HStringReference**.  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli *lhs* parametr jest mniejsza niż *rhs* parametru; w przeciwnym razie **false**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [HStringReference, klasa](../windows/hstringreference-class.md)