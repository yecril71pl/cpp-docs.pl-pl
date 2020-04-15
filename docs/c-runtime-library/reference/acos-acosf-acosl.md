---
title: acos, acosf, acosl
ms.date: 4/2/2020
api_name:
- acosf
- acos
- acosl
- _o_acos
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
- acos
- acosl
- acosf
- math/acosf
- math/acosl
helpviewer_keywords:
- acos function
- acosl function
- acosf function
- trigonometric functions
- arccosine function
ms.assetid: 00b89c48-8faf-4824-aa95-fa4349a4975d
ms.openlocfilehash: 4dd467ab807875dcf4236e4fbb744c77ec47880d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348971"
---
# <a name="acos-acosf-acosl"></a>acos, acosf, acosl

Oblicza arckozynę.

## <a name="syntax"></a>Składnia

```C
double acos( double x );
float acosf( float x );
long double acosl( long double x );
```

```cpp
float acos( float x );   // C++ only
long double acos( long double x );   // C++ only
```

### <a name="parameters"></a>Parametry

*X*<br/>
Wartość od -1 do 1, dla której ma być obliczona arckozyna (odwrotna cosine).

## <a name="return-value"></a>Wartość zwracana

Funkcja **acos** zwraca arckozynę *x* w zakresie od 0 do π radianów.

Domyślnie, jeśli *x* jest mniejsza niż -1 lub większa niż 1, **acos** zwraca nieokreślony.

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|± ∞|Nieprawidłowy|_DOMAIN|
|± QNAN, IND|brak|_DOMAIN|
|&#124;x&#124;>1|Nieprawidłowy|_DOMAIN|

## <a name="remarks"></a>Uwagi

Ponieważ C++ umożliwia przeciążenie, można wywołać przeciążenia **acos,** które biorą i zwracają **float** i **długie** **podwójne** typy. W programie **C, acos** zawsze ma i zwraca **podwójne**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**akos**, **acosf**, **acosl**|\<> math.h|\<> errno.h|

## <a name="example"></a>Przykład

Ten program monituje o wartość w zakresie od -1 do 1. Wartości wejściowe spoza `_DOMAIN` tego zakresu generują komunikaty o błędach. Jeśli zostanie wprowadzona prawidłowa wartość, program drukuje arcsine i arccosine tej wartości.

```C
// crt_asincos.c
// arguments: 0

#include <math.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( int ac, char* av[] )
{
    double  x,
            y;
    errno_t err;

    // argument checking
    if (ac != 2)
    {
        fprintf_s( stderr, "Usage: %s <number between -1 and 1>\n",
                   av[0]);
        return 1;
    }

    // Convert argument into a double value
    if ((err = sscanf_s( av[1], "%lf", &x )) != 1)
    {
        fprintf_s( stderr, "Error converting argument into ",
                   "double value.\n");
        return 1;
    }

    // Arcsine of X
    y = asin( x );
    printf_s( "Arcsine of %f = %f\n", x, y );

    // Arccosine of X
    y = acos( x );
    printf_s( "Arccosine of %f = %f\n", x, y );
}
```

```Output
Arcsine of 0.000000 = 0.000000
Arccosine of 0.000000 = 1.570796
```

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)
