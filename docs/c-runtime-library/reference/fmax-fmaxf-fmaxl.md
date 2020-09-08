---
title: fmax, fmaxf, fmaxl
description: Dokumentacja interfejsu API dla Fmax —, fmaxf — i fmaxl; określające więcej dwóch wartości liczbowych.
ms.date: 9/1/2020
api_name:
- fmax
- fmaxf
- fmaxl
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
- fmax
- fmaxf
- fmaxl
- math/fmax
- math/fmaxf
- math/fmaxl
helpviewer_keywords:
- fmax function
- fmaxf function
- fmaxl function
ms.assetid: a773ccf7-495e-4a9a-8c6d-dfb53e341e35
ms.openlocfilehash: 4f38db64b30598e7cfb4eb4d0f57dccf257dabc5
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556687"
---
# <a name="fmax-fmaxf-fmaxl"></a>fmax, fmaxf, fmaxl

Określ większą liczbę dwóch określonych wartości liczbowych.

## <a name="syntax"></a>Składnia

```C
double fmax(
   double x,
   double y
);

float fmax(
   float x,
   float y
); //C++ only

long double fmax(
   long double x,
   long double y
); //C++ only

float fmaxf(
   float x,
   float y
);

long double fmaxl(
   long double x,
   long double y
);

#define fmax(X, Y) // Requires C11 or higher
```

### <a name="parameters"></a>Parametry

*y*\
Pierwsza wartość do porównania.

*t*\
Druga wartość do porównania.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca większą liczbę *x* lub *y*. Zwracana wartość jest dokładna i nie zależy od żadnej formy zaokrąglania.

W przeciwnym razie może zwracać jedną z następujących wartości:

|Problem|Przesłać|
|-----------|------------|
|*x* = NaN|*t*|
|*y* = NaN|*x*|
|*x* i *y* = NaN|NaN|

Ta funkcja nie używa błędów określonych w  [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia Fmax —, które pobierają i zwracają `float` `long double` typy. W programie C, o ile nie jest używane \<tgmath.h> makro do wywołania tej funkcji, `fmax` zawsze przyjmuje i zwraca podwójny.

Jeśli używasz \<tgmath.h> `fmax()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek C++|
|--------------|--------------|------------------|
|**Fmax —**, **fmaxf —**, **fmaxl**|\<math.h>|\<cmath> lub \<math.h>|
|**Fmax —** — makro | \<tgmath.h> ||

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fmin, fminf, fminl](fmin-fminf-fminl.md)<br/>
