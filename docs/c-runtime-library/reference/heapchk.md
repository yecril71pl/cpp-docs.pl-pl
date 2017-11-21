---
title: "_heapchk — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _heapchk
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _heapchk
- heapchk
dev_langs: C++
helpviewer_keywords:
- debugging [CRT], heap-related problems
- consistency checking of heaps
- heapchk function
- heaps, checking consistency
- _heapchk function
ms.assetid: 859619a5-1e35-4f02-9e09-11d9fa266ec0
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9fcbafbb98385878dbc84f300e8d2bf0dac581c7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="heapchk"></a>_heapchk
Uruchamia sprawdzanie spójności na stosie.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _heapchk( void );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 `_heapchk`Zwraca jedną z następujących manifestu stałe całkowite zdefiniowane w Malloc.h.  
  
 `_HEAPBADBEGIN`  
 Informacje o nagłówku początkowy jest nieprawidłowy lub nie można odnaleźć.  
  
 `_HEAPBADNODE`  
 Znaleziono nieprawidłowy węzeł lub sterty jest uszkodzony.  
  
 `_HEAPBADPTR`  
 Wskaźnik do sterty jest nieprawidłowy.  
  
 `_HEAPEMPTY`  
 Stos nie został zainicjowany.  
  
 `_HEAPOK`  
 Sterty wydaje się być zgodne.  
  
 Ponadto, jeśli wystąpi błąd `_heapchk` ustawia `errno` do `ENOSYS`.  
  
## <a name="remarks"></a>Uwagi  
 `_heapchk` Funkcja pomaga debugowanie problemy związane ze stosem przez sprawdzanie spójności minimalnego sterty. Jeśli system operacyjny nie obsługuje `_heapchk`(na przykład Windows 98), funkcja zwraca `_HEAPOK` i ustawia `errno` do `ENOSYS`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_heapchk`|\<malloc.h >|\<errno.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_heapchk.c  
// This program checks the heap for  
// consistency and prints an appropriate message.  
  
#include <malloc.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int  heapstatus;  
   char *buffer;  
  
   // Allocate and deallocate some memory  
   if( (buffer = (char *)malloc( 100 )) != NULL )  
      free( buffer );  
  
   // Check heap status  
   heapstatus = _heapchk();  
   switch( heapstatus )  
   {  
   case _HEAPOK:  
      printf(" OK - heap is fine\n" );  
      break;  
   case _HEAPEMPTY:  
      printf(" OK - heap is empty\n" );  
      break;  
   case _HEAPBADBEGIN:  
      printf( "ERROR - bad start of heap\n" );  
      break;  
   case _HEAPBADNODE:  
      printf( "ERROR - bad node in heap\n" );  
      break;  
   }  
}  
```  
  
```Output  
OK - heap is fine  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Alokacja pamięci](../../c-runtime-library/memory-allocation.md)   
 [_heapadd —](../../c-runtime-library/heapadd.md)   
 [_heapmin —](../../c-runtime-library/reference/heapmin.md)   
 [_heapset —](../../c-runtime-library/heapset.md)   
 [_heapwalk —](../../c-runtime-library/reference/heapwalk.md)