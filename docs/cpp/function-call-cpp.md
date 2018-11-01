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
ms.openlocfilehash: 0064b17f0adf5cadf732321fbb62403a1da5db76
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649153"
---
# <a name="function-call-c"></a>Wywołanie funkcji (C++)

Operator wywołania funkcji, wywoływane przy użyciu nawiasów jest operator binarny.

## <a name="syntax"></a>Składnia

```
primary-expression ( expression-list )
```

## <a name="remarks"></a>Uwagi

W tym kontekście `primary-expression` jest pierwszym operandem, a `expression-list`, może być pusta lista argumentów, to drugi operand. Operator wywołania funkcji jest używana w operacjach wymagających liczbą parametrów. To działa, ponieważ `expression-list` jest lista zamiast jeden argument operacji. Operator wywołania funkcji musi być funkcją niestatycznej składowej.

Operator wywołania funkcji, gdy przeciążona, nie powoduje modyfikacji, jak funkcje są wywoływane; przeciwnie modyfikuje, jak operator ma być interpretowany w przypadku zastosowania do obiektów typu danej klasy. Na przykład poniższy kod zazwyczaj może być nieistotna:

```cpp
Point pt;
pt( 3, 2 );
```

Biorąc pod uwagę odpowiednie wywołanie przeciążonej funkcji operatora, jednak ta składnia może służyć do przesunięcia `x` koordynować 3 jednostki i `y` koordynować 2 jednostki. Poniższy kod przedstawia definicję takie:

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

Należy pamiętać, że operator wywołania funkcji jest stosowany do nazwę obiektu, a nie nazwą funkcji.

Można także przeciążyć operator wywołania funkcji za pomocą wskaźnika do funkcji (a nie samej funkcji).

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

## <a name="see-also"></a>Zobacz także

[Przeładowanie operatora](../cpp/operator-overloading.md)