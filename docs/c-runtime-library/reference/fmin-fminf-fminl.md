---
title: fmin, fminf, fminl
ms.date: 04/05/2018
api_name:
- fmin
- fminf
- fminl
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: d6cd16c298c3f4bedb8064d66efd2d4bbe20c22b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216989"
---
# <a name="fmin-fminf-fminl"></a>fmin, fminf, fminl

Określa mniejszą liczbę dwóch określonych wartości.

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

*t*<br/>
Druga wartość do porównania.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca mniejszą liczbę *x* lub *y*.

|Dane wejściowe|Wynik|
|-----------|------------|
|*x* jest NaN|*t*|
|*y* jest NaN|*x*|
|*x* i *y* są NaN|NaN|

Funkcja nie powoduje wywołania [_matherr](matherr.md) , spowodować żadnych wyjątków zmiennoprzecinkowych lub zmienić wartość **errno**.

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **fmin —** , które pobierają i zwracają **`float`** **`long double`** typy. W programie C **fmin —** zawsze przyjmuje i zwraca **`double`** .

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**fmin —**, **fminf —**, **fminl**|S\<math.h><br />C++: \<math.h> lub\<cmath>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
