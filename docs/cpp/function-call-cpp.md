---
title: Wywołanie funkcji (C++)
ms.date: 11/04/2016
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
ms.openlocfilehash: 6c7326b0f9c9592cb2b3be973a5ba1747a2015a0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179812"
---
# <a name="function-call-c"></a>Wywołanie funkcji (C++)

Operator wywołania funkcji wywoływany przy użyciu nawiasów, jest operatorem binarnym.

## <a name="syntax"></a>Składnia

```
primary-expression ( expression-list )
```

## <a name="remarks"></a>Uwagi

W tym kontekście `primary-expression` jest pierwszym operandem, a `expression-list`, prawdopodobnie pustą listą argumentów, jest drugim operandem. Operator wywołania funkcji jest używany dla operacji, które wymagają liczby parametrów. To działa, ponieważ `expression-list` jest listą zamiast jednego operandu. Operator wywołania funkcji musi być niestatyczną funkcją składową.

Operator wywołania funkcji, gdy przeciążony, nie modyfikuje sposobu wywołania funkcji; Zamiast tego modyfikuje sposób interpretowania operatora w przypadku zastosowania do obiektów danego typu klasy. Na przykład następujący kod zwykle będzie miał znaczenie:

```cpp
Point pt;
pt( 3, 2 );
```

Za pomocą odpowiedniego przeciążonego operatora wywołania funkcji można jednak użyć tej składni do przesunięcia `x` jednostek koordynacji 3 i `y` współrzędnych 2. Poniższy kod przedstawia takie definicje:

```cpp
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

Należy zauważyć, że operator wywołania funkcji jest stosowany do nazwy obiektu, a nie nazwy funkcji.

Można również przeciążać operator wywołania funkcji za pomocą wskaźnika do funkcji (a nie samej funkcji).

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
