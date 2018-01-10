---
title: "C4868 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft"
ms.date: 10/26/2017
ms.topic: error-reference
f1_keywords: C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 261e826043a4f922902de91573a16707897ae6b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4868"></a>Kompilator C4868 ostrzegawcze (poziom 4)

> "_pliku_(*line_number*)" kompilator może nie wymusić kolejności oceny od lewej do prawej na liście inicjatora w nawiasach klamrowych

Elementy listy inicjalizatora w nawiasach klamrowych zostaną ocenione w kolejności od lewej do prawej. Istnieją dwa przypadki, w których kompilator nie może zagwarantować następującej kolejności: jest pierwsza w przypadku niektórych elementów obiektów przekazany przez wartość; drugim jest podczas kompilowania przy użyciu `/clr` i niektóre elementy są pola obiektów lub elementów tablicy. Gdy kompilator nie może zagwarantować oceny od lewej do prawej emituje ostrzeżenie C4868.

To ostrzeżenie można wygenerować wyniku pracy zgodność kompilatora, która została wykonana dla programu Visual C++ 2015 Update 2. Kod, który skompilowany przed Visual C++ 2015 Update 2 może teraz wygenerować C4868.

To ostrzeżenie jest domyślnie wyłączone. Użyj `/Wall` Aby uaktywnić to ostrzeżenie.

Aby usunąć to ostrzeżenie, najpierw należy wziąć pod uwagę czy niezbędne, np. podczas obliczania elementów może powodować generowanie efekty uboczne zależne od kolejności oceny od lewej do prawej elementów listy inicjatorów. W wielu przypadkach kolejności, w jakiej są oceniane elementów nie ma efektu zauważalne.

Jeśli kolejność obliczania musi mieć od lewej do prawej, weź pod uwagę, jeśli istnieje możliwość przekazywania elementów `const` zamiast tego odwołania. Zmiany, takie jak to eliminuje ostrzeżenie w poniższym przykładzie kodu.

## <a name="example"></a>Przykład

W tym przykładzie generuje C4868 i przedstawia sposób, aby go rozwiązać:

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