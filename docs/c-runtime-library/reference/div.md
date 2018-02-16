---
title: DIV | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- div
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
- div
dev_langs:
- C++
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2090ca5e08af74854177f02d6313d6c1304ed2c6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="div"></a>div
Oblicza iloraz i pozostałej części dwóch wartości całkowite.  
  
## <a name="syntax"></a>Składnia  
  
```  
div_t div(   
   int numer,  
   int denom   
);  
ldiv_t div(  
   long numer,  
   long denom  
); /* C++ only */   
lldiv_t div(  
   long long numer,  
   long long denom  
); /* C++ only */  
```  
  
#### <a name="parameters"></a>Parametry  
 `numer`  
 Licznik.  
  
 `denom`  
 Denominator.  
  
## <a name="return-value"></a>Wartość zwracana  
 `div` wywoływane przy użyciu argumentów typu `int` zwraca struktura typu `div_t`, która obejmuje iloraz, a reszta. Wartość zwracana przeciążenia z argumentami typu `long` jest `ldiv_t`. Zarówno `div_t` i `ldiv_t` są zdefiniowane w STDLIB. H.  
  
## <a name="remarks"></a>Uwagi  
 `div` Funkcji bez reszty `numer` przez `denom` i tym samym oblicza iloraz, a reszta. [Div_t —](../../c-runtime-library/standard-types.md) struktura zawiera iloraz, `int quot`, a reszta, `int rem`. Znak iloraz jest taka sama jak iloraz matematycznych. Największa liczba całkowita, która jest mniejsza niż wartość bezwzględną liczby matematyczne iloraz ma jego wartość bezwzględna. Jeżeli dzielnik wynosi 0, program zakończy się z komunikatem o błędzie.  
  
 Przeciążenia, które przyjmują argumentów typu `long` lub `long long` są dostępne tylko dla kodu języka C++. Zwracany typ [ldiv_t —](../../c-runtime-library/standard-types.md) zawiera członków `long quot` i `long rem`, a zwracanym typem [lldiv_t](../../c-runtime-library/standard-types.md) zawiera członków `long long quot` i `long long rem`, które mają takie same znaczenie jako członków `div_t`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`div`|\<stdlib.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_div.c  
// arguments: 876 13  
  
// This example takes two integers as command-line  
// arguments and displays the results of the integer  
// division. This program accepts two arguments on the  
// command line following the program name, then calls  
// div to divide the first argument by the second.  
// Finally, it prints the structure members quot and rem.  
//  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <math.h>  
  
int main( int argc, char *argv[] )  
{  
   int x,y;  
   div_t div_result;  
  
   x = atoi( argv[1] );  
   y = atoi( argv[2] );  
  
   printf( "x is %d, y is %d\n", x, y );  
   div_result = div( x, y );  
   printf( "The quotient is %d, and the remainder is %d\n",  
           div_result.quot, div_result.rem );  
}  
```  
  
```Output  
x is 876, y is 13  
The quotient is 67, and the remainder is 5  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [ldiv —, lldiv —](../../c-runtime-library/reference/ldiv-lldiv.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)