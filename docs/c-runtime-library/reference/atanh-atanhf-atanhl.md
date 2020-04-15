---
title: atanh, atanhf, atanhl
ms.date: 4/2/2020
api_name:
- atanhl
- atanhf
- atanh
- _o_atanh
- _o_atanhf
- _o_atanhl
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
- atanhl
- atanhf
- atanh
helpviewer_keywords:
- atanhf function
- atanhl function
- atanh funciton
ms.assetid: 83a43b5b-2580-4461-854f-dc84236d9f32
ms.openlocfilehash: ef4a37c1ae76a88fd547b76c510097994a160253
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350132"
---
# <a name="atanh-atanhf-atanhl"></a>atanh, atanhf, atanhl

Oblicza odwrotną styczną hiperboliczną.

## <a name="syntax"></a>Składnia

```C
double atanh( double x );
float atanhf( float x );
long double atanhl( long double x );
```

```cpp
float atanh( float x );  // C++ only
long double atanh( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*X*<br/>
Wartość zmiennoprzecinku.

## <a name="return-value"></a>Wartość zwracana

Funkcje **atanh** zwracają odwrotną styczną hipoberboliczną (łuk hiperboliczny styczny) *x*. Jeśli *x* jest większa niż 1 lub mniejsza niż -1, **errno** jest ustawiona na **EDOM,** a wynik jest cichy NaN. Jeśli *x* jest równa 1 lub -1, zwracana jest dodatnia lub ujemna nieskończoność, a **errno** jest ustawiona na **ERANGE**.

|Dane wejściowe|Wyjątek SEH|**Matherr (matherr)** Wyjątek|
|-----------|-------------------|-------------------------|
|± QNAN, IND|brak|brak|
|*X* ≥ 1; *x* ≤ -1|brak|brak|

## <a name="remarks"></a>Uwagi

Ponieważ C++ umożliwia przeciążenie, można wywołać przeciążenia **atanh,** które przyjmują i zwracają **float** lub **długie** **podwójne** wartości. W programie **C, atanh** zawsze ma i zwraca **dwukrotnie**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**atanh**, **atanhf**, **atanhl**|\<> math.h|\<cmath> lub \<math.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_atanh.c
// This program displays the hyperbolic tangent of pi / 4
// and the arc hyperbolic tangent of the result.
//

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = tanh( pi / 4 );
   y = atanh( x );
   printf( "tanh( %f ) = %f\n", pi/4, x );
   printf( "atanh( %f ) = %f\n", x, y );
}
```

```Output
tanh( 0.785398 ) = 0.655794
atanh( 0.655794 ) = 0.785398
```

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[cosh, coshf, coshl](cosh-coshf-coshl.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
