---
title: logb, logbf, logbl, _logb, _logbf
ms.date: 04/05/2018
apiname:
- logb
- _logb
- _logbl
- logbf
- logbl
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
ms.openlocfilehash: 9f598eedaf30b1f2a1858129e648a117355d112e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285716"
---
# <a name="logb-logbf-logbl-logb-logbf"></a>logb, logbf, logbl, _logb, _logbf

Wyodrębnia wartość wykładnika argumentu zmiennoprzecinkowego.

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

*x*<br/>
Wartość zmiennoprzecinkowa.

## <a name="return-value"></a>Wartość zwracana

**logb —** zwraca bezstronną wartość wykładnika *x* jako liczba całkowita ze znakiem reprezentowane jako wartość zmiennoprzecinkowa.

## <a name="remarks"></a>Uwagi

**Logb —** funkcje wyodrębniają wartość zmiennoprzecinkową argumentu *x*, tak jakby *x* były reprezentowane z nieskończoną. Jeśli argument *x* jest zdenormalizowany, jest ona traktowana tak, jakby jakby był znormalizowany.

Ponieważ C++ pozwala na przeciążenie, można wywoływać przeciążenia **logb —** przyjmujące i zwracające **float** lub **długie** **double** wartości. W programie C **logb —** zawsze przyjmuje i zwraca **double**.

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|GRANICACH QNAN, ZNAJDŹ|Brak|_DOMAIN|
|± 0|ZERODIVIDE|_SING|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_logb —**|\<float.h>|
|**logb —**, **logbf —**, **logbl —**, **_logbf —**|\<math.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
