---
title: "cbrt —, cbrtf —, cbrtl | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- cbrt
- cbrtf
- cbrtl
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
- cbrtl
- cbrt
- cbrtf
dev_langs: C++
helpviewer_keywords:
- cbrtl function
- cbrtf function
- cbrt function
ms.assetid: ab51d916-3db2-4beb-b46a-28b4062cd33f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 578ff897f980a31efead2777835aa3461438d524
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cbrt-cbrtf-cbrtl"></a>cbrt, cbrtf, cbrtl
Oblicza pierwiastek modułu.  
  
## <a name="syntax"></a>Składnia  
  
```  
double cbrt(  
   double x   
);  
float cbrt(  
   float x   
);  // C++ only  
long double cbrt(  
   long double x  
);  // C++ only  
float cbrtf(  
   float x   
);  
long double cbrtl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Wartość zmiennoprzecinkowa  
  
## <a name="return-value"></a>Wartość zwracana  
 `cbrt` Zwracają pierwiastek modułu z `x`.  
  
|Dane wejściowe|Wyjątek SEH|`_matherr`Wyjątek|  
|-----------|-------------------|--------------------------|  
|∞; GRANICACH, QNAN, IND|brak|brak|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `cbrt` które trwają `float` lub `long double` typów. W programie C `cbrt` zawsze przyjmuje i zwraca `double`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`cbrt`, `cbrtf`, `cbrtl`|\<Math.h >|\<cmath >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```C  
// crt_cbrt.c  
// Compile using: cl /W4 crt_cbrt.c  
// This program calculates a cube root.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double question = -64.64;  
   double answer;  
  
   answer = cbrt(question);  
   printf("The cube root of %.2f is %.6f\n", question, answer);  
}  
```  
  
```Output  
The cube root of -64.64 is -4.013289  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [EXP, expf —, expl](../../c-runtime-library/reference/exp-expf.md)   
 [logf —, log10, log10f — w Dzienniku](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [Pow — powf —, powl —](../../c-runtime-library/reference/pow-powf-powl.md)