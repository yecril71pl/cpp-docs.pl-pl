---
title: remainder, remainderf, remainderl
description: Dokumentacja interfejsu API dla pozostałej, remainderf — i reszty; które oblicza resztę ilorazu dwóch wartości zmiennoprzecinkowych, zaokrągloną do najbliższej wartości całkowitej.
ms.date: 9/1/2020
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: ef2b326bef2288b52dba8988749e030ff0b46077
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556012"
---
# <a name="remainder-remainderf-remainderl"></a>remainder, remainderf, remainderl

Oblicza resztę ilorazu dwóch wartości zmiennoprzecinkowych zaokrągloną do najbliższej wartości całkowitej.

## <a name="syntax"></a>Składnia

```C
double remainder( double x, double y );
float remainderf( float x, float y );
long double remainderl( long double x, long double y );
#define remainder(X, Y) // Requires C11 or higher

float remainder( float x, float y ); /* C++ only */
long double remainder( long double x, long double y ); /* C++ only */
```

### <a name="parameters"></a>Parametry

*y*\
Licznik.

*t*\
Mianownik.

## <a name="return-value"></a>Wartość zwracana

Pozostała liczba zmiennoprzecinkowa *x*  /  *y*. Jeśli wartość *y* to 0,0, **reszta** zwraca cichy NaN. Aby uzyskać informacje o reprezentacji cichej wartości NaN przez rodzinę **printf** , zobacz [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Uwagi

**Pozostałe** funkcje obliczają liczbę zmiennoprzecinkową *r* z *x*  /  *y* , tak że *x*  =  *n* \* *y*  +  *r*, gdzie *n*jest liczbą całkowitą najbliższą wartości do *x*  /  *y* i *n*, nawet wtedy, gdy &#124; *n*  -  *x*  /  *y* &#124; = 1/2. Gdy *r* = 0, *r* ma ten sam znak jako *x*.

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **reszty** , które pobierają i **`float`** zwracają **`long double`** wartości. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **reszta** zawsze przyjmuje dwa **`double`** argumenty i zwraca **`double`** .

Jeśli używasz \<tgmath.h> `remainder()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|--------------|---------------------|-|
|**reszta**, **remainderf —**, **reszta**|\<math.h>|\<cmath> lub \<math.h>|
|**Pozostałe** makro | \<tgmath.h> ||

Aby uzyskać informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)\
[ldiv, lldiv](ldiv-lldiv.md)\
[imaxdiv](imaxdiv.md)\
[FMOD —, fmodf —](fmod-fmodf.md)\
[remquo, remquof, remquol](remquo-remquof-remquol.md)
