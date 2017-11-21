---
title: "&lt;funkcjonalności&gt; operatory | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- functional/std::operator!=
- functional/std::operator==
dev_langs: C++
helpviewer_keywords: functional operators
ms.assetid: d4b3c760-f3e2-4b65-bdaa-d42e8dd6f5e1
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0c165950500982698fc2ae631cae8e305ec5322a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltfunctionalgt-operators"></a>&lt;funkcjonalności&gt; operatory
|||  
|-|-|  
|[operator! =](#op_neq)|[operator ==](#op_eq_eq)|  
  
##  <a name="op_eq_eq"></a>operator ==  
 Testy, jeśli można wywołać obiektu jest pusta.  
  
```  
template <class Fty>  
bool operator==(const function<Fty>& f, null_ptr_type npc);

template <class Fty>  
bool operator==(null_ptr_type npc, const function<Fty>& f);
```  
  
### <a name="parameters"></a>Parametry  
 `Fty`  
 Typ funkcji do zakodowania.  
  
 `f`  
 Obiekt funkcji  
  
 `npc`  
 Wskaźnika o wartości null.  
  
### <a name="remarks"></a>Uwagi  
 Operatory zarówno zająć argument, który jest odwołaniem do `function` obiektu, a argument jest stałą pustego wskaźnika. Zwrócą wartość true tylko wtedy, gdy `function` obiekt jest pusty.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__functional__operator_eq.cpp
// compile with: /EHsc   
#include <functional>   
#include <iostream>   

int neg(int val)
{
    return (-val);
}

int main()
{
    std::function<int(int)> fn0;
    std::cout << std::boolalpha << "empty == "
        << (fn0 == 0) << std::endl;

    std::function<int(int)> fn1(neg);
    std::cout << std::boolalpha << "empty == "
        << (fn1 == 0) << std::endl;

    return (0);
}
  
```  
  
```Output  
empty == true  
empty == false  
```  
  
##  <a name="op_neq"></a>operator! =  
 Testy, jeśli można wywołać obiektu nie jest pusty.  
  
```  
template <class Fty>  
bool operator!=(const function<Fty>& f, null_ptr_type npc);

template <class Fty>  
bool operator!=(null_ptr_type npc, const function<Fty>& f);
```  
  
### <a name="parameters"></a>Parametry  
 `Fty`  
 Typ funkcji do zakodowania.  
  
 `f`  
 Obiekt funkcji  
  
 `npc`  
 Wskaźnika o wartości null.  
  
### <a name="remarks"></a>Uwagi  
 Operatory zarówno zająć argument, który jest odwołaniem do `function` obiektu, a argument jest stałą pustego wskaźnika. Zwrócą wartość true tylko wtedy, gdy `function` obiektu nie jest pusty.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__functional__operator_ne.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val)   
    {   
    return (-val);   
    }   
  
int main()   
    {   
    std::function<int (int)> fn0;   
    std::cout << std::boolalpha << "not empty == "   
        << (fn0 != 0) << std::endl;   
  
    std::function<int (int)> fn1(neg);   
    std::cout << std::boolalpha << "not empty == "   
        << (fn1 != 0) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
not empty == false  
not empty == true  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<funkcjonalności >](../standard-library/functional.md)

