---
title: Inicjatory | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- array-element initializers
- initializing arrays [C++], initializers
- arrays [C++], array-element initializers
- declarators, as initializers
- initializers, array element
ms.assetid: ce301ed8-aa1c-47b2-bb39-9f0541b4af85
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: be05c53e6f41c4df4d62bd4ba1920fcf57c1f0cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="initializers"></a>Inicjatory
Inicjator określa wartość początkową zmiennej. Można zainicjować zmienne w tych kontekstach:  
  
-   W definicji zmiennej:  
  
    ```cpp  
    int i = 3;  
    Point p1{ 1, 2 };  
    ```  
  
-   Jako jeden z parametrów funkcji:  
  
    ```cpp  
    set_point(Point{ 5, 6 });  
    ```  
  
-   Jako wartość zwracana funkcji:  
  
    ```cpp  
    Point get_new_point(int x, int y) { return { x, y }; }  
    Point get_new_point(int x, int y) { return Point{ x, y }; }  
  
    ```  
  
 Inicjatory mogą przybierać następujące formy:  
  
-   Wyrażenie (lub rozdzielana przecinkami lista wyrażeń) w nawiasach:  
  
    ```cpp  
    Point p1(1, 2);  
    ```  
  
-   Znak równości i następujące po nim wyrażenie:  
  
    ```cpp  
    string s = "hello";  
    ```  
  
-   Lista inicjatorów w nawiasach klamrowych. Lista może być pusta lub może składać się z zestawem list, jak w poniższym przykładzie:  
  
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
  
## <a name="kinds-of-initialization"></a>Rodzaje inicjowania  
 Istnieje kilka rodzajów inicjowania, które mogą wystąpić w różnych punktach wykonywania programu. Różne rodzaje inicjowania nie wykluczają się nawzajem — na przykład inicjowanie listy może wywołać inicjowanie wartości, a w innych okolicznościach może wywołać inicjowanie agregacji.  
  
### <a name="zero-initialization"></a>Inicjowanie zero  
 Inicjalizacja wartością zerową to ustawienie zmiennej na wartość zero niejawnie konwertowaną na typ:  
  
-   Zmienne liczbowe są inicjowane na wartość 0 (lub 0,0 lub 0,0000000000 itp.).  
  
-   CHAR zmienne są inicjowane do `'\0'`.  
  
-   Wskaźniki są inicjowane na `nullptr`.  
  
-   Tablice, [POD](../standard-library/is-pod-class.md) klas, struktur i Unii ma ich elementy członkowskie ustawiana na wartość zero.  
  
 Inicjalizacja z wartością zerową odbywa się w różnym czasie:  
  
-   Podczas uruchamiania programu, dla wszystkich zmiennych nazwanych, które mają statyczny czas trwania. Te zmienne mogą być później ponownie zainicjowane.  
  
-   Podczas inicjowania wartości, dla typów skalarnych i typów klasy POD, które są inicjowane za pomocą pustych nawiasów klamrowych.  
  
-   Dla tablic, które mają zainicjowany tylko podzbiór swoich elementów członkowskich.  
  
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
  
### <a name="default_initialization"></a>Inicjowanie domyślnych  
 Inicjowanie domyślnych dla klas, struktur i Unii jest inicjowania przy użyciu domyślnego konstruktora. Brak wyrażenia inicjowania lub z można wywołać konstruktora domyślnego `new` — słowo kluczowe:  
  
```cpp  
MyClass mc1;  
MyClass* mc3 = new MyClass;  
```  
  
 Jeśli klasa, struktura lub unia nie ma domyślnego konstruktora, kompilator generuje błąd.  
  
 Zmienne skalara są domyślnie zainicjowane, gdy są one zdefiniowane z Brak wyrażenia inicjowania. Mają one wartości nieokreślone.  
  
```cpp  
int i1;  
float f;  
char c;  
```  
  
 Tablice są domyślnie zainicjowane, gdy są one zdefiniowane z Brak wyrażenia inicjowania. Gdy tablica jest inicjowany domyślnie, jego elementów członkowskich są domyślnie zainicjowane i mają wartości nieokreślony, jak w poniższym przykładzie:  
  
```cpp  
int int_arr[3];  
```  
  
 Jeśli elementy członkowskie tablicy nie mają domyślnego konstruktora, kompilator generuje błąd.  
  
#### <a name="default-initialization-of-constant-variables"></a>Inicjowanie domyślnych stałych zmiennych  
 Stałe zmienne muszą zostać zadeklarowane wraz z inicjatorem. Jeśli są one typów skalarnych spowodują one wystąpi błąd kompilatora, a jeśli są one typu klasy, które ma domyślnego konstruktora spowodują one ostrzeżenie:  
  
```cpp  
class MyClass{};  
int main() {  
    //const int i2;   // compiler error C2734: const object must be initialized if not extern  
    //const char c2;  // same error  
    const MyClass mc1; // compiler error C4269: 'const automatic data initialized with compiler generated default constructor produces unreliable results  
}  
```  
  
#### <a name="default-initialization-of-static-variables"></a>Inicjowanie domyślnych zmienne statyczne  
 Zmienne statyczne, które są zadeklarowane za pomocą inicjatora nie są inicjowane 0 (niejawnie przekonwertowana na typ).  
  
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
  
 Aby uzyskać więcej informacji o Inicjowanie obiektów globalnych statycznych zobacz [dodatkowe zagadnienia dotyczące uruchamiania](../cpp/additional-startup-considerations.md).  
  
### <a name="value-initialization"></a>Inicjowanie wartości  
 Inicjowanie wartości odbywa się w następujących przypadkach:  
  
-   nazwana wartość została zainicjowana przy użyciu inicjowania pustych nawiasów klamrowych  
  
-   anonimowy obiekt tymczasowy jest zainicjowana przy użyciu pustych nawiasów lub nawiasy klamrowe  
  
-   Obiekt został zainicjowany przy `new` — słowo kluczowe oraz pustych nawiasów lub nawiasów klamrowych  
  
 Inicjowanie wartości wykonuje następujące czynności:  
  
-   dla klas z co najmniej jeden konstruktor publiczny nosi nazwę domyślnego konstruktora  
  
-   dla klas z systemem innym niż Unii z konstruktorów zadeklarowane obiekt jest inicjowany przez zero i nosi nazwę domyślnego konstruktora  
  
-   dla tablic każdy element jest inicjowany przez wartość  
  
-   we wszystkich innych przypadkach zmienna jest zainicjowana zero  
  
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
  
### <a name="copy-initialization"></a>Inicjalizacja kopiowania  
 Inicjalizacja kopiowania jest inicjowania jednego obiektu przy użyciu innego obiektu. Pojawi się w następujących przypadkach:  
  
-   zmienna jest zainicjowana przy użyciu znaku równości  
  
-   argument jest przekazywany do funkcji  
  
-   obiekt jest zwracany przez funkcję  
  
-   zgłoszony lub przechwycił wyjątek  
  
-   elementu członkowskiego danych niestatycznych został zainicjowany przy użyciu znaku równości  
  
-   klasy, struktury i złożenia elementów członkowskich są inicjowane przez Inicjowanie kopiowania podczas inicjowania agregacji. Zobacz [Inicjalizacja agregująca](#agginit) przykłady.  
  
 Poniższy kod przedstawia kilka przykładów Inicjalizacja kopiowania:  
  
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
  
 Inicjalizacja kopiowania nie może wywołać jawnych konstruktorów.  
  
```cpp  
vector<int> v = 10; // the constructor is explicit; compiler error C2440: cannot convert from 'int' to 'std::vector<int,std::allocator<_Ty>>'  
regex r = "a.*b"; // the constructor is explicit; same error  
shared_ptr<int> sp = new int(1729); // the constructor is explicit; same error  
```  
  
 W niektórych przypadkach, jeśli konstruktor kopiujący klasy jest usunięty lub niedostępny, inicjalizacja kopiująca powoduje błąd kompilatora. 
  
### <a name="direct-initialization"></a>Inicjowanie bezpośredniego  
 Inicjowanie bezpośrednie jest inicjowania przy użyciu nawiasach (pusta). W przeciwieństwie do inicjalizacji kopiującej, może wywołać jawne konstruktory. Pojawi się w następujących przypadkach:  
  
-   zmienna jest zainicjowana z niepustym nawiasami  
  
-   zmienna jest zainicjowana z `new` — słowo kluczowe plus niepustym nawiasami  
  
-   zmienna jest zainicjowana z`static_cast`  
  
-   w konstruktorze klasy podstawowe i z systemem innym niż statyczne elementy członkowskie są inicjowane przy użyciu listy inicjatora  
  
-   w kopii przechwyconej zmiennej wewnątrz wyrażenia lambda  
  
 Poniższy kod przedstawia niektóre przykłady bezpośredniego inicjowania:  
  
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
  
### <a name="list-initialization"></a>Inicjalizacja listy  
 Inicjalizacja listy występuje, gdy zmienna jest zainicjowana za pomocą listy inicjalizatora w nawiasach klamrowych. Nawiasach inicjatora list mogą być używane w następujących przypadkach:  
  
-   zmienna jest zainicjowana  
  
-   Klasa jest inicjowany z `new` — słowo kluczowe  
  
-   obiekt jest zwracany przez funkcję  
  
-   argument przekazany do funkcji  
  
-   jeden z argumentów bezpośredniego inicjowania  
  
-   w inicjatorze elementu członkowskiego danych niestatycznych  
  
-   na liście inicjatora konstruktora  
  
 Poniższy kod przedstawia niektóre przykłady Inicjalizacja listy:  
  
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
  
-   nie prywatne lub chronione elementy członkowskie  
  
-   ma konstruktorów dostarczane przez użytkownika, z wyjątkiem konstruktorów jawnie domyślne lub usunięty  
  
-   nie klasy podstawowe  
  
-   nie funkcji wirtualnych elementów członkowskich  
  
> [!NOTE]
>  <!--conformance note-->In Visual Studio 2015 and earlier, an aggregate is not allowed to have  brace-or-equal initializers for non-static members. This restriction was removed in the C++14 standard and implemented in Visual Studio 2017. 
  
 Inicjatory agregacji składają się z listą inicjowanie w nawiasach klamrowych, lub bez znaku równości, jak w poniższym przykładzie:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
struct MyAggregate{  
    int myInt;  
    char myChar;  
};  
  
int main() {  
    MyAggregate agg1{ 1, 'c' };  
  
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
  
 Powinny być widoczne następujące dane wyjściowe:  
  
```  
agg1: c: 1  
agg2: d: 2  
myArr1: 1 2 3 4  
myArr3: 8 9 10 0 0  
```  
  
> [!IMPORTANT]
>  Tablica elementów członkowskich, które są zadeklarowane, ale nie zostało zainicjowane podczas inicjowania agregacji są zero inicjowany, podobnie jak w `myArr3` powyżej.  
  
#### <a name="initializing-unions-and-structs"></a>Inicjowanie Unii i struktur  
 Jeśli Unii nie ma konstruktora, można go zainicjować z pojedynczej wartości (lub z innego wystąpienia Unii). Wartość służy do inicjowania pierwszego pola niestatycznego. Różni się to od inicjowania struktury, w którym pierwsza wartość w inicjatorze służy do inicjowania pierwszego pola, druga do zainicjowania drugiego pola itd. Porównanie inicjowanie Unii i struktur w poniższym przykładzie:  
  
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
  
#### <a name="initializing-aggregates-that-contain-aggregates"></a>Podczas inicjowania agregacji, które zawierają wartości zagregowanych  
 Typy agregacji może zawierać innych typów agregacji dla tablic przykład tablic, tablice struktur i tak dalej. Te typy są inicjowane przy użyciu zagnieżdżonych zestawów nawiasów klamrowych, na przykład:  
  
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
  
```  
// initializing_references.cppint   
int iVar;  
long lVar;  
int main()   
{   long& LongRef1 = lVar;   // No conversion required.  
   long& LongRef2 = iVar;   // C2440  
   const long& LongRef3 = iVar;   // OK  
   LongRef1 = 23L;   // Change lVar through a reference.  
   LongRef2 = 11L;   // Change iVar through a reference.  
   LongRef3 = 11L;   // C3892}  
```  
  
 Jedynym sposobem, aby zainicjować odwołanie tymczasowego obiektu, jest zainicjowanie tymczasowego obiektu stałego. Po zainicjowaniu, zmienna typu odwołania zawsze wskazuje ten sam obiekt; nie można zmodyfikować odwołania do innego obiektu.  
  
 Mimo że składnia może być taka sama, zainicjowanie zmiennych typu odwołania i przypisanie do zmiennych typu odwołania są semantycznie różne. W poprzednim przykładzie, przydziały, które zmieniają `iVar` i `lVar` wyglądają podobnie do inicjalizacji, ale dają różne efekty. Inicjalizacja określa obiekt, na który wskazuje zmienna typu odwołania; przypisanie przypisuje do określonego obiektu poprzez odniesienie.  
  
 Ponieważ zarówno przekazywanie argumentu typu odwołania do funkcji i zwracanie wartości typu odwołania przez funkcję są inicjalizacjami, formalne argumenty do funkcji są inicjowane poprawnie podczas zwracania odwołania.  
  
 Zmienna typu odwołania może być deklarowana bez inicjatorów tylko w następujących przypadkach:  
  
-   Deklaracje funkcji (prototypy). Na przykład:  
  
    ```  
    int func( int& );  
    ```  
  
-   Deklaracje typu funkcji zwracanej. Na przykład:  
  
    ```  
    int& func( int& );  
    ```  
  
-   Deklaracja składowej klasy typu odwołania. Na przykład:  
  
    ```  
    class c {public:   int& i;};  
    ```  
  
-   Jawna deklaracja zmiennej określonej jako `extern`. Na przykład:  
  
    ```  
    extern int& iVal;  
    ```  
  
 Podczas inicjowania zmiennej typu odwołania, kompilator używa wykresu decyzji pokazanego na poniższym rysunku, aby wybrać między utworzeniem odwołania do obiektu a tymczasowym obiektem, który wskazuje odwołanie.  
  
 ![Wykres decyzji inicjowania typu ref](../cpp/media/vc38s71.gif "vc38S71")  
Wykres decyzji dla inicjowania typów referencyjnych  
  
 Odwołuje się do `volatile` typów (zadeklarowany jako `volatile` *typename*  **&**  *identyfikator*) mogą być inicjowane z `volatile` obiekty tego samego typu lub obiektami, które nie zostały zgłoszone jako `volatile`. Nie można jednak, można zainicjować przy użyciu **const** obiekty tego typu. Podobnie, odwołuje się do **const** typów (zadeklarowany jako **const** *typename*  **&**  *identyfikator* ) mogą być inicjowane z **const** obiekty tego samego typu (lub wszystkie elementy, które ma konwersji do typu lub obiektami, które nie zostały zgłoszone jako **const**). Nie mogą one jednak być inicjowane z obiektami `volatile` tego typu.  
  
 Odwołania, które nie jest kwalifikowany za pomocą albo **const** lub `volatile` — słowo kluczowe mogą być inicjowane tylko z obiektami zadeklarowany jako ani **const** ani `volatile`.  
  
### <a name="initialization-of-external-variables"></a>Inicjowanie zmiennych zewnętrznych  
 Deklaracje zmiennych automatycznych, statyczne i zewnętrzne mogą zawierać inicjatory. Deklaracje zmiennych zewnętrznych może jednak zawierać inicjatory tylko wtedy, gdy zmienne nie są deklarowane jako `extern`.
  
