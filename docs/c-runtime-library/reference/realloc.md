---
title: realloc
ms.date: 11/04/2016
apiname:
- realloc
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
ms.openlocfilehash: 0d61746365a8ded8d68072b1f398a18ba6ce7605
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544966"
---
# <a name="realloc"></a>realloc

Ponowne przydzielenie bloków pamięci.

## <a name="syntax"></a>Składnia

```C
void *realloc(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Wskaźnik do bloku pamięci uprzednio przydzielony.

*Rozmiar*<br/>
Nowy rozmiar w bajtach.

## <a name="return-value"></a>Wartość zwracana

**realloc** zwraca **void** wskaźnik do bloku pamięci ponownie przydzielane (i ewentualnie przenoszenia).

Jeśli nie jest za mało dostępnej pamięci, aby rozwinąć blok na dany rozmiar, oryginalnym bloku pozostanie niezmieniona, a **NULL** jest zwracana.

Jeśli *rozmiar* jest zero, a następnie blok wskazywany przez *memblock* jest zwalniana; wartość zwracana jest **NULL**, i *memblock* pozostanie, wskazując Blok zwolnione.

Zwracana wartość wskazuje miejsce do magazynowania, który gwarantuje bycia odpowiednio wyrównaną do przechowywania dowolnego typu obiektu. Aby uzyskać wskaźnik do typu innego niż **void**, użyj typu rzutowanego na wartość zwracaną.

## <a name="remarks"></a>Uwagi

**Realloc** funkcja zmieni rozmiar bloku ilość przydzielonej pamięci. *Memblock* argument wskazuje na początku bloku pamięci. Jeśli *memblock* jest **NULL**, **realloc** działa tak samo jak **— funkcja malloc** i przydziela blok nowe *rozmiar*bajtów. Jeśli *memblock* nie jest **NULL**, wskaźnik zwracany przez poprzednie wywołanie powinno być **calloc**, **— funkcja malloc**, lub **realloc** .

*Rozmiar* argument zapewnia nowy rozmiar bloku, w bajtach. Zawartość bloku nie uległy zmianie maksymalnie krótszy z nowym i starym rozmiarów, mimo że nowego bloku mogą znajdować się w innej lokalizacji. Ponieważ nowy blok może znajdować się w nowej lokalizacji pamięci, wskaźnik zwracany przez **realloc** nie musi zostać przekazany przez wskaźnik myszy *memblock* argumentu. **realloc** jest niezerowe nowo przydzielonej pamięci w przypadku wzrostu buforu.

**realloc** ustawia **errno** do **ENOMEM** Jeśli alokacja pamięci nie powiedzie się lub Jeśli żądana ilość pamięci, przekracza **_heap_maxreq —**. Aby uzyskać informacje na temat tego i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**realloc** wywołania **— funkcja malloc** aby można było używać języka C++ [_set_new_mode](set-new-mode.md) funkcję, aby ustawić nowy tryb obsługi. Nowy tryb obsługi wskazuje, czy w przypadku awarii, **— funkcja malloc** ma wywoływać nową procedurę obsługi zgodnie z ustawieniem [_set_new_handler](set-new-handler.md). Domyślnie **— funkcja malloc** nie wywołuje nowej procedury obsługi awarii w celu przydzielenia pamięci. Można zastąpić to zachowanie domyślne tak, aby, gdy **realloc** nie może przydzielić pamięci, **— funkcja malloc** wywoła nową procedurę obsługi w taki sam sposób **nowe** jest operator Jeśli jej nie powiedzie się z tego samego powodu. Aby zastąpić domyślne, należy wywołać

```C
_set_new_mode(1);
```

wcześniej w tych program lub Połącz z biblioteką NEWMODE. OBJ (zobacz [opcje łącza](../../c-runtime-library/link-options.md)).

Gdy aplikacja jest połączona z wersji debugowania bibliotek uruchomieniowych C, **realloc** jest rozpoznawana jako [_realloc_dbg —](realloc-dbg.md). Aby uzyskać więcej informacji na temat sposobu zarządzania stosem podczas debugowania, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**realloc** jest oznaczony jako `__declspec(noalias)` i `__declspec(restrict)`, co oznacza, że funkcja daje gwarancję niemodyfikowania zmiennych globalnych i że zwrócony wskaźnik nie jest aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**realloc**|\<stdlib.h > i \<malloc.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
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

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
