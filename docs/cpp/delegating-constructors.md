---
title: Delegowanie konstruktorów (C++)
description: Użyj delegujących konstruktorów w języku C++ do wywoływania innych konstruktorów i zmniejszenia powtarzania kodu.
ms.date: 11/19/2019
ms.openlocfilehash: f26a013aa3c081d900ffc3eb32649acc77505db0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316671"
---
# <a name="delegating-constructors"></a>Delegowanie konstruktorów

Wiele klas ma wiele konstruktorów, które wykonują podobne czynności — na przykład sprawdzają poprawność parametrów:

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

Można zmniejszyć powtarzający się kod, dodając funkcję, która wykonuje wszystkie sprawdzania `class_c` poprawności, ale kod dla byłoby łatwiejsze do zrozumienia i utrzymania, jeśli jeden konstruktor może delegować niektóre z pracy do innego. Aby dodać konstruktory `constructor (. . .) : constructor (. . .)` delegujące, należy użyć składni:

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

Podczas przechodzenia przez poprzedni przykład zwróć `class_c(int, int, int)` uwagę, że `class_c(int, int)`konstruktor najpierw `class_c(int)`wywołuje konstruktora, co z kolei wywołuje . Każdy z konstruktorów wykonuje tylko pracę, która nie jest wykonywana przez innych konstruktorów.

Pierwszy konstruktor, który jest nazywany inicjuje obiekt tak, że wszystkie jego elementy członkowskie są inicjowane w tym momencie. Inicjowanie elementu członkowskiego w konstruktorze, który deleguje do innego konstruktora, jak pokazano w tym miejscu:

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

W następnym przykładzie pokazano użycie inicjatorów niestatycznych elementów członkowskich danych. Należy zauważyć, że jeśli konstruktor inicjuje również danego elementu członkowskiego danych, element członkowski inicjatora jest zastępowane:

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

Składnia delegowania konstruktora nie zapobiega przypadkowemu utworzeniu rekursji konstruktora — Konstruktor1 wywołuje Constructor2, który wywołuje Constructor1 — i żadne błędy nie są generowane, dopóki nie nastąpi przepełnienie stosu. Twoim obowiązkiem jest unikanie cykli.

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
