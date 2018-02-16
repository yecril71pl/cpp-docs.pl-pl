---
title: "calloc — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- calloc
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
- calloc
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f106ec1cd879282d557c492e4f19cdd01480575
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="calloc"></a>calloc
Przydziela tablicy w pamięci z elementami równe 0.  
  
## <a name="syntax"></a>Składnia  
  
```  
void *calloc(   
   size_t num,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `num`  
 Liczba elementów.  
  
 `size`  
 Długość w bajtach każdego elementu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `calloc` Zwraca wskaźnik do przydzielonego miejsca. Miejsca do magazynowania wskazywanej przez wartość zwracana jest gwarantowana odpowiednio dopasowany do przechowywania obiekty dowolnego typu. Aby otrzymywać wskaźnik do typu innego niż `void`, użyj typu rzutowania wartości zwracanej.  
  
## <a name="remarks"></a>Uwagi  
 `calloc` Funkcja przydziela miejsce do magazynowania dla tablicy `num` o długości elementów `size` bajtów. Każdy element jest ustawiana na 0.  
  
 `calloc` Ustawia `errno` do `ENOMEM` czy alokacja pamięci nie powiedzie się, czy ilość pamięci żądana przekracza `_HEAP_MAXREQ`. Aby uzyskać informacje na ten temat oraz innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 `calloc` wywołania `malloc` do użycia dla języka C++ [_set_new_mode —](../../c-runtime-library/reference/set-new-mode.md) funkcji, aby ustawić nowy tryb obsługi. Nowy tryb obsługi wskazuje, czy w przypadku awarii, `malloc` jest wywołanie nowe procedury obsługi zgodnie z ustawieniami [_set_new_handler —](../../c-runtime-library/reference/set-new-handler.md). Domyślnie `malloc` nie wywołuje nowe procedury obsługi nie można przydzielić pamięci. Można zastąpić to zachowanie domyślne, aby, gdy `calloc` nie może przydzielić pamięci, `malloc` wywołuje nowe procedury obsługi tak samo jak robi `new` operator nie w przypadku niepowodzenia tego samego powodu. Aby zastąpić domyślną, należy wywołać  
  
```  
_set_new_mode(1)  
```  
  
 wcześniej w program lub Połącz z biblioteką NEWMODE. OBJ (zobacz [opcje łącza](../../c-runtime-library/link-options.md)).  
  
 Gdy aplikacja jest połączony z wersją debugowania biblioteki wykonawcze języka C, `calloc` jest rozpoznawana jako [_calloc_dbg —](../../c-runtime-library/reference/calloc-dbg.md). Aby uzyskać więcej informacji dotyczących sposobu zarządzania infrastrukturą sterty podczas debugowania procesu, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 `calloc` jest oznaczony jako `__declspec(noalias)` i `__declspec(restrict)`, co oznacza, że funkcja jest gwarantowana nie do modyfikowania zmiennych globalnych i czy zwrócony wskaźnik nie jest używane z aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`calloc`|\<stdlib.h > i \<malloc.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_calloc.c  
// This program uses calloc to allocate space for  
// 40 long integers. It initializes each element to zero.  
  
#include <stdio.h>  
#include <malloc.h>  
  
int main( void )  
{  
   long *buffer;  
  
   buffer = (long *)calloc( 40, sizeof( long ) );  
   if( buffer != NULL )  
      printf( "Allocated 40 long integers\n" );  
   else  
      printf( "Can't allocate memory\n" );  
   free( buffer );  
}  
```  
  
```Output  
Allocated 40 long integers  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Alokacja pamięci](../../c-runtime-library/memory-allocation.md)   
 [W warstwie bezpłatna](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)