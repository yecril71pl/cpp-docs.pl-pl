---
title: lgamma, lgammaf, lgammal
ms.date: 4/2/2020
api_name:
- lgamma
- lgammaf
- lgammal
- _o_lgamma
- _o_lgammaf
- _o_lgammal
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
- lgamma
- lgammaf
- lgammal
- math/lgamma
- math/lgammaf
- math/lgammal
helpviewer_keywords:
- lgamma function
- lgammal function
- lgammaf function
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
ms.openlocfilehash: e2bdfbeac7b995be0b589156437a3ded39114adf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342163"
---
# <a name="lgamma-lgammaf-lgammal"></a>lgamma, lgammaf, lgammal

Określa logarytm naturalny wartości bezwzględnej funkcji gamma określonej wartości.

## <a name="syntax"></a>Składnia

```C
double lgamma( double x );
float lgammaf( float x );
long double lgammal( long double x );
```

```cpp
float lgamma( float x ); //C++ only
long double lgamma( long double x ); //C++ only
```

### <a name="parameters"></a>Parametry

*X*<br/>
Wartość do obliczenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwróć logarytm naturalny wartości bezwzględnej funkcji gamma *x*.

|Problem|Zwraca|
|-----------|------------|
|*x* = NaN|NaN|
|*x* = ±0|+NIESKOŃCZONOŚĆ|
|*x*= ujemna liczba całkowita|+NIESKOŃCZONOŚĆ|
|±NIESKOŃCZONOŚĆ|+NIESKOŃCZONOŚĆ|
|błąd bieguna|+HUGE_VAL, +HUGE_VALF lub +HUGE_VALL|
|błąd zakresu przepełnienia|±HUGE_VAL, ±HUGE_VALF lub ±HUGE_VALL|

Błędy są zgłaszane w sposób określony w [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ umożliwia przeciążenie, można wywołać przeciążenia **lgamma,** które biorą i zwracają **float** i **długie** **podwójne** typy. W programie **C, lgamma** zawsze bierze i zwraca **podwójne**.

Jeśli x jest liczbą racjonalną, ta funkcja zwraca logarytm czynnika (x - 1).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**lgamma**, **lgammaf**, **lgammal**|\<> math.h|\<> cmath|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[tgamma, tgammaf, tgammal](tgamma-tgammaf-tgammal.md)<br/>
