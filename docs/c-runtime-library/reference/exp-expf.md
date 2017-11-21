---
title: "EXP, expf —, expl | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- expf
- expl
- exp
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
- _expl
- expf
- expl
- exp
dev_langs: C++
helpviewer_keywords:
- exponential calculations
- expf function
- expl function
- calculating exponentials
- exp function
ms.assetid: 7070016d-1143-407e-9e9a-6b059bb88867
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4b63b99f7451d2fbb1a0e4137469a0c4f5b01046
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="exp-expf-expl"></a>EXP, expf —, expl
Oblicza wykładniczej.  
  
## <a name="syntax"></a>Składnia  
  
```  
double exp(   
   double x  
);  
float exp(  
   float x  
);  // C++ only  
long double exp(  
   long double x  
);  // C++ only  
float expf(   
   float x  
);  
long double expl(  
   long double x  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `x`  
 Zmiennoprzecinkowe do wartości exponentiate podstawa logarytmu naturalnego *e* przez.  
  
## <a name="return-value"></a>Wartość zwracana  
 `exp` Zwracają wykładniczej wartość parametru zmiennoprzecinkowego *x*, jeśli to się powiedzie. Wynik jest *e*<sup>*x*</sup>, gdzie *e* jest podstawą logarytmu naturalnego. Przepełnienie, funkcja zwraca INF (nieskończoności) i niedopełnienie `exp` zwraca wartość 0.  
  
|Dane wejściowe|Wyjątek SEH|Matherr — wyjątek|  
|-----------|-------------------|-----------------------|  
|Quiet NaN granicach, nieokreślone|Brak|_DOMAIN —|  
|Infinity granicach|NIEPRAWIDŁOWY|_DOMAIN —|  
|x ≥ 7.097827e + 002|NIEDOKŁADNY + PRZEPEŁNIENIA|PRZEPEŁNIENIE|  
|X ≤-7.083964e + 002|NIEDOPEŁNIENIE NIEDOKŁADNYMI +|NIEDOPEŁNIENIE|  
  
 `exp` Funkcja ma implementację, która używa Streaming SIMD Extensions 2 (SSE2). Zobacz [_set_sse2_enable —](../../c-runtime-library/reference/set-sse2-enable.md) informacje i ograniczenia dotyczące używania implementacji SSE2.  
  
## <a name="remarks"></a>Uwagi  
 C++ pozwala przeładowanie, dlatego można wywoływać przeciążenia `exp` które trwają **float** lub **podwójnej długości** argumentu. W programie C `exp` zawsze przyjmuje i zwraca **podwójne**.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek C|Wymagany nagłówek C++|  
|--------------|---------------------|---|  
|`exp`, `expf`|\<Math.h >|\<cmath > lub \<math.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_exp.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.302585093, y;  
  
   y = exp( x );  
   printf( "exp( %f ) = %f\n", x, y );  
}  
```  
  
```Output  
exp( 2.302585 ) = 10.000000  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [logf —, log10, log10f — w Dzienniku](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [_CIexp](../../c-runtime-library/ciexp.md)