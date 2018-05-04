---
title: fdim, fdimf, fdiml | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fdim
- fdimf
- fdiml
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
- fdim
- fdimf
- fdiml
- math/fdim
- math/fdimf
- math/fdiml
dev_langs:
- C++
helpviewer_keywords:
- fdim function
- fdimf function
- fdiml function
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cdcad02c94717715fdda1b3a9d2e820fc16d0bf4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="fdim-fdimf-fdiml"></a>fdim, fdimf, fdiml

Określa dodatnią różnica między wartościami pierwszego i drugiego.

## <a name="syntax"></a>Składnia

```C
double fdim(
   double x,
   double y
);

float fdim(
   float x,
   float y
); //C++ only

long double fdim(
   long double x,
   long double y
); //C++ only

float fdimf(
   float x,
   float y
);

long double fdiml(
   long double x,
   long double y
);

```

### <a name="parameters"></a>Parametry

*x*<br/>
Pierwsza wartość.

*y*<br/>
Druga wartość.

## <a name="return-value"></a>Wartość zwracana

Zwraca dodatnią różnicę między *x* i *y*:

|Wartość zwracana|Scenariusz|
|------------------|--------------|
|x i y|if x > y|
|0|Jeśli x < = y|

W przeciwnym razie może zwracać jedną z następujących błędów:

|Problem|Zwraca|
|-----------|------------|
|Błąd przepełnienia zakresu|+ Huge_val — + HUGE_VALF, lub + HUGE_VALL|
|Błąd zakresu niedopełnienie|poprawne wartości (zaokrągloną)|
|*x* lub *y* jest wartością typu NaN|NaN|

Błędy są zgłaszane jak określono w [_matherr —](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia **fdim —** który przyjmować i zwracać **float** i **długi** **podwójne** typów. W programie C **fdim —** zawsze przyjmuje i zwraca **podwójne**.

Z wyjątkiem obsługi NaN funkcja ta jest odpowiednikiem `fmax(x - y, 0)`.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
|--------------|--------------|------------------|
|**fdim —**, **fdimf —**, **fdiml**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
