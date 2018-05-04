---
title: ATAN, atanf —, atanl —, atan2, atan2f —, atan2l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
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
- atan
- atan2l
- atan2
- atanl
- atanf
- atan2f
dev_langs:
- C++
helpviewer_keywords:
- atan function
- atanf function
- atanl function
- atan2 function
- atan2l function
- arctangent function
- trigonometric functions
- atan2f function
ms.assetid: 7a87a18e-c94d-4727-9cb1-1bb5c2725ae4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e1f8b60c25c57e3e2eb6a9a964fd80664e3aa4c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>atan, atanf, atanl, atan2, atan2f, atan2l

Oblicza tangens **x** (**atan**, **atanf —**, i **atanl —**) lub arcus tangens **y** / **x** (**atan2**, **atan2f —**, i **atan2l —**).

## <a name="syntax"></a>Składnia

```C
double atan( double x );
float atanf( float x );
long double atanl( long double x );

double atan2( double y, double x );
float atan2f( float y, float x );
long double atan2l( long double y, long double x );
```

```cpp
float atan( float x );  // C++ only
long double atan( long double x );  // C++ only

float atan2( float y, float x );  // C++ only
long double atan2( long double y, long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*, *y*<br/>
Dowolne liczby.

## <a name="return-value"></a>Wartość zwracana

**ATAN** Zwraca arcus tangens *x* w zakresie - π/2 na radiany π/2. **ATAN2** Zwraca arcus tangens *y*/*x* w zakresie - π na radiany π. Jeśli *x* ma wartość 0, **atan** zwraca wartość 0. Jeśli oba parametry **atan2** 0, funkcja zwraca wartość 0. Wszystkie wyniki są wyświetlane w radianach.

**ATAN2** używa oznaki oba parametry w celu określenia wiązania kwadrantu zwracanej wartości.

|Dane wejściowe|Wyjątek SEH|Matherr — wyjątek|
|-----------|-------------------|-----------------------|
|GRANICACH **QNAN**, **IND**|brak|**_DOMAIN —**|

## <a name="remarks"></a>Uwagi

**Atan** funkcja oblicza tangens (odwrotna funkcja tangens) *x*. **ATAN2** oblicza tangens *y*/*x* (Jeśli *x* jest równe 0, **atan2** zwraca π/2, jeśli *y* jest dodatnia, jeśli - π/2 *y* jest wartość ujemną lub 0, jeśli *y* ma wartość 0.)

**ATAN** ma implementację, która używa Streaming SIMD Extensions 2 (SSE2). Aby uzyskać informacje i ograniczenia dotyczące korzystania z implementacji SSE2, zobacz [_set_sse2_enable —](set-sse2-enable.md).

Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia **atan** i **atan2** które trwają **float** lub **długi** **podwójne**  argumentów. W programie C **atan** i **atan2** zawsze pobierają **podwójne** argumentów i zwracane **podwójne**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymaganego nagłówka (C++)|
|-------------|---------------------|-|
|**ATAN**, **atan2**, **atanf —**, **atan2f —**, **atanl —**, **atan2l —**|\<math.h>|\<cmath > lub \<math.h >|

## <a name="example"></a>Przykład

```C
// crt_atan.c
// arguments: 5 0.5
#include <math.h>
#include <stdio.h>
#include <errno.h>

int main( int ac, char* av[] )
{
   double x, y, theta;
   if( ac != 3 ){
      fprintf( stderr, "Usage: %s <x> <y>\n", av[0] );
      return 1;
   }
   x = atof( av[1] );
   theta = atan( x );
   printf( "Arctangent of %f: %f\n", x, theta );
   y = atof( av[2] );
   theta = atan2( y, x );
   printf( "Arctangent of %f / %f: %f\n", y, x, theta );
   return 0;
}
```

```Output
Arctangent of 5.000000: 1.373401
Arctangent of 0.500000 / 5.000000: 0.099669
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[COS cosf —, cosl —](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
[_CIatan](../../c-runtime-library/ciatan.md)<br/>
[_CIatan2](../../c-runtime-library/ciatan2.md)<br/>
