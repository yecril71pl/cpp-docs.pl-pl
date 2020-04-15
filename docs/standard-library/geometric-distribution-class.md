---
title: geometric_distribution — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::geometric_distribution
- random/std::geometric_distribution::reset
- random/std::geometric_distribution::p
- random/std::geometric_distribution::param
- random/std::geometric_distribution::min
- random/std::geometric_distribution::max
- random/std::geometric_distribution::operator()
- random/std::geometric_distribution::param_type
- random/std::geometric_distribution::param_type::p
- random/std::geometric_distribution::param_type::operator==
- random/std::geometric_distribution::param_type::operator!=
helpviewer_keywords:
- std::geometric_distribution [C++]
- std::geometric_distribution [C++], reset
- std::geometric_distribution [C++], p
- std::geometric_distribution [C++], param
- std::geometric_distribution [C++], min
- std::geometric_distribution [C++], max
- std::geometric_distribution [C++], param_type
- std::geometric_distribution [C++], param_type
ms.assetid: 38f933af-3b49-492e-9d26-b6b272a60013
ms.openlocfilehash: 44b624995ed274212a2699cb457c91dfa4530f03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370638"
---
# <a name="geometric_distribution-class"></a>geometric_distribution — Klasa

Generuje rozkład geometryczny.

## <a name="syntax"></a>Składnia

```cpp
template<class IntType = int>
class geometric_distribution {
public:
    // types
    typedef IntType result_type;
    struct param_type;

    // constructors and reset functions
    explicit geometric_distribution(double p = 0.5);
    explicit geometric_distribution(const param_type& parm);
    void reset();

    // generating functions
    template <class URNG>
    result_type operator()(URNG& gen);
    template <class URNG>
    result_type operator()(URNG& gen, const param_type& parm);

    // property functions
    double p() const;
    param_type param() const;
    void param(const param_type& parm);
    result_type min() const;
    result_type max() const;
};
```

### <a name="parameters"></a>Parametry

*Typ int*\
Typ wyniku liczby całkowitej, domyślnie **int**. Możliwe typy można znaleźć w [ \<>losowych ](../standard-library/random.md).

*Urng*\
Jednolity silnik generatora liczb losowych. Możliwe typy można znaleźć w [ \<>losowych ](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje rozkład, który tworzy wartości typu całkowitego określonego przez użytkownika z rozkładem geometrycznym. W poniższej tabeli znajdują się łącza do artykułów dotyczących poszczególnych członków.

||||
|-|-|-|
|[geometric_distribution](#geometric_distribution)|`geometric_distribution::p`|`geometric_distribution::param`|
|`geometric_distribution::operator()`||[param_type](#param_type)|

Funkcja `p()` właściwości zwraca wartość przechowywanego `p`parametru dystrybucji .

Element członkowski `param()` właściwości `param_type` ustawia lub zwraca pakiet parametrów przechowywanej dystrybucji.

`min()` Funkcje `max()` i element członkowski zwracają odpowiednio najmniejszy możliwy wynik i największy możliwy wynik.

Funkcja `reset()` elementu członkowskiego odrzuca wszystkie buforowane wartości, dzięki czemu `operator()` wynik następnego wywołania nie zależy od żadnych wartości uzyskanych z aparatu przed wywołaniem.

Funkcje `operator()` członkowskie zwracają następną wygenerowaną wartość na podstawie aparatu URNG, z bieżącego pakietu parametrów lub określonego pakietu parametrów.

Aby uzyskać więcej informacji na temat klas dystrybucji i ich członków, zobacz [ \<losowe>](../standard-library/random.md).

Aby uzyskać szczegółowe informacje na temat dystrybucji chi-kwadrat, zobacz Wolfram MathWorld artykuł [Geometryczny Rozkład](https://go.microsoft.com/fwlink/p/?linkid=400529).

## <a name="example"></a>Przykład

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double p, const int s) {

    // uncomment to use a non-deterministic generator
    //    std::random_device gen;
    std::mt19937 gen(1701);

    std::geometric_distribution<> distr(p);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "p() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.p() << std::endl;

    // generate the distribution as a histogram
    std::map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Distribution for " << s << " samples:" << std::endl;
    for (const auto& elem : histogram) {
        std::cout << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double p_dist = 0.5;

    int samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the \'p\' distribution parameter: ";
    std::cin >> p_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(p_dist, samples);
}
```

Pierwszy test:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'p' distribution parameter: .5
Enter an integer value for the sample count: 100

min() == 0
max() == 2147483647
p() == 0.5000000000
Distribution for 100 samples:
    0 :::::::::::::::::::::::::::::::::::::::::::::::::::::
    1 ::::::::::::::::::::::::::
    2 ::::::::::::
    3 ::::::
    4 ::
    5 :
```

Drugi test:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'p' distribution parameter: .1
Enter an integer value for the sample count: 100

min() == 0
max() == 2147483647
p() == 0.1000000000
Distribution for 100 samples:
    0 :::::::::
    1 :::::::::::
    2 ::::::::::
    3 :::::::
    4 :::::
    5 ::::::::
    6 :::
    7 ::::::
    8 :::::::
    9 :::::
   10 :::
   11 :::
   12 ::
   13 :
   14 :::
   15 ::
   16 :::
   17 :::
   20 :::::
   21 :
   29 :
   32 :
   35 :
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowe>

**Przestrzeń nazw:** std

## <a name="geometric_distributiongeometric_distribution"></a><a name="geometric_distribution"></a>geometric_distribution::geometric_distribution

Konstruuje dystrybucję.

```cpp
explicit geometric_distribution(double p = 0.5);
explicit geometric_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*P*\
Parametr `p` rozkładu.

*Parm*\
Struktura parametrów używana do konstruowania rozkładu.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:**`0.0 < p && p < 1.0`

Pierwszy konstruktor tworzy obiekt, `p` którego przechowywana wartość przechowuje wartość *p*.

Drugi konstruktor tworzy obiekt, którego przechowywane parametry są inicjowane z *parm*. Można uzyskać i ustawić bieżące parametry istniejącej `param()` dystrybucji, wywołując funkcję elementu członkowskiego.

## <a name="geometric_distributionparam_type"></a><a name="param_type"></a>geometric_distribution::param_type

Przechowuje parametry dystrybucji.

```cpp
struct param_type {
   typedef geometric_distribution<result_type> distribution_type;
   param_type(double p = 0.5);
   double p() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

*P*\
Parametr `p` rozkładu.

*Prawo*\
Wystąpienie, `param_type` aby porównać to do.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:**`0.0 < p && p < 1.0`

Ta struktura może być przekazywana do konstruktora klasy `param()` dystrybucji w wystąpieniu, do funkcji elementu `operator()` członkowskiego, aby ustawić przechowywane parametry istniejącej dystrybucji i do użycia zamiast przechowywanych parametrów.

## <a name="see-also"></a>Zobacz też

[\<losowe>](../standard-library/random.md)
