---
title: remainder, remainderf, remainderl
ms.date: 04/05/2018
api_name:
- remainderl
- remainder
- remainderf
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
- remainderf
- remainder
- remainderl
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
ms.openlocfilehash: 851f022325bb617cb2b0ae9a331b680b9d9fd303
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949426"
---
# <a name="remainder-remainderf-remainderl"></a>remainder, remainderf, remainderl

Oblicza resztę ilorazu dwóch wartości zmiennoprzecinkowych zaokrągloną do najbliższej wartości całkowitej.

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

*x*<br/>
Licznik.

*y*<br/>
Mianownik.

## <a name="return-value"></a>Wartość zwracana

Pozostała liczba zmiennoprzecinkowa *x* / *y*. Jeśli wartość *y* to 0,0, **reszta** zwraca cichy NaN. Aby uzyskać informacje o reprezentacji cichej wartości NaN przez rodzinę **printf** , zobacz [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Uwagi

**Pozostałe** funkcje obliczają liczbę zmiennoprzecinkową *r* z *x* / *y* , taką jak *x* = *n* \* *y* + *r*, gdzie *n* jest liczbą całkowitą najbliższą wartości do *x* / *y* i *n*jest nawet za &#124; każdym razem, gdy *n* - *x* / *y* &#124; = 1/2. Gdy *r* = 0, *r* ma ten sam znak jako *x*.

Ponieważ C++ umożliwia Przeciążenie, można wywoływać przeciążenia **reszty** , które pobierają i zwracają wartości **zmiennoprzecinkowe** lub **długie** **Double** . W programie C **pozostała część** zawsze przyjmuje dwa **podwójne** argumenty i zwraca wartość **podwójnej precyzji**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|--------------|---------------------|-|
|**reszta**, **remainderf —** , **reszta**|\<math.h>|\<cmath > lub \<Math. h >|

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

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[remquo, remquof, remquol](remquo-remquof-remquol.md)<br/>
