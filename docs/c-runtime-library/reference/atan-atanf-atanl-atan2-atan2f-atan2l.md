---
title: atan, atanf, atanl, atan2, atan2f, atan2l
description: Dokumentacja interfejsu API dla atan, atanf —, atanl, atan2, atan2f — i atan2l; które oblicza arcus tangens wartości zmiennoprzecinkowej.
ms.date: 08/31/2020
api_name:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
- _o_atan
- _o_atan2
- _o_atan2f
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
ms.openlocfilehash: 1f1d33aac86d94ab3731dd5cf5b124af99ccb3f2
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555634"
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>atan, atanf, atanl, atan2, atan2f, atan2l

Oblicza arcus tangens liczby **x** (**atan**, **atanf —** i **atanl**) lub arcus tangens liczby **y** / **x** (**atan2**, **atan2f —** i **atan2l**).

## <a name="syntax"></a>Składnia

```C
double atan( double x );
float atanf( float x );
long double atanl( long double x );
#define atan(X) // Requires C11 or higher

float atan( float x );  // C++ only
long double atan( long double x );  // C++ only

double atan2( double y, double x );
float atan2f( float y, float x );
long double atan2l( long double y, long double x );
#define atan2(Y, X) // Requires C11 or higher

float atan2( float y, float x );  // C++ only
long double atan2( long double y, long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*, *y*\
Wszystkie liczby.

## <a name="return-value"></a>Wartość zwracana

**atan** zwraca arcus tangens *x* w zakresie od π/2 do π/2 radianów. Funkcja **atan2** zwraca arcus tangens liczby *y* / *x* w zakresie od π do π radianów. Jeśli *x* to 0, **atan** zwraca 0. Jeśli oba parametry **atan2** mają wartość 0, funkcja zwraca wartość 0. Wszystkie wyniki są w radianach.

Funkcja **atan2** używa znaków obu parametrów, aby określić ćwiartkę zwracanej wartości.

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|**QNAN**, **IND**|brak|**_DOMAIN**|

## <a name="remarks"></a>Uwagi

Funkcja **atan** Oblicza arcus tangens (funkcja odwrotnej styczności) *x*. Funkcja **atan2** Oblicza arcus tangens *liczby y* / *x* (Jeśli *x* jest równa 0, **atan2** zwraca π/2, jeśli *y* jest dodatnia,-π/2, jeśli *y* jest ujemna, lub 0, jeśli *y* jest równa 0).

Jeśli używasz \<tgmath.h> `atan()` `atan2()` makra lub, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

**atan** ma implementację, która używa Streaming SIMD Extensions 2 (SSE2). Informacje i ograniczenia dotyczące korzystania z implementacji SSE2 można znaleźć w temacie [_set_SSE2_enable](set-sse2-enable.md).

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **atan** i **atan2** przyjmujących **`float`** lub **`long double`** argumenty. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **atan** i **atan2** zawsze przyjmują **`double`** argumenty i zwracają **`double`** .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|-------------|---------------------|-|
|**atan**, **atan2**, **atanf —**, **atan2f —**, **atanl**, **atan2l**|\<math.h>|\<cmath> lub \<math.h>|
|**ATAN ()**, makra **atan2** | \<tgmath.h> ||

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

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
[_CIatan](../../c-runtime-library/ciatan.md)<br/>
[_CIatan2](../../c-runtime-library/ciatan2.md)<br/>
