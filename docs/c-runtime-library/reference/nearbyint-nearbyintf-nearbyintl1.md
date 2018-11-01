---
title: nearbyint, nearbyintf, nearbyintl
ms.date: 04/05/2018
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
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
ms.openlocfilehash: 4a36bddb28db9fb4c5809432dfaef9ca3ece4328
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668315"
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint, nearbyintf, nearbyintl

Zaokrągla określoną wartość zmiennoprzecinkowa do liczby całkowitej i zwraca tę wartość w formacie zmiennoprzecinkowych.

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

Jeśli operacja się powiedzie, zwraca *x*, zaokrąglony do najbliższej liczby całkowitej, przy użyciu bieżącego formatu zaokrąglania zgłoszonej przez [fegetround](fegetround-fesetround2.md). W przeciwnym razie funkcja może zwracać jedną z następujących wartości:

|Problem|Wróć|
|-----------|------------|
|*x* = ±INFINITY|±INFINITY w niezmienionej postaci|
|*x* = ±0|±0 w niezmienionej postaci|
|*x* = NaN|NaN|

Błędy nie są raportowane za pośrednictwem [_matherr](matherr.md); ściślej mówiąc, ta funkcja nie zgłasza dowolne **FE_INEXACT** wyjątków.

## <a name="remarks"></a>Uwagi

Główną różnicą między tej funkcji i [rukuj](rint-rintf-rintl.md) jest ta funkcja nie zgłaszała niedokładny wyjątek punktu zmiennoprzecinkowego.

Ponieważ maksymalnej wartości zmiennoprzecinkowe są dokładne liczb całkowitych, ta funkcja nigdy nie będzie overflow siebie. przeciwnie dane wyjściowe możliwe przepełnienie zwracanej wartości, w zależności od instalowanej wersji funkcji używasz.

Język C++ pozwala na przeciążenie, można więc wywoływać przeciążenia **nearbyint —** przyjmujące i zwracające **float** lub **długie** **double** parametrów. W programie C **nearbyint —** zawsze przyjmuje dwie wartości double i zwraca wartość typu double.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**nearbyint —**, **nearbyintf —**, **nearbyintl**|\<math.h>|\<cmath > lub \<math.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[Matematyczne i Obsługa liczb zmiennoprzecinkowych](../floating-point-support.md)<br/>
