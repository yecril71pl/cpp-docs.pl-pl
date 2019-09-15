---
title: frexp —, frexpf —, frexpl
ms.date: 04/05/2018
api_name:
- frexp
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
- frexp
- _frexpl
helpviewer_keywords:
- _frexpl function
- mantissas, floating-point variables
- frexpl function
- exponent, floating-point numbers
- frexp function
- floating-point functions, mantissa and exponent
ms.assetid: 9b020f2e-3967-45ec-a6a8-d467a071aa55
ms.openlocfilehash: 3a67ced9bd6653a7c40c98a8cf015663c37457bb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956636"
---
# <a name="frexp-frexpf-frexpl"></a>frexp —, frexpf —, frexpl

Pobiera mantysy i wykładnik liczby zmiennoprzecinkowej.

## <a name="syntax"></a>Składnia

```C
double frexp(
   double x,
   int *expptr
);
float frexpf(
   float x,
   int * expptr
);
long double frexpl(
   long double x,
   int * expptr
);
float frexp(
   float x,
   int * expptr
);  // C++ only
long double frexp(
   long double x,
   int * expptr
);  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa.

*expptr*<br/>
Wskaźnik do przechowywanego wykładniku liczb całkowitych.

## <a name="return-value"></a>Wartość zwracana

**frexp —** zwraca mantysy. Jeśli *x* to 0, funkcja zwraca 0 dla mantysy i wykładnika. Jeśli *expptr* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca wartość 0.

## <a name="remarks"></a>Uwagi

Funkcja **frexp —** dzieli wartość zmiennoprzecinkową (*x*) na mantysy (*m*) i wykładnik (*n*), w taki sposób, że wartość bezwzględna *m* jest większa lub równa 0,5 i mniejsza niż 1,0 i *x*  =  *m* * 2<sup>*n*</sup>. Wykładnik całkowity *n* jest przechowywany w lokalizacji wskazywanej przez *expptr*.

C++umożliwia Przeciążenie, dzięki czemu można wywoływać przeciążenia **frexp —** . W programie C **frexp —** zawsze Pobiera wskaźnik **Double** i **int** i zwraca wartość **Double**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**frexp —** , **frexpf —** , **frexpl**|\<math.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_frexp.c
// This program calculates frexp( 16.4, &n )
// then displays y and n.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y;
   int n;

   x = 16.4;
   y = frexp( x, &n );
   printf( "frexp( %f, &n ) = %f, n = %d\n", x, y, n );
}
```

```Output
frexp( 16.400000, &n ) = 0.512500, n = 5
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
