---
title: nearbyint, nearbyintf, nearbyintl
ms.date: 04/05/2018
api_name:
- nearbyint
- nearbyintf
- nearbyintl
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
ms.openlocfilehash: cd0a7d00c5019dd1e483d555df6db8d9770e61c1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951394"
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

*x*<br/>
Wartość do zaokrąglenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca wartość *x*, zaokrągloną do najbliższej liczby całkowitej, przy użyciu bieżącego formatu zaokrąglania, który jest raportowany przez [fegetround](fegetround-fesetround2.md). W przeciwnym razie funkcja może zwracać jedną z następujących wartości:

|Problem|przesłać|
|-----------|------------|
|*x* = ± nieskończoność|NIESKOŃCZONość, niezmodyfikowana|
|*x* = ± 0|0, niemodyfikowane|
|*x* = NaN|NaN|

Błędy nie są zgłaszane przez [_matherr](matherr.md); w przypadku tej funkcji nie są raportowane żadne wyjątki **FE_INEXACT** .

## <a name="remarks"></a>Uwagi

Podstawowa różnica między tą funkcją i [rukuj](rint-rintf-rintl.md) polega na tym, że ta funkcja nie podnosi dokładnego wyjątku zmiennoprzecinkowego.

Ponieważ maksymalne wartości zmiennoprzecinkowe są dokładnymi liczbami całkowitymi, ta funkcja nigdy nie przejdzie przez siebie. Zamiast tego dane wyjściowe mogą przekroczyć wartość zwracaną, w zależności od używanej wersji funkcji.

C++umożliwia Przeciążenie, dlatego można wywoływać przeciążenia **nearbyint —** , które pobierają i zwracają parametry **zmiennoprzecinkowe** lub **długie** . W programie C **nearbyint —** zawsze przyjmuje dwie wartości podwójne i zwraca wartość podwójnej precyzji.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|C++nagłówki|
|--------------|--------------|------------------|
|**nearbyint —** , **nearbyintf —** , **nearbyintl**|\<math.h>|\<cmath > lub \<Math. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[Obsługa obliczeń matematycznych i zmiennoprzecinkowych](../floating-point-support.md)<br/>
