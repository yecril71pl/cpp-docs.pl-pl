---
title: Klasa is_destructible | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: type_traits/std::is_destructible
dev_langs: C++
helpviewer_keywords: is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1b673ae9c46479723684a22205853229f913573d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="isdestructible-class"></a>is_destructible — klasa
Sprawdza, czy typ jest które można zniszczyć.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
struct is_destructible;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `T` jest które można zniszczyć typu, w przeciwnym razie posiada wartość false. Które można zniszczyć typy typów referencyjnych, typy i typów obiektów gdzie dla niektórych typów `U` równa `remove_all_extents_t<T>` nieobliczonym argument `std::declval<U&>.~U()` jest poprawnie sformułowany. Innych typów, w tym niekompletne typy `void`i typy funkcji, które można zniszczyć typy nie są.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)



