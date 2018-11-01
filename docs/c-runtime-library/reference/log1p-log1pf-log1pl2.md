---
title: log1p —, log1pf —, log1pl2
ms.date: 04/05/2018
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
ms.openlocfilehash: e7984367aa4244a927bb9dabc5533a807d74ac1a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524998"
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

Jeśli się powiedzie, zwraca fizyczna (podstawowy -*e*) dziennika systemu (*x* + 1).

W przeciwnym razie może zwracać jedną z następujących wartości:

|Dane wejściowe|Wynik|Wyjątek SEH|numer błędu|
|-----------|------------|-------------------|-----------|
|+ inf|+ inf|||
|Denormals|Takie same jak dane wejściowe|NIEDOPEŁNIENIE||
|±0|Takie same jak dane wejściowe|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|NaN|NIEPRAWIDŁOWY|EDOM|
|-inf|NaN|NIEPRAWIDŁOWY|EDOM|
|±SNaN|Takie same jak dane wejściowe|NIEPRAWIDŁOWY||
|±QNaN czas nieokreślony|Takie same jak dane wejściowe|||

**Errno** wartość jest równa ERANGE, jeśli *x* = -1. **Errno** wartość jest równa **EDOM** Jeśli *x* < wartość -1.

## <a name="remarks"></a>Uwagi

**Log1p —** funkcje mogą być bardziej precyzyjne niż przy użyciu `log(x + 1)` podczas *x* znajduje się w pobliżu 0.

Ponieważ C++ pozwala na przeciążenie, można wywoływać przeciążenia **log1p —** przyjmujące i zwracające **float** i **długie** **double** typów. W programie C **log1p —** zawsze przyjmuje i zwraca **double**.

Jeśli *x* to numer naturalnym, ta funkcja zwraca logarytm silni (*x* - 1).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**log1p —**, **log1pf —**, **log1pl**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
