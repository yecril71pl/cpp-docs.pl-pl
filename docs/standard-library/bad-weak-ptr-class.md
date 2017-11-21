---
title: "bad_weak_ptr — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: memory/std::bad_weak_ptr
dev_langs: C++
helpviewer_keywords:
- bad_weak_ptr
- bad_weak_ptr class
ms.assetid: a09336d5-7237-4480-ab6b-3787e0e6025e
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5cd4d1b82b4736b49c476d2f336a4b03db27bd51
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="badweakptr-class"></a>bad_weak_ptr — Klasa
Zgłasza zły wyjątek weak_ptr.  
  
## <a name="syntax"></a>Składnia  
  
```  
class bad_weak_ptr : public std::exception 
 {  
public:  
    bad_weak_ptr();
    const char *what() throw();
 };  
```  
  
## <a name="remarks"></a>Uwagi  
 Klasa opisuje wyjątek, który może zostać wygenerowany z [shared_ptr — klasa](../standard-library/shared-ptr-class.md) konstruktora, który przyjmuje argument typu [weak_ptr — klasa](../standard-library/weak-ptr-class.md). Funkcja członkowska `what` zwraca `"bad_weak_ptr"`.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// std__memory__bad_weak_ptr.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
 
int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int);
        wp = sp;
    }

    try
    {
        std::shared_ptr<int> sp1(wp); // weak_ptr has expired   
    }
    catch (const std::bad_weak_ptr&)
    {
        std::cout << "bad weak pointer" << std::endl;
    }
    catch (...)
    {
        std::cout << "unknown exception" << std::endl;
    }

    return (0);
}
```  
  
```Output  
bad weak pointer  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<pamięci >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [weak_ptr — klasa](../standard-library/weak-ptr-class.md)
