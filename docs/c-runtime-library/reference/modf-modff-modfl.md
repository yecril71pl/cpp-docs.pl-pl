---
title: modf —, modff —, modfl
ms.date: 04/05/2018
apiname:
- modff
- modf
- modfl
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
- modff
- _modfl
- modf
- modfl
- math/modf
- math/modff
- math/modfl
helpviewer_keywords:
- modf function
- modff function
- modfl function
ms.assetid: b1c7abf5-d476-43ca-a03c-02072a86e32d
ms.openlocfilehash: 59d6e2b9b02ad182c5630d6dc9a989c035e8fa92
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156333"
---
# <a name="modf-modff-modfl"></a>modf —, modff —, modfl

Dzieli wartość zmiennoprzecinkowa do ułamkową i całkowitą części.

## <a name="syntax"></a>Składnia

```C
double modf( double x, double * intptr );
float modff( float x, float * intptr );
long double modfl( long double x, long double * intptr );
```

```cpp
float modf( float x, float * intptr );  // C++ only
long double modf( long double x, long double * intptr );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa.

*intptr*<br/>
Wskaźnik do część całkowitą przechowywanych.

## <a name="return-value"></a>Wartość zwracana

Ta funkcja zwraca część ułamkową ze znakiem *x*. Nie będzie zwrotu błędu.

## <a name="remarks"></a>Uwagi

**Modf —** funkcje podzielić wartość zmiennoprzecinkową *x* w ułamkową i całkowitą części, z których każdy ma ten sam znak co *x*. Oznaczona ułamkowa część *x* jest zwracana. Część całkowitą jest przechowywany jako wartość zmiennoprzecinkowa o *intptr*.

**modf —** zawiera implementację, która używa Streaming SIMD Extensions 2 (SSE2). Zobacz [_set_sse2_enable —](set-sse2-enable.md) informacje i ograniczenia dotyczące przy użyciu implementacji SSE2.

Język C++ pozwala na przeciążenie, można więc wywoływać przeciążenia **modf —** przyjmujące i zwracające **float** lub **długie** **double** parametrów. W programie C **modf —** zawsze przyjmuje dwie wartości double i zwraca wartość typu double.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**modf —**, **modff —**, **modfl**|C: \<math.h><br /><br /> C++:, \<cmath > lub \<math.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_modf.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y, n;

   x = -14.87654321;      /* Divide x into its fractional */
   y = modf( x, &n );     /* and integer parts            */

   printf( "For %f, the fraction is %f and the integer is %.f\n",
           x, y, n );
}
```

```Output
For -14.876543, the fraction is -0.876543 and the integer is -14
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
