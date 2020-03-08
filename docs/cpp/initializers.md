---
title: Inicjatory
ms.date: 07/29/2019
description: Jak zainicjować klasy, struktury, tablice i podstawowe typy w C++.
helpviewer_keywords:
- arrays [C++], array-element initializers
- aggregate initializers [C++]
ms.assetid: ce301ed8-aa1c-47b2-bb39-9f0541b4af85
ms.openlocfilehash: 2cc68f2384402ce1eb3ac06b414f597a6b3951f0
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865791"
---
# <a name="initializers"></a>Inicjatory

Inicjator określa wartość początkową zmiennej. Można zainicjować zmienne w tych kontekstach:

- W definicji zmiennej:

    ```cpp
    int i = 3;
    Point p1{ 1, 2 };
    ```

- Jako jeden z parametrów funkcji:

    ```cpp
    set_point(Point{ 5, 6 });
    ```

- Jako wartość zwracana funkcji:

    ```cpp
    Point get_new_point(int x, int y) { return { x, y }; }
    Point get_new_point(int x, int y) { return Point{ x, y }; }
    ```

Inicjatory mogą przybierać następujące formy:

- Wyrażenie (lub rozdzielana przecinkami lista wyrażeń) w nawiasach:

    ```cpp
    Point p1(1, 2);
    ```

- Znak równości i następujące po nim wyrażenie:

    ```cpp
    string s = "hello";
    ```

- Lista inicjatorów w nawiasach klamrowych. Lista może być pusta lub może składać się z zestawu list, jak w poniższym przykładzie:

    ```cpp
    struct Point{
        int x;
        int y;
    };
    class PointConsumer{
    public:
        void set_point(Point p){};
        void set_points(initializer_list<Point> my_list){};
    };
    int main() {
        PointConsumer pc{};
        pc.set_point({});
        pc.set_point({ 3, 4 });
        pc.set_points({ { 3, 4 }, { 5, 6 } });
    }
    ```

## <a name="kinds-of-initialization"></a>Rodzaje inicjacji

Istnieje kilka rodzajów inicjowania, które mogą wystąpić w różnych punktach wykonywania programu. Różne rodzaje inicjowania nie wykluczają się nawzajem — na przykład inicjowanie listy może wywołać inicjowanie wartości, a w innych okolicznościach może wywołać inicjowanie agregacji.

### <a name="zero-initialization"></a>Inicjowanie zerowe

Inicjalizacja wartością zerową to ustawienie zmiennej na wartość zero niejawnie konwertowaną na typ:

- Zmienne liczbowe są inicjowane na wartość 0 (lub 0,0 lub 0,0000000000 itp.).

- Zmienne char są inicjowane w celu `'\0'`.

- Wskaźniki są inicjowane do **nullptr**.

- W tablicach [, klasach,](../standard-library/is-pod-class.md) strukturach i związkach ich składowe zostały zainicjowane do wartości zerowej.

Inicjalizacja z wartością zerową odbywa się w różnym czasie:

- Podczas uruchamiania programu, dla wszystkich zmiennych nazwanych, które mają statyczny czas trwania. Te zmienne mogą być później ponownie zainicjowane.

- Podczas inicjowania wartości, dla typów skalarnych i typów klasy POD, które są inicjowane za pomocą pustych nawiasów klamrowych.

- Dla tablic, które mają zainicjowany tylko podzbiór swoich elementów członkowskich.

Oto kilka przykładów inicjalizacji z wartością zerową:

```cpp
struct my_struct{
    int i;
    char c;
};

int i0;              // zero-initialized to 0
int main() {
    static float f1;  // zero-initialized to 0.000000000
    double d{};     // zero-initialized to 0.00000000000000000
    int* ptr{};     // initialized to nullptr
    char s_array[3]{'a', 'b'};  // the third char is initialized to '\0'
    int int_array[5] = { 8, 9, 10 };  // the fourth and fifth ints are initialized to 0
    my_struct a_struct{};   // i = 0, c = '\0'
}
```

### <a name="default_initialization"></a>Domyślna Inicjalizacja

Domyślna Inicjalizacja klas, struktur i Unii jest inicjowana przy użyciu domyślnego konstruktora. Konstruktor domyślny można wywołać bez wyrażenia inicjowania lub za pomocą słowa kluczowego **New** :

```cpp
MyClass mc1;
MyClass* mc3 = new MyClass;
```

Jeśli klasa, struktura lub unia nie ma domyślnego konstruktora, kompilator generuje błąd.

Zmienne skalarne są inicjowane domyślnie, gdy są zdefiniowane bez wyrażenia inicjowania. Mają one wartości nieokreślone.

```cpp
int i1;
float f;
char c;
```

Tablice są inicjowane domyślnie, gdy są zdefiniowane bez wyrażenia inicjowania. Gdy tablica jest inicjowana domyślnie, jej składowe są domyślnie inicjowane i mają wartości nieokreślone, jak w poniższym przykładzie:

```cpp
int int_arr[3];
```

Jeśli elementy członkowskie tablicy nie mają domyślnego konstruktora, kompilator generuje błąd.

#### <a name="default-initialization-of-constant-variables"></a>Domyślna Inicjalizacja zmiennych stałych

Stałe zmienne muszą zostać zadeklarowane wraz z inicjatorem. Jeśli są to typy skalarne powodujące błąd kompilatora, a jeśli są typami klas, które mają Konstruktor domyślny, powodują Ostrzeżenie:

```cpp
class MyClass{};
int main() {
    //const int i2;   // compiler error C2734: const object must be initialized if not extern
    //const char c2;  // same error
    const MyClass mc1; // compiler error C4269: 'const automatic data initialized with compiler generated default constructor produces unreliable results
}
```

#### <a name="default-initialization-of-static-variables"></a>Domyślne Inicjowanie zmiennych statycznych

Zmienne statyczne, które są zadeklarowane bez inicjatora są inicjowane do wartości 0 (niejawnie konwertowane na typ).

```cpp
class MyClass {
private:
    int m_int;
    char m_char;
};

int main() {
    static int int1;       // 0
    static char char1;     // '\0'
    static bool bool1;   // false
    static MyClass mc1;     // {0, '\0'}
}
```

Aby uzyskać więcej informacji na temat inicjowania globalnych obiektów statycznych, zobacz [Główne funkcje i argumenty wiersza polecenia](main-function-command-line-args.md).

### <a name="value-initialization"></a>Inicjowanie wartości

Inicjalizacja wartości występuje w następujących przypadkach:

- nazwana wartość jest inicjowana za pomocą pustego nawiasu klamrowego

- Anonimowy obiekt tymczasowy jest inicjowany za pomocą pustych nawiasów lub nawiasów klamrowych

- Obiekt jest inicjowany za pomocą słowa kluczowego **New** i pustych nawiasów lub nawiasów klamrowych

Inicjalizacja wartości wykonuje następujące czynności:

- dla klas z co najmniej jednym konstruktorem publicznym wywoływany jest Konstruktor domyślny

- dla klas nienależących do Unii bez zadeklarowanych konstruktorów obiekt jest inicjowany od zera i Konstruktor domyślny jest wywoływany

- w przypadku tablic każdy element jest inicjowany przez wartość

- we wszystkich innych przypadkach zmienna jest inicjowana zero

```cpp
class BaseClass {
private:
    int m_int;
};

int main() {
    BaseClass bc{};     // class is initialized
    BaseClass*  bc2 = new BaseClass();  // class is initialized, m_int value is 0
    int int_arr[3]{};  // value of all members is 0
    int a{};     // value of a is 0
    double b{};  // value of b is 0.00000000000000000
}
```

### <a name="copy-initialization"></a>Kopiuj inicjalizację

Inicjalizacja kopiowania jest inicjalizacją jednego obiektu przy użyciu innego obiektu. Występuje w następujących przypadkach:

- Zmienna jest inicjowana przy użyciu znaku równości

- do funkcji jest przenoszona argument

- Obiekt jest zwracany z funkcji

- wyjątek jest zgłaszany lub przechwytywany

- niestatyczny element członkowski danych jest inicjowany przy użyciu znaku równości

- elementy członkowskie klasy, struktury i Unii są inicjowane przez inicjalizację kopiowania podczas inicjowania agregacji. Przykłady można znaleźć w temacie [Inicjalizacja agregacji](#agginit) .

Poniższy kod pokazuje kilka przykładów inicjalizacji kopiowania:

```cpp
#include <iostream>
using namespace std;

class MyClass{
public:
    MyClass(int myInt) {}
    void set_int(int myInt) { m_int = myInt; }
    int get_int() const { return m_int; }
private:
    int m_int = 7; // copy initialization of m_int

};
class MyException : public exception{};
int main() {
    int i = 5;              // copy initialization of i
    MyClass mc1{ i };
    MyClass mc2 = mc1;      // copy initialization of mc2 from mc1
    MyClass mc1.set_int(i);    // copy initialization of parameter from i
    int i2 = mc2.get_int(); // copy initialization of i2 from return value of get_int()

    try{
        throw MyException();
    }
    catch (MyException ex){ // copy initialization of ex
        cout << ex.what();
    }
}
```

Inicjalizacja kopiowania nie może wywoływać jawnych konstruktorów.

```cpp
vector<int> v = 10; // the constructor is explicit; compiler error C2440: cannot convert from 'int' to 'std::vector<int,std::allocator<_Ty>>'
regex r = "a.*b"; // the constructor is explicit; same error
shared_ptr<int> sp = new int(1729); // the constructor is explicit; same error
```

W niektórych przypadkach, jeśli konstruktor kopiujący klasy jest usunięty lub niedostępny, inicjalizacja kopiująca powoduje błąd kompilatora.

### <a name="direct-initialization"></a>Inicjowanie bezpośrednie

Inicjalizacja bezpośrednia jest inicjowana za pomocą (Niepuste) nawiasów klamrowych lub nawiasów. W przeciwieństwie do inicjalizacji kopiującej, może wywołać jawne konstruktory. Występuje w następujących przypadkach:

- Zmienna jest inicjowana z niepustymi nawiasami klamrowymi lub nawiasami

- Zmienna jest inicjowana za pomocą słowa kluczowego **New** i niepustych nawiasów klamrowych lub nawiasów

- Zmienna jest inicjowana za pomocą **static_cast**

- w konstruktorze klasy bazowe i niestatyczne składowe są inicjowane za pomocą listy inicjalizatora

- w kopii przechwyconej zmiennej wewnątrz wyrażenia lambda

Poniższy kod przedstawia kilka przykładów inicjalizacji bezpośredniej:

```cpp
class BaseClass{
public:
    BaseClass(int n) :m_int(n){} // m_int is direct initialized
private:
    int m_int;
};

class DerivedClass : public BaseClass{
public:
    // BaseClass and m_char are direct initialized
    DerivedClass(int n, char c) : BaseClass(n), m_char(c) {}
private:
    char m_char;
};
int main(){
    BaseClass bc1(5);
    DerivedClass dc1{ 1, 'c' };
    BaseClass* bc2 = new BaseClass(7);
    BaseClass bc3 = static_cast<BaseClass>(dc1);

    int a = 1;
    function<int()> func = [a](){  return a + 1; }; // a is direct initialized
    int n = func();
}
```

### <a name="list-initialization"></a>Inicjowanie listy

Inicjalizacja listy występuje, gdy zmienna jest inicjowana za pomocą listy inicjalizatora w nawiasach klamrowych. Listy inicjalizatora w nawiasach klamrowych mogą być używane w następujących przypadkach:

- Zmienna jest inicjowana

- Klasa jest inicjowana za pomocą słowa kluczowego **New**

- Obiekt jest zwracany z funkcji

- argument przesłany do funkcji

- jeden z argumentów w inicjacji bezpośredniej

- w inicjatorze niestatycznej składowej danych

- na liście inicjatora konstruktora

Poniższy kod przedstawia kilka przykładów inicjalizacji listy:

```cpp
class MyClass {
public:
    MyClass(int myInt, char myChar) {}
private:
    int m_int[]{ 3 };
    char m_char;
};
class MyClassConsumer{
public:
    void set_class(MyClass c) {}
    MyClass get_class() { return MyClass{ 0, '\0' }; }
};
struct MyStruct{
    int my_int;
    char my_char;
    MyClass my_class;
};
int main() {
    MyClass mc1{ 1, 'a' };
    MyClass* mc2 = new MyClass{ 2, 'b' };
    MyClass mc3 = { 3, 'c' };

    MyClassConsumer mcc;
    mcc.set_class(MyClass{ 3, 'c' });
    mcc.set_class({ 4, 'd' });

    MyStruct ms1{ 1, 'a', { 2, 'b' } };
}
```

### <a name="agginit"></a>Inicjalizacja agregacji

Inicjalizacja agregacji jest formą inicjalizacji listy dla tablic lub typów klas (zwykle struktur lub unii), które:

- Brak prywatnych lub chronionych składowych

- Brak konstruktorów dostarczonych przez użytkownika, z wyjątkiem jawnie domyślnych lub usuniętych konstruktorów

- Brak klas bazowych

- Brak wirtualnych funkcji Członkowskich

> [!NOTE]
> <!--conformance note-->W programie Visual Studio 2015 i starszych funkcja agregująca nie może mieć inicjatorów w nawiasach klamrowych i niestatycznych elementów członkowskich. To ograniczenie zostało usunięte w standardzie C++ 14 i zaimplementowane w programie Visual Studio 2017.

Inicjatory agregujące składają się z listy inicjalizacji z nawiasami klamrowymi, z lub bez znaku równości, tak jak w poniższym przykładzie:

```cpp
#include <iostream>
using namespace std;

struct MyAggregate{
    int myInt;
    char myChar;
};

struct MyAggregate2{
    int myInt;
    char myChar = 'Z'; // member-initializer OK in C++14
};

int main() {
    MyAggregate agg1{ 1, 'c' };
    MyAggregate2 agg2{2};
    cout << "agg1: " << agg1.myChar << ": " << agg1.myInt << endl;
    cout << "agg2: " << agg2.myChar << ": " << agg2.myInt << endl;

    int myArr1[]{ 1, 2, 3, 4 };
    int myArr2[3] = { 5, 6, 7 };
    int myArr3[5] = { 8, 9, 10 };

    cout << "myArr1: ";
    for (int i : myArr1){
        cout << i << " ";
    }
    cout << endl;

    cout << "myArr3: ";
    for (auto const &i : myArr3) {
        cout << i << " ";
    }
    cout << endl;
}
```

Powinny zostać wyświetlone następujące dane wyjściowe:

```Output
agg1: c: 1
agg2: Z: 2
myArr1: 1 2 3 4
myArr3: 8 9 10 0 0
```

> [!IMPORTANT]
> Elementy członkowskie tablicy, które są zadeklarowane, ale nie są jawnie inicjowane podczas inicjowania agregacji, są inicjowane od zera, jak w `myArr3` powyżej.

#### <a name="initializing-unions-and-structs"></a>Inicjowanie Unii i struktur

Jeśli Unia nie ma konstruktora, można ją zainicjować za pomocą pojedynczej wartości (lub z innym wystąpieniem Unii). Wartość służy do inicjowania pierwszego pola niestatycznego. Różni się to od inicjowania struktury, w którym pierwsza wartość w inicjatorze służy do inicjowania pierwszego pola, druga do zainicjowania drugiego pola itd. Porównaj inicjalizacje Unii i struktur w następującym przykładzie:

```cpp
struct MyStruct {
    int myInt;
    char myChar;
};
union MyUnion {
    int my_int;
    char my_char;
    bool my_bool;
    MyStruct my_struct;
};

int main() {
    MyUnion mu1{ 'a' };  // my_int = 97, my_char = 'a', my_bool = true, {myInt = 97, myChar = '\0'}
    MyUnion mu2{ 1 };   // my_int = 1, my_char = 'x1', my_bool = true, {myInt = 1, myChar = '\0'}
    MyUnion mu3{};      // my_int = 0, my_char = '\0', my_bool = false, {myInt = 0, myChar = '\0'}
    MyUnion mu4 = mu3;  // my_int = 0, my_char = '\0', my_bool = false, {myInt = 0, myChar = '\0'}
    //MyUnion mu5{ 1, 'a', true };  // compiler error: C2078: too many initializers
    //MyUnion mu6 = 'a';            // compiler error: C2440: cannot convert from 'char' to 'MyUnion'
    //MyUnion mu7 = 1;              // compiler error: C2440: cannot convert from 'int' to 'MyUnion'

    MyStruct ms1{ 'a' };            // myInt = 97, myChar = '\0'
    MyStruct ms2{ 1 };              // myInt = 1, myChar = '\0'
    MyStruct ms3{};                 // myInt = 0, myChar = '\0'
    MyStruct ms4{1, 'a'};           // myInt = 1, myChar = 'a'
    MyStruct ms5 = { 2, 'b' };      // myInt = 2, myChar = 'b'
}
```

#### <a name="initializing-aggregates-that-contain-aggregates"></a>Inicjowanie agregacji zawierających wartości zagregowane

Typy agregacji mogą zawierać inne typy agregacji, na przykład tablice tablic, tablice struktur itd. Te typy są inicjowane przy użyciu zagnieżdżonych zestawów nawiasów klamrowych, na przykład:

```cpp
struct MyStruct {
    int myInt;
    char myChar;
};
int main() {
    int intArr1[2][2]{{ 1, 2 }, { 3, 4 }};
    int intArr3[2][2] = {1, 2, 3, 4};
    MyStruct structArr[]{ { 1, 'a' }, { 2, 'b' }, {3, 'c'} };
}
```

### <a name="reference-initialization"></a>Inicjowanie odwołania

Zmienne typu referencyjnego muszą być inicjowane z obiektem typu, który dziedziczy ten typ referencyjny lub obiektem typu, który może zostać przekonwertowany na typ, z którego dziedziczy typ referencyjny. Na przykład:

```cpp
// initializing_references.cpp
int iVar;
long lVar;
int main()
{
    long& LongRef1 = lVar;        // No conversion required.
    long& LongRef2 = iVar;        // Error C2440
    const long& LongRef3 = iVar;  // OK
    LongRef1 = 23L;               // Change lVar through a reference.
    LongRef2 = 11L;               // Change iVar through a reference.
    LongRef3 = 11L;               // Error C3892
}
```

Jedynym sposobem, aby zainicjować odwołanie tymczasowego obiektu, jest zainicjowanie tymczasowego obiektu stałego. Po zainicjowaniu, zmienna typu odwołania zawsze wskazuje ten sam obiekt; nie można zmodyfikować odwołania do innego obiektu.

Mimo że składnia może być taka sama, zainicjowanie zmiennych typu odwołania i przypisanie do zmiennych typu odwołania są semantycznie różne. W poprzednim przykładzie, przydziały, które zmieniają `iVar` i `lVar` wyglądają podobnie do inicjalizacji, ale dają różne efekty. Inicjalizacja określa obiekt, na który wskazuje zmienna typu odwołania; przypisanie przypisuje do określonego obiektu poprzez odniesienie.

Ponieważ zarówno przekazywanie argumentu typu odwołania do funkcji i zwracanie wartości typu odwołania przez funkcję są inicjalizacjami, formalne argumenty do funkcji są inicjowane poprawnie podczas zwracania odwołania.

Zmienna typu odwołania może być deklarowana bez inicjatorów tylko w następujących przypadkach:

- Deklaracje funkcji (prototypy). Na przykład:

    ```cpp
    int func( int& );
    ```

- Deklaracje typu funkcji zwracanej. Na przykład:

    ```cpp
    int& func( int& );
    ```

- Deklaracja składowej klasy typu odwołania. Na przykład:

    ```cpp
    class c {public:   int& i;};
    ```

- Deklaracja zmiennej jawnie określona jako **extern**. Na przykład:

    ```cpp
    extern int& iVal;
    ```

Podczas inicjowania zmiennej typu odwołania, kompilator używa wykresu decyzji pokazanego na poniższym rysunku, aby wybrać między utworzeniem odwołania do obiektu a tymczasowym obiektem, który wskazuje odwołanie.

![Wykres decyzyjny na potrzeby inicjalizacji typów referencyjnych](../cpp/media/vc38s71.gif "Wykres decyzyjny na potrzeby inicjalizacji typów referencyjnych") <br/>
Wykres decyzyjny na potrzeby inicjalizacji typów referencyjnych

Odwołania do typów **nietrwałych** (zadeklarowanych jako **volatile** *TypeName* <strong>&</strong> *Identyfikator*) można zainicjować przy użyciu obiektów **nietrwałych** tego samego typu lub obiektów, które nie zostały zadeklarowane jako **nietrwałe**. Nie mogą jednak być inicjowane z obiektami **const** tego typu. Podobnie odwołania do typów **stałych** (zadeklarowanych jako **const** *TypeName* <strong>&</strong> *Identifier*) mogą być inicjowane przy użyciu obiektów **const** tego samego typu (lub wszystkich elementów, które mają konwersję tego typu lub z obiektami, które nie zostały zadeklarowane jako **const**). Nie mogą jednak być inicjowane z obiektami **nietrwałymi** tego typu.

Odwołania, które nie są kwalifikowane za pomocą słowa kluczowego **const** lub **volatile** , mogą być inicjowane tylko z obiektami zadeklarowanymi jako ani **const** lub **volatile**.

### <a name="initialization-of-external-variables"></a>Inicjalizacja zmiennych zewnętrznych

Deklaracje zmiennych automatycznych, statycznych i zewnętrznych mogą zawierać inicjatory. Jednakże deklaracje zmiennych zewnętrznych mogą zawierać inicjatory tylko wtedy, gdy zmienne nie są zadeklarowane jako **extern**.
