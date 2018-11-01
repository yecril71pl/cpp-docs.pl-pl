---
title: Dziennik, logf —, logl, log10 log10f —, log10l
ms.date: 04/05/2018
apiname:
- log10f
- logf
- log10
- log
- log10l
- logl
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: c8e3f73e61fefa7a39a6d53d63739b094d78c499
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543302"
---
# <a name="log-logf-logl-log10-log10f-log10l"></a>Dziennik, logf —, logl, log10 log10f —, log10l

Obliczanie logarytmów.

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
Wartość, której logarytm ma zostać znaleziona.

## <a name="return-value"></a>Wartość zwracana

**Dziennika** funkcji Zwraca logarytm naturalny (podstawowy *e*) z *x* w przypadku powodzenia. **Log10** funkcje zwracają logarytm base 10. Jeśli *x* jest ujemna, te funkcje zwracają nieokreślony (Znajdź), domyślnie. Jeśli *x* wynosi 0, zwracają one infinity (INF).

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|GRANICACH QNAN, ZNAJDŹ|brak|_DOMAIN|
|± 0|ZERODIVIDE|_SING|
|*x* < 0|NIEPRAWIDŁOWY|_DOMAIN|

**Dziennik** i **log10** mają implementacji, który używa Streaming SIMD Extensions 2 (SSE2). Zobacz [_set_sse2_enable —](set-sse2-enable.md) informacje i ograniczenia dotyczące przy użyciu implementacji SSE2.

## <a name="remarks"></a>Uwagi

Język C++ pozwala na przeciążenie, można więc wywoływać przeciążenia **dziennika** i **log10** przyjmujące i zwracające **float** lub **typu long double** wartości. W programie C **dziennika** i **log10** zawsze przyjmują i zwracają **double**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Dziennik**, **logf —**, **logl**, **log10**, **log10f —**, **log10l**|\<math.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

Aby wygenerować logarytmów dla innych podstaw, użyj matematyczne relacji: dziennika podstawowego b == logarytmu naturalnego () / fizyczne dziennika (b).

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

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md) <br/>
[exp, expf, expl](exp-expf.md) <br/>
[_matherr](matherr.md) <br/>
[pow, powf, powl](pow-powf-powl.md) <br/>
[_CIlog](../../c-runtime-library/cilog.md) <br/>
[_CIlog10](../../c-runtime-library/cilog10.md)<br/>
