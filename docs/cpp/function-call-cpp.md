---
title: Wywołania funkcji (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function calls, C++ functions
- functions [C++], calling
- operator overloading [C++], function calls
- function overloading [C++], function-call operator
- function calls, operator
- operators [C++], overloading
- operator overloading [C++], examples
- function call operator ()
ms.assetid: 5094254a-045b-46f7-8653-69bc91e80dce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85e7a752630b391d09140fa7552a452b3d2b751a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="function-call-c"></a>Wywołanie funkcji (C++)
Operator wywołania funkcji, wywołana za pomocą nawiasów, jest operator binarny.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
primary-expression ( expression-list )  
```  
  
## <a name="remarks"></a>Uwagi  
 W tym kontekście `primary-expression` jest pierwszym argumentem i `expression-list`, prawdopodobnie pusta lista argumentów jest drugi argument operacji. Operator wywołania funkcji jest używana w operacjach wymagających liczbą parametrów. To działa, ponieważ `expression-list` jest listą zamiast jeden argument. Operator wywołania funkcji musi być niestatyczną funkcją członkowską.  
  
 Operator wywołania funkcji, gdy przeciążona, nie modyfikuje sposób funkcje są nazywane; zamiast modyfikuje jak operator jest interpretowane, gdy jest stosowany do obiektów klasy danego typu. Na przykład następujący kod będzie zazwyczaj znaczenia:  
  
```  
Point pt;  
pt( 3, 2 );  
```  
  
 Podana w operatorze odpowiednie wywołanie przeciążonej funkcji, jednak ta składnia może służyć do przesunięcia `x` koordynować 3 jednostki i `y` koordynować 2 jednostki. Poniższy kod przedstawia takie definicji:  
  
```  
// function_call.cpp  
class Point  
{  
public:  
    Point() { _x = _y = 0; }  
    Point &operator()( int dx, int dy )  
        { _x += dx; _y += dy; return *this; }  
private:  
    int _x, _y;  
};  
  
int main()  
{  
   Point pt;  
   pt( 3, 2 );  
}  
```  
  
 Uwaga zastosowana do nazwy obiektu, a nie nazwą funkcji operator wywołania funkcji.  
  
 Można także przeciążyć operator wywołania funkcji przy użyciu wskaźnika do funkcji (zamiast funkcji, sam).  
  
```cpp  
typedef void(*ptf)();  
void func()  
{  
}  
struct S  
{  
   operator ptf()  
   {  
      return func;  
   }  
};  
  
int main()  
{  
   S s;  
   s();//operates as s.operator ptf()()  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przeładowanie operatora](../cpp/operator-overloading.md)