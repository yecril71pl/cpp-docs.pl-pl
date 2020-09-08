---
title: ldexp —, ldexpf —, ldexpl
description: Dokumentacja interfejsu API dla ldexp —, ldexpf — i ldexpl; dzięki czemu iloczyn liczby zmiennoprzecinkowej jest mnożony przez całkowitą moc dwóch.
ms.date: 9/1/2020
api_name:
- ldexp
- ldexpf
- ldexpl
- _ldexpl
- _o_ldexp
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
- ldexp
- ldexpf
- ldexpl
- _ldexpl
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
ms.openlocfilehash: 6ce6bcbc8adbc62e8d8598b97a6f77e04fee1511
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555452"
---
# <a name="ldexp-ldexpf-ldexpl"></a>ldexp —, ldexpf —, ldexpl

Mnoży liczbę zmiennoprzecinkową przez całkowitą potęgę dwóch.

## <a name="syntax"></a>Składnia

```C
double ldexp(
   double x,
   int exp
);
float ldexpf(
   float x,
   int exp
);
long double ldexpl(
   long double x,
   int exp
);
#define ldexp(X, INT) // Requires C11 or higher

float ldexp(
   float x,
   int exp
);  // C++ only
long double ldexp(
   long double x,
   int exp
);  // C++ only
```

### <a name="parameters"></a>Parametry

*y*\
Wartość zmiennoprzecinkowa.

*EXP*\
Wykładnik wartości całkowitej.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia funkcja **ldexp —** zwraca wartość *x* \* 2<sup>*exp*</sup> . W przypadku przepełnienia i w zależności od znaku *x*, **ldexp —** zwraca +/- **HUGE_VAL**; wartość **errno** jest ustawiona na **ERANGE**.

Aby uzyskać więcej informacji na temat **errno** i możliwych zwracanych wartości błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **ldexp —** przyjmujących **`float`** lub **`long double`** . W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **ldexp —** zawsze przyjmuje **`double`** i **`int`** i zwraca **`double`** .

Jeśli używasz \<tgmath.h> `ldexp()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Nagłówek języka C|Nagłówek C++|
|-------------|--------------|------------------|
|**ldexp —**, **ldexpf —**, **ldexpl**|\<math.h>|\<cmath>|
|**ldexp —** — makro | \<tgmath.h> ||

Aby uzyskać informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
