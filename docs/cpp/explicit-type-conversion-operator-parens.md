---
title: 'Operator jawnej konwersji typu: () | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- explicit data type conversion operator
- conversions [C++], explicit
- operators [C++], explicit type conversion
- data type conversion [C++], explicit
- type conversion [C++], explicit conversions
ms.assetid: 54272006-5ffb-45ed-8283-27152ab97529
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 451901d595a91189fea1f8c1364ccd6cbd151a17
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043199"
---
# <a name="explicit-type-conversion-operator-"></a>Operator jawnej konwersji typu: ()

Język C++ pozwala na jawną konwersję typu przy użyciu składni podobnej do składni wywołania funkcji.

## <a name="syntax"></a>Składnia

```
simple-type-name ( expression-list )
```

## <a name="remarks"></a>Uwagi

A *simple-type-name* następuje *lista wyrażeń* ujęte w nawiasy konstrukcji obiektu określonego typu przy użyciu określonych wyrażeń. W poniższym przykładzie pokazano jawną konwersję typu na typ int.

```cpp
int i = int( d );
```

W poniższym przykładzie przedstawiono `Point` klasy.

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

Poprzedni przykład, który używa konwersji stylu funkcji, pokazuje, jak konwertować dwie wartości (jedną dla *x* i jeden dla *y*) do typu zdefiniowanego przez użytkownika `Point`.

> [!CAUTION]
>  Użyj jawnej konwersji typu z rozwagą, gdyż zastępuje ona kontrolę typów wbudowaną w kompilator C++.

[Rzutowania](../cpp/cast-operator-parens.md) notacji muszą być używane do konwersji na typy, które nie mają *simple-type-name* (typy wskaźnikowe lub odwołania, na przykład). Konwersja na typy, które mogą być wyrażone za pomocą *simple-type-name* może być zapisana w dowolnej postaci.

W ramach rzutowań niedozwolone są definicje typu.

## <a name="see-also"></a>Zobacz także

[Wyrażenia przyrostków](../cpp/postfix-expressions.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)