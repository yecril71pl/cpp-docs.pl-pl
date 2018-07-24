---
title: remainderf — resztę, remainderl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- remainderl
- remainder
- remainderf
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
- remainderf
- remainder
- remainderl
dev_langs:
- C++
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96d87a213029ab33e4d3c0269c4e7ba41e1aed43
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39209420"
---
# <a name="remainder-remainderf-remainderl"></a>remainder, remainderf, remainderl

Oblicza pozostałą część iloraz dwóch wartości zmiennoprzecinkowych zaokrąglona do najbliższej wartości całkowitej.

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

Zmiennoprzecinkową resztę działania *x* / *y*. Jeśli wartość *y* jest 0,0, Metoda **resztę** zwraca ciche NaN. Aby uzyskać informacje o reprezentowaniu cichych NaN przez **printf** rodziny, zobacz [printf, _printf_l —, wprintf, _wprintf_l —](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Uwagi

**Resztę** funkcje obliczają zmiennoprzecinkową resztę *r* z *x* / *y* tak, aby *x*   =  *n* \* *y* + *r*, gdzie *n*jest całkowitą najbliższej wartości do *x* / *y* i *n*jest parzysta zawsze wtedy, gdy &#124; *n*  -  *x* / *y* &#124; = 1/2. Gdy *r* = 0, *r* ma ten sam znak co *x*.

Ponieważ C++ pozwala na przeciążenie, można wywoływać przeciążenia **resztę** przyjmujące i zwracające **float** lub **długie** **double** wartości. W programie C **resztę** zawsze przyjmuje dwa **double** argumenty i zwraca **double**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|--------------|---------------------|-|
|**resztę**, **remainderf —**, **remainderl**|\<math.h>|\<cmath > lub \<math.h >|

Aby uzyskać informacje o zgodności – zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
