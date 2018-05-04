---
title: Pow, powf — powl — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- powl
- pow
- powf
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
- powl
- pow
- _powl
- powf
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5daf7348198cb6f3ba0186eb4586b2486548f6f5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="pow-powf-powl"></a>pow, powf, powl

Oblicza *x* podniesionej do potęgi równej *y*.

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

*x*<br/>
Podstawa.

*y*<br/>
Wykładnik.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość *x*<sup>*y*</sup>. Żaden komunikat o błędzie jest wydrukowany przepełnienie lub niedomiar.

|Wartości x i y|Wartość zwracana pow|
|-----------------------|-------------------------|
|*x* ! = 0,0 i *y* == 0.0|1|
|*x* == 0.0 i *y* == 0.0|1|
|*x* == 0.0 i *y* < 0|INF|

## <a name="remarks"></a>Uwagi

**Pow** nie rozpoznaje wartości całkowitych wartości zmiennoprzecinkowych większej niż 2<sup>64</sup> (na przykład 1.0E100).

**Pow** ma implementację, która używa Streaming SIMD Extensions 2 (SSE2). Aby uzyskać informacje i ograniczenia dotyczące korzystania z implementacji SSE2, zobacz [_set_sse2_enable —](set-sse2-enable.md).

Ponieważ C++ pozwala przeładowanie, można wywołać żadnego z różnych przeciążeń **pow**. W programie C **pow** zawsze ma dwa **podwójne** wartości i zwraca **podwójne** wartość.

`pow(int, int)` Przeciążenia nie jest już dostępny. Jeśli używasz tego przeciążenia, kompilator może emitować [C2668](../../error-messages/compiler-errors-2/compiler-error-c2668.md). Aby uniknąć tego problemu, należy rzutować pierwszy parametr **podwójne**, **float**, lub **długi** **podwójne**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymaganego nagłówka (C++)|
|-|-|-|
|**Pow**, **powf —**, **powl —**|\<math.h>|\<Math.h > lub \<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md) <br/>
[exp, expf, expl](exp-expf.md) <br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md) <br/>
[sqrt, sqrtf, sqrtl](sqrt-sqrtf-sqrtl.md) <br/>
[_CIpow](../../c-runtime-library/cipow.md)<br/>
