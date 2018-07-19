---
title: Inkrementacja i dekrementacja przeciążania operatorów (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- increment operators [C++]
- increment operators [C++], types of
- decrement operators [C++]
- decrement operators [C++], types of
ms.assetid: 5423c6ce-3999-4a77-92f6-ad540add1b1d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3ed5cee9d3742410c4316b0eb8c3c80b2f41353
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37948235"
---
# <a name="increment-and-decrement-operator-overloading-c"></a>Przeładowanie operatorów inkrementacji i dekrementacji (C++)
Operatory inkrementacji i dekrementacji dzielą się na specjalnej kategorii, ponieważ istnieją dwa warianty każdego z nich:  
  
-   Operacja preinkrementacji i postincrement  
  
-   Operacja predekrementacji i postdecrement  
  
 Kiedy piszesz funkcje przeciążonego operatora, może być przydatne do zaimplementowania oddzielnych wersji dla prefiksu i przyrostkowe wersje tych operatorów. Aby rozróżnić dwa, następująca reguła zostanie wykryty: forma przedrostkowa operatora zadeklarowano dokładnie taki sam sposób jak inne operatora jednoargumentowego; przyrostkowej formy akceptuje dodatkowy argument typu **int**.  
  
> [!NOTE]
>  Podczas określania przeciążonego operatora formularza przyrostkowego operatora inkrementacji lub dekrementacji, dodatkowy argument musi być typu **int**; generuje błąd, określając innego typu.  
  
 Poniższy przykład pokazuje, jak zdefiniować prefiksu i zwiększenie przyrostkowe operatory dekrementacji `Point` klasy:  
  
```cpp  
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
  
 Ten sam operatorów można zdefiniować w zakresie pliku (globalnie) przy użyciu następujących głowic funkcji:  
  
```cpp  
friend Point& operator++( Point& )      // Prefix increment  
friend Point& operator++( Point&, int ) // Postfix increment  
friend Point& operator--( Point& )      // Prefix decrement  
friend Point& operator--( Point&, int ) // Postfix decrement  
```  
  
 Argument typu **int** oznacza, że przyrostkowej formy przyrost lub operatora dekrementacyjnego nie jest najczęściej używany do przekazywania argumentów. Zawiera on zazwyczaj wartość 0. Jednak może służyć w następujący sposób:  
  
```cpp  
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
  
 Nie ma składni do przy użyciu operatorów inkrementacji lub dekrementacji przekazać te wartości innych niż jawnego wywołania, jak pokazano w poprzednim kodzie. Bardziej bezpośredni sposób zaimplementowania tej funkcji jest przeciążyć operator dodawania/przypisania (`+=`).  
  
## <a name="see-also"></a>Zobacz też  
 [Przeładowanie operatora](../cpp/operator-overloading.md)