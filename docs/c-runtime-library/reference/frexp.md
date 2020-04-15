---
title: frexp, frexpf, frexpl
ms.date: 4/2/2020
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 79fe70341f0d6fef1dc7fe00f872456a11972876
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345797"
---
# <a name="frexp-frexpf-frexpl"></a>frexp, frexpf, frexpl

Pobiera mantysi i wykładnik liczby zmiennoprzecinkowej.

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

*X*<br/>
Wartość zmiennoprzecinku.

*expptr (np.*<br/>
Wskaźnik do przechowywanego wykładnika liczby całkowitej.

## <a name="return-value"></a>Wartość zwracana

**frexp** zwraca mantysi. Jeśli *x* wynosi 0, funkcja zwraca wartość 0 zarówno dla modliszki, jak i wykładnika. Jeśli *wartość null* jest **null,** nieprawidłowy program obsługi parametrów jest wywoływany zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **EINVAL** i zwraca 0.

## <a name="remarks"></a>Uwagi

Funkcja **frexp** dzieli wartość zmiennoprzecinkową (*x*) na modlisę (*m)* i wykładnik (*n*), tak, że wartość bezwzględna *m* jest większa lub równa 0,5 i mniejszej niż 1,0, oraz *x* = *m* * 2<sup>*n*</sup>. Wykładnik liczby całkowitej *n* jest przechowywany w miejscu wskazanym przez *expptr*.

C++ umożliwia przeciążenie, dzięki czemu można wywołać przeciążenia **frexp**. W programie C **frexp** zawsze przyjmuje **podwójny** i **int** wskaźnik i zwraca **podwójny**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**frexp**, **frexpf**, **frexpl**|\<> math.h|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
