---
title: lgamma —, lgammaf —, lgammal | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- lgamma
- lgammaf
- lgammal
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
- lgamma
- lgammaf
- lgammal
- math/lgamma
- math/lgammaf
- math/lgammal
dev_langs:
- C++
helpviewer_keywords:
- lgamma function
- lgammal function
- lgammaf function
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4fb668e1c24d3f24331e0892002530192afdaeb6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400255"
---
# <a name="lgamma-lgammaf-lgammal"></a>lgamma, lgammaf, lgammal

Określa wartość bezwzględną liczby funkcji gamma określonej wartości logarytmu naturalnego.

## <a name="syntax"></a>Składnia

```C
double lgamma( double x );
float lgammaf( float x );
long double lgammal( long double x );
```

```cpp
float lgamma( float x ); //C++ only
long double lgamma( long double x ); //C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość do obliczenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca logarytm naturalny wartości bezwzględne funkcji gamma *x*.

|Problem|Zwraca|
|-----------|------------|
|*x* = NaN|NaN|
|*x* = ±0|+ INFINITY|
|*x*= ujemnej liczby całkowitej|+ INFINITY|
|±INFINITY|+ INFINITY|
|Błąd Bieguna|+ Huge_val — + HUGE_VALF, lub + HUGE_VALL|
|Błąd przepełnienia zakresu|±HUGE_VAL, ±HUGE_VALF lub ±HUGE_VALL|

Błędy są zgłaszane jak określono w [_matherr —](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia **lgamma —** który przyjmować i zwracać **float** i **długi** **podwójne** typów. W programie C **lgamma —** zawsze przyjmuje i zwraca **podwójne**.

Jeśli x to liczba wymierna, funkcja zwraca logarytm silni (x - 1).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
|--------------|--------------|------------------|
|**lgamma —**, **lgammaf —**, **lgammal**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[tgamma, tgammaf, tgammal](tgamma-tgammaf-tgammal.md)<br/>
