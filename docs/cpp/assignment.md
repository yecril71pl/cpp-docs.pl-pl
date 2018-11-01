---
title: Przypisanie
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
ms.openlocfilehash: 1e6d715011cfaab7e250e23a9a31bb3f0c83f36a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603442"
---
# <a name="assignment"></a>Przypisanie

Operator przypisania (**=**) jest ściśle rzecz ujmując, operatora binarnego. Jego deklaracji jest taka sama jak innych operatora binarnego, z następującymi wyjątkami:

- Musi być funkcją składową Niestatyczne. Nie **operator =** mogą być deklarowane jako funkcja niebędących.
- Nie jest dziedziczone przez klasy pochodne.
- Domyślnie **operator =** funkcji mogą być generowane przez kompilator dla typu klasy, jeśli żaden nie istnieje.

Poniższy przykład ilustruje sposób deklarowania operatora przypisania:

```cpp
class Point
{
public:
    int _x, _y;

    // Right side of copy assignment is the argument.
    Point& operator=(const Point&);
};

// Define copy assignment operator.
Point& Point::operator=(const Point& otherPoint)
{
    _x = otherPoint._x;
    _y = otherPoint._y;

    // Assignment operator returns left side of assignment.
    return *this;
}

int main()
{
    Point pt1, pt2;
    pt1 = pt2;
}
```

Podany argument to po prawej stronie wyrażenia. Operator zwraca obiekt, aby zachować zachowanie operator przypisania zwraca wartość po lewej stronie, po zakończeniu przydziału. Dzięki temu łańcucha przypisań, takich jak:

```cpp
pt1 = pt2 = pt3;
```

Operator przypisania kopiowania jest nie należy mylić z konstruktora kopiującego. Drugim jest wywoływana podczas tworzenia nowego obiektu z istniejącą grupę:

```cpp
// Copy constructor is called--not overloaded copy assignment operator!
Point pt3 = pt1;

// The previous initialization is similar to the following:
Point pt4(pt1); // Copy constructor call.
```

> [!NOTE]
> Zaleca się wykonać [reguły trzech](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)) , klasy, który definiuje operator przypisania kopiowania należy także jawnie zdefiniować Konstruktor kopiujący, destruktor, a, począwszy od C ++ 11, przejść Konstruktor i Przenieś przypisania operatora.

## <a name="see-also"></a>Zobacz także

- [Przeładowanie operatora](../cpp/operator-overloading.md)
- [Konstruktory kopiujące i kopiujące operatory przypisania (C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)