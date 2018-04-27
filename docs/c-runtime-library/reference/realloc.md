---
title: realloc | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e81f0456fd436ddb0036e0aebd0f56697c1ac213
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
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
Wskaźnik do bloku wcześniej alokacji pamięci.

*Rozmiar*<br/>
Nowy rozmiar w bajtach.

## <a name="return-value"></a>Wartość zwracana

**realloc** zwraca **void** wskaźnik do bloku pamięci przydzielić (i prawdopodobnie przenoszenia).

Jeśli nie jest za mało dostępnej pamięci, aby rozwinąć blok na dany rozmiar, oryginalnego bloku pozostanie niezmieniona, i **NULL** jest zwracany.

Jeśli *rozmiar* jest zero, a następnie bloku wskazywana przez *memblock* zostanie zwolniona; jest zwracana wartość **NULL**, i *memblock* pozostało, wskazując zwolnienie bloku.

Wartości zwracanej wskazuje miejsce do magazynowania, które na pewno jest odpowiednio dopasowany do przechowywania obiekty dowolnego typu. Aby otrzymywać wskaźnik do typu innego niż **void**, użyj typu rzutowania wartości zwracanej.

## <a name="remarks"></a>Uwagi

**Realloc** funkcja zmienia rozmiar bloku alokacji pamięci. *Memblock* argument wskazuje na początku bloku pamięci. Jeśli *memblock* jest **NULL**, **realloc** działa tak samo jak **— funkcja malloc** i przydziela nowy blok *rozmiar*bajtów. Jeśli *memblock* nie jest **NULL**, należy go wskaźnik zwrócony przez poprzednie wywołanie **calloc —**, **— funkcja malloc**, lub **realloc** .

*Rozmiar* argument zapewnia nowy rozmiar bloku, w bajtach. Treść bloku nie uległy zmianie do krótszej z nowym i starym rozmiary, chociaż nowego bloku może być w innej lokalizacji. Ponieważ nowy blok może znajdować się w nowej lokalizacji pamięci, wskaźnik zwrócony przez **realloc** nie musi być wskaźnikiem przekazywane *memblock* argumentu. **realloc** jest niezerowe nowo przydzielonej pamięci w przypadku wzrostu buforu.

**realloc** ustawia **errno** do **enomem —** czy alokacja pamięci nie powiedzie się, czy ilość pamięci żądana przekracza **_heap_maxreq —**. Aby uzyskać informacje na ten temat oraz innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**realloc** wywołania **— funkcja malloc** aby można było używać języka C++ [_set_new_mode —](set-new-mode.md) funkcji, aby ustawić nowy tryb obsługi. Nowy tryb obsługi wskazuje, czy w przypadku awarii, **— funkcja malloc** jest wywołanie nowe procedury obsługi zgodnie z ustawieniami [_set_new_handler —](set-new-handler.md). Domyślnie **— funkcja malloc** nie wywołuje nowe procedury obsługi nie można przydzielić pamięci. Można zastąpić to zachowanie domyślne, aby, gdy **realloc** nie może przydzielić pamięci, **— funkcja malloc** wywołuje nowe procedury obsługi w taki sam jak robi **nowe** operator jest Jeśli go nie powiodło się z tego samego powodu. Aby zastąpić domyślną, należy wywołać

```C
_set_new_mode(1);
```

wcześniej w tych program lub Połącz z biblioteką NEWMODE. OBJ (zobacz [opcje łącza](../../c-runtime-library/link-options.md)).

Gdy aplikacja jest połączony z wersją debugowania biblioteki wykonawcze języka C, **realloc** jest rozpoznawana jako [_realloc_dbg —](realloc-dbg.md). Aby uzyskać więcej informacji dotyczących sposobu zarządzania infrastrukturą sterty podczas debugowania procesu, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**realloc** jest oznaczony jako `__declspec(noalias)` i `__declspec(restrict)`, co oznacza, że funkcja jest gwarantowana nie do modyfikowania zmiennych globalnych i czy zwrócony wskaźnik nie jest używane z aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).

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
