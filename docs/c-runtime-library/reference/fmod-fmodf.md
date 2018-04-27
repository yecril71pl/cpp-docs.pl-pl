---
title: fmod —, fmodf —, fmodl | Dokumenty Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmodl function
- fmod function
- floating-point numbers, calculating remainders
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c31ec67e3b5c75c334a985461365c7b139758427
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="fmod-fmodf-fmodl"></a>fmod —, fmodf —, fmodl

Oblicza resztę zmiennoprzecinkowych.

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
Wartości zmiennoprzecinkowych.

## <a name="return-value"></a>Wartość zwracana

**fmod —** zwraca zmiennoprzecinkowe pozostałej części *x* / *y*. Jeśli wartość *y* jest 0.0, **fmod —** zwraca quiet NaN. Informacji o reprezentację quiet NaN przez **printf** rodziny, zobacz [printf](printf-printf-l-wprintf-wprintf-l.md).

## <a name="remarks"></a>Uwagi

**Fmod —** funkcja oblicza resztę zmiennoprzecinkowe *f* z *x* / *y* tak, aby *x*  =  *i* * *y* + *f*, gdzie *i* jest liczbą całkowitą *f* ma ten sam znak co *x*i wartość bezwzględną liczby *f* jest mniejsza niż wartość bezwzględną liczby *y*.

C++ pozwala przeładowanie, dlatego można wywoływać przeciążenia **fmod —** który przyjmować i zwracać **float** i **długi** **podwójne** wartości. W programie C **fmod —** zawsze ma dwa **podwójne** argumentów i zwraca **podwójne**.

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
