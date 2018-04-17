---
title: Konstruktory (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/06/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5c6e99d76c7ff35e1d3be9db743f69b63e78490a
ms.sourcegitcommit: 770f6c4a57200aaa9e8ac6e08a3631a4b4bdca05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="constructors-c"></a>Konstruktory (C++)

Aby dostosować, jak są inicjowane elementów członkowskich klasy lub wywołania funkcji, gdy utworzono obiekt klasy, zdefiniuj *konstruktora*. Konstruktor ma taką samą nazwę jak klasa i brak wartości zwracanej. Można określić dowolną liczbę przeciążone konstruktory zgodnie z potrzebami, aby dostosować inicjowania na różne sposoby. Zazwyczaj konstruktorów mają powszechnej dostępności, aby tworzyć obiektów klasy kodu spoza hierarchii klas definicji lub dziedziczenia. Ale również można zadeklarować konstruktora jako **chronione** lub **prywatnej**.

Konstruktory opcjonalnie możliwe jest elementem członkowskim listy inicjowania. Jest to bardziej wydajny sposób inicjowania elementów członkowskich klasy niż przypisywanie wartości w treści konstruktora. W poniższym przykładzie przedstawiono klasę `Box` z trzema przeciążone konstruktory. Ostatnie dwa użyj listach inicjowania elementów członkowskich:

```cpp

class Box {
public:
    // Default constructor
    Box() {}

    // Initalize a Box with equal dimensions (i.e. a cube)
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

W deklaracji wystąpienia klasy, wybierze kompilator, który konstruktor do wywołania, zgodnie z regułami Rozpoznanie przeciążenia:

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

- Konstruktory może być zadeklarowana jako **wbudowanego**, [jawne](#explicit_constructors), **friend** lub [constexpr](#constexpr_constructors).
- Konstruktor można zainicjować obiektu, który został zadeklarowany jako **const**, **volatile** lub **stała nietrwałe**. Obiekt staje się **const** po zakończeniu działania konstruktora.
- Zdefiniowanie konstruktora w pliku z implementacją, nadaj mu nazwę kwalifikowaną tak jak w przypadku innych funkcji członkowskiej: `Box::Box(){...}`.

## <a name="member_init_list"></a> Listy inicjatorów elementu członkowskiego

Konstruktor opcjonalnie może mieć listy inicjatorów elementu członkowskiego, który inicjuje elementów członkowskich klasy przed wykonaniem treść konstruktora. (Należy pamiętać, że listy inicjatorów elementu członkowskiego nie jest odpowiednikiem *listy inicjatorów* typu [std::initializer_list\<T >](../standard-library/initializer-list-class.md).)

Przy użyciu listy inicjatora elementu członkowskiego jest preferowana przez przypisywanie wartości w treści konstruktora, ponieważ bezpośrednio inicjuje element członkowski. W poniższym przykładzie przedstawiono inicjator elementu członkowskiego zawiera wszystkie listy **identifier(argument)** wyrażenia po dwukropku:

```cpp
  
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

Identyfikator musi odwoływać się do elementu członkowskiego klasy; jest on zainicjowany z wartością argumentu. Argument może być jeden z parametrów konstruktora, wywołanie funkcji lub [std::initializer_list\<T >](../standard-library/initializer-list-class.md). 

**Const** elementów członkowskich i elementów członkowskich typu referencyjnego musi zostać zainicjowany na liście inicjatora elementu członkowskiego.

Wywołania konstruktorów klasy podstawowej sparametryzowane należy na liście inicjatora upewnij się, że klasa podstawowa jest w pełni zainicjowany przed wykonaniem konstruktora pochodnych.

## <a name="default_constructors"></a> Konstruktory domyślne

 *Konstruktory domyślne* zwykle nie mają parametrów, ale mogą mieć parametrów mających wartości domyślne.

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

Konstruktory domyślne są jednym z [specjalnych funkcji Członkowskich](special-member-functions.md). Jeśli ma konstruktorów został zadeklarowany w klasie, kompilator zapewnia niejawny **wbudowanego** domyślnego konstruktora.

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

Jeśli użytkownik korzysta z domyślnego niejawnego konstruktora, pamiętaj zainicjować elementów członkowskich w definicji klasy, jak pokazano w poprzednim przykładzie. Bez tych inicjatory elementy członkowskie będą niezainicjowanej i wywołanie Volume() zwróci wartość pamięci. Ogólnie rzecz biorąc jest dobrym rozwiązaniem inicjuje elementów członkowskich w ten sposób, nawet wtedy, gdy nie polegania na niejawne domyślnego konstruktora.

Możesz uniemożliwić kompilator generowania niejawnego domyślnego konstruktora, definiując go jako [usunięte](#explicitly_defaulted_and_deleted_constructors):

```cpp

    // Default constructor
    Box() = delete;

```

Generowane przez kompilator domyślnego konstruktora zostanie zdefiniowany jako usunięty, jeśli żadnych elementów członkowskich klasy nie umożliwia konstrukcji domyślne. Na przykład wszystkie elementy członkowskie typu klasy i ich elementy członkowskie typu klasy, musi mieć konstruktora domyślnego i destruktory, które są dostępne. Typ wszystkie elementy członkowskie danych odwołania, a także jako **const** elementy członkowskie muszą mieć domyślny inicjator elementu członkowskiego.

Gdy wywołanie generowane przez kompilator domyślnego konstruktora i spróbuj użyć nawiasów, pojawi się ostrzeżenie:

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

Jest to przykład problemu najbardziej irytującej interpretacji składni (Most Vexing Parse). Ponieważ wyrażenie przykładowe może być interpretowane jako deklaracja funkcji lub wywołanie konstruktora domyślnego i ponieważ analizatory składni języka C++ promują deklaracje w stosunku do innych obiektów, wyrażenie jest traktowane jako deklaracja funkcji. Aby uzyskać więcej informacji, zobacz [najbardziej Vexing przeanalizować](http://en.wikipedia.org/wiki/Most_vexing_parse).

Jeśli zadeklarowano jakiekolwiek konstruktory inne niż domyślne, kompilator nie udostępnia domyślnego konstruktora:

```cpp
class Box {
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height){}
};
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

Jednak aby zainicjować tablicę obiektów pole można użyć zestawu listy inicjatorów:

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

Aby uzyskać więcej informacji, zobacz [inicjatory](initializers.md).

## <a name="copy_and_move_constructors"></a> Kopiowanie konstruktorów

A *Konstruktor kopiujący* inicjuje obiekt przez skopiowanie wartości elementów członkowskich z tego samego typu obiektu. Jeśli klasa należą wszystkie typy proste, takie jak wartości skalarnych, Konstruktor kopiujący generowane przez kompilator jest wystarczająca, i nie trzeba definiować własne. Jeśli klasa wymaga bardziej złożonej inicjowania, następnie należy wdrożyć konstruktora kopiującego niestandardowych. Na przykład jeśli wskaźnik jest elementem członkowskim klasy należy zdefiniować konstruktora kopiującego można przydzielić nowej pamięci i skopiuj wartości z drugiej strony wskazywana do obiektu. Konstruktor kopiujący generowane przez kompilator po prostu kopiuje wskaźnika, dzięki czemu nadal nowy wskaźnik wskazuje lokalizację pamięci drugiego.

Konstruktor kopiujący może mieć jeden z tych podpisów:

```cpp

    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

Podczas definiowania konstruktora kopiującego, ale również zdefiniować kopia operatora przypisania (=). Aby uzyskać więcej informacji, zobacz [przypisania](assignment.md) i [kopiowanie konstruktorów i skopiuj operatory przypisania](copy-constructors-and-copy-assignment-operators-cpp.md).

Aby zapobiec obiektu kopiowane, definiując Konstruktor kopiujący jako usunięty:

```cpp
    Box (const Box& other) = delete;
```

Podjęto próbę kopiowania obiektu powoduje błąd *C2280: Podjęto próbę odwołania usunięta funkcja*.

## <a name="move_constructors"></a> Konstruktory przenoszenia
A *przenoszenie konstruktora* jest specjalną funkcją członkowską który przenosi własność istniejący obiekt danych do nowej zmiennej, bez kopiowania oryginalnych danych. Trwa odwołania do r-wartości jako pierwszy parametr, a wszelkie dodatkowe parametry muszą mieć wartości domyślnej. Konstruktory przenoszenia może znacznie zwiększyć wydajność programu podczas przekazywania dużych obiektów. Konstruktor przenoszący przyjmuje odwołanie do r-wartości jako pierwszy parametr. Inne parametry muszą mieć wartości domyślnej.

```cpp
Box(Box&& other);
```

Wybierze kompilator Konstruktor przenoszący w pewnych sytuacjach, gdy obiekt jest inicjowany przez inny obiekt tego samego typu, który ma zostać zniszczone i nie będzie już potrzebował go zasobów. W poniższym przykładzie przedstawiono jeden przypadek, w przypadku wybrania Konstruktor przenoszący przez rozpoznanie przeciążenia. Zmienna *pole* zwrócony przez get_Box() jest *xvalue* (wartość wygasające) której ma się znaleźć poza zakresem. Zapewnienie motywacją w tym przykładzie załóżmy nadaj pole dużych wektor ciągów reprezentujących jego zawartość. Zamiast kopiowania wektora i jego ciągów, Konstruktor przenoszenia "dokonuje" go z wygasłymi wartości "pola", aby wektora teraz należy do nowego obiektu. Wywołanie `std::move` to wszystko, która jest potrzebna, ponieważ zarówno `vector` i `string` klasy implementowania konstruktorów ich przenoszenia.

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

Jeśli klasa nie definiuje Konstruktor przenoszenia, kompilator generuje niejawne co, jeśli nie Konstruktor kopiujący zadeklarowanych przez użytkownika operatora przypisania kopii, operator przypisania przenoszenia ani destruktora. Jeśli żaden konstruktor przenoszenia jawnych ani niejawnych jest zdefiniowany, operacje, które w przeciwnym razie użyje Konstruktor przenoszący użyć konstruktora kopiującego. Jeśli klasa deklaruje Konstruktor przenoszenia lub operator przypisania przenoszenia, Konstruktor kopiujący niejawnie zadeklarowany jest zdefiniowany jako usunięty.

Konstruktor przenoszenia niejawnie zadeklarowany jest zdefiniowany jako usunięty, jeśli nie mają żadnych elementów członkowskich, które są typy klas destruktora lub kompilator nie może określić, które konstruktora do użycia dla operacji przenoszenia.

Aby uzyskać więcej informacji na temat pisania Konstruktor przenoszący nieuproszczony, zobacz [konstruktory przenoszenia i operatory przypisania przenoszenia (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

## <a name="explicitly_defaulted_and_deleted_constructors"></a> Jawnie domyślne i usunięte konstruktorów

Można jawnie *domyślne* kopiowanie konstruktorów, konstruktory domyślne, Przenieś konstruktorów, skopiuj operatory przypisania, Przenieś operatory przypisania i destruktory. Można jawnie *usunąć* wszystkie funkcje specjalne elementu członkowskiego.

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

Aby uzyskać więcej informacji, zobacz [jawnie ustawiana domyślnie i usunięte funkcje](../cpp/explicitly-defaulted-and-deleted-functions.md).

## <a name="constexpr_constructors"></a> Konstruktory constexpr

Konstruktor może być zadeklarowana jako [constexpr](constexpr-cpp.md) Jeśli

- jest albo deklarowane jako domyślną, albo też spełnia wszystkie warunki dla [funkcji constexpr](constexpr-cpp.md#constexpr_functions) ogólnie;
- Klasa nie ma żadnych wirtualnych klas podstawowych;
- Każdy z parametrów jest [literalne](trivial-standard-layout-and-pod-types.md#literal_types);
- treść nie jest blokiem try funkcji;
- wszystkie elementy członkowskie danych niestatycznych i obiekty podrzędne klasy podstawowej są inicjowane;
- Jeśli klasa jest () Unii członkowie wariantu lub (b) ma związki anonimowe, tylko jeden z elementów członkowskich Unii jest inicjowany;
- Każdy element członkowski danych niestatycznych typu klasy i wszystkie obiekty podrzędne klasy podstawowej ma konstruktora constexpr


## <a name="init_list_constructors"></a> Konstruktory listy inicjatora

Jeśli ma on konstruktora [std::initializer_list\<T\> ](../standard-library/initializer-list-class.md) jako jego parametr, a inne parametry mieć argumentów domyślnych, ten konstruktor wybiera się rozpoznanie przeciążenia po klasie utworzona za pośrednictwem bezpośredniego inicjowania. Initializer_list służy do inicjowania dowolnego elementu członkowskiego, który może go zaakceptować. Załóżmy na przykład, klasa pola (pokazano wcześniej) ma `std::vector<string>` elementu członkowskiego **m_contents**. Można podać konstruktora następująco:

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

A następnie utworzyć obiekty pole następująco:

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit_constructors"></a> Jawnych konstruktorów

Jeśli klasa ma konstruktora z pojedynczym parametrem lub jeśli wszystkie parametry z wyjątkiem jednego ma wartość domyślną, można niejawnie przekonwertować typu parametru, do typu klasy. Na przykład jeśli `Box` klasa ma konstruktora następująco:

```cpp
Box(int size): m_width(size), m_length(size), m_height(size){}
```

Istnieje możliwość zainicjować pole następująco:

```cpp
Box b = 42;
```

Lub Przekaż int do funkcji, która przyjmuje pola:

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

Konwersje takie mogą być przydatne w niektórych przypadkach, ale często może prowadzić do niewielkie, ale poważne problemy występujące w kodzie. Jako ogólną regułę, należy użyć **jawne** — słowo kluczowe konstruktora (i operatory zdefiniowane przez użytkownika), aby uniknąć tego rodzaju niejawna konwersja typu:

```cpp

explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

W przypadku jawnego konstruktora tego wiersza spowoduje, że wystąpi błąd kompilatora: `ShippingOrder so(42, 10.8);`.  Aby uzyskać więcej informacji, zobacz [zdefiniowane przez użytkownika konwersje typów](../cpp/user-defined-type-conversions-cpp.md).

## <a name="order_of_construction"></a> Kolejność konstrukcji

Konstruktor wykonuje pracę w następującej kolejności:

1. Wywołuje klasę podstawową i konstruktory składowych w kolejności deklaracji.

2. Jeśli klasa jest pochodną wirtualnych klas bazowych, inicjuje wskaźniki wirtualnej bazy obiektu.

3. Jeśli klasa ma lub dziedziczy funkcje wirtualne, inicjuje wskaźniki funkcji wirtualnych obiektu. Wskaźniki funkcji wirtualnych wskazują na tabelę funkcji wirtualnych tej klasy, aby umożliwić poprawne powiązanie wywołań funkcji wirtualnych z kodem.

4. Wykonuje każdy kod w jego treści funkcji.

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

```output
Contained1 ctor
Contained2 ctor
BaseContainer ctor
Contained3 ctor
DerivedContainer ctor
```

Konstruktor klasy pochodnej zawsze wywołuje konstruktora klasy bazowej, tak aby mógł polegać na całkowicie skonstruowanych klasach bazowych, zanim wszelkie dodatkowe prace zostaną wykonane. Konstruktory klasy bazowej są wywoływane w kolejności wyprowadzenia — na przykład, jeśli ClassA jest wyprowadzany z ClassB, który z kolei jest wyprowadzany z ClassC, konstruktor ClassC jest wywoływany jako pierwszy, następnie konstruktor ClassB, a na koniec konstruktor ClassA.

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

### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>Konstruktory klas, które mają dziedziczenie wielokrotne

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

```output

BaseClass1 ctor
BaseClass2 ctor
BaseClass3 ctor
DerivedClass ctor

```

## <a name="virtual_functions_in_constructors"></a> Funkcje wirtualne w konstruktorach

Zalecamy, aby uważać podczas wywołania funkcji wirtualnych w konstruktorach. Ponieważ konstruktor klasy bazowej zawsze jest wywoływany przed konstruktorem klasy pochodnej, funkcja, która jest wywołana w konstruktorze klasy bazowej, jest wersją klasy bazowej, a nie wersją klasy pochodnej. W poniższym przykładzie konstruowania `DerivedClass` powoduje, że `BaseClass` implementacja `print_it()` do uruchomienia przed `DerivedClass` przyczyny konstruktora `DerivedClass` implementacja `print_it()` do wykonania:

```cpp
#include <iostream>
using namespace std;

class BaseClass{
public:
    BaseClass(){
        print_it();
    }
    virtual void print_it() {
        cout << "BaseClass print_it" << endl;
    }
};

class DerivedClass : public BaseClass {
public:
    DerivedClass() {
        print_it();
    }
    virtual void print_it(){
        cout << "Derived Class print_it" << endl;
    }
};

int main() {

    DerivedClass dc;
}
```

Oto dane wyjściowe:

```output
BaseClass print_it
Derived Class print_it
```

## <a name="delegating_constructors"></a> Delegowanie konstruktorów

A *delegowanie Konstruktor* wymaga innego konstruktora w tej samej klasie wykonania określonej prac inicjowania. Jest to przydatne, jeśli masz wiele konstruktorów mające do wykonywania pracy podobne. Możesz zapisać logiki główny w jeden konstruktor i wywołać go od innych użytkowników. W poniższym przykładzie trivial Box(int) deleguje jego pracy Box(int,int,int):

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initalize a Box with equal dimensions (i.e. a cube)
    Box(int i) :  Box(i, i, i);  // delegating constructor
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
    //... rest of class as before
};
```


Obiekt utworzony przez konstruktory jest w pełni zainicjowany natychmiast po zakończeniu wszelkich konstruktorów. Aby uzyskać więcej informacji, zobacz [jednolite inicjowanie i delegowanie konstruktorów](../cpp/uniform-initialization-and-delegating-constructors.md).

## <a name="inheriting_constructors"></a> Dziedziczenie konstruktory (C ++ 11)

Klasa pochodna może dziedziczyć konstruktorów bezpośredniej klasie podstawowej za pomocą używającego deklaracji, jak pokazano w poniższym przykładzie:

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

Przełącza za pomocą instrukcji w zakresie wszystkich konstruktorów z klasy podstawowej, z wyjątkiem tych, które mają taki sam podpis konstruktorów w klasie pochodnej. Ogólnie rzecz biorąc najlepiej użyć dziedziczących konstruktorów, gdy klasa pochodna nie deklaruje żadnych nowych elementów członkowskich danych lub konstruktorów.

Szablon klasy mogą dziedziczyć wszystkie konstruktory argument typu w przypadku tego typu Określa klasę podstawową:

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};

```

Klasa pochodna nie może dziedziczyć z wielu klas podstawowych, jeśli tych klas podstawowych mieć konstruktorów, które mają taki sam podpis.

## <a name="constructors_in_composite_classes"></a> Konstruktory i klasy złożone

Klasy, które zawierają elementy członkowskie typu klasy są określane jako *klasy złożone*. Gdy jest tworzona składowa typu klasa klasy złożonej, konstruktor jest wywoływany przed konstruktorem tej klasy. Gdy klasa zamknięta nie ma domyślnego konstruktora, należy użyć listy inicjalizacji w konstruktorze klasy złożonej. W starszych `StorageBox` przykład, jeśli zmienisz typ `m_label` zmiennej członkowskiej na nowy `Label` klasy, należy wywołać konstruktora klasy podstawowej i zainicjować `m_label` zmiennej w `StorageBox` konstruktora:

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