---
title: fma, fmaf, fmal
description: Dokumentacja interfejsu API dla FMA, fmaf — i Fmal; który Mnoży dwie wartości, dodaje trzecią wartość, a następnie zaokrągla wynik, bez utraty dokładności ze względu na zaokrąglenie pośrednie.
ms.date: 9/1/2020
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
ms.openlocfilehash: e9ae92c28f24b6281d73450c7cabaad775a84d42
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556700"
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

#define fma(X, Y, Z) // Requires C11 or higher
```

### <a name="parameters"></a>Parametry

*y*\
Pierwsza wartość do pomnożenia.

*t*\
Druga wartość do pomnożenia.

*porządku*\
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

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **FMA** , które pobierają i zwracają **`float`** **`long double`** typy. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **FMA** zawsze przyjmuje i zwraca **`double`** .

Jeśli używasz \<tgmath.h> `fma()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

Ta funkcja oblicza wartość tak, jakby była pobrana z dokładnością do nieskończoności, a następnie zaokrągla wynik końcowy.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek C++|
|--------------|--------------|------------------|
|**FMA**, **fmaf —**, **Fmal**|\<math.h>|\<cmath>|
|**FMA** — makro | \<tgmath.h> ||

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
