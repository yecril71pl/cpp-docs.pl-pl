---
title: realloc | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: realloc
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
- _brealloc
- _nrealloc
- realloc
- _frealloc
dev_langs: C++
helpviewer_keywords:
- _brealloc function
- realloc function
- nrealloc function
- frealloc function
- _nrealloc function
- memory blocks, reallocating
- memory, reallocating
- _frealloc function
- reallocate memory blocks
ms.assetid: 2b2239de-810b-4b11-9438-32ab0a244185
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d3243155fa99ec01e5401d0e5aac77d75807b6c1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="realloc"></a>realloc
Ponowne przydzielenie bloków pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
void *realloc(  
   void *memblock,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `memblock`  
 Wskaźnik do bloku wcześniej alokacji pamięci.  
  
 `size`  
 Nowy rozmiar w bajtach.  
  
## <a name="return-value"></a>Wartość zwracana  
 `realloc`Zwraca `void` wskaźnik do bloku pamięci przydzielić (i prawdopodobnie przenoszenia).  
  
 Jeśli nie jest za mało dostępnej pamięci, aby rozwinąć blok na dany rozmiar, oryginalnego bloku pozostanie niezmieniona, i `NULL` jest zwracany.  
  
 Jeśli `size` jest zero, a następnie bloku wskazywana przez `memblock` zostanie zwolniona; jest zwracana wartość `NULL`, i `memblock` pozostanie wskazującego zwolnionych blok.  
  
 Wartości zwracanej wskazuje miejsce do magazynowania, które na pewno jest odpowiednio dopasowany do przechowywania obiekty dowolnego typu. Aby otrzymywać wskaźnik do typu innego niż `void`, użyj typu rzutowania wartości zwracanej.  
  
## <a name="remarks"></a>Uwagi  
 `realloc` Funkcja zmienia rozmiar bloku alokacji pamięci. `memblock` Argument wskazuje na początku bloku pamięci. Jeśli `memblock` jest `NULL`, `realloc` działa tak samo jak `malloc` i przydziela nowy blok `size` bajtów. Jeśli `memblock` nie jest `NULL`, należy go wskaźnik zwrócony przez poprzednie wywołanie `calloc`, `malloc`, lub `realloc`.  
  
 `size` Argument zapewnia nowy rozmiar bloku, w bajtach. Treść bloku nie uległy zmianie do krótszej z nowym i starym rozmiary, chociaż nowego bloku może być w innej lokalizacji. Ponieważ nowy blok może znajdować się w nowej lokalizacji pamięci, wskaźnik zwrócony przez `realloc` nie musi być wskaźnikiem przekazywane `memblock` argumentu. `realloc`nie zero nowoprzydzielonych pamięci w przypadku wzrostu buforu.  
  
 `realloc`Ustawia `errno` do `ENOMEM` czy alokacja pamięci nie powiedzie się, czy ilość pamięci żądana przekracza `_HEAP_MAXREQ`. Aby uzyskać informacje na ten temat oraz innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 `realloc`wywołania `malloc` aby można było używać języka C++ [_set_new_mode —](../../c-runtime-library/reference/set-new-mode.md) funkcji, aby ustawić nowy tryb obsługi. Nowy tryb obsługi wskazuje, czy w przypadku awarii, `malloc` jest wywołanie nowe procedury obsługi zgodnie z ustawieniami [_set_new_handler —](../../c-runtime-library/reference/set-new-handler.md). Domyślnie `malloc` nie wywołuje nowe procedury obsługi nie można przydzielić pamięci. Można zastąpić to zachowanie domyślne, aby, gdy `realloc` nie może przydzielić pamięci, `malloc` wywołuje nowe procedury obsługi tak samo jak robi `new` operator nie w przypadku niepowodzenia tego samego powodu. Aby zastąpić domyślną, należy wywołać  
  
```  
_set_new_mode(1)  
```  
  
 wcześniej w tych program lub Połącz z biblioteką NEWMODE. OBJ (zobacz [opcje łącza](../../c-runtime-library/link-options.md)).  
  
 Gdy aplikacja jest połączony z wersją debugowania biblioteki wykonawcze języka C, `realloc` jest rozpoznawana jako [_realloc_dbg —](../../c-runtime-library/reference/realloc-dbg.md). Aby uzyskać więcej informacji dotyczących sposobu zarządzania infrastrukturą sterty podczas debugowania procesu, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 `realloc`jest oznaczony jako `__declspec(noalias)` i `__declspec(restrict)`, co oznacza, że funkcja jest gwarantowana nie do modyfikowania zmiennych globalnych i czy zwrócony wskaźnik nie jest używane z aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`realloc`|\<stdlib.h > i \<malloc.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_realloc.c  
// This program allocates a block of memory for  
// buffer and then uses _msize to display the size of that  
// block. Next, it uses realloc to expand the amount of  
// memory used by buffer and then calls _msize again to  
// display the new amount of memory allocated to buffer.  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   long *buffer, *oldbuffer;  
   size_t size;  
  
   if( (buffer = (long *)malloc( 1000 * sizeof( long ) )) == NULL )  
      exit( 1 );  
  
   size = _msize( buffer );  
   printf_s( "Size of block after malloc of 1000 longs: %u\n", size );  
  
   // Reallocate and show new size:  
   oldbuffer = buffer;     // save pointer in case realloc fails  
   if( (buffer = realloc( buffer, size + (1000 * sizeof( long )) ))   
        ==  NULL )  
   {  
      free( oldbuffer );  // free original block  
      exit( 1 );  
   }  
   size = _msize( buffer );  
   printf_s( "Size of block after realloc of 1000 more longs: %u\n",   
            size );  
  
   free( buffer );  
   exit( 0 );  
}  
```  
  
```Output  
Size of block after malloc of 1000 longs: 4000  
Size of block after realloc of 1000 more longs: 8000  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Alokacja pamięci](../../c-runtime-library/memory-allocation.md)   
 [calloc —](../../c-runtime-library/reference/calloc.md)   
 [w warstwie bezpłatna](../../c-runtime-library/reference/free.md)   
 [— funkcja malloc](../../c-runtime-library/reference/malloc.md)