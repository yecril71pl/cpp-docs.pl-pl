---
title: discrete_distribution — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::discrete_distribution
- random/std::discrete_distribution::reset
- random/std::discrete_distribution::probabilities
- random/std::discrete_distribution::param
- random/std::discrete_distribution::min
- random/std::discrete_distribution::max
- random/std::discrete_distribution::operator()
- random/std::discrete_distribution::param_type
- random/std::discrete_distribution::param_type::probabilities
- random/std::discrete_distribution::param_type::operator==
- random/std::discrete_distribution::param_type::operator!=
helpviewer_keywords:
- std::discrete_distribution [C++]
- std::discrete_distribution [C++], reset
- std::discrete_distribution [C++], probabilities
- std::discrete_distribution [C++], param
- std::discrete_distribution [C++], min
- std::discrete_distribution [C++], max
- std::discrete_distribution [C++], param_type
- std::discrete_distribution [C++], param_type
ms.assetid: 8c8ba8f8-c06f-4f07-b354-f53950142fcf
ms.openlocfilehash: 65d5c993efd1cb9c6dd35f11223ed39e026ed7c6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217808"
---
# <a name="discrete_distribution-class"></a>discrete_distribution — Klasa

Generuje dyskretną dystrybucję całkowitą, która ma jednolite interwały ze jednorodnym prawdopodobieństwem w każdym interwale.

## <a name="syntax"></a>Składnia

```cpp
template<class IntType = int>
class discrete_distribution
   {
public:
   // types
   typedef IntType result_type;
   struct param_type;

   // constructor and reset functions
   discrete_distribution();
   template <class InputIterator>
   discrete_distribution(InputIterator firstW, InputIterator lastW);
   discrete_distribution(initializer_list<double> weightlist);
   template <class UnaryOperation>
   discrete_distribution(size_t count, double xmin, double xmax, UnaryOperation funcweight);
   explicit discrete_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   vector<double> probabilities() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parametry

*IntType*\
Typ wyniku liczby całkowitej, wartość domyślna to **`int`** . Aby zapoznać się z możliwymi typami, zobacz [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>Uwagi

Ta dystrybucja próbkowania ma jednolite interwały ze jednorodnym prawdopodobieństwem w każdym interwale. Aby uzyskać informacje na temat innych dystrybucji próbkowania, zobacz [Piecewise_linear_distribution klasy](../standard-library/piecewise-linear-distribution-class.md) i [klasy piecewise_constant_distribution](../standard-library/piecewise-constant-distribution-class.md).

Poniższa tabela zawiera linki do artykułów na temat poszczególnych członków:

|||
|-|-|
|[discrete_distribution](#discrete_distribution)|`discrete_distribution::param`|
|`discrete_distribution::operator()`|[param_type](#param_type)|

Funkcja Property `vector<double> probabilities()` zwraca poszczególne prawdopodobieństwa dla każdej wygenerowanej liczby całkowitej.

Aby uzyskać więcej informacji na temat klas dystrybucji i ich członków, zobacz [\<random>](../standard-library/random.md) .

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

    discrete_distribution<> distr({ 1, 2, 3, 4, 5 });

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "probabilities (value: probability):" << endl;
    vector<double> p = distr.probabilities();
    int counter = 0;
    for (const auto& n : p) {
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
        cout << setw(5) << elem.first << ' ' << string(elem.second, ':') << endl;
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
max() == 4
probabilities (value: probability):
          0:   0.0666666667
          1:   0.1333333333
          2:   0.2000000000
          3:   0.2666666667
          4:   0.3333333333

Distribution for 100 samples:
    0 :::
    1 ::::::::::::::
    2 ::::::::::::::::::
    3 :::::::::::::::::::::::::::::
    4 ::::::::::::::::::::::::::::::::::::
```

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<random>

**Przestrzeń nazw:** std

## <a name="discrete_distributiondiscrete_distribution"></a><a name="discrete_distribution"></a>discrete_distribution::d iscrete_distribution

Konstruuje dystrybucję.

```cpp
// default constructor
discrete_distribution();

// construct using a range of weights, [firstW, lastW)
template <class InputIterator>
discrete_distribution(InputIterator firstW, InputIterator lastW);

// construct using an initializer list for range of weights
discrete_distribution(initializer_list<double> weightlist);

// construct using unary operation function
template <class UnaryOperation>
discrete_distribution(size_t count, double low, double high, UnaryOperation weightfunc);

// construct from an existing param_type structure
explicit discrete_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*firstW*\
Pierwszy iterator na liście, z którego ma zostać skonstruowany rozkład.

*lastW*\
Ostatni iterator na liście, z którego ma zostać skonstruowany rozkład (niewłączny, ponieważ Iteratory używają pustego elementu na końcu).

*weightlist*\
[Initializer_list](../cpp/initializers.md) , z którego ma zostać skonstruowany rozkład.

*liczbą*\
Liczba elementów w zakresie dystrybucji. Jeśli `count==0` , odpowiednik konstruktora domyślnego (zawsze generuje zero).

*małą*\
Najniższa wartość w zakresie dystrybucji.

*wysokowydajn*\
Najwyższa wartość w zakresie dystrybucji.

*weightfunc*\
Obiekt reprezentujący funkcję prawdopodobieństwa dla dystrybucji. Zarówno parametr, jak i wartość zwracana muszą być konwertowane na **`double`** .

*parametr*\
`param_type`Struktura używana do konstruowania rozkładu.

### <a name="remarks"></a>Uwagi

Konstruktor domyślny konstruuje obiekt, którego przechowywana wartość prawdopodobieństwa ma jeden element o wartości 1. Spowoduje to dystrybucję, która zawsze generuje zero.

Konstruktor zakresu iteratora, który ma parametry *firstW* i *lastW* konstruuje obiekt dystrybucji przy użyciu wartości wag pobranych z iteratorów w sekwencji interwału [*firstW*, *lastW*).

Konstruktor listy inicjatorów, który ma parametr *weightlist* konstruuje obiekt dystrybucji z odważnikami z listy inicjatorów *weightlist*.

Konstruktor, który ma parametry *Count*, *Low*, *High*i *weightfunc* , konstruuje obiekt dystrybucji zainicjowany na podstawie następujących reguł:

- Jeśli *licznik* < 1, **n** = 1, i jako taki jest równoważny z konstruktorem domyślnym, zawsze generuje zero.
- Jeśli *Liczba* > 0, **n**  =  *Count*. Podana wartość **d** =*(wysoka*  -  *niska*)/ **n** jest większa od zera, przy użyciu jednolitych podzakresów **d** , każda waga jest przypisywana w następujący sposób: `weight[k] = weightfunc(x)` , gdzie **x**  =  *niska*  +  **k**  *  **d**  +  **d** /2, dla **k** = 0,..., **n** -1.

Konstruktor, który ma `param_type` parametr *parametr* konstruuje obiekt dystrybucji przy użyciu *parametr* jako struktury przechowywanego parametru.

## <a name="discrete_distributionparam_type"></a><a name="param_type"></a>discrete_distribution::p aram_type

Przechowuje wszystkie parametry dystrybucji.

```cpp
struct param_type {
   typedef discrete_distribution<result_type> distribution_type;
   param_type();

   // construct using a range of weights, [firstW, lastW)
   template <class InputIterator>
   param_type(InputIterator firstW, InputIterator lastW);

   // construct using an initializer list for range of weights
   param_type(initializer_list<double> weightlist);

   // construct using unary operation function
   template <class UnaryOperation>
   param_type(size_t count, double low, double high, UnaryOperation weightfunc);

   std::vector<double> probabilities() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

*firstW*\
Pierwszy iterator na liście, z którego ma zostać skonstruowany rozkład.

*lastW*\
Ostatni iterator na liście, z którego ma zostać skonstruowany rozkład (niewłączny, ponieważ Iteratory używają pustego elementu na końcu).

*weightlist*\
[Initializer_list](../cpp/initializers.md) , z którego ma zostać skonstruowany rozkład.

*liczbą*\
Liczba elementów w zakresie dystrybucji. Jeśli *Liczba* jest równa 0, jest to odpowiednik domyślnego konstruktora (zawsze generuje zero).

*małą*\
Najniższa wartość w zakresie dystrybucji.

*wysokowydajn*\
Najwyższa wartość w zakresie dystrybucji.

*weightfunc*\
Obiekt reprezentujący funkcję prawdopodobieństwa dla dystrybucji. Zarówno parametr, jak i wartość zwracana muszą być konwertowane na **`double`** .

*Kliknij*\
Obiekt, który `param_type` ma zostać porównany.

### <a name="remarks"></a>Uwagi

Ten pakiet parametrów może zostać przesłany do `operator()` programu w celu wygenerowania wartości zwracanej.

## <a name="see-also"></a>Zobacz także

[\<random>](../standard-library/random.md)
