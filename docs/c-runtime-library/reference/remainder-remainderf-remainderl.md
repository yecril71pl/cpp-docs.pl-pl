---
title: remainder, remainderf, remainderl
ms.date: 4/2/2020
api_name:
- remainderl
- remainder
- remainderf
- _o_remainder
- _o_remainderf
- _o_remainderl
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
- remainderf
- remainder
- remainderl
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
ms.openlocfilehash: 4b70d3175a125d72ff67710c83899c44dbf72015
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332863"
---
# <a name="remainder-remainderf-remainderl"></a>remainder, remainderf, remainderl

Oblicza pozostałą część ilorazu dwóch wartości zmiennoprzecinkowych, zaokrąglone do najbliższej wartości integralnej.

## <a name="syntax"></a>Składnia

```C
double remainder( double x, double y );
float remainderf( float x, float y );
long double remainderl( long double x, long double y );
```

```cpp
float remainder( float x, float y ); /* C++ only */
long double remainder( long double x, long double y ); /* C++ only */
```

### <a name="parameters"></a>Parametry

*X*<br/>
Licznik.

*Y*<br/>
Mianownik.

## <a name="return-value"></a>Wartość zwracana

Zmiennoprzecinka pozostała *x* / *y*. Jeśli wartość *y* wynosi 0,0, **reszta** zwraca cichą NaN. Aby uzyskać informacje na temat reprezentacji cichej NaN przez rodzinę **printf,** zobacz [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Uwagi

Pozostałe **remainder** funkcje obliczają pozostałą powierzchnię obrotową *r* *x* / *y* tak, że *x* = *n* \* *y* + *r*, gdzie *n*jest liczą całkowitą najbliższą *wartością x* / *y* i *n,* nawet wtedy, gdy &#124; *n* - *x* / *y* &#124; = 1/2. Gdy *r* = 0, *r* ma ten sam znak co *x*.

Ponieważ C++ umożliwia przeciążenie, można wywołać przeciążenia **reszty,** które biorą i zwracają **float** lub **długie** **podwójne** wartości. W programie C **reszta** zawsze przyjmuje dwa **podwójne** argumenty i zwraca **podwójny**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|--------------|---------------------|-|
|**reszta**, **reszta ,** **reszta**|\<> math.h|\<cmath> lub \<math.h>|

Aby uzyskać informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_remainder.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = remainder(w, x);
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
