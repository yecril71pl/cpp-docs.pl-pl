---
title: Delegowanie konstruktorówC++()
description: Używaj konstruktorów delegowania C++ w programie, aby wywoływać inne konstruktory i ograniczyć powtarzanie kodu.
ms.date: 11/19/2019
ms.openlocfilehash: 533cdfbeb882f3770cc554b0633611a4ffc2cfbd
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74250675"
---
# <a name="delegating-constructors"></a>Delegowanie konstruktorów

Wiele klas ma wiele konstruktorów, które wykonują podobne czynności — na przykład weryfikują parametry:

```cpp
class class_c {
public:
    int max;
    int min;
    int middle;

    class_c() {}
    class_c(int my_max) {
        max = my_max > 0 ? my_max : 10;
    }
    class_c(int my_max, int my_min) {
        max = my_max > 0 ? my_max : 10;
        min = my_min > 0 && my_min < max ? my_min : 1;
    }
    class_c(int my_max, int my_min, int my_middle) {
        max = my_max > 0 ? my_max : 10;
        min = my_min > 0 && my_min < max ? my_min : 1;
        middle = my_middle < max && my_middle > min ? my_middle : 5;
    }
};
```

Można zmniejszyć powtarzający się kod, dodając funkcję, która wykonuje wszystkie walidacje, ale kod dla `class_c` byłby łatwiejszy do zrozumienia i utrzymania, jeśli jeden konstruktor może delegować część pracy do innej. Aby dodać konstruktory delegowania, użyj składni `constructor (. . .) : constructor (. . .)`:

```cpp
class class_c {
public:
    int max;
    int min;
    int middle;

    class_c(int my_max) {
        max = my_max > 0 ? my_max : 10;
    }
    class_c(int my_max, int my_min) : class_c(my_max) {
        min = my_min > 0 && my_min < max ? my_min : 1;
    }
    class_c(int my_max, int my_min, int my_middle) : class_c (my_max, my_min){
        middle = my_middle < max && my_middle > min ? my_middle : 5;
}
};
int main() {

    class_c c1{ 1, 3, 2 };
}
```

Po przekroczeniu poprzedniego przykładu należy zauważyć, że Konstruktor `class_c(int, int, int)` najpierw wywołuje konstruktora `class_c(int, int)`, co z kolei wywołuje `class_c(int)`. Każdy z konstruktorów wykonuje tylko zadania, które nie są wykonywane przez inne konstruktory.

Pierwszy Konstruktor, który jest wywoływany inicjuje obiekt w taki sposób, że wszystkie jego elementy członkowskie są inicjowane w tym momencie. Nie można zainicjować składowej w konstruktorze, który delegatuje do innego konstruktora, jak pokazano poniżej:

```cpp
class class_a {
public:
    class_a() {}
    // member initialization here, no delegate
    class_a(string str) : m_string{ str } {}

    //can’t do member initialization here
    // error C3511: a call to a delegating constructor shall be the only member-initializer
    class_a(string str, double dbl) : class_a(str) , m_double{ dbl } {}

    // only member assignment
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }
    double m_double{ 1.0 };
    string m_string;
};
```

W następnym przykładzie pokazano użycie niestatycznych inicjatorów składowych danych. Zwróć uwagę, że jeśli Konstruktor inicjuje również dany element członkowski danych, inicjator składowej jest zastępowany:

```cpp
class class_a {
public:
    class_a() {}
    class_a(string str) : m_string{ str } {}
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }
    double m_double{ 1.0 };
    string m_string{ m_double < 10.0 ? "alpha" : "beta" };
};

int main() {
    class_a a{ "hello", 2.0 };  //expect a.m_double == 2.0, a.m_string == "hello"
    int y = 4;
}
```

Składnia delegowania konstruktora nie uniemożliwia przypadkowego utworzenia rekursji konstruktorów — wywołania Constructor1 Constructor2, które wywołuje Constructor1 — i żadne błędy nie są zgłaszane do momentu przepełnienia stosu. Jest on odpowiedzialny za uniknięcie cykli.

```cpp
class class_f{
public:
    int max;
    int min;

    // don't do this
    class_f() : class_f(6, 3){ }
    class_f(int my_max, int my_min) : class_f() { }
};
```
