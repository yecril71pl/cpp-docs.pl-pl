---
title: piecewise_linear_distribution — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::piecewise_linear_distribution
- random/std::piecewise_linear_distribution::reset
- random/std::piecewise_linear_distribution::intervals
- random/std::piecewise_linear_distribution::densities
- random/std::piecewise_linear_distribution::param
- random/std::piecewise_linear_distribution::min
- random/std::piecewise_linear_distribution::max
- random/std::piecewise_linear_distribution::operator()
- random/std::piecewise_linear_distribution::param_type
- random/std::piecewise_linear_distribution::param_type::intervals
- random/std::piecewise_linear_distribution::param_type::densities
- random/std::piecewise_linear_distribution::param_type::operator==
- random/std::piecewise_linear_distribution::param_type::operator!=
helpviewer_keywords:
- std::piecewise_linear_distribution [C++]
- std::piecewise_linear_distribution [C++], reset
- std::piecewise_linear_distribution [C++], intervals
- std::piecewise_linear_distribution [C++], densities
- std::piecewise_linear_distribution [C++], param
- std::piecewise_linear_distribution [C++], min
- std::piecewise_linear_distribution [C++], max
- std::piecewise_linear_distribution [C++], param_type
- std::piecewise_linear_distribution [C++], param_type
ms.assetid: cd141152-7163-4754-8f98-c6d6500005e0
ms.openlocfilehash: 7d9e1f1b9af3002faa9e2d9b20b7ee76dce35aea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372084"
---
# <a name="piecewise_linear_distribution-class"></a>piecewise_linear_distribution — Klasa

Generuje rozkład liniowy fragmentarycznie, który ma różne interwały szerokości z liniowo zmiennym prawdopodobieństwem w każdym interwale.

## <a name="syntax"></a>Składnia

```cpp
template<class RealType = double>
class piecewise_linear_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructor and reset functions
   piecewise_linear_distribution();
   template <class InputIteratorI, class InputIteratorW>
   piecewise_linear_distribution(
      InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);
   template <class UnaryOperation>
   piecewise_linear_distribution(
      initializer_list<result_type> intervals, UnaryOperation weightfunc);
   template <class UnaryOperation>
   piecewise_linear_distribution(
      size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   explicit piecewise_linear_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   vector<result_type> intervals() const;
   vector<result_type> densities() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parametry

*Typ rzeczywisty*\
Typ wyniku zmiennoprzecinkowego, domyślnie **podwoić**. Możliwe typy można znaleźć w [ \<>losowych ](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Ten rozkład próbkowania ma różne odstępy szerokości z liniowo zmiennym prawdopodobieństwem w każdym interwale. Aby uzyskać informacje na temat innych rozkładów próbek, zobacz [piecewise_linear_distribution](../standard-library/piecewise-constant-distribution-class.md) i [discrete_distribution](../standard-library/discrete-distribution-class.md).

Poniższa tabela zawiera łącza do artykułów o poszczególnych członkach:

||||
|-|-|-|
|[piecewise_linear_distribution](#piecewise_linear_distribution)|`piecewise_linear_distribution::intervals`|`piecewise_linear_distribution::param`|
|`piecewise_linear_distribution::operator()`|`piecewise_linear_distribution::densities`|[param_type](#param_type)|

Funkcja `intervals()` właściwości zwraca `vector<result_type>` z zestawem przechowywanych interwałów rozkładu.

Funkcja `densities()` właściwości zwraca `vector<result_type>` z przechowywanych gęstości dla każdego zestawu interwałów, które są obliczane zgodnie z wagami podanymi w parametrach konstruktora.

Element członkowski `param()` właściwości `param_type` ustawia lub zwraca pakiet parametrów przechowywanej dystrybucji.

`min()` Funkcje `max()` i element członkowski zwracają odpowiednio najmniejszy możliwy wynik i największy możliwy wynik.

Funkcja `reset()` elementu członkowskiego odrzuca wszystkie buforowane wartości, dzięki czemu `operator()` wynik następnego wywołania nie zależy od żadnych wartości uzyskanych z aparatu przed wywołaniem.

Funkcje `operator()` członkowskie zwracają następną wygenerowaną wartość na podstawie aparatu URNG, z bieżącego pakietu parametrów lub określonego pakietu parametrów.

Aby uzyskać więcej informacji na temat klas dystrybucji i ich członków, zobacz [ \<losowe>](../standard-library/random.md).

## <a name="example"></a>Przykład

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

using namespace std;

void test(const int s) {

    // uncomment to use a non-deterministic generator
    // random_device rd;
    // mt19937 gen(rd());
    mt19937 gen(1701);

    // Three intervals, non-uniform: 0 to 1, 1 to 6, and 6 to 15
    vector<double> intervals{ 0, 1, 6, 15 };
    // weights determine the densities used by the distribution
    vector<double> weights{ 1, 5, 5, 10 };

    piecewise_linear_distribution<double> distr(intervals.begin(), intervals.end(), weights.begin());

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "intervals (index: interval):" << endl;
    vector<double> i = distr.intervals();
    int counter = 0;
    for (const auto& n : i) {
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;
        ++counter;
    }
    cout << endl;
    cout << "densities (index: density):" << endl;
    vector<double> d = distr.densities();
    counter = 0;
    for (const auto& n : d) {
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;
        ++counter;
    }
    cout << endl;

    // generate the distribution as a histogram
    map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    cout << "Distribution for " << s << " samples:" << endl;
    for (const auto& elem : histogram) {
        cout << setw(5) << elem.first << '-' << elem.first + 1 << ' ' << string(elem.second, ':') << endl;
    }
    cout << endl;
}

int main()
{
    int samples = 100;

    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;
    cout << "Enter an integer value for the sample count: ";
    cin >> samples;

    test(samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the sample count: 100
min() == 0
max() == 15
intervals (index: interval):
          0:   0.0000000000
          1:   1.0000000000
          2:   6.0000000000
          3:  15.0000000000
densities (index: density):
          0:   0.0645161290
          1:   0.3225806452
          2:   0.3225806452
          3:   0.6451612903
Distribution for 100 samples:
    0-1 :::::::::::::::::::::
    1-2 ::::::
    2-3 :::
    3-4 :::::::
    4-5 ::::::
    5-6 ::::::
    6-7 :::::
    7-8 ::::::::::
    8-9 ::::::::::
    9-10 ::::::
   10-11 ::::
   11-12 :::
   12-13 :::
   13-14 :::::
   14-15 :::::
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowe>

**Przestrzeń nazw:** std

## <a name="piecewise_linear_distributionpiecewise_linear_distribution"></a><a name="piecewise_linear_distribution"></a>piecewise_linear_distribution::piecewise_linear_distribution

Konstruuje dystrybucję.

```cpp
// default constructor
piecewise_linear_distribution();

// constructs using a range of intervals, [firstI, lastI), with
// matching weights starting at firstW
template <class InputIteratorI, class InputIteratorW>
piecewise_linear_distribution(InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);

// constructs using an initializer list for range of intervals,
// with weights generated by function weightfunc
template <class UnaryOperation>
piecewise_linear_distribution(initializer_list<RealType>
intervals, UnaryOperation weightfunc);

// constructs using an initializer list for range of count intervals,
// distributed uniformly over [xmin,xmax] with weights generated by function weightfunc
template <class UnaryOperation>
piecewise_linear_distribution(size_t count, RealType xmin, RealType xmax, UnaryOperation weightfunc);

// constructs from an existing param_type structure
explicit piecewise_linear_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*po pierwszeI*\
Iterator wejściowy pierwszego elementu w zakresie dystrybucji.

*lastI*\
Iterator wejściowy ostatniego elementu w zakresie dystrybucji.

*pierwszyW*\
Iterator wejściowy pierwszego elementu w zakresie wag.

*Odstępach czasu*\
[initializer_list](../cpp/initializers.md) z interwałami rozkładu.

*Liczba*\
Liczba elementów w zakresie dystrybucji.

*xmin (min.*\
Najniższa wartość w zakresie dystrybucji.

*Xmax*\
Najwyższa wartość w zakresie dystrybucji. Musi być większa niż *xmin*.

*wagafunc*\
Obiekt reprezentujący funkcję prawdopodobieństwa dla rozkładu. Zarówno parametr, jak i zwracana wartość muszą być konwertowane na **podwójną**.

*Parm*\
Struktura parametrów używana do konstruowania rozkładu.

### <a name="remarks"></a>Uwagi

Domyślny konstruktor ustawia przechowywane parametry w taki sposób, że istnieje jeden interwał, od 0 do 1, z gęstością prawdopodobieństwa 1.

Konstruktor zakresu iteratora

```cpp
template <class InputIteratorI, class InputIteratorW>
piecewise_linear_distribution(
    InputIteratorI firstI,
    InputIteratorI lastI,
    InputIteratorW firstW);
```

konstruuje obiekt dystrybucji z itnervals z iteratorów przez sekwencję [ `firstI`, `lastI`) i pasujące sekwencji wagi, począwszy od *firstW*.

Konstruktor listy inicjatora

```cpp
template <class UnaryOperation>
piecewise_linear_distribution(
    initializer_list<result_type> intervals,
    UnaryOperation weightfunc);
```

konstruuje obiekt rozkładu z interwałami z *interwałów* listy inicjatorów i wag generowanych z *funkcji weightfunc*.

Konstruktor zdefiniowany jako

```cpp
template <class UnaryOperation>
piecewise_linear_distribution(
    size_t count,
    result_type xmin,
    result_type xmax,
    UnaryOperation weightfunc);
```

konstruuje obiekt rozkładu z interwałami `xmin,xmax` *zliczania* rozłożonymi równomiernie nad [ ], przypisując każdy interwał wag zgodnie z *funkcją weightfunc*, a *weightfunc* musi zaakceptować jeden parametr i mieć wartość zwrotu, z których oba są konwertowane na `double`. **Warunek wstępny:**`xmin < xmax`.

Konstruktor zdefiniowany jako

```cpp
explicit piecewise_linear_distribution(const param_type& parm);
```

konstruuje obiekt dystrybucji przy użyciu *parm* jako przechowywanej struktury parametrów.

## <a name="piecewise_linear_distributionparam_type"></a><a name="param_type"></a>piecewise_linear_distribution::param_type

Przechowuje wszystkie parametry dystrybucji.

```cpp
struct param_type {
   typedef piecewise_linear_distribution<result_type> distribution_type;
   param_type();
   template <class IterI, class IterW>
   param_type(
      IterI firstI, IterI lastI, IterW firstW);
   template <class UnaryOperation>
   param_type(
      size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   std::vector<result_type> densities() const;
   std::vector<result_type> intervals() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

Zobacz parametry konstruktora [dla piecewise_linear_distribution](#piecewise_linear_distribution).

### <a name="remarks"></a>Uwagi

**Warunek wstępny:**`xmin < xmax`

Ta struktura może być przekazywana do konstruktora klasy `param()` dystrybucji w wystąpieniu, do funkcji elementu `operator()` członkowskiego, aby ustawić przechowywane parametry istniejącej dystrybucji i do użycia zamiast przechowywanych parametrów.

## <a name="see-also"></a>Zobacz też

[\<losowe>](../standard-library/random.md)
