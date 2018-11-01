---
title: fmin, fminf, fminl
ms.date: 04/05/2018
apiname:
- fmin
- fminf
- fminl
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
- fmin
- fminf
- fminl
- math/fmin
- math/fminf
- math/fminl
helpviewer_keywords:
- fmin function
- fminf function
- fminl function
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
ms.openlocfilehash: f73853e18bd5d7f699cd2c3109fe5fb830859bf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464366"
---
# <a name="fmin-fminf-fminl"></a>fmin, fminf, fminl

Określa mniejszą z dwóch określonych wartości.

## <a name="syntax"></a>Składnia

```C
double fmin(
   double x,
   double y
);

float fmin(
   float x,
   float y
); //C++ only

long double fmin(
   long double x,
   long double y
); //C++ only

float fminf(
   float x,
   float y
);

long double fminl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Pierwsza wartość do porównania.

*y*<br/>
Druga wartość do porównania.

## <a name="return-value"></a>Wartość zwracana

Jeśli operacja się powiedzie, zwraca mniejszy z *x* lub *y*.

|Dane wejściowe|Wynik|
|-----------|------------|
|*x* jest wartością typu NaN|*y*|
|*y* jest wartością typu NaN|*x*|
|*x* i *y* są NaN|NaN|

Funkcja nie powoduje, że [_matherr](matherr.md) do wywołania, powodują wyjątki zmiennoprzecinkowe lub zmień wartość właściwości **errno**.

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na przeciążenie, można wywoływać przeciążenia **fmin** przyjmujące i zwracające **float** i **długie** **double** typów. W programie C **fmin** zawsze przyjmuje i zwraca **double**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Fmin —**, **fminf —**, **fminl**|C: \<math.h ><br />C++: \<math.h > lub \<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
