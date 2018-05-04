---
title: calloc — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6986e1caec25cd544919039f690544af429524af
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="calloc"></a>calloc

Przydziela tablicy w pamięci z elementami równe 0.

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

**calloc —** zwraca wskaźnik do przydzielonego miejsca. Miejsca do magazynowania wskazywanej przez wartość zwracana jest gwarantowana odpowiednio dopasowany do przechowywania obiekty dowolnego typu. Aby otrzymywać wskaźnik do typu innego niż **void**, użyj typu rzutowania wartości zwracanej.

## <a name="remarks"></a>Uwagi

**Calloc —** funkcja przydziela miejsce do magazynowania dla tablicy *numer* o długości elementów *rozmiar* bajtów. Każdy element jest ustawiana na 0.

**calloc —** ustawia **errno** do **enomem —** czy alokacja pamięci nie powiedzie się, czy ilość pamięci żądana przekracza **_heap_maxreq —**. Aby uzyskać informacje na ten temat oraz innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**calloc —** wywołania **— funkcja malloc** do użycia dla języka C++ [_set_new_mode —](set-new-mode.md) funkcji, aby ustawić nowy tryb obsługi. Nowy tryb obsługi wskazuje, czy w przypadku awarii, **— funkcja malloc** jest wywołanie nowe procedury obsługi zgodnie z ustawieniami [_set_new_handler —](set-new-handler.md). Domyślnie **— funkcja malloc** nie wywołuje nowe procedury obsługi nie można przydzielić pamięci. Można zastąpić to zachowanie domyślne, aby, gdy **calloc —** nie może przydzielić pamięci, **— funkcja malloc** wywołuje nowe procedury obsługi w taki sam jak robi **nowe** operator jest Jeśli go nie powiodło się z tego samego powodu. Aby zastąpić domyślną, należy wywołać

```C
_set_new_mode(1);
```

wcześniej w program lub Połącz z biblioteką NEWMODE. OBJ (zobacz [opcje łącza](../../c-runtime-library/link-options.md)).

Gdy aplikacja jest połączony z wersją debugowania biblioteki wykonawcze języka C, **calloc —** jest rozpoznawana jako [_calloc_dbg —](calloc-dbg.md). Aby uzyskać więcej informacji dotyczących sposobu zarządzania infrastrukturą sterty podczas debugowania procesu, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**calloc —** jest oznaczony jako `__declspec(noalias)` i `__declspec(restrict)`, co oznacza, że funkcja jest gwarantowana nie do modyfikowania zmiennych globalnych i czy zwrócony wskaźnik nie jest używane z aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**calloc**|\<stdlib.h > i \<malloc.h >|

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
