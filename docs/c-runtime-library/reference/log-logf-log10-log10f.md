---
title: log, logf —, logl, log10 —, log10f —, log10l
ms.date: 6/5/2020
api_name:
- log10f
- logf
- log10
- log
- log10l
- logl
- _o_log
- _o_log10
- _o_log10f
- _o_logf
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- logf
- logl
- _log10l
- log
- _logl
- log10f
- log10l
- log10
helpviewer_keywords:
- calculating logarithms
- log10f function
- log10 function
- log function
- log10l function
- logl function
- logf function
- logarithms
ms.assetid: 7adc77c2-04f7-4245-a980-21215563cfae
ms.openlocfilehash: ddfe0198ab83f72868f383d6c35f040415893ad4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218601"
---
# <a name="log-logf-logl-log10-log10f-log10l"></a>log, logf —, logl, log10 —, log10f —, log10l

Oblicza logarytmy.

## <a name="syntax"></a>Składnia

```C
double log( double x );
float logf( float x );
long double logl( double x );
double log10( double x );
float log10f ( float x );
long double log10l( double x );
```

```cpp
float log( float x );  // C++ only
long double log( long double x );  // C++ only
float log10( float x );  // C++ only
long double log10( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość, której LOGARYTM ma zostać znaleziony.

## <a name="return-value"></a>Wartość zwracana

Funkcja **log** Zwraca logarytm naturalny (o podstawie *e*) z *x* , jeśli to się powiedzie. Funkcje **log10 —** zwracają logarytm dziesiętny. Jeśli *x* jest ujemna, te funkcje zwracają domyślnie nieokreślony (IND). Jeśli *x* to 0, zwracają nieskończoność (inf).

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|QNAN, IND|brak|_DOMAIN|
|± 0|ZERODIVIDE|_SING|
|*x* < 0|Nieprawidłowy|_DOMAIN|

**dzienniki** i **log10 —** mają implementację, która używa Streaming SIMD Extensions 2 (SSE2). Zobacz [_set_SSE2_enable](set-sse2-enable.md) , aby uzyskać informacje i ograniczenia dotyczące korzystania z implementacji SSE2.

## <a name="remarks"></a>Uwagi

Język C++ umożliwia Przeciążenie, dlatego można wywoływać przeciążenia **dzienników** i **log10 —** , które pobierają i zwracają **`float`** **`long double`** wartości. W programie w języku C **log** i **log10 —** zawsze przyjmują i zwracają **`double`** .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**log**, **logf —**, **logl**, **log10 —**, **log10f —**, **log10l**|\<math.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_log.c
/* This program uses log and log10
* to calculate the natural logarithm and
* the base-10 logarithm of 9,000.
*/

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 9000.0;
   double y;

   y = log( x );
   printf( "log( %.2f ) = %f\n", x, y );
   y = log10( x );
   printf( "log10( %.2f ) = %f\n", x, y );
}
```

```Output
log( 9000.00 ) = 9.104980
log10( 9000.00 ) = 3.954243
```

Aby wygenerować logarytmy dla innych baz, Użyj relacji matematycznej: log Base b z = = naturalnym log (a)/log (b).

```cpp
// logbase.cpp
#include <math.h>
#include <stdio.h>

double logbase(double a, double base)
{
   return log(a) / log(base);
}

int main()
{
   double x = 65536;
   double result;

   result = logbase(x, 2);
   printf("Log base 2 of %lf is %lf\n", x, result);
}
```

```Output
Log base 2 of 65536.000000 is 16.000000
```

## <a name="see-also"></a>Zobacz także

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md) <br/>
[exp, expf, expl](exp-expf.md) <br/>
[_matherr](matherr.md) <br/>
[pow, powf, powl](pow-powf-powl.md) <br/>
[_CIlog](../../c-runtime-library/cilog.md) <br/>
[_CIlog10](../../c-runtime-library/cilog10.md)<br/>
