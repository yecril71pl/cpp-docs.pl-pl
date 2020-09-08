---
title: log2, log2f, log2l
description: Dokumentacja interfejsu API dla log2 —, log2f — i log2l; który określa LOGARYTM binarny (Base-2) określonej wartości.
ms.date: 9/1/2020
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
ms.openlocfilehash: 37319560891dbd64030495750aaf347d9dedd7e7
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555361"
---
# <a name="log2-log2f-log2l"></a>log2, log2f, log2l

Określa LOGARYTM binarny (Base-2) określonej wartości.

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

#define log2(X) // Requires C11 or higher
```

### <a name="parameters"></a>Parametry

*y*\
Wartość określająca logarytm dziesiętny.

## <a name="return-value"></a>Wartość zwracana

Po powodzeniu zwraca wartość Return log2 — *x*.

W przeciwnym razie może zwracać jedną z następujących wartości:

|Problem|Przesłać|
|-----------|------------|
|*x* < 0|NaN|
|*x* = ± 0|-NIESKOŃCZONość|
|*x* = 1|+0|
|+ NIESKOŃCZONość|+ NIESKOŃCZONość|
|NaN|NaN|
|błąd domeny|NaN|
|błąd słupka|-HUGE_VAL,-HUGE_VALF lub-HUGE_VALL|

Błędy są raportowane zgodnie z opisem w [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Jeśli *x* jest liczbą całkowitą, ta funkcja zasadniczo zwraca indeks (liczony od zera) najbardziej znaczącej 1 bit *x*.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek C++|
|--------------|--------------|------------------|
|**log2 —**, **log2f —**, **log2l**|\<math.h>|\<cmath>|
|**log2 —** — makro | \<tgmath.h> ||

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
