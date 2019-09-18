---
title: Unie
ms.date: 05/06/2019
f1_keywords:
- union_cpp
helpviewer_keywords:
- class types [C++], unions as
- union keyword [C++]
ms.assetid: 25c4e219-fcbb-4b7b-9b64-83f3252a92ca
ms.openlocfilehash: 8a4ea3ae325eb5882c2f8b2524bbc156d12ffcc6
ms.sourcegitcommit: bf724dfc639b16d5410fab72183f8e6b781338bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71062057"
---
# <a name="unions"></a>Unie

> [!NOTE]
> W języku C++ 17 i nowszych Klasa **std:: Variant** jest bezpieczną alternatywą dla Unii.

**Unia** jest typem zdefiniowanym przez użytkownika, w którym wszyscy członkowie mają tę samą lokalizację w pamięci. Oznacza to, że w dowolnym momencie Unia może zawierać nie więcej niż jeden obiekt z listy członków. Oznacza to również, że niezależnie od tego, jak wiele składowych jest Unii, zawsze używa wystarczającej ilości pamięci do przechowywania największego elementu członkowskiego.

Unia może być przydatna do zachowywania pamięci, jeśli masz wiele obiektów i/lub ograniczoną ilość pamięci. Jednak wymaga to poprawnego użycia, ponieważ użytkownik jest odpowiedzialny za zapewnienie, że zawsze uzyskuje się dostęp do ostatniego elementu członkowskiego, który został zapisany. Jeśli jakiekolwiek typy elementów członkowskich mają Konstruktor nieuproszczony, należy napisać dodatkowy kod, aby jawnie skonstruować i zniszczyć ten element członkowski. Przed użyciem Unii należy rozważyć, czy problem, który próbujesz rozwiązać, może być lepiej wyrażony przy użyciu klasy bazowej i klas pochodnych.

## <a name="syntax"></a>Składnia

```cpp
union [name]  { member-list };
```

### <a name="parameters"></a>Parametry

*name*<br/>
Nazwa typu nadana unii.

*Lista elementów członkowskich*<br/>
Elementy członkowskie, które może zawierać Unia. Zobacz uwagi.

## <a name="remarks"></a>Uwagi

## <a name="declaring-a-union"></a>Deklarowanie unii

Rozpocznij deklarację Unii za pomocą słowa kluczowego **Union** i umieść listę elementów członkowskich w nawiasach klamrowych:

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

## <a name="using-unions"></a>Używanie Unii

W poprzednim przykładzie każdy kod, który uzyskuje dostęp do Unii, musi wiedzieć, który element członkowski posiada dane. Najbardziej typowym rozwiązaniem tego problemu jest ujęcie Unii w strukturze wraz z dodatkowym elementem członkowskim wyliczenia, który wskazuje typ danych, które są obecnie przechowywane w Unii. Jest to nazywane *Unią rozłącznych* i w poniższym przykładzie przedstawiono wzorzec podstawowy.

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

// Container for all the data records
queue<Input> inputs;
void Initialize();

int main(int argc, char* argv[])
{
    Initialize();
    while (!inputs.empty())
    {
        Input i = inputs.front();
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

void Initialize()
{
    Input first, second;
    first.type = WeatherDataType::Temperature;
    first.temp = { 101, 1418855664, 91.8, 108.5, 67.2 };
    inputs.push(first);

    second.type = WeatherDataType::Wind;
    second.wind = { 204,1418859354, 14, 27 };
    inputs.push(second);
}
```

W poprzednim przykładzie należy zauważyć, że Unia w strukturze wejściowej nie ma nazwy. Jest to anonimowa Unia, a jej członkowie są dostępni tak, jakby byli bezpośrednimi elementami członkowskimi struktury. Więcej informacji na temat anonimowych Unii znajduje się w sekcji poniżej.

Oczywiście w poprzednim przykładzie przedstawiono problem, który można również rozwiązać przy użyciu klas, które pochodzą ze wspólnej klasy bazowej, i rozgałęziać kod na podstawie typu środowiska uruchomieniowego każdego obiektu w kontenerze. Może to spowodować, że kod jest łatwiejszy do utrzymania i zrozumienia, ale może być również wolniejszy niż używanie Unii. Ponadto za pomocą Unii można przechowywać całkowicie niepowiązane typy i dynamicznie zmieniać typ wartości przechowywanej bez zmiany typu samej zmiennej Union. W związku z tym można utworzyć niejednorodną tablicę elementu webuniontype, której elementy przechowują różne wartości różnych typów.

Należy zauważyć, `Input` że struktura w powyższym przykładzie może być łatwo użyta. Aby uzyskać dostęp do elementu członkowskiego, który zawiera dane, należy prawidłowo użyć rozróżniacza. Możesz chronić przed nieprawidłowym użyciem, przekazując pozycję Union jako prywatną i udostępniając specjalne funkcje dostępu, jak pokazano w następnym przykładzie.

## <a name="unrestricted-unions-c11"></a>Nieograniczone związki (C++ 11)

W języku C++ 03 i starszych element Union może zawierać niestatyczne składowe danych o typie klasy, tak długo, jak typ nie ma konstruktorów dostarczonych przez użytkownika, destruktorów ani operatorów przypisania. W języku C++ 11 te ograniczenia są usuwane. W przypadku włączenia takiego elementu członkowskiego do Unii kompilator automatycznie oznaczy wszelkie specjalne funkcje członkowskie, które nie są dostarczane przez użytkownika jako usunięte. Jeśli Unia jest anonimową Unią w obrębie klasy lub struktury, wówczas wszelkie specjalne funkcje członkowskie klasy lub struktury, które nie są dostarczane przez użytkownika, są oznaczane jako usunięte. Poniższy przykład pokazuje, jak obsłużyć przypadek, w którym jeden z elementów członkowskich Unii ma element członkowski, który wymaga tego specjalnego traktowania:

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
#include <queue>
#include <iostream>
using namespace std;

enum class WeatherDataType
{
    Temperature, Wind
};

struct TempData
{
    TempData() : StationId(""), time(0), current(0), maxTemp(0), minTemp(0) {}
    TempData(string id, time_t t, double cur, double max, double min)
        : StationId(id), time(t), current(cur), maxTemp(max), minTemp(0) {}
    string StationId;
    time_t time = 0;
    double current;
    double maxTemp;
    double minTemp;
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
    Input() {}
    Input(const Input&) {}

    ~Input()
    {
        if (type == WeatherDataType::Temperature)
        {
            temp.StationId.~string();
        }
    }

    WeatherDataType type;
    void SetTemp(const TempData& td)
    {
        type = WeatherDataType::Temperature;

        // must use placement new because of string member!
        new(&temp) TempData(td);
    }

    TempData GetTemp()
    {
        if (type == WeatherDataType::Temperature)
            return temp;
        else
            throw logic_error("Can't return TempData when Input holds a WindData");
    }
    void SetWind(WindData wd)
    {
        // Explicitly delete struct member that has a
        // non-trivial constructor
        if (type == WeatherDataType::Temperature)
        {
            temp.StationId.~string();
        }
        wind = wd; //placement new not required.
    }
    WindData GetWind()
    {
        if (type == WeatherDataType::Wind)
        {
            return wind;
        }
        else
            throw logic_error("Can't return WindData when Input holds a TempData");
    }

private:

    union
    {
        TempData temp;
        WindData wind;
    };
};
```

W związku z tym nie można przechowywać odwołań. Unia nie obsługuje dziedziczenia, dlatego nie można używać samych związków jako klasy bazowej lub dziedziczyć z innej klasy ani mieć funkcji wirtualnych.

## <a name="initializing-unions"></a>Inicjowanie Unii

Można zadeklarować i zainicjować unię w tej samej instrukcji przez przypisanie wyrażenia ujętego w nawiasy klamrowe. Wyrażenie jest oceniane i przypisywane do pierwszego pola unii.

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
    cout << Values.dValue) << endl;
}
/* Output:
10
3.141600
*/
```

Unia `NumericType` jest umieszczona w pamięci (koncepcyjnie), jak pokazano na poniższym rysunku.

![Magazynowanie danych w Unii typu liczbowego](../cpp/media/vc38ul1.png "Magazynowanie danych w Unii numerycznej") <br/>
Przechowywanie danych w unii NumericType

## <a name="anonymous_unions"></a>Anonimowe Unii

Unii anonimowe to Unii, które są zadeklarowane bez *nazwy klasy* lub *listy deklarator*.

```cpp
union  {  member-list  }
```

Nazwy zadeklarowane w Unii anonimowej są używane bezpośrednio, podobnie jak zmienne niebędące członkami. W związku z tym nazwy zadeklarowane w anonimowej Unii muszą być unikatowe w otaczającym zakresie.

Oprócz ograniczeń dla nazwanych Unii, anonimowe Unii podlegają dodatkowym ograniczeniom:

- Muszą być również zadeklarowane jako **static** , jeśli są zadeklarowane w zakresie pliku lub przestrzeni nazw.

- Mogą mieć tylko **publiczne** elementy członkowskie; **prywatne** i **chronione** elementy członkowskie w Unii anonimowej generują błędy.

- Nie mogą mieć funkcji Członkowskich.

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../cpp/classes-and-structs-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[class](../cpp/class-cpp.md)<br/>
[struct](../cpp/struct-cpp.md)