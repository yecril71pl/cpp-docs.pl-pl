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
ms.openlocfilehash: eb2ee9bc6bc887ff6739c3da1bf2566dbdcbc016
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830686"
---
# <a name="numeric_limits-class"></a>numeric_limits — Klasa

Szablon klasy opisuje arytmetyczne właściwości wbudowanych typów liczbowych.

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
    class numeric_limits
```

### <a name="parameters"></a>Parametry

*Wprowadź*\
Typ danych elementu podstawowego, którego właściwości są testowane lub są badane lub ustawiane. *Typ* może być również zadeklarowany **`const`** , **`volatile`** , lub **`const volatile`** .

## <a name="remarks"></a>Uwagi

Nagłówek definiuje jawne specjalizacje dla typów,,,,,,,,,, **`wchar_t`** **`bool`** **`char`** **`signed char`** **`unsigned char`** **`short`** **`unsigned short`** **`int`** **`unsigned int`** **`long`** **`unsigned long`** ,,, **`float`** **`double`** ,, **`long double`** **`long long`** **`unsigned long long`** , **`char16_t`** i **`char32_t`** . Dla tych jawnych specjalizacji element członkowski [numeric_limits:: is_specialized](#is_specialized) jest **`true`** , a wszystkie odpowiednie elementy członkowskie mają znaczące wartości. Program może podawać dodatkowe jawne specjalizacje. Większość funkcji członkowskich klasy opisują lub mogą testować możliwe implementacje **`float`** .

W przypadku dowolnej specjalizacji żaden element członkowski nie ma znaczących wartości. Obiekt elementu członkowskiego, który nie ma zrozumiałej wartości, przechowuje zero (lub **`false`** ) i funkcję członkowską, która nie zwraca znaczących zwracanych wartości `Type(0)` .

## <a name="static-functions-and-constants"></a>Statyczne funkcje i stałe

|Nazwa|Opis|
|-|-|
|[denorm_min](#denorm_min)|Zwraca najmniejszą niezerową wartość nieznormalizowaną.|
|[cyfry](#digits)|Zwraca liczbę podstawy cyfr, które typ może reprezentować bez utraty dokładności.|
|[digits10](#digits10)|Zwraca liczbę cyfr dziesiętnych, które typ może reprezentować bez utraty dokładności.|
|[Epsilon](#epsilon)|Zwraca różnicę z przedziału od 1 do najmniejszej wartości większej niż 1, którą może reprezentować typ danych.|
|[has_denorm](#has_denorm)|Testuje, czy typ zezwala na nieznormalizowane wartości.|
|[has_denorm_loss](#has_denorm_loss)|Testuje, czy ubytek dokładności został wykryty jako ubytek denormalizacji, a nie jako wynik niedokładny.|
|[has_infinity](#has_infinity)|Testuje, czy typ ma reprezentację dla nieskończoności dodatniej.|
|[has_quiet_NaN](#has_quiet_nan)|Testuje, czy typ ma reprezentację dla cichej nie liczby (NAN), która nie jest sygnalizująca.|
|[has_signaling_NaN](#has_signaling_nan)|Testuje, czy typ ma reprezentację do sygnalizowania nie liczbą (NAN).|
|[nieskończoność](#infinity)|Reprezentacja dla dodatniej nieskończoności dla typu, jeśli jest dostępna.|
|[is_bounded](#is_bounded)|Testuje, czy zestaw wartości, które może reprezentować, jest ograniczony.|
|[is_exact](#is_exact)|Testuje, czy obliczenia wykonywane na typie są wolne od błędów zaokrąglania.|
|[is_iec559](#is_iec559)|Testuje, czy typ jest zgodny ze standardami IEC 559.|
|[is_integer](#is_integer)|Testuje, czy typ ma reprezentację liczb całkowitych.|
|[is_modulo](#is_modulo)|Testuje, czy typ ma reprezentację modulo.|
|[is_signed](#is_signed)|Testuje, czy typ ma podpisaną reprezentację.|
|[is_specialized](#is_specialized)|Testuje, czy typ ma jawną specjalizację zdefiniowaną w szablonie klasy `numeric_limits` .|
|[okreolon](#lowest)|Zwraca najbardziej ujemną wartość skończoną.|
|[max](#max)|Zwraca maksymalną skończoną wartość dla typu.|
|[max_digits10](#max_digits10)|Zwraca liczbę cyfr dziesiętnych wymaganych do zapewnienia, że dwie odrębne wartości typu mają odrębne reprezentacje dziesiętne.|
|[max_exponent](#max_exponent)|Zwraca maksymalną dodatnią wartość wykładnika całkowitą, którą typ zmiennoprzecinkowy może reprezentować jako skończone wartości, gdy podstawa podstawy jest podnoszona do tej potęgi.|
|[max_exponent10](#max_exponent10)|Zwraca maksymalną dodatnią wartość wykładnika całkowitą, którą typ zmiennoprzecinkowy może reprezentować jako skończone wartości, gdy baza danych jest podnoszona do tej potęgi.|
|[min](#min)|Zwraca minimalną znormalizowaną wartość dla typu.|
|[min_exponent](#min_exponent)|Zwraca maksymalny całkowity ujemny wykładnik, który typ zmiennoprzecinkowy może reprezentować jako skończoną wartość, gdy baza podstawy jest podniesiona do tej potęgi.|
|[min_exponent10](#min_exponent10)|Zwraca maksymalny całkowity ujemny wykładnik, który typ zmiennoprzecinkowy może reprezentować jako skończoną wartość, gdy baza danych jest podnoszona do tej potęgi.|
|[quiet_NaN](#quiet_nan)|Zwraca reprezentację wartości typu quiet nie jest liczbą (NAN) dla tego elementu.|
|[podstawy](#radix)|Zwraca część całkowitą, która jest określana jako podstawy, używana do reprezentowania typu.|
|[round_error](#round_error)|Zwraca maksymalny błąd zaokrąglenia typu.|
|[round_style](#round_style)|Zwraca wartość opisującą różne metody, które można wybrać, aby zaokrąglić wartość zmiennoprzecinkową do wartości całkowitej.|
|[signaling_NaN](#signaling_nan)|Zwraca reprezentację sygnalizującego nie jest liczbą (NAN) dla tego typu.|
|[tinyness_before](#tinyness_before)|Testuje, czy typ może określić, że wartość jest zbyt mała, aby reprezentować jako znormalizowaną wartość przed jej zaokrągleniem.|
|[pułapek](#traps)|Testuje, czy zalewkowanie raportów na wyjątkach arytmetycznych jest implementowane dla typu.|

### <a name="denorm_min"></a><a name="denorm_min"></a> denorm_min

Zwraca najmniejszą niezerową wartość nieznormalizowaną.

```cpp
static constexpr Type denorm_min() throw();
```

#### <a name="return-value"></a>Wartość zwracana

Najmniejsza nieznormalizowana wartość niezerową.

#### <a name="remarks"></a>Uwagi

**`long double`** jest taka sama jak **`double`** w przypadku kompilatora języka C++.

Funkcja zwraca wartość minimalną dla typu, która jest taka sama jak [minimalna](#min) , jeśli [has_denorm](#has_denorm) nie jest równa `denorm_present` .

#### <a name="example"></a>Przykład

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

### <a name="digits"></a><a name="digits"></a> cyfr

Zwraca liczbę podstawy cyfr, które typ może reprezentować bez utraty dokładności.

```cpp
static constexpr int digits = 0;
```

#### <a name="return-value"></a>Wartość zwracana

Liczba podstawy, które typ może reprezentować bez utraty dokładności.

#### <a name="remarks"></a>Uwagi

Składowa przechowuje liczbę podstawy cyfr, które typ może reprezentować bez zmiany, czyli liczbę bitów innych niż dowolny bit znaku dla wstępnie zdefiniowanego typu Integer lub liczbę cyfr mantysy dla wstępnie zdefiniowanego typu zmiennoprzecinkowego.

#### <a name="example"></a>Przykład

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

### <a name="digits10"></a><a name="digits10"></a> digits10

Zwraca liczbę cyfr dziesiętnych, które typ może reprezentować bez utraty dokładności.

```cpp
static constexpr int digits10 = 0;
```

#### <a name="return-value"></a>Wartość zwracana

Liczba cyfr dziesiętnych, które typ może reprezentować bez utraty dokładności.

#### <a name="example"></a>Przykład

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

### <a name="epsilon"></a><a name="epsilon"></a> Epsilon

Funkcja zwraca różnicę z zakresu od 1 do najmniejszej wartości większej niż 1, która jest zaprezentowana dla typu danych.

```cpp
static constexpr Type epsilon() throw();
```

#### <a name="return-value"></a>Wartość zwracana

Różnica między 1 a najmniejszą wartością większą niż 1, która jest zaprezentowania dla typu danych.

#### <a name="remarks"></a>Uwagi

Wartość jest FLT_EPSILON dla typu **`float`** . `epsilon`dla typu jest najmniejsza dodatnia liczba zmiennoprzecinkowa *n* , co oznacza, że *n*  +  `epsilon`  +  *n* jest możliwe do zaprezentowania.

#### <a name="example"></a>Przykład

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

### <a name="has_denorm"></a><a name="has_denorm"></a> has_denorm

Testuje, czy typ zezwala na nieznormalizowane wartości.

```cpp
static constexpr float_denorm_style has_denorm = denorm_absent;
```

#### <a name="return-value"></a>Wartość zwracana

Wartość wyliczenia typu `const float_denorm_style` wskazująca, czy typ zezwala na nieznormalizowane wartości.

#### <a name="remarks"></a>Uwagi

Elementy członkowskie są przechowywane `denorm_present` dla typu zmiennoprzecinkowego, który ma nieznormalizowane wartości, efektywnie zmienną liczbę bitów wykładnika.

#### <a name="example"></a>Przykład

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

### <a name="has_denorm_loss"></a><a name="has_denorm_loss"></a> has_denorm_loss

Testuje, czy ubytek dokładności został wykryty jako ubytek denormalizacji, a nie jako wynik niedokładny.

```cpp
static constexpr bool has_denorm_loss = false;
```

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli utrata dokładności zostanie wykryta jako ubytek, w **`false`** przeciwnym razie.

#### <a name="remarks"></a>Uwagi

Element członkowski zapisuje wartość true dla typu, który określa, czy wartość utraciła dokładność, ponieważ jest ona dostarczana jako wynik nieznormalizowany (za mały, aby reprezentować jako znormalizowana wartość) lub ponieważ jest ona niedokładna (nie jest taka sama jak w przypadku ograniczeń zakresu i dokładności wykładniki), opcja z replikami zmiennoprzecinkowymi IEC 559, które mogą mieć wpływ na niektóre wyniki

#### <a name="example"></a>Przykład

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

### <a name="has_infinity"></a><a name="has_infinity"></a> has_infinity

Testuje, czy typ ma reprezentację dla nieskończoności dodatniej.

```cpp
static constexpr bool has_infinity = false;
```

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli typ ma reprezentację dla nieskończoności dodatniej; w **`false`** przeciwnym razie.

#### <a name="remarks"></a>Uwagi

Element członkowski zwraca wartość, **`true`** jeśli [is_iec559](#is_iec559) **`true`** .

#### <a name="example"></a>Przykład

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

### <a name="has_quiet_nan"></a><a name="has_quiet_nan"></a> has_quiet_NaN

Testuje, czy typ ma reprezentację dla cichej nie liczby (NAN), która nie jest sygnalizująca.

```cpp
static constexpr bool has_quiet_NaN = false;
```

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli **Typ** ma reprezentację dla cichego NaN; w **`false`** przeciwnym razie.

#### <a name="remarks"></a>Uwagi

Cichy NAN jest kodowaniem nie jest liczbą, która nie sygnalizuje obecności w wyrażeniu. Wartość zwracana jest **`true`** jeśli [is_iec559](#is_iec559) ma wartość true.

#### <a name="example"></a>Przykład

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

### <a name="has_signaling_nan"></a><a name="has_signaling_nan"></a> has_signaling_NaN

Testuje, czy typ ma reprezentację do sygnalizowania nie liczbą (NAN).

```cpp
static constexpr bool has_signaling_NaN = false;
```

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli typ ma reprezentację dla wartości NAN sygnalizującej; w **`false`** przeciwnym razie.

#### <a name="remarks"></a>Uwagi

Sygnalizowanie NAN jest kodowaniem niebędącym liczbą, która sygnalizuje swoją obecność w wyrażeniu. Wartość zwracana jest **`true`** jeśli [is_iec559](#is_iec559) ma wartość true.

#### <a name="example"></a>Przykład

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

### <a name="infinity"></a><a name="infinity"></a> nieskończoność

Reprezentacja dodatniej nieskończoności dla typu, jeśli jest dostępna.

```cpp
static constexpr Type infinity() throw();
```

#### <a name="return-value"></a>Wartość zwracana

Reprezentacja dodatniej nieskończoności dla typu, jeśli jest dostępna.

#### <a name="remarks"></a>Uwagi

Wartość zwracana ma znaczenie tylko wtedy, gdy [has_infinity](#has_infinity) jest **`true`** .

#### <a name="example"></a>Przykład

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

### <a name="is_bounded"></a><a name="is_bounded"></a> is_bounded

Testuje, czy zestaw wartości, które może reprezentować, jest ograniczony.

```cpp
static constexpr bool is_bounded = false;
```

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli typ ma ograniczony zestaw wartości, które mają zostać wywidoczne; w **`false`** przeciwnym razie.

#### <a name="remarks"></a>Uwagi

Wszystkie wstępnie zdefiniowane typy mają ograniczonego zestawu wartości, które są dostępne i zwracają **`true`** .

#### <a name="example"></a>Przykład

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

### <a name="is_exact"></a><a name="is_exact"></a> is_exact

Testuje, czy obliczenia wykonywane na typie są wolne od błędów zaokrąglania.

```cpp
static constexpr bool is_exact = false;
```

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obliczenia są wolne od błędów zaokrąglania; w **`false`** przeciwnym razie.

#### <a name="remarks"></a>Uwagi

Wszystkie wstępnie zdefiniowane typy całkowite mają dokładne reprezentacje dla ich wartości i zwracają **`false`** . Reprezentacja stała lub racjonalna jest również uważana za dokładną, ale reprezentacja zmiennoprzecinkowa nie jest.

#### <a name="example"></a>Przykład

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

### <a name="is_iec559"></a><a name="is_iec559"></a> is_iec559

Testuje, czy typ jest zgodny ze standardami IEC 559.

```cpp
static constexpr bool is_iec559 = false;
```

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli typ jest zgodny ze standardami IEC 559, w **`false`** przeciwnym razie.

#### <a name="remarks"></a>Uwagi

IEC 559 jest międzynarodowym standardem do reprezentowania wartości zmiennoprzecinkowych i jest również znany jako IEEE 754 w USA.

#### <a name="example"></a>Przykład

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

### <a name="is_integer"></a><a name="is_integer"></a> is_integer

Testuje, czy typ ma reprezentację liczb całkowitych.

```cpp
static constexpr bool is_integer = false;
```

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli typ ma reprezentację całkowitą; w **`false`** przeciwnym razie.

#### <a name="remarks"></a>Uwagi

Wszystkie wstępnie zdefiniowane typy całkowite mają reprezentację liczb całkowitych.

#### <a name="example"></a>Przykład

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

### <a name="is_modulo"></a><a name="is_modulo"></a> is_modulo

Testuje, czy **Typ** ma reprezentację modulo.

```cpp
static constexpr bool is_modulo = false;
```

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli typ ma reprezentację modulo; w **`false`** przeciwnym razie.

#### <a name="remarks"></a>Uwagi

Reprezentacja modulo jest reprezentacją, w której wszystkie wyniki są ograniczone do niektórych wartości. Wszystkie wstępnie zdefiniowane typy całkowite bez znaku mają reprezentację modulo.

#### <a name="example"></a>Przykład

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

### <a name="is_signed"></a><a name="is_signed"></a> is_signed

Testuje, czy typ ma podpisaną reprezentację.

```cpp
static constexpr bool is_signed = false;
```

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli typ ma podpisaną reprezentację; w **`false`** przeciwnym razie.

#### <a name="remarks"></a>Uwagi

Element członkowski przechowuje wartość true dla typu, który ma podpisaną reprezentację, czyli w przypadku wszystkich wstępnie zdefiniowanych typów liczb całkowitych zmiennoprzecinkowych i ze znakiem.

#### <a name="example"></a>Przykład

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

### <a name="is_specialized"></a><a name="is_specialized"></a> is_specialized

Testuje, czy typ ma jawną specjalizację zdefiniowaną w szablonie klasy `numeric_limits` .

```cpp
static constexpr bool is_specialized = false;
```

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli typ ma jawną specjalizację zdefiniowaną w szablonie klasy; w **`false`** przeciwnym razie.

#### <a name="remarks"></a>Uwagi

Wszystkie typy skalarne inne niż wskaźniki mają jawną specjalizację zdefiniowaną dla szablonu klasy `numeric_limits` .

#### <a name="example"></a>Przykład

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

### <a name="lowest"></a><a name="lowest"></a> okreolon

Zwraca najbardziej ujemną wartość skończoną.

```cpp
static constexpr Type lowest() throw();
```

#### <a name="return-value"></a>Wartość zwracana

Zwraca najbardziej ujemną wartość skończoną.

#### <a name="remarks"></a>Uwagi

Zwraca najbardziej ujemną wartość skończoną dla typu (zazwyczaj `min()` dla typów całkowitych i `-max()` dla typów zmiennoprzecinkowych). Wartość zwracana ma znaczenie, jeśli `is_bounded` jest **`true`** .

### <a name="max"></a><a name="max"></a> Maksymalny

Zwraca maksymalną skończoną wartość dla typu.

```cpp
static constexpr Type max() throw();
```

#### <a name="return-value"></a>Wartość zwracana

Maksymalna wartość skończoną dla typu.

#### <a name="remarks"></a>Uwagi

Maksymalna wartość skończoną jest INT_MAX dla typu **`int`** i FLT_MAX dla typu **`float`** . Wartość zwracana ma znaczenie, jeśli [is_bounded](#is_bounded) jest **`true`** .

#### <a name="example"></a>Przykład

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

### <a name="max_digits10"></a><a name="max_digits10"></a> max_digits10

Zwraca liczbę cyfr dziesiętnych wymaganych do upewnienia się, że dwie odrębne wartości typu mają odrębne reprezentacje dziesiętne.

```cpp
static constexpr int max_digits10 = 0;
```

#### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę cyfr dziesiętnych, które są wymagane, aby upewnić się, że dwie odrębne wartości typu mają odrębne reprezentacje dziesiętne.

#### <a name="remarks"></a>Uwagi

Składowa przechowuje liczbę cyfr dziesiętnych wymaganych do upewnienia się, że dwie odrębne wartości typu mają odrębne reprezentacje dziesiętne.

### <a name="max_exponent"></a><a name="max_exponent"></a> max_exponent

Zwraca maksymalną dodatnią wartość wykładnika całkowitą, którą typ zmiennoprzecinkowy może reprezentować jako skończone wartości, gdy podstawa podstawy jest podnoszona do tej potęgi.

```cpp
static constexpr int max_exponent = 0;
```

#### <a name="return-value"></a>Wartość zwracana

Maksymalny szacowany całkowity podstawy wykładnika oparta na typie.

#### <a name="remarks"></a>Uwagi

Zwracana funkcja elementu członkowskiego ma znaczenie tylko dla typów zmiennoprzecinkowych. `max_exponent`Jest wartością FLT_MAX_EXP typu **`float`** .

#### <a name="example"></a>Przykład

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

### <a name="max_exponent10"></a><a name="max_exponent10"></a> max_exponent10

Zwraca maksymalną dodatnią wartość wykładnika całkowitą, którą typ zmiennoprzecinkowy może reprezentować jako skończone wartości, gdy baza danych jest podnoszona do tej potęgi.

```cpp
static constexpr int max_exponent10 = 0;
```

#### <a name="return-value"></a>Wartość zwracana

Maksymalny całkowity 10-podstawowy wykładnik, który jest zaprezentowany przez typ.

#### <a name="remarks"></a>Uwagi

Zwracana funkcja elementu członkowskiego ma znaczenie tylko dla typów zmiennoprzecinkowych. `max_exponent`Jest wartością FLT_MAX_10 typu **`float`** .

#### <a name="example"></a>Przykład

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

### <a name="min"></a><a name="min"></a> min

Zwraca minimalną znormalizowaną wartość dla typu.

```cpp
static constexpr Type min() throw();
```

#### <a name="return-value"></a>Wartość zwracana

Minimalna znormalizowana wartość dla typu.

#### <a name="remarks"></a>Uwagi

Minimalna znormalizowana wartość jest INT_MIN dla typu **`int`** i FLT_MIN dla typu **`float`** . Wartość zwracana ma znaczenie, jeśli [is_bounded](#is_bounded) jest **`true`** lub jeśli [is_signed](#is_signed) jest **`false`** .

#### <a name="example"></a>Przykład

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

### <a name="min_exponent"></a><a name="min_exponent"></a> min_exponent

Zwraca maksymalny całkowity ujemny wykładnik, który typ zmiennoprzecinkowy może reprezentować jako skończoną wartość, gdy baza podstawy jest podniesiona do tej potęgi.

```cpp
static constexpr int min_exponent = 0;
```

#### <a name="return-value"></a>Wartość zwracana

Minimalny całkowity podstawy wykładnika oparta na typie.

#### <a name="remarks"></a>Uwagi

Funkcja członkowska ma znaczenie tylko dla typów zmiennoprzecinkowych. `min_exponent`Jest wartością FLT_MIN_EXP typu **`float`** .

#### <a name="example"></a>Przykład

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

### <a name="min_exponent10"></a><a name="min_exponent10"></a> min_exponent10

Zwraca maksymalny całkowity ujemny wykładnik, który typ zmiennoprzecinkowy może reprezentować jako skończoną wartość, gdy baza danych jest podnoszona do tej potęgi.

```cpp
static constexpr int min_exponent10 = 0;
```

#### <a name="return-value"></a>Wartość zwracana

Minimalny całkowity, 10-podstawowy wykładnik do zaprezentowania przez typ.

#### <a name="remarks"></a>Uwagi

Funkcja członkowska ma znaczenie tylko dla typów zmiennoprzecinkowych. `min_exponent10`Jest wartością FLT_MIN_10_EXP typu **`float`** .

#### <a name="example"></a>Przykład

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

### <a name="quiet_nan"></a><a name="quiet_nan"></a> quiet_NaN

Zwraca reprezentację wartości typu quiet nie jest liczbą (NAN) dla tego elementu.

```cpp
static constexpr Type quiet_NaN() throw();
```

#### <a name="return-value"></a>Wartość zwracana

Reprezentacja cichego NAN dla typu.

#### <a name="remarks"></a>Uwagi

Wartość zwracana ma znaczenie tylko wtedy, gdy [has_quiet_NaN](#has_quiet_nan) jest **`true`** .

#### <a name="example"></a>Przykład

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

### <a name="radix"></a><a name="radix"></a> podstawy

Zwraca część całkowitą, która jest określana jako podstawy, używana do reprezentowania typu.

```cpp
static constexpr int radix = 0;
```

#### <a name="return-value"></a>Wartość zwracana

Część podstawowa dla reprezentacji typu.

#### <a name="remarks"></a>Uwagi

Podstawą jest 2 dla wstępnie zdefiniowanych typów całkowitych i podstawa, do której jest podnoszona wartość wykładnika lub FLT_RADIX, dla wstępnie zdefiniowanych typów zmiennoprzecinkowych.

#### <a name="example"></a>Przykład

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

### <a name="round_error"></a><a name="round_error"></a> round_error

Zwraca maksymalny błąd zaokrąglenia typu.

```cpp
static constexpr Type round_error() throw();
```

#### <a name="return-value"></a>Wartość zwracana

Maksymalny błąd zaokrąglania typu.

#### <a name="example"></a>Przykład

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

### <a name="round_style"></a><a name="round_style"></a> round_style

Zwraca wartość opisującą różne metody, które można wybrać, aby zaokrąglić wartość zmiennoprzecinkową do wartości całkowitej.

```cpp
static constexpr float_round_style round_style = round_toward_zero;
```

#### <a name="return-value"></a>Wartość zwracana

Wartość z `float_round_style` wyliczenia opisująca styl zaokrąglenia.

#### <a name="remarks"></a>Uwagi

Składowa przechowuje wartość opisującą różne metody, które można wybrać, aby zaokrąglić wartość zmiennoprzecinkową do wartości całkowitej.

Styl okrągły jest zakodowany w tej implementacji, więc nawet jeśli program zostanie uruchomiony z innym trybem zaokrąglania, ta wartość nie zostanie zmieniona.

#### <a name="example"></a>Przykład

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

### <a name="signaling_nan"></a><a name="signaling_nan"></a> signaling_NaN

Zwraca reprezentację sygnalizującego nie jest liczbą (NAN) dla tego typu.

```cpp
static constexpr Type signaling_NaN() throw();
```

#### <a name="return-value"></a>Wartość zwracana

Reprezentacja wartości NAN sygnalizującej typ.

#### <a name="remarks"></a>Uwagi

Wartość zwracana ma znaczenie tylko wtedy, gdy [has_signaling_NaN](#has_signaling_nan) jest **`true`** .

#### <a name="example"></a>Przykład

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

### <a name="tinyness_before"></a><a name="tinyness_before"></a> tinyness_before

Testuje, czy typ może określić, że wartość jest zbyt mała, aby reprezentować jako znormalizowaną wartość przed jej zaokrągleniem.

```cpp
static constexpr bool tinyness_before = false;
```

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli typ może wykryć małe wartości przed zaokrągleniem; **`false`** Jeśli nie jest to możliwe.

#### <a name="remarks"></a>Uwagi

Typy, które mogą wykrywać niewielką część, zostały dołączone jako opcja z reprezentacjimi zmiennoprzecinkowymi IEC 559, a jej implementacja może mieć wpływ na niektóre wyniki.

#### <a name="example"></a>Przykład

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

### <a name="traps"></a><a name="traps"></a> pułapek

Testuje, czy zalewkowanie raportów na wyjątkach arytmetycznych jest implementowane dla typu.

```cpp
static constexpr bool traps = false;
```

#### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli Pułapka jest zaimplementowana dla tego typu; **`false`** Jeśli tak nie jest.

#### <a name="example"></a>Przykład

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
