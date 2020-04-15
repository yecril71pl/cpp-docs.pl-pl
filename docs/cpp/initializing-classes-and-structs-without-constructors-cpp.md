---
title: Inicjowanie nawiasów klamrowych dla klas, struktur i związków
description: Użyj inicjowania nawiasów klamrowych z dowolną klasą, strukturą lub unią języka C++.
ms.date: 11/19/2019
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
ms.openlocfilehash: 4628ffe8935fc32e86468c631d5d9e9622d63d2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374074"
---
# <a name="brace-initialization"></a>Inicjowanie nawiasów klamrowych

Nie zawsze jest konieczne zdefiniowanie konstruktora dla klasy, zwłaszcza te, które są stosunkowo proste. Użytkownicy mogą inicjować obiekty klasy lub struktury przy użyciu jednolitego inicjowania, jak pokazano w poniższym przykładzie:

```cpp
// no_constructor.cpp
// Compile with: cl /EHsc no_constructor.cpp
#include <time.h>

// No constructor
struct TempData
{
    int StationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

// Has a constructor
struct TempData2
{
    TempData2(double minimum, double maximum, double cur, int id, time_t t) :
       stationId{id}, timeSet{t}, current{cur}, maxTemp{maximum}, minTemp{minimum} {}
    int stationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

int main()
{
    time_t time_to_set;

    // Member initialization (in order of declaration):
    TempData td{ 45978, time(&time_to_set), 28.9, 37.0, 16.7 };

    // Default initialization = {0,0,0,0,0}
    TempData td_default{};

    // Uninitialized = if used, emits warning C4700 uninitialized local variable
    TempData td_noInit;

    // Member declaration (in order of ctor parameters)
    TempData2 td2{ 16.7, 37.0, 28.9, 45978, time(&time_to_set) };

    return 0;
}
```

Należy zauważyć, że gdy klasa lub struktura nie ma konstruktora, należy podać elementy listy w kolejności, w której elementy członkowskie są zadeklarowane w klasie. Jeśli klasa ma konstruktora, podaj elementy w kolejności parametrów. Jeśli typ ma domyślny konstruktor, niejawnie lub jawnie zadeklarowany, można użyć domyślnego inicjowania nawiasów klamrowych (z pustymi nawiasami klamrowymi). Na przykład następująca klasa może zostać zainicjowana przy użyciu inicjowania nawiasów klamrowych zarówno domyślnie, jak i nieobekonu domyślnych:

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

Jeśli klasa ma konstruktory inne niż domyślne, kolejność, w której elementy członkowskie klasy pojawiają się w inicjatorze nawiasów klamrowych, jest `class_a` kolejność, w której odpowiednie parametry pojawiają się w konstruktorze, a nie kolejność, w której elementy członkowskie są zadeklarowane (jak w poprzednim przykładzie). W przeciwnym razie, jeśli typ nie ma zadeklarowany konstruktora, kolejność, w której elementy członkowskie pojawiają się w inicjatora nawiasu klamrowego jest taka sama jak kolejność, w której są one zadeklarowane; w takim przypadku można zainicjować dowolną liczbę członków publicznych, ale nie można pominąć żadnego członka. Poniższy przykład pokazuje kolejność, która jest używana w inicjowaniu nawiasów klamrowych, gdy nie ma zadeklarowanej konstruktora:

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
    class_d d5{ "string", 'c', 2.0 }; // compiler error
}
```

Jeśli domyślny konstruktor jest jawnie zadeklarowany, ale oznaczony jako usunięty, nie można użyć domyślnego inicjowania nawiasu klamrowego:

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

Inicjowania nawiasów klamrowych można używać w dowolnym miejscu, w przypadku którego zwykle inicjujesz — na przykład jako parametr funkcji lub wartość zwracana lub za pomocą **nowego** słowa kluczowego:

```cpp
class_d* cf = new class_d{4.5};
kr->add_d({ 4.5 });
return { 4.5 };
```

W **trybie /std:c++17** reguły inicjowania pustego nawiasu klamrowego są nieco bardziej restrykcyjne. Zobacz [Konstruktory pochodne i rozszerzona inicjalizacja agregacji](constructors-cpp.md#extended_aggregate).

## <a name="initializer_list-constructors"></a>konstruktory initializer_list

[Klasa initializer_list](../standard-library/initializer-list-class.md) reprezentuje listę obiektów określonego typu, które mogą być używane w konstruktorze i w innych kontekstach. Initializer_list można utworzyć za pomocą inicjowania nawiasów klamrowych:

```cpp
initializer_list<int> int_list{5, 6, 7};
```

> [!IMPORTANT]
> Aby użyć tej klasy, należy dołączyć [ \<initializer_list>](../standard-library/initializer-list.md) nagłówka.

Można `initializer_list` skopiować. W takim przypadku członkowie nowej listy są odwołaniami do członków oryginalnej listy:

```cpp
initializer_list<int> ilist1{ 5, 6, 7 };
initializer_list<int> ilist2( ilist1 );
if (ilist1.begin() == ilist2.begin())
    cout << "yes" << endl; // expect "yes"
```

Standardowe klasy kontenerów biblioteki, `regex`a `initializer_list` także `string`, `wstring`i , mają konstruktorów. Poniższe przykłady pokazują, jak wykonać inicjowanie nawiasów klamrowych za pomocą tych konstruktorów:

```cpp
vector<int> v1{ 9, 10, 11 };
map<int, string> m1{ {1, "a"}, {2, "b"} };
string s{ 'a', 'b', 'c' };
regex rgx{ 'x', 'y', 'z' };
```

## <a name="see-also"></a>Zobacz też

[Klasy i struktury](../cpp/classes-and-structs-cpp.md)<br/>
[Konstruktorów](../cpp/constructors-cpp.md)
