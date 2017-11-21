---
title: "ACOS acosf —, acosl — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- acos function
- acosl function
- acosf function
- trigonometric functions
- arccosine function
ms.assetid: 00b89c48-8faf-4824-aa95-fa4349a4975d
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ab09d3e189ea4c1990be25f2982a949d95a68359
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="acos-acosf-acosl"></a>acos, acosf, acosl
Oblicza cosinus.  
  
## <a name="syntax"></a>Składnia  
  
```  
double acos(   
   double x   
);  
float acos(  
   float x   
);   // C++ only  
long double acos(  
   long double x  
);   // C++ only  
float acosf(  
   float x   
);  
long double acosl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Wartości od -1 do 1, dla którego mają być obliczane cosinus (arcus cosinus).  
  
## <a name="return-value"></a>Wartość zwracana  
 `acos` Funkcja Zwraca arcus cosinus liczby `x` w zakresie od 0 do π radianów.  
  
 Domyślnie jeśli `x` jest mniejsza niż -1 lub większą niż 1, `acos` zwraca nieokreślony.  
  
|Dane wejściowe|Wyjątek SEH|Matherr — wyjątek|  
|-----------|-------------------|-----------------------|  
|± ∞|`INVALID`|`_DOMAIN`|  
|GRANICACH QNAN, IND|brak|`_DOMAIN`|  
|&#124; x &#124; > 1|`INVALID`|`_DOMAIN`|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `acos` który przyjmować i zwracać `float` i `long double` typów. W programie C `acos` zawsze przyjmuje i zwraca `double`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|----------------------|  
|`acos`, `acosf`, `acosl`|\<Math.h >|\<errno.h >|  
  
## <a name="example"></a>Przykład  
 Ten program monituje o podanie wartości z zakresu od -1 do 1. Wartości wejściowe poza tym zakresem utworzyć `_DOMAIN` komunikaty o błędach. W przypadku wprowadzenia jest prawidłową wartością program drukuje arcus sinus i cosinus tej wartości.  
  
```  
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
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [ASIN asinf —, asinl —](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [ATAN, atanf —, atanl —, atan2 atan2f —, atan2l —](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [COS, cosf —, cosl —, cosh, coshf — coshl —](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [_matherr —](../../c-runtime-library/reference/matherr.md)   
 [SIN, sinf —, sinl —, sinh sinhf —, sinhl —](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [TAN, tanf —, tanl —, tanh tanhf —, tanhl —](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)