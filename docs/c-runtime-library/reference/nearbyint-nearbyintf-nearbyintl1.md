---
title: nearbyint —, nearbyintf —, nearbyintl | Dokumentacja firmy Microsoft
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
- nearbyint
- nearbyintf
- nerabyintl
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
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
dev_langs:
- C++
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0aacdeb67e7c467bf6f8719172dfd9771e0cec8d
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint, nearbyintf, nearbyintl

Zaokrągla określona wartość zmiennoprzecinkowa na liczbę całkowitą i zwraca tę wartość w formacie liczb zmiennoprzecinkowych.

## <a name="syntax"></a>Składnia

```C
double nearbyint( double x );
float nearbyintf( float x );
long double nearbyintl( long double x );
```

```cpp
float nearbyint( float x ); //C++ only
long double nearbyint( long double x ); //C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
wartość do zaokrąglenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca *x*, zaokrąglona do najbliższej liczby całkowitej, przy użyciu bieżącego formatu zaokrąglania zgłoszonych przez [fegetround](fegetround-fesetround2.md). W przeciwnym razie funkcja może zwracać jedną z następujących wartości:

|Problem|Zwraca|
|-----------|------------|
|*x* = ±INFINITY|±INFINITY nie mają być modyfikowane|
|*x* = ±0|±0, nie mają być modyfikowane|
|*x* = NaN|NaN|

Błędy nie są zgłaszane przez [_matherr —](matherr.md); ściślej mówiąc, ta funkcja nie raportuje żadnego **FE_INEXACT** wyjątków.

## <a name="remarks"></a>Uwagi

Główną różnicą między tej funkcji i [drukowanie](rint-rintf-rintl.md) jest ta funkcja nie zgłaszał niedokładnymi zmiennoprzecinkowych wyjątków punktu.

Ponieważ maksymalne wartości zmiennoprzecinkowe są dokładne liczb całkowitych, ta funkcja nigdy nie będzie przepełnienie siebie. dane wyjściowe mogą zamiast przepełnienie zwracanej wartości, w zależności od instalowanej wersji funkcji używasz.

C++ pozwala przeładowanie, dlatego można wywoływać przeciążenia **nearbyint —** który przyjmować i zwracać **float** lub **długi** **podwójne** parametrów. W programie C **nearbyint —** zawsze ma dwie wartości double i zwraca wartość typu double.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
|--------------|--------------|------------------|
|**nearbyint —**, **nearbyintf —**, **nearbyintl**|\<math.h>|\<cmath > lub \<math.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[Matematyczne i Obsługa liczb zmiennoprzecinkowych](../floating-point-support.md)<br/>
