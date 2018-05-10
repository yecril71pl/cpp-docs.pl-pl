---
title: uniform_real_distribution — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::uniform_real_distribution
- random/std::uniform_real_distribution::reset
- random/std::uniform_real_distribution::a
- random/std::uniform_real_distribution::b
- random/std::uniform_real_distribution::param
- random/std::uniform_real_distribution::min
- random/std::uniform_real_distribution::max
- random/std::uniform_real_distribution::operator()
- random/std::uniform_real_distribution::param_type
- random/std::uniform_real_distribution::param_type::a
- random/std::uniform_real_distribution::param_type::b
- random/std::uniform_real_distribution::param_type::operator==
- random/std::uniform_real_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- std::uniform_real_distribution [C++]
- std::uniform_real_distribution [C++], reset
- std::uniform_real_distribution [C++], a
- std::uniform_real_distribution [C++], b
- std::uniform_real_distribution [C++], param
- std::uniform_real_distribution [C++], min
- std::uniform_real_distribution [C++], max
- std::uniform_real_distribution [C++], param_type
- std::uniform_real_distribution [C++], param_type
ms.assetid: 5cf906fd-0319-4984-b21b-98425cd7532d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bedb88ae44faaea9d65b41dcc98a4e83354ea71b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="uniformrealdistribution-class"></a>uniform_real_distribution — Klasa

Generuje jednolity (każda wartość jest równie prawdopodobne) zmiennoprzecinkowe dystrybucji w ramach danych wyjściowych zakresu, który jest wyłącznie włącznie.

## <a name="syntax"></a>Składnia

```cpp
template<class RealType = double>
   class uniform_real_distribution {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructors and reset functions
   explicit uniform_real_distribution(
      result_type a = 0.0, result_type b = 1.0);
   explicit uniform_real_distribution(const param_type& parm);
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

*RealType* wartość domyślna typu wynik zmiennoprzecinkowy to `double`. Dla typów możliwych [ \<losowe >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje dystrybucji wyłącznie z wartościami granicznymi tworzącego wartości określonych przez użytkownika całkowitych, zmiennoprzecinkowych typ punktu z dystrybucji tak, aby każda wartość jest równie prawdopodobne. Poniższe łącza tabeli do artykułów na temat poszczególnych członków.

||||
|-|-|-|
|[uniform_real_distribution](#uniform_real_distribution)|`uniform_real_distribution::a`|`uniform_real_distribution::param`|
|`uniform_real_distribution::operator()`|`uniform_real_distribution::b`|[param_type](#param_type)|

Element członkowski właściwości `a()` zwraca aktualnie przechowywana minimalna granica dystrybucji, podczas `b()` zwraca aktualnie przechowywana granica maksymalna. Dla tej klasy dystrybucji tych minimalne i maksymalne wartości są takie same jak zwracany przez typowych funkcji właściwości `min()` i `max()` opisanego w [ \<losowe >](../standard-library/random.md) tematu.

Element członkowski właściwości `param()` Ustawia lub zwraca `param_type` dystrybucji składowanych parametr pakietu.

`min()` i `max()` funkcje Członkowskie zwracają najmniejsza możliwa wynik i największa możliwa wynik, odpowiednio.

`reset()` Funkcji członkowskiej odrzuca wszystkie buforowane wartości, tak aby wynik następne wywołanie `operator()` nie zależy od wartości uzyskane z aparatu przed wywołaniem.

`operator()` Elementu członkowskiego zwracają wartość następnego wygenerowanego oparty na aparacie URNG, z bieżącego pakietu parametrów lub pakiet określony parametr.

Aby uzyskać więcej informacji o dystrybucji klasy i ich elementy członkowskie, zobacz [ \<losowe >](../standard-library/random.md).

## <a name="example"></a>Przykład

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double a, const double b, const int s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::uniform_real_distribution<> distr(a,b);

    std::cout << "lower bound == " << distr.a() << std::endl;
    std::cout << "upper bound == " << distr.b() << std::endl;

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
            << std::setprecision(10) << elem.first << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double a_dist = 1.0;
    double b_dist = 1.5;

    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the lower bound of the distribution: ";
    std::cin >> a_dist;
    std::cout << "Enter a floating point value for the upper bound of the distribution: ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}

```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the lower bound of the distribution: 0
Enter a floating point value for the upper bound of the distribution: 1
Enter an integer value for the sample count: 10
lower bound == 0
upper bound == 1
Distribution for 10 samples:
          1: 0.0288609485
          2: 0.2007994386
          3: 0.3027480117
          4: 0.4124758695
          5: 0.4413777133
          6: 0.4846447405
          7: 0.6225745916
          8: 0.6880935217
          9: 0.7541936723
         10: 0.8795716566
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowe >

**Namespace:** Standard

## <a name="uniform_real_distribution"></a>  uniform_real_distribution::uniform_real_distribution

Tworzy dystrybucji.

```cpp
explicit uniform_real_distribution(result_type a = 0.0, result_type b = 1.0);
explicit uniform_real_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*a* dolna granica wartości losowych włącznie.

*b* górna granica wartości losowych wyłącznego.

*Parametr* `param_type` struktury użyta do skonstruowania dystrybucji.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `a < b`

Pierwszy Konstruktor konstrukcji obiektu których przechowywane `a` wartość przechowuje wartość *a* i których przechowywane `b` wartość zawiera wartość *b*.

Drugi Konstruktor konstrukcji obiektu, którego parametry przechowywane są inicjowane z *parametr*. Możesz uzyskać i ustawić bieżących parametrów istniejącego dystrybucji przez wywołanie metody `param()` funkcję elementu członkowskiego.

## <a name="param_type"></a>  uniform_real_distribution::param_type

Przechowuje wszystkie parametry dystrybucji.

```cpp
struct param_type {
   typedef uniform_real_distribution<result_type> distribution_type;
   param_type(result_type a = 0.0, result_type b = 1.0);
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

*a* dolna granica wartości losowych włącznie.

*b* górna granica wartości losowych wyłącznego.

*prawy* `param_type` obiekt do porównania z tym.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `a < b`

Ta struktura może być przekazany do konstruktora klasy dystrybucji przy tworzeniu wystąpienia, do `param()` funkcji członkowskiej, aby ustawić parametry przechowywane istniejących dystrybucji oraz do `operator()` do użycia zamiast przechowywane parametry.

## <a name="see-also"></a>Zobacz także

[\<losowe >](../standard-library/random.md)<br/>
