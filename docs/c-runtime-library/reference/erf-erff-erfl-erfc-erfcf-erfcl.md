---
title: erf, erff, erfl, erfc, erfcf, erfcl
ms.date: 01/31/2019
api_name:
- erff
- erfl
- erf
- erfc
- erfcf
- erfcl
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
ms.openlocfilehash: df724ed056c02d79b5b51f97ae4aaf8ae267fde5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937617"
---
# <a name="erf-erff-erfl-erfc-erfcf-erfcl"></a>erf, erff, erfl, erfc, erfcf, erfcl

Oblicza funkcję Error lub uzupełniającą funkcję błędu wartości.

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

Funkcje **ERF** zwracają funkcję błędu Gaussa *x*. Funkcje **ERFC —** zwracają komplementarną funkcję błędu Gaussa *x*.

## <a name="remarks"></a>Uwagi

Funkcje **ERF** obliczają funkcję błędu Gaussa *x*, która jest definiowana jako:

![Funkcja błędu x](media/crt_erf_formula.PNG "Funkcja błędu x")

Funkcja błędu uzupełniającego Gaussa jest definiowana jako 1-ERF (x). Funkcje **ERF** zwracają wartość z zakresu od-1,0 do 1,0. Brak powrotu błędu. Funkcje **ERFC —** zwracają wartość z zakresu od 0 do 2. Jeśli *x* jest zbyt duży dla **ERFC —** , zmienna **errno** jest ustawiona na **ERANGE**.

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia wartości **ERF** i **ERFC —** , które pobierają i zwracają **zmiennoprzecinkowe** i **długie** **podwójne** typy. W programie C, funkcja **ERF** i **ERFC —** zawsze przyjmują i zwracają wartość **podwójną**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**ERF**, **erff —** , **erfl**, **ERFC —** , **erfcf —** , **erfcl**|\<math.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
