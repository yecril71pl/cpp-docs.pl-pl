---
title: "is_nothrow_copy_assignable — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 37964edce6b8b6370302a29c76e80386e54ab5a4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="isnothrowcopyassignable-class"></a>is_nothrow_copy_assignable — klasa
Sprawdza, czy typ ma operatora przypisania kopii, znany do kompilatora nie throw.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>
struct is_nothrow_copy_assignable;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu jest spełniony dla typu referenceable `T` gdzie `is_nothrow_assignable<T&, const T&>` ma wartość PRAWDA; w przeciwnym razie posiada wartość false.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)   
 [is_nothrow_assignable, klasa](../standard-library/is-nothrow-assignable-class.md)   





