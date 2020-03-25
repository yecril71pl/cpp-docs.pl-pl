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
ms.openlocfilehash: 079a3390df56ba55bd4d71a320faa249266abb54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189016"
---
# <a name="explicit-type-conversion-operator-"></a>Operator jawnej konwersji typu: ()

Język C++ pozwala na jawną konwersję typu przy użyciu składni podobnej do składni wywołania funkcji.

## <a name="syntax"></a>Składnia

```
simple-type-name ( expression-list )
```

## <a name="remarks"></a>Uwagi

*Prosta nazwa typu* , po której następuje *Lista wyrażeń* ujęta w nawiasy, konstruuje obiekt określonego typu przy użyciu określonych wyrażeń. W poniższym przykładzie pokazano jawną konwersję typu na typ int.

```cpp
int i = int( d );
```

W poniższym przykładzie pokazano klasę `Point`.

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

Poprzedni przykład, który używa konwersji w stylu funkcji, pokazuje, w jaki sposób konwertować dwie wartości (jeden dla *x* i jeden dla *y*) do typu zdefiniowanego przez użytkownika `Point`.

> [!CAUTION]
>  Użyj jawnej konwersji typu z rozwagą, gdyż zastępuje ona kontrolę typów wbudowaną w kompilator C++.

Notacja [rzutowania](../cpp/cast-operator-parens.md) musi być używana w przypadku konwersji na typy, które nie mają *prostej nazwy typu* (na przykład wskaźników lub typów referencyjnych). Konwersja na typy, które mogą być wyrażone przy użyciu *prostej nazwy typu* , może być zapisana w dowolnej postaci.

W ramach rzutowań niedozwolone są definicje typu.

## <a name="see-also"></a>Zobacz też

[Wyrażenia przyrostków](../cpp/postfix-expressions.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
