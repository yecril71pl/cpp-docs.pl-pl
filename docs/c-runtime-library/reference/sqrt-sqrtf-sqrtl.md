---
title: "SQRT sqrtf —, sqrtl — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- sqrtl
- sqrtf
- sqrt
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
- sqrt
- sqrtf
- _sqrtl
dev_langs: C++
helpviewer_keywords:
- sqrtf function
- sqrt function
- sqrtl function
- _sqrtl function
- calculating square roots
- square roots, calculating
ms.assetid: 2ba9467b-f172-41dc-8f10-b86f68fa813c
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f711ca2a09126b6a2e914ab094f5f491a9998c41
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="sqrt-sqrtf-sqrtl"></a>SQRT sqrtf —, sqrtl —
Oblicza pierwiastek kwadratowy.  
  
## <a name="syntax"></a>Składnia  
  
```  
double sqrt(  
   double x   
);  
float sqrt(  
   float x   
);  // C++ only  
long double sqrt(  
   long double x  
);  // C++ only  
float sqrtf(  
   float x   
);  
long double sqrtl(  
   long double x   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Wartość zmiennoprzecinkowa nieujemną.  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `sqrt` które trwają `float` lub `long double` typów. W programie C `sqrt` zawsze przyjmuje i zwraca `double`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `sqrt` Zwracają pierwiastek kwadratowy liczby `x`. Domyślnie jeśli `x` jest ujemna, `sqrt` zwraca nieograniczonego NaN.  
  
|Dane wejściowe|Wyjątek SEH|`_matherr`Wyjątek|  
|-----------|-------------------|--------------------------|  
|GRANICACH QNAN, IND|brak|_DOMAIN —|  
|- ∞|brak|_DOMAIN —|  
|x < 0|brak|_DOMAIN —|  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`sqrt`, `sqrtf`, `sqrtl`|\<Math.h >|\<cmath >|  
  
 Aby uzyskać informacje dotyczące zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```C  
// crt_sqrt.c  
// This program calculates a square root.  
  
#include <math.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   double question = 45.35, answer;  
   answer = sqrt( question );  
   if( question < 0 )  
      printf( "Error: sqrt returns %f\n", answer );  
   else  
      printf( "The square root of %.2f is %.2f\n", question, answer );  
}  
```  
  
```Output  
The square root of 45.35 is 6.73  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [EXP, expf —, expl](../../c-runtime-library/reference/exp-expf.md)   
 [logf —, log10, log10f — w Dzienniku](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [Pow — powf —, powl —](../../c-runtime-library/reference/pow-powf-powl.md)   
 [_CIsqrt](../../c-runtime-library/cisqrt.md)