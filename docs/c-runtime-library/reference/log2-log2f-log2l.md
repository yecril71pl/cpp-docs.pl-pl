---
title: log2, log2f, log2l
ms.date: 4/2/2020
api_name:
- log2
- log2l
- log2f
- _o_log2
- _o_log2f
- _o_log2l
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
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
ms.openlocfilehash: 29a1a9e2003091944a4587036c62a49d76333080
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341720"
---
# <a name="log2-log2f-log2l"></a>log2, log2f, log2l

Określa logarytm binarny (base-2) określonej wartości.

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

*X*<br/>
Wartość do określenia logarytmu base-2.

## <a name="return-value"></a>Wartość zwracana

Po sukcesie zwraca log2 *x .*

W przeciwnym razie może zwrócić jedną z następujących wartości:

|Problem|Zwraca|
|-----------|------------|
|*x* < 0|NaN|
|*x* = ±0|-NIESKOŃCZONOŚĆ|
|*x* = 1|+0|
|+NIESKOŃCZONOŚĆ|+NIESKOŃCZONOŚĆ|
|NaN|NaN|
|błąd domeny|NaN|
|błąd bieguna|-HUGE_VAL, -HUGE_VALF lub -HUGE_VALL|

Błędy są zgłaszane w sposób określony w [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Jeśli x jest liczeniem całkowitym, ta funkcja zasadniczo zwraca indeks od zera najbardziej znaczącego bitu 1 *x*.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**log2**, **log2f**, **log2l**|\<> math.h|\<> cmath|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
