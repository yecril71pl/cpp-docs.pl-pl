---
title: ldexp —, ldexpf —, ldexpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- ldexp
- ldexpf
- ldexpl
- _ldexpl
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
- ldexp
- ldexpf
- ldexpl
- _ldexpl
dev_langs:
- C++
helpviewer_keywords:
- calculating real numbers
- computing real numbers
- mantissas, floating-point variables
- ldexp function
- ldexpf function
- ldexpl function
- exponent, floating-point numbers
- floating-point functions, mantissa and exponent
ms.assetid: aa7f5310-3879-4f63-ae74-86a39fbdedfa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ead91ce542ce547f9453f52455dc76d61045b87
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39208418"
---
# <a name="ldexp-ldexpf-ldexpl"></a>ldexp —, ldexpf —, ldexpl

Mnoży liczbę zmiennoprzecinkową przez całkowitą potęgą liczby dwa.

## <a name="syntax"></a>Składnia

```C
double ldexp(
   double x,
   int exp
);
float ldexp(
   float x,
   int exp
);  // C++ only
long double ldexp(
   long double x,
   int exp
);  // C++ only
float ldexpf(
   float x,
   int exp
);
long double ldexpl(
   long double x,
   int exp
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa.

*EXP*<br/>
Wykładnik potęgi liczby całkowitej.

## <a name="return-value"></a>Wartość zwracana

**Ldexp —** funkcje zwracają wartość *x* \* 2<sup>*exp* </sup> w przypadku powodzenia. Przy przepełnieniu oraz od jej znaku *x*, **ldexp —** zwraca wartość +/- **HUGE_VAL**; **errno** wartość jest równa **ERANGE** .

Aby uzyskać więcej informacji na temat **errno** i błędach zwracają wartości, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na przeciążenie, można wywoływać przeciążenia **ldexp —** o **float** lub **długie** **double** typów. W programie C **ldexp —** zawsze ma **double** i **int** i zwraca **double**.

## <a name="requirements"></a>Wymagania

|Procedura|Nagłówek języka C|Nagłówek języka C++|
|-------------|--------------|------------------|
|**ldexp —**, **ldexpf —**, **ldexpl**|\<math.h>|\<cmath >|

Aby uzyskać informacje o zgodności – zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_ldexp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 4.0, y;
   int p = 3;

   y = ldexp( x, p );
   printf( "%2.1f times two to the power of %d is %2.1f\n", x, p, y );
}
```

## <a name="output"></a>Dane wyjściowe

```Output
4.0 times two to the power of 3 is 32.0
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
