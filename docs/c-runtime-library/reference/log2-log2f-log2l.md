---
title: log2 log2f —, log2l | Dokumentacja firmy Microsoft
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
- log2
- log2l
- log2f
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
dev_langs:
- C++
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ddde058c61bfbe83013111e3376a84bd463cd650
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="log2-log2f-log2l"></a>log2 log2f —, log2l

Określa binarne logarytmu (base-2) w określonej wartości.

## <a name="syntax"></a>Składnia

```C
double log2(
   double x
);

float log2(
   float x
); //C++ only

long double log2(
   long double x
); //C++ only

float log2f(
   float x
);

long double log2l(
   long double x
);

```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość, aby określić logarytmu base-2.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia zwraca zwracać log2 *x*.

W przeciwnym razie może zwracać jedną z następujących wartości:

|Problem|Zwraca|
|-----------|------------|
|*x* < 0|NaN|
|*x* = ±0|— INFINITY|
|*x* = 1|+0|
|+ INFINITY|+ INFINITY|
|NaN|NaN|
|błąd domeny|NaN|
|Błąd Bieguna|-Huge_val — i - HUGE_VALF, lub - HUGE_VALL|

Błędy są zgłaszane jak określono w [_matherr —](matherr.md).

## <a name="remarks"></a>Uwagi

Jeśli x jest liczbą całkowitą, funkcja zwraca zasadniczo liczony od zera indeks najbardziej znaczącego bitu 1 *x*.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
|--------------|--------------|------------------|
|**log2**, **log2f —**, **log2l**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
