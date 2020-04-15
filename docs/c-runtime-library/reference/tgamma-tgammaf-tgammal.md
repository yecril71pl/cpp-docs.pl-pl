---
title: tgamma, tgammaf, tgammal
ms.date: 4/2/2020
api_name:
- tgamma
- tgammaf
- tgammal
- _o_tgamma
- _o_tgammaf
- _o_tgammal
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
ms.openlocfilehash: d7e27e8b818a16cb0c18f58e2f40c0090dd13ecf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362505"
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma, tgammaf, tgammal

Określa funkcję gamma określonej wartości.

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

*X*<br/>
Wartość, aby znaleźć gamma.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwraca gamma *x*.

Błąd zakresu może wystąpić, jeśli wielkość *x* jest zbyt duża lub zbyt mała dla typu danych. Jeśli *x* <= 0 może wystąpić błąd domeny lub zakres.

|Problem|Zwraca|
|-----------|------------|
|x = ±0|±NIESKOŃCZONOŚĆ|
|x = ujemna liczba całkowita|NaN|
|x = -NIESKOŃCZONOŚĆ|NaN|
|x = +NIESKOŃCZONOŚĆ|+NIESKOŃCZONOŚĆ|
|x = NaN|NaN|
|błąd domeny|NaN|
|błąd bieguna|±HUGE_VAL, ±HUGE_VALF lub ±HUGE_VALL|
|błąd zakresu przepełnienia|±HUGE_VAL, ±HUGE_VALF lub ±HUGE_VALL|
|Błąd zakresu niedopełnienia|prawidłową wartość, po zaokrągleniu.|

Błędy są zgłaszane w sposób określony w [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ umożliwia przeciążenie, można wywołać przeciążenia **tgamma,** które biorą i zwracają **float** i **długie** **podwójne** typy. W programie **C, tgamma** zawsze ma i zwraca **podwójne**.

Jeśli x jest liczbą naturalną, ta funkcja zwraca faktor (x-1).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**tgamma**, **tgammaf**, **tgammal**|\<> math.h|\<> cmath|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
