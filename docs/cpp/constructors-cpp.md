---
title: Konstruktory (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 53a05467a876a8b305aba64e49e0763cf5690a56
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940888"
---
# <a name="constructors-c"></a>Konstruktory (C++)

Aby dostosować, jak elementy klas są inicjowane lub wywołania funkcji, gdy tworzony jest obiekt klasy, zdefiniuj *Konstruktor*. Konstruktor ma taką samą nazwę jak klasa i nie zwraca wartości. Można zdefiniować dowolną liczbę przeciążenia konstruktorów w razie potrzeby dostosować inicjowania na różne sposoby. Zazwyczaj konstruktorów mają powszechnej dostępności, w którym kod poza hierarchii definicji lub dziedziczenia klas może utworzyć obiektów klasy. Ale można również zadeklarować Konstruktor jako **chronione** lub **prywatnej**.

Konstruktory opcjonalnie może członka listy inicjowania. Jest to bardziej wydajny sposób inicjowania składowych niż przypisywanie wartości w treści konstruktora. W poniższym przykładzie pokazano klasę `Box` z trzema przeciążone konstruktory. Ostatnie dwa użyj listy inicjowania elementów członkowskich:

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

Kiedy Deklarujesz wystąpienia klasy, kompilator wybiera konstruktora do wywołania na podstawie reguł z Rozpoznanie przeciążenia:

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

- Konstruktory mogą być deklarowane jako **wbudowane**, [jawne](#explicit_constructors), **friend** lub [constexpr](#constexpr_constructors).
- Konstruktor można zainicjować obiektu, który został zadeklarowany jako **const**, **volatile** lub **const volatile**. Obiekt staje się **const** po zakończeniu działania konstruktora.
- Aby zdefiniować Konstruktor w pliku z implementacją, nadaj mu kwalifikowana nazwa podobnie jak w przypadku innych funkcji składowej: `Box::Box(){...}`.

## <a name="member_init_list"></a> Listy inicjatorów składowej

Konstruktor opcjonalnie może mieć listy inicjatorów składowej, który inicjuje elementy członkowskie klasy przed ciele konstruktora. (Należy pamiętać, że listy inicjatorów składowej nie jest tak samo jak *listy inicjatorów* typu [std::initializer_list\<T >](../standard-library/initializer-list-class.md).)

Za pomocą listy inicjatora składowej jest preferowana nad przypisywaniem wartości w treści konstruktora, ponieważ bezpośrednio inicjuje element członkowski. W poniższym przykładzie przedstawiono inicjator składowej lista zawiera wszystkie **identifier(argument)** wyrażeń po dwukropku:

```cpp
  
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

Identyfikator musi odwoływać się do elementu członkowskiego klasy; zostanie zainicjowany z wartością argumentu. Argument może być jeden z parametrów konstruktora, wywołanie funkcji lub [std::initializer_list\<T >](../standard-library/initializer-list-class.md). 

**Const** elementy członkowskie i elementy członkowskie typu referencyjnego musi zostać zainicjowany na liście inicjatora składowej.

Wywołania konstruktory sparametryzowane klasy bazowej należy na liście inicjatora upewnij się, że klasa podstawowa jest w pełni zainicjowany przed wykonywania pochodny Konstruktor.

## <a name="default_constructors"></a> Konstruktory domyślne

 *Domyślne konstruktory* zwykle nie mają parametrów, ale mogą mieć parametrów mających wartości domyślne.

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

Konstruktory domyślne są jednymi z [specjalnych funkcji Członkowskich](special-member-functions.md). Jeśli nie zadeklarowano konstruktorów w klasie, kompilator zapewnia niejawny **wbudowane** domyślnego konstruktora.

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

Jeśli polegać na niejawnego domyślnego konstruktora, pamiętaj zainicjować elementy członkowskie w definicji klasy, jak pokazano w poprzednim przykładzie. Bez tych inicjatory elementów członkowskich będzie niezainicjowanej i wywołania Volume() dałby w efekcie wartość pamięci. Ogólnie rzecz biorąc jest dobrą praktyką, aby zainicjować elementy członkowskie w ten sposób, nawet wtedy, gdy nie opierając się na niejawnego domyślnego konstruktora.

Możesz uniemożliwić kompilatorowi Generowanie niejawnego domyślnego konstruktora, definiując je jako [usunięte](#explicitly_defaulted_and_deleted_constructors):

```cpp

    // Default constructor
    Box() = delete;

```

Generowane przez kompilator domyślnego konstruktora zostanie zdefiniowany jako usunięty, jeśli wszystkie elementy członkowskie klasy nie są konstrukcyjną domyślne. Na przykład wszystkie elementy członkowskie typu klasy i składowe typu klasa musi mieć konstruktora domyślnego i destruktory, które są dostępne. Wszystkie składowe danych odwołania do typu również jako **const** Członkowie muszą mieć domyślny inicjator składowej.

Gdy wywołujesz Konstruktor domyślny wygenerowany przez kompilator i próbujesz użyć nawiasów, pojawi się ostrzeżenie:

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

Jest to przykład problemu najbardziej irytującej interpretacji składni (Most Vexing Parse). Ponieważ wyrażenie przykładowe może być interpretowane jako deklaracja funkcji lub wywołanie konstruktora domyślnego i ponieważ analizatory składni języka C++ promują deklaracje w stosunku do innych obiektów, wyrażenie jest traktowane jako deklaracja funkcji. Aby uzyskać więcej informacji, zobacz [najbardziej irytująca Most vexing Parse](http://en.wikipedia.org/wiki/Most_vexing_parse).

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

Jednak można użyć zestawu list inicjatorów do zainicjowania tablicy obiektów pola:

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

Aby uzyskać więcej informacji, zobacz [inicjatory](initializers.md).

## <a name="copy_and_move_constructors"></a> Kopiowanie konstruktorów

A *Konstruktor kopiujący* inicjuje obiekt przez skopiowanie wartości elementów członkowskich obiektu tego samego typu. Usługi składowe klasy w przypadku wszystkich typów prostych, takie jak wartości skalarnych, Konstruktor kopiujący wygenerowany przez kompilator jest wystarczająca, i nie musisz zdefiniować własne. Jeśli klasa wymaga bardziej złożonej inicjowania, należy zaimplementować konstruktora kopiującego niestandardowych. Na przykład jeśli element członkowski klasy jest wskaźnikiem typu należy zdefiniować Konstruktor kopiujący, można przydzielić nowej pamięci i skopiuj wartości z drugiej strony wskazywanego obiektu. Konstruktor kopiujący wygenerowany przez kompilator po prostu kopiuje wskaźnika, tak, aby nadal nowy wskaźnik wskazuje na lokalizację w drugiej strony pamięci.

Konstruktor kopiujący może mieć jedną z tych sygnatur:

```cpp

    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

Podczas definiowania konstruktora kopiującego, należy także zdefiniować kopia operatora przypisania (=). Aby uzyskać więcej informacji, zobacz [przypisania](assignment.md) i [kopiowanie konstruktorów i operatory przypisania kopiowania](copy-constructors-and-copy-assignment-operators-cpp.md).

Aby zapobiec obiektu kopiowane przez definiowanie konstruktora kopiującego jako usunięty:

```cpp
    Box (const Box& other) = delete;
```

Próby skopiowania obiektu powoduje błąd *C2280: próba odwania do usuniętej funkcji do*.

## <a name="move_constructors"></a> Konstruktory przenoszenia
A *Konstruktor przenoszący* jest funkcji specjalnych elementów członkowskich, który przenosi własności istniejący obiekt danych do nowej zmiennej bez kopiowania oryginalnych danych. Trwa odwołanie rvalue za swój pierwszy parametr i żadnych dodatkowych parametrów muszą mieć wartości domyślnej. Konstruktorów przenoszenia może znacznie zwiększyć wydajność swojego programu podczas przekazywania dużych obiektów. Konstruktor przenoszący przyjmuje odwołanie rvalue jako pierwszym parametrem. Inne parametry muszą mieć wartości domyślnej.

```cpp
Box(Box&& other);
```

Kompilator wybiera Konstruktor przenoszący, w niektórych sytuacjach, gdy obiekt jest inicjowany przez innego obiektu tego samego typu, który ma zostać zniszczone i nie jest już konieczne zasobów. Poniższy przykład pokazuje jeden przypadek, po wybraniu przez rozpoznanie przeciążenia konstruktora przenoszącego. Zmienna *pole* zwrócone przez get_Box() jest *xvalue* (wartość wygasający) który się wykraczają poza zakres. Aby zapewnić motywacji, w tym przykładzie, nadajmy pole wektor dużych ciągów reprezentujących jego zawartość. Zamiast kopiowania wektora i jej parametry, Konstruktor przenoszący "dokonuje" go z wygasające wartości "pola", aby wektora teraz należy do nowego obiektu. Wywołanie `std::move` to wszystko, co jest potrzebne, ponieważ oba `vector` i `string` klasy implementować własne konstruktorów przenoszenia.

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

Jeśli klasa nie definiuje konstruktora przenoszącego, kompilator generuje niejawne co, jeśli nie Konstruktor kopiujący zgłoszone przez użytkownika, operator przypisania kopiowania, operator przypisania przenoszenia lub destruktor. Jeśli żaden konstruktor przenoszący jawnych lub niejawnych nie jest zdefiniowany, operacje, które w przeciwnym razie użyć konstruktora przenoszącego zamiast tego użyj Konstruktora kopiującego. Jeśli klasa deklaruje Konstruktor przenoszący lub operator przypisania przenoszenia, Konstruktor kopiujący niejawnie zadeklarowanej jest zdefiniowany jako usunięty.

Konstruktor przenoszący niejawnie zadeklarowanej jest zdefiniowany jako usunięty, jeśli nie ma żadnych elementów członkowskich, które są typami klas destruktora lub kompilator nie może określić konstruktora do użycia dla operacji przenoszenia.

Aby uzyskać więcej informacji dotyczących sposobu pisania konstruktora przenoszącego nietrywialnymi zobacz [konstruktory przenoszenia i operatory przenoszenia przypisania (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

## <a name="explicitly_defaulted_and_deleted_constructors"></a> Konstruktory jawnie domyślne i usunięte

Możesz jawnie *domyślne* kopiowanie konstruktorów, domyślne konstruktory, konstruktory przenoszenia, operatory przypisania kopiowania, Przenieś operatory przypisania i destruktory. Możesz jawnie *Usuń* wszystkich funkcji specjalnych elementów członkowskich.

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

Aby uzyskać więcej informacji, zobacz [jawnie przyjmujące wartości domyślne i usunięte funkcje](../cpp/explicitly-defaulted-and-deleted-functions.md).

## <a name="constexpr_constructors"></a> Konstruktory constexpr

Konstruktor może być zadeklarowana jako [constexpr](constexpr-cpp.md) Jeśli

- jest albo zadeklarowane jako przyjmujące wartości domyślne lub — w przeciwnym razie spełnia wszystkie warunki dla [funkcjach ze specyfikatorem constexpr](constexpr-cpp.md#constexpr_functions) ogólnie rzecz biorąc;
- Klasa nie ma żadnych wirtualnych klas bazowych;
- Każdy z parametrów jest [literalne](trivial-standard-layout-and-pod-types.md#literal_types);
- treść nie jest blokiem try funkcji;
- wszystkie elementy członkowskie danych niestatyczna i obiekty podrzędne klasy bazowej są inicjowane;
- Jeśli klasa jest sumą () członkowie wariantu lub (b) ma związki anonimowe, tylko jeden z elementów członkowskich Unii jest zainicjowany;
- Każdy element członkowski danych niestatycznych typu klasy i wszystkie obiekty podrzędne klasa bazowa ma konstruktora constexpr


## <a name="init_list_constructors"></a> Konstruktory listy inicjatora

Jeśli Konstruktor przyjmuje [std::initializer_list\<T\> ](../standard-library/initializer-list-class.md) zgodnie z jego parametrów i innych parametrów mieć argumentów domyślnych, ten konstruktor zostanie wybrany w przeciążeniu rozdzielczości po klasie tworzone za pomocą inicjalizacji bezpośredniej. Lista initializer_list można użyć do zainicjowania dowolnego elementu członkowskiego, który może go zaakceptować. Załóżmy na przykład, klasa pole (pokazano wcześniej) ma `std::vector<string>` elementu członkowskiego `m_contents`. Możesz podać Konstruktor następująco:

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

A następnie utwórz pole obiektów, takich jak to:

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit_constructors"></a> Jawnych konstruktorów

Jeśli klasa ma Konstruktor z pojedynczym parametrem lub jeśli wszystkie parametry z wyjątkiem jednego mają wartość domyślną typu parametru mogą być niejawnie konwertowane na typ klasy. Na przykład jeśli `Box` klasa ma Konstruktor następująco:

```cpp
Box(int size): m_width(size), m_length(size), m_height(size){}
```

Użytkownik może zainicjować okno następująco:

```cpp
Box b = 42;
```

Lub przekazać int do funkcji, która przyjmuje pola:

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

Takie konwersje może być przydatne w niektórych przypadkach, ale częściej może prowadzić do subtelne, ale poważne problemy występujące w kodzie. Zgodnie z ogólną zasadą, należy użyć **jawne** słowo kluczowe w Konstruktorze (i operatory zdefiniowane przez użytkownika), aby uniknąć tego rodzaju niejawna konwersja typu:

```cpp

explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

Konstruktor jest jawne, ten wiersz powoduje błąd kompilatora: `ShippingOrder so(42, 10.8);`.  Aby uzyskać więcej informacji, zobacz [konwersje typów zdefiniowane przez użytkownika](../cpp/user-defined-type-conversions-cpp.md).

## <a name="order_of_construction"></a> Kolejność konstruowania

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

```output

BaseClass1 ctor
BaseClass2 ctor
BaseClass3 ctor
DerivedClass ctor

```

## <a name="virtual_functions_in_constructors"></a> Funkcje wirtualne w konstruktorach

Zalecamy, aby uważać podczas wywołania funkcji wirtualnych w konstruktorach. Ponieważ konstruktor klasy bazowej zawsze jest wywoływany przed konstruktorem klasy pochodnej, funkcja, która jest wywołana w konstruktorze klasy bazowej, jest wersją klasy bazowej, a nie wersją klasy pochodnej. W poniższym przykładzie konstruowanie `DerivedClass` powoduje, że `BaseClass` implementacji `print_it()` do wykonania przed `DerivedClass` powoduje, że Konstruktor `DerivedClass` implementacji `print_it()` do wykonania:

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

## <a name="delegating_constructors"></a> Konstrukty delegujące

A *Konstruktor delegujący* wywołuje innego konstruktora w tej samej klasie w celu wykonania niektórych prac inicjowania. Jest to przydatne, jeśli masz wiele konstruktorów wszystkie trzeba mają podobne działanie. Można zapisanie logiki głównego w jeden konstruktor i wywołać go od innych użytkowników. W poniższym przykładzie trivial Box(int) deleguje jego pracy Box(int,int,int):

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

## <a name="inheriting_constructors"></a> Dziedziczenie konstruktorów (C ++ 11)

Klasa pochodna może dziedziczyć konstruktory bezpośrednią klasą bazową za pomocą deklaracji, jak pokazano w poniższym przykładzie:

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

Za pomocą instrukcji wnosi do zakresu wszystkie konstruktory z klasy bazowej, z wyjątkiem tych, które mają identyczne podpisu konstruktorów w klasie pochodnej. Ogólnie rzecz biorąc najlepiej jest używać dziedziczącej konstruktorów, gdy klasa pochodna nie deklaruje żadnych nowych elementów członkowskich danych lub konstruktory.

Szablon klasy mogą dziedziczyć wszystkie konstruktory argument typu Jeśli ten typ Określa klasę bazową:

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};

```

Klasa pochodna nie może dziedziczyć z wielu klas bazowych, jeśli konstruktory, które mają identyczne tych klas bazowych.

## <a name="constructors_in_composite_classes"></a> Konstruktory i klasy złożone

Klasy, które zawierają składowe typu klasa są znane jako *klasy złożone*. Gdy jest tworzona składowa typu klasa klasy złożonej, konstruktor jest wywoływany przed konstruktorem tej klasy. Gdy klasa zamknięta nie ma domyślnego konstruktora, należy użyć listy inicjalizacji w konstruktorze klasy złożonej. We wcześniejszych przykładach `StorageBox` przykład, jeśli zmienisz typ `m_label` zmienną członkowską na nową `Label` klasy, musisz wywołać konstruktora klasy podstawowej i zainicjować `m_label` zmienną `StorageBox` Konstruktor:

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