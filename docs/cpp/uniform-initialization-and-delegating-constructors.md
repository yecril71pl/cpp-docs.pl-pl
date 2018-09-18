---
title: Jednolite inicjowanie i delegowanie konstruktorów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: aa4daa64-eaec-4a3c-ade4-d9325e31e9d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 80beb5e840e182396f519b6b827dd8d727252d61
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116246"
---
# <a name="uniform-initialization-and-delegating-constructors"></a>Jednolite inicjowanie i delegowanie konstruktorów

W nowoczesnym C++, można użyć *nawiasów inicjowania* dla dowolnego typu, bez znaku równości. Ponadto możesz użyć konstruktory delegujące można uprościć kod, jeśli masz wiele konstruktorów, które mają podobne działanie.

## <a name="brace-initialization"></a>Nawiasów klamrowych

Można użyć nawiasów klamrowych dla dowolnej klasy, struktury lub Unii. Jeśli typ ma konstruktora domyślnego, jawnie lub niejawnie zadeklarowany, możesz użyć domyślnego nawiasów klamrowych (za pomocą pustych nawiasów klamrowych). Na przykład następującej klasy może być inicjowane za pomocą domyślnego i innych niż domyślne nawiasów klamrowych:

```cpp
#include <string>
using namespace std;

class class_a {
public:
    class_a() {}
    class_a(string str) : m_string{ str } {}
    class_a(string str, double dbl) : m_string{ str }, m_double{ dbl } {}
double m_double;
string m_string;
};

int main()
{
    class_a c1{};
    class_a c1_1;

    class_a c2{ "ww" };
    class_a c2_1("xx");

    // order of parameters is the same as the constructor
    class_a c3{ "yy", 4.4 };
    class_a c3_1("zz", 5.5);
}
```

Jeśli klasa ma konstruktory inne niż domyślne, kolejności, w której klasy elementy członkowskie są wyświetlane w inicjatorze nawias klamrowy jest kolejność wyświetlania odpowiednich parametrów w konstruktorze, nie kolejności, w którym są zadeklarowane elementy członkowskie (podobnie jak w przypadku `class_a` w poprzedniego przykładu). W przeciwnym razie jeśli typ nie ma zadeklarowany konstruktora, kolejność wyświetlania elementów członkowskich w inicjatorze nawias klamrowy jest taka sama jak kolejność, w którym są one zadeklarowane; w takim przypadku można zainicjować tyle publiczne elementy członkowskie jako użytkownik chce, ale nie można pominąć dowolnego elementu członkowskiego. Poniższy przykład przedstawia kolejność, która jest używana w nawiasów klamrowych, po żaden konstruktor zadeklarowana:

```cpp
class class_d {
public:
    float m_float;
    string m_string;
    wchar_t m_char;
};

int main()
{
    class_d d1{};
    class_d d1{ 4.5 };
    class_d d2{ 4.5, "string" };
    class_d d3{ 4.5, "string", 'c' };

    class_d d4{ "string", 'c' }; // compiler error
    class_d d5("string", 'c', 2.0 }; // compiler error
}
```

Jeśli domyślny konstruktor jest jawnie zadeklarowana, lecz oznaczony jako usunięty, nie można użyć domyślnego nawiasów klamrowych:

```cpp
class class_f {
public:
    class_f() = delete;
    class_f(string x): m_string { x } {}
    string m_string;
};
int main()
{
    class_f cf{ "hello" };
    class_f cf1{}; // compiler error C2280: attempting to reference a deleted function
}
```

Możesz użyć nawiasów klamrowych dowolnym miejscu, należy zwykle wykonać inicjowania — na przykład, jako parametr funkcji lub wartość zwracana lub z **nowe** — słowo kluczowe:

```cpp
class_d* cf = new class_d{4.5};
kr->add_d({ 4.5 });
return { 4.5 };
```

## <a name="initializerlist-constructors"></a>Lista initializer_list konstruktorów

[Initializer_list, klasa](../standard-library/initializer-list-class.md) reprezentuje listę obiektów określonego typu, który może służyć w konstruktorze, a w innych kontekstach. Można skonstruować initializer_list, za pomocą nawiasów klamrowych:

```cpp
initializer_list<int> int_list{5, 6, 7};
```

> [!IMPORTANT]
>  Aby użyć tej klasy, należy dołączyć [ \<initializer_list >](../standard-library/initializer-list.md) nagłówka.

`initializer_list` Mogą być kopiowane. W tym przypadku nową listę elementów członkowskich są odwołaniami do oryginalnej listy elementów członkowskich:

```cpp
initializer_list<int> ilist1{ 5, 6, 7 };
initializer_list<int> ilist2( ilist1 );
if (ilist1.begin() == ilist2.begin())
    cout << "yes" << endl; // expect "yes"
```

Klasy kontenerów standardowej biblioteki, a także `string`, `wstring`, i `regex`, mają `initializer_list` konstruktorów. W poniższych przykładach pokazano, jak być ujmowana w nawiasy inicjowania za pomocą tych konstruktorów:

```cpp
vector<int> v1{ 9, 10, 11 };
map<int, string> m1{ {1, "a"}, {2, "b"} };
string s{ 'a', 'b', 'c' };
regex rgx{'x', 'y', 'z'};
```

## <a name="delegating-constructors"></a>Delegowanie konstruktorów

Wiele klas ma wiele konstruktorów, które wykonują podobne elementy — na przykład sprawdza poprawność parametrów:

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

Całość wielokrotnie używanego kodu może zmniejszyć, dodając funkcję, która wykonuje całą sprawdzania poprawności, ale kod `class_c` będą łatwiejsze do zrozumienia i utrzymania, jeśli jeden konstruktor może delegować część obciążenia pracą na inny. Aby dodać konstruktory delegujące, użyj `constructor (. . .) : constructor (. . .)` składni:

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

Podczas wykonywania kroków za pomocą poprzedniego przykładu, należy zauważyć, że Konstruktor `class_c(int, int, int)` najpierw wywołuje konstruktor `class_c(int, int)`, który z kolei wywołuje `class_c(int)`. Każda z konstruktorów wykonuje pracę, która nie jest wykonywane przez inne konstruktory.

Pierwszy Konstruktor, który jest nazywany inicjuje obiekt tak, aby wszystkie jego elementy członkowskie są inicjowane w tym momencie. Inicjowanie składowej w konstruktorze, który delegował do innego konstruktora, nie są, jak pokazano poniżej:

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

W kolejnym przykładzie pokazano użycie inicjatory niestatycznego elementu członkowskiego danych. Zwróć uwagę, że jeśli Konstruktor inicjuje również element członkowski danych danego, zastąpić inicjator składowej:

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

Konstruktor delegowania składni nie uniemożliwia przypadkowe tworzenie rekursji konstruktora — Constructor1 wywołuje Constructor2, która wywołuje Constructor1 — i nie są generowane błędy momentu przepełnienia stosu. Jest odpowiedzialny za uniknięcia cyklów.

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