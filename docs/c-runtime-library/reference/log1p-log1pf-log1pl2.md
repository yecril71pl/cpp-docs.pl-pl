---
title: log1p, log1pf, log1pl2
ms.date: 04/05/2018
api_name:
- log1p
- log1pf
- log1pl
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
ms.openlocfilehash: aad6675a832e1715c505026fe11ffe77f1f6d275
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953219"
---
# <a name="log1p-log1pf-log1pl"></a>log1p —, log1pf —, log1pl

Oblicza logarytm naturalny z 1 i podanej wartości.

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

Jeśli powiedzie się, zwraca naturalny (podstawowy-*e*) dziennik (*x* + 1).

W przeciwnym razie może zwracać jedną z następujących wartości:

|Dane wejściowe|Wynik|Wyjątek SEH|errno|
|-----------|------------|-------------------|-----------|
|\+ plik inf|\+ plik inf|||
|Denormalne|Analogicznie jak dane wejściowe|MIAR||
|±0|Analogicznie jak dane wejściowe|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|NaN|NIEPRAWIDŁOWY|EDOM|
|-inf|NaN|NIEPRAWIDŁOWY|EDOM|
|±SNaN|Analogicznie jak dane wejściowe|NIEPRAWIDŁOWY||
|QNaN, nieokreślony|Analogicznie jak dane wejściowe|||

Wartość **errno** jest ustawiona na ERANGE, jeśli *x* =-1. Wartość **errno** jest ustawiona na **Edom** , jeśli *x* <-1.

## <a name="remarks"></a>Uwagi

Funkcje **log1p —** mogą być bardziej dokładne niż użycie `log(x + 1)` , gdy *x* jest blisko 0.

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **log1p —** , które pobierają i zwracają **zmiennoprzecinkowe** i **długie** **podwójne** typy. W programie C **log1p —** zawsze przyjmuje i zwraca wartość **Double**.

Jeśli *x* jest liczbą naturalną, ta funkcja Zwraca logarytm o silności (*x* -1).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|C++nagłówki|
|--------------|--------------|------------------|
|**log1p —** , **log1pf —** , **log1pl**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
