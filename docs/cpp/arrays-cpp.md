---
title: Tablice (C++)
ms.date: 11/14/2019
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
ms.openlocfilehash: 91c57a9c4ef190dcace1813dd81739ac72e6b358
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188989"
---
# <a name="arrays-c"></a>Tablice (C++)

Tablica jest sekwencją obiektów tego samego typu, które zajmują ciągły obszar pamięci. Tradycyjne tablice języka C są źródłem wielu błędów, ale są nadal wspólne, szczególnie w przypadku starszych baz kodu. W nowoczesnych C++wersjach zdecydowanie zalecamy użycie [std:: Vector](../standard-library/vector-class.md) lub [std:: Array](../standard-library/array-class-stl.md) zamiast tablic w stylu C opisanych w tej sekcji. Oba te standardowe typy bibliotek przechowują swoje elementy jako ciągły blok pamięci, ale zapewniają znacznie większe bezpieczeństwo typów oraz Iteratory, które mają na celu wskazanie prawidłowej lokalizacji w sekwencji. Aby uzyskać więcej informacji, zobacz [kontenery C++(nowoczesne)](containers-modern-cpp.md).

## <a name="stack-declarations"></a>Deklaracje stosu

W deklaracji C++ tablicy rozmiar tablicy jest określany po nazwie zmiennej, a nie po nazwie typu, tak jak w innych językach. Poniższy przykład deklaruje tablicę 1000 podwaja się do przydzielenia na stosie. Liczba elementów musi być podana jako literał typu Integer lub else jako wyrażenie stałe, ponieważ kompilator musi wiedzieć, ile miejsca na stosie ma przydzielić; nie można użyć wartości obliczanej w czasie wykonywania. Każdy element w tablicy ma przypisaną wartość domyślną 0. Jeśli nie przypiszesz wartości domyślnej, każdy element początkowo będzie zawierał wszystkie losowe wartości, które będą znajdować się w tej lokalizacji.

```cpp
    constexpr size_t size = 1000;

    // Declare an array of doubles to be allocated on the stack
    double numbers[size] {0};

    // Assign a new value to the first element
    numbers[0] = 1;

    // Assign a value to each subsequent element
    // (numbers[1] is the second element in the array.)
    for (size_t i = 1; i < size; i++)
    {
        numbers[i] = numbers[i-1] * 1.1;
    }

    // Access each element
    for (size_t i = 0; i < size; i++)
    {
        std::cout << numbers[i] << " ";
    }
```

Pierwszy element w tablicy to element 0th, a ostatni element to (*n*-1), gdzie *n* to liczba elementów, które może zawierać tablica. Liczba elementów w deklaracji musi być typu całkowitego i musi być większa niż 0. Użytkownik jest odpowiedzialny za zapewnienie, że program nigdy nie przekaże wartości do operatora indeksu dolnego, który jest większy niż `(size - 1)`.

Tablica o rozmiarze zerowym jest dozwolona tylko wtedy, gdy tablica jest ostatnim polem w **strukturze** lub **Unii** i gdy włączone są rozszerzenia Microsoft (/ze).

Tablice oparte na stosie są szybsze do przydzielania i uzyskiwania dostępu do tablic opartych na stercie, ale liczba elementów nie może być tak duża, że zużywa zbyt dużo pamięci stosu. Jak dużo jest zbyt wiele zależy od programu. Za pomocą narzędzi profilowania można określić, czy tablica jest zbyt duża.

## <a name="heap-declarations"></a>Deklaracje sterty

Jeśli wymagana jest tablica, która jest zbyt duża, aby mogła zostać przydzielona na stosie lub której rozmiar nie może być znany w czasie kompilacji, można przydzielić ją na stercie przy użyciu [nowego wyrażenia \]\[](new-operator-cpp.md) . Operator zwraca wskaźnik do pierwszego elementu. Można użyć operatora indeksu dolnego ze zmienną wskaźnika tak samo jak w przypadku macierzy opartej na stosie. Można również użyć [arytmetyki wskaźnika](../c-language/pointer-arithmetic.md) , aby przenieść wskaźnik do dowolnego elementu w tablicy. Jest odpowiedzialny za zapewnienie, że:

- należy zawsze zachować kopię oryginalnego adresu wskaźnika, aby można było usunąć pamięć, gdy nie jest już potrzebna tablica.
- Nie zwiększaj ani nie zmniejszaj adresu wskaźnika poza granicami tablicy.

Poniższy przykład pokazuje, jak zdefiniować tablicę w stercie w czasie wykonywania i jak uzyskać dostęp do elementów tablicy przy użyciu operatora indeksu dolnego lub przy użyciu arytmetycznego wskaźnika:

```cpp

void do_something(size_t size)
{
    // Declare an array of doubles to be allocated on the heap
    double* numbers = new double[size]{ 0 };

    // Assign a new value to the first element
    numbers[0] = 1;

    // Assign a value to each subsequent element
    // (numbers[1] is the second element in the array.)
    for (size_t i = 1; i < size; i++)
    {
        numbers[i] = numbers[i - 1] * 1.1;
    }

    // Access each element with subscript operator
    for (size_t i = 0; i < size; i++)
    {
        std::cout << numbers[i] << " ";
    }

    // Access each element with pointer arithmetic
    // Use a copy of the pointer for iterating
    double* p = numbers;

    for (size_t i = 0; i < size; i++)
    {
        // Dereference the pointer, then increment it
        std::cout << *p++ << " ";
    }

    // Alternate method:
    // Reset p to numbers[0]:
    p = numbers;

    // Use address of pointer to compute bounds.
    // The compiler computes size as the number
    // of elements * (bytes per element).
    while (p < (numbers + size))
    {
        // Dereference the pointer, then increment it
        std::cout << *p++ << " ";
    }

    delete[] numbers; // don't forget to do this!

}
int main()
{
    do_something(108);
}

```

## <a name="initializing-arrays"></a>Inicjowanie tablic

Można zainicjować tablicę w pętli, jeden element w czasie lub w pojedynczej instrukcji. Zawartość następujących dwóch tablic jest identyczna:

```cpp
    int a[10];
    for (int i = 0; i < 10; ++i)
    {
        a[i] = i + 1;
    }

    int b[10]{ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
```

## <a name="passing-arrays-to-functions"></a>Przekazywanie tablic do funkcji

Gdy tablica jest przenoszona do funkcji, jest ona przenoszona jako wskaźnik do pierwszego elementu. Dotyczy to zarówno macierzy opartych na stosach, jak i opartych na stercie. Wskaźnik nie zawiera dodatkowego rozmiaru ani informacji o typie. Takie zachowanie jest nazywane *wskaźnikiem zanikania*. Gdy przekazujesz tablicę do funkcji, musisz zawsze określić liczbę elementów w osobnym parametrze. Takie zachowanie oznacza również, że elementy tablicy nie są kopiowane, gdy tablica jest przenoszona do funkcji. Aby zapobiec modyfikowaniu elementów przez funkcję, określ parametr jako wskaźnik do elementów **stałych** .

Poniższy przykład pokazuje funkcję, która akceptuje tablicę i długość. Wskaźnik wskazuje oryginalną tablicę, a nie kopię. Ponieważ parametr nie jest **stałą**, funkcja może modyfikować elementy tablicy.

```cpp
void process(double p*, const size_t len)
{
    std::cout << "process:\n";
    for (size_t i = 0; i < len; ++i)
    {
        // do something with p[i]
    }
}
```

Zadeklaruj tablicę jako stałą, aby uczynić ją tylko do odczytu w bloku funkcji:

```cpp
void process(const double p*, const size_t len);
```

Tę samą funkcję można także zadeklarować w taki sposób, bez zmiany w zachowaniu. Tablica jest nadal przenoszona jako wskaźnik do pierwszego elementu:

```cpp
// Unsized array
void process(const double p[] const size_t len);

// Fixed-size array. Length must still be specified explicitly.
void process(const double p[1000], const size_t len);
```

## <a name="multidimensional-arrays"></a>Tablice wielowymiarowe

Tablice zbudowane z innych tablic są tablicami wielowymiarowych. Te wielowymiarowe tablice są określane przez umieszczenie w sekwencji wielu wyrażeń stałych w nawiasach kwadratowych. Na przykład rozważmy następującą deklarację:

```cpp
int i2[5][7];
```

Określa tablicę typu **int**, koncepcyjnie ułożonej w dwuwymiarowej macierzy składającej się z pięciu wierszy i siedmiu kolumn, jak pokazano na poniższej ilustracji:

![Układ koncepcyjny tablicy&#45;wielowymiarowej](../cpp/media/vc38rc1.gif "Układ koncepcyjny tablicy&#45;wielowymiarowej") <br/>
Układ koncepcyjny macierzy wielowymiarowej

W deklaracjach tablic wielowymiarowych, które mają listę inicjatorów (zgodnie z opisem w [inicjatorach](../cpp/initializers.md)), można pominąć wyrażenie stałe określające granice dla pierwszego wymiaru. Na przykład:

```cpp
// arrays2.cpp
// compile with: /c
const int cMarkets = 4;
// Declare a float that represents the transportation costs.
double TransportCosts[][cMarkets] = {
   { 32.19, 47.29, 31.99, 19.11 },
   { 11.29, 22.49, 33.47, 17.29 },
   { 41.97, 22.09,  9.76, 22.55 }
};
```

Poprzednia deklaracja definiuje tablicę, która ma trzy wiersze o czterech kolumnach. Wiersze przedstawiają fabryki, a kolumny reprezentują rynki, do których są dostarczane fabryki. Wartości to koszty transportu od fabryk do rynków. Pierwszy wymiar tablicy jest pozostawiony, ale kompilator wypełnia go, sprawdzając inicjator.

Użycie operatora pośredniego (*) dla n-wymiarowego typu tablicy daje w wyniku tablicę n-1. Jeśli n to 1, jest wynikiem wartości skalarnej (lub elementu tablicy).

C++Tablice są przechowywane w kolejności najważniejszych wierszy. Wiersz — główne zamówienie oznacza, że ostatni indeks dolny różni się od najszybszego.

## <a name="example"></a>Przykład

Technika pomijania specyfikacji granic dla pierwszego wymiaru tablicy wielowymiarowej może być również używana w deklaracjach funkcji w następujący sposób:

```cpp
// multidimensional_arrays.cpp
// compile with: /EHsc
// arguments: 3
#include <limits>   // Includes DBL_MAX
#include <iostream>

const int cMkts = 4, cFacts = 2;

// Declare a float that represents the transportation costs
double TransportCosts[][cMkts] = {
   { 32.19, 47.29, 31.99, 19.11 },
   { 11.29, 22.49, 33.47, 17.29 },
   { 41.97, 22.09,  9.76, 22.55 }
};

// Calculate size of unspecified dimension
const int cFactories = sizeof TransportCosts /
                  sizeof( double[cMkts] );

double FindMinToMkt( int Mkt, double myTransportCosts[][cMkts], int mycFacts);

using namespace std;

int main( int argc, char *argv[] ) {
   double MinCost;

   if (argv[1] == 0) {
      cout << "You must specify the number of markets." << endl;
      exit(0);
   }
   MinCost = FindMinToMkt( *argv[1] - '0', TransportCosts, cFacts);
   cout << "The minimum cost to Market " << argv[1] << " is: "
       << MinCost << "\n";
}

double FindMinToMkt(int Mkt, double myTransportCosts[][cMkts], int mycFacts) {
   double MinCost = DBL_MAX;

   for( size_t i = 0; i < cFacts; ++i )
      MinCost = (MinCost < TransportCosts[i][Mkt]) ?
         MinCost : TransportCosts[i][Mkt];

   return MinCost;
}
```

```Output
The minimum cost to Market 3 is: 17.29
```

Funkcja `FindMinToMkt` jest zapisywana w taki sposób, że dodanie nowych fabryk nie wymaga żadnych zmian w kodzie, a dopiero ponowna kompilacja.

## <a name="initializing-arrays"></a>Inicjowanie tablic

Jeśli klasa ma Konstruktor, tablice tej klasy są inicjowane przez konstruktora. Jeśli na liście inicjatorów znajduje się mniej elementów niż elementy w tablicy, Konstruktor domyślny jest używany dla pozostałych elementów. Jeśli nie zdefiniowano domyślnego konstruktora dla klasy, lista inicjatorów musi być kompletna — to znaczy, że dla każdego elementu w tablicy musi istnieć jeden inicjator.

Rozważmy klasę `Point`, która definiuje dwa konstruktory:

```cpp
// initializing_arrays1.cpp
class Point
{
public:
   Point()   // Default constructor.
   {
   }
   Point( int, int )   // Construct from two ints
   {
   }
};

// An array of Point objects can be declared as follows:
Point aPoint[3] = {
   Point( 3, 3 )     // Use int, int constructor.
};

int main()
{
}
```

Pierwszy element `aPoint` jest konstruowany przy użyciu konstruktora `Point( int, int )`; Pozostałe dwa elementy są konstruowane przy użyciu domyślnego konstruktora.

Statyczne tablice członkowskie (bez względu na to, czy **const** lub not) mogą być inicjowane w ich definicjach (poza deklaracją klasy). Na przykład:

```cpp
// initializing_arrays2.cpp
class WindowColors
{
public:
    static const char *rgszWindowPartList[7];
};

const char *WindowColors::rgszWindowPartList[7] = {
    "Active Title Bar", "Inactive Title Bar", "Title Bar Text",
    "Menu Bar", "Menu Bar Text", "Window Background", "Frame"   };
int main()
{
}
```

## <a name="accessing-array-elements"></a>Uzyskiwanie dostępu do elementów tablicy

Dostęp do poszczególnych elementów tablicy można uzyskać za pomocą operatora indeksu dolnego (`[ ]`). Jeśli tablica Jednowymiarowa jest używana w wyrażeniu, które nie ma indeksu dolnego, nazwa tablicy zostanie przeznaczona do wskaźnika do pierwszego elementu w tablicy.

```cpp
// using_arrays.cpp
int main() {
   char chArray[10];
   char *pch = chArray;   // Evaluates to a pointer to the first element.
   char   ch = chArray[0];   // Evaluates to the value of the first element.
   ch = chArray[3];   // Evaluates to the value of the fourth element.
}
```

W przypadku korzystania z tablic wielowymiarowych można użyć różnych kombinacji w wyrażeniach.

```cpp
// using_arrays_2.cpp
// compile with: /EHsc /W1
#include <iostream>
using namespace std;
int main() {
   double multi[4][4][3];   // Declare the array.
   double (*p2multi)[3];
   double (*p1multi);

   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.
   p2multi = multi[3];               // Make p2multi point to
                                     // fourth "plane" of multi.
   p1multi = multi[3][2];            // Make p1multi point to
                                     // fourth plane, third row
                                     // of multi.
}
```

W poprzednim kodzie `multi` jest tablicą trójwymiarową typu **Double**. Wskaźnik `p2multi` wskazuje na tablicę typu o **podwójnym** rozmiarze trzech. W tym przykładzie tablica jest używana z jednym, dwoma i trzema indeksami dolnymi. Chociaż jest to bardziej powszechne, aby określić wszystkie indeksy dolne, jak w instrukcji `cout`, czasami warto wybrać konkretny podzbiór elementów tablicy, jak pokazano w instrukcjach, które obserwują `cout`.

## <a name="overloading-subscript-operator"></a>Przeciążanie operatora indeksu dolnego

Podobnie jak w przypadku innych operatorów, Operator indeksu dolnego (`[]`) może zostać ponownie zdefiniowany przez użytkownika. Domyślne zachowanie operatora indeksu dolnego (jeśli nie jest przeciążone) polega na połączeniu nazwy tablicy i indeksu dolnego przy użyciu następującej metody:

`*((array_name) + (subscript))`

Podobnie jak w przypadku wszystkich elementów, które obejmują typy wskaźników, skalowanie jest wykonywane automatycznie w celu dostosowania rozmiaru typu. W związku z tym wynikowa wartość nie jest *n* bajtami ze źródła nazwy Array-Name; Zamiast tego jest to *n*-ty element tablicy. Aby uzyskać więcej informacji na temat tej konwersji, zobacz [dodatek operatory](additive-operators-plus-and.md).

Podobnie w przypadku tablic wielowymiarowych adres jest wyprowadzany przy użyciu następującej metody:

`((array_name) + (subscript1 * max2 * max3 * ... * maxn) + (subscript2 * max3 * ... * maxn) + ... + subscriptn))`

## <a name="arrays-in-expressions"></a>Tablice w wyrażeniach

Gdy identyfikator typu tablicy pojawia się w wyrażeniu innym niż `sizeof`, adres (`&`) lub Inicjalizacja odwołania, jest konwertowany na wskaźnik do pierwszego elementu tablicy. Na przykład:

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

Wskaźnik `psz` wskazuje na pierwszy element `szError1`tablicy. Tablice, w przeciwieństwie do wskaźników, nie podlegają modyfikowaniu l-wartości. W związku z tym następujące przypisanie jest niedozwolone:

```cpp
szError1 = psz;
```

## <a name="see-also"></a>Zobacz także

[std:: Array](../standard-library/array-class-stl.md)
