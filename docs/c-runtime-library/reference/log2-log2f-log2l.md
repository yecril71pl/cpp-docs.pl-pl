---
title: log2 log2f —, log2l
ms.date: 04/05/2018
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
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
ms.openlocfilehash: d70d074b13b0f24f1f040ef0e861e073e303ac7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285942"
---
# <a name="log2-log2f-log2l"></a>log2 log2f —, log2l

Określa binarne logarytmu (base 2) od określonej wartości.

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
Wartość do określenia logarytm base 2.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia zwraca zwracają log2 *x*.

W przeciwnym razie może zwracać jedną z następujących wartości:

|Problem|Wróć|
|-----------|------------|
|*x* < 0|NaN|
|*x* = ±0|-NIESKOŃCZONOŚĆ.|
|*x* = 1|+0|
|+ INFINITY|+ INFINITY|
|NaN|NaN|
|domeny błędów|NaN|
|Błąd Bieguna|— HUGE_VAL, - HUGE_VALF, lub - HUGE_VALL|

Błędy są zgłaszane określonej [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Gdy wartość x jest liczbą całkowitą, ta funkcja zwraca zasadniczo liczony od zera indeks najbardziej znaczącego bitu 1 *x*.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**log2 —**, **log2f —**, **log2l**|\<math.h>|\<cmath>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
