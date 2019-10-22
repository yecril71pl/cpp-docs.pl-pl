---
title: uniform_int_distribution — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::uniform_int_distribution
- random/std::uniform_int_distribution::reset
- random/std::uniform_int_distribution::a
- random/std::uniform_int_distribution::b
- random/std::uniform_int_distribution::param
- random/std::uniform_int_distribution::min
- random/std::uniform_int_distribution::max
- random/std::uniform_int_distribution::operator()
- random/std::uniform_int_distribution::param_type
- random/std::uniform_int_distribution::param_type::a
- random/std::uniform_int_distribution::param_type::b
- random/std::uniform_int_distribution::param_type::operator==
- random/std::uniform_int_distribution::param_type::operator!=
helpviewer_keywords:
- std::uniform_int_distribution [C++]
- std::uniform_int_distribution [C++], reset
- std::uniform_int_distribution [C++], a
- std::uniform_int_distribution [C++], b
- std::uniform_int_distribution [C++], param
- std::uniform_int_distribution [C++], min
- std::uniform_int_distribution [C++], max
- std::uniform_int_distribution [C++], param_type
- std::uniform_int_distribution [C++], param_type
ms.assetid: a1867dcd-3bd9-4787-afe3-4b62692c1d04
ms.openlocfilehash: 7e24c320e909bb2d0471acdd275f89c43d3e44de
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684513"
---
# <a name="uniform_int_distribution-class"></a>uniform_int_distribution — Klasa

Generuje jednolity (każda wartość jest równie prawdopodobna) Dystrybucja liczb całkowitych w ramach zakresu wyjściowego, który jest włącznie.

## <a name="syntax"></a>Składnia

```cpp
template<class IntType = int>
   class uniform_int_distribution {
public:
   // types
   typedef IntType result_type;
   struct param_type;

   // constructors and reset functions
   explicit uniform_int_distribution(
      result_type a = 0, result_type b = numeric_limits<result_type>::max());
   explicit uniform_int_distribution(const param_type& parm);
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

*IntType* \
Typ wyniku liczby całkowitej, wartość domyślna to **int**. W przypadku możliwych typów zobacz [\<random >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje dystrybucję obejmującą włącznie, która tworzy wartości typu całkowitego określonego przez użytkownika z dystrybucją, tak aby każda wartość była równie prawdopodobna. Poniższa tabela zawiera linki do artykułów na temat poszczególnych członków.

||||
|-|-|-|
|[uniform_int_distribution](#uniform_int_distribution)|`uniform_int_distribution::a`|`uniform_int_distribution::param`|
|`uniform_int_distribution::operator()`|`uniform_int_distribution::b`|[param_type](#param_type)|

Element członkowski właściwości `a()` zwraca aktualnie przechowywaną minimalną granicę dystrybucji, podczas gdy `b()` zwraca aktualnie przechowywaną granicę maksymalną. Dla tej klasy dystrybucji te wartości minimalne i maksymalne są takie same jak te, które są zwracane przez wspólne funkcje właściwości `min()` i `max()`.

Element członkowski właściwości `param()` ustawia lub zwraca `param_type` przechowywany pakiet parametrów dystrybucji.

Funkcje członkowskie `min()` i `max()` zwracają najmniejszy możliwy wynik i największy możliwy wynik.

Funkcja członkowska `reset()` odrzuca wszystkie wartości pamięci podręcznej, dzięki czemu wynik następnego wywołania do `operator()` nie zależy od wartości uzyskanych z aparatu przed wywołaniem.

Funkcje składowe `operator()` zwracają następną wygenerowaną wartość opartą na aparacie URNG, z bieżącego pakietu parametrów lub z określonym pakietem parametrów.

Aby uzyskać więcej informacji na temat klas dystrybucji i ich członków, zobacz [\<random >](../standard-library/random.md).

## <a name="example"></a>Przykład

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const int a, const int b, const int s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::uniform_int_distribution<> distr(a, b);

    std::cout << "lower bound == " << distr.a() << std::endl;
    std::cout << "upper bound == " << distr.b() << std::endl;

    // generate the distribution as a histogram
    std::map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Distribution for " << s << " samples:" << std::endl;
    for (const auto& elem : histogram) {
        std::cout << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    int a_dist = 1;
    int b_dist = 10;

    int samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter an integer value for the lower bound of the distribution: ";
    std::cin >> a_dist;
    std::cout << "Enter an integer value for the upper bound of the distribution: ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the lower bound of the distribution: 0
Enter an integer value for the upper bound of the distribution: 12
Enter an integer value for the sample count: 200
lower bound == 0
upper bound == 12
Distribution for 200 samples:
    0 :::::::::::::::
    1 :::::::::::::::::::::
    2 ::::::::::::::::::
    3 :::::::::::::::
    4 :::::::
    5 :::::::::::::::::::::
    6 :::::::::::::
    7 ::::::::::
    8 :::::::::::::::
    9 :::::::::::::
   10 ::::::::::::::::::::::
   11 :::::::::::::
   12 :::::::::::::::::
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<random >

**Przestrzeń nazw:** std

## <a name="uniform_int_distribution"></a>uniform_int_distribution::uniform_int_distribution

Konstruuje dystrybucję.

```cpp
explicit uniform_int_distribution(
   result_type a = 0, result_type b = std::numeric_limits<result_type>::max());
explicit uniform_int_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*\*
Dolna granica wartości losowych włącznie.

*b* \
Górna granica wartości losowych, włącznie.

*parametr* \
Struktura `param_type` używana do konstruowania rozkładu.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `a ≤ b`

Pierwszy Konstruktor konstruuje obiekt, *którego przechowywana wartość utrzymuje wartość a* i *której* przechowywana wartość *b* utrzymuje wartość *b*.

Drugi Konstruktor konstruuje obiekt, którego przechowywane parametry są inicjowane z *parametr*. Możesz uzyskać i ustawić bieżące parametry istniejącej dystrybucji, wywołując funkcję elementu członkowskiego `param()`.

## <a name="param_type"></a>uniform_int_distribution::p aram_type

Przechowuje parametry dystrybucji.

```cpp
struct param_type {
   typedef uniform_int_distribution<result_type> distribution_type;
   param_type(
      result_type a = 0, result_type b = std::numeric_limits<result_type>::max());
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

*\*
Dolna granica wartości losowych włącznie.

*b* \
Górna granica wartości losowych, włącznie.

*prawa* \
Obiekt `param_type`, do którego ma zostać wykonane porównanie.

### <a name="remarks"></a>Uwagi

**Warunek wstępny:** `a ≤ b`

Tę strukturę można przesłać do konstruktora klasy dystrybucji podczas tworzenia wystąpienia, do funkcji składowej `param()`, aby ustawić przechowywane parametry istniejącej dystrybucji i `operator()` do użycia zamiast przechowywanych parametrów.

## <a name="see-also"></a>Zobacz także

[\<random >](../standard-library/random.md)
