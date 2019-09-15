---
title: exp, expf, expl
ms.date: 04/05/2018
api_name:
- expf
- expl
- exp
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
ms.openlocfilehash: 380f3e861b3ae1ba2f57aa781c32829771612b9f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941638"
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
Wartość zmiennoprzecinkowa do exponentiate logarytmu naturalnego *o podstawie.*

## <a name="return-value"></a>Wartość zwracana

Funkcje **EXP** zwracają wartość wykładniczą parametru zmiennoprzecinkowego *x*, jeśli to się powiedzie. Oznacza to, że wynik to *e*<sup>*x*</sup>, gdzie *e* jest podstawą logarytmu naturalnego. W przypadku przepełnienia funkcja zwraca plik INF (nieskończoność) i **w przypadku niedomiaru zwraca wartość 0** .

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|\+ Cichy NaN, nieokreślony|Brak|_DOMAIN|
|± Nieskończoność|NIEPRAWIDŁOWY|_DOMAIN|
|x ≥ 7.097827e+002|NIEDOKŁADNE + PRZEPEŁNIENIE|PRZEPŁYW|
|X ≤ -7.083964e+002|NIEDOKŁADNY I NIEDOPEŁNIENIE|MIAR|

Funkcja **EXP** ma implementację, która używa Streaming SIMD Extensions 2 (SSE2). Zobacz [_set_SSE2_enable](set-sse2-enable.md) , aby uzyskać informacje i ograniczenia dotyczące korzystania z implementacji SSE2.

## <a name="remarks"></a>Uwagi

C++zezwala na Przeciążenie, dzięki czemu można wywoływać przeciążenia operacji **EXP** , które przyjmują argument **zmiennoprzecinkowy** lub **długi** . W programie C funkcja **EXP** zawsze przyjmuje i zwraca wartość **Double**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek C|Wymagany C++ nagłówek|
|--------------|---------------------|---|
|**EXP**, **expf —** , **Expl**|\<math.h>|\<cmath > lub \<Math. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
