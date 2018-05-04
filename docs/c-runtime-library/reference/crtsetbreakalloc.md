---
title: _Crtsetbreakalloc — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CrtSetBreakAlloc function
- _CrtSetBreakAlloc function
ms.assetid: 33bfc6af-a9ea-405b-a29f-1c2d4d9880a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32e8fedcd70d0e901c63cd5e794773451f436326
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="crtsetbreakalloc"></a>_CrtSetBreakAlloc

Ustawia określony obiekt numer zamówienia alokacji (tylko wersja do debugowania) punkt przerwania.

## <a name="syntax"></a>Składnia

```C
long _CrtSetBreakAlloc(
   long lBreakAlloc
);
```

### <a name="parameters"></a>Parametry

*lBreakAlloc*<br/>
Numer zamówienia alokacji, dla którego można ustawić punktu przerwania.

## <a name="return-value"></a>Wartość zwracana

Zwraca obiekt alokacji kolejności poprzednich mająca ustawić punkt przerwania.

## <a name="remarks"></a>Uwagi

**_Crtsetbreakalloc —** temu aplikacja może wykonać wykrywanie przecieków pamięci podziału w określonym punkcie przydziału pamięci i śledzenie Wstecz, aby pochodzenia żądania. Funkcja używa o liczbie porządkowej alokacji obiektu sekwencyjne przypisane do blok pamięci, gdy została przydzielona w stosie. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań **_crtsetbreakalloc —** są usuwane podczas przetwarzania wstępnego.

Numer zamówienia alokacji obiekt jest przechowywany w *lRequest* pole **_crtmemblockheader —** struktury zdefiniowane w Crtdbg.h. Gdy informacje o blok pamięci został zgłoszony przez jedną z funkcji zrzutu debugowania, ta liczba jest ujęta w nawiasy klamrowe, takich jak {36}.

Aby uzyskać więcej informacji o tym, jak **_crtsetbreakalloc —** może być używany z innymi funkcje zarządzania pamięcią, zobacz [Śledzenie żądań alokacji sterty](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać więcej informacji dotyczących sposobu bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtSetBreakAlloc**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.

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
