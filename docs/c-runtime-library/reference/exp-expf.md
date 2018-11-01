---
title: exp, expf, expl
ms.date: 04/05/2018
apiname:
- expf
- expl
- exp
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
- _expl
- expf
- expl
- exp
helpviewer_keywords:
- exponential calculations
- expf function
- expl function
- calculating exponentials
- exp function
ms.assetid: 7070016d-1143-407e-9e9a-6b059bb88867
ms.openlocfilehash: b9fb38adcc442e60864ec632cd92793f16e47502
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596758"
---
# <a name="exp-expf-expl"></a>exp, expf, expl

Oblicza wartość wykładniczą.

## <a name="syntax"></a>Składnia

```C
double exp(
   double x
);
float exp(
   float x
);  // C++ only
long double exp(
   long double x
);  // C++ only
float expf(
   float x
);
long double expl(
   long double x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Zmiennoprzecinkowa wartość exponentiate podstawa logarytmu naturalnego *e* przez.

## <a name="return-value"></a>Wartość zwracana

**Exp** funkcje zwracają wartość parametru zmiennoprzecinkowego *x*, jeśli to się powiedzie. Wynik jest *e*<sup>*x*</sup>, gdzie *e* jest podstawą logarytmu naturalnego. W przepełnieniu, funkcja zwraca INF (nieskończoność) i na niedopełnienie **exp** zwraca wartość 0.

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|Ciche NaN granicach, nieokreślone|Brak|_DOMAIN|
|Infinity granicach|NIEPRAWIDŁOWY|_DOMAIN|
|x ≥ 7.097827e+002|NIEDOKŁADNY + PRZEPEŁNIENIA|PRZEPEŁNIENIA|
|X ≤ -7.083964e+002|+ NIEDOKŁADNY, NIEDOPEŁNIENIE|NIEDOPEŁNIENIE|

**Exp** funkcja ma implementację, która używa Streaming SIMD Extensions 2 (SSE2). Zobacz [_set_sse2_enable —](set-sse2-enable.md) informacje i ograniczenia dotyczące przy użyciu implementacji SSE2.

## <a name="remarks"></a>Uwagi

Język C++ pozwala na przeciążenie, można więc wywoływać przeciążenia **exp** o **float** lub **typu long double** argumentu. W programie C **exp** zawsze przyjmuje i zwraca **double**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek języka C|Wymagany nagłówek C++|
|--------------|---------------------|---|
|**EXP**, **expf —**, **expl**|\<math.h>|\<cmath > lub \<math.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_exp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.302585093, y;

   y = exp( x );
   printf( "exp( %f ) = %f\n", x, y );
}
```

```Output
exp( 2.302585 ) = 10.000000
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
[_CIexp](../../c-runtime-library/ciexp.md)<br/>
