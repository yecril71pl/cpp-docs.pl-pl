---
title: "floorf — piętro, floorl — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- floorf
- floorl
- floor
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
- floor
- floorl
- _floorl
- floorf
dev_langs: C++
helpviewer_keywords:
- floor function
- floorf function
- calculating floors of values
- floorl function
ms.assetid: e9955f70-d659-414f-8050-132e13c8ff36
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a3bad88cdfbc9ee589a695de5da5f3bf722ace56
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="floor-floorf-floorl"></a>floor, floorf, floorl
Oblicza Zaokrąglenie w dół o wartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
double floor(  
   double x  
);  
float floor(  
   float x   
); // C++ only  
long double floor(  
   long double x  
); // C++ only  
float floorf(  
   float x  
);  
long double floorl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Wartość zmiennoprzecinkowa.  
  
## <a name="return-value"></a>Wartość zwracana  
 `floor` Zwracają wartość zmiennoprzecinkowa, która reprezentuje największa liczba całkowita, która jest mniejsza lub równa `x`. Nie ma żadnych zwracany błąd.  
  
|Dane wejściowe|Wyjątek SEH|Matherr — wyjątek|  
|-----------|-------------------|-----------------------|  
|GRANICACH QNAN, IND|brak|_DOMAIN —|  
  
 `floor`zawiera implementację, która używa Streaming SIMD Extensions 2 (SSE2). Aby uzyskać informacje i ograniczenia dotyczące korzystania z implementacji SSE2, zobacz [_set_sse2_enable —](../../c-runtime-library/reference/set-sse2-enable.md).  
  
## <a name="remarks"></a>Uwagi  
 C++ pozwala przeładowanie, dlatego można wywoływać przeciążenia `floor` który przyjmować i zwracać `float` i `long double` wartości. W programie C `floor` zawsze przyjmuje i zwraca `double`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`floor`, `floorf`, `floorl`|\<Math.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_floor.c  
// This example displays the largest integers  
// less than or equal to the floating-point values 2.8  
// and -2.8. It then shows the smallest integers greater  
// than or equal to 2.8 and -2.8.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double y;  
  
   y = floor( 2.8 );  
   printf( "The floor of 2.8 is %f\n", y );  
   y = floor( -2.8 );  
   printf( "The floor of -2.8 is %f\n", y );  
  
   y = ceil( 2.8 );  
   printf( "The ceil of 2.8 is %f\n", y );  
   y = ceil( -2.8 );  
   printf( "The ceil of -2.8 is %f\n", y );  
}  
```  
  
```Output  
The floor of 2.8 is 2.000000  
The floor of -2.8 is -3.000000  
The ceil of 2.8 is 3.000000  
The ceil of -2.8 is -2.000000  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [ceil ceilf —, ceill —](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [ROUND, roundf — roundl —](../../c-runtime-library/reference/round-roundf-roundl.md)   
 [fmod, fmodf](../../c-runtime-library/reference/fmod-fmodf.md)