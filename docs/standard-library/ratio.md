---
title: '&lt;ratio&gt;'
ms.date: 11/04/2016
f1_keywords:
- ratio/std::mega
- ratio/std::peta
- ratio/std::ratio_greater
- ratio/std::micro
- ratio/std::ratio_add
- ratio/std::ratio_not_equal
- ratio/std::hecto
- ratio/std::nano
- ratio/std::ratio_less_equal
- ratio/std::ratio_less
- ratio/std::centi
- ratio/std::ratio_greater_equal
- ratio/std::ratio_subtract
- <ratio>
- ratio/std::atto
- ratio/std::tera
- ratio/std::milli
- ratio/std::ratio_multiply
- ratio/std::kilo
- ratio/std::ratio_divide
- ratio/std::giga
- ratio/std::pico
- ratio/std::femto
- ratio/std::ratio_equal
- ratio/std::ratio
- ratio/std::exa
- ratio/std::deci
- ratio/std::deca
ms.assetid: 8543e912-2d84-45ea-b3c0-bd7bfacee405
ms.openlocfilehash: f84bea2e3f4a01bb9428eddde3efbf53b73bc2f3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458163"
---
# <a name="ltratiogt"></a>&lt;ratio&gt;

Uwzględnij standardowy współczynnik \<nagłówka > do definiowania stałych i szablonów, które są używane do przechowywania i manipulowania wartościami racjonalnymi w czasie kompilacji.

## <a name="syntax"></a>Składnia

```cpp
#include <ratio>
```

### <a name="ratio-template"></a>Szablon współczynnika

```cpp
template<std::intmax_t Numerator, std::intmax_t Denominator = 1>
struct ratio // holds the ratio of Numerator to Denominator
{
   static constexpr std::intmax_t num;
   static constexpr std::intmax_t den;
   typedef ratio<num, den> type;
}
```

`ratio` Szablon definiuje stałe `den` statycznei`den` takie, `num` które  /  = = licznik/mianownik i `num` nie ma wspólnych czynników. `den` `num` `num` / `den`jest wartością, która jest reprezentowana przez klasę szablonu. W `type` związku z tym wyznacza `ratio<num, den>`Tworzenie wystąpienia.

### <a name="specializations"></a>Specjalizacje

\<współczynnik > również definiuje specjalizacje `ratio` , które mają następującą formę.

`template <class R1, class R2> struct ratio_specialization`

Każda specjalizacja przyjmuje dwa parametry szablonu, które również muszą być specjalizacjami `ratio`. Wartość `type` jest określana przez skojarzoną operację logiczną.

|Nazwa|`type`Wartościami|
|----------|------------------|
|`ratio_add`|`R1 + R2`|
|`ratio_divide`|`R1 / R2`|
|`ratio_equal`|`R1 == R2`|
|`ratio_greater`|`R1 > R2`|
|`ratio_greater_equal`|`R1 >= R2`|
|`ratio_less`|`R1 < R2`|
|`ratio_less_equal`|`R1 <= R2`|
|`ratio_multiply`|`R1 * R2`|
|`ratio_not_equal`|`!(R1 == R2)`|
|`ratio_subtract`|`R1 - R2`|

### <a name="typedefs"></a>definicje typów

Dla wygody nagłówek definiuje stosunki dla standardowych prefiksów SI:

```cpp
typedef ratio<1, 1000000000000000000> atto;
typedef ratio<1, 1000000000000000> femto;
typedef ratio<1, 1000000000000> pico;
typedef ratio<1, 1000000000> nano;
typedef ratio<1, 1000000> micro;
typedef ratio<1, 1000> milli;
typedef ratio<1, 100> centi;
typedef ratio<1, 10> deci;
typedef ratio<10, 1> deca;
typedef ratio<100, 1> hecto;
typedef ratio<1000, 1> kilo;
typedef ratio<1000000, 1> mega;
typedef ratio<1000000000, 1> giga;
typedef ratio<1000000000000, 1> tera;
typedef ratio<1000000000000000, 1> peta;
typedef ratio<1000000000000000000, 1> exa;
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
