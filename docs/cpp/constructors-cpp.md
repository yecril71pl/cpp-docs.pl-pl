---
title: Konstruktory (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 57854ec15d3104d80e8dbba68ebc33937222172f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="constructors-c"></a>Konstruktory (C++)
Konstruktor jest rodzajem funkcji członkowskiej, która inicjuje wystąpienie swojej klasy. Konstruktor ma taką samą nazwę jak klasa i brak wartości zwracanej. Konstruktor może mieć dowolną liczbę parametrów i klasa może zawierać dowolną liczbę przeciążone konstruktory. Konstruktory mogą mieć żadnych dostępności publicznych, chronionych lub prywatnych. Jeśli nie zdefiniowano żadnych konstruktorów, kompilator generuje domyślnego konstruktora, który nie przyjmuje żadnych parametrów; Aby zmienić to zachowanie, należy deklarowanie konstruktora domyślnego jako usunięte.  
  
## <a name="in-this-topic"></a>W tym temacie:  
  
-   [Kolejność konstrukcji](#order_of_construction)  
  
-   [Listach elementów członkowskich](#member_lists)  
  
-   [Jawnych konstruktorów](#explicit_constructors)  
  
-   [Konstruktory domyślne](#default_constructors)  
  
-   [Kopiowanie i przenoszenie konstruktorów](#copy_and_move_constructors)  
  
-   [Jawnie domyślne i usunięte konstruktorów](#explicitly_defaulted_and_deleted_constructors)  
  
-   [Konstruktorów w klasach pochodnych](#constructors_in_derived_classes)  
  
-   [Funkcje wirtualne w konstruktorach](#virtual_functions_in_constructors)  
  
-   [Konstruktory i klasy złożone](#constructors_in_composite_classes)  
  
-   [Delegowanie konstruktorów](#delegating_constructors)  
  
-   [Dziedziczenie konstruktory (C ++ 11)](#inheriting_constructors)  
  
-   [Reguły deklarowania konstruktorów](#rules_for_declaring_constructors)  
  
-   [Jawne wywołania konstruktorów](#explicitly_invoking_constructors)  
  
##  <a name="order_of_construction"></a>Kolejność konstrukcji  
 Konstruktor wykonuje pracę w następującej kolejności:  
  
1.  Wywołuje klasę podstawową i konstruktory składowych w kolejności deklaracji.  
  
2.  Jeśli klasa jest pochodną wirtualnych klas bazowych, inicjuje wskaźniki wirtualnej bazy obiektu.  
  
3.  Jeśli klasa ma lub dziedziczy funkcje wirtualne, inicjuje wskaźniki funkcji wirtualnych obiektu. Wskaźniki funkcji wirtualnych wskazują na tabelę funkcji wirtualnych tej klasy, aby umożliwić poprawne powiązanie wywołań funkcji wirtualnych z kodem.  
  
4.  Wykonuje każdy kod w jego treści funkcji.  
  
 Poniższy przykład pokazuje kolejność, w której konstruktory klasy podstawowej i składowych są wywoływane w konstruktorze klasy pochodnej. Najpierw jest wywoływany podstawowy konstruktor, następnie składowe klas bazowych są inicjowane w kolejności, w której pojawiają się w deklaracji klasy, a na koniec jest wywoływany pochodny konstruktor.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class Contained1 {  
public:  
    Contained1() {  
        cout << "Contained1 constructor." << endl;  
    }  
};  
  
class Contained2 {  
public:  
    Contained2() {  
        cout << "Contained2 constructor." << endl;  
    }  
};  
  
class Contained3 {  
public:  
    Contained3() {  
        cout << "Contained3 constructor." << endl;  
    }  
};  
  
class BaseContainer {  
public:  
    BaseContainer() {  
        cout << "BaseContainer constructor." << endl;  
    }  
private:  
    Contained1 c1;  
    Contained2 c2;  
};  
  
class DerivedContainer : public BaseContainer {  
public:  
    DerivedContainer() : BaseContainer() {  
        cout << "DerivedContainer constructor." << endl;  
    }  
private:  
    Contained3 c3;  
};  
  
int main() {  
    DerivedContainer dc;  
    int x = 3;  
}  
  
```  
  
 Oto dane wyjściowe:  
  
```  
Contained1 constructor.  
Contained2 constructor.  
BaseContainer constructor.  
Contained3 constructor.  
DerivedContainer constructor.  
```  
  
 Jeśli konstruktor zgłasza wyjątek, kolejność zniszczenia jest odwrotna do kolejności konstrukcji:  
  
1.  Kod w treści funkcji konstruktora jest rozwinięty.  
  
2.  Klasa podstawowa i obiekty składowe są usuwane w kolejności odwrotnej do deklarowania.  
  
3.  Jeśli konstruktor nie jest delegujący, wszystkie w pełni skonstruowane obiekty i składowe klasy podstawowej zostaną zniszczone. Jednak ponieważ sam obiekt nie jest w pełni skonstruowany, destruktor nie zostanie uruchomiony.  
  
##  <a name="member_lists"></a>Listach elementów członkowskich  
 Inicjowanie elementów członkowskich klasy z argumentów konstruktora za pomocą listy inicjatorów elementu członkowskiego. Ta metoda używa *bezpośredniego inicjowania*, który jest bardziej efektywne niż przy użyciu operatorów przypisania wewnątrz treści konstruktora.  
  
```cpp  
class Box {  
public:  
    Box(int width, int length, int height)   
        : m_width(width), m_length(length), m_height(height) // member init list  
    {}  
    int Volume() {return m_width * m_length * m_height; }  
private:  
    int m_width;  
    int m_length;  
    int m_height;  
  
};  
  
```  
  
 Utwórz obiekt pola:  
  
```  
Box b(42, 21, 12);  
cout << "The volume is " << b.Volume();  
```  
  
##  <a name="explicit_constructors"></a>Jawnych konstruktorów  
 Jeśli klasa ma konstruktora z pojedynczym parametrem lub jeśli wszystkie parametry z wyjątkiem jednego ma wartość domyślną, można niejawnie przekonwertować typu parametru, do typu klasy. Na przykład jeśli `Box` klasa ma konstruktora następująco:  
  
```  
Box(int size): m_width(size), m_length(size), m_height(size){}  
```  
  
 Istnieje możliwość zainicjować pole następująco:  
  
```  
Box b = 42;  
```  
  
 Lub Przekaż int do funkcji, która przyjmuje pola:  
  
```  
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
  
 Konwersje takie mogą być przydatne w niektórych przypadkach, ale często może prowadzić do niewielkie, ale poważne problemy występujące w kodzie. Jako ogólną regułę, należy użyć `explicit` — słowo kluczowe konstruktora (i operatory zdefiniowane przez użytkownika), aby uniknąć tego rodzaju niejawna konwersja typu:  
  
```  
  
explicit Box(int size): m_width(size), m_length(size), m_height(size){}  
```  
  
 W przypadku jawnego konstruktora tego wiersza spowoduje, że wystąpi błąd kompilatora: `ShippingOrder so(42, 10.8);`.  Aby uzyskać więcej informacji, zobacz [zdefiniowane przez użytkownika konwersje typów](../cpp/user-defined-type-conversions-cpp.md).  
  
##  <a name="default_constructors"></a>Konstruktory domyślne  
 *Konstruktory domyślne* nie może mieć parametrów; wykonaj są nieco inne reguły:  
  
 Konstruktory domyślne są jednym z *specjalnych funkcji Członkowskich*; ma konstruktorów jest zadeklarowana w klasie, kompilator zapewnia konstruktora domyślnego:  
  
```cpp  
class Box {  
    Box(int width, int length, int height)   
        : m_width(width), m_length(length), m_height(height){}  
};  
  
int main(){  
  
    Box box1{}; // call compiler-generated default ctor  
    Box box2;   // call compiler-generated default ctor  
}  
```  
  
 Gdy wywołujesz konstruktor domyślny i próbujesz użyć nawiasów, wyświetla się ostrzeżenie:  
  
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
    Box box4;     // compiler error C2512: no appropriate default constructor available  
}  
  
```  
  
 Jeśli klasa nie ma domyślnego konstruktora, nie można utworzyć tablicy obiektów tej klasy przy użyciu wyłącznie składni z nawiasami kwadratowymi. Na przykład, biorąc pod uwagę poprzedni blok kodu, tablicy pól nie można zadeklarować w ten sposób:  
  
```cpp  
Box boxes[3];    // compiler error C2512: no appropriate default constructor available  
  
```  
  
 Możesz jednak użyć zestawu list inicjatorów do zainicjowania tablicy pól:  
  
```cpp  
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };  
```  
  
##  <a name="copy_and_move_constructors"></a>Kopiowanie i przenoszenie konstruktorów  
 A *Konstruktor kopiujący* jest specjalną funkcją członkowską, który przyjmuje jako dane wejściowe odwołanie do obiektu tego samego typu i tworzy kopię. Aby uzyskać więcej informacji, zobacz [konstruktory kopiujące i kopiowania operatory przypisania (C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md). A *przenoszenie konstruktora* jest również funkcją członkowską specjalny, który przenosi własność istniejący obiekt danych do nowej zmiennej, bez kopiowania oryginalnych danych. Aby uzyskać więcej informacji, zobacz [konstruktory przenoszenia i operatory przypisania przenoszenia (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).  
  
##  <a name="explicitly_defaulted_and_deleted_constructors"></a>Jawnie domyślne i usunięte konstruktorów  
 Można jawnie *domyślne* kopiowanie konstruktorów, konstruktory domyślne, Przenieś konstruktorów, skopiuj operatory przypisania, Przenieś operatory przypisania i destruktory. Można jawnie *usunąć* wszystkie funkcje specjalne elementu członkowskiego. Aby uzyskać więcej informacji, zobacz [jawnie ustawiana domyślnie i usunięte funkcje](../cpp/explicitly-defaulted-and-deleted-functions.md).  
  
##  <a name="constructors_in_derived_classes"></a>Konstruktorów w klasach pochodnych  
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
  
### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>Konstruktory dla klas, które mają wiele dziedziczeń  
 Jeśli klasa jest pochodną wielu klas bazowych, konstruktory klas bazowych są wywoływane w kolejności, w której są wymienione w deklaracji klasy pochodnej:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class BaseClass1 {  
public:  
    BaseClass1() {  
        cout << "BaseClass1 constructor." << endl;  
    }  
};  
class BaseClass2 {  
public:  
    BaseClass2() {  
        cout << "BaseClass2 constructor." << endl;  
    }  
};  
class BaseClass3{  
public:  
    BaseClass3() {  
        cout << "BaseClass3 constructor." << endl;  
    }  
};  
class DerivedClass : public BaseClass1, public BaseClass2, public BaseClass3  {  
public:  
    DerivedClass() {  
        cout << "DerivedClass constructor." << endl;  
    }  
};  
  
int main() {  
    DerivedClass dc;  
}  
  
```  
  
 Powinny się wyświetlić poniższe dane wyjściowe:  
  
```  
BaseClass1 constructor.  
BaseClass2 constructor.  
BaseClass3 constructor.  
DerivedClass constructor.  
```  
  
##  <a name="virtual_functions_in_constructors"></a>Funkcje wirtualne w konstruktorach  
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
  
```  
BaseClass print_it  
Derived Class print_it  
```  
  
##  <a name="constructors_in_composite_classes"></a>Konstruktory i klasy złożone  
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
  
##  <a name="delegating_constructors"></a>Delegowanie konstruktorów  
 A *delegowanie Konstruktor* wymaga innego konstruktora w tej samej klasie wykonania określonej prac inicjowania. W poniższym przykładzie klasa pochodna ma trzy konstruktory — drugi konstruktor deleguje do pierwszego, a trzeci konstruktor deleguje do drugiego:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class ConstructorDestructor {  
public:  
    ConstructorDestructor() {  
        cout << "ConstructorDestructor default constructor." << endl;  
    }  
    ConstructorDestructor(int int1) {  
        cout << "ConstructorDestructor constructor with 1 int." << endl;  
    }  
    ConstructorDestructor(int int1, int int2) : ConstructorDestructor(int1) {  
        cout << "ConstructorDestructor constructor with 2 ints." << endl;  
  
        throw exception();  
    }  
    ConstructorDestructor(int int1, int int2, int int3) : ConstructorDestructor(int1, int2) {  
        cout << "ConstructorDestructor constructor with 3 ints." << endl;  
    }  
    ~ConstructorDestructor() {  
        cout << "ConstructorDestructor destructor." << endl;  
    }  
};  
  
int main() {  
    ConstructorDestructor dc(1, 2, 3);  
}  
  
```  
  
 Oto dane wyjściowe:  
  
```  
ConstructorDestructor constructor with 1 int.  
ConstructorDestructor constructor with 2 ints.  
ConstructorDestructor constructor with 3 ints.  
```  
  
 Obiekt utworzony przez konstruktory jest w pełni zainicjowany natychmiast po zakończeniu wszelkich konstruktorów. `DerivedContainer(int int1)`zakończy się powodzeniem, ale `DerivedContainer(int int1, int int2)` zakończy się niepowodzeniem i destruktor jest wywoływana.  
  
```cpp  
class ConstructorDestructor {  
public:  
    ConstructorDestructor() {  
        cout << "ConstructorDestructor default constructor." << endl;  
    }  
    ConstructorDestructor(int int1) {  
        cout << "ConstructorDestructor constructor with 1 int." << endl;  
    }  
    ConstructorDestructor(int int1, int int2) : ConstructorDestructor(int1) {  
        cout << "ConstructorDestructor constructor with 2 ints." << endl;  
        throw exception();  
    }  
    ConstructorDestructor(int int1, int int2, int int3) : ConstructorDestructor(int1, int2) {  
        cout << "ConstructorDestructor constructor with 3 ints." << endl;  
    }  
  
    ~ConstructorDestructor() {  
        cout << "ConstructorDestructor destructor." << endl;  
    }  
};  
  
int main() {  
  
    try {  
        ConstructorDestructor cd{ 1, 2, 3 };  
    }  
    catch (const exception& ex){  
    }  
}  
  
```  
  
 Dane wyjściowe:  
  
```  
ConstructorDestructor constructor with 1 int.  
ConstructorDestructor constructor with 2 ints.  
ConstructorDestructor destructor.  
```  
  
 Aby uzyskać więcej informacji, zobacz [jednolite inicjowanie i delegowanie konstruktorów](../cpp/uniform-initialization-and-delegating-constructors.md).  
  
##  <a name="inheriting_constructors"></a>Dziedziczenie konstruktory (C ++ 11)  
 Klasa pochodna może dziedziczyć konstruktorów bezpośredniej klasie podstawowej za pomocą używającego deklaracji, jak pokazano w poniższym przykładzie:  
  
```  
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
  
int main(int argc, char argv[])  
{  
    cout << "Derived d1(5) calls: ";   
    Derived d1(5);  
    cout << "Derived d1('c') calls: ";  
    Derived d2('c');  
    cout << "Derived d3 = d2 calls: " ;  
    Derived d3 = d2;  
    cout << "Derived d4 calls: ";  
    Derived d4;   
  
    // Keep console open in debug mode:  
    cout << endl << "Press Enter to exit.";  
    char in[1];  
    cin.getline(in, 1);  
    return 0;  
}  
  
/* Output:  
Derived d1(5) calls: Base(int)  
Derived d1('c') calls: Base(char)  
Derived d3 = d2 calls: Base(Base&)  
Derived d4 calls: Base()  
  
Press Enter to exit.  
  
```  
  
 Przełącza za pomocą instrukcji w zakresie wszystkich konstruktorów z klasy podstawowej, z wyjątkiem tych, które mają taki sam podpis konstruktorów w klasie pochodnej. Ogólnie rzecz biorąc najlepiej użyć dziedziczących konstruktorów, gdy klasa pochodna nie deklaruje żadnych nowych elementów członkowskich danych lub konstruktorów.  
  
 Szablon klasy mogą dziedziczyć wszystkie konstruktory argument typu w przypadku tego typu Określa klasę podstawową:  
  
```  
template< typename T >  
class Derived : T {  
    using T::T;   // declare the constructors from T  
    // ...  
};  
  
```  
  
 Klasa pochodna nie może dziedziczyć z wielu klas podstawowych, jeśli tych klas podstawowych mieć konstruktorów, które mają taki sam podpis.  
  
##  <a name="rules_for_declaring_constructors"></a>Reguły deklarowania konstruktorów  
 Konstruktor ma taką samą nazwę jak klasa. Zgodnie z regułami funkcji przeciążonych można zadeklarować dowolną liczbę konstruktorów.  
  
 `argument-declaration-list` może być pusta.  
  
 Język C++ definiuje dwa specjalne rodzaje konstruktorów: domyślny i kopiujący (opisane w poniższej tabeli).  
  
### <a name="default-and-copy-constructors"></a>Konstruktory: domyślny i kopiujący  
  
|Rodzaj konstrukcji|Argumenty|Cel|  
|--------------------------|---------------|-------------|  
|Konstruktor domyślny|Może być wywoływany bez argumentów|Konstruuje domyślny obiekt o typie danej klasy|  
|Konstruktor kopiujący|Może zaakceptować pojedynczy argument odwołania do typu tej samej klasy|Kopiuje obiekty o typie danej klasy|  
  
 Konstruktory domyślne mogą być wywoływane bez argumentów. Jednakże, możesz zadeklarować konstruktor domyślny z listą argumentów, pod warunkiem, że wszystkie argumenty mają wartości domyślne. Podobnie, konstruktory kopiujące muszą akceptować pojedynczy argument odwołania do typu tej samej klasy. Można dostarczyć więcej argumentów, pod warunkiem, że każdy kolejny argument posiada wartość domyślną.  
  
 Jeśli nie dostarczysz żadnego konstruktora, kompilator spróbuje wygenerować konstruktor domyślny. Jeśli nie dostarczysz konstruktora kopiującego, kompilator spróbuje go wygenerować. Konstruktory wygenerowane przez kompilator są traktowane jak publiczne funkcje członkowskie. Jeśli określisz konstruktor kopiujący, którego pierwszy argument jest obiektem, a nie odwołaniem, to wygenerowany zostanie błąd.  
  
 Konstruktor domyślny wygenerowany przez kompilator ustawia obiekt (inicjuje vftables i vbtables, jak opisano wcześniej) i wywołuje konstruktory domyślne klas podstawowych oraz składowych, ale nie podejmuje żadnej innej akcji. Konstruktory klas podstawowych i składowych są wywoływane tylko jeśli istnieją, są dostępne i jednoznaczne.  
  
 Konstruktor kopiujący wygenerowany przez kompilator ustawia nowy obiekt i wykonuje kopię zawartości wszystkich elementów członkowskich kopiowanego obiektu. Jeśli istnieje konstruktor klasy podstawowej lub składowej, to zostanie on wywołany; w przeciwnym razie wykonywane jest kopiowanie bitowe.  
  
 Jeśli wszystkie klasy podstawowe i element członkowski klasy `type` mieć konstruktorów kopiowania, które akceptują **const** argumentu, Konstruktor kopiujący generowane przez kompilator akceptuje jeden argument typu **const** `type` **&**. W przeciwnym razie Konstruktor kopiujący generowane przez kompilator akceptuje jeden argument typu `type`  **&** .  
  
 Aby zainicjować można użyć konstruktora **const** lub `volatile` obiekt, ale sam konstruktora nie może być zadeklarowana jako **const** lub `volatile`. Jest jedyną dozwoloną klasą magazynu dla konstruktora **wbudowanego**; użycie innych modyfikator klasy magazynowania, włącznie z `__declspec` — słowo kluczowe, przy użyciu konstruktora powoduje błąd kompilatora.  
  
 Stdcall konwencji wywoływania jest używany dla statycznych funkcji Członkowskich i funkcje globalne zadeklarowana z **__stdcall** — słowo kluczowe oraz że nie należy używać zmiennej listy argumentów. Jeśli używasz **__stdcall** — słowo kluczowe dla niestatycznego elementu członkowskiego funkcji, takich jak konstruktora, kompilator użyje thiscall konwencji wywoływania. "  
  
 Konstruktory klas bazowych nie są dziedziczone przez klasy pochodne. Gdy tworzony jest obiekt o typie klasy pochodnej, konstrukcja rozpoczyna się od składników klasy bazowej, a następnie przenoszona jest na składniki klasy pochodnej. Kompilator używa konstruktora każdej klasy podstawowej jako część cały obiekt został zainicjowany (z wyjątkiem przypadków wirtualnego pochodnym.  
  
##  <a name="explicitly_invoking_constructors"></a>Jawne wywołania konstruktorów  
 Konstruktory można jawnie wywołać programu do tworzenia obiektów danego typu. Na przykład, aby utworzyć dwa `Point` obiektów, które opisują końców linii, mogą być zapisywane następujący kod:  
  
```  
DrawLine( Point( 13, 22 ), Point( 87, 91 ) );  
```  
  
 Dwa obiekty typu `Point` utworzone, przekazany do funkcji `DrawLine`i zniszczona na koniec wyrażenia (wywołanie funkcji).  
  
 Inny kontekst, w którym jawnie wywołać konstruktora jest podczas inicjowania:  
  
```  
Point pt = Point( 7, 11 );  
```  
  
 Obiekt typu `Point` jest tworzony i zainicjowana przy użyciu konstruktora, który akceptuje dwa argumenty typu `int`.  
  
 Obiekty tworzone przez wywołanie metody konstruktorów jawnie, jak w poprzednich dwóch przykładach są nienazwane i okres istnienia, w którym są tworzone wyrażenia. To jest omówiona szczegółowo w [obiekty tymczasowe](../cpp/temporary-objects.md).  
  
 Zazwyczaj bezpiecznie wywołać jakiegokolwiek funkcji członkowskiej z wewnątrz konstruktora, ponieważ obiekt nie został całkowicie skonfigurowany (tabele wirtualne zainicjowano i tak dalej) przed wykonaniem pierwszy wiersz kodu użytkownika. Jednak jest potencjalnie niebezpieczny dla funkcji członkowskiej do wywoływania funkcji wirtualnego elementu członkowskiego dla abstrakcyjnej klasy podstawowej podczas utworzenia lub zniszczenia.  
  
 Konstruktory można wywołać funkcji wirtualnych. Wywołanego funkcji wirtualnych funkcja wywoływana jest funkcja zdefiniowana dla konstruktora własne klasy (lub dziedziczone z jego typów podstawowych). W poniższym przykładzie pokazano, co się stanie po wywołaniu funkcji wirtualnej z wewnątrz konstruktora:  
  
```  
// specl_calling_virtual_functions.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class Base  
{  
public:  
    Base();             // Default constructor.  
    virtual void f();   // Virtual member function.  
};  
  
Base::Base()  
{  
    cout << "Constructing Base sub-object\n";  
    f();                // Call virtual member function  
}                       //  from inside constructor.  
  
void Base::f()  
{  
    cout << "Called Base::f()\n";  
}  
  
class Derived : public Base  
{  
public:  
    Derived();          // Default constructor.  
    void f();           // Implementation of virtual  
};                      //  function f for this class.  
  
Derived::Derived()  
{  
    cout << "Constructing Derived object\n";  
}  
  
void Derived::f()  
{  
    cout << "Called Derived::f()\n";  
}  
  
int main()  
{  
    Derived d;  
}  
```  
  
 Po poprzednim program jest uruchamiany, deklaracji `Derived d` powoduje, że następująca sekwencja zdarzeń:  
  
1.  Konstruktor klasy `Derived` (`Derived::Derived`) jest wywoływana.  
  
2.  Przed wprowadzeniem treści `Derived` konstruktora klasy, Konstruktor dla klasy `Base` (`Base::Base`) jest wywoływana.  
  
 `Base::Base`wywołuje funkcję `f`, która jest funkcją wirtualną. Zwykle `Derived::f` będzie można wywołać, ponieważ obiekt `d` jest typu `Derived`. Ponieważ `Base::Base` funkcji jest konstruktorem, obiekt nie jest jeszcze `Derived` typu, i `Base::f` jest wywoływana.  
  
