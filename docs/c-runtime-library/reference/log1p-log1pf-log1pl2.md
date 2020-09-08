---
title: log1p, log1pf, log1pl2
description: Dokumentacja interfejsu API dla log1p —, log1pf —, log1pl2; który Oblicz logarytm naturalny z 1 i określoną wartość.
ms.date: 9/1/2020
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 8858d761428d4dad6e3fe836b82041ae92f1827a
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556233"
---
# <a name="log1p-log1pf-log1pl"></a>log1p —, log1pf —, log1pl

Oblicza logarytm naturalny z 1 i podanej wartości.

## <a name="syntax"></a>Składnia

```C
double log1p(
   double x
);
float log1pf(
   float x
);
long double log1pl(
   long double x
);

#define log1p(X) // Requires C11 or higher

float log1p(
   float x
); //C++ only

long double log1p(
   long double x
); //C++ only
```

### <a name="parameters"></a>Parametry

*y*\
Argument zmiennoprzecinkowy.

## <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, zwraca naturalny (podstawowy-*e*) dziennik (*x* + 1).

W przeciwnym razie może zwracać jedną z następujących wartości:

|Dane wejściowe|Wynik|Wyjątek SEH|errno|
|-----------|------------|-------------------|-----------|
|+ plik inf|+ plik inf|||
|Denormalne|Analogicznie jak dane wejściowe|MIAR||
|± 0|Analogicznie jak dane wejściowe|||
|-1|-inf|DIVBYZERO|ERANGE|
|<-1|NaN|Nieprawidłowy|EDOM|
|-inf|NaN|Nieprawidłowy|EDOM|
|SNaN|Analogicznie jak dane wejściowe|Nieprawidłowy||
|QNaN, nieokreślony|Analogicznie jak dane wejściowe|||

Wartość **errno** jest ustawiona na ERANGE, jeśli *x* =-1. Wartość **errno** jest ustawiona na **Edom** , jeśli *x* <-1.

## <a name="remarks"></a>Uwagi

Funkcje **log1p —** mogą być bardziej dokładne niż użycie, `log(x + 1)` gdy *x* jest blisko 0.

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **log1p —** , które pobierają i zwracają **`float`** **`long double`** typy. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **log1p —** zawsze przyjmuje i zwraca **`double`** .

Jeśli używasz \<tgmath.h> `log1p()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

Jeśli *x* jest liczbą naturalną, ta funkcja Zwraca logarytm o silności (*x* -1).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek C++|
|--------------|--------------|------------------|
|**log1p —**, **log1pf —**, **log1pl**|\<math.h>|\<cmath>|
|**log1p —** — makro | \<tgmath.h> ||

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne odwołanie do funkcji](crt-alphabetical-function-reference.md)\
[log2 —, log2f —, log2l](log2-log2f-log2l.md)\
[log, logf, log10, log10f](log-logf-log10-log10f.md)
