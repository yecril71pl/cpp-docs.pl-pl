---
title: Unie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- union_cpp
dev_langs:
- C++
helpviewer_keywords:
- class types [C++], unions as
- union keyword [C++]
ms.assetid: 25c4e219-fcbb-4b7b-9b64-83f3252a92ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 066f7c50940e6c68bb0fca554bb3bc56fc20b93c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32425702"
---
# <a name="unions"></a>Unie
A `union` jest typem zdefiniowane przez użytkownika, w której wszyscy członkowie mają tę samą lokalizację pamięci. Oznacza to, w danym momencie Unii może zawierać nie więcej niż jeden obiekt z listy elementów członkowskich. Oznacza to również, że niezależnie od tego, jak wiele elementów członkowskich Unii ma, zawsze używa tylko wystarczającej ilości pamięci do przechowywania największy element członkowski.  
  
 Unie może być przydatne w przypadku efektywne wykorzystanie pamięci, jeśli masz wiele obiektów i/lub ograniczonej pamięci. Jednak wymagają one szczególną uwagę używać poprawnie, ponieważ jest odpowiedzialny za zapewnienie zawsze dostęp do ostatniego członka, które zostało zapisane. Wszystkie typy elementów członkowskich ma nieuproszczone konstruktora, należy zapisać dodatkowy kod w celu jawnego utworzenia i zniszcz ten element członkowski. Przed użyciem Unii, należy wziąć pod uwagę czy problem, który chcesz rozwiązać, można lepiej można wyrazić przy użyciu klasy podstawowej i klas pochodnych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
union [name]  { member-list };  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Nazwa typu nadana unii.  
  
 `member-list`  
 Elementy członkowskie, które mogą zawierać Unii. Zobacz uwagi.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="declaring-a-union"></a>Deklarowanie unii  
 Rozpocznij deklaracji typu union z `union` — słowo kluczowe i ująć w nawiasy klamrowe listy elementów członkowskich:  
  
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
    t.f = 7.25 // t now holds a float   
}  
```  
  
## <a name="using-unions"></a>Przy użyciu Unii  
 W poprzednim przykładzie kodu, który uzyskuje dostęp do Unii musi wiedzieć, który element członkowski jest zawierający dane. Najbardziej typowe rozwiązania tego problemu jest Unii, należy ująć w strukturze wraz z elementu członkowskiego wyliczenia dodatkowych, który wskazuje typ danych obecnie przechowywanych w Unii. Ta metoda jest wywoływana *Suma rozłączna Unii* i w poniższym przykładzie przedstawiono podstawowe wzorca.  
  
```cpp  
#include "stdafx.h"  
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
  
 W poprzednim przykładzie należy pamiętać, że Unii w strukturze danych wejściowych nie ma nazwy. To jest anonimowa Unia i jej elementów członkowskich jest dostępny, tak jakby były bezpośrednie elementy członkowskie struktury. Aby uzyskać więcej informacji na temat związki anonimowe zobacz sekcję poniżej.  
  
 Oczywiście w poprzednim przykładzie przedstawiono problem, który może również zostać rozwiązane z wykorzystaniem klas pochodzących od wspólna klasa podstawowa i rozgałęzianie kodu na podstawie typu środowiska uruchomieniowego poszczególnych obiektów w kontenerze. Może to spowodować, że łatwiejsze do utrzymywania i zrozumieć, jednak może być również wolniej niż przy użyciu unie kodu. Ponadto z Unii, można przechowywać całkowicie niepowiązanych typów i dynamicznie Zmień typ wartości przechowywanych bez zmiany typu union samej zmiennej. W związku z tym można utworzyć heterogenicznych tablicę MyUnionType, której elementy przechowywać różne wartości różnych typów.  
  
 Należy pamiętać, że `Input` struktury w poprzednim przykładzie można łatwo użyte. Jest całkowicie użytkownika na potrzeby rozróżniacza poprawnie dostęp do elementu członkowskiego, który zawiera dane. Można chronić przed niewłaściwym użyciem przez tworzenie prywatnych Unii i udostępniając specjalne funkcje, jak pokazano w następnym przykładzie.  
  
## <a name="unrestricted-unions-c11"></a>Nieograniczonych Unii (C ++ 11)  
 W języku C ++ 03 i starszych Unii może zawierać elementy członkowskie danych statyczna z typu klasy, tak długo, jak typ nie ma konstruktorów podane przez użytkownika, destruktorów ani operatory przypisania. W języku C ++ 11 te ograniczenia zostały usunięte. Jeśli dołączysz element członkowski w związku z następnie kompilator automatycznie spowoduje oznaczenie żadnych specjalnych funkcji Członkowskich, które nie są podane jako usunięty przez użytkownika. Jeśli Unii anonimowej Unii wewnątrz klasy lub struktury, żadnych specjalnych funkcji Członkowskich klasy lub struktury, które nie są podane przez użytkownika są oznaczone jako usunięte. Poniższy przykład przedstawia sposób obsługi w przypadku, gdy jeden z elementów członkowskich Unii ma elementu członkowskiego, który wymaga specjalnego traktowania:  
  
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
  
 Unie nie można zapisać odwołań. Unie nie obsługuje dziedziczenia, w związku z tym Unii sam nie może służyć jako klasę podstawową lub dziedziczyć po innej klasie lub mieć funkcji wirtualnych.  
  
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
  
 ![Przechowywanie danych w Unii typ liczbowy](../cpp/media/vc38ul1.png "vc38UL1")  
Przechowywanie danych w unii NumericType  
  
## <a name="anonymous_unions"></a> Związki anonimowe  
 Związki anonimowe są Unii, które są zadeklarowane bez *Nazwa klasy* lub *deklarator listy*.  
  
```cpp  
union  {  member-list  }    
```  
  
Zadeklarowany w anonimowym związku używane są nazwy bezpośrednio, takich jak zmienne niebędący elementem członkowskim. W związku z tym nazwy zadeklarowany w anonimowa Unia musi być unikatowy w otaczającym zasięgu.  
  
Oprócz ograniczeń dla nazwanego unie związki anonimowe obowiązują następujące dodatkowe ograniczenia:  
  
-   Również musi być zadeklarowany jako **statycznych** zadeklarowana w zakresie pliku lub przestrzeni nazw.  
  
-   Mogą oni mieć tylko publiczne elementy członkowskie; prywatnych i chronionych elementów członkowskich w anonimowych uniach generować błędy.  
  
-   Funkcje Członkowskie nie mogą jednak mieć.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy i struktury](../cpp/classes-and-structs-cpp.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [Klasy](../cpp/class-cpp.md)   
 [struct](../cpp/struct-cpp.md)