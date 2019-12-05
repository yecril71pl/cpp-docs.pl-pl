---
title: Ostrzeżenie kompilatora C4868
ms.date: 10/26/2017
f1_keywords:
- C4868
helpviewer_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
ms.openlocfilehash: c1d49eb61a5c7c47fa83dacb39ed50f42e0fb147
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810481"
---
# <a name="compiler-warning-level-4-c4868"></a>Ostrzeżenie kompilatora (poziom 4) C4868

> Kompilator "_File_(*line_number*)" nie może wymusić kolejności oceny od lewej do prawej na liście inicjalizatora w nawiasach klamrowych

Elementy listy inicjalizatora w nawiasach klamrowych są oceniane w kolejności od lewej do prawej. Istnieją dwa przypadki, w których kompilator nie może zagwarantowania tej kolejności: pierwszy to, gdy niektóre elementy są obiektami przekazaną przez wartość; druga jest podczas kompilowania z `/clr`, a niektóre elementy są polami obiektów lub są elementami tablicy. Gdy kompilator nie może zagwarantować oceny od lewej do prawej, emituje ostrzeżenie C4868.

To ostrzeżenie może być generowane w wyniku działania kompilatora, który został wykonany dla programu Visual Studio 2015 Update 2. Kod, który został skompilowany przed Visual Studio 2015 Update 2, może teraz generować C4868.

To ostrzeżenie jest domyślnie wyłączone. Użyj `/Wall`, aby aktywować to ostrzeżenie.

Aby rozwiązać ten problem, należy najpierw rozważyć, czy konieczne jest oszacowanie wartości z listy inicjatorów od lewej do prawej, na przykład wtedy, gdy oceny elementów mogą generować efekty uboczne zależne od kolejności. W wielu przypadkach kolejność, w której elementy są oceniane, nie ma zauważalnego efektu.

Jeśli kolejność obliczeń musi być od lewej do prawej, należy rozważyć, czy można przekazać elementy przez `const` odwołanie. Zmiana taka, jak eliminuje to ostrzeżenie, w poniższym przykładzie kodu.

## <a name="example"></a>Przykład

Ten przykład generuje C4868 i przedstawia sposób jego rozwiązania:

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