---
title: modf, modff, modfl
ms.date: 4/2/2020
api_name:
- modff
- modf
- modfl
- _o_modf
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
ms.openlocfilehash: b509da5f18ea1f606b8a3b47ab66a78e4f595558
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338694"
---
# <a name="modf-modff-modfl"></a>modf, modff, modfl

Dzieli wartość zmiennoprzecinkową na części ułamkowe i całkowite.

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

*X*<br/>
Wartość zmiennoprzecinku.

*Intptr*<br/>
Wskaźnik do przechowywanej części całkowitej.

## <a name="return-value"></a>Wartość zwracana

Ta funkcja zwraca podpisaną ułamkową część *x*. Nie ma zwracania błędów.

## <a name="remarks"></a>Uwagi

Funkcje **modf** rozkładają wartość zmiennoprzecinkową *x* na części ułamkowe i całkowite, z których każda ma ten sam znak co *x*. Zwracana jest podpisana ułamkowa część *x.* Część całkowita jest przechowywana jako wartość zmiennoprzecinkowa *w intptr*.

**modf** ma implementację, która używa streamingu rozszerzeń SIMD 2 (SSE2). Zobacz [_set_SSE2_enable,](set-sse2-enable.md) aby uzyskać informacje i ograniczenia dotyczące korzystania z implementacji SSE2.

C++ umożliwia przeciążenie, dzięki czemu można wywołać przeciążenia **modf,** które biorą i zwracają **float** lub **długie** **podwójne** parametry. W programie C **modf** zawsze przyjmuje dwie podwójne wartości i zwraca podwójną wartość.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**modf**, **modff**, **modfl**|C: \<> math.h<br /><br /> C++: \<, cmath> \<lub math.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
