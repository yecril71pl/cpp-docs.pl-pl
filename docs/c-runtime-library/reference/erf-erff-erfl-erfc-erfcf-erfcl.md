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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 633a766684ed7485ab579157ae4c94fe209f7e73
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915012"
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

*y*<br/>
Wartość zmiennoprzecinkowa.

## <a name="return-value"></a>Wartość zwracana

Funkcje **ERF** zwracają funkcję błędu Gaussa *x*. Funkcje **ERFC —** zwracają komplementarną funkcję błędu Gaussa *x*.

## <a name="remarks"></a>Uwagi

Funkcje **ERF** obliczają funkcję błędu Gaussa *x*, która jest definiowana jako:

![Funkcja błędu x](media/crt_erf_formula.PNG "Funkcja błędu x")

Funkcja błędu uzupełniającego Gaussa jest definiowana jako 1-ERF (x). Funkcje **ERF** zwracają wartość z zakresu od-1,0 do 1,0. Brak powrotu błędu. Funkcje **ERFC —** zwracają wartość z zakresu od 0 do 2. Jeśli *x* jest zbyt duży dla **ERFC —**, zmienna **errno** jest ustawiona na **ERANGE**.

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia wartości **ERF** i **ERFC —** , które pobierają i zwracają **zmiennoprzecinkowe** i **długie** **podwójne** typy. W programie C, funkcja **ERF** i **ERFC —** zawsze przyjmują i zwracają wartość **podwójną**.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**ERF**, **erff —**, **erfl**, **ERFC —**, **erfcf —**, **erfcl**|\<> Math. h|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
