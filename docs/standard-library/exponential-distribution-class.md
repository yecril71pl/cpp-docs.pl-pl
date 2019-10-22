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
ms.openlocfilehash: 7418c0316f98f633d229b3bb544bd34d2ac0fb07
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688089"
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

@No__t_1 *rzeczywistości*
Typ wyniku zmiennoprzecinkowego, wartość domyślna to **Double**. W przypadku możliwych typów zobacz [\<random >](../standard-library/random.md).

*URNG* \
Aparat generatora liczb losowych. W przypadku możliwych typów zobacz [\<random >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje dystrybucję, która produkuje wartości typu całkowitego określonego przez użytkownika, lub typ **Double** , jeśli nie jest podany, dystrybuowany zgodnie z rozkładem wykładniczym. Poniższa tabela zawiera linki do artykułów na temat poszczególnych członków.

||||
|-|-|-|
|[exponential_distribution](#exponential_distribution)|`exponential_distribution::lambda`|`exponential_distribution::param`|
|`exponential_distribution::operator()`||[param_type](#param_type)|

Funkcja elementu członkowskiego właściwości `lambda()` zwraca wartość dla przechowywanego parametru dystrybucji `lambda`.

Funkcja elementu członkowskiego właściwości `param()` ustawia lub zwraca `param_type` przechowywany pakiet parametrów dystrybucji.

Aby uzyskać więcej informacji na temat klas dystrybucji i ich członków, zobacz [\<random >](../standard-library/random.md).

Aby uzyskać szczegółowe informacje na temat rozkładu wykładniczego, zobacz [rozkład wykładniczy](https://go.microsoft.com/fwlink/p/?linkid=401098)w artykule Wolfram MathWorld.

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

**Nagłówek:** \<random >

**Przestrzeń nazw:** std

## <a name="exponential_distribution"></a>exponential_distribution::exponential_distribution

Konstruuje dystrybucję.

```cpp
explicit exponential_distribution(result_type lambda = 1.0);
explicit exponential_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

\ *lambda*
@No__t_0 parametr dystrybucji.

*parametr* \
Pakiet parametrów używany do konstruowania rozkładu.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `0.0 < lambda`

Pierwszy Konstruktor konstruuje obiekt, którego przechowywana `lambda` wartość przechowuje wartość *lambda*.

Drugi Konstruktor konstruuje obiekt, którego przechowywane parametry są inicjowane z *parametr*. Możesz uzyskać i ustawić bieżące parametry istniejącej dystrybucji, wywołując funkcję elementu członkowskiego `param()`.

## <a name="param_type"></a>exponential_distribution::p aram_type

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

\ *lambda*
@No__t_0 parametr dystrybucji.

*prawa* \
Obiekt `param_type`, do którego ma zostać wykonane porównanie.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `0.0 < lambda`

Tę strukturę można przesłać do konstruktora klasy dystrybucji podczas tworzenia wystąpienia, do funkcji składowej `param()`, aby ustawić przechowywane parametry istniejącej dystrybucji i `operator()` do użycia zamiast przechowywanych parametrów.

## <a name="see-also"></a>Zobacz także

[\<random >](../standard-library/random.md)
