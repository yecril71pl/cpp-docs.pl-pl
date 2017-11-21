---
title: Klasa is_nothrow_assignable | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: type_traits/std::is_nothrow_assignable
dev_langs: C++
helpviewer_keywords: is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5bc98560000cc0f12270a55547aa0ee082d312a7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="isnothrowassignable-class"></a>is_nothrow_assignable — klasa
Sprawdza, czy wartość `From` typu mogą być przypisane do `To` typu i przypisanie wiadomo, że nie throw.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class To, class From>  
struct is_nothrow_assignable;
```  
  
#### <a name="parameters"></a>Parametry  
 Do  
 Typ obiektu, który odbiera przypisania.  
  
 Z  
 Typ obiektu, który zawiera wartość.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie `declval<To>() = declval<From>()` musi być poprawnie sformułowany i musi być znane w kompilatorze nie throw. Zarówno `From` i `To` musi być ukończone typy `void`, lub tablic z nieznanym powiązaniem.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)



