---
title: _CrtSetBreakAlloc
ms.date: 11/04/2016
apiname:
- _CrtSetBreakAlloc
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
apitype: DLLExport
f1_keywords:
- CrtSetBreakAlloc
- _CrtSetBreakAlloc
helpviewer_keywords:
- CrtSetBreakAlloc function
- _CrtSetBreakAlloc function
ms.assetid: 33bfc6af-a9ea-405b-a29f-1c2d4d9880a1
ms.openlocfilehash: bbc4b0de553533dde95f37675b3c9234569e3505
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342953"
---
# <a name="crtsetbreakalloc"></a>_CrtSetBreakAlloc

Ustawia punkt przerwania na określony obiekt alokacji numer zamówienia (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
long _CrtSetBreakAlloc(
   long lBreakAlloc
);
```

### <a name="parameters"></a>Parametry

*lBreakAlloc*<br/>
Numer zamówienia alokacji, do których chcesz ustawić punkt przerwania.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość poprzedniego numerem porządkowym obiektu alokacji zawierającego punkt przerwania.

## <a name="remarks"></a>Uwagi

**_CrtSetBreakAlloc** pozwala wykonać wykrywania przecieków pamięci za istotne w określonym punkcie alokacji pamięci i śledzenie wstecz do początku żądania aplikacji. Funkcja używa sekwencyjne numerem porządkowym obiektu alokacji przypisane do bloku pamięci, gdy został przydzielony w stercie. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtSetBreakAlloc** są usuwane podczas przetwarzania wstępnego.

Numerem porządkowym obiektu alokacji znajduje się w *lRequest* pole **_CrtMemBlockHeader** struktury, zdefiniowanego w Crtdbg.h. Gdy informacje o bloku pamięci są raportowane przez jedną z funkcji zrzutu debugowania, ta liczba jest ujęte w nawiasy klamrowe, takich jak {36}.

Aby uzyskać więcej informacji o tym, jak **_CrtSetBreakAlloc** może być używany z innymi funkcjami zarządzania pamięcią, zobacz [Śledzenie żądań alokacji sterty](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać więcej informacji na temat sposobu bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtSetBreakAlloc**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

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
