---
title: Klasa is_trivially_assignable | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: type_traits/std::is_trivially_assignable
dev_langs: C++
helpviewer_keywords: is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4d40adc84ae8e2a9bb8f53e78d3a90dda99fd7e8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="istriviallyassignable-class"></a>is_trivially_assignable — klasa
Sprawdza, czy wartość `From` typu mogą być trivially przypisane do `To` typu  
  
## <a name="syntax"></a>Składnia  
  
```
template <class To, class From>  
struct is_trivially_assignable;
```  
  
#### <a name="parameters"></a>Parametry  
 Do  
 Typ obiektu, który odbiera przypisania.  
  
 Z  
 Typ obiektu, który zawiera wartość.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie `declval<To>() = declval<From>()` musi być poprawnie sformułowany, a musi być znane w kompilatorze wymagające ma nieuproszczone operacji. Zarówno `From` i `To` musi być ukończone typy `void`, lub tablic z nieznanym powiązaniem.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)



