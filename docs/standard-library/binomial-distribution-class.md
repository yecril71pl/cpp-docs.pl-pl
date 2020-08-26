---
title: binomial_distribution — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::binomial_distribution
- random/std::binomial_distribution::reset
- random/std::binomial_distribution::p
- random/std::binomial_distribution::t
- random/std::binomial_distribution::param
- random/std::binomial_distribution::min
- random/std::binomial_distribution::max
- random/std::binomial_distribution::operator()
- random/std::binomial_distribution::param_type
- random/std::binomial_distribution::param_type::p
- random/std::binomial_distribution::param_type::t
- random/std::binomial_distribution::param_type::operator==
- random/std::binomial_distribution::param_type::operator!=
helpviewer_keywords:
- std::binomial_distribution [C++]
- std::binomial_distribution [C++], reset
- std::binomial_distribution [C++], p
- std::binomial_distribution [C++], t
- std::binomial_distribution [C++], param
- std::binomial_distribution [C++], min
- std::binomial_distribution [C++], max
- std::binomial_distribution [C++], param_type
- std::binomial_distribution [C++], param_type
ms.assetid: b7c8a26a-da8c-45a5-a3a8-208f7a3609ce
ms.openlocfilehash: 3054a29bd1bc82861461851d4403a7095ac1fcbd
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846514"
---
# <a name="binomial_distribution-class"></a>binomial_distribution — Klasa

Generuje rozkład dwumianowy.

## <a name="syntax"></a>Składnia

```cpp
template<class IntType = int>
class binomial_distribution
   {
public:
   // types
   typedef IntType result_type;
   struct param_type;

   // constructors and reset functions
   explicit binomial_distribution(result_type t = 1, double p = 0.5);
   explicit binomial_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type t() const;
   double p() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parametry

*IntType*\
Typ wyniku liczby całkowitej, wartość domyślna to **`int`** . Aby zapoznać się z możliwymi typami, zobacz [\<random>](../standard-library/random.md) .

*URNG*\
Jednolity aparat generatora liczb losowych. Aby zapoznać się z możliwymi typami, zobacz [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje dystrybucję, która produkuje wartości typu całkowitego określonego przez użytkownika, lub typ **`int`** , jeśli nie jest podany, dystrybuowany zgodnie z dyskretną funkcją skumulowanego prawdopodobieństwa rozkładu dwumianowego. Poniższa tabela zawiera linki do artykułów na temat poszczególnych członków.

[binomial_distribution](#binomial_distribution)\
[param_type](#param_type)

Elementy członkowskie właściwości `t()` i `p()` zwracają odpowiednio przechowywane wartości parametrów dystrybucji *t* i *p* .

Element członkowski właściwości `param()` Ustawia lub zwraca `param_type` przechowywany pakiet parametrów dystrybucji.

`min()`I `max()` funkcje członkowskie zwracają najmniejszy możliwy wynik i największy możliwy wynik.

`reset()`Funkcja członkowska odrzuca wszystkie wartości pamięci podręcznej, dzięki czemu wynik następnego wywołania do `operator()` nie zależy od wartości uzyskanych z aparatu przed wywołaniem.

`operator()`Funkcje członkowskie zwracają następną wygenerowaną wartość opartą na aparacie URNG, z bieżącego pakietu parametrów lub z określonym pakietem parametrów.

Aby uzyskać więcej informacji na temat klas dystrybucji i ich członków, zobacz [\<random>](../standard-library/random.md) .

Aby uzyskać szczegółowe informacje na temat funkcji dyskretnego prawdopodobieństwa rozkładu dwumianowego, zobacz Wolfram MathWorld [rozkład dwumianowy](https://go.microsoft.com/fwlink/p/?linkid=398469)artykułu.

## <a name="example"></a>Przykład

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const int t, const double p, const int& s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::binomial_distribution<> distr(t, p);

    std::cout << std::endl;
    std::cout << "p == " << distr.p() << std::endl;
    std::cout << "t == " << distr.t() << std::endl;

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
    int    t_dist = 1;
    double p_dist = 0.5;
    int    samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter an integer value for t distribution (where 0 <= t): ";
    std::cin >> t_dist;
    std::cout << "Enter a double value for p distribution (where 0.0 <= p <= 1.0): ";
    std::cin >> p_dist;
    std::cout << "Enter an integer value for a sample count: ";
    std::cin >> samples;

    test(t_dist, p_dist, samples);
}
```

Pierwsze uruchomienie:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for t distribution (where 0 <= t): 22
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .25
Enter an integer value for a sample count: 100

p == 0.25
t == 22
Histogram for 100 samples:
    1 :
    2 ::
    3 :::::::::::::
    4 ::::::::::::::
    5 :::::::::::::::::::::::::
    6 ::::::::::::::::::
    7 :::::::::::::
    8 ::::::
    9 ::::::
    11 :
    12 :
```

Drugi przebieg:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for t distribution (where 0 <= t): 22
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .5
Enter an integer value for a sample count: 100

p == 0.5
t == 22
Histogram for 100 samples:
    6 :
    7 ::
    8 :::::::::
    9 ::::::::::
    10 ::::::::::::::::
    11 :::::::::::::::::::
    12 :::::::::::
    13 :::::::::::::
    14 :::::::::::::::
    15 ::
    16 ::
```

Trzeci przebieg:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for t distribution (where 0 <= t): 22
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .75
Enter an integer value for a sample count: 100

p == 0.75
t == 22
Histogram for 100 samples:
    13 ::::
    14 :::::::::::
    15 :::::::::::::::
    16 :::::::::::::::::::::
    17 ::::::::::::::
    18 :::::::::::::::::
    19 :::::::::::
    20 ::::::
    21 :
```

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<random>

**Przestrzeń nazw:** std

## <a name="binomial_distributionbinomial_distribution"></a><a name="binomial_distribution"></a> binomial_distribution:: binomial_distribution

Konstruuje dystrybucję.

```cpp
explicit binomial_distribution(result_type t = 1, double p = 0.5);
explicit binomial_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*&*\
`t`Parametr rozkładu.

*St*\
`p`Parametr rozkładu.

*parametr*\
`param_type`Struktura używana do konstruowania rozkładu.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `0 ≤ t` lub `0.0 ≤ p ≤ 1.0`

Pierwszy Konstruktor konstruuje obiekt, którego przechowywana wartość *p* utrzymuje wartość *p* i której przechowywana wartość *t* przechowuje wartość *t*.

Drugi Konstruktor konstruuje obiekt, którego przechowywane parametry są inicjowane z *parametr*. Możesz uzyskać i ustawić bieżące parametry istniejącej dystrybucji, wywołując `param()` funkcję członkowską.

## <a name="binomial_distributionparam_type"></a><a name="param_type"></a> binomial_distribution::p aram_type

Przechowuje wszystkie parametry dystrybucji.

```cpp
struct param_type {
   typedef binomial_distribution<result_type> distribution_type;
   param_type(result_type t = 1, double p = 0.5);
   result_type t() const;
   double p() const;
   .....
   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

*&*\
`t`Parametr rozkładu.

*St*\
`p`Parametr rozkładu.

*Kliknij*\
Obiekt, który `param_type` ma zostać porównany.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `0 ≤ t` lub `0.0 ≤ p ≤ 1.0`

Tę strukturę można przesłać do konstruktora klasy dystrybucji podczas tworzenia wystąpienia, do `param()` funkcji składowej, aby ustawić przechowywane parametry istniejącej dystrybucji, a także `operator()` użyć zamiast przechowywanych parametrów.

## <a name="see-also"></a>Zobacz też

[\<random>](../standard-library/random.md)
