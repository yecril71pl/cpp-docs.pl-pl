---
title: remquo —, remquof —, remquol — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- remquof
- remquo
- remquol
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
- remquof
- remquol
- remquo
dev_langs:
- C++
helpviewer_keywords:
- remquol function
- remquof function
- remquo function
ms.assetid: a1d3cb8b-8027-4cd3-8deb-04eb17f299fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 480bf65d61581866fe447c9563a267d08d17c838
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207656"
---
# <a name="remquo-remquof-remquol"></a>remquo, remquof, remquol

Oblicza pozostałą część dwóch wartości całkowitych i przechowuje wartość całkowitą ze znakiem i przybliżoną wielkością współczynnika w lokalizacji, która jest określona w parametrze.

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

*numer*<br/>
Licznik.

*denom*<br/>
Mianownik.

*informacje o istniejącym*<br/>
Wskaźnik na liczbę całkowitą określającą wartość, która ma znak i przybliżonej wielkości ilorazu.

## <a name="return-value"></a>Wartość zwracana

**remquo —** zwraca zmiennoprzecinkową resztę działania *x* / *y*. Jeśli wartość *y* jest 0,0, Metoda **remquo —** zwraca ciche NaN. Aby uzyskać informacje o reprezentowaniu cichych NaN przez **printf** rodziny, zobacz [printf, _printf_l —, wprintf, _wprintf_l —](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Uwagi

**Remquo —** funkcja oblicza zmiennoprzecinkową resztę *f* z *x* / *y* tak, aby *x*   =  *i* \* *y* + *f*, gdzie *i* jest liczbą całkowitą , *f* ma ten sam znak co *x*, a wartość bezwzględna *f* jest mniejsza niż wartość bezwzględna *y*.

Język C++ pozwala na przeciążenie, można więc wywoływać przeciążenia **remquo —** przyjmujące i zwracające **float** lub **długie** **double** wartości. W programie C **remquo —** zawsze przyjmuje dwa **double** argumenty i zwraca **double**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|--------------|---------------------|-|
|**remquo —**, **remquof —**, **remquol —**|\<math.h>|\<cmath > lub \<math.h >|

Aby uzyskać informacje o zgodności – zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
