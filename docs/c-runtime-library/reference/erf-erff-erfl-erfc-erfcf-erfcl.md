---
title: erf, erff, erfl, erfc, erfcf, erfcl
ms.date: 4/2/2020
api_name:
- erff
- erfl
- erf
- erfc
- erfcf
- erfcl
- _o_erf
- _o_erfc
- _o_erfcf
- _o_erfcl
- _o_erff
- _o_erfl
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
- erfl
- erf
- erff
- erfc
- erfcf
- erfcl
helpviewer_keywords:
- erfl function
- erff function
- erf function
- erfcl function
- erfcf function
- erfc function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
ms.openlocfilehash: ad7ad279d3686e4f33a6f5f901c60348c131b89a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347923"
---
# <a name="erf-erff-erfl-erfc-erfcf-erfcl"></a>erf, erff, erfl, erfc, erfcf, erfcl

Oblicza funkcję błędu lub funkcję błędu uzupełniającego wartości.

## <a name="syntax"></a>Składnia

```C
double erf(
   double x
);
float erf(
   float x
); // C++ only
long double erf(
   long double x
); // C++ only
float erff(
   float x
);
long double erfl(
   long double x
);
double erfc(
   double x
);
float erfc(
   float x
); // C++ only
long double erfc(
   long double x
); // C++ only
float erfcf(
   float x
);
long double erfcl(
   long double x
);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Wartość zmiennoprzecinna.

## <a name="return-value"></a>Wartość zwracana

Funkcje **erf** zwracają funkcję błędu *Gaussa x*. Funkcje **erfc** zwracają uzupełniającą funkcję błędu Gaussa *x*.

## <a name="remarks"></a>Uwagi

Funkcje **erf** obliczają funkcję błędu Gaussa *x*, która jest zdefiniowana jako:

![Funkcja błędu x](media/crt_erf_formula.PNG "Funkcja błędu x")

Uzupełniająca funkcja błędu Gaussa jest zdefiniowana jako 1 - erf(x). Funkcje **erf** zwracają wartość w zakresie od -1,0 do 1,0. Nie ma zwracania błędów. Funkcje **erfc** zwracają wartość w zakresie od 0 do 2. Jeśli *x* jest zbyt duży dla **erfc**, **zmienna errno** jest ustawiona na **ERANGE**.

Ponieważ C++ umożliwia przeciążenie, można wywołać przeciążenia **erf** i **erfc,** które biorą i zwracają **float** i **długie** **typy podwójne.** W programie C, **erf** i **erfc** zawsze wziąć i zwrócić **podwójne**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**erf**, **erff**, **erfl**, **erfc**, **erfcf**, **erfcl**|\<> math.h|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
