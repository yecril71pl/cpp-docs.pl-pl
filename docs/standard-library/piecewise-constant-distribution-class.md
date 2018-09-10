---
title: piecewise_constant_distribution — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::piecewise_constant_distribution
- random/std::piecewise_constant_distribution::reset
- random/std::piecewise_constant_distribution::intervals
- random/std::piecewise_constant_distribution::densities
- random/std::piecewise_constant_distribution::param
- random/std::piecewise_constant_distribution::min
- random/std::piecewise_constant_distribution::max
- random/std::piecewise_constant_distribution::operator()
- random/std::piecewise_constant_distribution::param_type
- random/std::piecewise_constant_distribution::param_type::intervals
- random/std::piecewise_constant_distribution::param_type::densities
- random/std::piecewise_constant_distribution::param_type::operator==
- random/std::piecewise_constant_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- std::piecewise_constant_distribution [C++]
- std::piecewise_constant_distribution [C++], reset
- std::piecewise_constant_distribution [C++], intervals
- std::piecewise_constant_distribution [C++], densities
- std::piecewise_constant_distribution [C++], param
- std::piecewise_constant_distribution [C++], min
- std::piecewise_constant_distribution [C++], max
- std::piecewise_constant_distribution [C++], param_type
- std::piecewise_constant_distribution [C++], param_type
ms.assetid: 2c9a21fa-623e-4d63-b827-3f1556b6dedb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c2b4c93604a95b4c2d73c69a834ab6724bd9193
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103948"
---
# <a name="piecewiseconstantdistribution-class"></a>piecewise_constant_distribution — Klasa

Generuje rozkład elementowy stałej dystrybucji, która ma szerokość zróżnicowanie odstępach czasu, za pomocą jednolitego prawdopodobieństwo w każdym interwale.

## <a name="syntax"></a>Składnia

```cpp
template<class RealType = double>
class piecewise_constant_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructor and reset functions
   piecewise_constant_distribution();
   template <class InputIteratorI, class InputIteratorW>
   piecewise_constant_distribution(
       InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);
   template <class UnaryOperation>
   piecewise_constant_distribution(
      initializer_list<result_type> intervals, UnaryOperation weightfunc);
   template <class UnaryOperation>
   piecewise_constant_distribution(
      size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   explicit piecewise_constant_distribution(const param_type& parm);
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

*RealType*<br/>
Zmiennoprzecinkowy typu wyniku, wartość domyślna to **double**. Aby możliwych typów, zobacz [ \<losowy >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Tej dystrybucji próbkowania ma szerokość zróżnicowanie odstępach czasu, za pomocą jednolitego prawdopodobieństwo w każdym interwale. Aby uzyskać informacji na temat innych dystrybucji próbkowania, zobacz [piecewise_linear_distribution, klasa](../standard-library/piecewise-linear-distribution-class.md) i [discrete_distribution —](../standard-library/discrete-distribution-class.md).

Poniższa tabela zawiera linki do artykułów na temat poszczególnych elementów członkowskich:

||||
|-|-|-|
|[piecewise_constant_distribution](#piecewise_constant_distribution)|`piecewise_constant_distribution::intervals`|`piecewise_constant_distribution::param`|
|`piecewise_constant_distribution::operator()`|`piecewise_constant_distribution::densities`|[param_type](#param_type)|

Funkcja właściwości `intervals()` zwraca `vector<result_type>` za pomocą zestawu interwałów przechowywanych dystrybucji.

Funkcja właściwości `densities()` zwraca `vector<result_type>` przy użyciu przechowywanych gęstości dla każdego zestawu interwał, które są obliczane zgodnie z określonymi wagami parametry konstruktora.

Właściwość elementu członkowskiego `param()` Ustawia lub zwraca `param_type` pakiet parametrów przechowywanych dystrybucji.

`min()` i `max()` funkcje Członkowskie zwracają najmniejsza możliwa wynik i największych możliwych wyników, odpowiednio.

`reset()` Funkcja elementu członkowskiego odrzuca wszystkie wartości z pamięci podręcznej, tak aby wynik następnego wywołania metody `operator()` nie zależy od żadnych wartości uzyskane z aparatu przed wywołaniem.

`operator()` Funkcje Członkowskie zwracają dalej wygenerowaną wartość opartą na aparacie URNG, z bieżącego pakietu parametrów lub pakietu określony parametr.

Aby uzyskać więcej informacji o dystrybucji klasy i składowe, zobacz [ \<losowy >](../standard-library/random.md).

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
    vector<double> weights{ 1, 5, 10 };

    piecewise_constant_distribution<double> distr(intervals.begin(), intervals.end(), weights.begin());

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
        cout << setw(5) << elem.first << '-' << elem.first+1 << ' ' << string(elem.second, ':') << endl;
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
          0:   0.0625000000
          1:   0.0625000000
          2:   0.0694444444
Distribution for 100 samples:
    0-1 :::::::
    1-2 ::::::
    2-3 :::::
    3-4 ::::::
    4-5 :::::::
    5-6 ::::::
    6-7 :::
    7-8 ::::::::::
    8-9 ::::::
    9-10 ::::::::::::
    10-11 :::::
    11-12 ::::::
    12-13 :::::::::
    13-14 ::::
    14-15 ::::::::
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowy >

**Namespace:** standardowe

## <a name="piecewise_constant_distribution"></a>  piecewise_constant_distribution::piecewise_constant_distribution

Tworzy rozkład.

```cpp
// default constructor
piecewise_constant_distribution();

// constructs using a range of intervals, [firstI, lastI), with
// matching weights starting at firstW
template <class InputIteratorI, class InputIteratorW>
piecewise_constant_distribution(InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);

// constructs using an initializer list for range of intervals,
// with weights generated by function weightfunc
template <class UnaryOperation>
piecewise_constant_distribution(initializer_list<RealType>
intervals, UnaryOperation weightfunc);

// constructs using an initializer list for range of count intervals,
// distributed uniformly over [xmin,xmax] with weights generated by function weightfunc
template <class UnaryOperation>
piecewise_constant_distribution(size_t count, RealType xmin, RealType xmax, UnaryOperation weightfunc);

// constructs from an existing param_type structure
explicit piecewise_constant_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*firstI*<br/>
Iterator danych wejściowych do pierwszego elementu w zakresie dystrybucji.

*lastI*<br/>
Iterator danych wejściowych do ostatniego elementu w zakresie dystrybucji.

*firstW*<br/>
Iterator danych wejściowych do pierwszego elementu w zakresie wagi.

*intervals*<br/>
[Initializer_list](../cpp/initializers.md) z interwałami dystrybucji.

*Liczba*<br/>
Liczba elementów w zakresie dystrybucji.

*xmin*<br/>
Najniższa wartość z zakresu dystrybucji.

*xmax*<br/>
Najwyższą wartość w zakresie dystrybucji. Musi być większa niż *wartości xmin*.

*weightfunc*<br/>
Obiekt reprezentujący prawdopodobieństwa rozkładu. Zarówno parametr i wartość zwracana wartość musi być konwertowany na **double**.

*parm*<br/>
Struktura parametr, używane do konstruowania dystrybucji.

### <a name="remarks"></a>Uwagi

Domyślny konstruktor ustawia przechowywanych parametrów w taki sposób, że istnieje jeden interwał, od 0 do 1, 1 gęstości prawdopodobieństwa.

Konstruktor zakresu iteratora
```cpp
template <class InputIteratorI, class InputIteratorW>
piecewise_constant_distribution(InputIteratorI firstI, InputIteratorI lastI,
    InputIteratorW firstW);
```

Tworzy obiekt dystrybucji z itnervals z iteratorami za pośrednictwem sekwencji [ `firstI`, `lastI`) i odpowiadający mu wagi, zaczynając od sekwencji `firstW`.

Konstruktor listy inicjatora
```cpp
template <class UnaryOperation>
piecewise_constant_distribution(initializer_list<result_type>
intervals,
    UnaryOperation weightfunc);
```

Tworzy obiekt dystrybucji z interwałami na liście inicjatora *interwałów* i wagi generowane przez funkcję *weightfunc*.

Konstruktor zdefiniowany jako
```cpp
template <class UnaryOperation>
piecewise_constant_distribution(size_t count, result_type xmin, result_type xmax,
    UnaryOperation weightfunc);
```

Tworzy obiekt dystrybucji przy użyciu *liczba* interwały są dystrybuowane równomiernie ponad [ `xmin,xmax`], przypisując każdego interwału przeprowadzi zgodnie z funkcji *weightfunc*, i  *weightfunc* musi zaakceptować jeden parametr i mieć zwracanej wartości, które są konwertowane do `double`. **Warunek wstępny:** `xmin < xmax`

Konstruktor zdefiniowany jako
```cpp
explicit piecewise_constant_distribution(const param_type& parm);
```

Tworzy obiekt dystrybucji przy użyciu *parametr* struktury parametrów przechowywanych.

## <a name="param_type"></a>  piecewise_constant_distribution::param_type

Przechowuje wszystkie parametry dystrybucji.

```cpp
struct param_type {
   typedef piecewise_constant_distribution<result_type> distribution_type;
   param_type();
   template <class IterI, class IterW>
   param_type(IterI firstI, IterI lastI, IterW firstW);
   template <class UnaryOperation>
   param_type(size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   std::vector<result_type> densities() const;
   std::vector<result_type> intervals() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

Zobacz parametry konstruktora, aby [piecewise_constant_distribution —](#piecewise_constant_distribution).

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `xmin < xmax`

Ta struktura może być przekazywany do konstruktora klasy dystrybucji przy konkretyzacji, do `param()` funkcję elementu członkowskiego, aby ustawić przechowywanych parametrów istniejącego dystrybucji oraz do `operator()` ma być używany zamiast przechowywanych parametrów.

## <a name="see-also"></a>Zobacz także

[\<losowy >](../standard-library/random.md)<br/>
[piecewise_linear_distribution](../standard-library/piecewise-linear-distribution-class.md)<br/>
