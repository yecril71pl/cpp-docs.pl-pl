---
title: fmod, fmodf —, fmodl
ms.date: 04/05/2018
apiname:
- fmod
- fmodf
- fmodl
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
- fmod
- _fmodl
- fmodf
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmodl function
- fmod function
- floating-point numbers, calculating remainders
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
ms.openlocfilehash: 78677be1a0c9921c35e54d43a00b8956a9d858b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333355"
---
# <a name="fmod-fmodf-fmodl"></a>fmod, fmodf —, fmodl

Oblicza pozostałą zmiennoprzecinkową.

## <a name="syntax"></a>Składnia

```C
double fmod(
   double x,
   double y
);
float fmod(
   float x,
   float y
);  // C++ only
long double fmod(
   long double x,
   long double y
);  // C++ only
float fmodf(
   float x,
   float y
);
long double fmodl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>Parametry

*x*, *y*<br/>
Wartości zmiennoprzecinkowe.

## <a name="return-value"></a>Wartość zwracana

**fmod —** zwraca zmiennoprzecinkową resztę działania *x* / *y*. Jeśli wartość *y* jest 0,0, Metoda **fmod** zwraca ciche NaN. Aby uzyskać informacje o reprezentację cichych NaN przez **printf** rodziny, zobacz [printf](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Uwagi

**Fmod** funkcja oblicza zmiennoprzecinkową resztę *f* z *x* / *y* tak, aby *x*  =  *i* \* *y* + *f*, gdzie *i* jest liczbą całkowitą *f* ma ten sam znak co *x*, a wartość bezwzględna *f* jest mniejsza niż wartość bezwzględna *y*.

Język C++ pozwala na przeciążenie, można więc wywoływać przeciążenia **fmod** przyjmujące i zwracające **float** i **długie** **double** wartości. W programie C **fmod** zawsze przyjmuje dwa **double** argumenty i zwraca **double**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fmod —**, **fmodf —**, **fmodl**|\<math.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fmod.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = fmod( w, x );
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[_CIfmod](../../c-runtime-library/cifmod.md)<br/>
