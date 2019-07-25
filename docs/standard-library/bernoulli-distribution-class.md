---
title: bernoulli_distribution — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::bernoulli_distribution
- random/std::bernoulli_distribution::reset
- random/std::bernoulli_distribution::p
- random/std::bernoulli_distribution::param
- random/std::bernoulli_distribution::min
- random/std::bernoulli_distribution::max
- random/std::bernoulli_distribution::operator()
- random/std::bernoulli_distribution::param_type
- random/std::bernoulli_distribution::param_type::p
- random/std::bernoulli_distribution::param_type::operator==
- random/std::bernoulli_distribution::param_type::operator!=
helpviewer_keywords:
- std::bernoulli_distribution [C++]
- std::bernoulli_distribution [C++], reset
- std::bernoulli_distribution [C++], p
- std::bernoulli_distribution [C++], param
- std::bernoulli_distribution [C++], min
- std::bernoulli_distribution [C++], max
- std::bernoulli_distribution [C++], param_type
- std::bernoulli_distribution [C++], param_type
ms.assetid: 586bcde1-95ca-411a-bf17-4aaf19482f34
ms.openlocfilehash: faadc99b6351af884331e6658e1e11de8def2195
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447771"
---
# <a name="bernoullidistribution-class"></a>bernoulli_distribution — Klasa

Generuje rozkład Bernoulliego.

## <a name="syntax"></a>Składnia

```cpp
class bernoulli_distribution
   {
public:
   // types
   typedef bool result_type;
   struct param_type;

   // constructors and reset functions
   explicit bernoulli_distribution(double p = 0.5);
   explicit bernoulli_distribution(const param_type& parm);
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

*URNG*\
Jednolity aparat generatora liczb losowych. W przypadku możliwych typów zobacz [ \<losowe >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Klasa opisuje dystrybucję, która produkuje wartości typu **bool**, dystrybuowane zgodnie z funkcją dyskretnej dystrybucji rozkładu Bernoulliego. Poniższa tabela zawiera linki do artykułów na temat poszczególnych członków.

||||
|-|-|-|
|[bernoulli_distribution](#bernoulli_distribution)|`bernoulli_distribution::p`|`bernoulli_distribution::param`|
|`bernoulli_distribution::operator()`||[param_type](#param_type)|

Element członkowski `p()` właściwości zwraca aktualnie przechowywaną wartość `p`parametru dystrybucji.

Element członkowski `param()` właściwości ustawia lub `param_type` zwraca przechowywany pakiet parametrów dystrybucji.

`min()` I`max()` funkcje członkowskie zwracają najmniejszy możliwy wynik i największy możliwy wynik.

Funkcja członkowska odrzuca wszystkie wartości pamięci podręcznej, dzięki czemu wynik następnego wywołania do `operator()` nie zależy od wartości uzyskanych z aparatu przed wywołaniem. `reset()`

Funkcje `operator()` Członkowskie zwracają następną wygenerowaną wartość opartą na aparacie URNG, z bieżącego pakietu parametrów lub z określonym pakietem parametrów.

Aby uzyskać więcej informacji na temat klas dystrybucji i ich członków, zobacz [ \<Random >](../standard-library/random.md).

Aby uzyskać szczegółowe informacje na temat funkcji bezdyskretnego rozkładu Bernoulliego, zobacz artykuł Wolfram MathWorld [rozkład Bernoulliego](https://go.microsoft.com/fwlink/p/?linkid=398467).

## <a name="example"></a>Przykład

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double p, const int s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::bernoulli_distribution distr(p);

    std::cout << "p == " << distr.p() << std::endl;

    // generate the distribution as a histogram
    std::map<bool, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Histogram for " << s << " samples:" << std::endl;
    for (const auto& elem : histogram) {
        std::cout << std::boolalpha << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double p_dist = 0.5;
    int samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a double value for p distribution (where 0.0 <= p <= 1.0): ";
    std::cin >> p_dist;
    std::cout << "Enter an integer value for a sample count: ";
    std::cin >> samples;

    test(p_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .45
Enter an integer value for a sample count: 100
p == 0.45
Histogram for 100 samples:
false :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
true :::::::::::::::::::::::::::::::::::::::::
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowe >

**Przestrzeń nazw:** std

## <a name="bernoulli_distribution"></a>bernoulli_distribution::bernoulli_distribution

Konstruuje dystrybucję.

```cpp
explicit bernoulli_distribution(double p = 0.5);
explicit bernoulli_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*St*\
Parametr przechowywanej `p` dystrybucji.

*parametr*\
`param_type` Struktura używana do konstruowania rozkładu.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `0.0 ≤ p ≤ 1.0`

Pierwszy Konstruktor konstruuje obiekt, którego przechowywana `p` wartość przechowuje wartość *p*.

Drugi Konstruktor konstruuje obiekt, którego przechowywane parametry są inicjowane z *parametr*. Możesz uzyskać i ustawić bieżące parametry istniejącej dystrybucji, wywołując `param()` funkcję członkowską.

## <a name="param_type"></a>bernoulli_distribution::p aram_type

Zawiera parametry dystrybucji.

struct param_type {typedef bernoulli_distribution distribution_type; param_type (Double p = 0,5); Double p () const;

   operator logiczny = = (const param_type & Right) const; operator logiczny! = (const param_type & Right) const; };

### <a name="parameters"></a>Parametry

*St*\
Parametr przechowywanej `p` dystrybucji.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `0.0 ≤ p ≤ 1.0`

Tę strukturę można przesłać do konstruktora klasy dystrybucji podczas tworzenia wystąpienia, do `param()` funkcji składowej, aby ustawić przechowywane parametry istniejącej dystrybucji, `operator()` a także użyć zamiast przechowywanych parametrów.

## <a name="see-also"></a>Zobacz także

[\<random>](../standard-library/random.md)
