---
title: pow, powf, powl
ms.date: 4/2/2020
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: b181959ac05814a673ab11f33e4cfc5a39e3869e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333118"
---
# <a name="pow-powf-powl"></a>pow, powf, powl

Oblicza *x* podniesiony do potęgi *y*.

## <a name="syntax"></a>Składnia

```C
double pow( double x, double y );
float powf( float x, float y );
long double powl( long double x, long double y );
```

```cpp
double pow( double x, int y );  // C++ only
float pow( float x, float y );  // C++ only
float pow( float x, int y );  // C++ only
long double pow( long double x, long double y );  // C++ only
long double pow( long double x, int y );  // C++ only
```

### <a name="parameters"></a>Parametry

*X*<br/>
Podstawowej.

*Y*<br/>
Wykładnik.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość *x*<sup>*y*</sup>. Po przepełnienie lub niedopełnienie nie jest drukowane żaden komunikat o błędzie.

|Wartości x i y|Wartość zwrotu pow|
|-----------------------|-------------------------|
|*x* != 0,0 i *y* == 0,0|1|
|*x* == 0,0 i *y* == 0,0|1|
|*x* == 0,0 i *y* < 0|Inf|

## <a name="remarks"></a>Uwagi

**pow** nie rozpoznaje całkowitych wartości zmiennoprzecinkowych większych niż 2<sup>64</sup> (na przykład 1.0E100).

**pow** ma implementację, która używa streamingu rozszerzeń SIMD 2 (SSE2). Aby uzyskać informacje i ograniczenia dotyczące korzystania z implementacji SSE2, zobacz [_set_SSE2_enable](set-sse2-enable.md).

Ponieważ C++ umożliwia przeciążenie, można wywołać dowolny z różnych przeciążeń **pow**. W programie C **pow** zawsze przyjmuje dwie **podwójne** wartości i zwraca **podwójną** wartość.

Przeciążenie `pow(int, int)` nie jest już dostępne. Jeśli używasz tego przeciążenia, kompilator może emitować [C2668](../../error-messages/compiler-errors-2/compiler-error-c2668.md). Aby uniknąć tego problemu, należy odlecieć pierwszy **parametr,** aby podwoić, **float**lub **long** **double**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|-|-|-|
|**pow**, **powf**, **powl**|\<> math.h|\<>> lub \<cmath>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md) <br/>
[exp, expf, expl](exp-expf.md) <br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md) <br/>
[sqrt, sqrtf, sqrtl](sqrt-sqrtf-sqrtl.md) <br/>
[_CIpow](../../c-runtime-library/cipow.md)<br/>
