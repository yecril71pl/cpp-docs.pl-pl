---
title: log1p —, log1pf —, log1pl2 | Dokumentacja firmy Microsoft
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
- log1p
- log1pf
- log1pl
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
- log1p
- log1pf
- log1pl
- math/log1p
- math/log1pf
- math/log1pl
helpviewer_keywords:
- log1p function
- log1pf function
- log1pl function
ms.assetid: a40d965d-b4f6-42f4-ba27-2395546f7c12
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cf512bcf898a202eee771318afb022642d432b4f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="log1p-log1pf-log1pl"></a>log1p —, log1pf —, log1pl

Oblicza logarytm naturalny 1 oraz określonej wartości.

## <a name="syntax"></a>Składnia

```C
double log1p(
   double x
);

float log1p(
   float x
); //C++ only

long double log1p(
   long double x
); //C++ only

float log1pf(
   float x
);

long double log1pl(
   long double x
);

```

### <a name="parameters"></a>Parametry

*x*<br/>
Argument zmiennoprzecinkowy.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca fizyczna (podstawowa -*e*) logowania z (*x* + 1).

W przeciwnym razie może zwracać jedną z następujących wartości:

|Dane wejściowe|Wynik|Wyjątek SEH|errno|
|-----------|------------|-------------------|-----------|
|+ inf|+ inf|||
|Denormals|Taki sam jak wejście|NIEDOPEŁNIENIE||
|±0|Taki sam jak wejście|||
|-1|-inf|DIVBYZERO|ERANGE —|
|< -1|NaN|NIEPRAWIDŁOWY|EDOM —|
|-inf|NaN|NIEPRAWIDŁOWY|EDOM —|
|±SNaN|Taki sam jak wejście|NIEPRAWIDŁOWY||
|±QNaN nieograniczonego|Taki sam jak wejście|||

**Errno** wartość jest równa erange — Jeśli *x* = -1. **Errno** ma wartość **edom —** Jeśli *x* < -1.

## <a name="remarks"></a>Uwagi

**Log1p —** funkcje mogą być bardziej dokładne niż przy użyciu `log(x + 1)` podczas *x* znajduje się w pobliżu 0.

Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia **log1p —** który przyjmować i zwracać **float** i **długi** **podwójne** typów. W programie C **log1p —** zawsze przyjmuje i zwraca **podwójne**.

Jeśli *x* jest liczbą naturalnego, funkcja zwraca logarytm silni (*x* - 1).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
|--------------|--------------|------------------|
|**log1p —**, **log1pf —**, **log1pl**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
