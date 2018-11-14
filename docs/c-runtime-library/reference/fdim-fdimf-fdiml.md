---
title: fdim, fdimf, fdiml
ms.date: 04/05/2018
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
helpviewer_keywords:
- fdim function
- fdimf function
- fdiml function
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
ms.openlocfilehash: 263635a32b21b01faa84405ab97bd5518f054ba5
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518180"
---
# <a name="fdim-fdimf-fdiml"></a>fdim, fdimf, fdiml

Określa dodatnią różnicę między wartościami pierwszego i drugiego.

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

Określa dodatnią różnicę między *x* i *y*:

|Wartość zwracana|Scenariusz|
|------------------|--------------|
|x i y|if x > y|
|0|Jeśli x < = t|

W przeciwnym razie może zwracać jedną z następujących błędów:

|Problem|Wróć|
|-----------|------------|
|Błąd w zakresie przepełnienia|+ HUGE_VAL + HUGE_VALF, lub + HUGE_VALL|
|Błąd zakresu niedopełnienie|Prawidłowe wartości (zaokrągloną)|
|*x* lub *y* jest wartością typu NaN|NaN|

Błędy są zgłaszane określonej [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na przeciążenie, można wywoływać przeciążenia **fdim —** przyjmujące i zwracające **float** i **długie** **double** typów. W programie C **fdim —** zawsze przyjmuje i zwraca **double**.

Z wyjątkiem obsługi NaN, ta funkcja jest odpowiednikiem `fmax(x - y, 0)`.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**fdim —**, **fdimf —**, **fdiml**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
