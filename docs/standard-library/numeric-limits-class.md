---
title: numeric_limits — Klasa
ms.date: 11/04/2016
f1_keywords:
- limits/std::numeric_limits
- limits/std::numeric_limits::denorm_min
- limits/std::numeric_limits::digits
- limits/std::numeric_limits::digits10
- limits/std::numeric_limits::epsilon
- limits/std::numeric_limits::has_denorm
- limits/std::numeric_limits::has_denorm_loss
- limits/std::numeric_limits::has_infinity
- limits/std::numeric_limits::has_quiet_NaN
- limits/std::numeric_limits::has_signaling_NaN
- limits/std::numeric_limits::infinity
- limits/std::numeric_limits::is_bounded
- limits/std::numeric_limits::is_exact
- limits/std::numeric_limits::is_iec559
- limits/std::numeric_limits::is_integer
- limits/std::numeric_limits::is_modulo
- limits/std::numeric_limits::is_signed
- limits/std::numeric_limits::is_specialized
- limits/std::numeric_limits::lowest
- limits/std::numeric_limits::max
- limits/std::numeric_limits::max_digits10
- limits/std::numeric_limits::max_exponent
- limits/std::numeric_limits::max_exponent10
- limits/std::numeric_limits::min
- limits/std::numeric_limits::min_exponent
- limits/std::numeric_limits::min_exponent10
- limits/std::numeric_limits::quiet_NaN
- limits/std::numeric_limits::radix
- limits/std::numeric_limits::round_error
- limits/std::numeric_limits::round_style
- limits/std::numeric_limits::signaling_NaN
- limits/std::numeric_limits::tinyness_before
- limits/std::numeric_limits::traps
helpviewer_keywords:
- std::numeric_limits [C++]
- std::numeric_limits [C++], denorm_min
- std::numeric_limits [C++], digits
- std::numeric_limits [C++], digits10
- std::numeric_limits [C++], epsilon
- std::numeric_limits [C++], has_denorm
- std::numeric_limits [C++], has_denorm_loss
- std::numeric_limits [C++], has_infinity
- std::numeric_limits [C++], has_quiet_NaN
- std::numeric_limits [C++], has_signaling_NaN
- std::numeric_limits [C++], infinity
- std::numeric_limits [C++], is_bounded
- std::numeric_limits [C++], is_exact
- std::numeric_limits [C++], is_iec559
- std::numeric_limits [C++], is_integer
- std::numeric_limits [C++], is_modulo
- std::numeric_limits [C++], is_signed
- std::numeric_limits [C++], is_specialized
- std::numeric_limits [C++], lowest
- std::numeric_limits [C++], max
- std::numeric_limits [C++], max_digits10
- std::numeric_limits [C++], max_exponent
- std::numeric_limits [C++], max_exponent10
- std::numeric_limits [C++], min
- std::numeric_limits [C++], min_exponent
- std::numeric_limits [C++], min_exponent10
- std::numeric_limits [C++], quiet_NaN
- std::numeric_limits [C++], radix
- std::numeric_limits [C++], round_error
- std::numeric_limits [C++], round_style
- std::numeric_limits [C++], signaling_NaN
- std::numeric_limits [C++], tinyness_before
- std::numeric_limits [C++], traps
ms.assetid: 9e817177-0e91-48e6-b680-0531c4b26625
ms.openlocfilehash: 861850f192281d64ef02ec4a241315c05cd3318f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564622"
---
# <a name="numericlimits-class"></a>numeric_limits — Klasa

Klasa szablonu opisuje arytmetyczne właściwości wbudowanych typów liczbowych.

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class numeric_limits
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
Element podstawowy typ danych, którego właściwości są przetestowane zapytania lub zestawu.

## <a name="remarks"></a>Uwagi

Nagłówek definiuje jawne specjalizacje dla typów **wchar_t**, **bool**, **char**, **podpisany char**, **bez znaku CHAR**, **krótki**, **typ unsigned short**, **int**, **unsigned int**, **długich**, **unsigned long**, **float**, **double**, **typu long double**, **długi długi**, **unsigned long long**, **char16_t**, i **char32_t**. Dla tych jawne specjalizacje elementu członkowskiego [numeric_limits::is_specialized](#is_specialized) jest **true**, i wszystkie odpowiednie elementy członkowskie mają znaczący wartości. Program można podać dodatkowe jawne specjalizacje. Większość funkcji składowej klasy opisują lub testowania implementacji możliwe **float**.

Dla dowolnego specjalizacji żadnych elementów członkowskich mają znaczący wartości. Obiekt elementu członkowskiego, który nie ma odpowiednią wartość przechowuje wartość zero (lub **false**) i funkcja elementu członkowskiego, która nie zwraca zrozumiałą wartość zwraca `Type(0)`.

### <a name="static-functions-and-constants"></a>Funkcje statyczne i stałe

|||
|-|-|
|[denorm_min](#denorm_min)|Zwraca wartość różną od zera najmniejszy nieznormalizowane wartość.|
|[cyfry](#digits)|Zwraca liczbę cyfr podstawy, których typ może reprezentować bez utraty dokładności.|
|[digits10](#digits10)|Zwraca liczbę cyfr dziesiętnych, reprezentujących przez typ bez utraty dokładności.|
|[Epsilon](#epsilon)|Zwraca różnicę między 1 a najmniejsza wartość większa niż 1, który może reprezentować typu danych.|
|[has_denorm —](#has_denorm)|Sprawdza, czy typ umożliwia nieznormalizowane wartości.|
|[has_denorm_loss —](#has_denorm_loss)|Sprawdza, czy wykryto utratę dokładności utratę denormalizacja, a nie jako niedokładny wynik.|
|[has_infinity](#has_infinity)|Sprawdza, czy typ ma reprezentację nieskończoności dodatniej.|
|[has_quiet_NaN](#has_quiet_nan)|Sprawdza, czy typ ma reprezentację quiet nie jest liczbą (NAN), czyli nonsignaling.|
|[has_signaling_NaN](#has_signaling_nan)|Sprawdza, czy typ ma reprezentację sygnalizowania nie jest liczbą (NAN).|
|[infinity](#infinity)|Reprezentacja do nieskończoności dodatniej dla typu, jeśli jest dostępny.|
|[is_bounded](#is_bounded)|Sprawdza, czy zbiór wartości, które mogą reprezentować typem jest jednak ograniczona.|
|[is_exact](#is_exact)|Sprawdza, czy obliczenia wykonywane w danym typie są wolne od błędów zaokrąglania.|
|[is_iec559](#is_iec559)|Sprawdza, czy typ jest zgodny ze standardami IEC 559.|
|[is_integer](#is_integer)|Sprawdza, czy typ ma reprezentację w postaci liczby całkowitej.|
|[is_modulo](#is_modulo)|Sprawdza, czy typ ma modulo reprezentacji.|
|[is_signed](#is_signed)|Sprawdza, czy typ ma reprezentację podpisem.|
|[is_specialized](#is_specialized)|Sprawdza, czy typ ma jawnej specjalizacji zdefiniowanej w klasie szablonu `numeric_limits`.|
|[lowest](#lowest)|Zwraca najbardziej ujemną wartość skończoną.|
|[max](#max)|Zwraca maksymalną wartość skończoną dla typu.|
|[max_digits10](#max_digits10)|Zwraca liczbę cyfr dziesiętnych, które są wymagane w celu zapewnienia, że dwa odrębne wartości typu mają różne reprezentacje dziesiętną.|
|[max_exponent](#max_exponent)|Zwraca wartość maksymalnego dodatniego wykładnika typu całkowitego typu zmiennoprzecinkowego można przedstawić jako wartość skończoną, gdy została podniesiona do tych możliwości wersji podstawowej podstawy.|
|[max_exponent10](#max_exponent10)|Zwraca wartość maksymalnego dodatniego wykładnika typu całkowitego, który może reprezentować typu zmiennoprzecinkowego jako wartość skończoną, gdy base 10, zostanie zgłoszony do tych możliwości.|
|[min](#min)|Zwraca minimalną wartość znormalizowana dla typu.|
|[min_exponent —](#min_exponent)|Zwraca maksymalną ujemnego wykładnika typu całkowitego typu zmiennoprzecinkowego można przedstawić jako wartość skończoną, gdy została podniesiona do tych możliwości wersji podstawowej podstawy.|
|[min_exponent10](#min_exponent10)|Zwraca maksymalną ujemnego wykładnika typu całkowitego typu zmiennoprzecinkowego można przedstawić jako wartość skończoną, gdy base 10, zostanie zgłoszony do tych możliwości.|
|[quiet_NaN](#quiet_nan)|Zwraca reprezentację quiet nie jest liczbą (NAN) dla typu.|
|[radix](#radix)|Zwraca bazowego typu całkowitego, określane jako podstawy, używane do reprezentacji typu.|
|[round_error](#round_error)|Zwraca maksymalną zaokrąglania błąd dla typu.|
|[round_style](#round_style)|Zwraca wartość, która w tym artykule opisano różne metody wdrażania można wybrać podczas zaokrąglania wartość zmiennoprzecinkowa wartość będącą liczbą całkowitą.|
|[signaling_NaN](#signaling_nan)|Zwraca reprezentację sygnalizowania nie jest liczbą (NAN) dla typu.|
|[tinyness_before](#tinyness_before)|Sprawdza, czy typ można określić, czy wartość jest zbyt mała, aby przedstawić jako wartość znormalizowaną przed jej zaokrąglania.|
|[pułapki](#traps)|Sprawdza, czy generują pułapki, który zgłasza wyjątki arytmetyczne został zaimplementowany dla typu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<limity >

**Namespace:** standardowe

## <a name="denorm_min"></a>  numeric_limits::denorm_min

Zwraca wartość różną od zera najmniejszy nieznormalizowane wartość.

```cpp
static constexpr Type denorm_min() throw();
```

### <a name="return-value"></a>Wartość zwracana

Najmniejsza wartość różną od zera nieznormalizowany.

### <a name="remarks"></a>Uwagi

**double** jest taka sama jak **double** dla kompilatora języka C++.

Funkcja zwraca minimalną wartość dla typu, która jest taka sama jak [min](#min) Jeśli [has_denorm —](#has_denorm) nie jest równa `denorm_present`.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_denorm_min.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The smallest nonzero denormalized value" << endl
        << "for float objects is: "
        << numeric_limits<float>::denorm_min( ) << endl;
   cout << "The smallest nonzero denormalized value" << endl
        << "for double objects is: "
        << numeric_limits<double>::denorm_min( ) << endl;
   cout << "The smallest nonzero denormalized value" << endl
        << "for long double objects is: "
        << numeric_limits<long double>::denorm_min( ) << endl;

   // A smaller value will round to zero
   cout << numeric_limits<float>::denorm_min( )/2 <<endl;
   cout << numeric_limits<double>::denorm_min( )/2 <<endl;
   cout << numeric_limits<long double>::denorm_min( )/2 <<endl;
}
```

```Output
The smallest nonzero denormalized value
for float objects is: 1.4013e-045
The smallest nonzero denormalized value
for double objects is: 4.94066e-324
The smallest nonzero denormalized value
for long double objects is: 4.94066e-324
0
0
0
```

## <a name="digits"></a>  numeric_limits::digits

Zwraca liczbę cyfr podstawy, których typ może reprezentować bez utraty dokładności.

```cpp
static constexpr int digits = 0;
```

### <a name="return-value"></a>Wartość zwracana

Liczba cyfr podstawy, których typ może reprezentować bez utraty dokładności.

### <a name="remarks"></a>Uwagi

Element członkowski przechowuje liczbę cyfr podstawy, reprezentujących przez typ bez zmian, czyli liczbę bitów niż każdego bitu znaku dla typu integer wstępnie zdefiniowanych lub liczbę cyfr mantysy dla wstępnie zdefiniowanego typu zmiennoprzecinkowego.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_digits_min.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << numeric_limits<float>::digits <<endl;
   cout << numeric_limits<double>::digits <<endl;
   cout << numeric_limits<long double>::digits <<endl;
   cout << numeric_limits<int>::digits <<endl;
   cout << numeric_limits<__int64>::digits <<endl;
}
```

```Output
24
53
53
31
63
```

## <a name="digits10"></a>  numeric_limits::digits10

Zwraca liczbę cyfr dziesiętnych, reprezentujących przez typ bez utraty dokładności.

```cpp
static constexpr int digits10 = 0;
```

### <a name="return-value"></a>Wartość zwracana

Liczba cyfr dziesiętnych, reprezentujących przez typ bez utraty dokładności.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_digits10.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << numeric_limits<float>::digits10 <<endl;
   cout << numeric_limits<double>::digits10 <<endl;
   cout << numeric_limits<long double>::digits10 <<endl;
   cout << numeric_limits<int>::digits10 <<endl;
   cout << numeric_limits<__int64>::digits10 <<endl;
   float f = (float)99999999;
   cout.precision ( 10 );
   cout << "The float is; " << f << endl;
}
```

```Output
6
15
15
9
18
The float is; 100000000
```

## <a name="epsilon"></a>  numeric_limits::epsilon

Funkcja zwraca różnicę między 1 a najmniejsza wartość większa niż 1, który jest stałego dla typu danych.

```cpp
static constexpr Type epsilon() throw();
```

### <a name="return-value"></a>Wartość zwracana

Różnica między 1 a to najmniejsza wartość większa niż 1, który jest stałego dla typu danych.

### <a name="remarks"></a>Uwagi

FLT_EPSILON jest wartość typu **float**. `epsilon` Typ jest najmniejsza dodatnia liczba zmiennoprzecinkowa *N* tak, aby *N* + `epsilon` + *N* jest stałego.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_epsilon.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The difference between 1 and the smallest "
        << "value greater than 1" << endl
        << "for float objects is: "
        << numeric_limits<float>::epsilon( ) << endl;
   cout << "The difference between 1 and the smallest "
        << "value greater than 1" << endl
        << "for double objects is: "
        << numeric_limits<double>::epsilon( ) << endl;
   cout << "The difference between 1 and the smallest "
        << "value greater than 1" << endl
        << "for long double objects is: "
        << numeric_limits<long double>::epsilon( ) << endl;
}
```

```Output
The difference between 1 and the smallest value greater than 1
for float objects is: 1.19209e-007
The difference between 1 and the smallest value greater than 1
for double objects is: 2.22045e-016
The difference between 1 and the smallest value greater than 1
for long double objects is: 2.22045e-016
```

## <a name="has_denorm"></a>  numeric_limits::has_denorm

Sprawdza, czy typ umożliwia nieznormalizowane wartości.

```cpp
static constexpr float_denorm_style has_denorm = denorm_absent;
```

### <a name="return-value"></a>Wartość zwracana

Wartość wyliczenia typu **const**`float_denorm_style`oznaczający tego, czy typ dopuszcza wartości nieznormalizowany.

### <a name="remarks"></a>Uwagi

Magazyny elementu członkowskiego `denorm_present` dla typu zmiennoprzecinkowego, który ma być nieznormalizowane wartości skutecznie zmienną liczbę bitów wykładnika.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_has_denorm.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects allow denormalized values: "
        << numeric_limits<float>::has_denorm
        << endl;
   cout << "Whether double objects allow denormalized values: "
        << numeric_limits<double>::has_denorm
        << endl;
   cout << "Whether long int objects allow denormalized values: "
        << numeric_limits<long int>::has_denorm
        << endl;
}
```

```Output
Whether float objects allow denormalized values: 1
Whether double objects allow denormalized values: 1
Whether long int objects allow denormalized values: 0
```

## <a name="has_denorm_loss"></a>  numeric_limits::has_denorm_loss

Sprawdza, czy wykryto utratę dokładności utratę denormalizacja, a nie jako niedokładny wynik.

```cpp
static constexpr bool has_denorm_loss = false;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** wykrycie utraty dokładności utratę denormalizacja; **false** w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Element członkowski przechowuje wartość true dla typu, który określa, czy wartość utracił dokładności, ponieważ przekazaniem wyniku denormalizowane (zbyt mała, aby przedstawić jako wartość znormalizowaną) lub jest niedokładna (nie sam w rezultacie nie podlegają ograniczeń wykładnik zakres i dokładność) opcję z IEC 559 zmiennoprzecinkowych oświadczenia, które mogą wpłynąć na niektóre wyniki.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_has_denorm_loss.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects can detect denormalized loss: "
        << numeric_limits<float>::has_denorm_loss
        << endl;
   cout << "Whether double objects can detect denormalized loss: "
        << numeric_limits<double>::has_denorm_loss
        << endl;
   cout << "Whether long int objects can detect denormalized loss: "
        << numeric_limits<long int>::has_denorm_loss
        << endl;
}
```

```Output
Whether float objects can detect denormalized loss: 1
Whether double objects can detect denormalized loss: 1
Whether long int objects can detect denormalized loss: 0
```

## <a name="has_infinity"></a>  numeric_limits::has_infinity

Sprawdza, czy typ ma reprezentację nieskończoności dodatniej.

```cpp
static constexpr bool has_infinity = false;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli typ ma reprezentację nieskończoności dodatniej; **false** w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Zwraca element członkowski **true** Jeśli [is_iec559 —](#is_iec559) jest **true**.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_has_infinity.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have infinity: "
        << numeric_limits<float>::has_infinity
        << endl;
   cout << "Whether double objects have infinity: "
        << numeric_limits<double>::has_infinity
        << endl;
   cout << "Whether long int objects have infinity: "
        << numeric_limits<long int>::has_infinity
        << endl;
}
```

```Output
Whether float objects have infinity: 1
Whether double objects have infinity: 1
Whether long int objects have infinity: 0
```

## <a name="has_quiet_nan"></a>  numeric_limits::has_quiet_NaN

Sprawdza, czy typ ma reprezentację quiet nie jest liczbą (NAN), czyli nonsignaling.

```cpp
static constexpr bool has_quiet_NaN = false;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli **typu** ma reprezentację cichych NAN; **false** w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ciche NAN jest kodowanie nie jest liczbą, która nie sygnalizują jego obecność w wyrażeniu. Wartość zwracana jest **true** Jeśli [is_iec559 —](#is_iec559) ma wartość true.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_has_quiet_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have quiet_NaN: "
        << numeric_limits<float>::has_quiet_NaN
        << endl;
   cout << "Whether double objects have quiet_NaN: "
        << numeric_limits<double>::has_quiet_NaN
        << endl;
   cout << "Whether long int objects have quiet_NaN: "
        << numeric_limits<long int>::has_quiet_NaN
        << endl;
}
```

```Output
Whether float objects have quiet_NaN: 1
Whether double objects have quiet_NaN: 1
Whether long int objects have quiet_NaN: 0
```

## <a name="has_signaling_nan"></a>  numeric_limits::has_signaling_NaN

Sprawdza, czy typ ma reprezentację sygnalizowania nie jest liczbą (NAN).

```cpp
static constexpr bool has_signaling_NaN = false;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli typ ma reprezentację sygnalizowania NAN; **false** w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Sygnalizowanie NAN jest kodowanie nie jest liczbą, które sygnalizują jego obecność w wyrażeniu. Wartość zwracana jest **true** Jeśli [is_iec559 —](#is_iec559) ma wartość true.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_has_signaling_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have a signaling_NaN: "
        << numeric_limits<float>::has_signaling_NaN
        << endl;
   cout << "Whether double objects have a signaling_NaN: "
        << numeric_limits<double>::has_signaling_NaN
        << endl;
   cout << "Whether long int objects have a signaling_NaN: "
        << numeric_limits<long int>::has_signaling_NaN
        << endl;
}
```

```Output
Whether float objects have a signaling_NaN: 1
Whether double objects have a signaling_NaN: 1
Whether long int objects have a signaling_NaN: 0
```

## <a name="infinity"></a>  numeric_limits::infinity

Reprezentacja nieskończoności dodatniej dla typu, jeśli jest dostępny.

```cpp
static constexpr Type infinity() throw();
```

### <a name="return-value"></a>Wartość zwracana

Reprezentacja nieskończoności dodatniej dla typu, jeśli jest dostępny.

### <a name="remarks"></a>Uwagi

Wartość zwracana ma znaczenie tylko wtedy, gdy [has_infinity —](#has_infinity) jest **true**.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_infinity.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << numeric_limits<float>::has_infinity <<endl;
   cout << numeric_limits<double>::has_infinity<<endl;
   cout << numeric_limits<long double>::has_infinity <<endl;
   cout << numeric_limits<int>::has_infinity <<endl;
   cout << numeric_limits<__int64>::has_infinity <<endl;

   cout << "The representation of infinity for type float is: "
        << numeric_limits<float>::infinity( ) <<endl;
   cout << "The representation of infinity for type double is: "
        << numeric_limits<double>::infinity( ) <<endl;
   cout << "The representation of infinity for type long double is: "
        << numeric_limits<long double>::infinity( ) <<endl;
}
```

```Output
1
1
1
0
0
The representation of infinity for type float is: inf
The representation of infinity for type double is: inf
The representation of infinity for type long double is: inf
```

## <a name="is_bounded"></a>  numeric_limits::is_bounded

Sprawdza, czy zbiór wartości, które mogą reprezentować typem jest jednak ograniczona.

```cpp
static constexpr bool is_bounded = false;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli typ ma ograniczony zestaw reprezentowanych wartości. **false** w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Wszystkie wstępnie zdefiniowanych typów mają ograniczony zestaw reprezentowanych wartości i zwracają **true**.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_is_bounded.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have bounded set "
        << "of representable values: "
        << numeric_limits<float>::is_bounded
        << endl;
   cout << "Whether double objects have bounded set "
        << "of representable values: "
        << numeric_limits<double>::is_bounded
        << endl;
   cout << "Whether long int objects have bounded set "
        << "of representable values: "
        << numeric_limits<long int>::is_bounded
        << endl;
   cout << "Whether unsigned char objects have bounded set "
        << "of representable values: "
        << numeric_limits<unsigned char>::is_bounded
        << endl;
}
```

```Output
Whether float objects have bounded set of representable values: 1
Whether double objects have bounded set of representable values: 1
Whether long int objects have bounded set of representable values: 1
Whether unsigned char objects have bounded set of representable values: 1
```

## <a name="is_exact"></a>  numeric_limits::is_exact

Sprawdza, czy obliczenia wykonywane w danym typie są wolne od błędów zaokrąglania.

```cpp
static constexpr bool is_exact = false;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** w przypadku obliczeń wolny od błędów; zaokrąglania **false** w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Wszystkie wstępnie zdefiniowane całkowitoliczbowe mają dokładnie reprezentacji podanie ich wartości i zwracają **false**. Reprezentacja notację stałoprzecinkową lub wymierne jest również uważana za dokładne odwzorowanie liczby zmiennoprzecinkowej jest jednak nie.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_is_exact.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<float>::is_exact
        << endl;
   cout << "Whether double objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<double>::is_exact
        << endl;
   cout << "Whether long int objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<long int>::is_exact
        << endl;
   cout << "Whether unsigned char objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<unsigned char>::is_exact
        << endl;
}
```

```Output
Whether float objects have calculations free of rounding errors: 0
Whether double objects have calculations free of rounding errors: 0
Whether long int objects have calculations free of rounding errors: 1
Whether unsigned char objects have calculations free of rounding errors: 1
```

## <a name="is_iec559"></a>  numeric_limits::is_iec559

Sprawdza, czy typ jest zgodny ze standardami IEC 559.

```cpp
static constexpr bool is_iec559 = false;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli typ jest zgodny ze standardami IEC 559; **false** w przeciwnym razie.

### <a name="remarks"></a>Uwagi

IEC 559 jest międzynarodową normą dotyczącą reprezentująca różne wartości zmiennoprzecinkowe i jest również znany jako IEEE 754 w USA.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_is_iec559.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects conform to iec559 standards: "
        << numeric_limits<float>::is_iec559
        << endl;
   cout << "Whether double objects conform to iec559 standards: "
        << numeric_limits<double>::is_iec559
        << endl;
   cout << "Whether int objects conform to iec559 standards: "
        << numeric_limits<int>::is_iec559
        << endl;
   cout << "Whether unsigned char objects conform to iec559 standards: "
        << numeric_limits<unsigned char>::is_iec559
        << endl;
}
```

```Output
Whether float objects conform to iec559 standards: 1
Whether double objects conform to iec559 standards: 1
Whether int objects conform to iec559 standards: 0
Whether unsigned char objects conform to iec559 standards: 0
```

## <a name="is_integer"></a>  numeric_limits::is_integer

Sprawdza, czy typ ma reprezentację w postaci liczby całkowitej.

```cpp
static constexpr bool is_integer = false;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli typ ma reprezentację w postaci liczby całkowitej; **false** w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Wszystkie typy wstępnie zdefiniowanej liczby całkowitej mają reprezentację w postaci liczby całkowitej.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_is_integer.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have an integral representation: "
        << numeric_limits<float>::is_integer
        << endl;
   cout << "Whether double objects have an integral representation: "
        << numeric_limits<double>::is_integer
        << endl;
   cout << "Whether int objects have an integral representation: "
        << numeric_limits<int>::is_integer
        << endl;
   cout << "Whether unsigned char objects have an integral representation: "
        << numeric_limits<unsigned char>::is_integer
        << endl;
}
```

```Output
Whether float objects have an integral representation: 0
Whether double objects have an integral representation: 0
Whether int objects have an integral representation: 1
Whether unsigned char objects have an integral representation: 1
```

## <a name="is_modulo"></a>  numeric_limits::is_modulo

Sprawdza, czy **typu** ma modulo reprezentacji.

```cpp
static constexpr bool is_modulo = false;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli typ ma modulo reprezentacji; **false** w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Modulo reprezentacja jest reprezentacja gdzie wszystkie wyniki są zmniejszone modulo jakąś wartość. Wszystkie typy wstępnie zdefiniowanej liczby całkowitej bez znaku mają modulo reprezentacji.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_is_modulo.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have a modulo representation: "
        << numeric_limits<float>::is_modulo
        << endl;
   cout << "Whether double objects have a modulo representation: "
        << numeric_limits<double>::is_modulo
        << endl;
   cout << "Whether signed char objects have a modulo representation: "
        << numeric_limits<signed char>::is_modulo
        << endl;
   cout << "Whether unsigned char objects have a modulo representation: "
        << numeric_limits<unsigned char>::is_modulo
        << endl;
}
```

```Output
Whether float objects have a modulo representation: 0
Whether double objects have a modulo representation: 0
Whether signed char objects have a modulo representation: 1
Whether unsigned char objects have a modulo representation: 1
```

## <a name="is_signed"></a>  numeric_limits::is_signed

Sprawdza, czy typ ma reprezentację podpisem.

```cpp
static constexpr bool is_signed = false;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli typ ma reprezentację podpisany; **false** w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Element członkowski przechowuje wartość true dla typu, który został podpisany reprezentacji w przypadku wszystkich wstępnie zdefiniowanych typów zmiennoprzecinkowych i podpisane liczby całkowitej.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_is_signaled.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have a signed representation: "
        << numeric_limits<float>::is_signed
        << endl;
   cout << "Whether double objects have a signed representation: "
        << numeric_limits<double>::is_signed
        << endl;
   cout << "Whether signed char objects have a signed representation: "
        << numeric_limits<signed char>::is_signed
        << endl;
   cout << "Whether unsigned char objects have a signed representation: "
        << numeric_limits<unsigned char>::is_signed
        << endl;
}
```

```Output
Whether float objects have a signed representation: 1
Whether double objects have a signed representation: 1
Whether signed char objects have a signed representation: 1
Whether unsigned char objects have a signed representation: 0
```

## <a name="is_specialized"></a>  numeric_limits::is_specialized

Sprawdza, czy typ ma jawnej specjalizacji zdefiniowanej w klasie szablonu `numeric_limits`.

```cpp
static constexpr bool is_specialized = false;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli typ ma jawnej specjalizacji zdefiniowanej w klasie szablonu; **false** w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Wszystkie typy skalarne niż wskaźniki mają jawną specjalizacją zdefiniowane dla szablonu klasy `numeric_limits`.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_is_specialized.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<float>::is_specialized
        << endl;
   cout << "Whether float* objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<float*>::is_specialized
        << endl;
   cout << "Whether int objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<int>::is_specialized
        << endl;
   cout << "Whether int* objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<int*>::is_specialized
        << endl;
}
```

```Output
Whether float objects have an explicit specialization in the class: 1
Whether float* objects have an explicit specialization in the class: 0
Whether int objects have an explicit specialization in the class: 1
Whether int* objects have an explicit specialization in the class: 0
```

## <a name="lowest"></a>  numeric_limits::LOWEST

Zwraca najbardziej ujemną wartość skończoną.

```cpp
static constexpr Type lowest() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca najbardziej ujemną wartość skończoną.

### <a name="remarks"></a>Uwagi

Zwraca najbardziej ujemną wartość skończoną dla typu (zazwyczaj `min()` dla typów całkowitoliczbowych i `-max()` dla typów zmiennopozycyjnych). Wartość zwracana ma znaczenie przypadku `is_bounded` jest **true**.

## <a name="max"></a>  numeric_limits::Max

Zwraca maksymalną wartość skończoną dla typu.

```cpp
static constexpr Type max() throw();
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna wartość skończoną dla typu.

### <a name="remarks"></a>Uwagi

Maksymalna wartość skończoną jest INT_MAX dla typu **int** i FLT_MAX dla typu **float**. Wartość zwracana ma znaczenie przypadku [is_bounded](#is_bounded) jest **true**.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_max.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main() {
   cout << "The maximum value for type float is:  "
        << numeric_limits<float>::max( )
        << endl;
   cout << "The maximum value for type double is:  "
        << numeric_limits<double>::max( )
        << endl;
   cout << "The maximum value for type int is:  "
        << numeric_limits<int>::max( )
        << endl;
   cout << "The maximum value for type short int is:  "
        << numeric_limits<short int>::max( )
        << endl;
}
```

## <a name="max_digits10"></a>  numeric_limits::max_digits10

Zwraca liczbę cyfr dziesiętnych, które są wymagane, aby upewnić się, że dwa odrębne wartości typu mają różne reprezentacje dziesiętną.

```cpp
static constexpr int max_digits10 = 0;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę miejsc dziesiętnych, które są wymagane, aby upewnić się, że dwa odrębne wartości typu mają różne reprezentacje dziesiętną.

### <a name="remarks"></a>Uwagi

Element członkowski przechowuje liczbę cyfr dziesiętnych, wymagane, aby upewnić się, że dwa odrębne wartości typu mają różne reprezentacje dziesiętną.

## <a name="max_exponent"></a>  numeric_limits::max_exponent

Zwraca wartość maksymalnego dodatniego wykładnika typu całkowitego typu zmiennoprzecinkowego można przedstawić jako wartość skończoną, gdy została podniesiona do tych możliwości wersji podstawowej podstawy.

```cpp
static constexpr int max_exponent = 0;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalny całkowity na podstawie podstawy wykładnik reprezentowanych przez typ.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego, zwracany jest istotny tylko dla typów zmiennoprzecinkowych. `max_exponent` Jest wartość typu FLT_MAX_EXP **float**.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_max_exponent.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The maximum radix-based exponent for type float is:  "
        << numeric_limits<float>::max_exponent
        << endl;
   cout << "The maximum radix-based exponent for type double is:  "
        << numeric_limits<double>::max_exponent
        << endl;
   cout << "The maximum radix-based exponent for type long double is:  "
        << numeric_limits<long double>::max_exponent
        << endl;
}
```

```Output
The maximum radix-based exponent for type float is:  128
The maximum radix-based exponent for type double is:  1024
The maximum radix-based exponent for type long double is:  1024
```

## <a name="max_exponent10"></a>  numeric_limits::max_exponent10

Zwraca wartość maksymalnego dodatniego wykładnika typu całkowitego, który może reprezentować typu zmiennoprzecinkowego jako wartość skończoną, gdy base 10, zostanie zgłoszony do tych możliwości.

```cpp
static constexpr int max_exponent10 = 0;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalny całkowity o podstawie 10 wykładnik reprezentowanych przez typ.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego, zwracany jest istotny tylko dla typów zmiennoprzecinkowych. `max_exponent` Jest wartość typu FLT_MAX_10 **float**.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_max_exponent10.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The maximum base 10 exponent for type float is:  "
           << numeric_limits<float>::max_exponent10
           << endl;
   cout << "The maximum base 10 exponent for type double is:  "
           << numeric_limits<double>::max_exponent10
           << endl;
   cout << "The maximum base 10 exponent for type long double is:  "
           << numeric_limits<long double>::max_exponent10
           << endl;
}
```

```Output
The maximum base 10 exponent for type float is:  38
The maximum base 10 exponent for type double is:  308
The maximum base 10 exponent for type long double is:  308
```

## <a name="min"></a>  numeric_limits::min

Zwraca minimalną wartość znormalizowana dla typu.

```cpp
static constexpr Type min() throw();
```

### <a name="return-value"></a>Wartość zwracana

Minimalna wartość znormalizowana dla typu.

### <a name="remarks"></a>Uwagi

Minimalna wartość znormalizowana to INT_MIN dla typu **int** i FLT_MIN dla typu **float**. Wartość zwracana ma znaczenie przypadku [is_bounded](#is_bounded) jest **true** lub jeśli [is_signed —](#is_signed) jest **false**.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_min.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The minimum value for type float is:  "
        << numeric_limits<float>::min( )
        << endl;
   cout << "The minimum value for type double is:  "
        << numeric_limits<double>::min( )
        << endl;
   cout << "The minimum value for type int is:  "
        << numeric_limits<int>::min( )
        << endl;
   cout << "The minimum value for type short int is:  "
        << numeric_limits<short int>::min( )
        << endl;
}
```

```Output
The minimum value for type float is:  1.17549e-038
The minimum value for type double is:  2.22507e-308
The minimum value for type int is:  -2147483648
The minimum value for type short int is:  -32768
```

## <a name="min_exponent"></a>  numeric_limits::min_exponent

Zwraca maksymalną ujemnego wykładnika typu całkowitego typu zmiennoprzecinkowego można przedstawić jako wartość skończoną, gdy została podniesiona do tych możliwości wersji podstawowej podstawy.

```cpp
static constexpr int min_exponent = 0;
```

### <a name="return-value"></a>Wartość zwracana

Minimalna typu całkowitego na podstawie podstawy wykładnik reprezentowanych przez typ.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego ma znaczenie tylko dla typów zmiennoprzecinkowych. `min_exponent` Jest wartość typu FLT_MIN_EXP **float**.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_min_exponent.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The minimum radix-based exponent for type float is:  "
        << numeric_limits<float>::min_exponent
        << endl;
   cout << "The minimum radix-based exponent for type double is:  "
        << numeric_limits<double>::min_exponent
        << endl;
   cout << "The minimum radix-based exponent for type long double is:  "
         << numeric_limits<long double>::min_exponent
        << endl;
}
```

```Output
The minimum radix-based exponent for type float is:  -125
The minimum radix-based exponent for type double is:  -1021
The minimum radix-based exponent for type long double is:  -1021
```

## <a name="min_exponent10"></a>  numeric_limits::min_exponent10

Zwraca maksymalną ujemnego wykładnika typu całkowitego typu zmiennoprzecinkowego można przedstawić jako wartość skończoną, gdy base 10, zostanie zgłoszony do tych możliwości.

```cpp
static constexpr int min_exponent10 = 0;
```

### <a name="return-value"></a>Wartość zwracana

Minimum całkowitych o podstawie 10 wykładnik reprezentowanych przez typ.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego ma znaczenie tylko dla typów zmiennoprzecinkowych. `min_exponent10` Jest wartość typu FLT_MIN_10_EXP **float**.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_min_exponent10.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The minimum base 10 exponent for type float is:  "
        << numeric_limits<float>::min_exponent10
        << endl;
   cout << "The minimum base 10 exponent for type double is:  "
        << numeric_limits<double>::min_exponent10
        << endl;
   cout << "The minimum base 10 exponent for type long double is:  "
        << numeric_limits<long double>::min_exponent10
        << endl;
}
```

```Output
The minimum base 10 exponent for type float is:  -37
The minimum base 10 exponent for type double is:  -307
The minimum base 10 exponent for type long double is:  -307
```

## <a name="quiet_nan"></a>  numeric_limits::quiet_NaN

Zwraca reprezentację quiet nie jest liczbą (NAN) dla typu.

```cpp
static constexpr Type quiet_NaN() throw();
```

### <a name="return-value"></a>Wartość zwracana

Reprezentacja cichych NAN dla typu.

### <a name="remarks"></a>Uwagi

Wartość zwracana ma znaczenie tylko wtedy, gdy [has_quiet_nan —](#has_quiet_nan) jest **true**.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_quiet_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The quiet NaN for type float is:  "
        << numeric_limits<float>::quiet_NaN( )
        << endl;
   cout << "The quiet NaN for type int is:  "
        << numeric_limits<int>::quiet_NaN( )
        << endl;
   cout << "The quiet NaN for type long double is:  "
        << numeric_limits<long double>::quiet_NaN( )
        << endl;
}
```

```Output
The quiet NaN for type float is:  1.#QNAN
The quiet NaN for type int is:  0
The quiet NaN for type long double is:  1.#QNAN
```

## <a name="radix"></a>  numeric_limits::radix

Zwraca bazowego typu całkowitego, określane jako podstawy, używane do reprezentacji typu.

```cpp
static constexpr int radix = 0;
```

### <a name="return-value"></a>Wartość zwracana

Całkowite podstawa reprezentacji typu.

### <a name="remarks"></a>Uwagi

Podstawowa to 2, w przypadku typów całkowitych wstępnie zdefiniowanych i podstawowa, do którego jest wywoływane wykładnik lub FLT_RADIX, wstępnie zdefiniowanych typów zmiennoprzecinkowych.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_radix.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The base for type float is:  "
        << numeric_limits<float>::radix
        << endl;
   cout << "The base for type int is:  "
        << numeric_limits<int>::radix
        << endl;
   cout << "The base for type long double is:  "
        << numeric_limits<long double>::radix
        << endl;
}
```

```Output
The base for type float is:  2
The base for type int is:  2
The base for type long double is:  2
```

## <a name="round_error"></a>  numeric_limits::round_error

Zwraca maksymalną zaokrąglania błąd dla typu.

```cpp
static constexpr Type round_error() throw();
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna zaokrąglania błąd dla typu.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_round_error.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The maximum rounding error for type float is:  "
        << numeric_limits<float>::round_error( )
        << endl;
   cout << "The maximum rounding error for type int is:  "
        << numeric_limits<int>::round_error( )
        << endl;
   cout << "The maximum rounding error for type long double is:  "
        << numeric_limits<long double>::round_error( )
        << endl;
}
```

```Output
The maximum rounding error for type float is:  0.5
The maximum rounding error for type int is:  0
The maximum rounding error for type long double is:  0.5
```

## <a name="round_style"></a>  numeric_limits::round_style

Zwraca wartość, która w tym artykule opisano różne metody wdrażania można wybrać podczas zaokrąglania wartość zmiennoprzecinkowa wartość będącą liczbą całkowitą.

```cpp
static constexpr float_round_style round_style = round_toward_zero;
```

### <a name="return-value"></a>Wartość zwracana

Wartość z zakresu od `float_round_style` stylu wyliczenie opisujące zaokrąglania.

### <a name="remarks"></a>Uwagi

Element członkowski przechowuje wartość, która w tym artykule opisano różne metody wdrażania można wybrać podczas zaokrąglania wartość zmiennoprzecinkowa wartość będącą liczbą całkowitą.

Round stylu jest trudne, kodowane w tej implementacji, nawet po uruchomieniu programu przy użyciu innego trybu zaokrąglania, ta wartość nie zmienia się.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_round_style.cpp
// compile with: /EHsc
#include <iostream>
#include <float.h>
#include <limits>

using namespace std;

int main( )
{
   cout << "The rounding style for a double type is: "
        << numeric_limits<double>::round_style << endl;
   _controlfp_s(NULL,_RC_DOWN,_MCW_RC );
   cout << "The rounding style for a double type is now: "
        << numeric_limits<double>::round_style << endl;
   cout << "The rounding style for an int type is: "
        << numeric_limits<int>::round_style << endl;
}
```

```Output
The rounding style for a double type is: 1
The rounding style for a double type is now: 1
The rounding style for an int type is: 0
```

## <a name="signaling_nan"></a>  numeric_limits::signaling_NaN

Zwraca reprezentację sygnalizowania nie jest liczbą (NAN) dla typu.

```cpp
static constexpr Type signaling_NaN() throw();
```

### <a name="return-value"></a>Wartość zwracana

Reprezentację sygnalizowania NAN dla typu.

### <a name="remarks"></a>Uwagi

Wartość zwracana ma znaczenie tylko wtedy, gdy [has_signaling_nan —](#has_signaling_nan) jest **true**.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_signaling_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The signaling NaN for type float is:  "
        << numeric_limits<float>::signaling_NaN( )
        << endl;
   cout << "The signaling NaN for type int is:  "
        << numeric_limits<int>::signaling_NaN( )
        << endl;
   cout << "The signaling NaN for type long double is:  "
        << numeric_limits<long double>::signaling_NaN( )
        << endl;
}
```

## <a name="tinyness_before"></a>  numeric_limits::tinyness_before

Sprawdza, czy typ można określić, czy wartość jest zbyt mała, aby przedstawić jako wartość znormalizowaną przed jej zaokrąglania.

```cpp
static constexpr bool tinyness_before = false;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli typ może wykryć niewielki rozmiar wartości przed zaokrąglania; **false** Jeśli jest ona nieosiągalna.

### <a name="remarks"></a>Uwagi

Typy, które mogą wykrywać tinyness zostały opcją przy użyciu reprezentacji zmiennoprzecinkowych IEC 559, a jego implementacja może mieć wpływ na niektóre wyniki.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_tinyness_before.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float types can detect tinyness before rounding: "
        << numeric_limits<float>::tinyness_before
        << endl;
   cout << "Whether double types can detect tinyness before rounding: "
        << numeric_limits<double>::tinyness_before
        << endl;
   cout << "Whether long int types can detect tinyness before rounding: "
        << numeric_limits<long int>::tinyness_before
        << endl;
   cout << "Whether unsigned char types can detect tinyness before rounding: "
        << numeric_limits<unsigned char>::tinyness_before
        << endl;
}
```

```Output
Whether float types can detect tinyness before rounding: 1
Whether double types can detect tinyness before rounding: 1
Whether long int types can detect tinyness before rounding: 0
Whether unsigned char types can detect tinyness before rounding: 0
```

## <a name="traps"></a>  numeric_limits::Traps

Sprawdza, czy generują pułapki, który zgłasza wyjątki arytmetyczne został zaimplementowany dla typu.

```cpp
static constexpr bool traps = false;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wyłapywanie został zaimplementowany dla tego typu; **false** Jeśli tak nie jest.

### <a name="example"></a>Przykład

```cpp
// numeric_limits_traps.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float types have implemented trapping: "
        << numeric_limits<float>::traps
        << endl;
   cout << "Whether double types have implemented trapping: "
        << numeric_limits<double>::traps
        << endl;
   cout << "Whether long int types have implemented trapping: "
        << numeric_limits<long int>::traps
        << endl;
   cout << "Whether unsigned char types have implemented trapping: "
        << numeric_limits<unsigned char>::traps
        << endl;
}
```

```Output
Whether float types have implemented trapping: 1
Whether double types have implemented trapping: 1
Whether long int types have implemented trapping: 0
Whether unsigned char types have implemented trapping: 0
```

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
