---
title: atan, atanf, atanl, atan2, atan2f, atan2l
ms.date: 4/2/2020
api_name:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
- _o_atan
- _o_atan2
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- atan
- atan2l
- atan2
- atanl
- atanf
- atan2f
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
ms.openlocfilehash: 3b8411f9839022477dff3100792e271e2f0b572b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334115"
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>atan, atanf, atanl, atan2, atan2f, atan2l

Oblicza arctangent **z x** (**atan**, **atanf**, i **atanl**) lub arctangent **z y**/**x** (**atan2**, **atan2f**, i **atan2l**).

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

**atan** zwraca arctangent *x* w zakresie -π/2 do π/2 radianów. **atan2** zwraca arctangent *y*/*x* w zakresie -π do π radianów. Jeśli *x* wynosi 0, **atan** zwraca wartość 0. Jeśli oba parametry **atan2** są 0, funkcja zwraca 0. Wszystkie wyniki są w radianach.

**atan2** używa znaków obu parametrów do określenia kwadrantu wartości zwracanej.

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|brak|**_DOMAIN**|

## <a name="remarks"></a>Uwagi

Funkcja **atan** oblicza arctangent (odwrotną funkcję stycznej) *x*. **atan2** oblicza arctangent *y*/*x* (jeśli *x* jest równe 0, **atan2** zwraca π/2, jeśli *y* jest dodatni, -π/2, jeśli y jest *ujemna,* lub 0, jeśli *y* jest 0.)

**atan** ma implementację, która używa streamingu rozszerzeń SIMD 2 (SSE2). Aby uzyskać informacje i ograniczenia dotyczące korzystania z implementacji SSE2, zobacz [_set_SSE2_enable](set-sse2-enable.md).

Ponieważ C++ umożliwia przeciążenie, można wywołać przeciążenia **atan** i **atan2,** które przyjmują **float** lub **długie** **podwójne** argumenty. W programie C, **atan** i **atan2** zawsze wziąć **podwójne** argumenty i zwrócić **podwójne**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|-------------|---------------------|-|
|**atan**, **atan2**, **atanf**, **atan2f**, **atanl**, **atan2l**|\<> math.h|\<cmath> lub \<math.h>|

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

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
[_CIatan](../../c-runtime-library/ciatan.md)<br/>
[_CIatan2](../../c-runtime-library/ciatan2.md)<br/>
