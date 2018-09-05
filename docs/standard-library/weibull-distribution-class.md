---
title: weibull_distribution — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::weibull_distribution
- random/std::weibull_distribution::reset
- random/std::weibull_distribution::a
- random/std::weibull_distribution::b
- random/std::weibull_distribution::param
- random/std::weibull_distribution::min
- random/std::weibull_distribution::max
- random/std::weibull_distribution::operator()
- random/std::weibull_distribution::param_type
- random/std::weibull_distribution::param_type::a
- random/std::weibull_distribution::param_type::b
- random/std::weibull_distribution::param_type::operator==
- random/std::weibull_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- std::weibull_distribution [C++]
- std::weibull_distribution [C++], reset
- std::weibull_distribution [C++], a
- std::weibull_distribution [C++], b
- std::weibull_distribution [C++], param
- std::weibull_distribution [C++], min
- std::weibull_distribution [C++], max
- std::weibull_distribution [C++], param_type
- std::weibull_distribution [C++], param_type
ms.assetid: f20b49d3-1b9a-41af-8db4-baf800eaa02b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f6a71770afdb541efa76f85464d9aeef7b2fb91
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681011"
---
# <a name="weibulldistribution-class"></a>weibull_distribution — Klasa

Generuje rozkład Weibulla.

## <a name="syntax"></a>Składnia

```cpp
class weibull_distribution
   {
   public:
    // types
   typedef RealType result_type;
   struct param_type;

    // constructor and reset functions
   explicit weibull_distribution(result_type a = 1.0, result_type b = 1.0);
   explicit weibull_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
      result_type operator()(URNG& gen);
   template <class URNG>
      result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type a() const;
   result_type b() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parametry

*RealType* typu wyniku zmiennoprzecinkowych, wartość domyślna to **double**. Aby możliwych typów, zobacz [ \<losowy >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dystrybucji, który tworzy wartości zmiennoprzecinkowej określonych przez użytkownika wpisać lub typ **double** rozkładane Jeśli nie zostanie podana, rozkład Weibulla. Poniższa tabela zawiera linki do artykułów na temat poszczególnych elementów członkowskich.

||||
|-|-|-|
|[weibull_distribution](#weibull_distribution)|`weibull_distribution::a`|`weibull_distribution::param`|
|`weibull_distribution::operator()`|`weibull_distribution::b`|[param_type](#param_type)|

Funkcje właściwości `a()` i `b()` zwracać odpowiadających im wartości dla parametrów przechowywanych dystrybucji *a* i *b*.

Właściwość elementu członkowskiego `param()` Ustawia lub zwraca `param_type` pakiet parametrów przechowywanych dystrybucji.

`min()` i `max()` funkcje Członkowskie zwracają najmniejsza możliwa wynik i największych możliwych wyników, odpowiednio.

`reset()` Funkcja elementu członkowskiego odrzuca wszystkie wartości z pamięci podręcznej, tak aby wynik następnego wywołania metody `operator()` nie zależy od żadnych wartości uzyskane z aparatu przed wywołaniem.

`operator()` Funkcje Członkowskie zwracają dalej wygenerowaną wartość opartą na aparacie URNG, z bieżącego pakietu parametrów lub pakietu określony parametr.

Aby uzyskać więcej informacji o dystrybucji klasy i składowe, zobacz [ \<losowy >](../standard-library/random.md).

Aby uzyskać szczegółowe informacje na temat rozkład Weibulla, zobacz artykuł Wolfram MathWorld [rozkład Weibulla](http://mathworld.wolfram.com/WeibullDistribution.html).

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

    std::weibull_distribution<> distr(a, b);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "a() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.a() << std::endl;
    std::cout << "b() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.b() << std::endl;

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
    std::cout << "Enter a floating point value for the 'a' distribution parameter (must be greater than zero): ";
    std::cin >> a_dist;
    std::cout << "Enter a floating point value for the 'b' distribution parameter (must be greater than zero): ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}

```

## <a name="output"></a>Dane wyjściowe

Najpierw uruchom:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'a' distribution parameter (must be greater than zero): 1
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == 0
max() == 1.79769e+308
a() == 1.0000000000
b() == 1.0000000000
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

Uruchom drugie:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'a' distribution parameter (must be greater than zero): .5
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 5.5
Enter an integer value for the sample count: 10

min() == 0
max() == 1.79769e+308
a() == 0.5000000000
b() == 5.5000000000
Distribution for 10 samples:
    1: 0.0482759823
    2: 0.0826617486
    3: 2.2835941207
    4: 2.3604817485
    5: 2.9417663742
    6: 2.9418471657
    7: 3.1685268104
    8: 11.5109922290
    9: 14.8543594043
    10: 24.7220241239
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowy >

**Namespace:** standardowe

## <a name="weibull_distribution"></a>  weibull_distribution::weibull_distribution

```cpp
explicit weibull_distribution(result_type a = 1.0, result_type b = 1.0);
explicit weibull_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*a*  
`a` Parametru dystrybucji.

*b*  
`b` Parametru dystrybucji.

*parm*  
`param_type` Struktura używana do konstruowania dystrybucji.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `0.0 < a` i `0.0 < b`

Pierwszy Konstruktor konstrukcji obiektu których przechowywane `a` wartość przechowuje wartość *a* i których przechowywane `b` wartość zawiera wartość *b*.

Drugi Konstruktor konstruuje obiekt, którego przechowywane parametry są inicjowane z *parametr*. Możesz uzyskać i ustawić bieżących parametrów istniejącego dystrybucji przez wywołanie metody `param()` funkcja elementu członkowskiego.

## <a name="param_type"></a>  weibull_distribution::param_type

Przechowuje parametry dystrybucji.

```cpp
struct param_type {
   typedef weibull_distribution<result_type> distribution_type;
   param_type(result_type a = 1.0, result_type b = 1.0);
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

*a*  
`a` Parametru dystrybucji.

*b*  
`b` Parametru dystrybucji.

*right*  
`param_type` Obiekt do porównania z tym.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `0.0 < a` i `0.0 < b`

Ta struktura może być przekazywany do konstruktora klasy dystrybucji przy konkretyzacji, do `param()` funkcję elementu członkowskiego, aby ustawić przechowywanych parametrów istniejącego dystrybucji oraz do `operator()` ma być używany zamiast przechowywanych parametrów.

## <a name="see-also"></a>Zobacz także

[\<losowy >](../standard-library/random.md)<br/>
