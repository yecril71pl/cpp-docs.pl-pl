---
title: acos, acosf, acosl
description: Dokumentacja interfejsu API dla `acos` , `acosf` , i `acosl` ;, która oblicza arcus cosinus wartości zmiennoprzecinkowej.
ms.date: 08/31/2020
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: eeee51cea2a81882ee1ed8b014312ee9f9095dc6
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555101"
---
# <a name="acos-acosf-acosl"></a>acos, acosf, acosl

Oblicza arcus cosinus.

## <a name="syntax"></a>Składnia

```C
double acos( double x );
float acosf( float x );
long double acosl( long double x );
#define acos(X) // Requires C11 or higher

float acos( float x );   // C++ only
long double acos( long double x );   // C++ only
```

### <a name="parameters"></a>Parametry

*y*\
Wartość z przedziału od-1 do 1, dla którego ma zostać obliczony arcus cosinus (arcus cosinus).

## <a name="return-value"></a>Wartość zwracana

Funkcja **Acos** zwraca arcus cosinus *x* z zakresu od 0 do π radianów.

Domyślnie, jeśli *x* jest mniejsza niż-1 lub większa niż 1, **Acos** zwraca nieokreślony czas.

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|± ∞|Nieprawidłowy|_DOMAIN|
|QNAN, IND|brak|_DOMAIN|
|&#124;x&#124;>1|Nieprawidłowy|_DOMAIN|

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **Acos** , które pobierają i zwracają **`float`** **`long double`** typy. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **Acos** zawsze przyjmuje i zwraca **`double`** .

Jeśli używasz \<tgmath.h> `acos()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**Acos**, **acosf —**, **acosl**|\<math.h>|\<errno.h>|
|**Acos ()** — makro | \<tgmath.h> ||

## <a name="example"></a>Przykład

Ten program prosi o wartość z zakresu od 1 do 1. Wartości wejściowe spoza tego zakresu powodują generowanie `_DOMAIN` komunikatów o błędach. W przypadku wprowadzenia prawidłowej wartości, program drukuje arcus sinus i arcus cosinus tej wartości.

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

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)
