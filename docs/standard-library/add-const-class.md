---
title: "add_const — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::add_const
dev_langs: C++
helpviewer_keywords:
- add_const class
- add_const
ms.assetid: 1262a1eb-8c9c-4dd6-9f43-88ba280182f1
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d0f4baf1e9cb6a740cddc0739bb13b35e6a0a684
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="addconst-class"></a>add_const — Klasa
Sprawia, że stała typu z typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Ty>  
struct add_const;
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ do modyfikacji.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie modyfikator typu przechowuje zmodyfikowane — typ danych `Ty` Jeśli `Ty` jest odwołanie, funkcji lub kwalifikowanego typu const, w przeciwnym razie `const Ty`.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// std__type_traits__add_const.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
{   
    std::add_const<int>::type *p = (const int *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "add_const<int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
add_const<int> == int  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)   
 [remove_const — klasa](../standard-library/remove-const-class.md)
