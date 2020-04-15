---
title: 'Operator jawnej konwersji typu: ()'
ms.date: 11/04/2016
helpviewer_keywords:
- explicit data type conversion operator
- conversions [C++], explicit
- operators [C++], explicit type conversion
- data type conversion [C++], explicit
- type conversion [C++], explicit conversions
ms.assetid: 54272006-5ffb-45ed-8283-27152ab97529
ms.openlocfilehash: c168653a82b4d4c5023de1f76a1e6269625c74d8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354861"
---
# <a name="explicit-type-conversion-operator-"></a>Operator jawnej konwersji typu: ()

Język C++ pozwala na jawną konwersję typu przy użyciu składni podobnej do składni wywołania funkcji.

## <a name="syntax"></a>Składnia

```
simple-type-name ( expression-list )
```

## <a name="remarks"></a>Uwagi

Prosta *nazwa typu,* po której następuje *lista wyrażeń* ujęta w nawiasy, tworzy obiekt określonego typu przy użyciu określonych wyrażeń. W poniższym przykładzie pokazano jawną konwersję typu na typ int.

```cpp
int i = int( d );
```

Poniższy przykład `Point` pokazuje klasę.

## <a name="example"></a>Przykład

```cpp
// expre_Explicit_Type_Conversion_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class Point
{
public:
    // Define default constructor.
    Point() { _x = _y = 0; }
    // Define another constructor.
    Point( int X, int Y ) { _x = X; _y = Y; }

    // Define "accessor" functions as
    // reference types.
    unsigned& x() { return _x; }
    unsigned& y() { return _y; }
    void Show()   { cout << "x = " << _x << ", "
                         << "y = " << _y << "\n"; }
private:
    unsigned _x;
    unsigned _y;
};

int main()
{
    Point Point1, Point2;

    // Assign Point1 the explicit conversion
    //  of ( 10, 10 ).
    Point1 = Point( 10, 10 );

    // Use x() as an l-value by assigning an explicit
    //  conversion of 20 to type unsigned.
    Point1.x() = unsigned( 20 );
    Point1.Show();

    // Assign Point2 the default Point object.
    Point2 = Point();
    Point2.Show();
}
```

## <a name="output"></a>Dane wyjściowe

```Output
x = 20, y = 10
x = 0, y = 0
```

Mimo że w poprzednim przykładzie zademonstrowano jawną konwersję typu przy użyciu stałych, ta sama technika działa przy wykonywaniu konwersji na obiektach. Potwierdza to następujący fragment kodu:

```cpp
int i = 7;
float d;

d = float( i );
```

Jawne konwersje typu mogą być również określone przy użyciu składni „rzutowania”. Poprzedni przykład przepisany przy użyciu składni rzutowania:

```cpp
d = (float)i;
```

Zarówno rzutowanie, jak i konwersje w stylu funkcji, dają te same wyniki podczas konwertowania z pojedynczych wartości. Jednakże, w składni stylu funkcji można określić więcej niż jeden argument do konwersji. Różnica jest ważna dla typów zdefiniowanych przez użytkownika. Rozważ klasę `Point` i jej konwersje:

```cpp
struct Point
{
    Point( short x, short y ) { _x = x; _y = y; }
    ...
    short _x, _y;
};
...
Point pt = Point( 3, 10 );
```

W poprzednim przykładzie, który używa konwersji w stylu funkcji, pokazano, jak przekonwertować dwie wartości `Point`(jedną dla *x* i jedną dla *y)* na typ zdefiniowany przez użytkownika.

> [!CAUTION]
> Użyj jawnej konwersji typu z rozwagą, gdyż zastępuje ona kontrolę typów wbudowaną w kompilator C++.

Notacja [rzutowania](../cpp/cast-operator-parens.md) musi być używana w przypadku konwersji do typów, które nie mają *prostej nazwy typu* (na przykład typy wskaźników lub odwołań). Konwersja do typów, które mogą być wyrażone za pomocą *nazwy typu prostego* można zapisać w każdej formie.

W ramach rzutowań niedozwolone są definicje typu.

## <a name="see-also"></a>Zobacz też

[Wyrażenia poprawek](../cpp/postfix-expressions.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
