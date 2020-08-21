---
title: union
description: Opis standardowego union class typu C++ i słowa kluczowego, jego użycia i ograniczeń.
ms.date: 08/18/2020
f1_keywords:
- union_cpp
helpviewer_keywords:
- class type [C++], union as
- union keyword [C++]
ms.assetid: 25c4e219-fcbb-4b7b-9b64-83f3252a92ca
no-loc:
- union
- struct
- enum
- class
- static
ms.openlocfilehash: a4dc07df5e7858dffe62478509ee1d8dc759ce96
ms.sourcegitcommit: f1752bf90b4f869633a859ace85439ca19e208b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2020
ms.locfileid: "88722183"
---
# `union`

> [!NOTE]
> W języku C++ 17 i nowszych `std::variant` class jest to bezpieczna dla typu alternatywna dla union .

A **`union`** jest typem zdefiniowanym przez użytkownika, w którym wszyscy członkowie mają tę samą lokalizację w pamięci. Ta definicja oznacza, że w danym momencie union może zawierać nie więcej niż jeden obiekt z listy członków. Oznacza to również, że niezależnie od tego, jak wiele składowych union ma, zawsze używa wystarczającej ilości pamięci do przechowywania największego elementu członkowskiego.

unionMoże być przydatne w przypadku zachowywania pamięci w przypadku dużej ilości obiektów i ograniczonej ilości pamięci. Jednak union wymaga poprawnego użycia. Użytkownik jest odpowiedzialny za zapewnienie, że zawsze uzyskuje się dostęp do tego samego elementu członkowskiego, który został przypisany. Jeśli jakiekolwiek typy elementów członkowskich mają nieuproszczoną con struct lub, należy napisać dodatkowy kod, aby jawnie struct i zniszczyć ten element członkowski. Przed użyciem należy union rozważyć, czy problem, który próbujesz rozwiązać, może być lepiej wyrażony przy użyciu podstawowych class i pochodnych class typów.

## <a name="syntax"></a>Składnia

> **`union`***`tag`* <sub>opt</sub> **`{`** wybór *`member-list`***`};`**

### <a name="parameters"></a>Parametry

*`tag`*<br/>
Nazwa typu nadana union .

*`member-list`*<br/>
Elementy członkowskie, które union mogą zawierać.

## <a name="declare-a-no-locunion"></a>Zadeklaruj union

Rozpocznij deklarację a union za pomocą **`union`** słowa kluczowego i umieść listę elementów członkowskich w nawiasach klamrowych:

```cpp
// declaring_a_union.cpp
union RecordType    // Declare a simple union type
{
    char   ch;
    int    i;
    long   l;
    float  f;
    double d;
    int *int_ptr;
};

int main()
{
    RecordType t;
    t.i = 5; // t holds an int
    t.f = 7.25; // t now holds a float
}
```

## <a name="use-a-no-locunion"></a>Użyj union

W poprzednim przykładzie każdy kod, który uzyskuje dostęp do union potrzeb, aby wiedzieć, który element członkowski przechowuje dane. Najczęstsze rozwiązanie tego problemu nazywa się *odróżnieniem union *. unionZnajduje się w struct i zawiera enum element członkowski wskazujący typ elementu członkowskiego, który jest obecnie przechowywany w union . Poniższy przykład przedstawia podstawowy wzorzec:

```cpp
#include <queue>

using namespace std;

enum class WeatherDataType
{
    Temperature, Wind
};

struct TempData
{
    int StationId;
    time_t time;
    double current;
    double max;
    double min;
};

struct WindData
{
    int StationId;
    time_t time;
    int speed;
    short direction;
};

struct Input
{
    WeatherDataType type;
    union
    {
        TempData temp;
        WindData wind;
    };
};

// Functions that are specific to data types
void Process_Temp(TempData t) {}
void Process_Wind(WindData w) {}

void Initialize(std::queue<Input>& inputs)
{
    Input first;
    first.type = WeatherDataType::Temperature;
    first.temp = { 101, 1418855664, 91.8, 108.5, 67.2 };
    inputs.push(first);

    Input second;
    second.type = WeatherDataType::Wind;
    second.wind = { 204, 1418859354, 14, 27 };
    inputs.push(second);
}

int main(int argc, char* argv[])
{
    // Container for all the data records
    queue<Input> inputs;
    Initialize(inputs);
    while (!inputs.empty())
    {
        Input const i = inputs.front();
        switch (i.type)
        {
        case WeatherDataType::Temperature:
            Process_Temp(i.temp);
            break;
        case WeatherDataType::Wind:
            Process_Wind(i.wind);
            break;
        default:
            break;
        }
        inputs.pop();

    }
    return 0;
}
```

W poprzednim przykładzie, union w `Input` struct nie ma nazwy, dlatego jest nazywana *anonimowo* union . Dostęp do jego członków jest możliwy bezpośrednio, jeśli są członkami struct . Aby uzyskać więcej informacji na temat korzystania z anonimowego union , zobacz [sekcję union anonimowy](#anonymous_unions) .

W poprzednim przykładzie przedstawiono problem, który można również rozwiązać, używając class typów, które pochodzą ze wspólnej bazy class . Kod można rozgałęzić na podstawie typu środowiska uruchomieniowego każdego obiektu w kontenerze. Kod może być łatwiejszy do utrzymania i zrozumienia, ale może być również wolniejszy niż użycie union . Ponadto w przypadku programu union można przechowywać niepowiązane typy. A union pozwala dynamicznie zmienić typ przechowywanej wartości bez zmiany typu union samej zmiennej. Można na przykład utworzyć niejednorodną tablicę `MyUnionType` , której elementy przechowują różne wartości różnych typów.

W przykładzie jest to łatwe w użyciu `Input` struct . W celu uzyskania dostępu do elementu członkowskiego, który zawiera dane, należy do użytkownika poprawnie używać rozróżniacza. Możesz chronić przed nieprawidłowym użyciem, udostępniając union **`private`** specjalne funkcje dostępu, jak pokazano w następnym przykładzie.

## <a name="unrestricted-no-locunion-c11"></a>Bez ograniczeń union (c++ 11)

W języku C++ 03 i starszych union mogą zawierać static elementy członkowskie, które mają class Typ, tak długo, jak typ nie ma struct ORS, de struct ORS lub operator przypisania. W języku C++ 11 te ograniczenia są usuwane. Jeśli dołączysz taki element członkowski w programie union , kompilator automatycznie oznaczy wszelkie specjalne funkcje członkowskie, które nie są podane przez użytkownika jako **`deleted`** . Jeśli union jest to anonimowe union wewnątrz a class lub struct , wszelkie specjalne funkcje członkowskie class lub, struct które nie są podane przez użytkownika, są oznaczone jako **`deleted`** . Poniższy przykład pokazuje, jak obsłużyć ten przypadek. Jeden z członków elementu union Członkowskiego ma element członkowski, który wymaga tego specjalnego traktowania:

```cpp
// for MyVariant
#include <crtdbg.h>
#include <new>
#include <utility>

// for sample objects and output
#include <string>
#include <vector>
#include <iostream>

using namespace std;

struct A
{
    A() = default;
    A(int i, const string& str) : num(i), name(str) {}

    int num;
    string name;
    //...
};

struct B
{
    B() = default;
    B(int i, const string& str) : num(i), name(str) {}

    int num;
    string name;
    vector<int> vec;
    // ...
};

enum class Kind { None, A, B, Integer };

#pragma warning (push)
#pragma warning(disable:4624)
class MyVariant
{
public:
    MyVariant()
        : kind_(Kind::None)
    {
    }

    MyVariant(Kind kind)
        : kind_(kind)
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            new (&a_) A();
            break;
        case Kind::B:
            new (&b_) B();
            break;
        case Kind::Integer:
            i_ = 0;
            break;
        default:
            _ASSERT(false);
            break;
        }
    }

    ~MyVariant()
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            a_.~A();
            break;
        case Kind::B:
            b_.~B();
            break;
        case Kind::Integer:
            break;
        default:
            _ASSERT(false);
            break;
        }
        kind_ = Kind::None;
    }

    MyVariant(const MyVariant& other)
        : kind_(other.kind_)
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            new (&a_) A(other.a_);
            break;
        case Kind::B:
            new (&b_) B(other.b_);
            break;
        case Kind::Integer:
            i_ = other.i_;
            break;
        default:
            _ASSERT(false);
            break;
        }
    }

    MyVariant(MyVariant&& other)
        : kind_(other.kind_)
    {
        switch (kind_)
        {
        case Kind::None:
            break;
        case Kind::A:
            new (&a_) A(move(other.a_));
            break;
        case Kind::B:
            new (&b_) B(move(other.b_));
            break;
        case Kind::Integer:
            i_ = other.i_;
            break;
        default:
            _ASSERT(false);
            break;
        }
        other.kind_ = Kind::None;
    }

    MyVariant& operator=(const MyVariant& other)
    {
        if (&other != this)
        {
            switch (other.kind_)
            {
            case Kind::None:
                this->~MyVariant();
                break;
            case Kind::A:
                *this = other.a_;
                break;
            case Kind::B:
                *this = other.b_;
                break;
            case Kind::Integer:
                *this = other.i_;
                break;
            default:
                _ASSERT(false);
                break;
            }
        }
        return *this;
    }

    MyVariant& operator=(MyVariant&& other)
    {
        _ASSERT(this != &other);
        switch (other.kind_)
        {
        case Kind::None:
            this->~MyVariant();
            break;
        case Kind::A:
            *this = move(other.a_);
            break;
        case Kind::B:
            *this = move(other.b_);
            break;
        case Kind::Integer:
            *this = other.i_;
            break;
        default:
            _ASSERT(false);
            break;
        }
        other.kind_ = Kind::None;
        return *this;
    }

    MyVariant(const A& a)
        : kind_(Kind::A), a_(a)
    {
    }

    MyVariant(A&& a)
        : kind_(Kind::A), a_(move(a))
    {
    }

    MyVariant& operator=(const A& a)
    {
        if (kind_ != Kind::A)
        {
            this->~MyVariant();
            new (this) MyVariant(a);
        }
        else
        {
            a_ = a;
        }
        return *this;
    }

    MyVariant& operator=(A&& a)
    {
        if (kind_ != Kind::A)
        {
            this->~MyVariant();
            new (this) MyVariant(move(a));
        }
        else
        {
            a_ = move(a);
        }
        return *this;
    }

    MyVariant(const B& b)
        : kind_(Kind::B), b_(b)
    {
    }

    MyVariant(B&& b)
        : kind_(Kind::B), b_(move(b))
    {
    }

    MyVariant& operator=(const B& b)
    {
        if (kind_ != Kind::B)
        {
            this->~MyVariant();
            new (this) MyVariant(b);
        }
        else
        {
            b_ = b;
        }
        return *this;
    }

    MyVariant& operator=(B&& b)
    {
        if (kind_ != Kind::B)
        {
            this->~MyVariant();
            new (this) MyVariant(move(b));
        }
        else
        {
            b_ = move(b);
        }
        return *this;
    }

    MyVariant(int i)
        : kind_(Kind::Integer), i_(i)
    {
    }

    MyVariant& operator=(int i)
    {
        if (kind_ != Kind::Integer)
        {
            this->~MyVariant();
            new (this) MyVariant(i);
        }
        else
        {
            i_ = i;
        }
        return *this;
    }

    Kind GetKind() const
    {
        return kind_;
    }

    A& GetA()
    {
        _ASSERT(kind_ == Kind::A);
        return a_;
    }

    const A& GetA() const
    {
        _ASSERT(kind_ == Kind::A);
        return a_;
    }

    B& GetB()
    {
        _ASSERT(kind_ == Kind::B);
        return b_;
    }

    const B& GetB() const
    {
        _ASSERT(kind_ == Kind::B);
        return b_;
    }

    int& GetInteger()
    {
        _ASSERT(kind_ == Kind::Integer);
        return i_;
    }

    const int& GetInteger() const
    {
        _ASSERT(kind_ == Kind::Integer);
        return i_;
    }

private:
    Kind kind_;
    union
    {
        A a_;
        B b_;
        int i_;
    };
};
#pragma warning (pop)

int main()
{
    A a(1, "Hello from A");
    B b(2, "Hello from B");

    MyVariant mv_1 = a;

    cout << "mv_1 = a: " << mv_1.GetA().name << endl;
    mv_1 = b;
    cout << "mv_1 = b: " << mv_1.GetB().name << endl;
    mv_1 = A(3, "hello again from A");
    cout << R"aaa(mv_1 = A(3, "hello again from A"): )aaa" << mv_1.GetA().name << endl;
    mv_1 = 42;
    cout << "mv_1 = 42: " << mv_1.GetInteger() << endl;

    b.vec = { 10,20,30,40,50 };

    mv_1 = move(b);
    cout << "After move, mv_1 = b: vec.size = " << mv_1.GetB().vec.size() << endl;

    cout << endl << "Press a letter" << endl;
    char c;
    cin >> c;
}
```

unionNie można zapisać odwołania. unionPonadto nie obsługuje dziedziczenia. Oznacza to, że nie można użyć union jako podstawy class ani dziedziczyć z innego class lub mieć funkcje wirtualne.

## <a name="initialize-a-no-locunion"></a>Zainicjuj union

Można zadeklarować i zainicjować union w tej samej instrukcji przez przypisanie wyrażenia ujętego w nawiasy klamrowe. Wyrażenie jest oceniane i przypisywane do pierwszego pola union .

```cpp
#include <iostream>
using namespace std;

union NumericType
{
    short       iValue;
    long        lValue;
    double      dValue;
};

int main()
{
    union NumericType Values = { 10 };   // iValue = 10
    cout << Values.iValue << endl;
    Values.dValue = 3.1416;
    cout << Values.dValue << endl;
}
/* Output:
10
3.141600
*/
```

`NumericType` union Jest on uporządkowany w pamięci (koncepcyjnie), jak pokazano na poniższej ilustracji.

![Magazyn danych w typie liczbowym::: No-Loc (Unia)::](../cpp/media/vc38ul1.png "Magazyn danych w postaci liczbowej::: No-Loc (Unia)::") <br/>
Przechowywanie danych w `NumericType`union

## <a name="anonymous-no-locunion"></a><a name="anonymous_unions"></a> Anonimowe union

Anonimowy union jest zadeklarowany bez *`class-name`* lub *`declarator-list`* .

> **`union  {`**  *`member-list`*  **`}`**

Nazwy zadeklarowane w anonimowym union są używane bezpośrednio, podobnie jak zmienne nieczłonkowskie. Oznacza to, że nazwy zadeklarowane w anonimowym union musi być unikatowa w otaczającym zakresie.

Anonimowy union podlega tym dodatkowym ograniczeniom:

- Jeśli jest zadeklarowany w zakresie pliku lub przestrzeni nazw, musi również być zadeklarowany jako **`static`** .

- Może mieć tylko **`public`** członków, członków **`private`** i **`protected`** elementów członkowskich w ramach anonimowego union generowania błędów.

- Nie może mieć funkcji składowych.

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../cpp/classes-and-structs-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[`class`](../cpp/class-cpp.md)<br/>
[`struct`](../cpp/struct-cpp.md)
