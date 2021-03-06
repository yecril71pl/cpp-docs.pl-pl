---
title: modf, modff, modfl
description: Dokumentacja interfejsu API dla modf —, modff — i modfl; dzieląc wartość zmiennoprzecinkową na części ułamkowe i całkowite.
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 0d3522079acc8a9d2c8409b1cad78e7f50a7f788
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556765"
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

*x*<br/>
Wartość zmiennoprzecinkowa.

*IntPtr*<br/>
Wskaźnik do przechowywanej części całkowitej.

## <a name="return-value"></a>Wartość zwracana

Ta funkcja zwraca podpisaną część ułamkową *x*. Nie ma żadnego powrotu błędu.

## <a name="remarks"></a>Uwagi

Funkcja **modf —** dzieli wartość zmiennoprzecinkową *x* na części ułamkowe i całkowite, z których każdy ma ten sam znak jako *x*. Zwracana jest podpisana część ułamkowa *x* . Część całkowita jest przechowywana jako wartość zmiennoprzecinkowa w *IntPtr*.

**modf —** ma implementację, która używa Streaming SIMD Extensions 2 (SSE2). Zobacz [_set_SSE2_enable](set-sse2-enable.md) , aby uzyskać informacje i ograniczenia dotyczące korzystania z implementacji SSE2.

Język C++ umożliwia Przeciążenie, dlatego można wywoływać przeciążenia **modf —** , które pobierają i zwracają **`float`** **`long double`** parametry lub. W programie C **modf —** zawsze przyjmuje dwie wartości podwójne i zwraca wartość podwójnej precyzji.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**modf —**, **modff —**, **modfl**|S \<math.h><br /><br /> C++:, \<cmath> lub \<math.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
