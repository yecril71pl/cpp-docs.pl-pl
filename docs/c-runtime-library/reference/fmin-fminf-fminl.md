---
title: fmin, fminf, fminl
description: Dokumentacja interfejsu API dla fmin —, fminf — i fminl; który określa mniejszą liczbę dwóch wartości.
ms.date: 9/1/2020
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
ms.openlocfilehash: 6a070835d809c6adcb5b7bfd57b5373886b348ca
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556713"
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

#define fmin(x) // Requires C11 or higher
```

### <a name="parameters"></a>Parametry

*y*\
Pierwsza wartość do porównania.

*t*\
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

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **fmin —** , które pobierają i zwracają **`float`** **`long double`** typy. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **fmin —** zawsze przyjmuje i zwraca **`double`** .

Jeśli używasz \<tgmath.h> `fmin()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**fmin —**, **fminf —**, **fminl**|S \<math.h><br />C++: \<math.h> lub \<cmath>|
|**fmin —** — makro | \<tgmath.h> ||

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
