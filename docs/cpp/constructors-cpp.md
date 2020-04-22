---
title: Konstruktory (C++)
ms.date: 12/27/2019
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
ms.openlocfilehash: 4640bcf5f21bbe018a8744a6c5206bdd09509c98
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749646"
---
# <a name="constructors-c"></a>Konstruktory (C++)

Aby dostosować sposób inicjowania elementów członkowskich klasy lub wywołać funkcje podczas tworzenia obiektu klasy, należy zdefiniować *konstruktor*. Konstruktor ma taką samą nazwę jak klasa i nie ma wartości zwracanej. Można zdefiniować dowolną liczbę przeciążonych konstruktorów, ile potrzeba, aby dostosować inicjalizację na różne sposoby. Zazwyczaj konstruktory mają dostępność publiczną, dzięki czemu kod poza definicją klasy lub hierarchią dziedziczenia może tworzyć obiekty klasy. Ale można również zadeklarować konstruktora jako **chronione** lub **prywatne**.

Konstruktory opcjonalnie można podjąć init listy elementu członkowskiego. Jest to bardziej efektywny sposób inicjowania elementów członkowskich klasy niż przypisywanie wartości w treści konstruktora. W poniższym przykładzie pokazano klasę `Box` z trzech przeciążonych konstruktorów. Dwa ostatnie użyj init listy elementu członkowskiego:

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initialize a Box with equal dimensions (i.e. a cube)
    explicit Box(int i) : m_width(i), m_length(i), m_height(i) // member init list
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}

    int Volume() { return m_width * m_length * m_height; }

private:
    // Will have value of 0 when default constructor is called.
    // If we didn't zero-init here, default constructor would
    // leave them uninitialized with garbage values.
    int m_width{ 0 };
    int m_length{ 0 };
    int m_height{ 0 };
};
```

Podczas deklarowania wystąpienia klasy kompilator wybiera konstruktora do wywołania na podstawie reguł rozpoznawania przeciążenia:

```cpp
int main()
{
    Box b; // Calls Box()

    // Using uniform initialization (preferred):
    Box b2 {5}; // Calls Box(int)
    Box b3 {5, 8, 12}; // Calls Box(int, int, int)

    // Using function-style notation:
    Box b4(2, 4, 6); // Calls Box(int, int, int)
}
```

- Konstruktory mogą być zadeklarowane jako **wbudowane,** [jawne,](#explicit_constructors) **przyjaciel** lub [constexpr](#constexpr_constructors).
- Konstruktor może zainicjować obiekt, który został zadeklarowany jako **const**, **volatile** lub **const volatile**. Obiekt staje się **const** po zakończeniu konstruktora.
- Aby zdefiniować konstruktora w pliku implementacji, nadaj `Box::Box(){...}`mu nazwę kwalifikowaną, tak jak w przypadku każdej innej funkcji elementu członkowskiego: .

## <a name="member-initializer-lists"></a><a name="member_init_list"></a>Listy inicjatorów elementów członkowskich

Konstruktor może opcjonalnie mieć listę inicjatora elementu członkowskiego, który inicjuje członków klasy przed wykonaniem obiektu konstruktora. (Należy zauważyć, że lista inicjatora elementu członkowskiego nie jest tym samym, co *lista inicjatora* typu [\<std::initializer_list T>](../standard-library/initializer-list-class.md).)

Za pomocą listy inicjatora elementu członkowskiego jest preferowane niż przypisywanie wartości w treści konstruktora, ponieważ bezpośrednio inicjuje element członkowski. W poniższym przykładzie przedstawiono listę inicjatora elementu członkowskiego składa się ze wszystkich wyrażeń **identyfikator(argument)** po dwukropku:

```cpp
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

Identyfikator musi odnosić się do elementu członkowskiego klasy; jest inicjowany z wartością argumentu. Argument może być jednym z parametrów konstruktora, wywołaniem funkcji lub [std::initializer_list\<T>](../standard-library/initializer-list-class.md).

**const** elementów członkowskich i członków typu odwołania musi być zainicjowany na liście inicjatora elementu członkowskiego.

Wywołania do sparametryzowanych konstruktorów klas podstawowych powinny być wykonane na liście inicjatora, aby upewnić się, że klasa podstawowa jest w pełni zainicjowana przed wykonaniem konstruktora pochodnego.

## <a name="default-constructors"></a><a name="default_constructors"></a>Konstruktory domyślne

*Domyślne konstruktory* zazwyczaj nie mają parametrów, ale mogą mieć parametry z wartościami domyślnymi.

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

Domyślne konstruktory są jedną ze [specjalnych funkcji elementów członkowskich](special-member-functions.md). Jeśli żadne konstruktory nie są zadeklarowane w klasie, kompilator zapewnia niejawne **wbudowany** konstruktor domyślny.

```cpp
#include <iostream>
using namespace std;

class Box {
public:
    int Volume() {return m_width * m_height * m_length;}
private:
    int m_width { 0 };
    int m_height { 0 };
    int m_length { 0 };
};

int main() {
    Box box1; // Invoke compiler-generated constructor
    cout << "box1.Volume: " << box1.Volume() << endl; // Outputs 0
}
```

Jeśli polegasz na niejawnym konstruktorze domyślnym, należy zainicjować elementy członkowskie w definicji klasy, jak pokazano w poprzednim przykładzie. Bez tych inicjatorów, elementy członkowskie będą niezainicjowane i Volume() wywołanie spowoduje wartość śmieci. Ogólnie rzecz biorąc jest dobrą praktyką, aby zainicjować elementy członkowskie w ten sposób, nawet wtedy, gdy nie polega na niejawnym konstruktora domyślnego.

Można uniemożliwić kompilatorowi wygenerowanie domyślnego konstruktora niejawnego, definiując go jako [usuniętego:](#explicitly_defaulted_and_deleted_constructors)

```cpp
    // Default constructor
    Box() = delete;
```

Domyślny konstruktor wygenerowany przez kompilator zostanie zdefiniowany jako usunięty, jeśli wszystkie elementy członkowskie klasy nie są konstruowane domyślnie. Na przykład wszystkie elementy członkowskie typu klasy i ich członków typu klasy, musi mieć domyślny konstruktor i destruktory, które są dostępne. Wszystkie elementy członkowskie danych typu odwołania, a także **const** członków musi mieć domyślny inicjatora elementu członkowskiego.

Podczas wywoływania domyślnego konstruktora wygenerowanego przez kompilator i próby użycia nawiasów jest wydawane ostrzeżenie:

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

Jest to przykład problemu najbardziej irytującej interpretacji składni (Most Vexing Parse). Ponieważ wyrażenie przykładowe może być interpretowane jako deklaracja funkcji lub wywołanie konstruktora domyślnego i ponieważ analizatory składni języka C++ promują deklaracje w stosunku do innych obiektów, wyrażenie jest traktowane jako deklaracja funkcji. Aby uzyskać więcej informacji, zobacz [Najbardziej vexing analizowania](https://en.wikipedia.org/wiki/Most_vexing_parse).

Jeśli zadeklarowano jakiekolwiek konstruktory inne niż domyślne, kompilator nie udostępnia domyślnego konstruktora:

```cpp
class Box {
public:
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height){}
private:
    int m_width;
    int m_length;
    int m_height;

};

int main(){

    Box box1(1, 2, 3);
    Box box2{ 2, 3, 4 };
    Box box3; // C2512: no appropriate default constructor available
}
```

Jeśli klasa nie ma domyślnego konstruktora, nie można utworzyć tablicy obiektów tej klasy przy użyciu wyłącznie składni z nawiasami kwadratowymi. Na przykład, biorąc pod uwagę poprzedni blok kodu, tablicy pól nie można zadeklarować w ten sposób:

```cpp
Box boxes[3]; // C2512: no appropriate default constructor available
```

Można jednak użyć zestawu list inicjatorów, aby zainicjować tablicę obiektów Box:

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

Aby uzyskać więcej informacji, zobacz [Inicjatorzy](initializers.md).

## <a name="copy-constructors"></a><a name="copy_and_move_constructors"></a>Konstruktory kopiowania

*Konstruktor kopii* inicjuje obiekt, kopiując wartości elementów członkowskich z obiektu tego samego typu. Jeśli elementy członkowskie klasy są wszystkie proste typy, takie jak wartości skalarne, konstruktor kopii generowany przez kompilator jest wystarczająca i nie trzeba definiować własne. Jeśli klasa wymaga bardziej złożonego inicjowania, należy zaimplementować konstruktora kopii niestandardowej. Na przykład jeśli element członkowski klasy jest wskaźnikiem, należy zdefiniować konstruktor kopii, aby przydzielić nową pamięć i skopiować wartości z obiektu spiczastego innego. Konstruktor kopii generowany przez kompilator po prostu kopiuje wskaźnik, dzięki czemu nowy wskaźnik nadal wskazuje lokalizację pamięci drugiej strony.

Konstruktor kopii może mieć jeden z tych podpisów:

```cpp
    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

Podczas definiowania konstruktora kopii należy również zdefiniować operator przypisania kopii (=). Aby uzyskać więcej informacji, zobacz [Konstruktory przypisywania](assignment.md) i [kopiowania oraz operatory przypisywania kopiowania](copy-constructors-and-copy-assignment-operators-cpp.md).

Można zapobiec kopiowaniu obiektu, definiując konstruktor kopii jako usunięty:

```cpp
    Box (const Box& other) = delete;
```

Próba skopiowania obiektu powoduje błąd *C2280: próba odwołania się do usuniętej funkcji*.

## <a name="move-constructors"></a><a name="move_constructors"></a>Konstruktory przenoszenia

*Konstruktor przenoszenia* jest specjalną funkcją elementu członkowskiego, która przenosi własność danych istniejącego obiektu do nowej zmiennej bez kopiowania oryginalnych danych. Przyjmuje odwołanie rvalue jako pierwszy parametr, a wszelkie dodatkowe parametry muszą mieć wartości domyślne. Konstruktory przenoszenia mogą znacznie zwiększyć wydajność programu podczas przekazywania wokół dużych obiektów.

```cpp
Box(Box&& other);
```

Kompilator wybiera konstruktora przenoszenia w niektórych sytuacjach, gdy obiekt jest inicjowany przez inny obiekt tego samego typu, który ma zostać zniszczony i nie potrzebuje już swoich zasobów. Poniższy przykład pokazuje jeden przypadek, gdy konstruktor przenoszenia jest zaznaczony przez rozdzielczość przeciążenia. W konstruktorze, który wywołuje, `get_Box()`zwracana wartość jest *xvalue* (eXpiring wartość). Nie jest przypisany do żadnej zmiennej i dlatego ma zamiar wyjść poza zakres. Aby zapewnić motywację dla tego przykładu, dajmy Box duży wektor ciągów, które reprezentują jego zawartość. Zamiast kopiowania wektora i jego ciągów, konstruktor przenoszenia "kradnie" go z wygasającej wartości "box", dzięki czemu wektor należy teraz do nowego obiektu. Wywołanie `std::move` jest wszystko, co jest `vector` `string` potrzebne, ponieważ zarówno i klasy implementują własne konstruktory przenoszenia.

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
using namespace std;

class Box {
public:
    Box() { std::cout << "default" << std::endl; }
    Box(int width, int height, int length)
       : m_width(width), m_height(height), m_length(length)
    {
        std::cout << "int,int,int" << std::endl;
    }
    Box(Box& other)
       : m_width(other.m_width), m_height(other.m_height), m_length(other.m_length)
    {
        std::cout << "copy" << std::endl;
    }
    Box(Box&& other) : m_width(other.m_width), m_height(other.m_height), m_length(other.m_length)
    {
        m_contents = std::move(other.m_contents);
        std::cout << "move" << std::endl;
    }
    int Volume() { return m_width * m_height * m_length; }
    void Add_Item(string item) { m_contents.push_back(item); }
    void Print_Contents()
    {
        for (const auto& item : m_contents)
        {
            cout << item << " ";
        }
    }
private:
    int m_width{ 0 };
    int m_height{ 0 };
    int m_length{ 0 };
    vector<string> m_contents;
};

Box get_Box()
{
    Box b(5, 10, 18); // "int,int,int"
    b.Add_Item("Toupee");
    b.Add_Item("Megaphone");
    b.Add_Item("Suit");

    return b;
}

int main()
{
    Box b; // "default"
    Box b1(b); // "copy"
    Box b2(get_Box()); // "move"
    cout << "b2 contents: ";
    b2.Print_Contents(); // Prove that we have all the values

    char ch;
    cin >> ch; // keep window open
    return 0;
}
```

Jeśli klasa nie definiuje konstruktora przenoszenia, kompilator generuje niejawny, jeśli nie ma konstruktora kopii zadeklarowanego przez użytkownika, operatora przypisania kopiowania, operatora przenoszenia przydziału lub destruktora. Jeśli nie jawne lub niejawne przenieść konstruktora jest zdefiniowany, operacje, które w przeciwnym razie użyć konstruktora przenieść zamiast tego. Jeśli klasa deklaruje move konstruktora lub przenieść operator przypisania, niejawnie zadeklarowany konstruktor kopii jest zdefiniowany jako usunięty.

Niejawnie zadeklarowany konstruktor przenoszenia jest zdefiniowany jako usunięty, jeśli jakiekolwiek elementy członkowskie, które są typami klas, nie mają destruktora lub kompilatora nie może określić, który konstruktor ma być używany dla operacji przenoszenia.

Aby uzyskać więcej informacji na temat zapisywania nietrywialnego konstruktora przenoszenia, zobacz [Przenoszenie konstruktorów i operatorów przenoszenia przydziałów (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

## <a name="explicitly-defaulted-and-deleted-constructors"></a><a name="explicitly_defaulted_and_deleted_constructors"></a>Jawnie domyślnie i usunięte konstruktory

Można jawnie *domyślne* konstruktory kopiowania, konstruktory domyślne, konstruktory przenoszenia, operatory przypisywania kopiowania, przenosić operatory przydziałów i destruktory. Można jawnie *usunąć* wszystkie funkcje elementów członkowskich specjalnych.

```cpp
class Box
{
public:
    Box2() = delete;
    Box2(const Box2& other) = default;
    Box2& operator=(const Box2& other) = default;
    Box2(Box2&& other) = default;
    Box2& operator=(Box2&& other) = default;
    //...
};
```

Aby uzyskać więcej informacji, zobacz [Jawnie domyślne i usunięte funkcje](../cpp/explicitly-defaulted-and-deleted-functions.md).

## <a name="constexpr-constructors"></a><a name="constexpr_constructors"></a>konstruktory constexpr

Konstruktor może zostać zgłoszony jako [constexpr,](constexpr-cpp.md) jeśli

- jest albo zadeklarowany jako domyślny, albo spełnia wszystkie warunki [dla funkcji constexpr](constexpr-cpp.md#constexpr_functions) w ogóle;
- klasa nie ma wirtualnych klas podstawowych;
- każdy z parametrów jest [typem dosłownym;](trivial-standard-layout-and-pod-types.md#literal_types)
- ciało nie jest funkcją try-block;
- wszystkie niestatyczne elementy członkowskie danych i obiekty podrzędne klasy podstawowej są inicjowane;
- jeśli klasa jest (a) związkiem posiadającym członków wariantu lub b) ma anonimowe związki, tylko jeden z członków związku jest inicjowany;
- każdy niestatyczny element członkowski danych typu klasy, a wszystkie podkategoraliczne obiekty klasy podstawowej mają konstruktor constexpr

## <a name="initializer-list-constructors"></a><a name="init_list_constructors"></a>Konstruktory listy inicjatorów

Jeśli konstruktor przyjmuje [std::initializer_list\<T\> ](../standard-library/initializer-list-class.md) jako parametr, a inne parametry mają domyślne argumenty, ten konstruktor zostanie wybrany w rozdzielczości przeciążenia, gdy klasa zostanie skonkrzetowana przez bezpośrednie inicjowanie. Za pomocą initializer_list można zainicjować dowolny element członkowski, który może go zaakceptować. Załóżmy na przykład, że klasa Box `std::vector<string>` `m_contents`(pokazana wcześniej) ma element członkowski . Konstruktora można podać w ten sposób:

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

A następnie utwórz obiekty Box w ten sposób:

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit-constructors"></a><a name="explicit_constructors"></a>Jawne konstruktory

Jeśli klasa ma konstruktora z jednym parametrem lub jeśli wszystkie parametry z wyjątkiem jednego mają wartość domyślną, typ parametru może być niejawnie konwertowany na typ klasy. Na przykład jeśli `Box` klasa ma konstruktora w ten sposób:

```cpp
Box(int size): m_width(size), m_length(size), m_height(size){}
```

Możliwe jest zainicjowanie boxa w ten sposób:

```cpp
Box b = 42;
```

Lub przekazać int do funkcji, która zajmuje Pole:

```cpp
class ShippingOrder
{
public:
    ShippingOrder(Box b, double postage) : m_box(b), m_postage(postage){}

private:
    Box m_box;
    double m_postage;
}
//elsewhere...
    ShippingOrder so(42, 10.8);
```

Takie konwersje mogą być przydatne w niektórych przypadkach, ale częściej mogą prowadzić do subtelnych, ale poważnych błędów w kodzie. Zgodnie z ogólną zasadą należy użyć **jawnego** słowa kluczowego w konstruktorze (i operatorach zdefiniowanych przez użytkownika), aby zapobiec tego rodzaju konwersji typu niejawnego:

```cpp
explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

Gdy konstruktor jest jawny, ten wiersz `ShippingOrder so(42, 10.8);`powoduje błąd kompilatora: .  Aby uzyskać więcej informacji, zobacz [Konwersje typu zdefiniowane przez użytkownika](../cpp/user-defined-type-conversions-cpp.md).

## <a name="order-of-construction"></a><a name="order_of_construction"></a>Kolejność budowy

Konstruktor wykonuje pracę w następującej kolejności:

1. Wywołuje klasę podstawową i konstruktory składowych w kolejności deklaracji.

1. Jeśli klasa jest pochodną wirtualnych klas bazowych, inicjuje wskaźniki wirtualnej bazy obiektu.

1. Jeśli klasa ma lub dziedziczy funkcje wirtualne, inicjuje wskaźniki funkcji wirtualnych obiektu. Wskaźniki funkcji wirtualnych wskazują na tabelę funkcji wirtualnych tej klasy, aby umożliwić poprawne powiązanie wywołań funkcji wirtualnych z kodem.

1. Wykonuje każdy kod w jego treści funkcji.

Poniższy przykład pokazuje kolejność, w której konstruktory klasy podstawowej i składowych są wywoływane w konstruktorze klasy pochodnej. Najpierw jest wywoływany podstawowy konstruktor, następnie składowe klas bazowych są inicjowane w kolejności, w której pojawiają się w deklaracji klasy, a na koniec jest wywoływany pochodny konstruktor.

```cpp
#include <iostream>

using namespace std;

class Contained1 {
public:
    Contained1() { cout << "Contained1 ctor\n"; }
};

class Contained2 {
public:
    Contained2() { cout << "Contained2 ctor\n"; }
};

class Contained3 {
public:
    Contained3() { cout << "Contained3 ctor\n"; }
};

class BaseContainer {
public:
    BaseContainer() { cout << "BaseContainer ctor\n"; }
private:
    Contained1 c1;
    Contained2 c2;
};

class DerivedContainer : public BaseContainer {
public:
    DerivedContainer() : BaseContainer() { cout << "DerivedContainer ctor\n"; }
private:
    Contained3 c3;
};

int main() {
    DerivedContainer dc;
}
```

Oto dane wyjściowe:

```Output
Contained1 ctor
Contained2 ctor
BaseContainer ctor
Contained3 ctor
DerivedContainer ctor
```

Konstruktor klasy pochodnej zawsze wywołuje konstruktora klasy bazowej, tak aby mógł polegać na całkowicie skonstruowanych klasach bazowych, zanim wszelkie dodatkowe prace zostaną wykonane. Konstruktory klasy podstawowej są wywoływane w `ClassA` kolejności wyprowadzania `ClassB`— na przykład, `ClassC` jeśli pochodzi od , `ClassB` który pochodzi od `ClassA` `ClassC`, konstruktor jest nazywany najpierw, następnie konstruktor, a następnie konstruktora.

Jeśli klasa bazowa nie ma domyślnego konstruktora, musisz podać parametry konstruktora klasy bazowej w konstruktorze klasy pochodnej:

```cpp
class Box {
public:
    Box(int width, int length, int height){
       m_width = width;
       m_length = length;
       m_height = height;
    }

private:
    int m_width;
    int m_length;
    int m_height;
};

class StorageBox : public Box {
public:
    StorageBox(int width, int length, int height, const string label&) : Box(width, length, height){
        m_label = label;
    }
private:
    string m_label;
};

int main(){

    const string aLabel = "aLabel";
    StorageBox sb(1, 2, 3, aLabel);
}
```

Jeśli konstruktor zgłasza wyjątek, kolejność zniszczenia jest odwrotna do kolejności konstrukcji:

1. Kod w treści funkcji konstruktora jest rozwinięty.

1. Klasa podstawowa i obiekty składowe są usuwane w kolejności odwrotnej do deklarowania.

1. Jeśli konstruktor nie jest delegujący, wszystkie w pełni skonstruowane obiekty i składowe klasy podstawowej zostaną zniszczone. Jednak ponieważ sam obiekt nie jest w pełni skonstruowany, destruktor nie zostanie uruchomiony.

## <a name="derived-constructors-and-extended-aggregate-initialization"></a><a name="extended_aggregate"></a>Konstruktory pochodne i inicjalizacja agregacji rozszerzonej

Jeśli konstruktor klasy podstawowej jest niepubliczny, ale dostępny dla klasy pochodnej, w obszarze **/std:c++17** w trybie Visual Studio 2017 i nowszych nie można użyć pustych nawiasów klamrowych do zainicjowania obiektu typu pochodnego.

Poniższy przykład przedstawia zachowanie konformanta języka C++14:

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {};

Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // OK in C++14: Calls Derived::Derived()
               // which can call Base ctor.
```

W języku C++ `Derived` 17 jest teraz uważany za typ agregacji. Oznacza to, że `Base` inicjowanie za pośrednictwem prywatnego konstruktora domyślnego odbywa się bezpośrednio, jako część rozszerzonej reguły inicjowania agregacji. Wcześniej `Base` konstruktor prywatny został wywołany za pośrednictwem `Derived` konstruktora i zakończyło się pomyślnie z powodu deklaracji znajomego.

W poniższym przykładzie przedstawiono zachowanie języka C++17 w programie Visual Studio 2017 i później w trybie **/std:c++17:**

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {
    Derived() {} // add user-defined constructor
                 // to call with {} initialization
};

Derived d1; // OK. No aggregate init involved.

Derived d2 {}; // error C2248: 'Base::Base': cannot access
               // private member declared in class 'Base'
```

### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>Konstruktory klas, które mają wielokrotne dziedziczenie

Jeśli klasa jest pochodną wielu klas bazowych, konstruktory klas bazowych są wywoływane w kolejności, w której są wymienione w deklaracji klasy pochodnej:

```cpp
#include <iostream>
using namespace std;

class BaseClass1 {
public:
    BaseClass1() { cout << "BaseClass1 ctor\n"; }
};
class BaseClass2 {
public:
    BaseClass2() { cout << "BaseClass2 ctor\n"; }
};
class BaseClass3 {
public:
    BaseClass3() { cout << "BaseClass3 ctor\n"; }
};
class DerivedClass : public BaseClass1,
                     public BaseClass2,
                     public BaseClass3
                     {
public:
    DerivedClass() { cout << "DerivedClass ctor\n"; }
};

int main() {
    DerivedClass dc;
}
```

Powinny się wyświetlić poniższe dane wyjściowe:

```Output
BaseClass1 ctor
BaseClass2 ctor
BaseClass3 ctor
DerivedClass ctor
```

## <a name="delegating-constructors"></a><a name="delegating_constructors"></a>Delegowanie konstruktorów

*Konstruktor delegowania* wywołuje inny konstruktor w tej samej klasie, aby wykonać niektóre pracy inicjowania. Jest to przydatne, gdy masz wiele konstruktorów, które wszystkie muszą wykonywać podobną pracę. Można napisać logikę główną w jednym konstruktorze i wywołać go od innych. W poniższym trywialnym przykładzie Box(int) deleguje swoją pracę do Box(int,int,int):

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initialize a Box with equal dimensions (i.e. a cube)
    Box(int i) :  Box(i, i, i);  // delegating constructor
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
    //... rest of class as before
};
```

Obiekt utworzony przez konstruktory jest w pełni zainicjowany natychmiast po zakończeniu wszelkich konstruktorów. Aby uzyskać więcej informacji, zobacz [Delegowanie konstruktorów](../cpp/delegating-constructors.md).

## <a name="inheriting-constructors-c11"></a><a name="inheriting_constructors"></a>Konstruktory dziedziczące (C++11)

Klasa pochodna może dziedziczyć konstruktorów z bezpośredniej klasy **podstawowej** przy użyciu using deklaracji, jak pokazano w poniższym przykładzie:

```cpp
#include <iostream>
using namespace std;

class Base
{
public:
    Base() { cout << "Base()" << endl; }
    Base(const Base& other) { cout << "Base(Base&)" << endl; }
    explicit Base(int i) : num(i) { cout << "Base(int)" << endl; }
    explicit Base(char c) : letter(c) { cout << "Base(char)" << endl; }

private:
    int num;
    char letter;
};

class Derived : Base
{
public:
    // Inherit all constructors from Base
    using Base::Base;

private:
    // Can't initialize newMember from Base constructors.
    int newMember{ 0 };
};

int main()
{
    cout << "Derived d1(5) calls: ";
    Derived d1(5);
    cout << "Derived d1('c') calls: ";
    Derived d2('c');
    cout << "Derived d3 = d2 calls: " ;
    Derived d3 = d2;
    cout << "Derived d4 calls: ";
    Derived d4;
}

/* Output:
Derived d1(5) calls: Base(int)
Derived d1('c') calls: Base(char)
Derived d3 = d2 calls: Base(Base&)
Derived d4 calls: Base()*/
```

::: moniker range=">=vs-2017"

**Visual Studio 2017 i nowsze:** **Using** instrukcji w **trybie /std:c++17** wprowadza do zakresu wszystkie konstruktory z klasy podstawowej, z wyjątkiem tych, które mają identyczny podpis do konstruktorów w klasie pochodnej. Ogólnie rzecz biorąc najlepiej jest użyć konstruktorów dziedziczenia, gdy klasa pochodna deklaruje żadnych nowych elementów członkowskich danych lub konstruktorów. Zobacz też [ulepszenia w programie Visual Studio 2017 w wersji 15.7](https://docs.microsoft.com/cpp/overview/cpp-conformance-improvements?view=vs-2017#improvements_157).

::: moniker-end

Szablon klasy może dziedziczyć wszystkie konstruktory z argumentu typu, jeśli ten typ określa klasę podstawową:

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};
```

Klasa pochodna nie może dziedziczyć z wielu klas podstawowych, jeśli te klasy podstawowe mają konstruktory, które mają identyczny podpis.

## <a name="constructors-and-composite-classes"></a><a name="constructors_in_composite_classes"></a>Konstruktory i klasy kompozytowe

Klasy, które zawierają elementy członkowskie typu klasy są znane jako *klasy złożone*. Gdy jest tworzona składowa typu klasa klasy złożonej, konstruktor jest wywoływany przed konstruktorem tej klasy. Gdy klasa zamknięta nie ma domyślnego konstruktora, należy użyć listy inicjalizacji w konstruktorze klasy złożonej. We wcześniejszym `StorageBox` przykładzie, jeśli zmienisz `m_label` typ zmiennej `Label` elementu członkowskiego na nową klasę, należy wywołać zarówno konstruktor klasy podstawowej, jak i zainicjować zmienną `m_label` w konstruktorze: `StorageBox`

```cpp
class Label {
public:
    Label(const string& name, const string& address) { m_name = name; m_address = address; }
    string m_name;
    string m_address;
};

class StorageBox : public Box {
public:
    StorageBox(int width, int length, int height, Label label)
        : Box(width, length, height), m_label(label){}
private:
    Label m_label;
};

int main(){
// passing a named Label
    Label label1{ "some_name", "some_address" };
    StorageBox sb1(1, 2, 3, label1);

    // passing a temporary label
    StorageBox sb2(3, 4, 5, Label{ "another name", "another address" });

    // passing a temporary label as an initializer list
    StorageBox sb3(1, 2, 3, {"myname", "myaddress"});
}
```

## <a name="in-this-section"></a>W tej sekcji

- [Konstruktory kopiowania i operatory przypisywania kopii](copy-constructors-and-copy-assignment-operators-cpp.md)
- [Przenoszenie konstruktorów i przenoszenie operatorów przydziałów](move-constructors-and-move-assignment-operators-cpp.md)
- [Delegowanie konstruktorów](delegating-constructors.md)

## <a name="see-also"></a>Zobacz też

[Klasy i struktury](classes-and-structs-cpp.md)
