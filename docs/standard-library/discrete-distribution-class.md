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
ms.openlocfilehash: 83d69df399d556025d0f7d4a8ccd714ff43a76ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368771"
---
# <a name="discrete_distribution-class"></a>discrete_distribution — Klasa

Generuje dyskretny rozkład liczby całkowitej, który ma interwały o jednolitej szerokości z jednolitym prawdopodobieństwem w każdym interwale.

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

*Typ int*\
Typ wyniku liczby całkowitej, domyślnie **int**. Możliwe typy można znaleźć w [ \<>losowych ](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Ten rozkład próbkowania ma odstępy szerokości jednolitej z jednolitym prawdopodobieństwem w każdym interwale. Aby uzyskać informacje na temat innych rozkładów próbkowania, zobacz [piecewise_linear_distribution klasa i](../standard-library/piecewise-linear-distribution-class.md) klasa [piecewise_constant_distribution](../standard-library/piecewise-constant-distribution-class.md).

Poniższa tabela zawiera łącza do artykułów o poszczególnych członkach:

|||
|-|-|
|[discrete_distribution](#discrete_distribution)|`discrete_distribution::param`|
|`discrete_distribution::operator()`|[param_type](#param_type)|

Funkcja `vector<double> probabilities()` właściwości zwraca indywidualne prawdopodobieństwa dla każdej wygenerowanej liczby całkowitej.

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

**Nagłówek:** \<losowe>

**Przestrzeń nazw:** std

## <a name="discrete_distributiondiscrete_distribution"></a><a name="discrete_distribution"></a>discrete_distribution::discrete_distribution

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

*pierwszyW*\
Pierwszy iterator na liście, z którego można skonstruować dystrybucję.

*lastW*\
Ostatni iterator na liście, z którego można skonstruować dystrybucję (niewli włącznie, ponieważ iteratory używają pustego elementu na końcu).

*lista wag*\
[initializer_list,](../cpp/initializers.md) z którego można skonstruować dystrybucję.

*Liczba*\
Liczba elementów w zakresie dystrybucji. Jeśli `count==0`, odpowiednik domyślnego konstruktora (zawsze generuje zero).

*Niskie*\
Najniższa wartość w zakresie dystrybucji.

*Wysokiej*\
Najwyższa wartość w zakresie dystrybucji.

*wagafunc*\
Obiekt reprezentujący funkcję prawdopodobieństwa dla rozkładu. Zarówno parametr, jak i zwracana wartość muszą być konwertowane na **podwójną**.

*Parm*\
Struktura `param_type` używana do konstruowania dystrybucji.

### <a name="remarks"></a>Uwagi

Domyślny konstruktor konstruuje obiekt, którego wartość przechowywane prawdopodobieństwo ma jeden element o wartości 1. Spowoduje to dystrybucji, która zawsze generuje zero.

Konstruktor zakresu iteratora, który ma parametry *firstW* i *lastW* konstruuje obiekt rozkładu przy użyciu wartości wagi pobranych z iteratorów w sekwencji interwałów [*firstW*, *lastW*).

Konstruktor listy inicjatorów, który ma parametr *listy wagowej,* konstruuje obiekt rozkładu z wagami z *listy wagowej*listy inicjatorów .

Konstruktor, który ma *count*, *low*, *high*, i *weightfunc* parametry konstruuje obiekt rozkładu zainicjowany na podstawie tych reguł:

- Jeśli *count* < 1, **n** = 1 i jako takie jest odpowiednikiem domyślnego konstruktora, zawsze generowania zero.
- Jeśli *liczba* > 0, **n** = *count*. Pod **warunkiem, że d** = (*wysoki* - *niski)*/ **n** jest większy od zera, przy użyciu **d** jednolitych podzakładów, każda waga jest przypisana w następujący sposób: `weight[k] = weightfunc(x)`, gdzie **x** = *niskie* + **k** * **d** + **d** / 2, dla **k** = 0, ..., **n** - 1.

Konstruktor, który `param_type` ma parametr *parm* konstruuje obiekt dystrybucji przy użyciu *parm* jako przechowywanej struktury parametrów.

## <a name="discrete_distributionparam_type"></a><a name="param_type"></a>discrete_distribution::param_type

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

*pierwszyW*\
Pierwszy iterator na liście, z którego można skonstruować dystrybucję.

*lastW*\
Ostatni iterator na liście, z którego można skonstruować dystrybucję (niewli włącznie, ponieważ iteratory używają pustego elementu na końcu).

*lista wag*\
[initializer_list,](../cpp/initializers.md) z którego można skonstruować dystrybucję.

*Liczba*\
Liczba elementów w zakresie dystrybucji. Jeśli *liczba* wynosi 0, jest to równoważne domyślnego konstruktora (zawsze generuje zero).

*Niskie*\
Najniższa wartość w zakresie dystrybucji.

*Wysokiej*\
Najwyższa wartość w zakresie dystrybucji.

*wagafunc*\
Obiekt reprezentujący funkcję prawdopodobieństwa dla rozkładu. Zarówno parametr, jak i zwracana wartość muszą być konwertowane na **podwójną**.

*Prawo*\
Obiekt `param_type` do porównania z tym.

### <a name="remarks"></a>Uwagi

Ten pakiet parametrów `operator()` można przekazać do generowania wartości zwracanej.

## <a name="see-also"></a>Zobacz też

[\<losowe>](../standard-library/random.md)
