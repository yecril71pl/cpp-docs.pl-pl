---
title: fma, fmaf, fmal
ms.date: 4/2/2020
api_name:
- fma
- fmaf
- fmal
- _o_fma
- _o_fmaf
- _o_fmal
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
- fma
- fmaf
- fmal
- math/fma
- math/fmaf
- math/fmal
helpviewer_keywords:
- fma function
- fmaf function
- fmal function
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
ms.openlocfilehash: d82565ed53f311ef1b2cf5942d207bf96090bd13
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217002"
---
# <a name="fma-fmaf-fmal"></a>fma, fmaf, fmal

Mnoży dwie wartości, dodaje trzecią wartość, a następnie zaokrągla wynik, bez utraty dokładności ze względu na zaokrąglenie pośrednie.

## <a name="syntax"></a>Składnia

```C
double fma(
   double x,
   double y,
   double z
);

float fma(
   float  x,
   float  y,
   float z
); //C++ only

long double fma(
   long double  x,
   long double  y,
   long double z
); //C++ only

float fmaf(
   float  x,
   float  y,
   float z
);

long double fmal(
   long double  x,
   long double  y,
   long double z
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Pierwsza wartość do pomnożenia.

*t*<br/>
Druga wartość do pomnożenia.

*porządku*<br/>
Wartość do dodania.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość `(x * y) + z`. Wartość zwracana jest następnie zaokrąglana przy użyciu bieżącego formatu zaokrąglania.

W przeciwnym razie może zwracać jedną z następujących wartości:

|Problem|Przesłać|
|-----------|------------|
|*x* = nieskończoność, *y* = 0 lub<br /><br /> *x* = 0, *y* = nieskończoność|NaN|
|*x* lub *y* = dokładnie ± nieskończoność *z =* nieskończoność ze znakiem odwrotnym|NaN|
|*x* lub *y* = NaN|NaN|
|nie (*x* = 0, *y*= nieograniczone) i *z* = NaN<br /><br /> nie (*x*= nieokreślony, *y*= 0) i *z* = NaN|NaN|
|Błąd przepełnienia zakresu|± HUGE_VAL, ± HUGE_VALF lub ± HUGE_VALL|
|Błąd zakresu niedopełnienia|poprawna wartość po zaokrągleniu.|

Błędy są raportowane zgodnie z opisem w [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **FMA** , które pobierają i zwracają **`float`** **`long double`** typy. W programie C **FMA** zawsze przyjmuje i zwraca **`double`** .

Ta funkcja oblicza wartość tak, jakby była pobrana z dokładnością do nieskończoności, a następnie zaokrągla wynik końcowy.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek C++|
|--------------|--------------|------------------|
|**FMA**, **fmaf —**, **Fmal**|\<math.h>|\<cmath>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
