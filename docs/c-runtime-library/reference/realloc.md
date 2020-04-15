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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 964c465a95d44de9d8a4d399f23ec43f8a3a6692
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332933"
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

*blok memblock*<br/>
Wskaźnik do wcześniej przydzielonego bloku pamięci.

*Rozmiar*<br/>
Nowy rozmiar w bajtach.

## <a name="return-value"></a>Wartość zwracana

**realloc** zwraca wskaźnik **void** do ponownie przydzielonego (i ewentualnie przeniesionego) bloku pamięci.

Jeśli nie ma wystarczającej ilości dostępnej pamięci, aby rozwinąć blok do danego rozmiaru, oryginalny blok pozostaje niezmieniony, a **null** jest zwracany.

Jeśli *rozmiar* wynosi zero, blok wskazywki *przez blok memblock* jest zwalniany; zwracana wartość **null**, a *memblock* jest pozostawiony wskazujący na zwolniony blok.

Zwracana wartość wskazuje miejsce do magazynowania, które jest gwarantowane odpowiednio wyrównane do przechowywania dowolnego typu obiektu. Aby uzyskać wskaźnik do typu innego niż **void**, należy użyć typu rzutu na wartość zwracaną.

## <a name="remarks"></a>Uwagi

Funkcja **ponownego przymieszczenia** zmienia rozmiar przydzielonego bloku pamięci. Argument *memblock* wskazuje na początek bloku pamięci. Jeśli *memblock* ma **wartość NULL,** **realloc** zachowuje się tak samo jak **malloc** i przydziela nowy blok *bajtów rozmiaru.* Jeśli *memblock* nie ma **wartości NULL**, powinien to być wskaźnik zwrócony przez poprzednie wywołanie **calloc**, **malloc**lub **realloc**.

Argument *size* daje nowy rozmiar bloku w bajtach. Zawartość bloku pozostaje niezmieniona do krótszego rozmiaru nowych i starych, chociaż nowy blok może znajdować się w innym miejscu. Ponieważ nowy blok może znajdować się w nowej lokalizacji pamięci, wskaźnik zwracany przez **realloc** nie jest gwarantowane jako wskaźnik przeszedł przez argument *memblock.* **realokacji** nie zero nowo przydzielonej pamięci w przypadku wzrostu buforu.

**realloc** ustawia **errno** na **ENOMEM,** jeśli alokacja pamięci nie powiedzie się lub jeśli ilość żądanej pamięci przekracza **_HEAP_MAXREQ**. Aby uzyskać informacje na temat tego i innych kodów błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**realloc** wywołuje **malloc** w celu użycia funkcji [_set_new_mode C++](set-new-mode.md) do ustawiania nowego trybu obsługi. Nowy tryb obsługi wskazuje, czy w przypadku awarii **malloc** ma wywołać nową procedurę obsługi zgodnie z [_set_new_handler](set-new-handler.md). Domyślnie **malloc** nie wywołać nową procedurę obsługi na niepowodzenie alokacji pamięci. Można zastąpić to domyślne zachowanie, tak aby, gdy **realloc** nie można przydzielić pamięci, **malloc** wywołuje nową procedurę obsługi w taki sam sposób, jak **nowy** operator robi, gdy nie powiedzie się z tego samego powodu. Aby zastąpić wartość domyślną,

```C
_set_new_mode(1);
```

na początku programu lub linku z NEWMODE. OBJ (patrz [Opcje łącza).](../../c-runtime-library/link-options.md)

Gdy aplikacja jest połączona z wersją debugowania bibliotek w czasie wykonywania języka C, **realloc** jest rozpoznawany [jako _realloc_dbg](realloc-dbg.md). Aby uzyskać więcej informacji na temat zarządzania stertą podczas procesu debugowania, zobacz [Sterta debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**realokacji** `__declspec(noalias)` jest `__declspec(restrict)`oznaczony i , co oznacza, że funkcja jest gwarantowana nie modyfikować zmiennych globalnych i że wskaźnik zwrócony nie jest aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**realloc**|\<> i \<malloc.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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
[Wolna](free.md)<br/>
[malloc](malloc.md)<br/>
