---
title: tgamma —, tgammaf —, tgammal | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- tgamma
- tgammaf
- tgammal
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
- tgamma
- tgammaf
- tgammal
- math/tgamma
- math/tgammaf
- math/tgammal
dev_langs:
- C++
helpviewer_keywords:
- tgamma function
- tgammaf function
- tgammal function
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7861b297646f4a704134e0d874fad8c924a7ebc8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma, tgammaf, tgammal

Określa funkcja gamma określonej wartości.

## <a name="syntax"></a>Składnia

```C
double tgamma(
   double x
);

float tgamma(
   float x
); //C++ only

long double tgamma(
   long double x
); //C++ only

float tgammaf(
   float x
);

long double tgammal(
   long double x
);

```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość, aby znaleźć wartości gamma.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca gamma *x*.

Błąd zakresu może wystąpić, jeśli wielkość *x* jest za duża albo za mała dla wartości typu danych. Błąd domeny lub zakres błąd może wystąpić, jeśli *x* < = 0.

|Problem|Zwraca|
|-----------|------------|
|x = ±0|±INFINITY|
|x = ujemnej liczby całkowitej|NaN|
|x = - INFINITY|NaN|
|x = + INFINITY|+ INFINITY|
|x = NaN|NaN|
|błąd domeny|NaN|
|Błąd Bieguna|±HUGE_VAL, ±HUGE_VALF lub ±HUGE_VALL|
|Błąd przepełnienia zakresu|±HUGE_VAL, ±HUGE_VALF lub ±HUGE_VALL|
|Błąd zakresu niedopełnienie|prawidłowa wartość zaokrągloną.|

Błędy są zgłaszane jak określono w [_matherr —](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia **tgamma —** który przyjmować i zwracać **float** i **długi** **podwójne** typów. W programie C **tgamma —** zawsze przyjmuje i zwraca **podwójne**.

Jeśli x to liczba naturalna, funkcja zwraca silnię liczby (x-1).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
|--------------|--------------|------------------|
|**tgamma —**, **tgammaf —**, **tgammal**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
