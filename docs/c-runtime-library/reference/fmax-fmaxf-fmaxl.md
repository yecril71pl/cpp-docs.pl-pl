---
title: fmax, fmaxf, fmaxl
ms.date: 04/05/2018
apiname:
- fmax
- fmaxf
- fmaxl
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
ms.openlocfilehash: 371d53257427f2235048807968c82fec1b8bf699
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523705"
---
# <a name="fmax-fmaxf-fmaxl"></a>fmax, fmaxf, fmaxl

Określ większą z dwóch wartości liczbowych określony.

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
```

### <a name="parameters"></a>Parametry

*x*<br/>
Pierwsza wartość do porównania.

*y*<br/>
Druga wartość do porównania.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca większy z nich *x* lub *y*. Wartość zwracana jest dokładne i nie zależy od dowolnej formie zaokrąglania.

W przeciwnym razie może zwracać jedną z następujących wartości:

|Problem|Wróć|
|-----------|------------|
|*x* = NaN|*y*|
|*y* = NaN|*x*|
|*x* i *y* = NaN|NaN|

Ta funkcja nie używa błędy określone w [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na przeciążenie, można wywoływać przeciążenia fmax, które przyjmują i zwracają zmiennoprzecinkowych i typu long double. W programie C fmax zawsze przyjmuje i zwraca wartość o podwójnej precyzji.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**Fmax**, **fmaxf —**, **fmaxl**|\<math.h>|\<cmath > lub \<math.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fmin, fminf, fminl](fmin-fminf-fminl.md)<br/>
