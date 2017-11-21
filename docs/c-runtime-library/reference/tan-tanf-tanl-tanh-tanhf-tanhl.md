---
title: "TAN, tanf —, tanl —, tanh tanhf —, tanhl — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- tanhf
- tanh
- tan
- tanhl
- tanf
- tanl
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
- tanh
- tan
- _tanl
- tanl
- _tanhl
- tanf
- tanhf
- tanhl
dev_langs: C++
helpviewer_keywords:
- tanl function
- tanhl function
- _tanl function
- _tanhl function
- tan function
- calculating tangents
- tangent
- tanh function
- tanhf function
- tanf function
- trigonometric functions
- hyperbolic functions
ms.assetid: 36cc0ce8-9c80-4653-b354-ddb3b378b6bd
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c0f094272514966655e8ecfe45a3f35e179db333
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="tan-tanf-tanl-tanh-tanhf-tanhl"></a>TAN, tanf —, tanl —, tanh tanhf —, tanhl —
Oblicza tangens (`tan`, `tanf`, lub `tanl`), lub tangens hiperboliczny (`tanh`, `tanhf`, lub `tanhl`).  
  
## <a name="syntax"></a>Składnia  
  
```  
double tan(  
   double x   
);  
float tan(  
   float x   
);  // C++ only  
long double tan(  
   long double x  
);  // C++ only  
float tanf(  
   float x   
);  
long double tanl(  
   long double x  
);  
double tanh(  
   double x   
);  
float tanh(  
   float x   
);  // C++ only  
long double tanh(  
   long double x  
);  // C++ only  
float tanhf(  
   float x   
);  
long double tanhl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Kąt w radianach.  
  
## <a name="return-value"></a>Wartość zwracana  
 `tan` Funkcje tangensa `x`. Jeśli `x` jest większa niż lub równa 263 lub mniejsza niż lub równa -263 dojdzie do utraty znaczenie w wyniku.  
  
 `tanh` Zwracają tangens hiperboliczny liczby `x`. Nie ma żadnych zwracany błąd.  
  
|Dane wejściowe|Wyjątek SEH|`Matherr`Wyjątek|  
|-----------|-------------------|-------------------------|  
|GRANICACH QNAN, IND|brak|_DOMAIN —|  
|± ∞  (`tan`, `tanf`)|`INVALID`|_DOMAIN —|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `tan` i `tanh` który przyjmować i zwracać `float` lub `long double` wartości. W programie C `tan` i `tanh` zawsze przyjmować i zwracać `double`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`tan`, `tanf`, `tanl`, `tanh`, `tanhf`, `tanhl`|\<Math.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_tan.c  
// This program displays the tangent of pi / 4  
// and the hyperbolic tangent of the result.  
//  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = tan( pi / 4 );  
   y = tanh( x );  
   printf( "tan( %f ) = %f\n", pi/4, x );  
   printf( "tanh( %f ) = %f\n", x, y );  
}  
```  
  
```Output  
tan( 0.785398 ) = 1.000000  
tanh( 1.000000 ) = 0.761594  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [ACOS acosf —, acosl —](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [ASIN asinf —, asinl —](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [ATAN, atanf —, atanl —, atan2 atan2f —, atan2l —](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [COS, cosf —, cosl —, cosh, coshf — coshl —](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [SIN, sinf —, sinl —, sinh sinhf —, sinhl —](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [_CItan](../../c-runtime-library/citan.md)