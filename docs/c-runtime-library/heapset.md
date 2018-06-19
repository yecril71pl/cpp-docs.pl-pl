---
title: _heapset — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _heapset
apilocation:
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _heapset
- heapset
dev_langs:
- C++
helpviewer_keywords:
- checking heap
- heapset function
- heaps, checking
- debugging [CRT], heap-related problems
- _heapset function
ms.assetid: 9667eeb0-55bc-4c19-af5f-d1fd0a142b3c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c45c4cc3e6e6ffe23378ce0b4f26383369e92058
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391590"
---
# <a name="heapset"></a>_heapset
Sprawdza stosów minimalnego spójności i ustawia wolnego wpisy na określoną wartość.  
  
> [!IMPORTANT]
>  Ta funkcja jest przestarzała. Począwszy od programu Visual Studio 2015, nie jest dostępna w CRT.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _heapset(   
   unsigned int fill   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fill`  
 Należy podać znak.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_heapset` Zwraca jedną z następujących manifestu stałe całkowite zdefiniowane w Malloc.h.  
  
 `_HEAPBADBEGIN`  
 Informacje o nagłówku początkowej nieprawidłowy lub nie została znaleziona.  
  
 `_HEAPBADNODE`  
 Stercie odnaleziono uszkodzony lub nieprawidłowy węzeł.  
  
 `_HEAPEMPTY`  
 Stos nie jest zainicjowany.  
  
 `_HEAPOK`  
 Sterty wydaje się być zgodne.  
  
 Ponadto, jeśli wystąpi błąd `_heapset` ustawia `errno` do `ENOSYS`.  
  
## <a name="remarks"></a>Uwagi  
 `_heapset` Funkcja wykazuje lokalizacje wolnej pamięci lub węzłów, które zostały zastąpione przypadkowo.  
  
 `_heapset` sprawdza, czy minimalny spójności na stosie, a następnie ustawia każdego bajtu wpisów wolnego sterty `fill` wartość. Ta wartość znane zawiera lokalizacje pamięci sterty zawierać wolnych węzłów i które zawierają dane przypadkowo napisanych zwolnionych pamięci. Jeśli system operacyjny nie obsługuje `_heapset`(na przykład Windows 98), funkcja zwraca `_HEAPOK` i ustawia `errno` do `ENOSYS`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_heapset`|\<malloc.h>|\<errno.h>|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_heapset.c  
// This program checks the heap and  
// fills in free entries with the character 'Z'.  
  
#include <malloc.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int heapstatus;  
   char *buffer;  
  
   if( (buffer = malloc( 1 )) == NULL ) // Make sure heap is   
      exit( 0 );                        //    initialized       
   heapstatus = _heapset( 'Z' );        // Fill in free entries   
   switch( heapstatus )  
   {  
   case _HEAPOK:  
      printf( "OK - heap is fine\n" );  
      break;  
   case _HEAPEMPTY:  
      printf( "OK - heap is empty\n" );  
      break;  
   case _HEAPBADBEGIN:  
      printf( "ERROR - bad start of heap\n" );  
      break;  
   case _HEAPBADNODE:  
      printf( "ERROR - bad node in heap\n" );  
      break;  
   }  
   free( buffer );  
}  
```  
  
```Output  
OK - heap is fine  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Alokacja pamięci](../c-runtime-library/memory-allocation.md)   
 [_heapadd —](../c-runtime-library/heapadd.md)   
 [_heapchk](../c-runtime-library/reference/heapchk.md)   
 [_heapmin —](../c-runtime-library/reference/heapmin.md)   
 [_heapwalk](../c-runtime-library/reference/heapwalk.md)