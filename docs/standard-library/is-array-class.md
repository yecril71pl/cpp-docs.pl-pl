---
title: "is_array — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_array
dev_langs: C++
helpviewer_keywords:
- is_array class
- is_array
ms.assetid: 61fb2201-8de3-4746-9721-617f02df170f
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c977cc6e963c7865a94272546ca135bd79fd5f17
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="isarray-class"></a>is_array — Klasa
Testy, jeśli typ tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Ty>  
struct is_array;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `Ty` jest typem tablicy, w przeciwnym razie posiada wartość false.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// std__type_traits__is_array.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_array<trivial> == " << std::boolalpha   
        << std::is_array<trivial>::value << std::endl;   
    std::cout << "is_array<int> == " << std::boolalpha   
        << std::is_array<int>::value << std::endl;   
    std::cout << "is_array<int[5]> == " << std::boolalpha   
        << std::is_array<int[5]>::value << std::endl;   
  
    return (0);   
    }  
```  
  
```Output  
is_array<trivial> == false  
is_array<int> == false  
is_array<int[5]> == true  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)   
 [Extent — klasa](../standard-library/extent-class.md)   
 [Rank — klasa](../standard-library/rank-class.md)
