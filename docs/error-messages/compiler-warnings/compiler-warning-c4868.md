---
title: Ostrzeżenie kompilatora C4868
ms.date: 10/26/2017
f1_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
ms.openlocfilehash: d0bc8716e53e71c52f6a31036a95d0b4cefedd79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481320"
---
# <a name="compiler-warning-level-4-c4868"></a>Ostrzeżenie (poziom 4) kompilatora C4868

> "_pliku_(*line_number*)" kompilator może nie wymusić kolejności oceny od lewej do prawej na liście inicjatora w nawiasach klamrowych

Elementy listy inicjatora w nawiasach klamrowych mają być obliczane w kolejności od lewej do prawej. Istnieją dwa przypadki, w których kompilator nie może zagwarantować to zamówienie: pierwszy to umieszczenie niektóre elementy są przekazywane przez wartość; obiekty drugi to podczas kompilowania za pomocą `/clr` i niektóre elementy są pola obiektów lub elementów tablicy. Gdy kompilator nie może zagwarantować oceny od lewej do prawej emituje ostrzeżenie C4868.

To ostrzeżenie, mogą być generowane w wyniku pracy zgodności kompilatora, która została wykonana dla Visual C++ 2015 Update 2. Kod, który jest skompilowany przed Visual C++ 2015 Update 2 można teraz wygenerować C4868.

To ostrzeżenie jest domyślnie wyłączona. Użyj `/Wall` można aktywować tego ostrzeżenia.

Aby rozwiązać tego ostrzeżenia, najpierw należy wziąć pod uwagę czy oceny od lewej do prawej elementów listy inicjatorów są niezbędne, np. podczas oceny elementów może powodować generowanie efekty uboczne zależnych od kolejności. W wielu przypadkach kolejność, w jakiej są oceniane elementów nie ma efektu zauważalne.

Jeśli kolejność obliczania musi mieć od lewej do prawej, weź pod uwagę, jeśli istnieje możliwość przekazywania elementów `const` zamiast tego odwołania. Zmiany, takie jak ta eliminuje ostrzeżenie w następującym przykładzie kodu.

## <a name="example"></a>Przykład

Ten przykład generuje C4868 i pokazuje sposób, aby rozwiązać ten problem:

```cpp
// C4868.cpp
// compile with: /c /Wall
#include <cstdio>

class HasCopyConstructor
{
public:
    int x;

    HasCopyConstructor(int x): x(x) {}

    HasCopyConstructor(const HasCopyConstructor& h): x(h.x)
    {
        printf("Constructing %d\n", h.x);
    }
};

class TripWarning4868
{
public:
    // note that taking "HasCopyConstructor" parameters by-value will trigger copy-construction.
    TripWarning4868(HasCopyConstructor a, HasCopyConstructor b) {}

    // This variation will not trigger the warning:
    // TripWarning4868(const HasCopyConstructor& a, const HasCopyConstructor& b) {}
};

int main()
{
    HasCopyConstructor a{1};
    HasCopyConstructor b{2};

    // the warning will indicate the below line, the usage of the braced initializer list.
    TripWarning4868 warningOnThisLine{a, b};
};
```