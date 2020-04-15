---
title: negative_binomial_distribution — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::negative_binomial_distribution
- random/std::negative_binomial_distribution::reset
- random/std::negative_binomial_distribution::k
- random/std::negative_binomial_distribution::p
- random/std::negative_binomial_distribution::param
- random/std::negative_binomial_distribution::min
- random/std::negative_binomial_distribution::max
- random/std::negative_binomial_distribution::operator()
- random/std::negative_binomial_distribution::param_type
- random/std::negative_binomial_distribution::param_type::k
- random/std::negative_binomial_distribution::param_type::p
- random/std::negative_binomial_distribution::param_type::operator==
- random/std::negative_binomial_distribution::param_type::operator!=
helpviewer_keywords:
- std::negative_binomial_distribution [C++]
- std::negative_binomial_distribution [C++], reset
- std::negative_binomial_distribution [C++], k
- std::negative_binomial_distribution [C++], p
- std::negative_binomial_distribution [C++], param
- std::negative_binomial_distribution [C++], min
- std::negative_binomial_distribution [C++], max
- std::negative_binomial_distribution [C++], param_type
- std::negative_binomial_distribution [C++], param_type
ms.assetid: 7f5f0967-7fdd-4578-99d4-88f292b4fe9c
ms.openlocfilehash: 940ea790e724ffacdefe2cefb256a3314ba244e3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367964"
---
# <a name="negative_binomial_distribution-class"></a>negative_binomial_distribution — Klasa

Generuje ujemny rozkład dwumianowy.

## <a name="syntax"></a>Składnia

```
template<class IntType = int>
class negative_binomial_distribution
{
public:
    // types
    typedef IntType result_type;
    struct param_type;

    // constructor and reset functions
    explicit negative_binomial_distribution(result_type k = 1, double p = 0.5);
    explicit negative_binomial_distribution(const param_type& parm);
    void reset();

    // generating functions
    template `<`class URNG>
    result_type operator()(URNG& gen);
    template `<`class URNG>
    result_type operator()(URNG& gen, const param_type& parm);

    // property functions
    result_type k() const;
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

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje rozkład, który tworzy wartości typu całkowitego określonego przez użytkownika lub wpisz **int,** jeśli nie jest dostarczany, rozłożone zgodnie z ujemną rozkładem dwumianowym dyskretną funkcją prawdopodobieństwa. W poniższej tabeli znajdują się łącza do artykułów dotyczących poszczególnych członków.

||||
|-|-|-|
|[negative_binomial_distribution](#negative_binomial_distribution)|`negative_binomial_distribution::k`|`negative_binomial_distribution::param`|
|`negative_binomial_distribution::operator()`|`negative_binomial_distribution::p`|[param_type](#param_type)|

Elementy członkowskie `k()` `p()` właściwości i zwraca aktualnie przechowywane wartości parametrów dystrybucji *k* i *p* odpowiednio.

Element członkowski `param()` właściwości `param_type` ustawia lub zwraca pakiet parametrów przechowywanej dystrybucji.

`min()` Funkcje `max()` i element członkowski zwracają odpowiednio najmniejszy możliwy wynik i największy możliwy wynik.

Funkcja `reset()` elementu członkowskiego odrzuca wszystkie buforowane wartości, dzięki czemu `operator()` wynik następnego wywołania nie zależy od żadnych wartości uzyskanych z aparatu przed wywołaniem.

Funkcje `operator()` członkowskie zwracają następną wygenerowaną wartość na podstawie aparatu URNG, z bieżącego pakietu parametrów lub określonego pakietu parametrów.

Aby uzyskać więcej informacji na temat klas dystrybucji i ich członków, zobacz [ \<losowe>](../standard-library/random.md).

Aby uzyskać szczegółowe informacje na temat ujemnej funkcji rozkładu dwumianowego dyskretnego prawdopodobieństwa, zobacz artykuł Wolfram MathWorld [Ujemny rozkład dwumianowy](https://go.microsoft.com/fwlink/p/?linkid=400516).

## <a name="example"></a>Przykład

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const int k, const double p, const int& s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::negative_binomial_distribution<> distr(k, p);

    std::cout << std::endl;
    std::cout << "k == " << distr.k() << std::endl;
    std::cout << "p == " << distr.p() << std::endl;

    // generate the distribution as a histogram
    std::map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Histogram for " << s << " samples:" << std::endl;
    for (const auto& elem : histogram) {
        std::cout << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    int    k_dist = 1;
    double p_dist = 0.5;
    int    samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter an integer value for k distribution (where 0 < k): ";
    std::cin >> k_dist;
    std::cout << "Enter a double value for p distribution (where 0.0 < p <= 1.0): ";
    std::cin >> p_dist;
    std::cout << "Enter an integer value for a sample count: ";
    std::cin >> samples;

    test(k_dist, p_dist, samples);
}
```

Pierwszy bieg:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for k distribution (where 0 `<` k): 1
Enter a double value for p distribution (where 0.0 `<`p `<`= 1.0): .5
Enter an integer value for a sample count: 100

k == 1
p == 0.5
Histogram for 100 samples:
    0 :::::::::::::::::::::::::::::::::::::::::::
    1 ::::::::::::::::::::::::::::::::
    2 ::::::::::::
    3 :::::::
    4 ::::
    5 ::
```

Drugi bieg:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for k distribution (where 0 `<` k): 100
Enter a double value for p distribution (where 0.0 `<` p <= 1.0): .667
Enter an integer value for a sample count: 100

k == 100
p == 0.667
Histogram for 100 samples:
    31 ::
    32 :
    33 ::
    34 :
    35 ::
    37 ::
    38 :
    39 :
    40 ::
    41 :::
    42 :::
    43 :::::
    44 :::::
    45 ::::
    46 ::::::
    47 ::::::::
    48 :::
    49 :::
    50 :::::::::
    51 :::::::
    52 ::
    53 :::
    54 :::::
    56 ::::
    58 :
    59 :::::
    60 ::
    61 :
    62 ::
    64 :
    69 ::::
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowe>

**Przestrzeń nazw:** std

## <a name="negative_binomial_distributionnegative_binomial_distribution"></a><a name="negative_binomial_distribution"></a>negative_binomial_distribution::negative_binomial_distribution

Konstruuje dystrybucję.

```cpp
explicit negative_binomial_distribution(result_type k = 1, double p = 0.5);
explicit negative_binomial_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*K*\
Parametr `k` rozkładu.

*P*\
Parametr `p` rozkładu.

*Parm*\
Struktura parametrów używana do konstruowania rozkładu.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `0.0 < k` i`0.0 < p ≤ 1.0`

Pierwszy konstruktor konstruuje `p` obiekt, którego przechowywana `k` wartość zawiera wartość *p* i której przechowywana wartość posiada wartość *k*.

Drugi konstruktor tworzy obiekt, którego przechowywane parametry są inicjowane z *parm*. Można uzyskać i ustawić bieżące parametry istniejącej `param()` dystrybucji, wywołując funkcję elementu członkowskiego.

## <a name="negative_binomial_distributionparam_type"></a><a name="param_type"></a>negative_binomial_distribution::param_type

Przechowuje parametry dystrybucji.

param_type struktury { typedef negative_binomial_distribution`<`result_type> distribution_type; param_type(result_type k = 1, double p = 0,5); result_type k() const; double p() const;

   bool operator==(const param_type& right) const; bool operator!=(const param_type& right) const; };

### <a name="parameters"></a>Parametry

*K*\
Parametr `k` rozkładu.

*P*\
Parametr `p` rozkładu.

*Prawo*\
Struktura `param_type` używana do porównania.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `0.0 < k` i`0.0 < p ≤ 1.0`

Ta struktura może być przekazywana do konstruktora klasy `param()` dystrybucji w wystąpieniu, do funkcji elementu `operator()` członkowskiego, aby ustawić przechowywane parametry istniejącej dystrybucji i do użycia zamiast przechowywanych parametrów.

## <a name="see-also"></a>Zobacz też

[\<losowe>](../standard-library/random.md)
