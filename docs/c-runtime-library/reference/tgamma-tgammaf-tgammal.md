---
title: tgamma, tgammaf, tgammal
ms.date: 04/05/2018
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
helpviewer_keywords:
- tgamma function
- tgammaf function
- tgammal function
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
ms.openlocfilehash: 6cfe455b0e9e83cd5283d36fed33ca168bc97d0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570667"
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma, tgammaf, tgammal

Określa funkcja gamma od określonej wartości.

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
Wartość do znalezienia wartości gamma.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca wartości gamma *x*.

Błąd zakresu może wystąpić, jeśli wielkość *x* jest za duży lub za mały dla typu danych. Błąd domeny lub zakresu błąd może wystąpić, jeśli *x* < = 0.

|Problem|Wróć|
|-----------|------------|
|x = ±0|±INFINITY|
|x = ujemną liczbę całkowitą|NaN|
|x = - NIESKOŃCZONOŚĆ|NaN|
|x =, + NIESKOŃCZONOŚĆ|+ INFINITY|
|x = NaN|NaN|
|domeny błędów|NaN|
|Błąd Bieguna|±HUGE_VAL, ±HUGE_VALF lub ±HUGE_VALL|
|Błąd w zakresie przepełnienia|±HUGE_VAL, ±HUGE_VALF lub ±HUGE_VALL|
|Błąd zakresu niedopełnienie|Prawidłowe wartości po zaokrągleniu zgodnym.|

Błędy są zgłaszane określonej [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na przeciążenie, można wywoływać przeciążenia **tgamma —** przyjmujące i zwracające **float** i **długie** **double** typów. W programie C **tgamma —** zawsze przyjmuje i zwraca **double**.

Gdy wartość x jest numer naturalnym, ta funkcja zwraca silnię (x-1).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**tgamma —**, **tgammaf —**, **tgammal**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
