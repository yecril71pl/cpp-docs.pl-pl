---
title: Stałe matematyczne
ms.date: 11/04/2016
f1_keywords:
- c.constants.math
helpviewer_keywords:
- M_PI constant
- M_PI_2 constant
- math constants
- M_2_PI constant
- M_1_PI constant
- M_E constant
- USE_MATH_DEFINES constant
- M_LOG2E constant
- M_LOG10E constant
- M_LN10 constant
- M_SQRT1_2 constant
- _USE_MATH_DEFINES constant
- M_PI_4 constant
- constants, math
- M_2_SQRTPI constant
- M_SQRT2 constant
- M_LN2 constant
ms.assetid: db533c3f-6ae8-4520-9d35-c8fabbef3529
ms.openlocfilehash: 156e4df4bcd4be457f2d14e7e5f5531d93d642be
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438263"
---
# <a name="math-constants"></a>Stałe matematyczne

## <a name="syntax"></a>Składnia

```
#define _USE_MATH_DEFINES // for C++
#include <cmath>

#define _USE_MATH_DEFINES // for C
#include <math.h>
```

## <a name="remarks"></a>Uwagi

Następujące symbole są zdefiniowane dla wartości ich wskazanych wyrażeń:

|Symbol|Wyrażenie|Wartość|
|------------|----------------|-----------|
|M_E|e|2.71828182845904523536|
|M_LOG2E|log2 — (e)|1.44269504088896340736|
|M_LOG10E|LOG10 — (e)|0.434294481903251827651|
|M_LN2|ln(2)|0.693147180559945309417|
|M_LN10|ln(10)|2.30258509299404568402|
|M_PI|przetwarzania|3.14159265358979323846|
|M_PI_2|Pi/2|1.57079632679489661923|
|M_PI_4|Pi/4|0.785398163397448309616|
|M_1_PI|1/pi|0.318309886183790671538|
|M_2_PI|2/pi|0.636619772367581343076|
|M_2_SQRTPI|2/sqrt(pi)|1.12837916709551257390|
|M_SQRT2|sqrt(2)|1.41421356237309504880|
|M_SQRT1_2|1/sqrt(2)|0.707106781186547524401|

Stałe matematyczne nie są zdefiniowane w standardowymC++języku C/. Aby ich używać, należy najpierw zdefiniować `_USE_MATH_DEFINES` a następnie uwzględnić cmath lub Math. h.

Plik ATLComTime. h zawiera zapis Math. h, gdy projekt jest skompilowany w trybie wydania. Jeśli używasz co najmniej jednej z stałych matematycznych w projekcie, który zawiera także ATLComTime. h, musisz zdefiniować `_USE_MATH_DEFINES` przed dołączeniem ATLComTime. h.

## <a name="see-also"></a>Zobacz też

[Stałe globalne](../c-runtime-library/global-constants.md)
