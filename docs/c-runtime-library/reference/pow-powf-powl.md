---
title: "Pow, powf — powl — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- powl
- pow
- powf
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
- powl
- pow
- _powl
- powf
dev_langs:
- C++
helpviewer_keywords:
- exponential calculations
- powl function
- _powl function
- exponentiation
- powers, calculating
- calculating exponentials
- powf function
- pow function
ms.assetid: e75c33ed-2e59-48b1-be40-81da917324f1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 09b618e557fffadd3bfffb431fc7e89458c4f420
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="pow-powf-powl"></a>pow, powf, powl
Oblicza `x` podniesionej do potęgi równej `y`.  
  
## <a name="syntax"></a>Składnia  
  
```  
double pow(  
   double x,  
   double y   
);  
double pow(  
   double x,  
   int y  
);  // C++ only  
float pow(  
   float x,  
   float y   
);  // C++ only  
float pow(  
   float x,  
   int y  
);  // C++ only  
long double pow(  
   long double x,  
   long double y  
);  // C++ only  
long double pow(  
   long double x,  
   int y  
);  // C++ only  
float powf(  
   float x,  
   float y   
);  
long double powl(  
   long double x,  
   long double y  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Podstawa.  
  
 `y`  
 Wykładnik.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość `x` <sup>y</sup>. Żaden komunikat o błędzie jest wydrukowany przepełnienie lub niedomiar.  
  
|Wartości x i y|Wartość zwracana pow|  
|-----------------------|-------------------------|  
|`x` \< > 0 i `y` = 0,0|1|  
|`x` = 0,0 i `y` = 0,0|1|  
|`x` = 0,0 i `y` < 0|INF|  
  
## <a name="remarks"></a>Uwagi  
 `pow` nie rozpoznaje wartości całkowitych wartości zmiennoprzecinkowych większej niż 2<sup>64</sup> (na przykład `1.0E100`).  
  
 `pow` zawiera implementację, która używa Streaming SIMD Extensions 2 (SSE2). Aby uzyskać informacje i ograniczenia dotyczące korzystania z implementacji SSE2, zobacz [_set_sse2_enable —](../../c-runtime-library/reference/set-sse2-enable.md).  
  
 Ponieważ C++ pozwala przeładowanie, można wywołać żadnego z różnych przeciążeń `pow`. W programie C `pow` zawsze ma dwie wartości double i zwraca wartość typu double.  
  
 `pow(int, int)` Przeciążenia nie jest już dostępny. Jeśli używasz tego przeciążenia, kompilator może emitować C2668. Aby uniknąć tego problemu, należy rzutować pierwszy parametr `double`, `float`, lub `long double`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`pow`, `powf`, `powl`|\<math.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_pow.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.0, y = 3.0, z;  
  
   z = pow( x, y );  
   printf( "%.1f to the power of %.1f is %.1f\n", x, y, z );  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
2.0 to the power of 3.0 is 8.0  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [exp, expf, expl](../../c-runtime-library/reference/exp-expf.md)   
 [log, logf, log10, log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [sqrt, sqrtf, sqrtl](../../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)   
 [_CIpow](../../c-runtime-library/cipow.md)