---
title: exponential_distribution — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::exponential_distribution
- random/std::exponential_distribution::reset
- random/std::exponential_distribution::lambda
- random/std::exponential_distribution::param
- random/std::exponential_distribution::min
- random/std::exponential_distribution::max
- random/std::exponential_distribution::operator()
- random/std::exponential_distribution::param_type
- random/std::exponential_distribution::param_type::lambda
- random/std::exponential_distribution::param_type::operator==
- random/std::exponential_distribution::param_type::operator!=
helpviewer_keywords:
- std::exponential_distribution [C++]
- std::exponential_distribution [C++], reset
- std::exponential_distribution [C++], lambda
- std::exponential_distribution [C++], param
- std::exponential_distribution [C++], min
- std::exponential_distribution [C++], max
- std::exponential_distribution [C++], param_type
- std::exponential_distribution [C++], param_type
ms.assetid: d54f3126-a09b-45f9-a30b-0d94d03bcdc9
ms.openlocfilehash: a281f7fd77c0a68fca3a8fcfa163758ec464f1d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368720"
---
# <a name="exponential_distribution-class"></a>exponential_distribution — Klasa

Generuje rozkład wykładniczy.

## <a name="syntax"></a>Składnia

```cpp
template<class RealType = double>
class exponential_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructors and reset functions
   explicit exponential_distribution(result_type lambda = 1.0);
   explicit exponential_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type lambda() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parametry

*Typ rzeczywisty*\
Typ wyniku zmiennoprzecinkowego, domyślnie **podwoić**. Możliwe typy można znaleźć w [ \<>losowych ](../standard-library/random.md).

*Urng*\
Silnik generatora liczb losowych. Możliwe typy można znaleźć w [ \<>losowych ](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje rozkład, który tworzy wartości typu całkowitego określonego przez użytkownika lub wpisz **dwukrotnie,** jeśli nie jest podany, dystrybuowane zgodnie z rozkładem wykładniczym. W poniższej tabeli znajdują się łącza do artykułów dotyczących poszczególnych członków.

||||
|-|-|-|
|[exponential_distribution](#exponential_distribution)|`exponential_distribution::lambda`|`exponential_distribution::param`|
|`exponential_distribution::operator()`||[param_type](#param_type)|

Funkcja `lambda()` elementu członkowskiego właściwości zwraca wartość `lambda`przechowywanego parametru rozkładu .

Funkcja elementu `param()` członkowskiego właściwości `param_type` ustawia lub zwraca pakiet parametrów przechowywanej dystrybucji.

Aby uzyskać więcej informacji na temat klas dystrybucji i ich członków, zobacz [ \<losowe>](../standard-library/random.md).

Aby uzyskać szczegółowe informacje na temat dystrybucji wykładniczej, zobacz Artykuł Wolfram MathWorld [Wykładniczy Rozkład](https://go.microsoft.com/fwlink/p/?linkid=401098).

## <a name="example"></a>Przykład

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double l, const int s) {

    // uncomment to use a non-deterministic generator
    //    std::random_device gen;
    std::mt19937 gen(1701);

    std::exponential_distribution<> distr(l);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "lambda() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.lambda() << std::endl;

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
    double l_dist = 0.5;
    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the 'lambda' distribution parameter (must be greater than zero): ";
    std::cin >> l_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(l_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'lambda' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == 0
max() == 1.79769e+308
lambda() == 1.0000000000
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

**Nagłówek:** \<losowe>

**Przestrzeń nazw:** std

## <a name="exponential_distributionexponential_distribution"></a><a name="exponential_distribution"></a>exponential_distribution::exponential_distribution

Konstruuje dystrybucję.

```cpp
explicit exponential_distribution(result_type lambda = 1.0);
explicit exponential_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*Lambda*\
Parametr `lambda` rozkładu.

*Parm*\
Pakiet parametrów używany do konstruowania dystrybucji.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:**`0.0 < lambda`

Pierwszy konstruktor tworzy obiekt, `lambda` którego przechowywana wartość zawiera wartość *lambda*.

Drugi konstruktor tworzy obiekt, którego przechowywane parametry są inicjowane z *parm*. Można uzyskać i ustawić bieżące parametry istniejącej `param()` dystrybucji, wywołując funkcję elementu członkowskiego.

## <a name="exponential_distributionparam_type"></a><a name="param_type"></a>exponential_distribution::param_type

Przechowuje parametry dystrybucji.

```cpp
struct param_type {
   typedef exponential_distribution<result_type> distribution_type;
   param_type(result_type lambda = 1.0);
   result_type lambda() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

*Lambda*\
Parametr `lambda` rozkładu.

*Prawo*\
Obiekt `param_type` do porównania z tym.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:**`0.0 < lambda`

Ta struktura może być przekazywana do konstruktora klasy `param()` dystrybucji w wystąpieniu, do funkcji elementu `operator()` członkowskiego, aby ustawić przechowywane parametry istniejącej dystrybucji i do użycia zamiast przechowywanych parametrów.

## <a name="see-also"></a>Zobacz też

[\<losowe>](../standard-library/random.md)
