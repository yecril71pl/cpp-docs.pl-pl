---
title: ASINH asinhf —, asinhl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- asinh
- asinhf
- asinhl
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
- asinhf
- asinhl
- asinh
dev_langs:
- C++
helpviewer_keywords:
- asinh function
- asinhl function
- asinhf function
ms.assetid: 4488babe-1a7e-44ca-8b7b-c2db0a70084f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1387e44b885d0f1ed58113b87d26ba5928768c18
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="asinh-asinhf-asinhl"></a>asinh, asinhf, asinhl

Oblicza sinus hiperboliczny.

## <a name="syntax"></a>Składnia

```C
double asinh( double x );
float asinhf( float x );
long double asinhl( long double x );
```

```cpp
float asinh( float x );  // C++ only
long double asinh( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa.

## <a name="return-value"></a>Wartość zwracana

**Asinh** hyberbolic odwrotny sinus (arcus sinus hiperboliczny) zwracają *x*. Ta funkcja jest prawidłowa w zmiennoprzecinkowe domenie. Jeśli *x* jest NaN quiet — nieokreślony, lub nieskończoności, jest zwracana przez tę samą wartość.

|Dane wejściowe|Wyjątek SEH|**_matherr —** wyjątku|
|-----------|-------------------|--------------------------|
|INF QNAN, IND GRANICACH|brak|brak|

## <a name="remarks"></a>Uwagi

Korzystając z języka C++, można wywoływać przeciążenia **asinh** który przyjmować i zwracać **float** lub **długi** **podwójne** wartości. W programie C **asinh** zawsze przyjmuje i zwraca **podwójne**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek C|Wymagany nagłówek C++|
|--------------|--------------|------------------|
|**ASINH**, **asinhf —**, **asinhl**|\<math.h>|\<cmath > lub \<math.h <|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[cosh, coshf, coshl](cosh-coshf-coshl.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
