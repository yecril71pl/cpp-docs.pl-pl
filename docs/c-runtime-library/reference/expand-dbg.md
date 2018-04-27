---
title: _expand_dbg — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b8fc9db941700542d82b2a1a1449aafc0375fbf6
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="expanddbg"></a>_expand_dbg

Zmienia rozmiar określony blok pamięci w stercie przez rozszerzanie lub zawierania bloku (tylko wersja do debugowania).

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

*Danych użytkownika*<br/>
Wskaźnik do bloku wcześniej alokacji pamięci.

*newSize*<br/>
Żądany nowy rozmiar bloku (w bajtach).

*blockType*<br/>
Żądany typ bloku zmienionym rozmiarze: **_client_block —** lub **_normal_block —**.

*Nazwa pliku*<br/>
Wskaźnik do nazwy pliku źródłowego, który zażądał rozwiń operacji lub **NULL**.

*numer wiersza*<br/>
Numer w pliku źródłowym, której zażądano operacji rozwiń wiersza lub **NULL**.

*Filename* i *numer wiersza* parametry są dostępne tylko podczas **_expand_dbg —** została jawnie wywołana lub [_crtdbg_map_alloc —](../../c-runtime-library/crtdbg-map-alloc.md)stała preprocesora została zdefiniowana.

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym ukończeniu **_expand_dbg —** zwraca wskaźnik do bloku pamięci o zmienionym rozmiarze. Ponieważ pamięci nie jest przenoszony, adres jest taki sam jak danych użytkownika. Jeśli wystąpił błąd lub nie można rozszerzyć bloku żądany rozmiar, zwraca **NULL**. Jeśli wystąpi błąd, **errno** jest o informacje z systemu operacyjnego temat charakteru błędu. Aby uzyskać więcej informacji na temat **errno**, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Expand_dbg —** funkcji jest wersja debugowania-[rozwiń](expand.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowana, każde wywołanie **_expand_dbg —** zostanie zmniejszona do wywołania **_rozszerz lokację**. Zarówno **_rozszerz lokację** i **_expand_dbg —** zmienić rozmiar bloku pamięci w stosie podstawowej, ale **_expand_dbg —** bierze pod uwagę kilka funkcji debugowania: buforów po obu stronach użytkownika część bloku do testowania przecieki, parametr typu bloku do śledzenia alokacji określonych typów, a *filename*/*numer wiersza* informacji do ustalenia pochodzenia żądań alokacji.

**_expand_dbg —** zmienia rozmiar bloku pamięci określony nieco więcej miejsca niż żądany *newSize*. *newSize* może być większa lub mniejsza niż rozmiar bloku pierwotnie alokacji pamięci. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Rozmiar odbywa się przez rozszerzanie lub instytucje oryginalnego bloku pamięci. **_expand_dbg —** nie przenosi blok pamięci, tak jak w przypadku [_realloc_dbg —](realloc-dbg.md) funkcji.

Gdy *newSize* jest większa niż oryginalnego bloku rozmiar bloku pamięci jest rozwinięta. Podczas rozszerzania, jeśli blok pamięci nie można rozszerzyć, aby pomieścić żądany rozmiar **NULL** jest zwracany. Gdy *newSize* jest mniejszy od oryginalnego bloku rozmiar bloku pamięci jest umową aż do uzyskania nowego rozmiaru.

Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Informacje o typach bloku alokacji i sposobu ich używania, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywoływanie funkcji sterty standardowe i jego wersji do debugowania w kompilację debugowania aplikacji, zobacz [debugowania wersji z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

Ta funkcja weryfikuje jego parametrów. Jeśli *memblock* jest wskaźnika o wartości null, lub jeśli rozmiar jest większy niż **_heap_maxreq —**, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i funkcja zwraca **NULL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_expand_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.

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

Dane wyjściowe tego programu, zależy od możliwości na komputerze, aby rozwinąć wszystkie sekcje. Jeśli wszystkie sekcje są rozwinięte, dane wyjściowe znajduje odzwierciedlenie w sekcji danych wyjściowych.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
