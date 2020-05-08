---
title: tgamma, tgammaf, tgammal
ms.date: 4/2/2020
api_name:
- tgamma
- tgammaf
- tgammal
- _o_tgamma
- _o_tgammaf
- _o_tgammal
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
ms.openlocfilehash: 6f3eb1bd791e645407b09a99a8c8e96025ca47e3
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912230"
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

*y*<br/>
Wartość, dla której ma zostać znaleziony współczynnik gamma.

## <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, zwraca wartość gamma dla *x*.

Może wystąpić błąd zakresu, jeśli wielkość *x* jest za duża lub za mała dla typu danych. Jeśli *x* <= 0, może wystąpić błąd lub zakres domeny.

|Problem|Przesłać|
|-----------|------------|
|x = ± 0|± NIESKOŃCZONość|
|x = ujemna liczba całkowita|NaN|
|x = — NIESKOŃCZONość|NaN|
|x = + NIESKOŃCZONość|+ NIESKOŃCZONość|
|x = NaN|NaN|
|błąd domeny|NaN|
|błąd słupka|± HUGE_VAL, ± HUGE_VALF lub ± HUGE_VALL|
|błąd przepełnienia zakresu|± HUGE_VAL, ± HUGE_VALF lub ± HUGE_VALL|
|błąd zakresu niedopełnienia|poprawna wartość po zaokrągleniu.|

Błędy są raportowane zgodnie z opisem w [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **tgamma —** , które pobierają i zwracają **zmiennoprzecinkowe** i **długie** **podwójne** typy. W programie C **tgamma —** zawsze przyjmuje i zwraca wartość **Double**.

Jeśli x jest liczbą naturalną, ta funkcja Zwraca silnię (x-1).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek C++|
|--------------|--------------|------------------|
|**tgamma —**, **tgammaf —**, **tgammal**|\<> Math. h|\<cmath>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[lgamma, lgammaf, lgammal](lgamma-lgammaf-lgammal.md)<br/>
