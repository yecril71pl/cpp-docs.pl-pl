---
title: "Przeciążanie funkcji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 1/25/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function overloading [C++], about function overloading
- function overloading
- declaring functions [C++], overloading
ms.assetid: 3c9884cb-1d5e-42e8-9a49-6f46141f929e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d21ecfb649748c9bf7e190d4857ce93ebee61dd1
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="function-overloading"></a>Przeładowywanie funkcji
C++ umożliwia określenie więcej niż jednej funkcji o tej samej nazwie w tym samym zakresie. Są one nazywane *przeciążony* funkcji. Funkcje przeciążone umożliwiają podać semantykę różną dla funkcji, w zależności od typów i liczby argumentów. 
  
 Na przykład **drukowanie** funkcja, która przyjmuje **std::string** argument może wykonywać bardzo różnych zadań niż jeden, który przyjmuje argument typu **podwójne**. Przeciążanie pozwala uniknąć konieczności użycia nazwy, takie jak `print_string` lub `print_double`. W czasie kompilacji wybierze kompilator które przeładowanie do użycia na podstawie typu argumentów przekazany przez wywołującego.  Jeśli należy wywołać **print(42.0)** , a następnie **void drukowania (dwa razy d)** funkcja zostanie wywołana. Jeśli należy wywołać **drukowania (tekst "hello world")** , a następnie **void print(std::string)** przeciążenia zostanie wywołany.

Można przeciążać zarówno funkcji Członkowskich i funkcji z systemem innym niż elementów członkowskich. W poniższej tabeli przedstawiono, które części deklaracji funkcji język C++ używa do rozróżniania grup funkcji o tej samej nazwie w tym samym zakresie.  
  
### <a name="overloading-considerations"></a>Zagadnienia przeciążania  
  
|Element deklaracji funkcji|Używany w przeciążaniu?|  
|----------------------------------|---------------------------|  
|Typ zwracany przez funkcję|Nie|  
|Liczba argumentów|Tak|  
|Typ argumentów|Tak|  
|Obecność lub brak wielokropka|Tak|  
|Korzystanie z nazw `typedef`|Nie|  
|Nieokreślone granice tablic|Nie|  
|**Const** lub `volatile`|Tak, gdy jest stosowany do całej funkcji|
|[ref-qualifier](#ref-qualifier)|Tak|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób użycia przeciążenia.  
  
```  
// function_overloading.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <math.h>  
#include <string>

// Prototype three print functions.  
int print(std::string s);             // Print a string.  
int print(double dvalue);            // Print a double.  
int print(double dvalue, int prec);  // Print a double with a  
                                     //  given precision.  
using namespace std;
int main(int argc, char *argv[])
{
    const double d = 893094.2987;
    if (argc < 2)
    {
        // These calls to print invoke print( char *s ).  
        print("This program requires one argument.");
        print("The argument specifies the number of");
        print("digits precision for the second number");
        print("printed.");
        exit(0);
    }

    // Invoke print( double dvalue ).  
    print(d);

    // Invoke print( double dvalue, int prec ).  
    print(d, atoi(argv[1]));
}

// Print a string.  
int print(string s)
{
    cout << s << endl;
    return cout.good();
}

// Print a double in default precision.  
int print(double dvalue)
{
    cout << dvalue << endl;
    return cout.good();
}

//  Print a double in specified precision.  
//  Positive numbers for precision indicate how many digits  
//  precision after the decimal point to show. Negative  
//  numbers for precision indicate where to round the number  
//  to the left of the decimal point.  
int print(double dvalue, int prec)
{
    // Use table-lookup for rounding/truncation.  
    static const double rgPow10[] = {
        10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1, 
        10E0, 10E1,  10E2,  10E3,  10E4, 10E5,  10E6 };
    const int iPowZero = 6;

    // If precision out of range, just print the number.  
    if (prec < -6 || prec > 7)
    {
        return print(dvalue);
    }
    // Scale, truncate, then rescale.  
    dvalue = floor(dvalue / rgPow10[iPowZero - prec]) *
        rgPow10[iPowZero - prec];
    cout << dvalue << endl;
    return cout.good();
}  
```  
  
 Poprzedni kod pokazuje przeciążenie funkcji `print` w zakresie pliku.  
  
 Argument domyślny nie jest uważany za część typu funkcji. W związku z tym nie służy w wyborze przeciążonej funkcji. Dwie funkcje, które różnią się tylko w ich argumenty domyślne są traktowane jako wiele definicji zamiast przeciążonej funkcji.  
  
 Argumenty domyślne nie mogą być dostarczane na potrzeby operatory przeciążone.  
  
  
## <a name="argument-matching"></a>Dopasowywanie argumentów  
 Funkcje przeciążone zostały wybrane do najlepsze dopasowanie deklaracje funkcji w bieżącym zakresie do argumentów w wywołaniu funkcji. Jeśli odpowiedniej funkcji zostanie znaleziony, że funkcja jest wywoływana. W tym kontekście "odpowiednie" oznacza jedną z następujących czynności:  
  
-   Znaleziono dokładnego dopasowania.  
  
-   Prosta konwersji została wykonana.  
  
-   Promocję typu całkowitego została wykonana.  
  
-   Konwersja standardowa do typu argumentu żądaną istnieje.  
  
-   Zdefiniowane przez użytkownika konwersja (operator konwersji lub konstruktora) na typ argumentu żądaną istnieje.  
  
-   Znaleziono reprezentowany przez wielokropek argumentów.  
  
 Kompilator tworzy zbiór candidate funkcje dla każdego argumentu. Funkcje kandydujące są funkcje, w których rzeczywisty argument w tym miejscu można przekonwertować na typ formalnego argumentu.  
  
 Zestaw "najbardziej pasującym funkcji" jest przeznaczony dla każdego argumentu i wybranej funkcji jest część wspólną wszystkich zestawów. Jeśli część wspólną zawiera więcej niż jedną funkcję, przeładowanie jest niejednoznaczne i generuje błąd. Funkcja ostatecznie wybranego zawsze jest lepszym dopasowaniem niż co innych funkcji, w grupie co najmniej jednego argumentu. Wywołanie funkcji generuje błąd, jeśli nie jest to wymagane (Jeśli nie jest brak wyczyść wygrał użytkownik).  
  
 Należy wziąć pod uwagę następujące deklaracje (funkcje są oznaczone `Variant 1`, `Variant 2`, i `Variant 3`, do identyfikacji w następujących dyskusji):  
  
```  
Fraction &Add( Fraction &f, long l );       // Variant 1  
Fraction &Add( long l, Fraction &f );       // Variant 2  
Fraction &Add( Fraction &f, Fraction &f );  // Variant 3  
  
Fraction F1, F2;  
```  
  
 Należy wziąć pod uwagę następująca instrukcja:  
  
```  
F1 = Add( F2, 23 );  
```  
  
 Powyższych instrukcji tworzy dwa zestawy:  
  
|Zestaw 1: Candidate funkcje, które mają pierwszy Argument typu ułamka|Zestaw 2: Candidate funkcje Whose drugi Argument można przekonwertować na typ int|  
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Wariant 1|Variant 1 (`int` może zostać przekonwertowany na `long` za pomocą konwersji standardowej)|  
|Variant 3||  
  
 Funkcje w wersji 2 ustawić są funkcje, dla której są niejawną konwersję z typu rzeczywisty parametr formalny parametr typu i między takie funkcje to funkcja, dla którego jest "koszt" Konwertowanie typu rzeczywistego parametru na jego typ parametrów formalnych najmniejszy.  
  
 Część wspólną tych dwóch zestawów to Variant 1. Przykład wywołania funkcji niejednoznaczne to:  
  
```  
F1 = Add( 3, 6 );  
```  
  
 Poprzednie wywołanie funkcji kompilacje następujących zestawów:  
  
|Zestaw 1: Candidate funkcji czy mieć pierwszy Argument typu int|Zestaw 2: Candidate funkcji czy mieć drugi Argument typu int|  
|---------------------------------------------------------------------|----------------------------------------------------------------------|  
|Variant 2 (`int` może zostać przekonwertowany na `long` za pomocą konwersji standardowej)|Variant 1 (`int` może zostać przekonwertowany na `long` za pomocą konwersji standardowej)|  
  
 Należy pamiętać, że przecięcia między dwoma zestawami jest pusty. W związku z tym kompilator generuje komunikat o błędzie.  
  
 Dla argumentu dopasowania, funkcja z *n* argumenty domyślne są traktowane jako *n*funkcji oddzielne + 1, każda z różną liczbą argumentów.  
  
 Działa wielokropek (...) jako symbolu wieloznacznego, jest on zgodny z dowolnym rzeczywisty argument. Może to prowadzić do wielu zestawów niejednoznaczny, nie projektowania sieci przeciążona funkcja zestawów z rozwagą.  
  
> [!NOTE]
>  Nie można określić niejednoznaczności przeciążonej funkcji, dopóki napotkano wywołania funkcji. W tym momencie zestawy są tworzone dla każdej argument w wywołaniu funkcji, a następnie można określić, czy istnieje jednoznaczne przeciążenia. Oznacza to, że niejednoznaczności może pozostawać w kodzie, dopóki nie są one przywołane przez wywołanie określonej funkcji.  
  
## <a name="argument-type-differences"></a>Różnice typu argumentów  
 Funkcje przeciążone odróżnić typy argumentów, przyjmujących różnych inicjatory. W związku z tym argument danego typu i odwołanie do tego typu są traktowane jako takie same na potrzeby logowania. Są one uznawane za takie same, ponieważ ich wejściem w tym samym inicjatory. Na przykład `max( double, double )` jest uznawany za taki sam jak `max( double &, double & )`. Deklarowanie dwóch takich funkcji powoduje błąd.  
  
 Z tego samego powodu funkcji argumentów typu, który został zmodyfikowany przez **const** lub `volatile` nie są traktowane inaczej niż typu podstawowego na potrzeby logowania.  
  
 Jednak funkcja przeładowanie mechanizmu można rozróżnić odwołań, które jest kwalifikowana **const** i `volatile` i odwołania do typu podstawowego. Dzięki temu kodu, takie jak następujące możliwości:  
  
```  
// argument_type_differences.cpp  
// compile with: /EHsc /W3  
// C4521 expected  
#include <iostream>  
  
using namespace std;  
class Over {  
public:  
   Over() { cout << "Over default constructor\n"; }  
   Over( Over &o ) { cout << "Over&\n"; }  
   Over( const Over &co ) { cout << "const Over&\n"; }  
   Over( volatile Over &vo ) { cout << "volatile Over&\n"; }  
};  
  
int main() {  
   Over o1;            // Calls default constructor.  
   Over o2( o1 );      // Calls Over( Over& ).  
   const Over o3;      // Calls default constructor.  
   Over o4( o3 );      // Calls Over( const Over& ).  
   volatile Over o5;   // Calls default constructor.  
   Over o6( o5 );      // Calls Over( volatile Over& ).  
}  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
Over default constructor  
Over&  
Over default constructor  
const Over&  
Over default constructor  
volatile Over&  
```  
  
 Wskaźniki do **const** i `volatile` obiekty są także traktowane jako inny niż wskaźniki do typu podstawowego na potrzeby logowania.  
  
## <a name="argument-matching-and-conversions"></a>Konwersje i dopasowania argumentów  
 Próba odpowiada argumenty rzeczywiste względem argumentów w deklaracji funkcji przez kompilator go dostarczyć standard lub zdefiniowanych przez użytkownika konwersje Aby uzyskać poprawny typ, jeśli nie znaleziono dokładnego dopasowania mogą być. Aplikacja konwersji podlega te reguły:  
  
-   Nie są uznawane za sekwencji konwersje, które zawierają więcej niż jeden konwersji zdefiniowanej przez użytkownika.  
  
-   Sekwencje konwersje, które zostać skrócony przez usunięcie konwersje pośrednie nie są uwzględniane.  
  
 Wynikowe sekwencji konwersji, jeśli taki występuje, jest nazywany najlepiej dopasowaną sekwencji. Istnieje kilka sposobów, aby przekonwertować obiektu typu `int` na typ `unsigned long` przy użyciu standardowych konwersji (opisany w [konwersje standardowe](../cpp/standard-conversions.md)):  
  
-   Konwertowanie z `int` do `long` , a następnie z `long` do `unsigned long`.  
  
-   Konwertowanie z `int` do `unsigned long`.  
  
 Pierwszy sekwencji, mimo że jego osiąga żądany cel, nie jest najlepiej dopasowaną sekwencji — sekwencja krótszą istnieje.  
  
 W poniższej tabeli przedstawiono grupy konwersji, nazywany trivial konwersje, które mają ograniczony wpływ na temat określania, które sekwencja jest najlepsze dopasowanie. Na liście w poniższej tabeli opisano wystąpień, w których trivial konwersje wpłynąć na wybór sekwencji.  
  
### <a name="trivial-conversions"></a>Prosta konwersje  
  
|Konwersja z typu|Konwertuj na typ|  
|-----------------------|---------------------|  
|*Nazwa typu*|*Nazwa typu* **&**|  
|*Nazwa typu* **&**|*Nazwa typu*|  
|*Nazwa typu* **]**|*Nazwa typu\**|  
|*Nazwa typu* **(** *listy argumentów* **)**|**(**  *\*nazwy typu* **) (** *listy argumentów* **)**|  
|*Nazwa typu*|**Const** *nazwy typu*|  
|*Nazwa typu*|`volatile` *Nazwa typu*|  
|*Nazwa typu\**|**Const** *nazwy typu\**|  
|*Nazwa typu\**|`volatile` *Nazwa typu\**|  
  
 Kolejność, w którym są próby konwersji wygląda następująco:  
  
1.  Dokładne dopasowanie. Dokładnego dopasowania z typów, z którymi funkcja jest wywoływana i typy zadeklarowane w prototyp funkcji jest zawsze najlepsze dopasowanie. Sekwencje trivial konwersje sklasyfikowanych jako dokładne dopasowania. Jednak sekwencji, których nie należy wprowadzać dowolne z tych konwersji są traktowane jako lepszym rozwiązaniem niż sekwencje konwersji:  
  
    -   Ze wskaźnika na wskaźnik do **const** (`type`  **\***  do **const** `type`  **\***  ).  
  
    -   Ze wskaźnika na wskaźnik do `volatile` (`type`  **\***  do `volatile` `type`  **\*** ).  
  
    -   Z odwołania do odwołania do **const** (`type`  **&**  do **const** `type`  **&** ).  
  
    -   Z odwołania do odwołania do `volatile` (`type`  **&**  do `volatile` `type`  **&** ).  
  
2.  Dopasuj je przy użyciu promocji. Wszelkie sekwencji nie są sklasyfikowane jako dokładnego dopasowania, który zawiera tylko promocje typów całkowitych, konwersje z **float** do **podwójne**, i konwersje trivial zostanie sklasyfikowany jako dopasowanie przy użyciu promocji. Chociaż nie tak dobrze dopasowania jako żadnych dokładnego dopasowania, dopasowanie przy użyciu promocji jest lepszym rozwiązaniem niż przy użyciu standardowych konwersji dopasowania.  
  
3.  Dopasuj je przy użyciu standardowych konwersji. Wszelkie sekwencji nie są sklasyfikowane jako dokładnego dopasowania lub dopasowania za pomocą promocji, zawierający tylko konwersje standardowe i konwersje trivial zostanie sklasyfikowany jako dopasowanie przy użyciu standardowych konwersji. W tej kategorii stosowane są następujące reguły:  
  
    -   Konwersja ze wskaźnika do klasy pochodnej na wskaźnik do bezpośredniej lub pośredniej klasy podstawowej jest preferowana do konwertowania na **void \***  lub **const void \*** .  
  
    -   Konwersja ze wskaźnika do klasy pochodnej na wskaźnik do klasy podstawowej zapewnia lepsze dopasowanie bliżej klasa podstawowa jest do bezpośredniej klasie podstawowej. Załóżmy, że jest hierarchia klas, jak pokazano na poniższej ilustracji.  
  
 ![Preferowany konwersje](../cpp/media/vc391t1.gif "vc391T1")  
Wykres pokazujący preferowanych konwersje  
  
 Konwersja z typu `D*` na typ `C*` lepiej jest konwersja z typu `D*` na typ `B*`. Podobnie, konwersja z typu `D*` na typ `B*` lepiej jest konwersja z typu `D*` na typ `A*`.  
  
 Ten sam reguła ma zastosowanie do konwersje odwołań. Konwersja z typu `D&` na typ `C&` lepiej jest konwersja z typu `D&` na typ `B&`i tak dalej.  
  
 Konwersje wskaźników do elementów członkowskich stosowana ta reguła tego samego. Konwersja z typu `T D::*` na typ `T C::*` lepiej jest konwersja z typu `T D::*` na typ `T B::*`i tak dalej (gdzie `T` jest typem elementu członkowskiego).  
  
 Poprzedni reguła ma zastosowanie tylko wraz z danej ścieżce pochodnym. Należy wziąć pod uwagę wykres pokazano na poniższej ilustracji.  
  
 ![Obsługa wielu&#45;dziedziczenia, pokazujący preferowanych konwersje](../cpp/media/vc391t2.gif "vc391T2")  
Wykres dziedziczenia wielokrotnego pokazujący preferowanych konwersje  
  
 Konwersja z typu `C*` na typ `B*` lepiej jest konwersja z typu `C*` na typ `A*`. Przyczyną jest to, że znajdują się w tej samej ścieżki i `B*` zbliżonej. Jednak konwersja z typu `C*` na typ `D*` nieodpowiednim do konwersji na typ `A*`; jest Brak preferencji, ponieważ konwersje należy wykonać różne ścieżki.  
  
1.  Zgodny z konwersje zdefiniowane przez użytkownika. Ta sekwencja nie mogą być klasyfikowane jako dokładnego dopasowania, dopasowanie przy użyciu promocji lub przy użyciu standardowych konwersji dopasowania. Sekwencja musi zawierać tylko konwersje zdefiniowane przez użytkownika konwersje standardowe i konwersje prosta klasyfikowane jako dopasowania konwersje zdefiniowane przez użytkownika. Dopasowania konwersje zdefiniowane przez użytkownika jest traktowany jako będący lepszym dopasowaniem niż dopasowania z wielokropkiem, ale nie tak dobrze dopasowanie jako dopasowania konwersje standardowe.  
  
2.  Zgodny z wielokropkiem. Każda sekwencja odpowiadający wielokropek w deklaracji jest sklasyfikowany jako zgodne z wielokropkiem. To jest uważany za najsłabszą dopasowania.  
  
 Konwersje zdefiniowane przez użytkownika są stosowane, jeśli nie ma wbudowanej podwyższania poziomu ani konwersji. Konwersje te są wybierane na podstawie typu argumentu filtrowanego. Rozważmy następujący kod:  
  
```  
// argument_matching1.cpp  
class UDC  
{  
public:  
   operator int()  
   {  
      return 0;  
   }  
   operator long();  
};  
  
void Print( int i )  
{  
};  
  
UDC udc;  
  
int main()  
{  
   Print( udc );  
}  
```  
  
 Dostępne konwersje zdefiniowane przez użytkownika dla klasy `UDC` z typu `int` i typ **długi**. W związku z tym kompilator traktuje konwersje dla typu obiektu filtrowanego: `UDC`. Konwersja do `int` istnieje, i jest zaznaczony.  
  
 W trakcie dopasowania argumentów konwersje standardowe może odnosić się do tego argumentu i wynik konwersji zdefiniowanej przez użytkownika. W związku z tym działa następujący kod:  
  
```  
void LogToFile( long l );  
...  
UDC udc;  
LogToFile( udc );  
```  
  
 W poprzednim przykładzie, konwersja zdefiniowana przez użytkownika **operator długi**, wywoływana w celu konwersji `udc` na typ **długi**. Jeśli brak zdefiniowanych przez użytkownika konwersji na typ **długi** zostały zdefiniowane, konwersja będzie mieć przystąpiła w następujący sposób: typ `UDC` czy przekonwertować na typ `int` za pomocą konwersji zdefiniowanej przez użytkownika. Następnie standardowych konwersji z typu `int` na typ **długi** będzie stosowane do dopasowania argumentu w deklaracji.  
  
 Jeśli wszystkie konwersje zdefiniowane przez użytkownika są wymagane, aby dopasować argumentu, konwersje standardowe nie są używane podczas obliczania najlepsze dopasowanie. Dotyczy to nawet wtedy, gdy więcej niż jedna funkcja candidate wymaga konwersji zdefiniowanej przez użytkownika; w takim przypadku funkcje są traktowane jako równe. Na przykład:  
  
```  
// argument_matching2.cpp  
// C2668 expected  
class UDC1  
{  
public:  
   UDC1( int );  // User-defined conversion from int.  
};  
  
class UDC2  
{  
public:  
   UDC2( long ); // User-defined conversion from long.  
};  
  
void Func( UDC1 );  
void Func( UDC2 );  
  
int main()  
{  
   Func( 1 );  
}  
```  
  
 Obie wersje `Func` wymaga konwersji zdefiniowanej przez użytkownika można przekonwertować typu `int` do argumentu typu klasy. Konwersje możliwe są następujące:  
  
-   Konwersja z typu `int` na typ `UDC1` (konwersji zdefiniowanej przez użytkownika).  
  
-   Konwersja z typu `int` na typ **długi**; a następnie przekonwertować na typ `UDC2` (konwersji dwuetapowej).  
  
 Mimo że drugi z nich wymaga konwersji standardowej, a także konwersji zdefiniowanej przez użytkownika, konwersje dwóch nadal są uwzględniane takie same.  
  
> [!NOTE]
>  Konwersje zdefiniowane przez użytkownika są uważane za konwersji konstruowania lub konwersji przez inicjowania (funkcja konwersji). Obie metody są traktowane jako równe, rozważając najlepsze dopasowanie.  
  
## <a name="argument-matching-and-the-this-pointer"></a>Dopasowanie argumentu i jego wskaźnika  
 Funkcje elementów członkowskich klasy są traktowane inaczej, w zależności od tego, czy są deklarowane jako `static`. Ponieważ Niestatyczne funkcje ma niejawne argumentu, który dostarcza `this` wskaźnik, Niestatyczne funkcje są traktowane jako, aby mieć jeden argument więcej niż statyczne funkcje; w przeciwnym razie są one zgłoszone tak samo.  
  
 Te Niestatyczne funkcje Członkowskie wymagają, aby domniemanych `this` wskaźnika jest zgodny z typem obiektu za pośrednictwem której wywołano tę funkcję, lub dla przeciążone operatory wymagają zgodności pierwszy argument obiektu, na którym są operator stosowane. (Aby uzyskać więcej informacji na temat przeciążone operatory zobacz [przeciążone operatory](../cpp/operator-overloading.md).)  
  
 W przeciwieństwie do innych argumentów przeciążonej funkcji są wprowadzane nie obiekty tymczasowe i konwersji są próby podczas próby dopasowania `this` argumentu będącego wskaźnikiem.  
  
 Gdy `->` operatora wyboru elementu członkowskiego umożliwia dostęp do funkcji członkowskiej klasy `class_name`, `this` wskaźnika argument ma typ `class_name * const`. Jeśli elementy członkowskie są deklarowane jako `const` lub `volatile`, istnieją typy `const class_name * const` i `volatile class_name * const`odpowiednio.  
  
 `.` Operatora wyboru elementu członkowskiego działa dokładnie tak samo, z wyjątkiem niejawnej `&` operator (address-of) jest prefiksem do nazwy obiektu. W poniższym przykładzie pokazano, jak to działa:  
  
```  
// Expression encountered in code  
obj.name  
  
// How the compiler treats it  
(&obj)->name  
```  
  
 Lewy argument operacji `->*` i `.*` operatory (wskaźnik do elementu członkowskiego) są traktowane w taki sam sposób jak `.` i `->` operatory (wyboru elementu członkowskiego) względem dopasowania argumentów.  

## <a name="ref-qualifiers"></a> Kwalifikatory ref w funkcjach Członkowskich  
Kwalifikatory REF umożliwiają przeciążyć funkcji członkowskiej na podstawie tego, czy obiekt wskazywany przez `this` r-wartości lub l-wartością.  Tej funkcji można uniknąć operacje kopiowania niepotrzebnych w scenariuszach, w których użytkownik chce nie wskaźnika dostęp do danych. Załóżmy na przykład, klasa **C** niektóre dane w jego Konstruktor inicjuje i zwraca kopię danych w funkcji członkowskiej **get_data()**. Jeśli obiekt typu **C** jest r-wartości jest zniszczony, a następnie wybierze kompilator **get_data() & &** przeciążenia, które przenosi dane, a nie skopiować go. 

```cpp
#include <iostream>
#include <vector>

using namespace std;

class C
{

public:
    C() {/*expensive initialization*/}
    vector<unsigned> get_data() & 
    { 
        cout << "lvalue\n";
        return _data;
    }
    vector<unsigned> get_data() && 
    {
        cout << "rvalue\n";
        return std::move(_data);
    }
    
private:
    vector<unsigned> _data;
};

int main()
{
    C c;
    auto v = c.get_data(); // get a copy. prints "lvalue".
    auto v2 = C().get_data(); // get the original. prints "rvalue"
    return 0;
}

```
  
## <a name="restrictions-on-overloading"></a>Ograniczenia przeciążania  
 Kilka ograniczeń regulują dopuszczalnego zestawu przeciążonej funkcji:  
  
-   Wszelkie dwóch funkcji w zestawie przeciążonej funkcji musi mieć listy argumentów inny.  
  
-   Przeciążanie funkcji z listy argumentów tego samego typu na podstawie zwracanego typu samodzielnie, występuje błąd.  
  
     **Microsoft Specific**  
  
 Można przeciążać **nowy operator** wyłącznie w oparciu o typ zwracany — w szczególności na podstawie modyfikator modelu pamięci określono.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
-   Funkcje elementów członkowskich nie może zostać przeciążony wyłącznie na podstawie jednego podpisu statyczne i innych nonstatic.  
  
-   `typedef` deklaracje nie definiują nowe typy; synonimy dla istniejących typów ich wprowadzenie. Nie ma wpływu na przeciążania mechanizmu. Rozważmy następujący kod:  
  
    ```  
    typedef char * PSTR;  
  
    void Print( char *szToPrint );  
    void Print( PSTR szToPrint );  
    ```  
  
     Poprzednie dwie funkcje mają identyczne argumentu listy. `PSTR` jest synonimem typu **char \*** . Ten kod generuje błąd, w zakresie elementu członkowskiego.  
  
-   Typy wyliczane są różne typy i służy do rozróżnienia przeciążonej funkcji.  
  
-   Typy "tablica" i "wskaźnik" są traktowane jako w taki sam na potrzeby rozróżniania przeciążonej funkcji. Dotyczy to tylko dla tablic pojedynczo wymiarów. W związku z tym następujące przeciążonej funkcji konflikt i generuje komunikat o błędzie:  
  
    ```  
    void Print( char *szToPrint );  
    void Print( char szToPrint[] );  
    ```  
  
     Dla tablic mnożenie wymiarów drugi i wszystkie kolejne wymiary są traktowane jako część typu. W związku z tym są używane w rozróżniania przeciążonej funkcji:  
  
    ```  
    void Print( char szToPrint[] );  
    void Print( char szToPrint[][7] );  
    void Print( char szToPrint[][9][42] );  
    ```  
  
## <a name="overloading-overriding-and-hiding"></a>Przeładowanie, zastępowanie i ukrywanie
  
 Wszelkie dwie deklaracje funkcji o tej samej nazwie w tym samym zakresie, mogą odwoływać się do tej samej funkcji lub do dwóch funkcji dyskretnych, które są przeciążone. Jeśli wykazy argumentów deklaracji zawierają równoważne typy argumentów (zgodnie z opisem w poprzedniej sekcji), deklaracje funkcji odnoszą się do tej samej funkcji. W przeciwnym razie, odnoszą się do dwóch różnych funkcji, które są wybrane za pomocą przeciążenia.  
  
 Zakres klasy jest ściśle przestrzegany; w związku z tym, funkcja zadeklarowana w klasie bazowej nie jest w tym samym zakresie, co funkcja zadeklarowana w klasie pochodnej. Jeśli funkcja w klasie pochodnej jest zadeklarowany z taką samą nazwę jak funkcję wirtualną w klasie podstawowej funkcji klas pochodnych *zastępuje* funkcji klasy podstawowej. Aby uzyskać więcej informacji, zobacz [funkcji wirtualnych](../cpp/virtual-functions.md).

Jeśli funkcji klasy podstawowej nie jest zadeklarowany jako "virtual", a następnie funkcja klasy pochodnej jest nazywany *Ukryj* go. Zarówno zastępowanie i ukrywanie różnią się od przeciążenia.  
  
 Zakres bloku jest ściśle przestrzegany; w związku z tym, funkcja zadeklarowana w zakresie pliku nie jest w tym samym zakresie, co funkcja zadeklarowana lokalnie. Jeśli funkcja zadeklarowana lokalnie ma taką samą nazwę, co funkcja zadeklarowana w zakresie pliku, funkcja zadeklarowana lokalnie ukrywa funkcje należącą do zakresu pliku, zamiast powodować przeciążenie. Na przykład:  
  
```  
// declaration_matching1.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
void func( int i )  
{  
    cout << "Called file-scoped func : " << i << endl;  
}  
  
void func( char *sz )  
{  
   cout << "Called locally declared func : " << sz << endl;  
}  
  
int main()  
{  
   // Declare func local to main.  
   extern void func( char *sz );  
  
   func( 3 );   // C2664 Error. func( int ) is hidden.  
   func( "s" );  
}  
```  
  
 Poprzedni kod pokazuje dwie definicje funkcji `func`. Definicja, która wymaga argumentu typu `char *` jest lokalna dla `main` z powodu instrukcji `extern`. W związku z tym, definicja która przyjmuje argument typu `int` jest ukryta, a pierwsze wywołanie funkcji `func` jest błędne.  
  
 Dla przeciążonych funkcji członkowskich, różne wersje funkcji mogą mieć różne przywileje dostępu. Ale nadal uważa się, że znajdują się w zakresie otaczającym klasę, a więc są funkcjami przeciążonymi. Rozważmy poniższy kod, w którym funkcja członkowska `Deposit` jest przeciążona; jedna wersja jest publiczna, inne są prywatne.  
  
 Zamiarem tego przykładu jest dostarczenie klasy `Account`, w której wymagane jest poprawne hasło, aby wykonać depozyty. Jest to uzyskiwane za pomocą przeciążenia.  
  
 Należy zauważyć, że wywołanie `Deposit` w klasie `Account::Deposit` wywołuje prywatne funkcje członkowskie. To wywołanie jest poprawne, ponieważ `Account::Deposit` jest funkcją składową, a zatem ma dostęp do prywatnych składowych klasy.  
  
```  
// declaration_matching2.cpp  
class Account  
{  
public:  
   Account()  
   {  
   }  
   double Deposit( double dAmount, char *szPassword );  
  
private:  
   double Deposit( double dAmount )  
   {  
      return 0.0;  
   }  
   int Validate( char *szPassword )  
   {  
      return 0;  
   }  
  
};  
  
int main()  
{  
    // Allocate a new object of type Account.  
    Account *pAcct = new Account;  
  
    // Deposit $57.22. Error: calls a private function.  
    // pAcct->Deposit( 57.22 );  
  
    // Deposit $57.22 and supply a password. OK: calls a  
    //  public function.  
    pAcct->Deposit( 52.77, "pswd" );  
}  
  
double Account::Deposit( double dAmount, char *szPassword )  
{  
   if ( Validate( szPassword ) )  
      return Deposit( dAmount );  
   else  
      return 0.0;  
}  
```



  
## <a name="see-also"></a>Zobacz też  
 [Funkcje (C++)](../cpp/functions-cpp.md)