---
title: "is_integral — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_integral
dev_langs: C++
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: de9db1c9ebf6e95670a36f44c9233458badd74c9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="isintegral-class"></a>is_integral — Klasa
Testy, jeśli typ jest integralną częścią.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Ty>  
struct is_integral;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `Ty` jest jednym z typów całkowitych lub `cv-qualified` postaci jednego z typów całkowitych, w przeciwnym razie posiada wartość false.  
  
 Typ całkowity jest jednym z `bool`, `char`, `unsigned char`, `signed char`, `wchar_t`, `short`, `unsigned short`, `int`, `unsigned int`, `long`, i `unsigned long`. Ponadto z kompilatorów, które zapewniają im typ całkowity może być jedną z `long long`, `unsigned long long`, `__int64`, i `unsigned __int64`.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// std__type_traits__is_integral.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_integral<trivial> == " << std::boolalpha   
        << std::is_integral<trivial>::value << std::endl;   
    std::cout << "is_integral<int> == " << std::boolalpha   
        << std::is_integral<int>::value << std::endl;   
    std::cout << "is_integral<float> == " << std::boolalpha   
        << std::is_integral<float>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_integral<trivial> == false  
is_integral<int> == true  
is_integral<float> == false  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)   
 [is_enum — klasa](../standard-library/is-enum-class.md)   
 [is_floating_point, klasa](../standard-library/is-floating-point-class.md)
