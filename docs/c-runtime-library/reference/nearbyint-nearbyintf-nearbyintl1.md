---
title: nearbyint, nearbyintf, nearbyintl
ms.date: 4/2/2020
api_name:
- nearbyint
- nearbyintf
- nearbyintl
- _o_nearbyint
- _o_nearbyintf
- _o_nearbyintl
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
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
ms.openlocfilehash: 92e3a744ef8069d45733c06b7a2681905c3eab55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338589"
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint, nearbyintf, nearbyintl

Zaokrągla określoną wartość zmiennoprzecinkową do liczby całkowitej i zwraca tę wartość w formacie zmiennoprzecinkowym.

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

*X*<br/>
Wartość do zaokrąglenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwraca *x*, zaokrąglone do najbliższej liczby całkowitej, przy użyciu bieżącego formatu zaokrąglania, jak zgłaszane przez [fegetround](fegetround-fesetround2.md). W przeciwnym razie funkcja może zwrócić jedną z następujących wartości:

|Problem|Zwraca|
|-----------|------------|
|*x* = ±INFINITY|±NIESKOŃCZONOŚĆ, niezmodyfikowana|
|*x* = ±0|±0, niezmodyfikowane|
|*x* = NaN|NaN|

Błędy nie są zgłaszane za pośrednictwem [_matherr;](matherr.md) w szczególności ta funkcja nie zgłasza żadnych **wyjątków FE_INEXACT.**

## <a name="remarks"></a>Uwagi

Podstawową różnicą między tą funkcją a [rint](rint-rintf-rintl.md) jest to, że ta funkcja nie powoduje podniesienia niedokładnego wyjątku zmiennoprzecinkowego.

Ponieważ maksymalne wartości zmiennoprzecinkowy są dokładne liczby całkowite, ta funkcja nigdy nie przepełnienie przez siebie; dane wyjściowe mogą przepełniać wartość zwracaną, w zależności od używanej wersji funkcji.

C++ umożliwia przeciążenie, dzięki czemu można wywołać przeciążenia **nearbyint,** które przyjmują i zwracają **float** lub **długie** **podwójne** parametry. W programie C **nearbyint** zawsze przyjmuje dwie podwójne wartości i zwraca podwójną wartość.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**nearbyint**, **nearbyintf**, **nearbyintl**|\<> math.h|\<cmath> lub \<math.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[Wsparcie matematyczne i zmiennoprzecinkowy](../floating-point-support.md)<br/>
