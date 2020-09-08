---
title: frexp —, frexpf —, frexpl
description: Dokumentacja interfejsu API dla frexp —, frexpf — i frexpl; który pobiera mantysy i wykładnik liczby zmiennoprzecinkowej.
ms.date: 9/1/2020
api_name:
- frexp
- _o_frexp
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
ms.openlocfilehash: a23de4160abcfab2518125bfa0fd35a389901674
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555751"
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
#define frexpl(X, INT_PTR) // Requires C11 or higher
```

```cpp
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

*y*\
Wartość zmiennoprzecinkowa.

*expptr*\
Wskaźnik do przechowywanego wykładniku liczb całkowitych.

## <a name="return-value"></a>Wartość zwracana

**frexp —** zwraca mantysy. Jeśli *x* to 0, funkcja zwraca 0 dla mantysy i wykładnika. Jeśli *expptr* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca wartość 0.

## <a name="remarks"></a>Uwagi

Funkcja **frexp —** dzieli wartość zmiennoprzecinkową (*x*) na mantysy (*m*) i wykładnik (*n*), tak że wartość bezwzględna *m* jest większa lub równa 0,5 i mniejsza niż 1,0 i *x*  =  *m* * 2<sup>*n*</sup>. Wykładnik całkowity *n* jest przechowywany w lokalizacji wskazywanej przez *expptr*.

Język C++ umożliwia Przeciążenie, dlatego można wywoływać przeciążenia **frexp —**. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **frexp —** zawsze przyjmuje **`double`** wskaźnik i **`int`** zwraca **`double`** .

Jeśli używasz \<tgmath.h> `frexp()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**frexp —**, **frexpf —**, **frexpl**|\<math.h>|
|**frexp —** — makro | \<tgmath.h> |

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

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
