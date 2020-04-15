---
title: Przeładowywanie funkcji
ms.date: 03/27/2019
helpviewer_keywords:
- function overloading [C++], about function overloading
- function overloading
- declaring functions [C++], overloading
ms.assetid: 3c9884cb-1d5e-42e8-9a49-6f46141f929e
ms.openlocfilehash: a59c0e27a4500cb20ef42e9a55b4eb0004e07f65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368906"
---
# <a name="function-overloading"></a>Przeładowywanie funkcji

C++ umożliwia określenie więcej niż jednej funkcji o tej samej nazwie w tym samym zakresie. Funkcje te są nazywane *przeciążone* funkcje. Przeciążone funkcje umożliwiają dostarczanie różnych semantyki dla funkcji, w zależności od typów i liczby argumentów.

Na przykład `print` funkcja, która `std::string` przyjmuje argument może wykonywać bardzo różne zadania niż ten, który przyjmuje argument typu **double**. Przeciążenie pozwala zaoszczędzić na konieczności używania nazw takich jak `print_string` lub `print_double`. W czasie kompilacji kompilator wybiera, które przeciążenie do użycia na podstawie typu argumentów przekazanych przez wywołującego.  Jeśli wywołasz `print(42.0)`, `void print(double d)` funkcja zostanie wywołana. Jeśli wywołasz `print("hello world")`, `void print(std::string)` a następnie przeciążenie zostanie wywołane.

Można przeciążyć zarówno funkcje członkowskie, jak i funkcje niebędące członkami. W poniższej tabeli przedstawiono, które części deklaracji funkcji język C++ używa do rozróżniania grup funkcji o tej samej nazwie w tym samym zakresie.

### <a name="overloading-considerations"></a>Zagadnienia przeciążania

|Element deklaracji funkcji|Używany w przeciążaniu?|
|----------------------------------|---------------------------|
|Typ zwracany przez funkcję|Nie|
|Liczba argumentów|Tak|
|Typ argumentów|Tak|
|Obecność lub brak wielokropka|Tak|
|Używanie nazw **typedef**|Nie|
|Nieokreślone granice tablic|Nie|
|**const** lub **lotny**|Tak, po zastosowaniu do całej funkcji|
|[Ref-kwalifikatory](#ref-qualifiers)|Tak|

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

Domyślny argument nie jest uważany za część typu funkcji. W związku z tym nie jest używany przy wyborze przeciążonych funkcji. Dwie funkcje, które różnią się tylko w ich domyślne argumenty są uważane za wiele definicji, a nie przeciążone funkcje.

Domyślne argumenty nie mogą być dostarczane dla przeciążonych operatorów.

## <a name="argument-matching"></a>Dopasowywanie argumentów

Przeciążone funkcje są wybierane dla najlepszego dopasowania deklaracji funkcji w bieżącym zakresie do argumentów podanych w wywołaniu funkcji. Jeśli zostanie znaleziona odpowiednia funkcja, ta funkcja jest wywoływana. "Odpowiednie" w tym kontekście oznacza:

- Znaleziono dokładne dopasowanie.

- Dokonano banalnej konwersji.

- Przeprowadzono integralną promocję.

- Istnieje standardowa konwersja do żądanego typu argumentu.

- Istnieje konwersja zdefiniowana przez użytkownika (operator konwersji lub konstruktor) do żądanego typu argumentu.

- Znaleziono argumenty reprezentowane przez wielokropek.

Kompilator tworzy zestaw funkcji kandydata dla każdego argumentu. Funkcje kandydujące to funkcje, w których rzeczywisty argument na tym stanowisku można przekonwertować na typ argumentu formalnego.

Dla każdego argumentu jest zbudowany zestaw "najlepiej pasujących funkcji", a wybrana funkcja jest przecięciem wszystkich zestawów. Jeśli przecięcie zawiera więcej niż jedną funkcję, przeciążenie jest niejednoznaczne i generuje błąd. Funkcja, która zostanie ostatecznie wybrana, jest zawsze lepiej dopasowana niż każda inna funkcja w grupie dla co najmniej jednego argumentu. Jeśli nie ma wyraźnego zwycięzcy, wywołanie funkcji generuje błąd.

Rozważmy następujące deklaracje (funkcje `Variant 2`są `Variant 3`oznaczone `Variant 1`, i , do identyfikacji w następującej dyskusji):

```cpp
Fraction &Add( Fraction &f, long l );       // Variant 1
Fraction &Add( long l, Fraction &f );       // Variant 2
Fraction &Add( Fraction &f, Fraction &f );  // Variant 3

Fraction F1, F2;
```

Należy wziąć pod uwagę następującą instrukcję:

```cpp
F1 = Add( F2, 23 );
```

Poprzednia instrukcja tworzy dwa zestawy:

|Zestaw 1: Funkcje kandydujące, które mają pierwszy argument ułamka typu|Zestaw 2: Funkcje kandydujące, których drugi argument można przekonwertować na **typ int**|
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
|Wariant 1|Wariant 1 **(int** można przekonwertować na **długi** przy użyciu standardowej konwersji)|
|Wariant 3||

Funkcje w zestawie 2 to funkcje, dla których istnieją niejawne konwersje z rzeczywistego typu parametru do typu parametru formalnego, a wśród takich funkcji istnieje funkcja, dla której "koszt" konwersji rzeczywistego typu parametru na jego typ parametru formalnego jest najmniejszy.

Przecięcie tych dwóch zestawów jest wariant 1. Przykładem niejednoznacznego wywołania funkcji jest:

```cpp
F1 = Add( 3, 6 );
```

Poprzednie wywołanie funkcji tworzy następujące zestawy:

|Zestaw 1: Funkcje kandydata, które mają pierwszy argument typu **int**|Zestaw 2: Funkcje kandydujące, które mają drugi argument typu **int**|
|---------------------------------------------------------------------|----------------------------------------------------------------------|
|Wariant 2 **(int** można przekonwertować na **długi** przy użyciu standardowej konwersji)|Wariant 1 **(int** można przekonwertować na **długi** przy użyciu standardowej konwersji)|

Ponieważ przecięcie tych dwóch zestawów jest puste, kompilator generuje komunikat o błędzie.

W przypadku dopasowywania argumentów funkcja z *n* argumentami domyślnymi jest traktowana jako *n*+1 oddzielne funkcje, z których każda ma inną liczbę argumentów.

Wielokropek (...) działa jako symbol wieloznaczny; pasuje do każdego rzeczywistego argumentu. Może to prowadzić do wielu niejednoznacznych zestawów, jeśli nie zaprojektujesz przeciążonych zestawów funkcji ze szczególną ostrożnością.

> [!NOTE]
> Niejednoznaczności przeciążonych funkcji nie można określić, dopóki nie zostanie napotkane wywołanie funkcji. W tym momencie zestawy są tworzone dla każdego argumentu w wywołaniu funkcji i można określić, czy istnieje jednoznaczne przeciążenie. Oznacza to, że niejasności mogą pozostać w kodzie, dopóki nie zostaną wywołane przez wywołanie określonej funkcji.

## <a name="argument-type-differences"></a>Różnice typu argumentów

Przeciążone funkcje rozróżniają typy argumentów, które przyjmują różne inicjatory. W związku z tym argument danego typu i odwołanie do tego typu są uważane za takie same dla celów przeciążenia. Są one uważane za takie same, ponieważ biorą te same inicjatory. Na przykład, `max( double, double )` jest uważany `max( double &, double & )`za taki sam jak . Deklarowanie dwóch takich funkcji powoduje błąd.

Z tego samego powodu argumenty funkcji typu zmodyfikowanego przez **const** lub **volatile** nie są traktowane inaczej niż typ podstawowy do celów przeciążenia.

Jednak mechanizm przeciążania funkcji można odróżnić odwołania, które są kwalifikowane przez **const** i **volatile** i odwołania do typu podstawowego. To sprawia, że kod, takich jak następujące możliwe:

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

Wskaźniki do **const** i **volatile** obiektów są również uważane za różne od wskaźników do typu podstawowego na potrzeby przeciążenia.

## <a name="argument-matching-and-conversions"></a>Dopasowywanie argumentów i konwersje

Gdy kompilator próbuje dopasować rzeczywiste argumenty do argumentów w deklaracjach funkcji, może dostarczyć konwersji standardowych lub zdefiniowanych przez użytkownika, aby uzyskać poprawny typ, jeśli nie można znaleźć dokładne dopasowanie. Zastosowanie konwersji podlega tym zasadom:

- Sekwencje konwersji, które zawierają więcej niż jedną konwersję zdefiniowaną przez użytkownika, nie są brane pod uwagę.

- Sekwencje konwersji, które można skrócić przez usunięcie konwersji pośrednich, nie są brane pod uwagę.

Wynikowa sekwencja konwersji, jeśli istnieje, jest nazywany najlepszą sekwencją dopasowania. Istnieje kilka sposobów konwersji obiektu typu **int** na typ **niepodpisany długo** przy użyciu standardowych konwersji (opisanych w [konwersjach standardowych):](../cpp/standard-conversions.md)

- Konwersja z **int** na **długi,** a następnie z **długiej** na **niepodpisaną długą**.

- Konwersja z **int** na **niepodpisaną długą**.

Pierwsza sekwencja, mimo że osiąga pożądany cel, nie jest najlepszą sekwencją dopasowywania — istnieje krótsza sekwencja.

W poniższej tabeli przedstawiono grupę konwersji, zwaną konwersjami trywialnymi, które mają ograniczony wpływ na określenie, która sekwencja jest najlepiej dopasowana. Wystąpienia, w których konwersje trywialne wpływają na wybór sekwencji są omówione na liście po tabeli.

### <a name="trivial-conversions"></a>Trywialne konwersje

|Konwertuj z typu|Konwertuj na typ|
|-----------------------|---------------------|
|*nazwa typu*|*nazwa typu***&**|
|*nazwa typu***&**|*nazwa typu*|
|*nazwa typu* **[ ]**|*nazwa typu*__\*__|
|*nazwa typu* **(** *lista argumentów* **)**|**(** __\*__ *nazwa typu* ) **(** *lista argumentów* **)**|
|*nazwa typu*|*nazwa typu* **const**|
|*nazwa typu*|nazwa typu **nietrwałego** *type-name*|
|*nazwa typu*__\*__|*nazwa typu* **const**__\*__|
|*nazwa typu*__\*__|nazwa typu **nietrwałego** *type-name*__\*__|

Kolejność, w której próbowano konwersji jest następująca:

1. Dokładne dopasowanie. Dokładne dopasowanie między typami, z którymi funkcja jest wywoływana i typy zadeklarowane w prototypie funkcji jest zawsze najlepszym dopasowaniem. Sekwencje banalnych konwersji są klasyfikowane jako dokładne dopasowania. Jednak sekwencje, które nie tworzą żadnej z tych konwersji są uważane za lepsze niż sekwencje, które konwertują:

   - Od wskaźnika, do wskaźnika do **const** (`type` <strong>\*</strong> do **const** `type` <strong>\*</strong>).

   - Od wskaźnika do wskaźnika do **lotnych** (do`type` <strong>\*</strong> **lotnych).** `type` <strong>\*</strong>

   - Od odniesienia do odniesienia do`type` **&** **const** ( do **const** `type` **&**).

   - Od odniesienia do odniesienia`type` **&** do **lotnych** ( do **lotnych).** `type` **&**

1. Dopasuj za pomocą promocji. Każda sekwencja, która nie została sklasyfikowana jako dokładne dopasowanie, która zawiera tylko integralne promocje, konwersje z **float** na **double**i banalne konwersje są klasyfikowane jako dopasowanie za pomocą promocji. Chociaż mecz nie jest tak dobry jak w każdym dopasowaniu, mecz z użyciem promocji jest lepszy niż mecz przy użyciu standardowych konwersji.

1. Dopasuj za pomocą standardowych konwersji. Każda sekwencja, która nie została sklasyfikowana jako dopasowanie ścisłe lub dopasowanie przy użyciu promocji, które zawierają tylko standardowe konwersje i trywialne konwersje, jest klasyfikowana jako dopasowana przy użyciu standardowych konwersji. W ramach tej kategorii stosuje się następujące zasady:

   - Konwersja ze wskaźnika do klasy pochodnej do wskaźnika do bezpośredniej lub `void *` pośredniej klasy podstawowej jest korzystniejsza niż konwersja do lub `const void *`. .

   - Konwersja ze wskaźnika do klasy pochodnej, do wskaźnika do klasy podstawowej daje lepsze dopasowanie bliżej klasy podstawowej jest do bezpośredniej klasy podstawowej. Załóżmy, że hierarchia klas jest przedstawiona na poniższym rysunku.

![Wykres preferowanych konwersji](../cpp/media/vc391t1.gif "Wykres preferowanych konwersji") <br/>
Wykres przedstawiający preferowane konwersje

Konwersja `D*` z `C*` typu na typ jest `D*` korzystniejsza niż konwersja z typu na typ `B*`. Podobnie konwersja z `D*` typu `B*` na typ jest `D*` korzystniejsza niż konwersja z typu na typ `A*`.

Ta sama reguła ma zastosowanie do konwersji referencyjnych. Konwersja `D&` z `C&` typu na typ jest `D&` korzystniejsza niż konwersja z typu na typ `B&`i tak dalej.

Ta sama reguła dotyczy konwersji typu wskaźnik do elementu członkowskiego. Konwersja `T D::*` z `T C::*` typu na typ jest `T D::*` korzystniejsza niż konwersja z typu na typ `T B::*`i tak dalej (gdzie `T` jest typ elementu członkowskiego).

Poprzednia reguła ma zastosowanie tylko wzdłuż danej ścieżki wyprowadzania. Należy wziąć pod uwagę wykres pokazany na poniższym rysunku.

![Wielokrotne dziedziczenie&#45;, które pokazuje preferowane konwersje](../cpp/media/vc391t2.gif "Wielokrotne dziedziczenie&#45;, które pokazuje preferowane konwersje") <br/>
Wykres wielokrotnego dziedziczenia przedstawiający preferowane konwersje

Konwersja `C*` z `B*` typu na typ jest `C*` korzystniejsza niż konwersja z typu na typ `A*`. Powodem jest to, że są `B*` na tej samej drodze i jest bliżej. Jednak konwersja `C*` z `D*` typu na typ nie jest `A*`korzystniejsza niż konwersja na typ; nie ma żadnych preferencji, ponieważ konwersje podążają różnymi ścieżkami.

1. Dopasuj do konwersji zdefiniowanych przez użytkownika. Tej sekwencji nie można klasyfikować jako dopasowania ścisłego, dopasowania przy użyciu promocji lub dopasowania przy użyciu standardowych konwersji. Sekwencja musi zawierać tylko konwersje zdefiniowane przez użytkownika, konwersje standardowe lub trywialne konwersje, które mają być klasyfikowane jako zgodne z konwersjami zdefiniowanymi przez użytkownika. Dopasowanie do konwersji zdefiniowanych przez użytkownika jest uważane za lepsze dopasowanie niż dopasowanie z wielokropkiem, ale nie tak dobre dopasowanie jak dopasowanie do standardowych konwersji.

1. Dopasuj do wielokropek. Każda sekwencja, która pasuje do wielokropek w deklaracji jest klasyfikowany jako dopasowanie z wielokropka. Jest uważany za najsłabszy mecz.

Konwersje zdefiniowane przez użytkownika są stosowane, jeśli nie istnieje wbudowana promocja lub konwersja. Konwersje te są wybierane na podstawie typu dopasowanego argumentu. Spójrzmy na poniższy kod:

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

Dostępne konwersje zdefiniowane przez `UDC` użytkownika dla klasy są od typu **int** i typu **long**. W związku z tym kompilator uwzględnia konwersje dla typu `UDC`obiektu, który jest dopasowywany: . Istnieje konwersja **na int** i jest zaznaczona.

Podczas procesu dopasowywania argumentów można zastosować standardowe konwersje zarówno do argumentu, jak i do wyniku konwersji zdefiniowanej przez użytkownika. W związku z tym działa następujący kod:

```cpp
void LogToFile( long l );
...
UDC udc;
LogToFile( udc );
```

W poprzednim przykładzie konwersja zdefiniowana przez użytkownika, **operator** `udc` long , jest wywoływana w celu konwersji na typ **long**. Gdyby nie zdefiniowano **konwersji** zdefiniowanej przez użytkownika na typ długo, `UDC` konwersja przebiegłaby w następujący sposób: Typ zostałby przekonwertowany na **int** przy użyciu konwersji zdefiniowanej przez użytkownika. Następnie standardowa konwersja z typu **int** do typu **long** zostałaby zastosowana w celu dopasowania argumentu w deklaracji.

Jeśli wszystkie konwersje zdefiniowane przez użytkownika są wymagane do dopasowania argumentu, standardowe konwersje nie są używane podczas oceny najlepszego dopasowania. Nawet jeśli więcej niż jedna funkcja kandydata wymaga konwersji zdefiniowanej przez użytkownika, funkcje są uważane za równe. Przykład:

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

Obie wersje `Func` wymagają konwersji zdefiniowanej przez użytkownika w celu konwersji typu **int** na argument typu klasy. Możliwe konwersje to:

- Konwertuj z `UDC1` typu **int** na typ (konwersja zdefiniowana przez użytkownika).

- Konwertuj z typu **int** na typ **długi;** następnie konwertuj na typ `UDC2` (konwersja dwuetapowa).

Mimo że druga wymaga zarówno konwersji standardowej, jak i konwersji zdefiniowanej przez użytkownika, obie konwersje są nadal uważane za równe.

> [!NOTE]
> Konwersje zdefiniowane przez użytkownika są uważane za konwersję według konstrukcji lub konwersji przez inicjację (funkcja konwersji). Obie metody są uważane za równe, biorąc pod uwagę najlepsze dopasowanie.

## <a name="argument-matching-and-the-this-pointer"></a>Dopasowywanie argumentów i ten wskaźnik

Funkcje elementów członkowskich klasy są traktowane inaczej, w zależności od tego, czy są one zadeklarowane jako **statyczne**. Ponieważ funkcje niestatyczne mają niejawny argument, który dostarcza **ten** wskaźnik, funkcje niestatyczne są uważane za mają jeden argument więcej niż funkcje statyczne; w przeciwnym razie są one zadeklarowane identycznie.

Te niestatyczne funkcje członkowskie wymagają, aby implikowany **ten** wskaźnik odpowiadał typowi obiektu, za pomocą którego wywoływana jest funkcja, lub w przypadku przeciążonych operatorów, wymagają, aby pierwszy argument odpowiadał obiektowi, na którym jest stosowany operator. (Aby uzyskać więcej informacji na temat przeciążonych operatorów, zobacz [Przeciążone operatory](../cpp/operator-overloading.md).)

W przeciwieństwie do innych argumentów w przeciążonych funkcji, nie obiekty tymczasowe są wprowadzane i nie konwersje są podejmowane podczas próby dopasowania **tego** argumentu wskaźnika.

Gdy `->` operator wyboru elementu członkowskiego jest używany do `class_name`uzyskiwania dostępu do funkcji `class_name * const`elementu członkowskiego klasy, **ten** argument wskaźnika ma typ . Jeśli elementy członkowskie są zadeklarowane jako **const** lub **volatile**, typy są `const class_name * const` i `volatile class_name * const`, odpowiednio.

Operator `.` wyboru elementu członkowskiego działa dokładnie w ten `&` sam sposób, z tą różnicą, że operator niejawny (adres) jest poprzedzony nazwą obiektu. W poniższym przykładzie pokazano, jak to działa:

```cpp
// Expression encountered in code
obj.name

// How the compiler treats it
(&obj)->name
```

Lewy operand `->*` operatorów i `.*` (wskaźnik do elementu członkowskiego) `.` są `->` traktowane w taki sam sposób jak operatory i (wybór elementu członkowskiego) w odniesieniu do dopasowywania argumentów.

## <a name="ref-qualifiers-on-member-functions"></a><a name="ref-qualifiers"></a>Ref-kwalifikatory dla funkcji członkowskich

Ref kwalifikatory umożliwiają przeciążenie funkcji elementu członkowskiego na podstawie **tego,** czy obiekt wskazywał przez to wartość rvalue lub lvalue.  Ta funkcja może służyć do uniknięcia niepotrzebnych operacji kopiowania w scenariuszach, w których nie można zapewnić dostęp wskaźnika do danych. Załóżmy na `C` przykład, że klasa inicjuje niektóre dane w konstruktorze i zwraca kopię tych danych w funkcji `get_data()`elementu członkowskiego . Jeśli obiekt typu `C` jest rvalue, który ma zostać zniszczony, kompilator `get_data() &&` wybierze przeciążenie, które przenosi dane, a nie je skopiować.

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

## <a name="restrictions-on-overloading"></a>Ograniczenia dotyczące przeciążenia

Kilka ograniczeń reguluje dopuszczalny zestaw przeciążonych funkcji:

- Wszystkie dwie funkcje w zestawie przeciążonych funkcji muszą mieć różne listy argumentów.

- Przeciążanie funkcji z listami argumentów tych samych typów, na podstawie samego typu zwracanego, jest błędem.

     **Specyficzne dla firmy Microsoft**

Operator przeciążenia **można przeciążenia nowy** wyłącznie na podstawie typu zwracanego — w szczególności, na podstawie modyfikatora modelu pamięci określony.

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

- Funkcje członkowskie nie mogą być przeciążone wyłącznie na podstawie jednego jest statyczne, a inne niestatyczne.

- **deklaracje typedef** nie definiują nowych typów; wprowadzają synonimy dla istniejących typów. Nie wpływają one na mechanizm przeciążenia. Spójrzmy na poniższy kod:

    ```cpp
    typedef char * PSTR;

    void Print( char *szToPrint );
    void Print( PSTR szToPrint );
    ```

   Dwie poprzednie funkcje mają identyczne listy argumentów. `PSTR`jest synonimem typu `char *`. W zakresie członkowskim ten kod generuje błąd.

- Wyliczane typy są różne typy i może służyć do rozróżniania funkcji przeciążonych.

- Typy "tablica" i "wskaźnik do" są uważane za identyczne do celów rozróżnienia między przeciążonymi funkcjami, ale tylko dla pojedynczo wymiarowanych tablic. Dlatego te przeciążone funkcje powodują konflikt i generują komunikat o błędzie:

    ```cpp
    void Print( char *szToPrint );
    void Print( char szToPrint[] );
    ```

   W przypadku tablic wymiarowanych mnożenie drugi i wszystkie kolejne wymiary są uważane za część typu. W związku z tym są one używane do rozróżniania przeciążonych funkcji:

    ```cpp
    void Print( char szToPrint[] );
    void Print( char szToPrint[][7] );
    void Print( char szToPrint[][9][42] );
    ```

## <a name="overloading-overriding-and-hiding"></a>Przeciążanie, zastępowanie i ukrywanie

Wszelkie dwie deklaracje funkcji o tej samej nazwie w tym samym zakresie, mogą odwoływać się do tej samej funkcji lub do dwóch funkcji dyskretnych, które są przeciążone. Jeśli wykazy argumentów deklaracji zawierają równoważne typy argumentów (zgodnie z opisem w poprzedniej sekcji), deklaracje funkcji odnoszą się do tej samej funkcji. W przeciwnym razie, odnoszą się do dwóch różnych funkcji, które są wybrane za pomocą przeciążenia.

Zakres klasy jest ściśle przestrzegany; w związku z tym funkcja zadeklarowana w klasie podstawowej nie jest w tym samym zakresie jako funkcja zadeklarowana w klasie pochodnej. Jeśli funkcja w klasie pochodnej jest zadeklarowana o takiej samej nazwie jak funkcja wirtualna w klasie podstawowej, funkcja klasy pochodnej *zastępuje* funkcję klasy podstawowej. Aby uzyskać więcej informacji, zobacz [Funkcje wirtualne](../cpp/virtual-functions.md).

Jeśli funkcja klasy podstawowej nie jest zadeklarowana jako "wirtualna", funkcja klasy pochodnej jest nazywana *ukrywanie.* Zarówno nadrzędne i ukrywanie różnią się od przeciążenia.

Zakres bloku jest ściśle przestrzegany; w związku z tym funkcja zadeklarowana w zakresie pliku nie jest w tym samym zakresie jako funkcja zadeklarowana lokalnie. Jeśli funkcja zadeklarowana lokalnie ma taką samą nazwę, co funkcja zadeklarowana w zakresie pliku, funkcja zadeklarowana lokalnie ukrywa funkcje należącą do zakresu pliku, zamiast powodować przeciążenie. Przykład:

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

Poprzedni kod pokazuje dwie definicje funkcji `func`. Definicja, która przyjmuje `char *` argument typu `main` jest lokalny ze względu na **extern** instrukcji. W związku z tym definicja, która przyjmuje argument typu **int** jest ukryty, a pierwsze wywołanie `func` jest w błędzie.

Dla przeciążonych funkcji członkowskich, różne wersje funkcji mogą mieć różne przywileje dostępu. Ale nadal uważa się, że znajdują się w zakresie otaczającym klasę, a więc są funkcjami przeciążonymi. Rozważmy poniższy kod, w którym funkcja członkowska `Deposit` jest przeciążona; jedna wersja jest publiczna, inne są prywatne.

Zamiarem tego przykładu jest dostarczenie klasy `Account`, w której wymagane jest poprawne hasło, aby wykonać depozyty. Odbywa się to za pomocą przeciążenia.

Wywołanie `Deposit` w `Account::Deposit` wywołuje funkcję prywatnego elementu członkowskiego. To wywołanie `Account::Deposit` jest poprawne, ponieważ jest funkcją elementu członkowskiego i ma dostęp do prywatnych członków klasy.

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
