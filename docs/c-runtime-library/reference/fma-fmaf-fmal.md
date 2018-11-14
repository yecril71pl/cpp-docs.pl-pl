---
title: fma, fmaf, fmal
ms.date: 04/05/2018
apiname:
- fma
- fmaf
- fmal
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
ms.openlocfilehash: f96592e245e443bae2f3334da51cae5572753708
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51517803"
---
# <a name="fma-fmaf-fmal"></a>fma, fmaf, fmal

Mnoży dwie wartości ze sobą, dodaje trzecia wartość, a następnie zaokrągla wyniku bez utraty żadnych dokładności spowodowane zaokrąglanie pośrednie.

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

*y*<br/>
Druga wartość do pomnożenia.

*z*<br/>
Wartość do dodania.

## <a name="return-value"></a>Wartość zwracana

Zwraca `(x * y) + z`. Wartość zwracana to jest zaokrąglana przy użyciu bieżącego formatu zaokrąglania.

W przeciwnym razie może zwracać jedną z następujących wartości:

|Problem|Wróć|
|-----------|------------|
|*x* = NIESKOŃCZONOŚĆ, *y* = 0 lub<br /><br /> *x* = 0, *y* = NIESKOŃCZONOŚĆ|NaN|
|*x* lub *y* dokładnie mniej więcej w NIESKOŃCZONOŚĆ, *z* = NIESKOŃCZONOŚCI znakiem odwrotną|NaN|
|*x* lub *y* = NaN|NaN|
|nie (*x* = 0, *y*= nieokreślony) i *z* = NaN<br /><br /> nie (*x*= nieokreślony, *y*= 0) i *z* = NaN|NaN|
|Błąd w zakresie przepełnienia|±HUGE_VAL, ±HUGE_VALF lub ±HUGE_VALL|
|Błąd zakresu niedopełnienie|poprawnej wartości, po zaokrągleniu zgodnym.|

Błędy są zgłaszane określonej [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na przeciążenie, można wywoływać przeciążenia **fma** przyjmujące i zwracające **float** i **długie** **double** typów. W programie C **fma** zawsze przyjmuje i zwraca **double**.

Ta funkcja oblicza wartość tak, jakby zostały pobrane z dokładnością do nieskończoności, a następnie zaokrągla wynik końcowy.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**FMA**, **fmaf —**, **fmal**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
