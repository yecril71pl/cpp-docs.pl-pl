---
title: erf, erff, erfl, erfc, erfcf, erfcl
ms.date: 11/19/2018
apiname:
- erff
- erfl
- erf
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
- erfl
- erf
- erff
helpviewer_keywords:
- erfl function
- erff function
- erf function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
ms.openlocfilehash: 5c64a7ac6c3a4d79c221ff1ca5f9460e9e6bdea6
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176828"
---
# <a name="erf-erff-erfl-erfc-erfcf-erfcl"></a>erf, erff, erfl, erfc, erfcf, erfcl

Oblicza funkcję błędu lub komplementarną funkcję błędu wartości.

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

*x*<br/>
Wartość zmiennoprzecinkowa.

## <a name="return-value"></a>Wartość zwracana

**Erf** funkcje zwracają Gaussa funkcję błędu *x*. **Erfc** funkcje zwracają Gaussa uzupełniającą funkcję błędu *x*.

## <a name="remarks"></a>Uwagi

**Erf** funkcje obliczają wartość funkcji błędu Gaussa z *x*, która została zdefiniowana jako:

![Funkcję błędu x](media/crt_erf_formula.PNG "funkcję błędu x")

Uzupełniająca funkcja błędu Gaussa jest zdefiniowana jako 1 – erf(x). **Erf** funkcje zwracają wartość z zakresu od – 1,0 do 1,0. Nie będzie zwrotu błędu. **Erfc** funkcje zwracają wartość z zakresu od 0 do 2. Jeśli *x* jest zbyt duży dla **erfc**, **errno** zmienna jest ustawiona na **ERANGE**.

Ponieważ C++ pozwala na przeciążenie, można wywoływać przeciążenia **erf** i **erfc** przyjmujące i zwracające **float** i **długie** **double** typów. W programie C **erf** i **erfc** zawsze przyjmują i zwracają **double**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**ERF**, **erff —**, **erfl —**, **erfc**, **erfcf —**, **erfcl**|\<math.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
