---
title: "remove_all_extents — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::remove_all_extents
dev_langs:
- C++
helpviewer_keywords:
- remove_all_extents class
- remove_all_extents
ms.assetid: 548dc536-82e7-423a-b8c1-443d66d9632e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d527deeeaea38bb57d9edf32d7325b1684ea8a5c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="removeallextents-class"></a>remove_all_extents — Klasa
Tworzy typ inny niż tablica z typu tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>
struct remove_all_extents;

template <class T>  
using remove_all_extents_t = typename remove_all_extents<T>::type;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ do modyfikacji.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie `remove_all_extents<T>` przechowuje zmodyfikowane — typ danych typu elementu typu tablicy `T` z usunięte, wszystkie wymiary tablicy lub `T` Jeśli `T` nie jest typem tablicy.  
  
## <a name="example"></a>Przykład  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "remove_all_extents<int> == "   
        << typeid(std::remove_all_extents_t<int>).name()   
        << std::endl;   
    std::cout << "remove_all_extents_t<int[5]> == "   
        << typeid(std::remove_all_extents_t<int[5]>).name()   
        << std::endl;   
    std::cout << "remove_all_extents_t<int[5][10]> == "   
        << typeid(std::remove_all_extents_t<int[5][10]>).name()   
        << std::endl;   
  
    return (0);   
    }  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)   
 [remove_extent, klasa](../standard-library/remove-extent-class.md)
