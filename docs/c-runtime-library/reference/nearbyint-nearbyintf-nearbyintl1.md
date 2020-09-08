---
title: nearbyint, nearbyintf, nearbyintl
description: Dokumentacja interfejsu API dla nearbyint —, nearbyintf — i nearbyintl; który zaokrągla określoną wartość zmiennoprzecinkową do liczby całkowitej i zwraca tę wartość w formacie zmiennoprzecinkowym.
ms.date: 9/1/2020
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 9717559518032c6f1f2126c7ded7cb90603bce64
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556388"
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint, nearbyintf, nearbyintl

Zaokrągla określoną wartość zmiennoprzecinkową do liczby całkowitej i zwraca tę wartość w formacie zmiennoprzecinkowym.

## <a name="syntax"></a>Składnia

```C
double nearbyint( double x );
float nearbyintf( float x );
long double nearbyintl( long double x );
#define nearbyint( X ) // Requires C11 or higher

float nearbyint( float x ); //C++ only
long double nearbyint( long double x ); //C++ only
```

### <a name="parameters"></a>Parametry

*y*\
Wartość do zaokrąglenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca wartość *x*, zaokrągloną do najbliższej liczby całkowitej, przy użyciu bieżącego formatu zaokrąglania, który jest raportowany przez [fegetround](fegetround-fesetround2.md). W przeciwnym razie funkcja może zwracać jedną z następujących wartości:

|Problem|Przesłać|
|-----------|------------|
|*x* = ± nieskończoność|NIESKOŃCZONość, niezmodyfikowana|
|*x* = ± 0|0, niemodyfikowane|
|*x* = NaN|NaN|

Błędy nie są zgłaszane przez [_matherr](matherr.md); Ta funkcja nie zgłasza żadnych wyjątków **FE_INEXACT** .

## <a name="remarks"></a>Uwagi

Podstawowa różnica między tą funkcją i [rukuj](rint-rintf-rintl.md) polega na tym, że ta funkcja nie podnosi dokładnego wyjątku zmiennoprzecinkowego.

Ponieważ maksymalne wartości zmiennoprzecinkowe są dokładnymi liczbami całkowitymi, ta funkcja nigdy nie przejdzie przez siebie. Zamiast tego dane wyjściowe mogą przekroczyć wartość zwracaną, w zależności od używanej wersji funkcji.

Język C++ umożliwia Przeciążenie, dlatego można wywoływać przeciążenia **nearbyint —** , które pobierają i zwracają **`float`** **`long double`** parametry lub. W programie C, o ile nie używasz \<tgmath.h> makra do wywołania tej funkcji, **nearbyint —** zawsze przyjmuje dwie wartości podwójne i zwraca wartość podwójnej precyzji.

Jeśli używasz \<tgmath.h> `nearbyint()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek C++|
|--------------|--------------|------------------|
|**nearbyint —**, **nearbyintf —**, **nearbyintl**|\<math.h>|\<cmath> lub \<math.h>|
|**nearbyint —** — makro | \<tgmath.h> ||

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[Obsługa obliczeń matematycznych i zmiennoprzecinkowych](../floating-point-support.md)<br/>
