---
title: "integral_constant — klasa, bool_constant klasy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::integral_constant
- XTR1COMMON/std::integral_constant
- type_traits/std::bool_constant
- XTR1COMMON/std::bool_constant
dev_langs: C++
helpviewer_keywords:
- std::integral_constant [C++]
- std::bool_constant [C++]
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d519e7310237a00e1423f70adea5fa0590ec5350
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="integralconstant-class-boolconstant-class"></a>integral_constant — klasa, bool_constant — klasa
Sprawia, że typem całkowitym stałej od typu i wartości.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T, T v>
struct integral_constant {  
   static constexpr T value = v;  
   typedef T value_type;  
   typedef integral_constant<T, v> type;  
   constexpr operator value_type() const noexcept;  
   constexpr value_type operator()() const noexcept;  
   };  
```
  
### <a name="parameters"></a>Parametry  
*T*  
Typ stałej.  
  
*v*  
Wartość stała.  
  
## <a name="remarks"></a>Uwagi  
`integral_constant` Klasy szablonu, gdy specjalizowany z typem całkowitym *T* i wartość *v* tego typu reprezentuje obiekt przechowujący stałą tego typu całkowitego na określoną wartość. Element członkowski o nazwie `type` jest aliasem typ wygenerowanego szablonu specjalizacji i `value` elementu członkowskiego zawiera wartość *v* pozwala utworzyć specjalizacji.  
  
`bool_constant` Jawna specjalizacja częściowa jest szablon klasy `integral_constant` używającą `bool` jako *T* argumentu.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// std__type_traits__integral_constant.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "integral_constant<int, 5> == "   
        << std::integral_constant<int, 5>::value << std::endl;   
    std::cout << "integral_constant<bool, false> == " << std::boolalpha   
        << std::integral_constant<bool, false>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
integral_constant<int, 5> == 5  
integral_constant<bool, false> == false  
```  
  
## <a name="requirements"></a>Wymagania  

**Nagłówek:** \<type_traits >
  
**Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)   
 [false_type](../standard-library/type-traits-typedefs.md#false_type)   
 [true_type](../standard-library/type-traits-typedefs.md#true_type)

