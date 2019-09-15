---
title: remquo, remquof, remquol
ms.date: 04/05/2018
api_name:
- remquof
- remquo
- remquol
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
- remquof
- remquol
- remquo
helpviewer_keywords:
- remquol function
- remquof function
- remquo function
ms.assetid: a1d3cb8b-8027-4cd3-8deb-04eb17f299fc
ms.openlocfilehash: c96357dda007e9bf12ddaf6091af47794bfc0630
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949365"
---
# <a name="remquo-remquof-remquol"></a>remquo, remquof, remquol

Oblicza pozostałą część dwóch wartości całkowitych i przechowuje wartość całkowitą ze znakiem i przybliżoną wielkością ilorazu w lokalizacji określonej w parametrze.

## <a name="syntax"></a>Składnia

```C
double remquo( double numer, double denom, int* quo );
float remquof( float numer, float denom, int* quo );
long double remquol( long double numer, long double denom, int* quo );
```

```cpp
float remquo( float numer, float denom, int* quo ); /* C++ only */
long double remquo( long double numer, long double denom, int* quo ); /* C++ only */
```

### <a name="parameters"></a>Parametry

*numeracj*<br/>
Licznik.

*denom*<br/>
Mianownik.

*quo*<br/>
Wskaźnik do liczby całkowitej do przechowywania wartości, która ma znak i przybliżoną wielkość ilorazu.

## <a name="return-value"></a>Wartość zwracana

**remquo —** zwraca liczbę zmiennoprzecinkową z przestawu *x* / *y*. Jeśli wartość *y* to 0,0, **remquo —** zwraca cichy NaN. Aby uzyskać informacje o reprezentacji cichej wartości NaN przez rodzinę **printf** , zobacz [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Uwagi

Funkcja **remquo —** oblicza pozostałą liczbę zmiennoprzecinkową *f* z *x* / *y* , taką jak *x* = *i* \* *y* + *f*, *gdzie* jest liczbą całkowitą, *f* ma ten sam znak jako *x*, a wartość bezwzględna *f* jest mniejsza niż wartość bezwzględna *y*.

C++zezwala na Przeciążenie, dzięki czemu można wywoływać przeciążenia **remquo —** , które pobierają i zwracają wartości **zmiennoprzecinkowe** lub **długie** o **podwójnej precyzji** . W programie C **remquo —** zawsze przyjmuje dwa **podwójne** argumenty i zwraca wartość **podwójną**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|--------------|---------------------|-|
|**remquo**, **remquof**, **remquol**|\<math.h>|\<cmath > lub \<Math. h >|

Aby uzyskać informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_remquo.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;
   int quo = 0;

   z = remquo(w, x, &quo);
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);
   printf("Approximate signed quotient is %d\n", quo);
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
Approximate signed quotient is -3
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[remainder, remainderf, remainderl](remainder-remainderf-remainderl.md)<br/>
