---
title: lgamma, lgammaf, lgammal
description: Dokumentacja interfejsu API dla lgamma —, lgammaf — i lgammal; Określa logarytm naturalny wartości bezwzględnej funkcji gamma określonej wartości.
ms.date: 9/1/2020
api_name:
- lgamma
- lgammaf
- lgammal
- _o_lgamma
- _o_lgammaf
- _o_lgammal
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lgamma
- lgammaf
- lgammal
- math/lgamma
- math/lgammaf
- math/lgammal
helpviewer_keywords:
- lgamma function
- lgammal function
- lgammaf function
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
ms.openlocfilehash: 202250f3575f61fcef1cf29a687b8fdf36e6db33
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555400"
---
# <a name="lgamma-lgammaf-lgammal"></a>lgamma, lgammaf, lgammal

Określa logarytm naturalny wartości bezwzględnej funkcji gamma określonej wartości.

## <a name="syntax"></a>Składnia

```C
double lgamma( double x );
float lgammaf( float x );
long double lgammal( long double x );
#define lgammal(X) // Requires C11 or higher

float lgamma( float x ); //C++ only
long double lgamma( long double x ); //C++ only
```

### <a name="parameters"></a>Parametry

*y*\
Wartość do obliczenia.

## <a name="return-value"></a>Wartość zwracana

W przypadku pomyślnego zwrócenia logarytmu naturalnego wartości bezwzględnej funkcji gamma *x*.

|Problem|Przesłać|
|-----------|------------|
|*x* = NaN|NaN|
|*x* = ± 0|+ NIESKOŃCZONość|
|*x*= ujemna liczba całkowita|+ NIESKOŃCZONość|
|± NIESKOŃCZONość|+ NIESKOŃCZONość|
|błąd słupka|+ HUGE_VAL, + HUGE_VALF lub + HUGE_VALL|
|błąd przepełnienia zakresu|± HUGE_VAL, ± HUGE_VALF lub ± HUGE_VALL|

Błędy są raportowane zgodnie z opisem w [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **lgamma —** , które pobierają i zwracają **`float`** **`long double`** typy. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **lgamma —** zawsze przyjmuje i zwraca **`double`** .

Jeśli używasz \<tgmath.h> `lgamma()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

Jeśli x jest liczbą racjonalną, funkcja Zwraca logarytm o silności (x-1).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek C++|
|--------------|--------------|------------------|
|**lgamma —**, **lgammaf —**, **lgammal**|\<math.h>|\<cmath>|
|**lgamma —** — makro | \<tgmath.h> ||

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[tgamma, tgammaf, tgammal](tgamma-tgammaf-tgammal.md)<br/>
