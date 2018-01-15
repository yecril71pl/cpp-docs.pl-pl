---
title: "is_pointer — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_pointer
dev_langs: C++
helpviewer_keywords:
- is_pointer class
- is_pointer
ms.assetid: 44e0a403-7241-4e0a-8922-32877bcb9a4c
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 32377754dcb8f8098ab1f74db8fb8d4d74b0c73c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ispointer-class"></a>is_pointer — Klasa
Testy, jeśli wskaźnik jest typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Ty>  
struct is_pointer;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `Ty` jest wskaźnikiem do `void`, wskaźnik do obiektu lub wskaźnik do funkcji lub a `cv-qualified` formularza jednego z nich, w przeciwnym razie posiada wartość false. Należy pamiętać, że `is_pointer` blokad wartość false, gdy `Ty` jest wskaźnik do elementu członkowskiego lub wskaźnika do funkcji członkowskiej.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// std__type_traits__is_pointer.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_pointer<trivial> == " << std::boolalpha   
        << std::is_pointer<trivial>::value << std::endl;   
    std::cout << "is_pointer<int trivial::*> == " << std::boolalpha   
        << std::is_pointer<int trivial::*>::value << std::endl;   
    std::cout << "is_pointer<trivial *> == " << std::boolalpha   
        << std::is_pointer<trivial *>::value << std::endl;   
    std::cout << "is_pointer<int> == " << std::boolalpha   
        << std::is_pointer<int>::value << std::endl;   
    std::cout << "is_pointer<int *> == " << std::boolalpha   
        << std::is_pointer<int *>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_pointer<trivial> == false  
is_pointer<int trivial::*> == false  
is_pointer<trivial *> == true  
is_pointer<int> == false  
is_pointer<int *> == true  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)   
 [is_member_pointer — klasa](../standard-library/is-member-pointer-class.md)   
 [is_reference, klasa](../standard-library/is-reference-class.md)
