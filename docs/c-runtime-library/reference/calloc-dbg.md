---
title: "_calloc_dbg — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _calloc_dbg
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
- _calloc_dbg
- calloc_dbg
dev_langs: C++
helpviewer_keywords:
- _calloc_dbg function
- calloc_dbg function
ms.assetid: 7f62c42b-eb9f-4de5-87d0-df57036c87de
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1a44f6b7ff132bc402e1b7256b298ce0d3ac9985
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="callocdbg"></a>_calloc_dbg
Przydziela liczba bloków pamięci sterty z dodatkowym miejscem dla nagłówka debugowania i zastąpić buforów (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
void *_calloc_dbg(   
   size_t num,  
   size_t size,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `num`  
 Żądana liczba bloków pamięci.  
  
 `size`  
 Żądany rozmiar każdego bloku pamięci (w bajtach).  
  
 `blockType`  
 Żądany typ bloku pamięci: `_CLIENT_BLOCK` lub `_NORMAL_BLOCK`.  
  
 Informacje o typach bloku alokacji i sposobu ich używania, zobacz[typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).  
  
 `filename`  
 Wskaźnik do nazwy pliku źródłowego, który żądanej operacji alokacji lub `NULL`.  
  
 `linenumber`  
 Numer w pliku źródłowym, której zażądano operacji alokacji wiersza lub `NULL`.  
  
 `filename` i `linenumber` parametry są dostępne tylko podczas `_calloc_dbg` została jawnie wywołana lub [_crtdbg_map_alloc —](../../c-runtime-library/crtdbg-map-alloc.md) stała preprocesora została zdefiniowana.  
  
## <a name="return-value"></a>Wartość zwracana  
 Po pomyślnym ukończeniu ta funkcja zwraca wskaźnik do części użytkownika ostatniego bloku alokacji pamięci, nowych funkcji programu obsługi lub zwraca `NULL`. Pełny opis zwracany zachowanie znajduje się w sekcji uwag. Aby uzyskać więcej informacji o sposobie korzystania z nowych funkcji programu obsługi, zobacz [calloc —](../../c-runtime-library/reference/calloc.md) funkcji.  
  
## <a name="remarks"></a>Uwagi  
 `_calloc_dbg`jest to wersja debugowania [calloc —](../../c-runtime-library/reference/calloc.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowana, każde wywołanie `_calloc_dbg` zostanie zmniejszona do wywołania `calloc`. Zarówno `calloc` i `_calloc_dbg` przydzielić `num` bloki pamięci w stosie podstawowej, ale `_calloc_dbg` oferuje kilka funkcji debugowania:  
  
-   Bufory po obu stronach użytkownika część bloku do testowania przecieki.  
  
-   Parametr typu bloku do śledzenia alokacji określonych typów.  
  
-   `filename`/`linenumber`informacji do ustalenia źródła żądań alokacji.  
  
 `_calloc_dbg`Każdy blok pamięci z nieco więcej miejsca niż żądany przydziela `size`. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Gdy blok zostanie przydzielony, część użytkownika bloku jest wypełniania wartościami 0xCD a każdy bufor zastąpienia jest wypełniany wartościami 0xFD.  
  
 `_calloc_dbg`Ustawia `errno` do `ENOMEM` Jeśli alokacja pamięci nie powiodło się; `EINVAL` jest zwracany, jeśli ilość pamięci potrzebnej (łącznie z czynności wymienionych wcześniej) przekracza `_HEAP_MAXREQ`. Aby uzyskać informacji dotyczących tego i innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywołanie funkcji standardowego stosu lub jego wersja do debugowania kompilacji debugowanej aplikacji, zobacz [debugowania wersji z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_calloc_dbg`|\<crtdbg.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_callocd.c  
/*  
 * This program uses _calloc_dbg to allocate space for  
 * 40 long integers. It initializes each element to zero.  
 */  
#include <stdio.h>  
#include <malloc.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
        long *bufferN, *bufferC;  
  
        /*   
         * Call _calloc_dbg to include the filename and line number  
         * of our allocation request in the header and also so we can  
         * allocate CLIENT type blocks specifically  
         */  
        bufferN = (long *)_calloc_dbg( 40, sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );  
        bufferC = (long *)_calloc_dbg( 40, sizeof(long), _CLIENT_BLOCK, __FILE__, __LINE__ );  
        if( bufferN != NULL && bufferC != NULL )  
              printf( "Allocated memory successfully\n" );  
        else  
              printf( "Problem allocating memory\n" );  
  
        /*   
         * _free_dbg must be called to free CLIENT type blocks  
         */  
        free( bufferN );  
        _free_dbg( bufferC, _CLIENT_BLOCK );  
}  
```  
  
```Output  
Allocated memory successfully  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)   
 [calloc —](../../c-runtime-library/reference/calloc.md)   
 [_malloc_dbg —](../../c-runtime-library/reference/malloc-dbg.md)   
 [_DEBUG](../../c-runtime-library/debug.md)