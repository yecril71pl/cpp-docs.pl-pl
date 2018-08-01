---
title: Funkcje ACOS, acosf —, acosl — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- acosf
- acos
- acosl
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
- acos
- acosl
- acosf
- math/acosf
- math/acosl
dev_langs:
- C++
helpviewer_keywords:
- acos function
- acosl function
- acosf function
- trigonometric functions
- arccosine function
ms.assetid: 00b89c48-8faf-4824-aa95-fa4349a4975d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5384d4e97ebb4f3f6152278e916c02bb350090ea
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401941"
---
# <a name="acos-acosf-acosl"></a>acos, acosf, acosl

Oblicza arcus cosinus.

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

*x*  
Wartość od -1 do 1, dla którego ma zostać obliczona arcus cosinus (odwrotność funkcji cosinus).

## <a name="return-value"></a>Wartość zwracana

**Acos** funkcja Zwraca arcus cosinus *x* z zakresu od 0 do π wartość w radianach.

Domyślnie jeśli *x* jest mniejsza niż -1 lub większa niż 1, **acos** zwraca wartość nieokreśloną.

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|± ∞|NIEPRAWIDŁOWY|_DOMAIN|
|GRANICACH QNAN, ZNAJDŹ|brak|_DOMAIN|
|&#124;x&#124;>1|NIEPRAWIDŁOWY|_DOMAIN|

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na przeciążenie, można wywoływać przeciążenia **acos** przyjmujące i zwracające **float** i **długie** **double** typów. W programie C **acos** zawsze przyjmuje i zwraca **double**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**ACOS**, **acosf —**, **acosl —**|\<math.h>|\<errno.h>|

## <a name="example"></a>Przykład

Ten program wyświetli monit o wartości z zakresu od -1 do 1. Wartości wejściowe poza tym zakresem dają `_DOMAIN` komunikaty o błędach. W przypadku wprowadzenia jest prawidłową wartością program drukuje arcus sinus i cosinus tej wartości.

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

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)  
[asin, asinf, asinl](asin-asinf-asinl.md)  
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)  
[COS cosf —, cosl —](cos-cosf-cosl.md)  
[_matherr](matherr.md)  
[sin, sinf, sinl](sin-sinf-sinl.md)  
[tan, tanf, tanl](tan-tanf-tanl.md)  