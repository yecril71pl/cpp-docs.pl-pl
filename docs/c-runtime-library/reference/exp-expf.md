---
title: EXP, expf —, expl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- exponential calculations
- expf function
- expl function
- calculating exponentials
- exp function
ms.assetid: 7070016d-1143-407e-9e9a-6b059bb88867
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 580c756c53f1a177506230f669fabd2be39d71d6
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="exp-expf-expl"></a>exp, expf, expl

Oblicza wykładniczej.

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
Zmiennoprzecinkowe do wartości exponentiate podstawa logarytmu naturalnego *e* przez.

## <a name="return-value"></a>Wartość zwracana

**Exp** zwracają wykładniczej wartość parametru zmiennoprzecinkowego *x*, jeśli to się powiedzie. Wynik jest *e*<sup>*x*</sup>, gdzie *e* jest podstawą logarytmu naturalnego. Przepełnienie, funkcja zwraca INF (nieskończoności) i niedopełnienie **exp** zwraca wartość 0.

|Dane wejściowe|Wyjątek SEH|Matherr — wyjątek|
|-----------|-------------------|-----------------------|
|Quiet NaN granicach, nieokreślone|Brak|_DOMAIN|
|Infinity granicach|NIEPRAWIDŁOWY|_DOMAIN|
|x ≥ 7.097827e+002|NIEDOKŁADNY + PRZEPEŁNIENIA|PRZEPEŁNIENIE|
|X ≤ -7.083964e+002|NIEDOPEŁNIENIE NIEDOKŁADNYMI +|NIEDOPEŁNIENIE|

**Exp** funkcja ma implementację, która używa Streaming SIMD Extensions 2 (SSE2). Zobacz [_set_sse2_enable —](set-sse2-enable.md) informacje i ograniczenia dotyczące używania implementacji SSE2.

## <a name="remarks"></a>Uwagi

C++ pozwala przeładowanie, dlatego można wywoływać przeciążenia **exp** które trwają **float** lub **podwójnej długości** argumentu. W programie C **exp** zawsze przyjmuje i zwraca **podwójne**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek C|Wymagany nagłówek C++|
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
