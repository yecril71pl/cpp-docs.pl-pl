---
title: realloc
description: Dokumentacja interfejsu API dla realloc (); który ponownie przydziela bloki pamięci.
ms.date: 9/11/2020
api_name:
- realloc
- _o_realloc
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: c68909b2f5d73959465d63af522ceeb00c8ce23e
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075819"
---
# <a name="realloc"></a>realloc

Ponowne przydzielanie bloków pamięci.

## <a name="syntax"></a>Składnia

```C
void *realloc(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*`memblock`*\
Wskaźnik do wcześniej przydzielony blok pamięci.

*`size`*\
Nowy rozmiar w bajtach.

## <a name="return-value"></a>Wartość zwracana

**`realloc`** zwraca **`void`** wskaźnik do bloku pamięci z ponownie przydzielonym (i prawdopodobnie przeniesionym).

Jeśli nie ma wystarczającej ilości dostępnej pamięci, aby rozszerzyć blok do danego rozmiaru, oryginalny blok zostanie pozostawiony bez zmian i **`NULL`** jest zwracany.

Jeśli *`size`* jest równa zero, blok wskazywany przez *`memblock`* jest zwalniany; zwracana wartość to **`NULL`** , i *`memblock`* pozostanie pozostawiony w bloku zwolnionym.

Wartość zwracana wskazuje miejsce do magazynowania, które jest odpowiednio wyrównane do przechowywania dowolnego typu obiektu. Aby uzyskać wskaźnik do typu innego niż **`void`** , należy użyć rzutowania typu dla zwracanej wartości.

## <a name="remarks"></a>Uwagi

> [!NOTE]
> **`realloc`** nie została zaktualizowana w celu zaimplementowania zachowania C17, ponieważ nowe zachowanie nie jest zgodne z systemem operacyjnym Windows.

**`realloc`** Funkcja zmienia rozmiar przydzielony blok pamięci. *`memblock`* Argument wskazuje początek bloku pamięci. Jeśli *`memblock`* jest **`NULL`** , **`realloc`** działa tak samo jak **`malloc`** i przydziela nowy blok *`size`* bajtów. Jeśli *`memblock`* nie jest **`NULL`** , powinien być wskaźnikiem zwróconym przez poprzednie wywołanie do **`calloc`** , **`malloc`** lub **`realloc`** .

*`size`* Argument zawiera nowy rozmiar bloku, w bajtach. Zawartość bloku nie zmienia się do krótszej wielkości nowych i starych rozmiarów, chociaż nowy blok może znajdować się w innej lokalizacji. Ponieważ nowy blok może znajdować się w nowej lokalizacji pamięci, wskaźnik zwracany przez **`realloc`** nie gwarantuje, że wskaźnik przeszedł przez *`memblock`* argument. **`realloc`** w przypadku wzrostu buforu nie jest to zero nowo przydzieloną pamięci.

**`realloc`** ustawia **`errno`** na **`ENOMEM`** Jeśli alokacja pamięci nie powiedzie się lub jeśli żądana ilość pamięci przekroczy **`_HEAP_MAXREQ`** . Aby uzyskać informacje na temat tego i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**`realloc`** wywołania **`malloc`** w celu użycia funkcji [_Set_new_mode](set-new-mode.md) języka C++ do ustawienia nowego trybu obsługi. Nowy tryb obsługi wskazuje, czy w przypadku niepowodzenia, **`malloc`** ma wywołać nową procedurę obsługi jako ustawioną przez [_set_new_handler](set-new-handler.md). Domyślnie program nie **`malloc`** wywołuje nowej procedury obsługi w przypadku niepowodzenia przydzielenia pamięci. Można zastąpić to zachowanie domyślne, tak aby w przypadku **`realloc`** niepowodzenia przydzielenia pamięci program **`malloc`** wywołuje nową procedurę obsługi w taki sam sposób, w jaki **`new`** operator wykonuje, gdy nie powiedzie się z tego samego powodu. Aby zastąpić wartość domyślną, Połącz

```C
_set_new_mode(1);
```

Wczesne lub połączone z NEWMODE. OBJ (zobacz [Opcje linku](../../c-runtime-library/link-options.md)).

Gdy aplikacja jest połączona z wersją debugową bibliotek uruchomieniowych C, program **`realloc`** rozwiązuje [_realloc_dbg](realloc-dbg.md). Aby uzyskać więcej informacji na temat sposobu zarządzania sterty podczas procesu debugowania, zobacz [sterta debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**`realloc`** jest oznaczona `__declspec(noalias)` i `__declspec(restrict)` , co oznacza, że funkcja nie modyfikuje zmiennych globalnych i że zwrócony wskaźnik nie jest aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczaj](../../cpp/restrict.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**`realloc`**|\<stdlib.h> i \<malloc.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)\
[calloc](calloc.md)\
[zwolniony](free.md)\
[malloc](malloc.md)
