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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 993ca4d57202b3789929161a964b3e41d48fd98f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346566"
---
# <a name="fma-fmaf-fmal"></a>fma, fmaf, fmal

Mnoży dwie wartości razem, dodaje trzecią wartość, a następnie zaokrągla wynik, nie tracąc żadnej precyzji z powodu pośredniego zaokrąglania.

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

*X*<br/>
Pierwsza wartość do pomnożenia.

*Y*<br/>
Druga wartość do pomnożenia.

*Z*<br/>
Wartość do dodania.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość `(x * y) + z`. Zwracana wartość jest następnie zaokrąglana przy użyciu bieżącego formatu zaokrąglania.

W przeciwnym razie może zwrócić jedną z następujących wartości:

|Problem|Zwraca|
|-----------|------------|
|*x* = NIESKOŃCZONOŚĆ, *y* = 0 lub<br /><br /> *x* = 0, *y* = NIESKOŃCZONOŚĆ|NaN|
|*x* lub *y* = dokładne ± NIESKOŃCZONOŚĆ, *z* = NIESKOŃCZONOŚĆ z przeciwległym znakiem|NaN|
|*x* lub *y* = NaN|NaN|
|nie (*x* = 0, *y*= nieokreślony) i *z* = NaN<br /><br /> nie (*x*=nieokreślony, *y*=0) i *z* = NaN|NaN|
|Błąd zakresu przepełnienia|±HUGE_VAL, ±HUGE_VALF lub ±HUGE_VALL|
|Błąd zakresu niedopełnienia|prawidłową wartość, po zaokrągleniu.|

Błędy są zgłaszane w sposób określony w [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ umożliwia przeciążenie, można wywołać przeciążenia **fma,** które biorą i zwracają **float** i **długie** **podwójne** typy. W programie C **fma** zawsze bierze i zwraca **podwójne**.

Ta funkcja oblicza wartość tak, jakby została podjęta do nieskończonej precyzji, a następnie zaokrągla wynik końcowy.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**fma**, **fmaf**, **fmal**|\<> math.h|\<> cmath|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
