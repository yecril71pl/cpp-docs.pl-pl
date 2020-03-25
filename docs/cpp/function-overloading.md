---
title: Przeładowywanie funkcji
ms.date: 03/27/2019
helpviewer_keywords:
- function overloading [C++], about function overloading
- function overloading
- declaring functions [C++], overloading
ms.assetid: 3c9884cb-1d5e-42e8-9a49-6f46141f929e
ms.openlocfilehash: fe390ae190f422f7951f7101a7c08808b1c6a526
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179786"
---
# <a name="function-overloading"></a>Przeładowywanie funkcji

C++ umożliwia określenie więcej niż jednej funkcji o tej samej nazwie w tym samym zakresie. Te funkcje są nazywane *przeciążonymi* funkcjami. Przeciążone funkcje umożliwiają dostarczenie różnych semantyki dla funkcji, w zależności od typów i liczby argumentów.

Na przykład funkcja `print`, która przyjmuje argument `std::string`, może wykonywać bardzo różne zadania niż jeden, który przyjmuje argument typu **Double**. Przeciążanie powoduje, że nie trzeba używać nazw, takich jak `print_string` lub `print_double`. W czasie kompilacji kompilator wybiera, którego przeciążenia użyć na podstawie typu argumentów przekazaną przez wywołującego.  Jeśli wywołasz `print(42.0)`, funkcja `void print(double d)` zostanie wywołana. Jeśli wywołasz `print("hello world")`, zostanie wywołane Przeciążenie `void print(std::string)`.

Można przeciążać zarówno funkcje członkowskie, jak i funkcje, które nie są elementami członkowskimi. W poniższej tabeli przedstawiono, które części deklaracji funkcji język C++ używa do rozróżniania grup funkcji o tej samej nazwie w tym samym zakresie.

### <a name="overloading-considerations"></a>Zagadnienia przeciążania

|Element deklaracji funkcji|Używany w przeciążaniu?|
|----------------------------------|---------------------------|
|Typ zwracany przez funkcję|Nie|
|Liczba argumentów|Yes|
|Typ argumentów|Yes|
|Obecność lub brak wielokropka|Yes|
|Używanie nazw **typedef**|Nie|
|Nieokreślone granice tablic|Nie|
|**const** lub **volatile**|Tak, po zastosowaniu do całej funkcji|
|[Kwalifikatory ref](#ref-qualifiers)|Yes|

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia przeciążenia.

```cpp
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

Domyślny argument nie jest uważany za część typu funkcji. W związku z tym nie jest używany podczas wybierania przeciążonych funkcji. Dwie funkcje, które różnią się tylko argumentami domyślnymi, są traktowane jako wiele definicji, a nie przeciążone funkcje.

Nie można dostarczyć argumentów domyślnych dla przeciążonych operatorów.

## <a name="argument-matching"></a>Dopasowywanie argumentów

Przeciążone funkcje są wybierane w celu najlepszego dopasowania deklaracji funkcji w bieżącym zakresie do argumentów dostarczonych w wywołaniu funkcji. Jeśli zostanie znaleziona odpowiednia funkcja, ta funkcja jest wywoływana. "Odpowiednie" w tym kontekście oznacza:

- Znaleziono dokładne dopasowanie.

- Wykonano uproszczoną konwersję.

- Wykonano promocję integralną.

- Istnieje konwersja standardowa do żądanego typu argumentu.

- Istnieje konwersja zdefiniowana przez użytkownika (Operator konwersji lub Konstruktor) na żądany typ argumentu.

- Znaleziono argumenty reprezentowane przez wielokropek.

Kompilator tworzy zestaw funkcji kandydujących dla każdego argumentu. Funkcje kandydujące to funkcje, w których rzeczywisty argument w tym miejscu można przekonwertować na typ argumentu formalnego.

Zestaw "najlepszych dopasowanych funkcji" jest tworzony dla każdego argumentu, a wybrana funkcja to część wspólna wszystkich zestawów. Jeśli część wspólna zawiera więcej niż jedną funkcję, Przeciążenie jest niejednoznaczne i generuje błąd. Funkcja, która jest ostatecznie zaznaczona, zawsze jest lepszym rozwiązaniem niż każda inna funkcja w grupie dla co najmniej jednego argumentu. Jeśli nie ma żadnych wyraźnych zwycięzców, wywołanie funkcji generuje błąd.

Należy wziąć pod uwagę następujące deklaracje (funkcje są oznaczone `Variant 1`, `Variant 2`i `Variant 3`do identyfikacji w poniższej dyskusji):

```cpp
Fraction &Add( Fraction &f, long l );       // Variant 1
Fraction &Add( long l, Fraction &f );       // Variant 2
Fraction &Add( Fraction &f, Fraction &f );  // Variant 3

Fraction F1, F2;
```

Weź pod uwagę następujące instrukcje:

```cpp
F1 = Add( F2, 23 );
```

Poprzednia instrukcja kompiluje dwa zestawy:

|Set 1: funkcje kandydujące, które mają pierwszy argument typu ułamek|Set 2: funkcje kandydujące, których drugi argument można przekonwertować na typ **int**|
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
|Wariant 1|Wariant 1 (**int** można przekonwertować na wartość **Long** przy użyciu konwersji standardowej)|
|Wariant 3||

Funkcje w zestawie 2 są funkcjami, dla których istnieją niejawne konwersje z rzeczywistego typu parametru do formalnego typu parametru i między takimi funkcjami istnieje funkcja, dla której wartość "koszt" konwersji rzeczywistego typu parametru na jego typ parametru formalnego to najmniejsza.

Przecięcie tych dwóch zestawów jest wariantem 1. Przykładem niejednoznacznego wywołania funkcji jest:

```cpp
F1 = Add( 3, 6 );
```

Poprzednie wywołanie funkcji kompiluje następujące zestawy:

|Set 1: funkcje kandydujące, które mają pierwszy argument typu **int**|Set 2: funkcje kandydujące, które mają drugi argument typu **int**|
|---------------------------------------------------------------------|----------------------------------------------------------------------|
|Wariant 2 (**int** można przekonwertować na wartość **Long** przy użyciu konwersji standardowej)|Wariant 1 (**int** można przekonwertować na wartość **Long** przy użyciu konwersji standardowej)|

Ponieważ część wspólną tych dwóch zestawów jest pusta, kompilator generuje komunikat o błędzie.

W przypadku dopasowywania argumentów funkcja z argumentami domyślnymi *n* jest traktowana jako *n*+ 1 oddzielne funkcje, z których każdy ma inną liczbę argumentów.

Wielokropek (...) działa jako symbol wieloznaczny; Dopasowuje dowolny rzeczywisty argument. Może to prowadzić do wielu niejednoznacznych zestawów, jeśli nie projektujesz przeciążonych zestawów funkcji z najwyższą starannością.

> [!NOTE]
>  Nie można określić niejednoznaczności przeciążonych funkcji, dopóki nie zostanie napotkane wywołanie funkcji. W tym momencie zestawy są kompilowane dla każdego argumentu w wywołaniu funkcji i można określić, czy istnieje jednoznaczne Przeciążenie. Oznacza to, że niejasności może pozostawać w kodzie do momentu evoked przez określone wywołanie funkcji.

## <a name="argument-type-differences"></a>Różnice typu argumentów

Przeciążone funkcje odróżniają między typami argumentów, które mają różne inicjatory. W związku z tym argument danego typu i odwołanie do tego typu są uznawane za takie same dla celów przeciążenia. Są one uznawane za takie same, ponieważ przyjmują te same inicjatory. Na przykład `max( double, double )` jest uznawana za taka sama jak `max( double &, double & )`. Deklarowanie dwóch takich funkcji powoduje wystąpienie błędu.

Z tego samego powodu argumenty funkcji typu modyfikowane przez **const** lub **volatile** nie są traktowane inaczej niż typ podstawowy do celów przeciążenia.

Jednak mechanizm przeciążania funkcji może rozróżnić odwołania, które są kwalifikowane przez **const** i **volatile** , i odwołania do typu podstawowego. Wprowadza kod, taki jak następujące możliwe:

```cpp
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

```Output
Over default constructor
Over&
Over default constructor
const Over&
Over default constructor
volatile Over&
```

Wskaźniki do obiektów **const** i **volatile** są również uznawane za różne od wskaźników do typu podstawowego w celach przeciążenia.

## <a name="argument-matching-and-conversions"></a>Dopasowywanie argumentów i konwersje

Gdy kompilator próbuje dopasować rzeczywiste argumenty do argumentów w deklaracjach funkcji, może dostarczyć standardowe lub zdefiniowane przez użytkownika Konwersje w celu uzyskania poprawnego typu, jeśli nie można znaleźć dokładnego dopasowania. Zastosowanie konwersji podlega tym regułom:

- Nie są uwzględniane sekwencje konwersji zawierające więcej niż jedną konwersję zdefiniowaną przez użytkownika.

- Sekwencje konwersji, które mogą być skracane przez usunięcie konwersji pośrednich, nie są brane pod uwagę.

Wynikowa sekwencja konwersji, jeśli istnieje, jest nazywana najlepszą pasującą sekwencją. Istnieje kilka sposobów konwersji obiektu typu **int** na typ **unsigned long** przy użyciu konwersji standardowych (opisanych w [konwersji standardowe](../cpp/standard-conversions.md)):

- Konwertuj z **int** na **Long** , a następnie od **Long** do **unsigned long**.

- Konwertuj z **int** na **unsigned long**.

Pierwsza sekwencja, chociaż osiąga żądany cel, nie jest najlepszą zgodną sekwencją — istnieje krótsza sekwencja.

W poniższej tabeli przedstawiono grupę konwersji o nazwie uproszczone konwersje, które mają ograniczony wpływ na określanie, która sekwencja jest najlepszym dopasowaniem. Wystąpienia, w których konwersje uproszczone mają wpływ na wybór sekwencji, omówiono na liście poniżej tabeli.

### <a name="trivial-conversions"></a>Konwersje uproszczone

|Konwertuj z typu|Konwertuj na typ|
|-----------------------|---------------------|
|*Nazwa typu*|*Nazwa typu* **&**|
|*Nazwa typu* **&**|*Nazwa typu*|
|*Nazwa typu* **[]**|*Nazwa typu* __\*__|
|*type-name* **(** *Lista argumentów* **)**|**(** __\*__ *type-name* **) (** *Lista argumentów* **)**|
|*Nazwa typu*|**const** *— Nazwa typu*|
|*Nazwa typu*|**nietrwała** *Nazwa typu*|
|*Nazwa typu* __\*__|**stała** *Nazwa typu* __\*__|
|*Nazwa typu* __\*__|**nietrwała** *Nazwa typu* __\*__|

Sekwencja, w której są podejmowane próby konwersji, jest następująca:

1. Dokładne dopasowanie. Dokładne dopasowanie między typami, z których wywoływana jest funkcja, a typy zadeklarowane w prototypie funkcji są zawsze najlepszym dopasowaniem. Sekwencje uproszczonych konwersji są klasyfikowane jako dokładne dopasowania. Jednak sekwencje, które nie tworzą żadnej z tych konwersji, są uznawane za lepsze niż sekwencje, które konwertują:

   - Ze wskaźnika do wskaźnika do **stałej** (`type` <strong>\*</strong> do **stałej** `type` <strong>\*</strong>).

   - Ze wskaźnika do wskaźnika do **nietrwałego** (`type` <strong>\*</strong> do **nietrwałego** `type` <strong>\*</strong>).

   - Z odwołania do odwołania do **const** (`type` **&** do **const** `type` **&** ).

   - Z odwołania, aby odwołać się do **nietrwałego** (`type` **&** do **nietrwałej** `type` **&** ).

1. Dopasowuje się do korzystania z promocji. Każda sekwencja nie została sklasyfikowana jako dokładne dopasowanie, która zawiera tylko promocje całkowite, konwersje z **zmiennoprzecinkowe** na **podwójne**, a konwersje uproszczone są klasyfikowane jako dopasowanie przy użyciu promocji. Chociaż nie jest to dobre dopasowanie jako dokładne dopasowanie, dopasowanie przy użyciu promocji jest lepszym rozwiązaniem niż dopasowanie przy użyciu konwersji standardowych.

1. Dopasowanie przy użyciu konwersji standardowych. Dowolna sekwencja nie została sklasyfikowana jako dokładne dopasowanie ani dopasowanie przy użyciu promocji, które zawierają tylko Konwersje standardowe i konwersje uproszczone są klasyfikowane jako dopasowanie przy użyciu konwersji standardowych. W tej kategorii są stosowane następujące reguły:

   - Konwersja ze wskaźnika na klasę pochodną do wskaźnika do bezpośredniej lub pośredniej klasy podstawowej jest preferowana do konwersji na `void *` lub `const void *`.

   - Konwersja ze wskaźnika do klasy pochodnej na wskaźnik do klasy bazowej daje lepszy dopasowanie do klasy bazowej do bezpośredniej klasy podstawowej. Załóżmy, że hierarchia klas jest pokazana na poniższej ilustracji.

![Wykres preferowanych konwersji](../cpp/media/vc391t1.gif "Wykres preferowanych konwersji") <br/>
Wykres przedstawiający preferowane konwersje

Konwersja z typu `D*` na typ `C*` jest preferowana konwersja z typu `D*` na typ `B*`. Podobnie konwersja z typu `D*` na typ `B*` jest preferowana konwersja z typu `D*` na typ `A*`.

Ta sama reguła ma zastosowanie do konwersji odwołań. Konwersja z typu `D&` na typ `C&` jest preferowana konwersja z typu `D&` na typ `B&`i tak dalej.

Ta sama reguła ma zastosowanie do konwersji wskaźnika do elementu członkowskiego. Konwersja z typu `T D::*` na typ `T C::*` jest preferowana konwersja z typu `T D::*` na typ `T B::*`i tak dalej (gdzie `T` jest typem elementu członkowskiego).

Poprzednia reguła ma zastosowanie tylko do danej ścieżki pochodnej. Rozważmy wykres przedstawiony na poniższej ilustracji.

![Wielokrotne&#45;dziedziczenie, które pokazuje preferowane konwersje](../cpp/media/vc391t2.gif "Wielokrotne&#45;dziedziczenie, które pokazuje preferowane konwersje") <br/>
Wykres wielokrotnego dziedziczenia, który pokazuje preferowane konwersje

Konwersja z typu `C*` na typ `B*` jest preferowana konwersja z typu `C*` na typ `A*`. Powodem jest to, że znajdują się one w tej samej ścieżce, a `B*` jest bliższe. Jednak konwersja z typu `C*` na typ `D*` nie jest preferowany do konwersji na typ `A*`; nie ma preferencji, ponieważ konwersje są zgodne z różnymi ścieżkami.

1. Dopasowuje się do konwersji zdefiniowanych przez użytkownika. Tej sekwencji nie można zaklasyfikować jako dokładnego dopasowania, dopasowania przy użyciu promocji lub dopasowania przy użyciu konwersji standardowych. Sekwencja musi zawierać tylko konwersje zdefiniowane przez użytkownika, Konwersje standardowe lub konwersje proste, które mają być sklasyfikowane jako zgodne z konwersjemi zdefiniowanymi przez użytkownika. Dopasowanie z konwersjemi zdefiniowanymi przez użytkownika jest uznawane za lepsze niż dopasowanie z wielokropkiem, ale nie jako zgodne ze standardowymi konwersjemi.

1. Dopasowuje się do wielokropka. Wszelkie sekwencje pasujące do wielokropka w deklaracji są klasyfikowane jako zgodne z wielokropkiem. Jest on traktowany jak najsłabsze dopasowanie.

Konwersje zdefiniowane przez użytkownika są stosowane w przypadku braku wbudowanej promocji lub konwersji. Te konwersje są wybierane na podstawie typu pasującego argumentu. Rozważmy następujący kod:

```cpp
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

Dostępne konwersje zdefiniowane przez użytkownika dla klas `UDC` są typu **int** i typu **Long**. W związku z tym kompilator rozważa konwersje dla typu pasującego obiektu: `UDC`. Konwersja na **typ int** istnieje i została wybrana.

Podczas procesu dopasowywania argumentów Konwersje standardowe mogą być stosowane do argumentu i wyniku konwersji zdefiniowanej przez użytkownika. W związku z tym Poniższy kod działa:

```cpp
void LogToFile( long l );
...
UDC udc;
LogToFile( udc );
```

W poprzednim przykładzie zdefiniowana przez użytkownika konwersja, **operator Long**, jest wywoływana w celu przekonwertowania `udc` na typ **Long**. Jeśli nie zdefiniowano żadnej konwersji zdefiniowanej przez użytkownika dla typu **Long** , konwersja zostałaby przebiegać w następujący sposób: typ `UDC` zostałby przekonwertowany na typ **int** przy użyciu konwersji zdefiniowanej przez użytkownika. Następnie konwersja standardowa typu **int** na typ **Long** zostałaby zastosowana w celu dopasowania do argumentu w deklaracji.

Jeśli wszystkie konwersje zdefiniowane przez użytkownika są wymagane do dopasowania argumentu, standardowe konwersje nie są używane podczas oceny najlepszego dopasowania. Nawet jeśli więcej niż jedna funkcja kandydująca wymaga konwersji zdefiniowanej przez użytkownika, funkcje są uważane za równe. Na przykład:

```cpp
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

Obie wersje `Func` wymagają konwersji zdefiniowanej przez użytkownika na konwersję typu **int** do argumentu typu klasy. Możliwe konwersje to:

- Konwertuj z typu **int** na typ `UDC1` (konwersja zdefiniowana przez użytkownika).

- Konwertuj z typu **int** na typ **Long**; następnie przekonwertuj na `UDC2` typu (konwersja dwuetapowa).

Mimo że druga z nich wymaga konwersji standardowej i konwersji zdefiniowanej przez użytkownika, dwie konwersje są nadal uważane za równe.

> [!NOTE]
>  Konwersje zdefiniowane przez użytkownika są uznawane za konwersję lub konwersję przez inicjalizację (funkcję konwersji). Obie metody są uważane za równe przy uwzględnieniu najlepszego dopasowania.

## <a name="argument-matching-and-the-this-pointer"></a>Dopasowanie argumentów i ten wskaźnik

Funkcje składowe klasy są traktowane inaczej, w zależności od tego, czy są one zadeklarowane jako **statyczne**. Ponieważ niestatyczne funkcje mają niejawny argument, który dostarcza **ten** wskaźnik, niestatyczne funkcje są uznawane za mające jeden argument niż funkcje statyczne; w przeciwnym razie są one deklarowane identycznie.

Te niestatyczne funkcje Członkowskie wymagają, aby implikowany **wskaźnik pasował** do typu obiektu, za pomocą którego wywoływana jest funkcja, lub dla przeciążonych operatorów, wymagają, aby pierwszy argument był zgodny z obiektem, na którym jest stosowany operator. (Aby uzyskać więcej informacji na temat przeciążonych operatorów, zobacz [przeciążone operatory](../cpp/operator-overloading.md)).

W przeciwieństwie do innych argumentów w przeciążonych funkcjach, nie są wprowadzane żadne obiekty tymczasowe i nie podjęto próby konwersji przy próbie dopasowania **tego** argumentu wskaźnika.

Gdy operator wyboru `->` member jest używany w celu uzyskania dostępu do funkcji składowej klasy `class_name`, **ten** argument wskaźnika ma typ `class_name * const`. Jeśli składowe są zadeklarowane jako **const** lub **volatile**, typy są odpowiednio `const class_name * const` i `volatile class_name * const`.

Operator wyboru elementu członkowskiego `.` działa dokładnie tak samo, z tą różnicą, że niejawny operator `&` (Address-of) jest poprzedzony nazwą obiektu. Poniższy przykład pokazuje, jak to działa:

```cpp
// Expression encountered in code
obj.name

// How the compiler treats it
(&obj)->name
```

Lewy argument operacji dla operatorów `->*` i `.*` (wskaźnik do składowej) jest traktowany tak samo jak `.` i `->` (wybór elementu członkowskiego) w odniesieniu do argumentów.

## <a name="ref-qualifiers-on-member-functions"></a><a name="ref-qualifiers"></a>Kwalifikatory ref w funkcjach składowych

Kwalifikatory ref umożliwiają przeciążanie funkcji składowej w oparciu o to, czy obiekt wskazywany przez **to** jest rvalue, czy lvalue.  Ta funkcja umożliwia uniknięcie niepotrzebnych operacji kopiowania w scenariuszach, w których nie można zapewnić dostępu do danych za pomocą wskaźnika. Załóżmy na przykład, że Klasa `C` inicjuje pewne dane w konstruktorze i zwraca kopię tych danych w funkcji składowej `get_data()`. Jeśli obiekt typu `C` jest rvalue, który ma zostać zniszczony, kompilator wybierze `get_data() &&` Przeciążenie, które przenosi dane zamiast kopiować.

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

## <a name="restrictions-on-overloading"></a>Ograniczenia dotyczące przeciążania

Niektóre ograniczenia podlegają akceptowalnemu zestawowi przeciążonych funkcji:

- Wszystkie dwie funkcje w zestawie przeciążonych funkcji muszą mieć różne listy argumentów.

- Przeciążanie funkcji z listami argumentów tego samego typu, na podstawie samego typu zwracanego, jest błędem.

     **Specyficzne dla firmy Microsoft**

Można przeciążać **operator new** wyłącznie na podstawie typu zwracanego — w odniesieniu do określonego modyfikatora pamięci.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

- Funkcje składowe nie mogą być przeciążone wyłącznie na podstawie jednego statycznego i innego niestatycznego.

- deklaracje **typedef** nie definiują nowych typów; wprowadzają synonimy dla istniejących typów. Nie wpływają one na mechanizm przeciążania. Rozważmy następujący kod:

    ```cpp
    typedef char * PSTR;

    void Print( char *szToPrint );
    void Print( PSTR szToPrint );
    ```

   Poprzednie dwie funkcje mają identyczne listy argumentów. `PSTR` jest synonimem typu `char *`. W zakresie elementu członkowskiego ten kod generuje błąd.

- Typy wyliczeniowe są różnymi typami i mogą być używane do rozróżniania między przeciążonymi funkcjami.

- Typy "array of" i "wskaźnik do" są uważane za identyczne dla celów rozróżniania między przeciążonymi funkcjami, ale tylko dla tablic wielowymiarowych z wymiarami. Dlatego te przeciążone funkcje powodują konflikt i generują komunikat o błędzie:

    ```cpp
    void Print( char *szToPrint );
    void Print( char szToPrint[] );
    ```

   W przypadku mnożonych tablic wymiarowych drugi i wszystkie pomyślne wymiary są uważane za część typu. W związku z tym są używane w odróżnieniu od przeciążonych funkcji:

    ```cpp
    void Print( char szToPrint[] );
    void Print( char szToPrint[][7] );
    void Print( char szToPrint[][9][42] );
    ```

## <a name="overloading-overriding-and-hiding"></a>Przeciążanie, zastępowanie i ukrywanie

Wszelkie dwie deklaracje funkcji o tej samej nazwie w tym samym zakresie, mogą odwoływać się do tej samej funkcji lub do dwóch funkcji dyskretnych, które są przeciążone. Jeśli wykazy argumentów deklaracji zawierają równoważne typy argumentów (zgodnie z opisem w poprzedniej sekcji), deklaracje funkcji odnoszą się do tej samej funkcji. W przeciwnym razie, odnoszą się do dwóch różnych funkcji, które są wybrane za pomocą przeciążenia.

Zakres klasy jest ściśle przestrzegany; w związku z tym, Funkcja zadeklarowana w klasie bazowej nie jest w tym samym zakresie co funkcja zadeklarowana w klasie pochodnej. Jeśli funkcja klasy pochodnej jest zadeklarowana z tą samą nazwą jak funkcja wirtualna w klasie bazowej, funkcja klasy pochodnej *zastępuje* funkcję klasy podstawowej. Aby uzyskać więcej informacji, zobacz [funkcje wirtualne](../cpp/virtual-functions.md).

Jeśli funkcja klasy bazowej nie jest zadeklarowana jako "Virtual", funkcja klasy pochodnej jest określana do *ukrycia* . Zastępowanie i ukrywanie różnią się od przeciążenia.

Zakres bloku jest ściśle przestrzegany; w związku z tym, Funkcja zadeklarowana w zakresie pliku nie jest w tym samym zakresie co funkcja zadeklarowana lokalnie. Jeśli funkcja zadeklarowana lokalnie ma taką samą nazwę, co funkcja zadeklarowana w zakresie pliku, funkcja zadeklarowana lokalnie ukrywa funkcje należącą do zakresu pliku, zamiast powodować przeciążenie. Na przykład:

```cpp
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

Poprzedni kod pokazuje dwie definicje funkcji `func`. Definicja, która przyjmuje argument typu `char *`, jest lokalna dla `main` z powodu instrukcji **extern** . W związku z tym definicja, która przyjmuje argument typu **int** , jest ukryta, a pierwsze wywołanie `func` jest błędne.

Dla przeciążonych funkcji członkowskich, różne wersje funkcji mogą mieć różne przywileje dostępu. Ale nadal uważa się, że znajdują się w zakresie otaczającym klasę, a więc są funkcjami przeciążonymi. Rozważmy poniższy kod, w którym funkcja członkowska `Deposit` jest przeciążona; jedna wersja jest publiczna, inne są prywatne.

Zamiarem tego przykładu jest dostarczenie klasy `Account`, w której wymagane jest poprawne hasło, aby wykonać depozyty. Jest to wykonywane przy użyciu przeciążenia.

Wywołanie `Deposit` w `Account::Deposit` wywołuje prywatną funkcję członkowską. To wywołanie jest poprawne, ponieważ `Account::Deposit` jest funkcją członkowską i ma dostęp do prywatnych składowych klasy.

```cpp
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
