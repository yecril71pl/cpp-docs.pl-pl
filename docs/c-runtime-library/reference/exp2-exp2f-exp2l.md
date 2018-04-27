---
title: exp2 —, exp2f —, exp2l | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- exp2
- exp2f
- exp2l
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
- exp2
- math/exp2
- exp2f
- math/exp2f
- exp2l
- math/exp2l
dev_langs:
- C++
helpviewer_keywords:
- exp2 function
- exp2f function
- exp2l function
ms.assetid: 526e3e10-201a-4610-a886-533f44ece344
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 69b7deb8e6e43ded0a3545bc1b33961d977eeb1f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
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

*x*<br/>
Wartość wykładnik.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca wykładnik base-2 *x*, czyli 2<sup>x</sup>. W przeciwnym razie zwraca jedną z następujących wartości:

|Problem|Zwraca|
|-----------|------------|
|*x* = ±0|1|
|*x* = - INFINITY|+0|
|*x* = + INFINITY|+ INFINITY|
|*x* = NaN|NaN|
|Błąd przepełnienia zakresu|+ Huge_val — + HUGE_VALF, lub + HUGE_VALL|
|Błąd zakresu niedopełnienie|Prawidłowego wyniku zaokrągloną|

Błędy są zgłaszane jak określono w [_matherr —](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia **exp2 —** który przyjmować i zwracać **float** i **podwójnej długości** typów. W programie C **exp2 —** zawsze przyjmuje i zwraca **podwójne**.

## <a name="requirements"></a>Wymagania

|Procedura|Nagłówek C|Nagłówek C++|
|-------------|--------------|------------------|
|**EXP**, **expf —**, **expl**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
