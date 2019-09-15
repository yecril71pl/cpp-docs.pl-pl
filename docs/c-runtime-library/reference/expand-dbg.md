---
title: _expand_dbg
ms.date: 11/04/2016
api_name:
- _expand_dbg
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- expand_dbg
- _expand_dbg
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
ms.openlocfilehash: 836b9cffcf0367f248a14469b30c1a355e2bdec2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941579"
---
# <a name="_expand_dbg"></a>_expand_dbg

Zmienia rozmiar określonego bloku pamięci w stercie przez rozwijanie lub zapełnienie bloku (tylko wersja do debugowania).

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
Wskaźnik do wcześniej przydzielony blok pamięci.

*newSize*<br/>
Żądany nowy rozmiar bloku (w bajtach).

*BlockType*<br/>
Żądany typ dla bloku o zmienionym rozmiarze: **_CLIENT_BLOCK** lub **_NORMAL_BLOCK**.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który zażądał operacji rozszerzania lub **ma wartość null**.

*LineNumber*<br/>
Numer wiersza w pliku źródłowym, w którym zażądano operacji rozwiń lub **wartość null**.

Parametry *filename* i *LineNumber* są dostępne tylko wtedy, gdy **_expand_dbg** została wywołana jawnie lub została zdefiniowana stała preprocesora [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) .

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym zakończeniu **_expand_dbg** zwraca wskaźnik do bloku pamięci o zmienionym rozmiarze. Ponieważ pamięć nie jest przenoszona, adres jest taki sam jak userData. Jeśli wystąpi błąd lub nie można rozszerzyć bloku o żądany rozmiar, zwraca **wartość null**. Jeśli wystąpi awaria, **errno** jest z informacjami z systemu operacyjnego o charakterze błędu. Aby uzyskać więcej informacji na temat **errno**, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_expand_dbg** jest wersją debugowania funkcji _[expand](expand.md) . Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, każde wywołanie **_expand_dbg** jest ograniczone do wywołania **_expand**. Zarówno **_expand** , jak i **_expand_dbg** , Zmień rozmiar bloku pamięci w stercie podstawowej, ale **_expand_dbg** obsługuje kilka funkcji debugowania: bufory po obu stronach części bloku, aby przetestować pod kątem wycieków, parametr typu bloku do śledzenia określone typy alokacji i *Nazwa pliku*/*LineNumber* informacje w celu określenia pochodzenia żądań alokacji.

**_expand_dbg** zmienia rozmiar określonego bloku pamięci na nieco więcej miejsca niż żądany *NewSize*. wartość *NewSize* może być większa lub mniejsza od rozmiaru pierwotnie przydzielonych bloków pamięci. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Zmiana rozmiaru jest realizowana przez rozwijanie lub zapełnienie oryginalnego bloku pamięci. **_expand_dbg** nie przenosi bloku pamięci, podobnie jak funkcja [_realloc_dbg](realloc-dbg.md) .

Gdy wartość *NewSize* jest większa niż oryginalny rozmiar bloku, blok pamięci jest rozwinięty. Podczas rozszerzania, jeśli blok pamięci nie może zostać rozszerzony w celu dopasowania żądanego rozmiaru, zwracana jest **wartość null** . Gdy wartość *NewSize* jest mniejsza niż oryginalny rozmiar bloku, blok pamięci jest zakontraktowany do momentu uzyskania nowego rozmiaru.

Aby uzyskać informacje o tym, jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania sterty podstawowej, zobacz [szczegóły sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o typach bloków alokacji i sposobach ich użycia, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywołaniem standardowej funkcji sterty i jej wersji debugowania w kompilacji debugowania aplikacji, zobacz [debugowanie wersji funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *memblock* jest wskaźnikiem o wartości null lub jeśli rozmiar jest większy niż **_HEAP_MAXREQ**, ta funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a funkcja zwraca **wartość null**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_expand_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje wyłącznie [bibliotek uruchomieniowych C](../../c-runtime-library/crt-library-features.md) .

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

Dane wyjściowe tego programu zależą od możliwości rozwinięcia wszystkich sekcji przez komputer. Jeśli wszystkie sekcje są rozwinięte, dane wyjściowe zostaną odzwierciedlone w sekcji Output (dane wyjściowe).

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
