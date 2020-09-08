---
title: fdim, fdimf, fdiml
description: Dokumentacja interfejsu API dla fdim —, fdimf — i fdiml; który określa dodatnią różnicę między dwiema wartościami.
ms.date: 9/1/2020
api_name:
- fdim
- fdimf
- fdiml
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
ms.openlocfilehash: 406fc5cfe543aa0865760df9ff780c62e78510fc
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554789"
---
# <a name="fdim-fdimf-fdiml"></a>fdim, fdimf, fdiml

Określa dodatnią różnicę między pierwszą i drugą wartością.

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

#define fdim(X) // Requires C11 or higher
```

### <a name="parameters"></a>Parametry

*y*\
Pierwsza wartość.

*t*\
Druga wartość.

## <a name="return-value"></a>Wartość zwracana

Zwraca dodatnią różnicę z zakresu od *x* do *y*:

|Wartość zwracana|Scenariusz|
|------------------|--------------|
|x-y|Jeśli x > y|
|0|Jeśli x <= y|

W przeciwnym razie może zwrócić jeden z następujących błędów:

|Problem|Przesłać|
|-----------|------------|
|Błąd przepełnienia zakresu|+ HUGE_VAL, + HUGE_VALF lub + HUGE_VALL|
|Błąd zakresu niedopełnienia|poprawna wartość (po zaokrągleniu)|
|*x* lub *y* jest NaN|NaN|

Błędy są raportowane zgodnie z opisem w [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **fdim —** , które pobierają i zwracają **`float`** **`long double`** typy. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **fdim —** zawsze przyjmuje i zwraca **`double`** .

Jeśli używasz \<tgmath.h> `fdim()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

Z wyjątkiem obsługi NaN, ta funkcja jest równoważna z `fmax(x - y, 0)` .

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek C++|
|--------------|--------------|------------------|
|**fdim —**, **fdimf —**, **fdiml**|\<math.h>|\<cmath>|
|**fdim —** — makro | \<tgmath.h> ||

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
