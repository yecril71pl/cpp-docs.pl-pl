---
title: lognormal_distribution — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::lognormal_distribution
- random/std::lognormal_distribution::reset
- random/std::lognormal_distribution::m
- random/std::lognormal_distribution::s
- random/std::lognormal_distribution::param
- random/std::lognormal_distribution::min
- random/std::lognormal_distribution::max
- random/std::lognormal_distribution::operator()
- random/std::lognormal_distribution::param_type
- random/std::lognormal_distribution::param_type::m
- random/std::lognormal_distribution::param_type::s
- random/std::lognormal_distribution::param_type::operator==
- random/std::lognormal_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- std::lognormal_distribution [C++]
- std::lognormal_distribution [C++], reset
- std::lognormal_distribution [C++], m
- std::lognormal_distribution [C++], s
- std::lognormal_distribution [C++], param
- std::lognormal_distribution [C++], min
- std::lognormal_distribution [C++], max
- std::lognormal_distribution [C++], param_type
- std::lognormal_distribution [C++], param_type
ms.assetid: f2d6a431-6c3a-4370-b12e-4adb4ddf6cc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72b42546f140dfd150676c8bc21b4b651815281f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="lognormaldistribution-class"></a>lognormal_distribution — Klasa

Generuje dziennik rozkładu normalnego.

## <a name="syntax"></a>Składnia

```cpp
template <class RealType = double>
class lognormal_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;
   // constructor and reset functions
   explicit lognormal_distribution(result_type m = 0.0, result_type s = 1.0);
   explicit lognormal_distribution(const param_type& parm);
   void reset();
   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);
   // property functions
   result_type m() const;
   result_type s() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parametry

*RealType* wartość domyślna typu wynik zmiennoprzecinkowy to `double`. Dla typów możliwych [ \<losowe >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dystrybucji, który spowoduje utworzenie wartości typu całkowitego określone przez użytkownika typu lub typu `double` Jeśli nie zostanie podana, dystrybuowane zgodnie z dziennika rozkładu normalnego. Poniższe łącza tabeli do artykułów na temat poszczególnych członków.

||||
|-|-|-|
|[lognormal_distribution —](#lognormal_distribution)|`lognormal_distribution::m`|`lognormal_distribution::param`|
|`lognormal_distribution::operator()`|`lognormal_distribution::s`|[param_type](#param_type)|

Funkcje właściwości `m()` i `s()` zwracane wartości dla parametrów przechowywanych dystrybucji *m* i *s*odpowiednio.

Element członkowski właściwości `param()` Ustawia lub zwraca `param_type` dystrybucji składowanych parametr pakietu.

`min()` i `max()` funkcje Członkowskie zwracają najmniejsza możliwa wynik i największa możliwa wynik, odpowiednio.

`reset()` Funkcji członkowskiej odrzuca wszystkie buforowane wartości, tak aby wynik następne wywołanie `operator()` nie zależy od wartości uzyskane z aparatu przed wywołaniem.

`operator()` Elementu członkowskiego zwracają wartość następnego wygenerowanego oparty na aparacie URNG, z bieżącego pakietu parametrów lub pakiet określony parametr.

Aby uzyskać więcej informacji o dystrybucji klasy i ich elementy członkowskie, zobacz [ \<losowe >](../standard-library/random.md).

Aby uzyskać szczegółowe informacje na temat dystrybucji logarytmu naturalnego, zobacz artykuł Wolfram MathWorld [logarytmu naturalnego dystrybucji](http://go.microsoft.com/fwlink/p/?linkid=400917).

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

    lognormal_distribution<> distr(m, s);

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "m() == " << fixed << setw(11) << setprecision(10) << distr.m() << endl;
    cout << "s() == " << fixed << setw(11) << setprecision(10) << distr.s() << endl;

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
    cout << "Enter a floating point value for the 'm' distribution parameter: ";
    cin >> m_dist;
    cout << "Enter a floating point value for the 's' distribution parameter (must be greater than zero): ";
    cin >> s_dist;
    cout << "Enter an integer value for the sample count: ";
    cin >> samples;

    test(m_dist, s_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'm' distribution parameter: 0
Enter a floating point value for the 's' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == -1.79769e+308
max() == 1.79769e+308
m() == 0.0000000000
s() == 1.0000000000
Distribution for 10 samples:
    1: 0.3862809339
    2: 0.4128865601
    3: 0.4490576787
    4: 0.4862035428
    5: 0.5930607126
    6: 0.8190778771
    7: 0.8902379317
    8: 2.8332911667
    9: 5.1359445565
    10: 5.4406507912
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowe >

**Namespace:** Standard

## <a name="lognormal_distribution"></a>  lognormal_distribution::lognormal_distribution

Tworzy dystrybucji.

```cpp
explicit lognormal_distribution(RealType m = 0.0, RealType s = 1.0);
explicit lognormal_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*m* `m` parametru dystrybucji.

*s* `s` parametru dystrybucji.

*Parametr* `param_type` struktury użyta do skonstruowania dystrybucji.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `0.0 < s`

Pierwszy Konstruktor konstrukcji obiektu których przechowywane `m` wartość zawiera wartość *m* i których przechowywane `s` wartość przechowuje wartość *s*.

Drugi Konstruktor konstrukcji obiektu, którego parametry przechowywane są inicjowane z *parametr*. Możesz uzyskać i ustawić bieżących parametrów istniejącego dystrybucji przez wywołanie metody `param()` funkcję elementu członkowskiego.

## <a name="param_type"></a>  lognormal_distribution::param_type

Przechowuje parametry dystrybucji.

```cpp
struct param_type {
   typedef lognormal_distribution<result_type> distribution_type;
   param_type(result_type m = 0.0, result_type s = 1.0);
   result_type m() const;
   result_type s() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
};
```

### <a name="parameters"></a>Parametry

*m* `m` parametru dystrybucji.

*s* `s` parametru dystrybucji.

*prawy* `param_type` struktury użyty do porównania.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `0.0 < s`

Ta struktura może być przekazany do konstruktora klasy dystrybucji przy tworzeniu wystąpienia, do `param()` funkcji członkowskiej, aby ustawić parametry przechowywane istniejących dystrybucji oraz do `operator()` do użycia zamiast przechowywane parametry.

## <a name="see-also"></a>Zobacz także

[\<losowe >](../standard-library/random.md)<br/>
