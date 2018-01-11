---
title: "Inkrementacja i dekrementacja przeciążania operatorów (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- increment operators [C++]
- increment operators [C++], types of
- decrement operators [C++]
- decrement operators [C++], types of
ms.assetid: 5423c6ce-3999-4a77-92f6-ad540add1b1d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 10987b351ebc34b7b17963e17047e32ee0d9bc5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="increment-and-decrement-operator-overloading-c"></a>Przeładowanie operatorów inkrementacji i dekrementacji (C++)
Operatory inkrementacji i dekrementacji należą do specjalnej kategorii, ponieważ istnieją dwie odmiany każdego:  
  
-   Preincrement i postincrement  
  
-   Predecrement i postdecrement  
  
 Podczas pisania funkcji Przeciążony operator może być przydatne do wdrożenia różne wersje prefiks i przyrostka wersje tych operatorów. Aby rozróżnić, zaobserwowano następującą regułę: forma przedrostkowa operatora zadeklarowano dokładnie taki sam sposób jak inne operatora jednoargumentowego; dodatkowy argument typu akceptuje przyrostkowej formy `int`.  
  
> [!NOTE]
>  Podczas określania Przeciążony operator formularza przyrostkowego operatora inkrementacji lub dekrementacji, dodatkowy argument musi być typu `int`; generuje błąd, określając innego typu.  
  
 Poniższy przykład przedstawia sposób określają prefiks przyrostka inkrementacji i dekrementacji operatory `Point` klasy:  
  
```  
// increment_and_decrement1.cpp  
class Point  
{  
public:  
   // Declare prefix and postfix increment operators.  
   Point& operator++();       // Prefix increment operator.  
   Point operator++(int);     // Postfix increment operator.  
  
   // Declare prefix and postfix decrement operators.  
   Point& operator--();       // Prefix decrement operator.  
   Point operator--(int);     // Postfix decrement operator.  
  
   // Define default constructor.  
   Point() { _x = _y = 0; }  
  
   // Define accessor functions.  
   int x() { return _x; }  
   int y() { return _y; }  
private:  
   int _x, _y;  
};  
  
// Define prefix increment operator.  
Point& Point::operator++()  
{  
   _x++;  
   _y++;  
   return *this;  
}  
  
// Define postfix increment operator.  
Point Point::operator++(int)  
{  
   Point temp = *this;  
   ++*this;  
   return temp;  
}  
  
// Define prefix decrement operator.  
Point& Point::operator--()  
{  
   _x--;  
   _y--;  
   return *this;  
}  
  
// Define postfix decrement operator.  
Point Point::operator--(int)  
{  
   Point temp = *this;  
   --*this;  
   return temp;  
}  
int main()  
{  
}  
```  
  
 Operatory tego samego można zdefiniować w zakresie pliku (globalny) przy użyciu następujących głowic funkcji:  
  
```  
friend Point& operator++( Point& )      // Prefix increment  
friend Point& operator++( Point&, int ) // Postfix increment  
friend Point& operator--( Point& )      // Prefix decrement  
friend Point& operator--( Point&, int ) // Postfix decrement  
```  
  
 Argument typu `int` oznacza, że przyrostkowej formy przyrost lub zmniejszenie operator nie jest często używana do przekazywanie argumentów. Zwykle zawiera wartość 0. Jednak może służyć w następujący sposób:  
  
```  
// increment_and_decrement2.cpp  
class Int  
{  
public:  
    Int &operator++( int n );  
private:  
    int _i;  
};  
  
Int& Int::operator++( int n )  
{  
    if( n != 0 )    // Handle case where an argument is passed.  
        _i += n;  
    else  
        _i++;       // Handle case where no argument is passed.  
    return *this;  
}  
int main()  
{  
   Int i;  
   i.operator++( 25 ); // Increment by 25.  
}  
```  
  
 Brak składnię przy użyciu operatorów inkrementacji lub dekrementacji przekazać te wartości innych niż jawnego wywołania, jak pokazano w poprzednim kodzie. Jest więcej łatwe do wykonania tej funkcji do przeciążenia operatora dodawania/przypisania (`+=`).  
  
## <a name="see-also"></a>Zobacz też  
 [Przeładowanie operatora](../cpp/operator-overloading.md)