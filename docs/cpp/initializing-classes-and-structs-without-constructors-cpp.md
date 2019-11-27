---
title: Inicjalizacja nawiasów klamrowych dla klas, struktur i Unii
description: Użyj inicjowania nawiasów klamrowych C++ z dowolną klasą, strukturą lub Unią
ms.date: 11/19/2019
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
ms.openlocfilehash: 41ff38bc4bcc9ebca913b5e66b5ac2f395044222
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246502"
---
# <a name="brace-initialization"></a>Inicjowanie nawiasów klamrowych

Nie zawsze jest konieczne zdefiniowanie konstruktora dla klasy, szczególnie, które są stosunkowo proste. Użytkownicy mogą inicjować obiekty klasy lub struktury przy użyciu jednolitej inicjalizacji, jak pokazano w następującym przykładzie:

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

Należy pamiętać, że jeśli Klasa lub struktura nie ma konstruktora, należy dostarczyć elementy listy w kolejności, w której elementy członkowskie są zadeklarowane w klasie. Jeśli klasa ma konstruktora, podaj elementy w kolejności parametrów. Jeśli typ ma konstruktora domyślnego, niejawnie lub jawnie zadeklarowane, można użyć domyślnego inicjowania nawiasów klamrowych (z pustymi nawiasami klamrowymi). Na przykład następująca Klasa może zostać zainicjowana przy użyciu domyślnego i niedomyślnego nawiasu klamrowego:

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

Jeśli klasa ma konstruktory inne niż domyślne, kolejność, w której elementy członkowskie klasy pojawiają się w inicjatorze nawiasów klamrowych, jest kolejnością, w której są odpowiednie parametry w konstruktorze, a nie kolejność, w której są zadeklarowane elementy członkowskie (jak w poprzednim przykładzie `class_a`). W przeciwnym razie, jeśli typ nie ma zadeklarowanego konstruktora, kolejność, w której elementy członkowskie pojawiają się w inicjatorze nawiasów klamrowych jest taka sama jak kolejność, w jakiej zostały zadeklarowane; w takim przypadku można zainicjować dowolną liczbę publicznych członków, ale nie można pominąć żadnego elementu członkowskiego. Poniższy przykład pokazuje kolejność, która jest używana w inicjacji w nawiasach klamrowych, gdy nie istnieje zadeklarowany Konstruktor:

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

Jeśli domyślny konstruktor jest zadeklarowany w sposób jawny, ale oznaczony jako usunięty, nie można użyć domyślnego inicjowania nawiasów klamrowych:

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

Można użyć inicjalizacji nawiasów klamrowych wszędzie tam, gdzie jest to zwykle inicjowane — na przykład jako parametru funkcji lub wartości zwracanej lub za pomocą słowa kluczowego **New** :

```cpp
class_d* cf = new class_d{4.5};
kr->add_d({ 4.5 });
return { 4.5 };
```

## <a name="initializer_list-constructors"></a>Konstruktory initializer_list

[Klasa initializer_list](../standard-library/initializer-list-class.md) reprezentuje listę obiektów określonego typu, które mogą być używane w konstruktorze, oraz w innych kontekstach. Initializer_list można skonstruować za pomocą inicjowania nawiasów klamrowych:

```cpp
initializer_list<int> int_list{5, 6, 7};
```

> [!IMPORTANT]
>  Aby użyć tej klasy, należy uwzględnić [\<initializer_list >](../standard-library/initializer-list.md) nagłówku.

`initializer_list` można skopiować. W takim przypadku elementy członkowskie nowej listy są odwołaniami do członków oryginalnej listy:

```cpp
initializer_list<int> ilist1{ 5, 6, 7 };
initializer_list<int> ilist2( ilist1 );
if (ilist1.begin() == ilist2.begin())
    cout << "yes" << endl; // expect "yes"
```

Klasy kontenerów biblioteki standardowej, a także `string`, `wstring`i `regex`mają konstruktorów `initializer_list`. W poniższych przykładach pokazano, jak wykonać inicjalizację nawiasów klamrowych przy użyciu następujących konstruktorów:

```cpp
vector<int> v1{ 9, 10, 11 };
map<int, string> m1{ {1, "a"}, {2, "b"} };
string s{ 'a', 'b', 'c' };
regex rgx{'x', 'y', 'z'};
```


## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../cpp/classes-and-structs-cpp.md)<br/>
[Konstruktory](../cpp/constructors-cpp.md)
