---
title: calloc
ms.date: 11/04/2016
apiname:
- calloc
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
- calloc
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
ms.openlocfilehash: 59aa535136cf32ea5dd68b8917ec969eee41e2ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347733"
---
# <a name="calloc"></a>calloc

Przydziela tablicy w pamięci z elementami inicjowane na wartość 0.

## <a name="syntax"></a>Składnia

```C
void *calloc(
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*Numer*<br/>
Liczba elementów.

*Rozmiar*<br/>
Długość w bajtach każdego elementu.

## <a name="return-value"></a>Wartość zwracana

**calloc** zwraca wskaźnik do przydzielonego miejsca. Miejsca do magazynowania wskazywany przez wartość zwracana jest gwarantowane do bycia odpowiednio wyrównaną do przechowywania dowolnego typu obiektu. Aby uzyskać wskaźnik do typu innego niż **void**, użyj typu rzutowanego na wartość zwracaną.

## <a name="remarks"></a>Uwagi

**Calloc** funkcja przydziela miejsce do magazynowania do tablicy *numer* o długości elementów *rozmiar* bajtów. Każdy element jest inicjowana wartością 0.

**calloc** ustawia **errno** do **ENOMEM** Jeśli alokacja pamięci nie powiedzie się lub Jeśli żądana ilość pamięci, przekracza **_heap_maxreq —**. Aby uzyskać informacje na temat tego i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**calloc** wywołania **— funkcja malloc** używać C++ [_set_new_mode](set-new-mode.md) funkcję, aby ustawić nowy tryb obsługi. Nowy tryb obsługi wskazuje, czy w przypadku awarii, **— funkcja malloc** ma wywoływać nową procedurę obsługi zgodnie z ustawieniem [_set_new_handler](set-new-handler.md). Domyślnie **— funkcja malloc** nie wywołuje nowej procedury obsługi awarii w celu przydzielenia pamięci. Można zastąpić to zachowanie domyślne tak, aby, gdy **calloc** nie może przydzielić pamięci, **— funkcja malloc** wywoła nową procedurę obsługi w taki sam sposób **nowe** jest operator Jeśli jej nie powiedzie się z tego samego powodu. Aby zastąpić domyślne, należy wywołać

```C
_set_new_mode(1);
```

wcześniej program, lub Połącz z biblioteką NEWMODE. OBJ (zobacz [opcje łącza](../../c-runtime-library/link-options.md)).

Gdy aplikacja jest połączona z wersji debugowania bibliotek uruchomieniowych C, **calloc** jest rozpoznawana jako [_calloc_dbg —](calloc-dbg.md). Aby uzyskać więcej informacji na temat sposobu zarządzania stosem podczas debugowania, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**calloc** jest oznaczony jako `__declspec(noalias)` i `__declspec(restrict)`, co oznacza, że funkcja daje gwarancję niemodyfikowania zmiennych globalnych i że zwrócony wskaźnik nie jest aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**calloc**|\<stdlib.h> and \<malloc.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_calloc.c
// This program uses calloc to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>

int main( void )
{
   long *buffer;

   buffer = (long *)calloc( 40, sizeof( long ) );
   if( buffer != NULL )
      printf( "Allocated 40 long integers\n" );
   else
      printf( "Can't allocate memory\n" );
   free( buffer );
}
```

```Output
Allocated 40 long integers
```

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
