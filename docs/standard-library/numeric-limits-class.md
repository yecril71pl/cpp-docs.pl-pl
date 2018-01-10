---
title: Klasy numeric_limits | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ccd200c1ee710100bbf3390033ca97381b5dddf2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="numericlimits-class"></a>numeric_limits — Klasa
Klasa szablonu opisuje arytmetyczne właściwości wbudowanych typów wartości liczbowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Type>  
class numeric_limits  
```  
  
#### <a name="parameters"></a>Parametry  
 `Type`  
 Element podstawowy typ danych, którego właściwości są testowane lub wykonać zapytania lub ustaw.  
  
## <a name="remarks"></a>Uwagi  
 Nagłówek definiuje jawne specjalizacje dla typów `wchar_t`, `bool`, `char`, `signed char`, `unsigned char`, `short`, `unsigned short`, `int`, `unsigned int`, `long`, `unsigned long`, `float`, `double`, `long double` **,** `long long`, `unsigned long long`, `char16_t`, i `char32_t`. Dla tych jawne specjalizacje element członkowski [numeric_limits::is_specialized](#is_specialized) jest `true`, i wszystkich odpowiednich elementów członkowskich mają znaczenie wartości. Program można podać dodatkowe jawne specjalizacje. Większość funkcji elementów członkowskich klasy opisują lub testowania możliwe implementacje `float`.  
  
 Dla dowolnego specjalizacji żadnych elementów członkowskich mają znaczenie wartości. Obiekt elementu członkowskiego, który nie ma odpowiednią wartość przechowuje zero (lub `false`) i zwraca funkcji członkowskiej, która nie zwraca wartości znaczący `Type(0)`.  
  
### <a name="static-functions-and-constants"></a>Statyczne funkcje i stałych  
  
|||  
|-|-|  
|[denorm_min](#denorm_min)|Zwraca najmniejszą niezerową nieznormalizowane wartość.|  
|[cyfr](#digits)|Zwraca liczbę miejsc po przecinku podstawa, reprezentujące przez typ bez utraty dokładności.|  
|[digits10](#digits10)|Zwraca liczbę cyfr dziesiętnych, które reprezentują typ bez utraty dokładności.|  
|[Epsilon](#epsilon)|Zwraca różnicę między 1 a najmniejszą wartość większą niż 1 reprezentujące typu danych.|  
|[has_denorm](#has_denorm)|Określa, czy typem umożliwia nieznormalizowane wartości testy.|  
|[has_denorm_loss](#has_denorm_loss)|Sprawdza, czy utrata dokładności wykryciu utratę denormalization, a nie jako wynik niedokładne.|  
|[has_infinity](#has_infinity)|Sprawdza, czy typ ma reprezentację nieskończoności dodatniej.|  
|[has_quiet_NaN](#has_quiet_nan)|Sprawdza, czy typ ma reprezentację quiet nie liczbą (NAN), który jest nonsignaling.|  
|[has_signaling_NaN](#has_signaling_nan)|Sprawdza, czy typ ma reprezentację sygnalizowania nie liczbą (NAN).|  
|[infinity](#infinity)|Reprezentacja do nieskończoności dodatniej dla typu, jeśli jest dostępna.|  
|[is_bounded](#is_bounded)|Testy, jeśli zbiór wartości, które mogą stanowić typem jest jednak ograniczona.|  
|[is_exact](#is_exact)|Testy w przypadku obliczenia wykonywane w typie bez błędów zaokrąglania.|  
|[is_iec559](#is_iec559)|Testy, jeśli typem jest zgodny ze standardami IEC 559.|  
|[is_integer](#is_integer)|Testy, jeśli typ ma reprezentację w postaci liczby całkowitej.|  
|[is_modulo](#is_modulo)|Testy, jeśli typ ma modulo reprezentacji.|  
|[is_signed —](#is_signed)|Testy, jeśli typ ma reprezentację podpisem.|  
|[is_specialized](#is_specialized)|Testy, jeśli typ ma zdefiniowany w klasie szablonu jawnej specjalizacji `numeric_limits`.|  
|[Najniższa](#lowest)|Zwraca najbardziej ujemną wartość skończoną.|  
|[Maksymalna](#max)|Zwraca maksymalną wartością skończoną dla typu.|  
|[max_digits10](#max_digits10)|Zwraca liczbę cyfr dziesiętnych wymagane w celu zapewnienia, że dwa różne wartości typu mają różne reprezentacje dziesiętną.|  
|[max_exponent](#max_exponent)|Zwraca maksymalną dodatnią wykładnik integralną typ zmiennoprzecinkowy może reprezentować wartością skończoną podstawowej podstawa zgłoszony do zasilania.|  
|[max_exponent10](#max_exponent10)|Zwraca maksymalną dodatnią wykładnik integralną typ zmiennoprzecinkowy może reprezentować wartością skończoną base dziesięciu zgłoszony do zasilania.|  
|[min](#min)|Zwraca minimalną wartość znormalizowaną dla typu.|  
|[min_exponent](#min_exponent)|Zwraca maksymalną ujemna wykładnik integralną typ zmiennoprzecinkowy może reprezentować wartością skończoną podstawowej podstawa zgłoszony do zasilania.|  
|[min_exponent10](#min_exponent10)|Zwraca maksymalną ujemna wykładnik integralną typ zmiennoprzecinkowy może reprezentować wartością skończoną base dziesięciu zgłoszony do zasilania.|  
|[quiet_NaN](#quiet_nan)|Zwraca reprezentację quiet nie liczbą (NAN) dla typu.|  
|[Podstawa](#radix)|Zwraca integralną bazowego, określany jako podstawa, używane do reprezentacji typu.|  
|[round_error](#round_error)|Zwraca maksymalną zaokrąglania błąd dla tego typu.|  
|[round_style](#round_style)|Zwraca wartość, która zawiera opis różnych metod, które można wybrać implementację zaokrąglania wartości zmiennoprzecinkowej na wartość całkowitą.|  
|[signaling_NaN](#signaling_nan)|Zwraca reprezentację sygnalizowania nie liczbą (NAN) dla typu.|  
|[tinyness_before](#tinyness_before)|Sprawdza, czy typ można określić, czy wartość jest za mały, aby reprezentować wartość znormalizowaną przed jej zaokrąglania.|  
|[pułapki](#traps)|Testy czy generują pułapki, który raport dotyczący arytmetyczne wyjątków jest zaimplementowany dla typu.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<limity >  
  
 **Namespace:** Standard  
  
##  <a name="denorm_min"></a>numeric_limits::denorm_min  
 Zwraca najmniejszą niezerową nieznormalizowane wartość.  
  
```  
static Type denorm_min() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Najmniejsza niezerową Nieznormalizowana wartość.  
  
### <a name="remarks"></a>Uwagi  
 `long double`jest taka sama jak **podwójne** dla kompilatora języka C++.  
  
 Funkcja zwraca minimalną wartość dla typu, która jest taka sama jak [min](#min) Jeśli [has_denorm](#has_denorm) nie jest równa **denorm_present**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// numeric_limits_denorm_min.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <limits>  
  
using namespace std;  
  
int main( )  
{  
   cout << "The smallest nonzero denormalized value\n for float "  
        << "objects is: " << numeric_limits<float>::denorm_min( )   
        << endl;  
   cout << "The smallest nonzero denormalized value\n for double "  
        << "objects is: " << numeric_limits<double>::denorm_min( )   
        << endl;  
   cout << "The smallest nonzero denormalized value\n for long double "  
        << "objects is: " << numeric_limits<long double>::denorm_min( )   
        << endl;  
  
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
  
##  <a name="digits"></a>numeric_limits::digits  
 Zwraca liczbę miejsc po przecinku podstawa, reprezentujące przez typ bez utraty dokładności.  
  
```  
static const int digits = 0;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba cyfr podstawa, reprezentujące przez typ bez utraty dokładności.  
  
### <a name="remarks"></a>Uwagi  
 Element członkowski przechowuje liczbę miejsc po przecinku podstawa, reprezentujące przez typ bez zmian, czyli liczby bitów niż żadnych bitu znaku dla typu Liczba całkowita wstępnie zdefiniowanych lub liczbę cyfr mantysa wstępnie zdefiniowany typ zmiennoprzecinkowy.  
  
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
  
##  <a name="digits10"></a>numeric_limits::digits10  
 Zwraca liczbę cyfr dziesiętnych, które reprezentują typ bez utraty dokładności.  
  
```  
static const int digits10 = 0;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba cyfr dziesiętnych, które reprezentują typ bez utraty dokładności.  
  
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
  
##  <a name="epsilon"></a>numeric_limits::epsilon  
 Funkcja zwraca różnicę między 1 a najmniejszą wartość większą niż 1, który jest reprezentacja typu danych.  
  
```  
static Type epsilon() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różnica między 1 a najmniejszą wartość większą niż 1, który jest reprezentacja typu danych.  
  
### <a name="remarks"></a>Uwagi  
 Wartość jest typu flt_epsilon — **float**. `epsilon`dla typu jest najmniejsza dodatnia liczba zmiennoprzecinkowa *N* tak, aby *N* + `epsilon` + *N* jest można przedstawić.  
  
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
        << "value greater than 1\n for float objects is: "   
        << numeric_limits<float>::epsilon( )   
        << endl;  
   cout << "The difference between 1 and the smallest "  
        << "value greater than 1\n for double objects is: "   
        << numeric_limits<double>::epsilon( )   
        << endl;  
   cout << "The difference between 1 and the smallest "  
        << "value greater than 1\n for long double objects is: "   
        << numeric_limits<long double>::epsilon( )   
        << endl;  
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
  
##  <a name="has_denorm"></a>numeric_limits::has_denorm  
 Określa, czy typem umożliwia nieznormalizowane wartości testy.  
  
```  
static const float_denorm_style has_denorm = denorm_absent;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość wyliczenia typu **const**`float_denorm_style`, wskazujące czy typ umożliwia nieznormalizowany wartości.  
  
### <a name="remarks"></a>Uwagi  
 Magazyny elementu członkowskiego **denorm_present** dla typu zmiennoprzecinkowego, który ma nieznormalizowane wartości skutecznie zmienną liczbę bitów wykładnika.  
  
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
  
##  <a name="has_denorm_loss"></a>numeric_limits::has_denorm_loss  
 Sprawdza, czy utrata dokładności wykryciu utratę denormalization, a nie jako wynik niedokładne.  
  
```  
static const bool has_denorm_loss = false;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** w przypadku wykrycia utratę dokładności utratę denormalization; **false** , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
 Element członkowski przechowuje wartość true dla typu, który określa, czy wartość utracił dokładność, ponieważ dostarczeniu jako wynik nieznormalizowany (za mały, aby reprezentować wartość znormalizowaną) lub jest niedokładna (nie takie same w związku z tym nie podlegają ograniczenia wykładnik zakres i dokładność), opcję z IEC 559 zmiennoprzecinkowe oświadczenia, które mogą mieć wpływ na niektóre wyniki.  
  
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
  
##  <a name="has_infinity"></a>numeric_limits::has_infinity  
 Sprawdza, czy typ ma reprezentację nieskończoności dodatniej.  
  
```  
static const bool has_infinity = false;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli typ ma reprezentację nieskończoności dodatniej; **false** , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca element członkowski **true** Jeśli [is_iec559](#is_iec559) jest **true**.  
  
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
  
##  <a name="has_quiet_nan"></a>numeric_limits::has_quiet_NaN  
 Sprawdza, czy typ ma reprezentację quiet nie liczbą (NAN), który jest nonsignaling.  
  
```  
static const bool has_quiet_NaN = false;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli **typu** ma reprezentację NAN cichy; **false** , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
 Quiet NAN jest kodowanie nieliczbową, którego nie można sygnalizować jej obecności w wyrażeniu. Wartość zwracana jest **true** Jeśli [is_iec559](#is_iec559) ma wartość true.  
  
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
  
##  <a name="has_signaling_nan"></a>numeric_limits::has_signaling_NaN  
 Sprawdza, czy typ ma reprezentację sygnalizowania nie liczbą (NAN).  
  
```  
static const bool has_signaling_NaN = false;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli typ ma reprezentację sygnalizowania NAN; **false** , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
 NAN sygnalizowania jest kodowanie nie liczba, która sygnalizuje jej obecności w wyrażeniu. Wartość zwracana jest **true**[is_iec559](#is_iec559) ma wartość true.  
  
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
  
##  <a name="infinity"></a>numeric_limits::infinity  
 Reprezentacja nieskończoności dodatniej dla typu, jeśli jest dostępna.  
  
```  
static Type infinity() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Reprezentacja nieskończoności dodatniej dla typu, jeśli jest dostępna.  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwracana ma znaczenie tylko wtedy, gdy [has_infinity](#has_infinity) jest **true**.  
  
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
The representation of infinity for type float is: 1.#INF  
The representation of infinity for type double is: 1.#INF  
The representation of infinity for type long double is: 1.#INF  
```  
  
##  <a name="is_bounded"></a>numeric_limits::is_bounded  
 Testy, jeśli zbiór wartości, które mogą stanowić typem jest jednak ograniczona.  
  
```  
static const bool is_bounded = false;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli typ ma ograniczonego zestawu można przedstawić wartości; **false** , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie typy wstępnie zdefiniowanych ograniczonego zestawu można przedstawić wartości i zwraca **true**.  
  
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
  
##  <a name="is_exact"></a>numeric_limits::is_exact  
 Testy w przypadku obliczenia wykonywane w typie bez błędów zaokrąglania.  
  
```  
static const bool is_exact = false;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli obliczenia są wolne zaokrąglenia liczby błędów; **false** , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie typy całkowite wstępnie zdefiniowanych ma dokładnie reprezentacje ich wartości i zwraca **false**. Reprezentacja stałoprzecinkowej lub ich rozsądne jest traktowana jako dokładne, ale nie jest odwzorowanie liczby zmiennoprzecinkowej.  
  
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
  
##  <a name="is_iec559"></a>numeric_limits::is_iec559  
 Testy, jeśli typem jest zgodny ze standardami IEC 559.  
  
```  
static const bool is_iec559 = false;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli typ jest zgodny ze standardami IEC 559; **false** , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
 IEC 559 jest standardem międzynarodowe reprezentujący wartości zmiennoprzecinkowych i jest także znana jako IEEE 754 w USA.  
  
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
  
##  <a name="is_integer"></a>numeric_limits::is_integer  
 Testy, jeśli typ ma reprezentację w postaci liczby całkowitej.  
  
```  
static const bool is_integer = false;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli typ ma reprezentację w postaci liczby całkowitej; **false** , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie typy całkowite wstępnie zdefiniowanych ma reprezentację w postaci liczby całkowitej.  
  
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
  
##  <a name="is_modulo"></a>numeric_limits::is_modulo  
 Sprawdza, czy **typu** ma modulo reprezentacji.  
  
```  
static const bool is_modulo = false;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli typ ma modulo reprezentacja; **false** , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
 A modulo reprezentacja jest reprezentację, gdzie wszystkie wyniki zostały zredukowane modulo niektóre wartości. Wszystkie typy wstępnie zdefiniowanych liczbę całkowitą bez znaku mają modulo reprezentacji.  
  
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
  
##  <a name="is_signed"></a>numeric_limits::is_signed  
 Testy, jeśli typ ma reprezentację podpisem.  
  
```  
static const bool is_signed = false;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli typ ma reprezentację podpisem; **false** , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
 Element członkowski przechowuje wartość true dla typu, który został podpisany reprezentacji w przypadku wszystkich wstępnie zdefiniowanych typów zmiennoprzecinkowych i podpisanej liczby całkowitej.  
  
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
  
##  <a name="is_specialized"></a>numeric_limits::is_specialized  
 Testy, jeśli typ ma zdefiniowany w klasie szablonu jawnej specjalizacji `numeric_limits`.  
  
```  
static const bool is_specialized = false;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli typ ma zdefiniowany w klasie szablonu; jawnej specjalizacji **false** , jeśli nie.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie typy skalarne niż wskaźniki mieć jawnej specjalizacji zdefiniowanej dla klasy szablonu `numeric_limits`.  
  
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
  
##  <a name="lowest"></a>numeric_limits::LOWEST  
 Zwraca najbardziej ujemną wartość skończoną.  
  
```  
static Type lowest() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca najbardziej ujemną wartość skończoną.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca najbardziej ujemna skończona wartość dla typu (co jest typowe `min()` dla typów całkowitych i `-max()` dla typów zmiennoprzecinkowych). Wartość zwracana jest łatwy do rozpoznania Jeśli `is_bounded` jest `true`.  
  
##  <a name="max"></a>numeric_limits::Max  
 Zwraca maksymalną wartością skończoną dla typu.  
  
```  
static Type max() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalną wartością skończoną dla typu.  
  
### <a name="remarks"></a>Uwagi  
 Ograniczona wartość maksymalna to int_max — dla typu `int` i flt_max — dla typu **float**. Wartość zwracana jest łatwy do rozpoznania Jeśli [is_bounded](#is_bounded) jest **true**.  
  
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
  
##  <a name="max_digits10"></a>numeric_limits::max_digits10  
 Zwraca liczbę miejsc dziesiętnych, które są wymagane, aby upewnić się, że dwa różne wartości typu mają różne reprezentacje dziesiętną.  
  
```  
static int max_digits10 = 0;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę cyfr dziesiętnych, które są wymagane, aby upewnić się, że dwa różne wartości typu mają różne reprezentacje dziesiętną.  
  
### <a name="remarks"></a>Uwagi  
 Element członkowski przechowuje liczba cyfr dziesiętnych, wymagane, aby upewnić się, że dwa różne wartości typu mają różne reprezentacje dziesiętną.  
  
##  <a name="max_exponent"></a>numeric_limits::max_exponent  
 Zwraca maksymalną dodatnią wykładnik integralną typ zmiennoprzecinkowy może reprezentować wartością skończoną podstawowej podstawa zgłoszony do zasilania.  
  
```  
static const int max_exponent = 0;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalny całkowity na podstawie radix — wykładnik można przedstawić przez typ.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwracany jest znaczący tylko dla typów zmiennoprzecinkowych. `max_exponent` Jest flt_max_exp — wartość dla typu **float**.  
  
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
  
##  <a name="max_exponent10"></a>numeric_limits::max_exponent10  
 Zwraca maksymalną dodatnią wykładnik integralną typ zmiennoprzecinkowy może reprezentować wartością skończoną base dziesięciu zgłoszony do zasilania.  
  
```  
static const int max_exponent10 = 0;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalny całkowity o podstawie 10 wykładnik można przedstawić według typu.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwracany jest znaczący tylko dla typów zmiennoprzecinkowych. `max_exponent` Jest FLT_MAX_10 wartość dla typu **float**.  
  
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
  
##  <a name="min"></a>numeric_limits::min  
 Zwraca minimalną wartość znormalizowaną dla typu.  
  
```  
static Type min() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Minimalna wartość znormalizowaną dla typu.  
  
### <a name="remarks"></a>Uwagi  
 Minimalna wartość znormalizowaną to int_min — dla typu `int` i flt_min — dla typu `float`. Wartość zwracana jest łatwy do rozpoznania Jeśli [is_bounded](#is_bounded) jest `true` lub, jeśli [is_signed —](#is_signed) jest `false`.  
  
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
  
##  <a name="min_exponent"></a>numeric_limits::min_exponent  
 Zwraca maksymalną ujemna wykładnik integralną typ zmiennoprzecinkowy może reprezentować wartością skończoną podstawowej podstawa zgłoszony do zasilania.  
  
```  
static const int min_exponent = 0;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Minimalna całkowitych na podstawie radix — wykładnik można przedstawić według typu.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska jest znaczący tylko dla typów zmiennoprzecinkowych. `min_exponent` Jest flt_min_exp — wartość dla typu **float**.  
  
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
  
##  <a name="min_exponent10"></a>numeric_limits::min_exponent10  
 Zwraca maksymalną ujemna wykładnik integralną typ zmiennoprzecinkowy może reprezentować wartością skończoną base dziesięciu zgłoszony do zasilania.  
  
```  
static const int min_exponent10 = 0;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Minimalny całkowity o podstawie 10 wykładnik można przedstawić według typu.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska jest znaczący tylko dla typów zmiennoprzecinkowych. `min_exponent10` Jest flt_min_10_exp — wartość dla typu **float**.  
  
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
  
##  <a name="quiet_nan"></a>numeric_limits::quiet_NaN  
 Zwraca reprezentację quiet nie liczbą (NAN) dla typu.  
  
```  
static Type quiet_NaN() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Reprezentacja quiet NAN dla typu.  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwracana ma znaczenie tylko wtedy, gdy [has_quiet_NaN](#has_quiet_nan) jest **true**.  
  
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
  
##  <a name="radix"></a>numeric_limits::radix  
 Zwraca integralną bazowego, określany jako podstawa, używane do reprezentacji typu.  
  
```  
static const int radix = 0;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Całkowite podstawa reprezentacja tego typu.  
  
### <a name="remarks"></a>Uwagi  
 Element podstawowy jest 2 do typów wstępnie zdefiniowanych całkowitą i podstawowej, do którego jest uruchamiany wykładnik lub flt_radix —, wstępnie zdefiniowanych typów zmiennoprzecinkowych.  
  
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
  
##  <a name="round_error"></a>numeric_limits::round_error  
 Zwraca maksymalną zaokrąglania błąd dla tego typu.  
  
```  
static Type round_error() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna zaokrąglania błąd dla tego typu.  
  
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
  
##  <a name="round_style"></a>numeric_limits::round_style  
 Zwraca wartość, która zawiera opis różnych metod, które można wybrać implementację zaokrąglania wartości zmiennoprzecinkowej na wartość całkowitą.  
  
```  
static const float_round_style round_style = round_toward_zero;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość z zakresu od `float_round_style` styl wyliczenie opisujące zaokrąglania.  
  
### <a name="remarks"></a>Uwagi  
 Element członkowski przechowuje wartość, która zawiera opis różnych metod, które można wybrać implementację zaokrąglania wartości zmiennoprzecinkowej na wartość całkowitą.  
  
 Round styl jest trudna kodowanych w tej implementacji, dlatego nawet jeśli uruchamiania programu z innego trybu zaokrąglania, ta wartość nie zostanie zmieniona.  
  
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
  
##  <a name="signaling_nan"></a>numeric_limits::signaling_NaN  
 Zwraca reprezentację sygnalizowania nie liczbą (NAN) dla typu.  
  
```  
static Type signaling_NaN() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Reprezentacja sygnalizowania NAN dla typu.  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwracana ma znaczenie tylko wtedy, gdy [has_signaling_NaN](#has_signaling_nan) jest **true**.  
  
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
  
##  <a name="tinyness_before"></a>numeric_limits::tinyness_before  
 Sprawdza, czy typ można określić, czy wartość jest za mały, aby reprezentować wartość znormalizowaną przed jej zaokrąglania.  
  
```  
static const bool tinyness_before = false;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli typ może wykryć niewielki rozmiar wartości przed zaokrąglania; `false` Jeśli nie jest możliwy.  
  
### <a name="remarks"></a>Uwagi  
 Typy, które umożliwia wykrywanie tinyness były opcją z IEC 559 reprezentacje liczb zmiennoprzecinkowych i jego implementacja może mieć wpływ na niektóre wyniki.  
  
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
  
##  <a name="traps"></a>numeric_limits::Traps  
 Testy czy generują pułapki, który raport dotyczący arytmetyczne wyjątków jest zaimplementowany dla typu.  
  
```  
static const bool traps = false;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli wyłapywanie jest zaimplementowany dla tego typu; **false** Jeśli nie jest.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

