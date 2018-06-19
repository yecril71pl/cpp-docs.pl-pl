---
title: FMA fmaf —, fmal | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- fma function
- fmaf function
- fmal function
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b28009a9c3cc4edceb9032660a0c2a71916dfb2f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401480"
---
# <a name="fma-fmaf-fmal"></a>fma, fmaf, fmal

Mnoży dwie wartości ze sobą, dodaje trzecia wartość, a następnie zaokrągla wyniku bez utraty żadnych precyzji z powodu pośredniczące zaokrąglania.

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
Pierwsza wartość wielokrotnie.

*y*<br/>
Druga wartość używana w wielokrotnie.

*z*<br/>
Wartość do dodania.

## <a name="return-value"></a>Wartość zwracana

Zwraca `(x * y) + z`. Wartość zwracana jest następnie zaokrąglana przy użyciu bieżącego formatu zaokrąglania.

W przeciwnym razie może zwracać jedną z następujących wartości:

|Problem|Zwraca|
|-----------|------------|
|*x* = NIESKOŃCZONOŚCI, *y* = 0 lub<br /><br /> *x* = 0, *y* = INFINITY|NaN|
|*x* lub *y* mniej dokładne więcej NIESKOŃCZONOŚCI, *z* = NIESKOŃCZONOŚCI symbol przeciwnego|NaN|
|*x* lub *y* = NaN|NaN|
|nie (*x* = 0, *y*= nieograniczonego) i *z* = NaN<br /><br /> nie (*x*= nieokreślony, *y*= 0) i *z* = NaN|NaN|
|Błąd przepełnienia zakresu|±HUGE_VAL, ±HUGE_VALF lub ±HUGE_VALL|
|Błąd zakresu niedopełnienie|prawidłowa wartość zaokrągloną.|

Błędy są zgłaszane jak określono w [_matherr —](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia **fma** który przyjmować i zwracać **float** i **długi** **podwójne** typów. W programie C **fma** zawsze przyjmuje i zwraca **podwójne**.

Ta funkcja oblicza wartość tak, jakby zostały podjęte dokładnością nieskończone, a następnie zaokrągla wynik końcowy.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
|--------------|--------------|------------------|
|**FMA**, **fmaf —**, **fmal**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
