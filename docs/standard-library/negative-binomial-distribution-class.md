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
ms.openlocfilehash: d8e71b351d88a1c4dee61f88c18aec513d776cd3
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689254"
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

*IntType* \
Typ wyniku liczby całkowitej, wartość domyślna to **int**. W przypadku możliwych typów zobacz [\<random >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje dystrybucję, która produkuje wartości typu całkowitego określonego przez użytkownika, lub typ **int** , jeśli nie jest podany, dystrybuowany zgodnie z ujemną funkcją prawdopodobieństwa rozkład dwumianowy. Poniższa tabela zawiera linki do artykułów na temat poszczególnych członków.

||||
|-|-|-|
|[negative_binomial_distribution](#negative_binomial_distribution)|`negative_binomial_distribution::k`|`negative_binomial_distribution::param`|
|`negative_binomial_distribution::operator()`|`negative_binomial_distribution::p`|[param_type](#param_type)|

Elementy członkowskie właściwości `k()` i `p()` zwracają aktualnie przechowywane wartości parametrów dystrybucji *k* i *p* .

Element członkowski właściwości `param()` ustawia lub zwraca `param_type` przechowywany pakiet parametrów dystrybucji.

Funkcje członkowskie `min()` i `max()` zwracają najmniejszy możliwy wynik i największy możliwy wynik.

Funkcja członkowska `reset()` odrzuca wszystkie wartości pamięci podręcznej, dzięki czemu wynik następnego wywołania do `operator()` nie zależy od wartości uzyskanych z aparatu przed wywołaniem.

Funkcje składowe `operator()` zwracają następną wygenerowaną wartość opartą na aparacie URNG, z bieżącego pakietu parametrów lub z określonym pakietem parametrów.

Aby uzyskać więcej informacji na temat klas dystrybucji i ich członków, zobacz [\<random >](../standard-library/random.md).

Aby uzyskać szczegółowe informacje o ujemnej funkcji prawdopodobieństwa rozkładu dwumianowego, zobacz [rozkład dwumianowy](https://go.microsoft.com/fwlink/p/?linkid=400516)Wolfram MathWorld.

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

Pierwsze uruchomienie:

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

Drugi przebieg:

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

**Nagłówek:** \<random >

**Przestrzeń nazw:** std

## <a name="negative_binomial_distribution"></a>negative_binomial_distribution::negative_binomial_distribution

Konstruuje dystrybucję.

```cpp
explicit negative_binomial_distribution(result_type k = 1, double p = 0.5);
explicit negative_binomial_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

\ *k*
@No__t_0 parametr dystrybucji.

*p* \
@No__t_0 parametr dystrybucji.

*parametr* \
Struktura parametru używana do konstruowania rozkładu.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `0.0 < k` i `0.0 < p ≤ 1.0`

Pierwszy Konstruktor konstruuje obiekt, którego składowana `p` wartość utrzymuje wartość *p* i której przechowywana `k` wartość przechowuje wartość *k*.

Drugi Konstruktor konstruuje obiekt, którego przechowywane parametry są inicjowane z *parametr*. Możesz uzyskać i ustawić bieżące parametry istniejącej dystrybucji, wywołując funkcję elementu członkowskiego `param()`.

## <a name="param_type"></a>negative_binomial_distribution::p aram_type

Przechowuje parametry dystrybucji.

struct param_type {typedef negative_binomial_distribution `<`result_type > distribution_type; param_type (result_type k = 1, Double p = 0,5); result_type k () const; Double p () const;

   operator logiczny = = (const param_type & Right) const; operator logiczny! = (const param_type & Right) const; };

### <a name="parameters"></a>Parametry

\ *k*
@No__t_0 parametr dystrybucji.

*p* \
@No__t_0 parametr dystrybucji.

*prawa* \
Struktura `param_type` używana do porównywania.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `0.0 < k` i `0.0 < p ≤ 1.0`

Tę strukturę można przesłać do konstruktora klasy dystrybucji podczas tworzenia wystąpienia, do funkcji składowej `param()`, aby ustawić przechowywane parametry istniejącej dystrybucji i `operator()` do użycia zamiast przechowywanych parametrów.

## <a name="see-also"></a>Zobacz także

[\<random >](../standard-library/random.md)
