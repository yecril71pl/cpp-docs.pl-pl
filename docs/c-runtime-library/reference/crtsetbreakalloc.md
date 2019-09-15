---
title: _CrtSetBreakAlloc
ms.date: 11/04/2016
api_name:
- _CrtSetBreakAlloc
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CrtSetBreakAlloc
- _CrtSetBreakAlloc
helpviewer_keywords:
- CrtSetBreakAlloc function
- _CrtSetBreakAlloc function
ms.assetid: 33bfc6af-a9ea-405b-a29f-1c2d4d9880a1
ms.openlocfilehash: e13c908c1efd1af9196885dee6e3b0f45845946b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942315"
---
# <a name="_crtsetbreakalloc"></a>_CrtSetBreakAlloc

Ustawia punkt przerwania dla określonego numeru zamówienia alokacji obiektu (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
long _CrtSetBreakAlloc(
   long lBreakAlloc
);
```

### <a name="parameters"></a>Parametry

*lBreakAlloc*<br/>
Numer zamówienia alokacji, dla którego ma zostać ustawiony punkt przerwania.

## <a name="return-value"></a>Wartość zwracana

Zwraca poprzedni numer zamówienia alokacji obiektów, który miał ustawiony punkt przerwania.

## <a name="remarks"></a>Uwagi

**_CrtSetBreakAlloc** umożliwia aplikacji wykonywanie wykrywania przecieków pamięci przez rozdzielenie w określonym punkcie alokacji pamięci i śledzenie z powrotem do źródła żądania. Funkcja używa numeru kolejności alokacji sekwencyjnego obiektu przypisanego do bloku pamięci, gdy został przydzielony w stercie. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtSetBreakAlloc** są usuwane podczas przetwarzania wstępnego.

Numer zamówienia alokacji obiektów jest przechowywany w polu *lRequest* struktury **_CrtMemBlockHeader** , zdefiniowanej w CRTDBG. h. Gdy informacje o bloku pamięci są raportowane przez jedną z funkcji zrzutu debugowania, ta liczba jest ujęta w nawiasy klamrowe {36}, na przykład.

Aby uzyskać więcej informacji o tym, jak **_CrtSetBreakAlloc** może być używany z innymi funkcjami zarządzania pamięcią, zobacz [śledzenie żądań alokacji sterty](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać więcej informacji o tym, jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania sterty podstawowej, zobacz [szczegóły sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtSetBreakAlloc**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje wyłącznie [bibliotek uruchomieniowych C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Przykład

```C
// crt_setbrkal.c
// compile with: -D_DEBUG /MTd -Od -Zi -W3 /c /link -verbose:lib -debug

/*
* In this program, a call is made to the _CrtSetBreakAlloc routine
* to verify that the debugger halts program execution when it reaches
* a specified allocation number.
*/

#include <malloc.h>
#include <crtdbg.h>

int main( )
{
        long allocReqNum;
        char *my_pointer;

        /*
         * Allocate "my_pointer" for the first
         * time and ensure that it gets allocated correctly
         */
        my_pointer = malloc(10);
        _CrtIsMemoryBlock(my_pointer, 10, &allocReqNum, NULL, NULL);

        /*
         * Set a breakpoint on the allocation request
         * number for "my_pointer"
         */
        _CrtSetBreakAlloc(allocReqNum+2);

        /*
         * Alternate freeing and reallocating "my_pointer"
         * to verify that the debugger halts program execution
         * when it reaches the allocation request
         */
        free(my_pointer);
        my_pointer = malloc(10);
        free(my_pointer);
        my_pointer = malloc(10);
        free(my_pointer);
}
```

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
