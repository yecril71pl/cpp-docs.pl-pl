---
title: Konstruktory (C++)
ms.date: 11/19/2019
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
ms.openlocfilehash: 6cdf6241542c3f93484097c65015181a91647d49
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246618"
---
# <a name="constructors-c"></a>Konstruktory (C++)

Aby dostosować sposób inicjowania składowych klasy lub wywołania funkcji po utworzeniu obiektu klasy, zdefiniuj *konstruktora*. Konstruktor ma taką samą nazwę jak Klasa i nie zwraca wartości. Można zdefiniować dowolną liczbę przeciążonych konstruktorów, aby dostosować inicjalizację na różne sposoby. Zazwyczaj konstruktory mają publicznego ułatwienia dostępu, tak aby kod poza hierarchią klasy lub hierarchii dziedziczenia mógł tworzyć obiekty klasy. Ale można również zadeklarować konstruktora jako **Protected** lub **Private**.

Konstruktory mogą opcjonalnie przyjmować listę init elementu członkowskiego. Jest to bardziej wydajny sposób na zainicjowanie elementów członkowskich klasy niż przypisanie wartości w treści konstruktora. Poniższy przykład przedstawia klasę `Box` z trzema przeciążonymi konstruktorami. Ostatnie dwie listy init elementu członkowskiego use:

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

W przypadku deklarowania instancji klasy kompilator wybiera konstruktora, który ma zostać wywołany na podstawie reguł rozpoznania przeciążenia:

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

- Konstruktory mogą być zadeklarowane jako **inline**, [Explicit](#explicit_constructors), **zaprzyjaźnione** lub [constexpr](#constexpr_constructors).
- Konstruktor może zainicjować obiekt, który został zadeklarowany jako **const**, **volatile** lub **const volatile**. Obiekt **zostanie stały po zakończeniu konstruktora** .
- Aby zdefiniować konstruktora w pliku implementacji, nadaj mu nazwę kwalifikowaną, tak jak w przypadku każdej innej funkcji członkowskiej: `Box::Box(){...}`.

## <a name="member_init_list"></a>Listy inicjatorów składowych

Konstruktor może opcjonalnie mieć listę inicjatorów składowych, która inicjuje składowe klasy przed wykonaniem treści konstruktora. (Należy zauważyć, że lista inicjatorów składowych nie jest taka sama jak lista *inicjatorów* typu [std:: initializer_list\<t >](../standard-library/initializer-list-class.md)).

Użycie listy inicjatorów składowych jest preferowane przez przypisanie wartości w treści konstruktora, ponieważ bezpośrednio Inicjuje element członkowski. W poniższym przykładzie przedstawiono listę inicjatorów składowych składającą się ze wszystkich wyrażeń **identyfikatora (argumentu)** po dwukropku:

```cpp
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

Identyfikator musi odwoływać się do elementu członkowskiego klasy; zostanie ona zainicjowana przy użyciu wartości argumentu. Argument może być jednym z parametrów konstruktora, wywołania funkcji lub [std:: initializer_list\<t >](../standard-library/initializer-list-class.md).

składowe **const** i elementy członkowskie typu referencyjnego muszą być zainicjowane na liście inicjatorów elementów członkowskich.

Wywołania sparametryzowanych konstruktorów klas podstawowych powinny być wprowadzane na liście inicjatorów, aby upewnić się, że klasa bazowa jest w pełni zainicjowana przed wykonaniem konstruktora pochodnego.

## <a name="default_constructors"></a>Konstruktory domyślne

*Konstruktory domyślne* nie mają zwykle żadnych parametrów, ale mogą mieć parametry z wartościami domyślnymi.

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

Konstruktory domyślne są jedną z [specjalnych funkcji Członkowskich](special-member-functions.md). Jeśli w klasie nie zadeklarowano konstruktorów, kompilator dostarcza niejawnego **wbudowanego** konstruktora domyślnego.

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

Jeśli korzystasz z niejawnego konstruktora domyślnego, pamiętaj o zainicjowaniu elementów członkowskich w definicji klasy, jak pokazano w poprzednim przykładzie. Bez tych inicjatorów elementy członkowskie byłyby niezainicjowane, a wywołanie Volume () wygenerowało wartość bezużyteczną. Ogólnie rzecz biorąc, dobrym sposobem jest zainicjowanie elementów członkowskich w ten sposób nawet wtedy, gdy nie polega na niejawnym konstruktorze domyślnym.

Można uniemożliwić kompilatorowi generowanie niejawnego konstruktora domyślnego przez zdefiniowanie go jako [usuniętego](#explicitly_defaulted_and_deleted_constructors):

```cpp
    // Default constructor
    Box() = delete;
```

Konstruktor domyślny wygenerowany przez kompilator zostanie zdefiniowany jako usunięty, jeśli którykolwiek element członkowski klasy nie jest domyślny-konstrukcyjną. Na przykład wszystkie elementy członkowskie typu klasy i ich elementy członkowskie typu klasy muszą mieć domyślny Konstruktor i destruktory, które są dostępne. Wszystkie elementy członkowskie danych typu referencyjnego, a także składowe **const** muszą mieć domyślny inicjator składowej.

Gdy wywołujesz Konstruktor domyślny wygenerowany przez kompilator i spróbujesz użyć nawiasów, zostanie wygenerowane Ostrzeżenie:

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

Jest to przykład problemu najbardziej irytującej interpretacji składni (Most Vexing Parse). Ponieważ wyrażenie przykładowe może być interpretowane jako deklaracja funkcji lub wywołanie konstruktora domyślnego i ponieważ analizatory składni języka C++ promują deklaracje w stosunku do innych obiektów, wyrażenie jest traktowane jako deklaracja funkcji. Aby uzyskać więcej informacji, zobacz [większość uciążliwych Parse](https://en.wikipedia.org/wiki/Most_vexing_parse).

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

Aby uzyskać więcej informacji, zobacz [inicjatory](initializers.md).

## <a name="copy_and_move_constructors"></a>Kopiuj konstruktory

*Konstruktor kopiujący* inicjuje obiekt kopiując wartości elementu członkowskiego z obiektu tego samego typu. Jeśli składowe klasy są wszystkie typy proste, takie jak wartości skalarne, Konstruktor kopiujący generowany przez kompilator jest wystarczający i nie trzeba definiować własnych. Jeśli Klasa wymaga bardziej złożonej inicjalizacji, należy zaimplementować niestandardowy Konstruktor kopiujący. Na przykład, jeśli element członkowski klasy jest wskaźnikiem, należy zdefiniować Konstruktor kopiujący, aby przydzielić nową pamięć i skopiować wartości z innego obiektu wskazywanego przez. Konstruktor kopiujący wygenerowany przez kompilator po prostu kopiuje wskaźnik, tak aby nowy wskaźnik nadal wskazywał lokalizację w pamięci.

Konstruktor kopiujący może mieć jeden z następujących sygnatur:

```cpp
    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

Podczas definiowania konstruktora kopiującego należy również zdefiniować operator przypisania kopiowania (=). Aby uzyskać więcej informacji, zobacz [przypisania](assignment.md) i [kopiowania konstruktorów oraz kopiowanie operatorów przypisania](copy-constructors-and-copy-assignment-operators-cpp.md).

Można zapobiec kopiowaniu obiektu przez zdefiniowanie konstruktora kopiującego jako usuniętego:

```cpp
    Box (const Box& other) = delete;
```

Próba skopiowania obiektu powoduje błąd *C2280: próbuje odwołać się do usuniętej funkcji*.

## <a name="move_constructors"></a>Przenoszenie konstruktorów

*Konstruktor przenoszący* jest specjalną funkcją członkowską, która przenosi własność istniejących danych obiektu do nowej zmiennej bez kopiowania oryginalnych danych. Przyjmuje odwołanie rvalue jako pierwszy parametr, a wszystkie dodatkowe parametry muszą mieć wartości domyślne. Konstruktory przenoszenia mogą znacząco zwiększyć wydajność programu podczas przekazywania dużych obiektów.

```cpp
Box(Box&& other);
```

Kompilator wybiera Konstruktor przenoszący w pewnych sytuacjach, gdzie obiekt jest inicjowany przez inny obiekt tego samego typu, który ma zostać zniszczony i nie potrzebuje już zasobów. W poniższym przykładzie pokazano jeden przypadek, gdy Konstruktor przenoszenia jest wybierany przez rozpoznanie przeciążenia. W konstruktorze, który wywołuje `get_Box()`, zwracana wartość to *XValue* (wartość wygaśnięcia). Nie jest ona przypisana do żadnej zmiennej i w związku z tym wkrótce wyjdzie poza zakres. Aby dostarczyć motywację do tego przykładu, przypuśćmy do pudełka duży wektor ciągów, które reprezentują jego zawartość. Zamiast kopiować wektor i jego ciągi, Konstruktor przenoszenia "wykraść" z wartości "Box", tak aby wektor należał teraz do nowego obiektu. Wywołanie `std::move` jest konieczne, ponieważ klasy `vector` i `string` implementują własne konstruktory przenoszenia.

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
    void Get_Contents()
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
    b2.Get_Contents(); // Prove that we have all the values

    char ch;
    cin >> ch; // keep window open
    return 0;
}
```

Jeśli Klasa nie definiuje konstruktora przenoszenia, kompilator generuje niejawny, jeśli nie istnieje zadeklarowany przez użytkownika Konstruktor kopiujący, operator przypisania kopiowania, operator przypisania przenoszenia lub destruktor. Jeśli nie zdefiniowano jawnego lub niejawnego konstruktora przenoszącego, operacje w przeciwnym razie używają konstruktora kopiującego. Jeśli Klasa deklaruje Konstruktor przenoszenia lub operator przypisania przenoszenia, niejawnie zadeklarowany Konstruktor kopiujący jest zdefiniowany jako usunięty.

Niejawnie zadeklarowany Konstruktor przenoszący został zdefiniowany jako usunięty, jeśli którykolwiek element członkowski, który jest typem klasy nie ma destruktora lub kompilator nie może określić konstruktora, który ma być używany dla operacji przenoszenia.

Aby uzyskać więcej informacji na temat pisania nieuproszczonego konstruktora przenoszenia, zobacz [przenoszenie konstruktorów i operatory przypisania przenoszenia (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

## <a name="explicitly_defaulted_and_deleted_constructors"></a>Konstruktory jawnie domyślne i usunięte

Można jawnie *domyślne* konstruktory kopiowania, konstruktory domyślne, konstruktory przenoszenia, operatory przypisania kopii, operatory przypisania przenoszenia i destruktory. Można jawnie *usunąć* wszystkie specjalne funkcje składowe.

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

Aby uzyskać więcej informacji, zobacz [jawnie domyślne i usunięte funkcje](../cpp/explicitly-defaulted-and-deleted-functions.md).

## <a name="constexpr_constructors"></a>Konstruktory constexpr

Konstruktor może być zadeklarowany jako [constexpr](constexpr-cpp.md) , jeśli

- jest zadeklarowany jako domyślny lub w przeciwnym razie spełnia wszystkie warunki [funkcji constexpr](constexpr-cpp.md#constexpr_functions) w ogóle;
- Klasa nie ma wirtualnych klas bazowych;
- Każdy z parametrów jest [typem literału](trivial-standard-layout-and-pod-types.md#literal_types);
- treść nie jest funkcją try-Block;
- wszystkie niestatyczne składowe danych i podrzędne obiekty klasy bazowej są inicjowane;
- Jeśli Klasa to (a) Unia z składowymi Variant lub (b) ma anonimowe Unii, inicjowana jest tylko jeden z członków Unii;
- Każdy niestatyczny element członkowski danych typu klasy, a wszystkie obiekty podrzędne klasy podstawowej mają konstruktora constexpr

## <a name="init_list_constructors"></a>Konstruktory list inicjatorów

Jeśli Konstruktor przyjmuje wartość [std:: initializer_list\<t\>](../standard-library/initializer-list-class.md) jako parametr, a wszystkie inne parametry mają argumenty domyślne, ten Konstruktor zostanie wybrany w celu rozpoznania przeciążenia, gdy Klasa zostanie utworzona przy użyciu inicjowania bezpośredniego. Initializer_list można użyć do zainicjowania dowolnego elementu członkowskiego, który może go zaakceptować. Załóżmy na przykład, że Klasa Box (pokazana wcześniej) ma `std::vector<string>` składową `m_contents`. Można podać Konstruktor podobny do tego:

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

A następnie utwórz obiekty Box w następujący sposób:

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit_constructors"></a>Konstruktory jawne

Jeśli klasa ma Konstruktor z pojedynczym parametrem lub jeśli wszystkie parametry z wyjątkiem jednego mają wartość domyślną, typ parametru może być niejawnie konwertowany na typ klasy. Na przykład jeśli Klasa `Box` ma Konstruktor podobny do tego:

```cpp
Box(int size): m_width(size), m_length(size), m_height(size){}
```

Możliwe jest zainicjowanie pola w następujący sposób:

```cpp
Box b = 42;
```

Lub Przekaż liczbę całkowitą do funkcji, która przyjmuje pole:

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

Takie Konwersje mogą być przydatne w niektórych przypadkach, ale częściej mogą prowadzić do delikatnych, ale poważniejszych błędów w kodzie. Ogólnie rzecz biorąc, należy użyć słowa kluczowego **Explicit** dla konstruktora (i operatorów zdefiniowanych przez użytkownika), aby zapobiec niejawnej konwersji typów:

```cpp
explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

Gdy Konstruktor jest jawny, ten wiersz powoduje błąd kompilatora: `ShippingOrder so(42, 10.8);`.  Aby uzyskać więcej informacji, zobacz [konwersje typów zdefiniowane przez użytkownika](../cpp/user-defined-type-conversions-cpp.md).

## <a name="order_of_construction"></a>Kolejność konstrukcji

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

Konstruktor klasy pochodnej zawsze wywołuje konstruktora klasy bazowej, tak aby mógł polegać na całkowicie skonstruowanych klasach bazowych, zanim wszelkie dodatkowe prace zostaną wykonane. Konstruktory klas bazowych są wywoływane w kolejności wyprowadzenia — na przykład, jeśli `ClassA` pochodzi od `ClassB`, który pochodzi od `ClassC`, Konstruktor `ClassC` jest wywoływany jako pierwszy, a następnie Konstruktor `ClassB`, a następnie Konstruktor `ClassA`.

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

### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>Konstruktory dla klas, które mają wiele dziedziczeń

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

## <a name="delegating_constructors"></a>Delegowanie konstruktorów

*Konstruktor delegowania* wywołuje innego konstruktora w tej samej klasie, aby wykonać część pracy inicjalizacji. Jest to przydatne w przypadku wielu konstruktorów, które wszystkie muszą wykonywać podobne prace. Można napisać podstawową logikę w jednym konstruktorze i wywołać ją od innych. W poniższym prostym przykładzie pole (int) deleguje swoją służbę do pola (int, int, int):

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

Obiekt utworzony przez konstruktory jest w pełni zainicjowany natychmiast po zakończeniu wszelkich konstruktorów. Aby uzyskać więcej informacji, zobacz [delegowanie konstruktorów](../cpp/delegating-constructors.md).

## <a name="inheriting_constructors"></a>Konstruktory dziedziczenia (C++ 11)

Klasa pochodna może dziedziczyć konstruktory z bezpośredniej klasy podstawowej przy użyciu deklaracji **using** , jak pokazano w następującym przykładzie:

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

**Visual Studio 2017 i nowsze**: instrukcja **using** w **/std: c++ 17** tryb umożliwia zakres wszystkich konstruktorów z klasy bazowej, z wyjątkiem tych, które mają identyczny podpis do konstruktorów w klasie pochodnej. Ogólnie rzecz biorąc, najlepszym rozwiązaniem jest użycie konstruktorów dziedziczenia, gdy Klasa pochodna nie deklaruje nowych elementów członkowskich lub konstruktorów danych. Zobacz również [ulepszenia w programie Visual Studio 2017 w wersji 15,7](https://docs.microsoft.com/cpp/overview/cpp-conformance-improvements?view=vs-2017#improvements_157).

::: moniker-end

Szablon klasy może dziedziczyć wszystkich konstruktorów z argumentu typu, jeśli ten typ określa klasę bazową:

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};
```

Klasa pochodna nie może dziedziczyć z wielu klas bazowych, jeśli te klasy bazowe mają takie same sygnatury.

## <a name="constructors_in_composite_classes"></a>Konstruktory i klasy złożone

Klasy, które zawierają składowe typu klasy, są znane jako *klasy złożone*. Gdy jest tworzona składowa typu klasa klasy złożonej, konstruktor jest wywoływany przed konstruktorem tej klasy. Gdy klasa zamknięta nie ma domyślnego konstruktora, należy użyć listy inicjalizacji w konstruktorze klasy złożonej. W poprzednim `StorageBox` przykładzie, jeśli zmienisz typ zmiennej składowej `m_label` na nową klasę `Label`, musisz wywołać zarówno konstruktora klasy bazowej, jak i zainicjować zmienną `m_label` w konstruktorze `StorageBox`:

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

- [Kopiuj konstruktory i skopiuj operatory przypisania](copy-constructors-and-copy-assignment-operators-cpp.md)
- [Przenieś konstruktory i operatory przypisania przenoszenia](move-constructors-and-move-assignment-operators-cpp.md)
- [Delegowanie konstruktorów](delegating-constructors.md)

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](classes-and-structs-cpp.md)
