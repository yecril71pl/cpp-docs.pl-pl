---
title: Przeciążanie funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 1/25/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function overloading [C++], about function overloading
- function overloading
- declaring functions [C++], overloading
ms.assetid: 3c9884cb-1d5e-42e8-9a49-6f46141f929e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d942e2c5bca7d86e66cb579de1cbe946cb9f5f6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081498"
---
# <a name="function-overloading"></a>Przeładowywanie funkcji

C++ umożliwia określenie więcej niż jednej funkcji o tej samej nazwie w tym samym zakresie. Są to tak zwane *przeciążone* funkcji. Przeciążone funkcje umożliwiają podanie różnego znaczenia dla funkcji, w zależności od typu i liczby argumentów.

Na przykład `print` funkcji, która przyjmuje `std::string` argument może wykonywać bardzo różne zadania niż ta, która przyjmuje argument typu **double**. Przeciążanie pozwala uniknąć używać nazw takich jak `print_string` lub `print_double`. W czasie kompilacji kompilator wybiera, które przeładowanie do użycia na podstawie typu przekazanych przez obiekt wywołujący argumentów.  Jeśli wywołasz `print(42.0)` , a następnie `void print(double d)` zostanie wywołana funkcja. Jeśli wywołasz `print("hello world")` , a następnie `void print(std::string)` przeciążenia zostaną wywołane.

Możesz doprowadzić do przeciążenia funkcji elementów członkowskich i funkcje nieczłonkowskie. W poniższej tabeli przedstawiono, które części deklaracji funkcji język C++ używa do rozróżniania grup funkcji o tej samej nazwie w tym samym zakresie.

### <a name="overloading-considerations"></a>Zagadnienia przeciążania

|Element deklaracji funkcji|Używany w przeciążaniu?|
|----------------------------------|---------------------------|
|Typ zwracany przez funkcję|Nie|
|Liczba argumentów|Tak|
|Typ argumentów|Tak|
|Obecność lub brak wielokropka|Tak|
|Korzystanie z **typedef** nazwy|Nie|
|Nieokreślone granice tablic|Nie|
|**Const** lub **volatile**|Tak, gdy jest stosowany do całej funkcji|
|[ref-qualifier](#ref-qualifier)|Tak|

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

Argument domyślny nie jest uważany za część dla typu funkcji. W związku z tym nieużywanych wyborze przeciążonych funkcji. Dwie funkcje, które różnią się tylko w ich argumenty domyślne są traktowane jako wiele definicji zamiast przeciążone funkcje.

Nie można dostarczyć domyślne argumenty dla operatorów przeciążonych.

## <a name="argument-matching"></a>Dopasowywanie argumentów

Funkcje przeciążone są zaznaczone dla najlepsze dopasowanie deklaracji funkcji w bieżącym zakresie argumentów w wywołaniu funkcji. Jeśli odpowiednia funkcja zostanie znaleziony, że funkcja jest wywoływana. "Odpowiedni" w tym kontekście oznacza, że jeden z następujących czynności:

- Znaleziono dokładnego dopasowania.

- Prosta Konwersja została wykonana.

- Promocja typu całkowitego została wykonana.

- Istnieje standardowa konwersja na typ żądanego argumentu.

- Konwersja zdefiniowana przez użytkownika (operator konwersji lub konstruktora) na typ żądanego argumentu istnieje.

- Argumenty reprezentowane przez wielokropek znaleziono.

Kompilator tworzy zestaw Release Candidate funkcji dla każdego argumentu. Funkcje kandydujące są funkcje, w których rzeczywisty argument, w tym miejscu można przekonwertować na typ argumentu formalnego.

Zestaw "najlepiej dopasowaną funkcji" jest przeznaczony dla każdego argumentu i wybranej funkcji jest przecięcia wszystkich zestawów. Jeśli część wspólną zawiera więcej niż jedną funkcję, przeciążenie jest niejednoznaczne i generuje błąd. Funkcja, która jest ostatecznie zaznaczone jest zawsze lepsze dopasowane niż co innych funkcji, w grupie co najmniej jednego argumentu. Wywołanie funkcji generuje błąd, jeśli nie jest to wymagane (jeśli ma nie wyczyść zwycięzca).

Rozważ następujące deklaracje (funkcje są oznaczone `Variant 1`, `Variant 2`, i `Variant 3`, dla identyfikatora w następujących dyskusji):

```cpp
Fraction &Add( Fraction &f, long l );       // Variant 1
Fraction &Add( long l, Fraction &f );       // Variant 2
Fraction &Add( Fraction &f, Fraction &f );  // Variant 3

Fraction F1, F2;
```

Rozważmy następującą instrukcję:

```cpp
F1 = Add( F2, 23 );
```

Poprzednia instrukcja tworzy dwa zestawy:

|Zestaw 1: Release Candidate funkcji, które mają pierwszy Argument typu ułamka|Zestaw 2: Release Candidate funkcje Whose drugi Argument można przekonwertować na typ **int**|
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
|Wariantu 1|Wariantu 1 (**int** mogą być konwertowane na **długie** za pomocą konwersji standardowej)|
|Variant 3||

Funkcje w wersji 2 zestawu są funkcje, dla której są niejawną konwersję z typu rzeczywisty parametr formalny parametr typu, a wśród tych funkcji jest funkcją, dla którego jest "cost" konwersji typu rzeczywistego parametru typu formalnego parametru najmniejszy.

Przecięcie tymi dwoma zestawami jest wariantu 1. Przykład wywołania niejednoznacznego funkcji to:

```cpp
F1 = Add( 3, 6 );
```

Poprzedniego wywołania funkcji kompilacje następujących zestawów:

|Zestaw 1: Release Candidate funkcje, mają pierwszy Argument typu **int**|Zestaw 2: Release Candidate funkcje, mieć drugi Argument typu **int**|
|---------------------------------------------------------------------|----------------------------------------------------------------------|
|Variant 2 (**int** mogą być konwertowane na **długie** za pomocą konwersji standardowej)|Wariantu 1 (**int** mogą być konwertowane na **długie** za pomocą konwersji standardowej)|

Należy pamiętać, że część wspólną między tymi dwoma zestawami jest pusty. W związku z tym kompilator generuje komunikat o błędzie.

Dla argumentu dopasowania funkcji z *n* argumenty domyślne jest traktowany jako *n*funkcje oddzielne + 1, każda z różną liczbę argumentów.

Działa wielokropek (...) jako symbolu wieloznacznego; Dopasowuje dowolny z rzeczywistych argumentów. Może to prowadzić do wielu zestawów niejednoznaczny, jeżeli nie należy projektować swoje zestawy przeciążonej funkcji z rozwagą.

> [!NOTE]
>  Nie można ustalić niejednoznaczności przeciążonych funkcji, dopóki nie zostanie osiągnięty wywołania funkcji. W tym momencie zestawy są tworzone dla każdego argumentu w wywołaniu funkcji, a następnie można określić, czy istnieje jednoznaczna przeciążenie. Oznacza to, że niejednoznaczności może pozostać w kodzie, dopóki nie są one przywołane przez wywołanie konkretną funkcję.

## <a name="argument-type-differences"></a>Różnice typu argumentów

Przeciążone funkcje rozróżnienia między typami argumentów, które przyjmują różne inicjatory. W związku z tym argument danego typu i odwołania do tego typu są traktowane jako takie same na potrzeby logowania. Są uważane za takie same ponieważ przyjmują tego samego inicjatory. Na przykład `max( double, double )` uznaje się taka sama jak `max( double &, double & )`. Deklarowanie dwóch takich funkcji spowoduje wystąpienie błędu.

Z tego samego powodu argumenty typu, który został zmodyfikowany przez funkcji **const** lub **volatile** nie są traktowane inaczej niż typu podstawowego na potrzeby logowania.

Jednak funkcja przeciążenie mechanizm może rozróżnić odwołań, które są kwalifikowane przez **const** i **volatile** i odwołania do typu podstawowego. To sprawia, że kod taki jak następujące możliwości:

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

Wskaźniki do **const** i **volatile** obiektów są także traktowane jako inny niż wskaźniki do typu podstawowego na potrzeby logowania.

## <a name="argument-matching-and-conversions"></a>Konwersje i dopasowania argumentów

Gdy kompilator próbuje dopasować rzeczywiste argumenty względem argumentów w deklaracjach funkcji, go podać standardowych lub zdefiniowanych przez użytkownika konwersje do uzyskania dokładnego dopasowania można znaleźć poprawnego typu. Aplikacja konwersje podlega te reguły:

- Sekwencje konwersje, które zawierają więcej niż jednej konwersji zdefiniowanej przez użytkownika nie są uwzględniane.

- Sekwencje konwersji, które zostać skrócony, usuwając pośrednich konwersje nie są uwzględniane.

Wynikowe sekwencji konwersji, jeśli istnieje, nosi nazwę najlepiej dopasowaną sekwencji. Istnieje kilka sposobów, aby przekonwertować obiektu typu **int** na typ **unsigned long** przy użyciu standardowych konwersji (opisanych w [konwersje standardowe](../cpp/standard-conversions.md)):

- Konwertowanie z **int** do **długie** a następnie z **długie** do **unsigned long**.

- Konwertowanie z **int** do **unsigned long**.

Pierwszej sekwencji, mimo że powoduje to osiągnięcie żądanego celu nie jest najlepiej dopasowaną sekwencji — istnieje sekwencja krótszy.

W poniższej tabeli przedstawiono grupy konwersji, o nazwie trivial konwersji, które mają ograniczony wpływ na temat określania, jaka sekwencja jest najlepsze dopasowanie. Wystąpienia, w których trivial konwersje wpływa na wybór sekwencji zostały omówione w liście pod tabelą.

### <a name="trivial-conversions"></a>Konwersje prosta

|Konwersja z typu|Konwertowanie na typ|
|-----------------------|---------------------|
|*Nazwa typu*|*Nazwa typu* **&**|
|*Nazwa typu* **&**|*Nazwa typu*|
|*Nazwa typu* **]**|*Nazwa typu\**|
|*Nazwa typu* **(** *listy argumentów* **)**|**(**  *\*nazwy typu* **) (** *listy argumentów* **)**|
|*Nazwa typu*|**Const** *Nazwa typu*|
|*Nazwa typu*|**volatile** *Nazwa typu*|
|*Nazwa typu\**|**Const** *Nazwa typu\**|
|*Nazwa typu\**|**volatile** *Nazwa typu\**|

Kolejność, w którym są próby konwersji jest następująca:

1. Dokładne dopasowanie. Dokładne dopasowanie między typami, z którymi funkcja jest wywoływana i typy zadeklarowane w prototyp funkcji jest zawsze najlepsze dopasowanie. Sekwencje trivial konwersje są klasyfikowane jako dokładne dopasowania. Jednak sekwencji, których nie należy do żadnego z tych konwersje są uważane za lepsze niż sekwencji, które konwertują:

   - Ze wskaźnika do wskaźnika do **const** (`type` <strong>\*</strong> do **const** `type` <strong>\*</strong> ).

   - Ze wskaźnika do wskaźnika do **volatile** (`type` <strong>\*</strong> do **volatile** `type` <strong>\*</strong>).

   - Z odwołania do odwołania do **const** (`type` **&** do **const** `type` **&**).

   - Z odwołania do odwołania do **volatile** (`type` **&** do **volatile** `type` **&**).

1. Dopasuj je przy użyciu promocji. Dowolnej sekwencji, które nie są klasyfikowane jako dokładne dopasowanie, który zawiera tylko promocje typów całkowitych, konwersje z **float** do **double**, i prosta konwersje są klasyfikowane jako dopasowanie za pomocą promocji. Jednak nie tak dobrze, dopasowanie dowolnej dokładne dopasowanie, dopasowanie za pomocą promocji jest lepsza niż przy użyciu standardowych konwersji dopasowania.

1. Dopasuj je przy użyciu standardowych konwersji. Dowolnej sekwencji nie sklasyfikowane jako dopasowanie dokładne lub dopasowania przy użyciu w promocjach, zawierający tylko konwersje standardowe i prosta konwersje zostanie sklasyfikowany jako dopasowanie przy użyciu standardowych konwersji. W ramach tej kategorii są stosowane następujące reguły:

   - Konwersja ze wskaźnika do klasy pochodnej na wskaźnik do bezpośredniej lub pośredniej klasy bazowej jest konwertowanie `void *` lub `const void *`.

   - Konwersja ze wskaźnika do klasy pochodnej na wskaźnik do klasy bazowej daje lepsze dopasowanie bliżej klasa bazowa ma bezpośrednią klasą bazową. Załóżmy, że jest hierarchii klas, jak pokazano na poniższej ilustracji.

![Preferowane konwersje](../cpp/media/vc391t1.gif "vc391T1") wykres pokazujący preferowane konwersje

Konwersja z typu `D*` na typ `C*` jest konwersja z typu `D*` na typ `B*`. Podobnie, konwersja z typu `D*` na typ `B*` jest konwersja z typu `D*` na typ `A*`.

Ta sama zasada dotyczy konwersje odwołań. Konwersja z typu `D&` na typ `C&` jest konwersja z typu `D&` na typ `B&`i tak dalej.

Ta sama zasada dotyczy konwersje wskaźników do elementów członkowskich. Konwersja z typu `T D::*` na typ `T C::*` jest konwersja z typu `T D::*` na typ `T B::*`i tak dalej (gdzie `T` jest typ elementu członkowskiego).

Poprzedni reguła ma zastosowanie tylko na ścieżce danego pochodnym. Należy wziąć pod uwagę wykres pokazano na poniższej ilustracji.

![Wiele&#45;dziedziczenia, pokazujący preferowanych konwersje](../cpp/media/vc391t2.gif "vc391T2") dziedziczenia wielokrotnego wykres pokazujący preferowanych konwersje

Konwersja z typu `C*` na typ `B*` jest konwersja z typu `C*` na typ `A*`. Przyczyną jest to, że znajdują się w tej samej ścieżce i `B*` zbliżonej. Jednak konwersja z typu `C*` na typ `D*` nieodpowiednim do konwersji na typ `A*`; jest Brak preferencji, ponieważ konwersje postępuj zgodnie z różnych ścieżek.

1. Zgodna z konwersje zdefiniowane przez użytkownika. Ta sekwencja nie mogą być klasyfikowane jako dokładne dopasowanie, dopasowanie za pomocą promocji lub przy użyciu standardowych konwersji dopasowania. Sekwencja musi zawierać tylko konwersje zdefiniowane przez użytkownika, konwersje standardowe lub trivial konwersji jest uważany za dopasowania konwersje zdefiniowane przez użytkownika. Dopasowania konwersje zdefiniowane przez użytkownika jest uważany za lepsze dopasowane niż dopasowania z wielokropkiem, ale nie tak dobrze, dopasowanie jako zgodny ze standardowych konwersji.

1. Zgodne z wielokropkiem. Dowolnej sekwencji, który odpowiada wielokropek w deklaracji jest klasyfikowana jako zgodny z wielokropkiem. To jest traktowany jako najsłabsza dopasowania.

Konwersje zdefiniowane przez użytkownika są stosowane, jeśli nie ma wbudowanych podwyższania poziomu ani konwersji. Te konwersje są wybierane na podstawie typu argumentu są dopasowywane. Rozważmy poniższy kod:

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

Dostępne zdefiniowane przez użytkownika konwersje na klasę `UDC` pochodzą z typu **int** i typ **długie**. W związku z tym, kompilator traktuje konwersji na typ obiektu są dopasowywane: `UDC`. Konwersja na **int** istnieje, i jest ono zaznaczone.

Podczas dopasowywania argumentów konwersje standardowe można zastosować do tego argumentu i wynik konwersji zdefiniowanej przez użytkownika. W związku z tym działa w następujący kod:

```cpp
void LogToFile( long l );
...
UDC udc;
LogToFile( udc );
```

W poprzednim przykładzie, konwersja zdefiniowana przez użytkownika **operator długie**, zostanie wywołana można skonwertować `udc` na typ **długie**. Jeśli nie zdefiniowana przez użytkownika konwersja na typ **długie** była zdefiniowana, konwersja będzie mieć zanalizować w następujący sposób: typ `UDC` będzie konwertowany na typ **int** przy użyciu zdefiniowanych przez użytkownika Konwersja. Następnie standardowa konwersja z typu **int** na typ **długie** będzie stosowane do dopasowania argumentów w deklaracji.

Jeśli wszystkie konwersje zdefiniowane przez użytkownika muszą być zgodne z argumentem, konwersje standardowe nie są używane podczas obliczania najlepsze dopasowanie. Ta zasada obowiązuje nawet wtedy, gdy więcej niż jednej funkcji kandydata wymaga konwersji zdefiniowanej przez użytkownika; w takim przypadku funkcje są uznawane za równe. Na przykład:

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

Obie wersje `Func` wymaga konwersji zdefiniowanej przez użytkownika w celu konwersji typu **int** argumentu typu klasy. Konwersje możliwe są następujące:

- Konwersja z typu **int** na typ `UDC1` (konwersja zdefiniowana przez użytkownika).

- Konwersja z typu **int** na typ **długie**; a następnie przekonwertować na typ `UDC2` (konwersji dwuetapowej).

Mimo że drugi z nich wymaga konwersji standardowej, a także konwersja zdefiniowana przez użytkownika, dwa konwersje są nadal uważane za równe.

> [!NOTE]
>  Konwersje zdefiniowane przez użytkownika są traktowane jako konwersji, konstruowania lub konwersja przez inicjowanie (funkcja konwersji). Obie metody są traktowane jako równe, rozważając najlepsze dopasowanie.

## <a name="argument-matching-and-the-this-pointer"></a>Dopasowanie argumentu i jego wskaźnika

Funkcje składowych klasy są traktowane inaczej w zależności od tego, czy są deklarowane jako **statyczne**. Ponieważ Niestatyczne funkcje mają niejawnego argumentu, który dostarcza **to** wskaźnik, Niestatyczne funkcje są uznawane za mieć jeden argument więcej niż statycznych funkcji; w przeciwnym razie są deklarowane identycznie.

Te Niestatyczne funkcje Członkowskie wymagającą dorozumianych **to** wskaźnik odpowiada typowi obiektu, za pomocą którego jest wywoływana funkcja lub dla operatorów przeciążonych wymagają one, czy pierwszy argument odpowiadają obiektu, na którym operator jest stosowany. (Aby uzyskać więcej informacji na temat przeciążonych operatorów, zobacz [przeciążone operatory](../cpp/operator-overloading.md).)

W przeciwieństwie do innych argumentów w funkcje przeciążone są wprowadzane nie obiekty tymczasowe i są próby konwersji, podczas próby dopasowania **to** argumentu będącego wskaźnikiem.

Gdy `->` operator wyboru elementów członkowskich umożliwia dostęp do funkcji składowej klasy `class_name`, **to** argumentu będącego wskaźnikiem ma typ `class_name * const`. Jeśli elementy członkowskie są zadeklarowane jako **const** lub **volatile**, typy są `const class_name * const` i `volatile class_name * const`, odpowiednio.

`.` Operator wyboru elementów członkowskich działa dokładnie tak samo, chyba że ukrytego `&` operatora (address-of) jest poprzedzana do nazwy obiektu. Poniższy przykład pokazuje, jak to działa:

```cpp
// Expression encountered in code
obj.name

// How the compiler treats it
(&obj)->name
```

Lewy operand `->*` i `.*` operatorów (wskaźnik do elementu członkowskiego) są traktowane tak samo, jak `.` i `->` operatorów (wyboru elementów członkowskich) w odniesieniu do dopasowania argumentów.

## <a name="ref-qualifiers"></a> Kwalifikatory ref w funkcjach składowych

Kwalifikatory umożliwiają przeciążyć funkcji składowej na podstawie tego, czy obiekt wskazywany przez **to** to rvalue lub l-wartością.  Ta funkcja może służyć w celu uniknięcia kopiowania niepotrzebne operacje w scenariuszach gdzie nie chcesz zapewnić dostęp wskaźnik do danych. Załóżmy na przykład, klasa `C` inicjuje niektóre dane w jego konstruktorze i zwraca kopię danych w funkcji składowej `get_data()`. Jeśli obiekt typu `C` to rvalue, który ma zostać zniszczone, a następnie wybierze kompilator `get_data() &&` przeciążenia, które przenosi dane, a nie skopiuj go.

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

Kilka ograniczeń określają dopuszczalne zestaw przeciążonych funkcji:

- Wszelkie dwie funkcje w zestaw przeciążonych funkcji musi mieć listy różnych argumentów.

- Przeładowywanie funkcji z listami argumentów tego samego typu, na podstawie zwracanego typu samodzielnie, występuje błąd.

     **Microsoft Specific**

Możesz doprowadzić do przeciążenia **nowy operator** wyłącznie w oparciu o typ zwracany — w szczególności na podstawie modyfikator model pamięci określona.

**END specyficzny dla Microsoft**

- Nie można przeciążyć funkcje Członkowskie wyłącznie na podstawie jednej są statyczne i innych nonstatic.

- **Element TypeDef** deklaracji nie zdefiniujesz nowe typy; wprowadzają synonimy dla istniejących typów. Nie wpływają one mechanizm przeciążania operacji. Rozważmy poniższy kod:

    ```cpp
    typedef char * PSTR;

    void Print( char *szToPrint );
    void Print( PSTR szToPrint );
    ```

   Poprzedni dwie funkcje mają listy argumentów identyczne. `PSTR` jest synonimem typu `char *`. W zakresie członka ten kod generuje błąd.

- Typy wyliczone są różnych typów i może służyć do rozróżnienia przeciążonych funkcji.

- Typy "tablica" i "wskaźnik" są traktowane jako w identyczne do celów rozróżniania przeciążonych funkcji. Jest to istotne tylko dla tablic zwymiarowany pojedynczo. W związku z tym następujące przeciążone funkcje konfliktu i generować komunikat o błędzie:

    ```cpp
    void Print( char *szToPrint );
    void Print( char szToPrint[] );
    ```

   Zwymiarowany mnożenie macierzy drugi i kolejne wszystkie wymiary są traktowane jako część tego typu. W związku z tym są one używane w rozróżniania przeciążonych funkcji:

    ```cpp
    void Print( char szToPrint[] );
    void Print( char szToPrint[][7] );
    void Print( char szToPrint[][9][42] );
    ```

## <a name="overloading-overriding-and-hiding"></a>Przeciążenie, zastępowanie i ukrywanie

Wszelkie dwie deklaracje funkcji o tej samej nazwie w tym samym zakresie, mogą odwoływać się do tej samej funkcji lub do dwóch funkcji dyskretnych, które są przeciążone. Jeśli wykazy argumentów deklaracji zawierają równoważne typy argumentów (zgodnie z opisem w poprzedniej sekcji), deklaracje funkcji odnoszą się do tej samej funkcji. W przeciwnym razie, odnoszą się do dwóch różnych funkcji, które są wybrane za pomocą przeciążenia.

Zakres klasy jest ściśle przestrzegany; w związku z tym, funkcja zadeklarowana w klasie bazowej nie jest w tym samym zakresie, co funkcja zadeklarowana w klasie pochodnej. Jeśli funkcja w klasie pochodnej jest zadeklarowana z taką samą nazwę jak funkcję wirtualną w klasie bazowej, funkcja klasy pochodnej *zastępuje* funkcji klasy podstawowej. Aby uzyskać więcej informacji, zobacz [funkcji wirtualnych](../cpp/virtual-functions.md).

Jeśli funkcja klasy bazowej nie jest zadeklarowana jako "virtual", a następnie funkcja klasy pochodnej jest nazywany *Ukryj* go. Zastępowanie i ukrywanie różnią się od przeciążenia.

Zakres bloku jest ściśle przestrzegany; w związku z tym, funkcja zadeklarowana w zakresie pliku nie jest w tym samym zakresie, co funkcja zadeklarowana lokalnie. Jeśli funkcja zadeklarowana lokalnie ma taką samą nazwę, co funkcja zadeklarowana w zakresie pliku, funkcja zadeklarowana lokalnie ukrywa funkcje należącą do zakresu pliku, zamiast powodować przeciążenie. Na przykład:

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

Poprzedni kod pokazuje dwie definicje funkcji `func`. Definicja która przyjmuje argument typu `char *` jest lokalną grupą `main` z powodu **extern** instrukcji. W związku z tym, definicja która przyjmuje argument typu **int** jest ukryta, a pierwsze wywołanie `func` wystąpił błąd.

Dla przeciążonych funkcji członkowskich, różne wersje funkcji mogą mieć różne przywileje dostępu. Ale nadal uważa się, że znajdują się w zakresie otaczającym klasę, a więc są funkcjami przeciążonymi. Rozważmy poniższy kod, w którym funkcja członkowska `Deposit` jest przeciążona; jedna wersja jest publiczna, inne są prywatne.

Zamiarem tego przykładu jest dostarczenie klasy `Account`, w której wymagane jest poprawne hasło, aby wykonać depozyty. Jest to uzyskiwane za pomocą przeciążenia.

Należy zauważyć, że wywołanie `Deposit` w klasie `Account::Deposit` wywołuje prywatne funkcje członkowskie. To wywołanie jest poprawne, ponieważ `Account::Deposit` jest funkcją składową, a zatem ma dostęp do prywatnych składowych klasy.

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

## <a name="see-also"></a>Zobacz także

[Funkcje (C++)](../cpp/functions-cpp.md)