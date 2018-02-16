---
title: "remainderf — pozostałe, remainderl | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- remainderl
- remainder
- remainderf
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
- remainderf
- remainder
- remainderl
dev_langs:
- C++
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2b7a5d55fd079f03338a6860755a783ba4d82b76
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="remainder-remainderf-remainderl"></a>remainder, remainderf, remainderl
Oblicza w pozostałej części iloraz dwóch wartości zmiennoprzecinkowych zaokrąglona do najbliższej wartości całkowite.  
  
## <a name="syntax"></a>Składnia  
  
```  
double remainder(   
   double numer,  
   double denom  
);  
float remainder(   
   float numer,  
   float denom  
); /* C++ only */  
long double remainder(   
   long double numer,  
   long double denom  
); /* C++ only */  
float remainderf(   
   float numer,  
   float denom  
);  
long double remainderl(   
   long double numer,  
   long double denom  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `numer`  
 Licznik.  
  
 `denom`  
 Denominator.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zmiennoprzecinkowe pozostałej części `x`  /  `y`. Jeśli wartość `y` jest 0.0, `remainder` zwraca quiet NaN. Informacji o reprezentację quiet NaN przez `printf` rodziny, zobacz [printf, _printf_l —, wprintf, _wprintf_l —](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md).  
  
## <a name="remarks"></a>Uwagi  
 `remainder` Funkcja oblicza resztę zmiennoprzecinkowe `r` z `x`  /  `y` tak, aby `x`  =  `n`  *  `y`  +  `r`, gdzie `n` jest liczbą całkowitą w wartości do najbliższej `x`  /  `y` i `n` jest nawet przy każdym &#124; `n`  -  `x`  /  `y` &#124; = 1/2. Gdy `r` = 0, `r` ma ten sam znak co `x`.  
  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `remainder` który przyjmować i zwracać `float` lub `long double` wartości. W programie C `remainder` zawsze przyjmuje dwa symulacyjnych i zwraca wartość o podwójnej precyzji.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`remainder`, `remainderf`, `remainderl`|\<math.h>|  
  
 Aby uzyskać informacje dotyczące zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```C  
// crt_remainder.c  
// This program displays a floating-point remainder.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double w = -10.0, x = 3.0, z;  
  
   z = remainder(w, x);  
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);  
}  
```  
  
```Output  
The remainder of -10.00 / 3.00 is -1.000000  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [ldiv —, lldiv —](../../c-runtime-library/reference/ldiv-lldiv.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)   
 [fmod —, fmodf —](../../c-runtime-library/reference/fmod-fmodf.md)   
 [remquo, remquof, remquol](../../c-runtime-library/reference/remquo-remquof-remquol.md)