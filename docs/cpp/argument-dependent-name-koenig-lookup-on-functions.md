---
title: "Odnośnik do nazwy zależnej od argumentu (Koenig) funkcji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- Koenig lookup
- argument-dependent lookup [C++]
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4a97e629276c104bfc9c81a9924a20e727949150
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="argument-dependent-name-koenig-lookup-on-functions"></a>Odnośnik do nazwy zależnej od argumentu (Koenig) funkcji
Kompilator umożliwia znalezienie definicji wywołanie funkcji niekwalifikowane nazwy zależnej od argumentu. Odnośnik do nazwy zależnej od argumentu jest również nazywany wyszukiwanie Koeniga. Typ każdy argument w wywołaniu funkcji jest zdefiniowany w ramach hierarchii z przestrzeni nazw, klasy, struktury, złożenia lub szablonów. Po określeniu niekwalifikowane [przyrostka](../cpp/postfix-expressions.md) wywołanie funkcji Kompilator szuka definicji funkcji w hierarchii skojarzone z każdym typem argumentu.  
  
## <a name="example"></a>Przykład  
 W przykładzie kompilator uwagi dotyczące tej funkcji `f()` przyjmuje argument `x`. Argument `x` jest typu `A::X`, który jest zdefiniowany w przestrzeni nazw `A`. Kompilator szuka przestrzeni nazw `A` i klient znajdzie definicji dla funkcji `f()` które przyjmuje argument typu `A::X`.  
  
```  
// argument_dependent_name_koenig_lookup_on_functions.cpp  
namespace A  
{  
   struct X  
   {  
   };  
   void f(const X&)  
   {  
   }  
}  
int main()  
{  
// The compiler finds A::f() in namespace A, which is where   
// the type of argument x is defined. The type of x is A::X.  
   A::X x;  
   f(x);     
}  
```  
