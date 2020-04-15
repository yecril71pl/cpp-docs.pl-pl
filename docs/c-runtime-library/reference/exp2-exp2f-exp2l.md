---
title: exp2, exp2f, exp2l
ms.date: 4/2/2020
api_name:
- exp2
- exp2f
- exp2l
- _o_exp2
- _o_exp2f
- _o_exp2l
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
- exp2
- math/exp2
- exp2f
- math/exp2f
- exp2l
- math/exp2l
helpviewer_keywords:
- exp2 function
- exp2f function
- exp2l function
ms.assetid: 526e3e10-201a-4610-a886-533f44ece344
ms.openlocfilehash: a5df1a216b4565f013a4c42b4ef4369b5b7f9b04
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347584"
---
# <a name="exp2-exp2f-exp2l"></a>exp2, exp2f, exp2l

Oblicza 2 podniesione do określonej wartości.

## <a name="syntax"></a>Składnia

```C
double exp2(
   double x
);

float exp2(
   float x
);  // C++ only

long double exp2(
   long double x
); // C++ only

float exp2f(
   float x
);

long double exp2l(
   long double x
);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Wartość wykładnika.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwraca wykładnik base-2 *x*, czyli 2<sup>x</sup>. W przeciwnym razie zwraca jedną z następujących wartości:

|Problem|Zwraca|
|-----------|------------|
|*x* = ±0|1|
|*x* = -NIESKOŃCZONOŚĆ|+0|
|*x* = +NIESKOŃCZONOŚĆ|+NIESKOŃCZONOŚĆ|
|*x* = NaN|NaN|
|Błąd zakresu przepełnienia|+HUGE_VAL, +HUGE_VALF lub +HUGE_VALL|
|Błąd zakresu niedopełnienia|Prawidłowy wynik po zaokrągleniu|

Błędy są zgłaszane w sposób określony w [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ umożliwia przeciążenie, można wywołać przeciążenia **exp2,** które przyjmują i zwracają **float** i **długie typy podwójne.** W programie C **exp2** zawsze przyjmuje i zwraca **podwójny**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Nagłówek C|Nagłówek języka C++|
|-------------|--------------|------------------|
|**exp**, **expf**, **expl**|\<> math.h|\<> cmath|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
