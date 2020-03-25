---
title: acosh, acoshf, acoshl
ms.date: 04/05/2018
api_name:
- acoshf
- acosh
- acoshl
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
ms.openlocfilehash: da1d6024cc9f00ebfc7696ddedf92ea9f25728a1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170361"
---
# <a name="acosh-acoshf-acoshl"></a>acosh, acoshf, acoshl

Oblicza odwrotny cosinus hiperboliczny.

## <a name="syntax"></a>Składnia

```C
double acosh( double x );
float acoshf( float x );
long double acoshl( long double x );
```

```cpp
float acosh( float x );  // C++ only
long double acosh( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*y*<br/>
Wartość zmiennoprzecinkowa.

## <a name="return-value"></a>Wartość zwracana

Funkcje **ACOSH —** zwracają odwrotność hyberbolic cosinus (arcus cosinus hiperboliczny) *x*. Te funkcje są prawidłowe dla domeny *x* ≥ 1. Jeśli wartość *x* jest mniejsza niż 1, `errno` jest ustawiona na `EDOM`, a wynikiem jest cichy NaN. Jeśli *x* to cichy NaN, nieokreślony lub nieskończony, zwracana jest ta sama wartość.

|Dane wejściowe|Wyjątek SEH|Wyjątek `_matherr`|
|-----------|-------------------|--------------------------|
|QNAN, IND, INF|brak|brak|
|*x* < 1|brak|brak|

## <a name="remarks"></a>Uwagi

W przypadku korzystania C++z programu można wywoływać przeciążenia **ACOSH —** , które pobierają i zwracają wartości **zmiennoprzecinkowe** lub **długie** o **podwójnej precyzji** . W programie C **ACOSH —** zawsze przyjmuje i zwraca wartość **Double**.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|C++nagłówki|
|--------------|--------------|------------------|
|**ACOSH —** , **acoshf —** , **acoshl**|\<> Math. h|\<cmath >|

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

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[cosh, coshf, coshl](cosh-coshf-coshl.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)
