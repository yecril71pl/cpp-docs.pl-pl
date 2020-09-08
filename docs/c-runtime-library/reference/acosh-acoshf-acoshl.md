---
title: acosh, acoshf, acoshl
description: Dokumentacja interfejsu API dla acosh —, acoshf — i acoshl; które oblicza odwrotny cosinus hiperboliczny wartości zmiennoprzecinkowej.
ms.date: 08/31/2020
api_name:
- acoshf
- acosh
- acoshl
- _o_acosh
- _o_acoshf
- _o_acoshl
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
- acosh
- acoshf
- acoshl
- math/acosh
- math/acoshf
- math/acoshl
helpviewer_keywords:
- acoshf function
- acosh function
- acoshl function
ms.assetid: 6985c4d7-9e2a-44ce-9a9b-5a43015f15f7
ms.openlocfilehash: ef6d47ca07f96be84962303c13162b154086e5f2
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555114"
---
# <a name="acosh-acoshf-acoshl"></a>acosh, acoshf, acoshl

Oblicza odwrotny cosinus hiperboliczny.

## <a name="syntax"></a>Składnia

```C
double acosh( double x );
float acoshf( float x );
long double acoshl( long double x );
#define acosh(X) // Requires C11 or higher

float acosh( float x );  // C++ only
long double acosh( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*y*\
Wartość zmiennoprzecinkowa.

## <a name="return-value"></a>Wartość zwracana

Funkcje **ACOSH —** zwracają odwrotność hyberbolic cosinus (arcus cosinus hiperboliczny) *x*. Te funkcje są prawidłowe dla domeny *x* ≥ 1. Jeśli wartość *x* jest mniejsza niż 1, `errno` jest ustawiona na `EDOM` , a wynikiem jest cichy NaN. Jeśli *x* to cichy NaN, nieokreślony lub nieskończony, zwracana jest ta sama wartość.

|Dane wejściowe|Wyjątek SEH|`_matherr` Oprócz|
|-----------|-------------------|--------------------------|
|QNAN, IND, INF|brak|brak|
|*x* < 1|brak|brak|

## <a name="remarks"></a>Uwagi

Gdy używasz języka C++, możesz wywoływać przeciążenia **ACOSH —** , które pobierają i **`float`** zwracają **`long double`** wartości. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **ACOSH —** zawsze przyjmuje i zwraca **`double`** .

Jeśli używasz \<tgmath.h> `acosh()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek C++|
|--------------|--------------|------------------|
|**ACOSH —**, **acoshf —**, **acoshl**|\<math.h>|\<cmath>|
|**ACOSH — ()** — makro | \<tgmath.h> ||

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_acosh.c
// Compile by using: cl /W4 crt_acosh.c
// This program displays the hyperbolic cosine of pi / 4
// and the arc hyperbolic cosine of the result.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = cosh( pi / 4 );
   y = acosh( x );
   printf( "cosh( %f ) = %f\n", pi/4, x );
   printf( "acosh( %f ) = %f\n", x, y );
}
```

```Output
cosh( 0.785398 ) = 1.324609
acosh( 1.324609 ) = 0.785398
```

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[cosh, coshf, coshl](cosh-coshf-coshl.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)
