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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: cbf303b2b92afd83a1c3181dc98a1dbdcd639c1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347598"
---
# <a name="exp-expf-expl"></a>exp, expf, expl

Oblicza wykładnicze.

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

*X*<br/>
Wartość zmiennoprzecinkowa do wykładnicy podstawy logarytmu naturalnego *e* przez.

## <a name="return-value"></a>Wartość zwracana

Funkcje **exp** zwracają wartość wykładniczą parametru zmiennoprzecinkowego, *x*, jeśli zakończy się pomyślnie. Oznacza to, że wynik jest *e*<sup>*x*</sup>, gdzie *e* jest podstawą logarytmu naturalnego. W przypadku przepełnienia funkcja zwraca INF (nieskończoność) i przy niedopełnionym, **exp** zwraca wartość 0.

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|± Cichy NaN, nieokreślony|Brak|_DOMAIN|
|± Nieskończoność|Nieprawidłowy|_DOMAIN|
|x ≥ 7,097827e+002|INEXACT+OVERFLOW|Przepełnienie|
|X ≤ -7,083964e+002|INEXACT+UNDERFLOW|Niedomiar|

Funkcja **exp** ma implementację, która używa rozszerzenia SIMD przesyłania strumieniowego 2 (SSE2). Zobacz [_set_SSE2_enable,](set-sse2-enable.md) aby uzyskać informacje i ograniczenia dotyczące korzystania z implementacji SSE2.

## <a name="remarks"></a>Uwagi

C++ umożliwia przeciążenie, dzięki czemu można wywołać przeciążenia **exp,** które przyjmują **float** lub **long double** argument. W programie C **exp** zawsze przyjmuje i zwraca **podwójny**plik .

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek C|Wymagany nagłówek języka C++|
|--------------|---------------------|---|
|**exp**, **expf**, **expl**|\<> math.h|\<cmath> lub \<math.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
[_CIexp](../../c-runtime-library/ciexp.md)<br/>
