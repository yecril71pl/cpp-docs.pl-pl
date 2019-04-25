---
title: _expand_dbg
ms.date: 11/04/2016
apiname:
- _expand_dbg
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
- expand_dbg
- _expand_dbg
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
ms.openlocfilehash: cc3aa2b7e39b52eb71ac10a9b5c4a221ba6fb70c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62288048"
---
# <a name="expanddbg"></a>_expand_dbg

Zmienia rozmiar określony blok pamięci w stosie przez rozszerzanie lub zawierania bloku (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
void *_expand_dbg(
   void *userData,
   size_t newSize,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*userData*<br/>
Wskaźnik do bloku pamięci uprzednio przydzielony.

*newsize:*<br/>
Żądany nowy rozmiar bloku (w bajtach).

*blockType*<br/>
Żądany typ bloku o zmienionym rozmiarze: **_CLIENT_BLOCK** lub **_NORMAL_BLOCK**.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który zażądał rozwiń operacji lub **NULL**.

*numer wiersza*<br/>
Numer wiersza w pliku źródłowym, gdzie zażądano operacji rozwijania lub **NULL**.

*Filename* i *linenumber* parametry są dostępne tylko podczas **_expand_dbg —** została jawnie wywołana lub [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)stała preprocesora został zdefiniowany.

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym zakończeniu **_expand_dbg —** zwraca wskaźnik do bloku pamięci o zmienionym rozmiarze. Ponieważ pamięci nie jest przenoszony, adres jest taki sam jak userData. Jeśli wystąpił błąd lub nie można zdekompresować bloku żądany rozmiar, zwraca **NULL**. Jeśli wystąpi błąd, **errno** jest przy użyciu informacji z systemu operacyjnego dotyczące charakteru błędu. Aby uzyskać więcej informacji na temat **errno**, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Expand_dbg —** funkcja jest wersją debugowania _[rozwiń](expand.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, każde wywołanie **_expand_dbg —** jest ograniczone do wywołania **_rozwiń**. Zarówno **_rozwiń** i **_expand_dbg —** rozmiar bloku pamięci na stosie podstawowym, ale **_expand_dbg —** obsługuje kilka funkcji debugowania: bufory po obu stronach użytkownika część bloku do testowania przecieków, parametr typu blok do śledzenia określonych typów alokacji i *filename*/*linenumber* informacji do ustalenia źródła pochodzenia żądania alokacji.

**_expand_dbg —** zmienia rozmiar bloku określonym pamięci z nieco większą ilością miejsca niż żądane *newSize*. *newSize* może być większa lub mniejsza niż rozmiar bloku pamięci pierwotnie przydzielone. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Zmiana rozmiaru odbywa się przez rozszerzanie lub instytucje oryginalnego bloku pamięci. **_expand_dbg —** nie powoduje przeniesienia bloku pamięci, tak jak [_realloc_dbg —](realloc-dbg.md) funkcji.

Gdy *newSize* jest większa niż oryginalnego bloku jest rozwinięty rozmiar bloku pamięci. Podczas rozszerzania, jeśli blok pamięci nie można rozszerzyć, aby dopasować żądany rozmiar **NULL** jest zwracana. Gdy *newSize* jest mniejszy od oryginalnego bloku jest nabytej rozmiar bloku pamięci, aż do uzyskania nowego rozmiaru.

Aby dowiedzieć się jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje dotyczące alokacji typów bloków i sposobu ich używania, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacji na temat różnic między wywołaniem funkcji sterty standard oraz jego wersję debugowania do kompilacji debugowanej aplikacji, zobacz [Debuguj wersje z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *memblock* jest wskaźnikiem typu null, lub jeśli rozmiar jest większy niż **_heap_maxreq —**, funkcja wywoła procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** a funkcja zwraca **NULL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_expand_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

```C
// crt_expand_dbg.c
//
// This program allocates a block of memory using _malloc_dbg
// and then calls _msize_dbg to display the size of that block.
// Next, it uses _expand_dbg to expand the amount of
// memory used by the buffer and then calls _msize_dbg again to
// display the new amount of memory allocated to the buffer.
//

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>
#include <crtdbg.h>

int main( void )
{
   long *buffer;
   size_t size;

   // Call _malloc_dbg to include the filename and line number
   // of our allocation request in the header
   buffer = (long *)_malloc_dbg( 40 * sizeof(long),
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );
   if( buffer == NULL )
      exit( 1 );

   // Get the size of the buffer by calling _msize_dbg
   size = _msize_dbg( buffer, _NORMAL_BLOCK );
   printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );

   // Expand the buffer using _expand_dbg and show the new size
   buffer = (long *)_expand_dbg( buffer, size + sizeof(long),
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );

   if( buffer == NULL )
      exit( 1 );
   size = _msize_dbg( buffer, _NORMAL_BLOCK );
   printf( "Size of block after _expand_dbg of 1 more long: %u\n",
           size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after _malloc_dbg of 40 longs: 160
Size of block after _expand_dbg of 1 more long: 164
```

## <a name="comment"></a>Komentarz

Dane wyjściowe tego programu, zależy od możliwości na komputerze, aby rozwinąć wszystkie sekcje. Jeśli wszystkie sekcje są rozwinięte, danych wyjściowych jest widoczne w sekcji danych wyjściowych.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
