---
title: log2, log2f, log2l
ms.date: 04/05/2018
api_name:
- log2
- log2l
- log2f
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
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
ms.openlocfilehash: bf1734ea2f96fa1c09b3b0d1f43b681fc31c8f9f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953167"
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
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość określająca logarytm dziesiętny.

## <a name="return-value"></a>Wartość zwracana

Po powodzeniu zwraca wartość Return log2 — *x*.

W przeciwnym razie może zwracać jedną z następujących wartości:

|Problem|przesłać|
|-----------|------------|
|*x* < 0|NaN|
|*x* = ± 0|-NIESKOŃCZONOŚĆ|
|*x* = 1|+0|
|\+ NIESKOŃCZONOŚĆ|\+ NIESKOŃCZONOŚĆ|
|NaN|NaN|
|błąd domeny|NaN|
|błąd słupka|-HUGE_VAL,-HUGE_VALF lub-HUGE_VALL|

Błędy są raportowane zgodnie z opisem w [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Jeśli x jest liczbą całkowitą, ta funkcja zasadniczo zwraca indeks (liczony od zera) najbardziej znaczącej 1 bit *x*.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|C++nagłówki|
|--------------|--------------|------------------|
|**log2 —** , **log2f —** , **log2l**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
