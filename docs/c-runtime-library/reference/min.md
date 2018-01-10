---
title: "__min — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: __min
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
apitype: DLLExport
f1_keywords:
- __min
- min
- _min
dev_langs: C++
helpviewer_keywords:
- __min macro
- min macro
- minimum macro
- _min macro
ms.assetid: 2037f26c-b48a-4a69-8870-22519f052a3c
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8504736d10c02a58ba456e8dd501ca09084c9529
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="min"></a>__min
Zwraca mniejszy z dwóch wartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
type __min(  
   type a,  
   type b   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 Wszystkie dane typu liczbowego.  
  
 `a, b`  
 Wartości typu liczbowego do porównania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Mniejszy z dwóch argumentów.  
  
## <a name="remarks"></a>Uwagi  
 `__min` Makro porównuje dwie wartości i zwraca wartość mniejszy. Argumenty mogą być dowolnego liczbowego typu danych, podpisu lub bez znaku. Zarówno argumentów i zwracana wartość musi być tego samego typu danych.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`__min`|\<stdlib.h >|  
  
## <a name="example"></a>Przykład  
  
```  
// crt_minmax.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int a = 10;  
   int b = 21;  
  
   printf( "The larger of %d and %d is %d\n",  a, b, __max( a, b ) );  
   printf( "The smaller of %d and %d is %d\n", a, b, __min( a, b ) );  
}  
```  
  
```Output  
The larger of 10 and 21 is 21  
The smaller of 10 and 21 is 10  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [__max](../../c-runtime-library/reference/max.md)