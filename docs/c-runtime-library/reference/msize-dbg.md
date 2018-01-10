---
title: "_msize_dbg — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _msize_dbg
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
- _msize_dbg
- msize_dbg
dev_langs: C++
helpviewer_keywords:
- memory blocks
- _msize_dbg function
- msize_dbg function
ms.assetid: a333f4b6-f8a2-4e61-bb69-cb34063b8cef
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 018fb7fdce1aeb2a69ac2e6381df1c0da24036a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="msizedbg"></a>_msize_dbg
Oblicza rozmiar bloku pamięci sterty (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      size_t _msize_dbg(  
   void *userData,  
   int blockType   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `userData`  
 Wskaźnik do bloku pamięci dla do ustalania rozmiaru.  
  
 *blockType*  
 Typ bloku pamięci określony: `_CLIENT_BLOCK` lub **_normal_block —**.  
  
## <a name="return-value"></a>Wartość zwracana  
 Po pomyślnym ukończeniu `_msize_dbg` zwraca rozmiar (w bajtach) pamięci określonego bloku; w przeciwnym razie zwraca wartość NULL.  
  
## <a name="remarks"></a>Uwagi  
 `_msize_dbg`jest to wersja debugowania _[msize —](../../c-runtime-library/reference/msize.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowana, każde wywołanie `_msize_dbg` zostanie zmniejszona do wywołania `_msize`. Zarówno `_msize` i `_msize_dbg` Oblicz rozmiar bloku pamięci w stercie podstawowy, ale `_msize_dbg` dodaje dwie funkcje debugowania: rozmiar zwróconego zawiera buforów po obu stronach użytkownika część bloku pamięci i umożliwia rozmiar obliczenia bloku określonego typu.  
  
 Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Informacje o typach bloku alokacji i sposobu ich używania, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywoływanie funkcji sterty standardowe i jego wersji do debugowania w kompilację debugowania aplikacji, zobacz [debugowania wersji z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
 Ta funkcja weryfikuje jej parametr. Jeśli `memblock` wskaźnika o wartości null, jest `_msize` wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli ten błąd jest obsługiwane, funkcja ustawia `errno` do `EINVAL` i zwraca wartość -1.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_msize_dbg`|\<crtdbg.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_msize_dbg.c  
// compile with: /MTd  
/*  
 * This program allocates a block of memory using _malloc_dbg  
 * and then calls _msize_dbg to display the size of that block.  
 * Next, it uses _realloc_dbg to expand the amount of  
 * memory used by the buffer and then calls _msize_dbg again to  
 * display the new amount of memory allocated to the buffer.  
 */  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
        long *buffer, *newbuffer;  
        size_t size;  
  
        /*   
         * Call _malloc_dbg to include the filename and line number  
         * of our allocation request in the header  
         */  
        buffer = (long *)_malloc_dbg( 40 * sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );  
        if( buffer == NULL )  
               exit( 1 );  
  
        /*   
         * Get the size of the buffer by calling _msize_dbg  
         */  
        size = _msize_dbg( buffer, _NORMAL_BLOCK );  
        printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );  
  
        /*   
         * Reallocate the buffer using _realloc_dbg and show the new size  
         */  
        newbuffer = _realloc_dbg( buffer, size + (40 * sizeof(long)), _NORMAL_BLOCK, __FILE__, __LINE__ );  
        if( newbuffer == NULL )  
               exit( 1 );  
        buffer = newbuffer;  
        size = _msize_dbg( buffer, _NORMAL_BLOCK );  
        printf( "Size of block after _realloc_dbg of 40 more longs: %u\n", size );  
  
        free( buffer );  
        exit( 0 );  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
Size of block after _malloc_dbg of 40 longs: 160  
Size of block after _realloc_dbg of 40 more longs: 320  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)   
 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)