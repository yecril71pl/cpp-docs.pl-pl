---
title: Klasa is_assignable | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d616145aa0810a370d2a9c8f602fc578b28a661b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="isassignable-class"></a>is_assignable — klasa
Sprawdza, czy wartość `From` typu mogą być przypisane do `To` typu.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class To, class From>  
struct is_assignable;
```  
  
#### <a name="parameters"></a>Parametry  
 Do  
 Typ obiektu, który odbiera przypisania.  
  
 Z  
 Typ obiektu, który zawiera wartość.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie, którego nie obliczono `declval<To>() = declval<From>()` musi być poprawnie sformułowany. Zarówno `From` i `To` musi być ukończone typy `void`, lub tablic z nieznanym powiązaniem.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [<type_traits>](../standard-library/type-traits.md)



