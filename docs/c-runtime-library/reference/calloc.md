---
title: calloc
description: Funkcja biblioteki środowiska uruchomieniowego języka C calloc przypisuje pamięć zainicjowaną przez zero.
ms.date: 4/2/2020
api_name:
- calloc
- _o_calloc
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
- calloc
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
ms.openlocfilehash: 067ce6f347f4b24ad8c85990e70fe4d79305535c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213635"
---
# <a name="calloc"></a>calloc

Alokuje tablicę w pamięci z elementami zainicjowanymi do 0.

## <a name="syntax"></a>Składnia

```C
void *calloc(
   size_t number,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*liczba*<br/>
Liczba elementów.

*zmienia*<br/>
Długość w bajtach każdego elementu.

## <a name="return-value"></a>Wartość zwracana

**calloc** zwraca wskaźnik do przydzielonych miejsc. Miejsce do magazynowania wskazywane przez wartość zwracaną jest gwarantowane odpowiednio wyrównane do przechowywania dowolnego typu obiektu. Aby uzyskać wskaźnik do typu innego niż **`void`** , należy użyć rzutowania typu dla zwracanej wartości.

## <a name="remarks"></a>Uwagi

Funkcja **calloc** przydziela miejsce do magazynowania dla tablicy elementów *liczbowych* , o *długości bajtów.* Każdy element jest inicjowany do wartości 0.

**calloc** ustawia **errno** na **ENOMEM** , jeśli alokacja pamięci nie powiedzie się lub jeśli żądana ilość pamięci przekroczy **_HEAP_MAXREQ**. Aby uzyskać informacje na temat tego i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

W implementacji firmy Microsoft, jeśli *Liczba* lub *rozmiar* wynosi zero, **calloc** zwraca wskaźnik do przydzielony blok o rozmiarze innym niż zero. Próba odczytu lub zapisu przez zwrócony wskaźnik prowadzi do niezdefiniowanego zachowania.

**calloc** używa funkcji C++ [_set_new_mode](set-new-mode.md) , aby ustawić *Nowy tryb obsługi*. Nowy tryb obsługi wskazuje, czy w przypadku niepowodzenia **calloc** ma wywołać nową procedurę obsługi jako ustawioną przez [_set_new_handler](set-new-handler.md). Domyślnie **calloc** nie wywołuje nowej procedury obsługi w przypadku niepowodzenia przydzielenia pamięci. Można zastąpić to zachowanie domyślne, tak aby w przypadku niepowodzenia przydzielenia pamięci przez program **calloc** w taki sam sposób wywołuje nową procedurę obsługi w taki sam sposób, jak w przypadku **`new`** niepowodzenia z tego samego powodu. Aby zastąpić wartość domyślną, Połącz

```C
_set_new_mode(1);
```

Wczesne w programie lub łącz z *NEWMODE. OBJ* (zobacz [Opcje linku](../../c-runtime-library/link-options.md)).

Gdy aplikacja jest połączona z wersją debugową bibliotek uruchomieniowych C, **calloc** jest rozpoznawana jako [_calloc_dbg](calloc-dbg.md). Aby uzyskać więcej informacji na temat sposobu zarządzania sterty podczas procesu debugowania, zobacz [sterta debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**calloc** jest oznaczona `__declspec(noalias)` i `__declspec(restrict)` , co oznacza, że funkcja nie modyfikuje zmiennych globalnych i że wskaźnik nie ma aliasu. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczaj](../../cpp/restrict.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**calloc**|\<stdlib.h> i \<malloc.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
[zwolniony](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
