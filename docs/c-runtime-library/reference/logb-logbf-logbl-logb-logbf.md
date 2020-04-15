---
title: logb, logbf, logbl, _logb, _logbf
ms.date: 4/2/2020
api_name:
- logb
- _logb
- _logbl
- logbf
- _logbf
- logbl
- _o__logb
- _o_logb
- _o_logbf
- _o_logbl
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
- logb
- logbl
- _logb
- _logbf
- logbf
helpviewer_keywords:
- _logbf function
- mantissas, floating-point variables
- logbf function
- _logb function
- exponent, floating-point numbers
- logbl function
- logb function
- floating-point functions
- floating-point functions, mantissa and exponent
- exponents and mantissas
ms.assetid: 780c4daa-6fe6-4fbc-9412-4c1ba1a1766f
ms.openlocfilehash: 1fe34a6661f768bbe22838eedb1914f7d21e31a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341683"
---
# <a name="logb-logbf-logbl-_logb-_logbf"></a>logb, logbf, logbl, _logb, _logbf

Wyodrębnia wykładnik wartości argumentu zmiennoprzecinkowego.

## <a name="syntax"></a>Składnia

```C
double logb(
   double x
);
float logb(
   float x
); // C++ only
long double logb(
   long double x
); // C++ only
float logbf(
   float x
);
long double logbl(
   long double x
);
double _logb(
   double x
);
float _logbf(
   float x
);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Wartość zmiennoprzecinna.

## <a name="return-value"></a>Wartość zwracana

**logb** zwraca bezstronną wykładniką wartość *x* jako podpisaną liczbę całkowitą reprezentowaną jako wartość zmiennoprzecinkową.

## <a name="remarks"></a>Uwagi

Funkcje **logb** wyodrębnić wartość wykładniczą argumentu zmiennoprzecinkowego *x*, tak jakby *x* były reprezentowane z nieskończonym zakresie. Jeśli argument *x* jest zdenormalizowane, jest traktowany tak, jakby zostały znormalizowane.

Ponieważ C++ umożliwia przeciążenie, można wywołać przeciążenia **logb,** które przyjmują i zwracają **float** lub **długie** **podwójne** wartości. W programie C **logb** zawsze przyjmuje i zwraca **podwójny**plik .

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|± QNAN, IND|Brak|_DOMAIN|
|± 0|ZERODYDYWAK|_SING|

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_logb**|\<> float.h|
|**logb**, **logbf**, **logbl**, **_logbf**|\<> math.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
