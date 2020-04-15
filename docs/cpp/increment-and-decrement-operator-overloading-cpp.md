---
title: Przeładowanie operatorów inkrementacji i dekrementacji (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators [C++]
- increment operators [C++], types of
- decrement operators [C++]
- decrement operators [C++], types of
ms.assetid: 5423c6ce-3999-4a77-92f6-ad540add1b1d
ms.openlocfilehash: 40ae12130fdced9fd958c3b8316fa3b718ca9b5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374128"
---
# <a name="increment-and-decrement-operator-overloading-c"></a>Przeładowanie operatorów inkrementacji i dekrementacji (C++)

Operatory przyrostu i dekrementacji należą do kategorii specjalnej, ponieważ istnieją dwa warianty każdego z nich:

- Przyrost wstępny i postincrement

- Predecrement i postdecrement

Podczas pisania przeciążonych funkcji operatora, może być przydatne do zaimplementowania oddzielnych wersji dla wersji prefiksu i postfix tych operatorów. Aby odróżnić te dwa, przestrzegana jest następująca reguła: Formularz prefiksu operatora jest zadeklarowany dokładnie w taki sam sposób, jak każdy inny operator jednoobrzętowy; formularz postfix akceptuje dodatkowy argument typu **int**.

> [!NOTE]
> Podczas określania przeciążony operator dla formularza postfix operatora przyrostu lub dekrementacji, dodatkowy argument musi być typu **int;** określenie dowolnego innego typu generuje błąd.

W poniższym przykładzie pokazano, jak zdefiniować operatory prefiksu i przyrostu poprawek i dekrementacji dla `Point` klasy:

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

Te same operatory można zdefiniować w zakresie plików (globalnie) przy użyciu następujących głowic funkcji:

```cpp
friend Point& operator++( Point& )      // Prefix increment
friend Point& operator++( Point&, int ) // Postfix increment
friend Point& operator--( Point& )      // Prefix decrement
friend Point& operator--( Point&, int ) // Postfix decrement
```

Argument typu **int,** który oznacza formę postfix operatora przyrostu lub dekrementacji nie jest powszechnie używany do przekazywania argumentów. Zwykle zawiera wartość 0. Jednakże, może być stosowany w następujący sposób:

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

Nie ma składni przy użyciu operatorów przyrostu lub dekrementacji do przekazywania tych wartości innych niż jawne wywołanie, jak pokazano w poprzednim kodzie. Prostszym sposobem zaimplementowania tej funkcji jest przeciążenie operatora dodawania/przypisania (**+=**).

## <a name="see-also"></a>Zobacz też

[Przeciążenie operatora](../cpp/operator-overloading.md)
