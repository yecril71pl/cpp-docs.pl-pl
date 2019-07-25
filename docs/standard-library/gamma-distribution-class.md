---
title: gamma_distribution — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::gamma_distribution
- random/std::gamma_distribution::reset
- random/std::gamma_distribution::alpha
- random/std::gamma_distribution::beta
- random/std::gamma_distribution::param
- random/std::gamma_distribution::min
- random/std::gamma_distribution::max
- random/std::gamma_distribution::operator()
- random/std::gamma_distribution::param_type
- random/std::gamma_distribution::param_type::alpha
- random/std::gamma_distribution::param_type::beta
- random/std::gamma_distribution::param_type::operator==
- random/std::gamma_distribution::param_type::operator!=
helpviewer_keywords:
- std::gamma_distribution [C++]
- std::gamma_distribution [C++], reset
- std::gamma_distribution [C++], alpha
- std::gamma_distribution [C++], beta
- std::gamma_distribution [C++], param
- std::gamma_distribution [C++], min
- std::gamma_distribution [C++], max
- std::gamma_distribution [C++], param_type
- std::gamma_distribution [C++], param_type
ms.assetid: 2a6798ac-6152-41d7-8ef6-d684d92f1572
ms.openlocfilehash: ac6a82cc7f342f6a96b5f79f36b23d23a1d27097
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453937"
---
# <a name="gammadistribution-class"></a>gamma_distribution — Klasa

Generuje rozkład gamma.

## <a name="syntax"></a>Składnia

```cpp
template<class RealType = double>
class gamma_distribution {
public:
    // types
    typedef RealType result_type;
    struct param_type;

    // constructors and reset functions
    explicit gamma_distribution(result_type alpha = 1.0, result_type beta = 1.0);
    explicit gamma_distribution(const param_type& parm);
    void reset();

    // generating functions
    template <class URNG>
    result_type operator()(URNG& gen);
    template <class URNG>
    result_type operator()(URNG& gen, const param_type& parm);

    // property functions
    result_type alpha() const;
    result_type beta() const;
    param_type param() const;
    void param(const param_type& parm);
    result_type min() const;
    result_type max() const;
};
```

### <a name="parameters"></a>Parametry

*Liczba rzeczywista*\
Typ wyniku zmiennoprzecinkowego, wartość domyślna to **Double**. W przypadku możliwych typów zobacz [ \<losowe >](../standard-library/random.md).

*URNG*\
Jednolity aparat generatora liczb losowych. W przypadku możliwych typów zobacz [ \<losowe >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dystrybucję, która produkuje wartości typu zmiennoprzecinkowego określonego przez użytkownika, lub typ **Double** , jeśli nie jest podany, dystrybuowany zgodnie z rozkładem gamma. Poniższa tabela zawiera linki do artykułów na temat poszczególnych członków.

||||
|-|-|-|
|[gamma_distribution](#gamma_distribution)|`gamma_distribution::alpha`|`gamma_distribution::param`|
|`gamma_distribution::operator()`|`gamma_distribution::beta`|[param_type](#param_type)|

Funkcja `alpha()` właściwości i `beta()` zwracają odpowiednie wartości dla przechowywanych parametrów dystrybucji *Alpha* i *beta*.

Element członkowski `param()` właściwości ustawia lub `param_type` zwraca przechowywany pakiet parametrów dystrybucji.

`min()` I`max()` funkcje członkowskie zwracają najmniejszy możliwy wynik i największy możliwy wynik.

Funkcja członkowska odrzuca wszystkie wartości pamięci podręcznej, dzięki czemu wynik następnego wywołania do `operator()` nie zależy od wartości uzyskanych z aparatu przed wywołaniem. `reset()`

Funkcje `operator()` Członkowskie zwracają następną wygenerowaną wartość opartą na aparacie URNG, z bieżącego pakietu parametrów lub z określonym pakietem parametrów.

Aby uzyskać więcej informacji na temat klas dystrybucji i ich członków, zobacz [ \<Random >](../standard-library/random.md).

Aby uzyskać szczegółowe informacje o dystrybucji gamma, zobacz [rozkład gamma](https://go.microsoft.com/fwlink/p/?linkid=401111)artykułu Wolfram MathWorld.

## <a name="example"></a>Przykład

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double a, const double b, const int s) {

    // uncomment to use a non-deterministic generator
    //    std::random_device gen;

    std::mt19937 gen(1701);

    std::gamma_distribution<> distr(a, b);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "alpha() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.alpha() << std::endl;
    std::cout << "beta() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.beta() << std::endl;

    // generate the distribution as a histogram
    std::map<double, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Distribution for " << s << " samples:" << std::endl;
    int counter = 0;
    for (const auto& elem : histogram) {
        std::cout << std::fixed << std::setw(11) << ++counter << ": "
            << std::setw(14) << std::setprecision(10) << elem.first << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double a_dist = 0.0;
    double b_dist = 1;

    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the 'alpha' distribution parameter (must be greater than zero): ";
    std::cin >> a_dist;
    std::cout << "Enter a floating point value for the 'beta' distribution parameter (must be greater than zero): ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'alpha' distribution parameter (must be greater than zero): 1
Enter a floating point value for the 'beta' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == 4.94066e-324
max() == 1.79769e+308
alpha() == 1.0000000000
beta() == 1.0000000000
Distribution for 10 samples:
    1: 0.0936880533
    2: 0.1225944894
    3: 0.6443593183
    4: 0.6551171649
    5: 0.7313457551
    6: 0.7313557977
    7: 0.7590097389
    8: 1.4466885214
    9: 1.6434088411
    10: 2.1201210996
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowe >

**Przestrzeń nazw:** std

## <a name="gamma_distribution"></a>gamma_distribution::gamma_distribution

Konstruuje dystrybucję.

```cpp
explicit gamma_distribution(result_type alpha = 1.0, result_type beta = 1.0);
explicit gamma_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*alfa*\
Parametr `alpha` rozkładu.

*Beta*\
Parametr `beta` rozkładu.

*parametr*\
Struktura parametru używana do konstruowania rozkładu.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `0.0 < alpha` i`0.0 < beta`

Pierwszy Konstruktor konstruuje obiekt, którego przechowywana `alpha` wartość przechowuje wartość *Alpha* i której przechowywana `beta` wartość przechowuje wartość *beta*.

Drugi Konstruktor konstruuje obiekt, którego przechowywane parametry są inicjowane z *parametr*. Możesz uzyskać i ustawić bieżące parametry istniejącej dystrybucji, wywołując `param()` funkcję członkowską.

## <a name="param_type"></a>gamma_distribution::p aram_type

Przechowuje parametry dystrybucji.

```cpp
struct param_type {
   typedef gamma_distribution<result_type> distribution_type;
   param_type(result_type alpha = 1.0, result_type beta 1.0);
   result_type alpha() const;
   result_type beta() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

*alfa*\
Parametr `alpha` rozkładu.

*Beta*\
Parametr `beta` rozkładu.

*Kliknij*\
Wystąpienie `param_type` , do którego ma zostać wykonane porównanie.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `0.0 < alpha` i`0.0 < beta`

Tę strukturę można przesłać do konstruktora klasy dystrybucji podczas tworzenia wystąpienia, do `param()` funkcji składowej, aby ustawić przechowywane parametry istniejącej dystrybucji, `operator()` a także użyć zamiast przechowywanych parametrów.

## <a name="see-also"></a>Zobacz także

[\<random>](../standard-library/random.md)
