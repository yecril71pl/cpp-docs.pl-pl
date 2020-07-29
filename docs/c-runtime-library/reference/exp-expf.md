---
title: exp, expf, expl
ms.date: 4/2/2020
api_name:
- expf
- expl
- exp
- _o_exp
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
ms.openlocfilehash: 9872a83ba3ec5346b7aed5fb51ee837d3ed827aa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234175"
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
|+ Cichy NaN, nieokreślony|Brak|_DOMAIN|
|± Nieskończoność|Nieprawidłowy|_DOMAIN|
|x ≥ 7.097827 e + 002|niedokładne + przepełnienie|PRZEPŁYW|
|X ≤-7.083964 e + 002|niedokładny i niedopełnienie|MIAR|

Funkcja **EXP** ma implementację, która używa Streaming SIMD Extensions 2 (SSE2). Zobacz [_set_SSE2_enable](set-sse2-enable.md) , aby uzyskać informacje i ograniczenia dotyczące korzystania z implementacji SSE2.

## <a name="remarks"></a>Uwagi

Język C++ pozwala na Przeciążenie, dlatego można wywoływać przeciążenia, **które** przyjmują **`float`** argument lub **`long double`** . W programie C funkcja **EXP** zawsze przyjmuje i zwraca **`double`** .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek C|Wymagany nagłówek C++|
|--------------|---------------------|---|
|**EXP**, **expf —**, **Expl**|\<math.h>|\<cmath> lub \<math.h>|

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

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
[_CIexp](../../c-runtime-library/ciexp.md)<br/>
