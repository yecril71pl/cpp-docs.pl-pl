---
title: pow, powf, powl
description: Dokumentacja interfejsu API dla pow, powf — i POWL; który obliczy wzrost do potęgi.
ms.date: 08/31/2020
api_name:
- powl
- pow
- powf
- _o_pow
- _o_powf
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
- powl
- pow
- _powl
- powf
helpviewer_keywords:
- exponential calculations
- powl function
- _powl function
- exponentiation
- powers, calculating
- calculating exponentials
- powf function
- pow function
ms.assetid: e75c33ed-2e59-48b1-be40-81da917324f1
ms.openlocfilehash: 8fb6679e2b509274b4ea60c410a81b54df866416
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505571"
---
# <a name="pow-powf-powl"></a>pow, powf, powl

Oblicza wartość *x* podniesioną do potęgi *y*.

## <a name="syntax"></a>Składnia

```C
double pow( double x, double y );
float powf( float x, float y );
long double powl( long double x, long double y );
define pow(X, Y) // Requires C11 or higher

double pow( double x, int y );  // C++ only
float pow( float x, float y );  // C++ only
float pow( float x, int y );  // C++ only
long double pow( long double x, long double y );  // C++ only
long double pow( long double x, int y );  // C++ only
```

### <a name="parameters"></a>Parametry

*y*\
Opiera.

*t*\
Zapis.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość *x*<sup>*y*</sup>. Żaden komunikat o błędzie nie jest drukowany w przypadku przepełnienia lub niedomiaru.

|Wartości x i y|Wartość zwracana pow|
|-----------------------|-------------------------|
|*x* ! = 0,0 i *y* = = 0,0|1|
|*x* = = 0,0 i *y* = = 0,0|1|
|*x* = = 0,0 i *y* < 0|INF|

## <a name="remarks"></a>Uwagi

**pow** nie rozpoznaje całkowitych wartości zmiennoprzecinkowych większych niż 2<sup>64</sup> (na przykład 1,0 E100).

**pow** ma implementację, która używa Streaming SIMD Extensions 2 (SSE2). Informacje i ograniczenia dotyczące korzystania z implementacji SSE2 można znaleźć w temacie [_set_SSE2_enable](set-sse2-enable.md).

Ponieważ C++ pozwala na Przeciążenie, można wywołać dowolne z różnych przeciążeń **pow**. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **pow** zawsze przyjmuje dwie **`double`** wartości i zwraca **`double`** wartość.

Jeśli używasz \<tgmath.h> `pow()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

`pow(int, int)`Przeciążenie nie jest już dostępne. W przypadku użycia tego przeciążenia kompilator może emitować [C2668](../../error-messages/compiler-errors-2/compiler-error-c2668.md). Aby uniknąć tego problemu, należy rzutować pierwszy parametr na **`double`** , **`float`** , lub **`long double`** .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|-|-|-|
|**pow**, **powf —**, **POWL**|\<math.h>|\<math.h> lub \<cmath>|
|**pow** — makro | \<tgmath.h> ||

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_pow.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.0, y = 3.0, z;

   z = pow( x, y );
   printf( "%.1f to the power of %.1f is %.1f\n", x, y, z );
}
```

```Output
2.0 to the power of 3.0 is 8.0
```

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md) <br/>
[exp, expf, expl](exp-expf.md) <br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md) <br/>
[sqrt, sqrtf, sqrtl](sqrt-sqrtf-sqrtl.md) <br/>
[_CIpow](../../c-runtime-library/cipow.md)<br/>
