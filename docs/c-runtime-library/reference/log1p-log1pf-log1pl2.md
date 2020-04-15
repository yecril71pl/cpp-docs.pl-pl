---
title: log1p, log1pf, log1pl2
ms.date: 4/2/2020
api_name:
- log1p
- log1pf
- log1pl
- _o_log1p
- _o_log1pf
- _o_log1pl
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
ms.openlocfilehash: b4e077f5b806dbe38ed4a4f4e8eef0259170cb7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341807"
---
# <a name="log1p-log1pf-log1pl"></a>log1p, log1pf, log1pl

Oblicza logarytm naturalny 1 plus określoną wartość.

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

*X*<br/>
Argument zmiennoprzecinowy.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwraca naturalny (base-*e)* dziennik (*x* + 1).

W przeciwnym razie może zwrócić jedną z następujących wartości:

|Dane wejściowe|Wynik|Wyjątek SEH|Errno|
|-----------|------------|-------------------|-----------|
|+inf|+inf|||
|Denormals ( Denormals )|Tak samo jak dane wejściowe|Niedomiar||
|±0|Tak samo jak dane wejściowe|||
|-1|-inf|DIVBYZERO ( DIVBYZERO )|Układ ERANGE|
|< -1|Nan|Nieprawidłowy|Edom|
|-inf|Nan|Nieprawidłowy|Edom|
|±SNan|Tak samo jak dane wejściowe|Nieprawidłowy||
|±QNaN, nieokreślony|Tak samo jak dane wejściowe|||

Wartość **errno** jest ustawiona na ERANGE, jeśli *x* = -1. Wartość **errno** jest ustawiona na **EDOM,** jeśli *x* < -1.

## <a name="remarks"></a>Uwagi

Funkcje **log1p** mogą być `log(x + 1)` dokładniejsze niż przy użyciu *x* jest w pobliżu 0.

Ponieważ C++ umożliwia przeciążenie, można wywołać przeciążenia **log1p,** które przyjmują i zwracają **float** i **długie** **typy podwójne.** W programie C **log1p** zawsze przyjmuje i zwraca **podwójny**.

Jeśli *x* jest liczbą naturalną, ta funkcja zwraca logarytm czynnika (*x* - 1).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**log1p**, **log1pf**, **log1pl**|\<> math.h|\<> cmath|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
