---
title: calloc
description: Funkcja biblioteki wykonawczej C calloc przydziela pamięć zainicjowaną przyuśmiać zero.
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: fb4f7d6dc059023d34cb0b811edf5dfb48cb7a34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333648"
---
# <a name="calloc"></a>calloc

Przydziela tablicę w pamięci z elementami zainicjowanymi do 0.

## <a name="syntax"></a>Składnia

```C
void *calloc(
   size_t number,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*numer*<br/>
Liczba elementów.

*Rozmiar*<br/>
Długość w bajtach każdego elementu.

## <a name="return-value"></a>Wartość zwracana

**calloc** zwraca wskaźnik do przydzielonego miejsca. Miejsce do magazynowania wskazane przez wartość zwracaną jest gwarantowane odpowiednio wyrównane do przechowywania dowolnego typu obiektu. Aby uzyskać wskaźnik do typu innego niż **void**, należy użyć typu rzutu na wartość zwracaną.

## <a name="remarks"></a>Uwagi

Funkcja **calloc** przydziela miejsce do magazynowania dla tablicy elementów *liczbowych,* z których każdy ma bajtów *rozmiaru* długości. Każdy element jest inicjowany do 0.

**calloc** ustawia **errno** na **ENOMEM,** jeśli alokacja pamięci nie powiedzie się lub jeśli ilość żądanej pamięci przekracza **_HEAP_MAXREQ**. Aby uzyskać informacje na temat tego i innych kodów błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

W implementacji firmy Microsoft, jeśli *liczba* lub *rozmiar* wynosi zero, **calloc** zwraca wskaźnik do przydzielonego bloku o rozmiarze zerowym. Próba odczytu lub zapisu za pośrednictwem zwróconego wskaźnika prowadzi do niezdefiniowanego zachowania.

**calloc** używa funkcji [_set_new_mode](set-new-mode.md) C++ do ustawiania *nowego trybu obsługi*. Nowy tryb obsługi wskazuje, czy w przypadku awarii **calloc** ma wywołać nową procedurę obsługi zgodnie z [_set_new_handler](set-new-handler.md). Domyślnie **calloc** nie wywołać nową procedurę obsługi na niepowodzenie alokacji pamięci. Można zastąpić to zachowanie domyślne, tak aby, gdy **calloc** nie można przydzielić pamięci, wywołuje nową procedurę obsługi w taki sam sposób, jak **nowy** operator robi, gdy nie powiedzie się z tego samego powodu. Aby zastąpić wartość domyślną,

```C
_set_new_mode(1);
```

na początku programu lub link z *NEWMODE. OBJ* (patrz [Opcje łącza).](../../c-runtime-library/link-options.md)

Gdy aplikacja jest połączona z wersją debugowania bibliotek w czasie wykonywania języka C, **calloc** rozpoznaje [_calloc_dbg](calloc-dbg.md). Aby uzyskać więcej informacji na temat zarządzania stertą podczas procesu debugowania, zobacz [Sterta debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**calloc** jest `__declspec(noalias)` `__declspec(restrict)`oznaczony i , co oznacza, że funkcja jest gwarantowana, aby nie modyfikować zmiennych globalnych i że wskaźnik zwrócony nie jest aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**calloc**|\<> i \<malloc.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[Wolna](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
