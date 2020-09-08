---
title: asinh, asinhf, asinhl
description: Dokumentacja interfejsu API dla asinh —, asinhf — i asinhl; które oblicza odwrotny sinus hiperboliczny wartości zmiennoprzecinkowej.
ms.date: 08/31/2020
api_name:
- asinh
- asinhf
- asinhl
- _o_asinh
- _o_asinhf
- _o_asinhl
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
- asinhf
- asinhl
- asinh
helpviewer_keywords:
- asinh function
- asinhl function
- asinhf function
ms.assetid: 4488babe-1a7e-44ca-8b7b-c2db0a70084f
ms.openlocfilehash: 332e6bfc95bd297d703d879cdd468b450cfdc763
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556791"
---
# <a name="asinh-asinhf-asinhl"></a>asinh, asinhf, asinhl

Oblicza odwrotny sinus hiperboliczny.

## <a name="syntax"></a>Składnia

```C
double asinh( double x );
float asinhf( float x );
long double asinhl( long double x );
#define asinh(X) // Requires C11 or higher

float asinh( float x );  // C++ only
long double asinh( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa.

## <a name="return-value"></a>Wartość zwracana

Funkcje **ASINH —** zwracają odwrotność hyberbolic sinus (łuk hiperboliczny sinus) *x*. Ta funkcja jest prawidłowa w przypadku domeny zmiennoprzecinkowej. Jeśli *x* to cichy NaN, nieokreślony lub nieskończony, zwracana jest ta sama wartość.

|Dane wejściowe|Wyjątek SEH|**_matherr** Oprócz|
|-----------|-------------------|--------------------------|
|QNAN, IND, INF|brak|brak|

## <a name="remarks"></a>Uwagi

Gdy używasz języka C++, możesz wywoływać przeciążenia **ASINH —** , które pobierają i **`float`** zwracają **`long double`** wartości. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **ASINH —** zawsze przyjmuje i zwraca **`double`** .

Jeśli używasz \<tgmath.h> `asinh()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .


Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek C|Wymagany nagłówek C++|
|--------------|--------------|------------------|
|**ASINH —**, **asinhf —**, **asinhl**|\<math.h>|\<cmath> lub \<math.h>|
|**ASINH — ()** — makro | \<tgmath.h> ||

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_asinh.c
// Compile by using: cl /W4 crt_asinh.c
// This program displays the hyperbolic sine of pi / 4
// and the arc hyperbolic sine of the result.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = sinh( pi / 4 );
   y = asinh( x );
   printf( "sinh( %f ) = %f\n", pi/4, x );
   printf( "asinh( %f ) = %f\n", x, y );
}
```

```Output
sinh( 0.785398 ) = 0.868671
asinh( 0.868671 ) = 0.785398
```

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[cosh, coshf, coshl](cosh-coshf-coshl.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
