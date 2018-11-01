---
title: _msize_dbg
ms.date: 11/04/2016
apiname:
- _msize_dbg
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
helpviewer_keywords:
- memory blocks
- _msize_dbg function
- msize_dbg function
ms.assetid: a333f4b6-f8a2-4e61-bb69-cb34063b8cef
ms.openlocfilehash: 3b6d08d44162d8263ca88147fe86166924d7d162
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629128"
---
# <a name="msizedbg"></a>_msize_dbg

Oblicza rozmiar bloku pamięci w stercie (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
size_t _msize_dbg(
   void *userData,
   int blockType
);
```

### <a name="parameters"></a>Parametry

*danych użytkownika*<br/>
Wskaźnik do bloku pamięci, do których chcesz określić rozmiar.

*blockType*<br/>
Typ bloku pamięci określonej: **_CLIENT_BLOCK** lub **_NORMAL_BLOCK**.

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym zakończeniu **_msize_dbg —** zwraca rozmiar (w bajtach) bloku pamięci określonej; w przeciwnym razie zwraca **NULL**.

## <a name="remarks"></a>Uwagi

**_msize_dbg —** jest wersją debugowania _[msize —](msize.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, każde wywołanie **_msize_dbg —** jest ograniczone do wywołania **_msize —**. Zarówno **_msize —** i **_msize_dbg —** Oblicz rozmiar bloku pamięci w stosie podstawowym, ale **_msize_dbg —** dodaje dwie funkcje debugowania: obejmuje buforów po obu stronach użytkownika część bloku pamięci, rozmiaru zwróconego i go umożliwia obliczenia rozmiaru dla typów określonego bloku.

Aby dowiedzieć się jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje dotyczące alokacji typów bloków i sposobu ich używania, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacji na temat różnic między wywołaniem funkcji sterty standard oraz jego wersję debugowania do kompilacji debugowanej aplikacji, zobacz [Debuguj wersje z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

Ta funkcja sprawdza poprawność swojego parametru. Jeśli *memblock* jest pustym wskaźnikiem, **_msize —** wywołuje program obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli obsługiwany jest błąd, funkcja ustawia **errno** do **EINVAL** i zwraca wartość -1.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_msize_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

```C
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

### <a name="output"></a>Dane wyjściowe

```Output
Size of block after _malloc_dbg of 40 longs: 160
Size of block after _realloc_dbg of 40 more longs: 320
```

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
