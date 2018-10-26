---
title: normal_distribution — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::normal_distribution
- random/std::normal_distribution::reset
- random/std::normal_distribution::mean
- random/std::normal_distribution::stddev
- random/std::normal_distribution::param
- random/std::normal_distribution::min
- random/std::normal_distribution::max
- random/std::normal_distribution::operator()
- random/std::normal_distribution::param_type
- random/std::normal_distribution::param_type::mean
- random/std::normal_distribution::param_type::stddev
- random/std::normal_distribution::param_type::operator==
- random/std::normal_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- std::normal_distribution [C++]
- std::normal_distribution [C++], reset
- std::normal_distribution [C++], mean
- std::normal_distribution [C++], stddev
- std::normal_distribution [C++], param
- std::normal_distribution [C++], min
- std::normal_distribution [C++], max
- std::normal_distribution [C++], param_type
- std::normal_distribution [C++], param_type
ms.assetid: bf92cdbd-bc72-4d4a-b588-173d748f0d7d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d298da140955c809db5e6128df3bf712838446e0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067738"
---
# <a name="normaldistribution-class"></a>normal_distribution — Klasa

Generuje rozkład normalny.

## <a name="syntax"></a>Składnia

```cpp
template<class RealType = double>
class normal_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructors and reset functions
   explicit normal_distribution(result_type mean = 0.0, result_type stddev = 1.0);
   explicit normal_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type mean() const;
   result_type stddev() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parametry

*RealType*<br/>
Typ wyniku zmiennoprzecinkowych, wartość domyślna to **double**. Aby możliwych typów, zobacz [ \<losowy >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dystrybucji, który tworzy wartości całkowitego określone przez użytkownika wpisać lub typ **double** rozkładane Jeśli nie zostanie podana, rozkład normalny. Poniższa tabela zawiera linki do artykułów na temat poszczególnych elementów członkowskich.

||||
|-|-|-|
|[normal_distribution](#normal_distribution)|`normal_distribution::mean`|`normal_distribution::param`|
|`normal_distribution::operator()`|`normal_distribution::stddev`|[param_type](#param_type)|

Funkcje właściwości `mean()` i `stddev()` zwracane wartości dla parametrów przechowywanych dystrybucji *oznacza* i *stddev* odpowiednio.

Właściwość elementu członkowskiego `param()` Ustawia lub zwraca `param_type` pakiet parametrów przechowywanych dystrybucji.

`min()` i `max()` funkcje Członkowskie zwracają najmniejsza możliwa wynik i największych możliwych wyników, odpowiednio.

`reset()` Funkcja elementu członkowskiego odrzuca wszystkie wartości z pamięci podręcznej, tak aby wynik następnego wywołania metody `operator()` nie zależy od żadnych wartości uzyskane z aparatu przed wywołaniem.

`operator()` Funkcje Członkowskie zwracają dalej wygenerowaną wartość opartą na aparacie URNG, z bieżącego pakietu parametrów lub pakietu określony parametr.

Aby uzyskać więcej informacji o dystrybucji klasy i składowe, zobacz [ \<losowy >](../standard-library/random.md).

Aby uzyskać szczegółowe informacje na temat rozkład normalny, zobacz artykuł Wolfram MathWorld [rozkładu normalnego](http://go.microsoft.com/fwlink/p/?linkid=400924).

## <a name="example"></a>Przykład

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

using namespace std;

void test(const double m, const double s, const int samples) {

    // uncomment to use a non-deterministic seed
    //    random_device gen;
    //    mt19937 gen(rd());
    mt19937 gen(1701);

    normal_distribution<> distr(m, s);

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "m() == " << fixed << setw(11) << setprecision(10) << distr.mean() << endl;
    cout << "s() == " << fixed << setw(11) << setprecision(10) << distr.stddev() << endl;

    // generate the distribution as a histogram
    map<double, int> histogram;
    for (int i = 0; i < samples; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    cout << "Distribution for " << samples << " samples:" << endl;
    int counter = 0;
    for (const auto& elem : histogram) {
        cout << fixed << setw(11) << ++counter << ": "
            << setw(14) << setprecision(10) << elem.first << endl;
    }
    cout << endl;
}

int main()
{
    double m_dist = 1;
    double s_dist = 1;
    int samples = 10;

    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;
    cout << "Enter a floating point value for the 'mean' distribution parameter: ";
    cin >> m_dist;
    cout << "Enter a floating point value for the 'stddev' distribution parameter (must be greater than zero): ";
    cin >> s_dist;
    cout << "Enter an integer value for the sample count: ";
    cin >> samples;

    test(m_dist, s_dist, samples);
}

```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'mean' distribution parameter: 0
Enter a floating point value for the 'stddev' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == -1.79769e+308
max() == 1.79769e+308
m() == 0.0000000000
s() == 1.0000000000
Distribution for 10 samples:
    1: -0.8845823965
    2: -0.1995761116
    3: -0.1162665130
    4: -0.0685154932
    5: 0.0403741461
    6: 0.1591327792
    7: 1.0414389924
    8: 1.5876269426
    9: 1.6362637713
    10: 2.7821317338
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowy >

**Namespace:** standardowe

## <a name="normal_distribution"></a>  normal_distribution::normal_distribution

Tworzy rozkład.

```cpp
explicit normal_distribution(result_type mean = 0.0, result_type stddev = 1.0);
explicit normal_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*mean*<br/>
`mean` Parametru dystrybucji.

*stddev*<br/>
`stddev` Parametru dystrybucji.

*parm*<br/>
Struktura parametr, używane do konstruowania dystrybucji.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `0.0 ≤ stddev`

Pierwszy Konstruktor konstruuje obiekt, którego przechowywane `mean` wartość przechowuje wartość *oznacza* i którego przechowywane `stddev` wartość przechowuje wartość *stddev*.

Drugi Konstruktor konstruuje obiekt, którego przechowywane parametry są inicjowane z *parametr*. Możesz uzyskać i ustawić bieżących parametrów istniejącego dystrybucji przez wywołanie metody `param()` funkcja elementu członkowskiego.

## <a name="param_type"></a>  normal_distribution::param_type

Przechowuje parametry dystrybucji.

```cpp
struct param_type {
   typedef normal_distribution<result_type> distribution_type;
   param_type(result_type mean = 0.0, result_type stddev = 1.0);
   result_type mean() const;
   result_type stddev() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

*mean*<br/>
`mean` Parametru dystrybucji.

*stddev*<br/>
`stddev` Parametru dystrybucji.

*right*<br/>
`param_type` Struktury użyty do porównania.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `0.0 ≤ stddev`

Ta struktura może być przekazywany do konstruktora klasy dystrybucji przy konkretyzacji, do `param()` funkcję elementu członkowskiego, aby ustawić przechowywanych parametrów istniejącego dystrybucji oraz do `operator()` ma być używany zamiast przechowywanych parametrów.

## <a name="see-also"></a>Zobacz także

[\<losowy >](../standard-library/random.md)<br/>
