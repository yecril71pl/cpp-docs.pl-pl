---
title: "is_member_object_pointer — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_member_object_pointer
dev_langs: C++
helpviewer_keywords:
- is_member_object_pointer class
- is_member_object_pointer
ms.assetid: 64f9cdf3-4621-4310-a076-a7bc986926b9
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: abd7a37c32a2def953f376a28de6c561cea55fee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ismemberobjectpointer-class"></a>is_member_object_pointer — Klasa
Testy, jeśli typ jest wskaźnik do obiektu elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Ty>  
struct is_member_object_pointer;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `Ty` wskaźnik do obiektu elementu członkowskiego lub `cv-qualified` wskaźnika do elementu członkowskiego obiektu, w przeciwnym razie posiada wartość false. Należy pamiętać, że `is_member_object_pointer` blokad wartość false, gdy `Ty` wskaźnik do funkcji członkowskiej.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// std__type_traits__is_member_object_pointer.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
struct functional   
    {   
    int f();   
    };   
  
int main()   
    {   
    std::cout << "is_member_object_pointer<trivial *> == "   
        << std::boolalpha   
        << std::is_member_object_pointer<trivial *>::value   
        << std::endl;   
    std::cout << "is_member_object_pointer<int trivial::*> == "   
        << std::boolalpha   
        << std::is_member_object_pointer<int trivial::*>::value   
        << std::endl;   
    std::cout << "is_member_object_pointer<int (functional::*)()> == "   
        << std::boolalpha   
        << std::is_member_object_pointer<int (functional::*)()>::value   
        << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_member_object_pointer<trivial *> == false  
is_member_object_pointer<int trivial::*> == true  
is_member_object_pointer<int (functional::*)()> == false  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)   
 [is_member_pointer, klasa](../standard-library/is-member-pointer-class.md)
