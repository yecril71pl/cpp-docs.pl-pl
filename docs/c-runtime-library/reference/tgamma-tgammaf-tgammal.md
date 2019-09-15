---
title: tgamma, tgammaf, tgammal
ms.date: 04/05/2018
api_name:
- tgamma
- tgammaf
- tgammal
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
- tgamma
- tgammaf
- tgammal
- math/tgamma
- math/tgammaf
- math/tgammal
helpviewer_keywords:
- tgamma function
- tgammaf function
- tgammal function
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
ms.openlocfilehash: 02926fa49bbabeb9cf532f53cfa6e30a77805e70
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946209"
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma, tgammaf, tgammal

Określa funkcję gamma określonej wartości.

## <a name="syntax"></a>Składnia

```C
double tgamma(
   double x
);

float tgamma(
   float x
); //C++ only

long double tgamma(
   long double x
); //C++ only

float tgammaf(
   float x
);

long double tgammal(
   long double x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość, dla której ma zostać znaleziony współczynnik gamma.

## <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, zwraca wartość gamma dla *x*.

Może wystąpić błąd zakresu, jeśli wielkość *x* jest za duża lub za mała dla typu danych. Jeśli *x* < = 0, może wystąpić błąd lub zakres domeny.

|Problem|przesłać|
|-----------|------------|
|x = ±0|± NIESKOŃCZONOŚĆ|
|x = ujemna liczba całkowita|NaN|
|x = — NIESKOŃCZONość|NaN|
|x = + NIESKOŃCZONość|\+ NIESKOŃCZONOŚĆ|
|x = NaN|NaN|
|błąd domeny|NaN|
|błąd słupka|HUGE_VAL, HUGE_VALF lub HUGE_VALL|
|Błąd przepełnienia zakresu|HUGE_VAL, HUGE_VALF lub HUGE_VALL|
|Błąd zakresu niedopełnienia|poprawna wartość po zaokrągleniu.|

Błędy są raportowane zgodnie z opisem w [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **tgamma —** , które pobierają i zwracają **zmiennoprzecinkowe** i **długie** **podwójne** typy. W programie C **tgamma —** zawsze przyjmuje i zwraca wartość **Double**.

Jeśli x jest liczbą naturalną, ta funkcja Zwraca silnię (x-1).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|C++nagłówki|
|--------------|--------------|------------------|
|**tgamma —** , **tgammaf —** , **tgammal**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
