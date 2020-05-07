---
title: realloc
ms.date: 4/2/2020
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
ms.openlocfilehash: 15c818ee6f70d02fb9b63f12deef6b1bf3698322
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917941"
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

*memblock*<br/>
Wskaźnik do wcześniej przydzielony blok pamięci.

*size*<br/>
Nowy rozmiar w bajtach.

## <a name="return-value"></a>Wartość zwracana

Funkcja **realloc** zwraca wskaźnik **void** do ponownie przydzielony blok pamięci (i prawdopodobnie przeniesiony).

Jeśli nie ma wystarczającej ilości dostępnej pamięci, aby rozszerzyć blok do danego rozmiaru, oryginalny blok pozostaje niezmieniony i zwracana jest **wartość null** .

Jeśli *rozmiar* wynosi zero, blok wskazywany przez *memblock* jest zwolniony. zwracana wartość ma wartość **null**, a *memblock* pozostawia w bloku zwolnionym.

Wartość zwracana wskazuje miejsce do magazynowania, które jest gwarantowane odpowiednio wyrównane do przechowywania dowolnego typu obiektu. Aby uzyskać wskaźnik do typu innego niż **void**, należy użyć rzutowania typu dla zwracanej wartości.

## <a name="remarks"></a>Uwagi

Funkcja **realloc** zmienia rozmiar przydzielony blok pamięci. Argument *memblock* wskazuje początek bloku pamięci. Jeśli *memblock* ma **wartość null**, funkcja ponownej **alokacji** zachowuje się tak samo jak **malloc** i przydziela nowy blok *rozmiaru* bajtów. Jeśli *memblock* nie ma **wartości null**, powinien być wskaźnikiem zwróconym przez poprzednie wywołanie metody **calloc**, **malloc**lub **realloc**.

Argument *size* zawiera nowy rozmiar bloku, w bajtach. Zawartość bloku nie zmienia się do krótszej wielkości nowych i starych rozmiarów, chociaż nowy blok może znajdować się w innej lokalizacji. Ponieważ nowy blok może znajdować się w nowej lokalizacji pamięci, wskaźnik zwracany przez proces **realloc** nie gwarantuje, że wskaźnik przeszedł przez argument *memblock* . **realloc** nie ma zerowej nowo przydzieloną pamięci w przypadku wzrostu buforu.

**reallocing** ustawia **errno** do **ENOMEM** , jeśli alokacja pamięci nie powiedzie się lub jeśli żądana ilość pamięci przekroczy **_HEAP_MAXREQ**. Aby uzyskać informacje na temat tego i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**przeallocj** wywołania **malloc** , aby użyć funkcji [_set_new_mode](set-new-mode.md) C++ do ustawienia nowego trybu obsługi. Nowy tryb obsługi wskazuje, czy w przypadku niepowodzenia, **malloc** ma wywołać nową procedurę obsługi jako ustawioną przez [_set_new_handler](set-new-handler.md). Domyślnie funkcja **malloc** nie wywołuje nowej procedury obsługi w przypadku niepowodzenia przydzielenia pamięci. To zachowanie domyślne można przesłonić, dzięki czemu **w przypadku** niepowodzenia alokacji pamięci przez ponowną alokację funkcja **malloc** wywołuje nową procedurę obsługi w taki sam sposób, w jaki operator **New** wykonuje, gdy nie powiedzie się z tego samego powodu. Aby zastąpić wartość domyślną, Połącz

```C
_set_new_mode(1);
```

Wczesne lub połączone z NEWMODE. OBJ (zobacz [Opcje linku](../../c-runtime-library/link-options.md)).

Gdy aplikacja jest połączona z wersją debugową bibliotek uruchomieniowych C, **realloc** rozwiązuje [_realloc_dbg](realloc-dbg.md). Aby uzyskać więcej informacji na temat sposobu zarządzania sterty podczas procesu debugowania, zobacz [sterta debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**realloc** jest oznaczona `__declspec(noalias)` i `__declspec(restrict)`, co oznacza, że funkcja jest gwarantowana, aby nie modyfikować zmiennych globalnych i że zwrócony wskaźnik nie ma aliasu. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczaj](../../cpp/restrict.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**realloc**|\<STDLIB. h> i \<malloc. h>|

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

## <a name="see-also"></a>Zobacz też

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[zwolniony](free.md)<br/>
[malloc](malloc.md)<br/>
