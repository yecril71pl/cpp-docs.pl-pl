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
ms.openlocfilehash: d9e7adb321d85c728c5185c1663fd7f945fc4a82
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914579"
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

*y*<br/>
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

Język C++ pozwala na Przeciążenie, dlatego można wywoływać przeciążenia **nearbyint —** , które pobierają i **zwracają parametry** **zmiennoprzecinkowe** lub **długie** . W programie C **nearbyint —** zawsze przyjmuje dwie wartości podwójne i zwraca wartość podwójnej precyzji.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek C++|
|--------------|--------------|------------------|
|**nearbyint —**, **nearbyintf —**, **nearbyintl**|\<> Math. h|\<cmath> lub \<Math. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[Obsługa obliczeń matematycznych i zmiennoprzecinkowych](../floating-point-support.md)<br/>
