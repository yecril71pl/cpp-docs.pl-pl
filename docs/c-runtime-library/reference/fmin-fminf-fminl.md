---
title: fmin, fminf, fminl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- fmin
- fminf
- fminl
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
- fmin
- fminf
- fminl
- math/fmin
- math/fminf
- math/fminl
helpviewer_keywords:
- fmin function
- fminf function
- fminl function
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3de46ba0a8d550d961fd05527b49a68a1518c50a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="fmin-fminf-fminl"></a>fmin, fminf, fminl

Określa mniejszy z dwiema określonymi wartościami.

## <a name="syntax"></a>Składnia

```C
double fmin(
   double x,
   double y
);

float fmin(
   float x,
   float y
); //C++ only

long double fmin(
   long double x,
   long double y
); //C++ only

float fminf(
   float x,
   float y
);

long double fminl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Pierwsza wartość do porównania.

*y*<br/>
Druga wartość do porównania.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca mniejszy z *x* lub *y*.

|Dane wejściowe|Wynik|
|-----------|------------|
|*x* jest wartością typu NaN|*y*|
|*y* jest wartością typu NaN|*x*|
|*x* i *y* są NaN|NaN|

Funkcja nie powoduje, że [_matherr —](matherr.md) do wywołania, powodują wyjątki zmiennoprzecinkowe lub zmień wartość **errno**.

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia **fmin** który przyjmować i zwracać **float** i **długi** **podwójne** typów. W programie C **fmin** zawsze przyjmuje i zwraca **podwójne**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Fmin**, **fminf —**, **fminl**|C: \<math.h ><br />C++: \<math.h > lub \<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
