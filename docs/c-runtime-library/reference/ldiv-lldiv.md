---
title: "ldiv —, lldiv — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ldiv
- lldiv
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ldiv
- lldiv
dev_langs: C++
helpviewer_keywords:
- ldiv function
- lldiv function
- quotients, computing
- computing remainders
- remainder computing
- computing quotients
ms.assetid: 68ab5d83-27a4-479c-9d52-d055eb139eca
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0443ce4ec90a9c6aef8fb07854200341cc369cb2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ldiv-lldiv"></a>ldiv, lldiv
Oblicza iloraz i pozostałej części dwie liczb całkowitych jako jedna operacja.  
  
## <a name="syntax"></a>Składnia  
  
```  
ldiv_t ldiv(  
   long numer,  
   long denom   
);  
lldiv_t lldiv(  
   long long numer,  
   long long denom   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `numer`  
 Licznik.  
  
 `denom`  
 Denominator.  
  
## <a name="return-value"></a>Wartość zwracana  
 `ldiv`Zwraca struktura typu [ldiv_t —](../../c-runtime-library/standard-types.md) który obejmuje zarówno iloraz, a reszta. `lldiv`Zwraca struktura typu [lldiv_t](../../c-runtime-library/standard-types.md) który obejmuje zarówno iloraz, a reszta.  
  
## <a name="remarks"></a>Uwagi  
 `ldiv` i `lldiv` funkcji dzielenia `numer` przez `denom`i tym samym obliczeniowe iloraz i pozostałej. Znak iloraz jest taka sama jak iloraz matematycznych. Wartość bezwzględna iloraz jest największa liczba całkowita, która jest mniejsza niż wartość bezwzględną liczby iloraz matematycznych. Jeżeli dzielnik wynosi 0, program zakończy się z komunikatem o błędzie. `ldiv`i `lldiv` są takie same jak `div`, z wyjątkiem tego, że argumenty `ldiv` i elementy członkowskie struktury zwracane są wszystkie typu `long`i argumenty `lldiv` i elementy członkowskie struktury zwracane są typu `long long`.  
  
 `ldiv_t` i `lldiv_t` struktury są zdefiniowane w \<stdlib.h >.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`ldiv`, `lldiv`|\<stdlib.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_ldiv.c  
  
#include <stdlib.h>  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   long x = 5149627, y = 234879;  
   ldiv_t div_result;  
  
   div_result = ldiv( x, y );  
   printf( "For %ld / %ld, the quotient is ", x, y );  
   printf( "%ld, and the remainder is %ld\n",   
            div_result.quot, div_result.rem );  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
For 5149627 / 234879, the quotient is 21, and the remainder is 217168  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [DIV](../../c-runtime-library/reference/div.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)