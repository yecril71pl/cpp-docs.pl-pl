---
title: "ACOSH acoshf —, acoshl | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- acoshf
- acosh
- acoshl
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
- acosh
- acoshf
- acoshl
- math/acosh
- math/acoshf
- math/acoshl
dev_langs: C++
helpviewer_keywords:
- acoshf function
- acosh function
- acoshl function
ms.assetid: 6985c4d7-9e2a-44ce-9a9b-5a43015f15f7
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 44872bc2ad2ef2be8e9a91403852574c9047a051
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="acosh-acoshf-acoshl"></a>acosh, acoshf, acoshl
Oblicza cosinus hiperboliczny.  
  
## <a name="syntax"></a>Składnia  
  
```  
double acosh(  
   double x   
);  
float acosh(  
   float x   
);  // C++ only  
long double acosh(  
   long double x  
);  // C++ only  
float acoshf(  
   float x   
);  
long double acoshl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Wartość zmiennoprzecinkowa.  
  
## <a name="return-value"></a>Wartość zwracana  
 `acosh` Hyberbolic odwrotny cosinus (arcus cosinus hiperboliczny) zwracają `x`. Te funkcje są prawidłowe w domenie `x` ≥ 1. Jeśli `x` jest mniejszy niż 1 `errno` ustawiono `EDOM` i quiet NaN. Jeśli `x` jest NaN quiet — nieokreślony, lub nieskończoności, jest zwracana przez tę samą wartość.  
  
|Dane wejściowe|Wyjątek SEH|`_matherr`Wyjątek|  
|-----------|-------------------|--------------------------|  
|INF QNAN, IND GRANICACH|brak|brak|  
|x < 1|brak|brak|  
  
## <a name="remarks"></a>Uwagi  
 Korzystając z języka C++, można wywoływać przeciążenia `acosh` który przyjmować i zwracać `float` lub `long double` wartości. W programie C `acosh` zawsze przyjmuje i zwraca `double`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`acosh`, `acoshf`, `acoshl`|\<Math.h >|\<cmath >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```C  
// crt_acosh.c  
// Compile by using: cl /W4 crt_acosh.c  
// This program displays the hyperbolic cosine of pi / 4  
// and the arc hyperbolic cosine of the result.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = cosh( pi / 4 );  
   y = acosh( x );  
   printf( "cosh( %f ) = %f\n", pi/4, x );  
   printf( "acosh( %f ) = %f\n", x, y );  
}  
```  
  
```Output  
cosh( 0.785398 ) = 1.324609  
acosh( 1.324609 ) = 0.785398  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [COS, cosf —, cosl —, cosh, coshf — coshl —](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [SIN, sinf —, sinl —, sinh sinhf —, sinhl —](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [ASINH asinhf —, asinhl](../../c-runtime-library/reference/asinh-asinhf-asinhl.md)   
 [TAN, tanf —, tanl —, tanh tanhf —, tanhl —](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [ATANH atanhf —, atanhl —](../../c-runtime-library/reference/atanh-atanhf-atanhl.md)   
 [_CItan](../../c-runtime-library/citan.md)