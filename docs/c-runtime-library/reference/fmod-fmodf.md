---
title: fmod, fmodf, fmodl
ms.date: 4/2/2020
api_name:
- fmod
- fmodf
- fmodl
- _o_fmod
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
ms.openlocfilehash: 0cf25e2029f06c2e02a24ca84926e1a8b8f30159
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346551"
---
# <a name="fmod-fmodf-fmodl"></a>fmod, fmodf, fmodl

Oblicza pozostałą część zmiennoprzecinową.

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

**fmod** zwraca zmiennoprzecinkową pozostałą część *x* / *y*. Jeśli wartość *y* wynosi 0,0, **fmod** zwraca cichą wartość NaN. Aby uzyskać informacje na temat reprezentacji cichej nan przez rodzinę **printf,** zobacz [printf](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Uwagi

Funkcja **fmod** oblicza pozostałą część zmiennoprzecinową *f* *x* / *y* tak, że *x* = *i* \* *y* + *f*, gdzie *i* jest liczą całkowitą, *f* ma ten sam znak co *x*, a wartość bezwzględna *f* jest mniejsza niż wartość *bezwzględna y*.

C++ umożliwia przeciążenie, dzięki czemu można wywołać przeciążenia **fmod,** które biorą i zwracają **float** i **długie** **podwójne** wartości. W programie C **fmod** zawsze przyjmuje dwa **podwójne** argumenty i zwraca **podwójny**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fmod**, **fmodf**, **fmodl**|\<> math.h|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[_CIfmod](../../c-runtime-library/cifmod.md)<br/>
