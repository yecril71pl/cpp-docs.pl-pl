---
title: _calloc_dbg — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _calloc_dbg
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
- _calloc_dbg
- calloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- _calloc_dbg function
- calloc_dbg function
ms.assetid: 7f62c42b-eb9f-4de5-87d0-df57036c87de
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2759c19fb88b820fc346b5cf35e97522b7e74cb6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396774"
---
# <a name="callocdbg"></a>_calloc_dbg

Przydziela liczba bloków pamięci sterty z dodatkowym miejscem dla nagłówka debugowania i zastąpić buforów (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
void *_calloc_dbg(
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*Numer*<br/>
Żądana liczba bloków pamięci.

*Rozmiar*<br/>
Żądany rozmiar każdego bloku pamięci (w bajtach).

*blockType*<br/>
Żądany typ bloku pamięci: **_client_block —** lub **_normal_block —**.

Informacje o typach bloku alokacji i sposobu ich używania, zobacz[typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).

*Nazwa pliku*<br/>
Wskaźnik do nazwy pliku źródłowego, który żądanej operacji alokacji lub **NULL**.

*numer wiersza*<br/>
Numer w pliku źródłowym, której zażądano operacji alokacji wiersza lub **NULL**.

*Filename* i *numer wiersza* parametry są dostępne tylko podczas **_calloc_dbg —** została jawnie wywołana lub [_crtdbg_map_alloc —](../../c-runtime-library/crtdbg-map-alloc.md)stała preprocesora została zdefiniowana.

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym ukończeniu ta funkcja zwraca wskaźnik do części użytkownika ostatniego bloku alokacji pamięci, nowych funkcji programu obsługi lub zwraca **NULL**. Pełny opis zwracany zachowanie znajduje się w sekcji uwag. Aby uzyskać więcej informacji o sposobie korzystania z nowych funkcji programu obsługi, zobacz [calloc —](calloc.md) funkcji.

## <a name="remarks"></a>Uwagi

**_calloc_dbg —** jest wersja debugowania [calloc —](calloc.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowana, każde wywołanie **_calloc_dbg —** zostanie zmniejszona do wywołania **calloc —**. Zarówno **calloc —** i **_calloc_dbg —** przydzielić *numer* bloki pamięci w stosie podstawowej, ale **_calloc_dbg —** oferuje kilka debugowania funkcje:

- Bufory po obu stronach użytkownika część bloku do testowania przecieki.

- Parametr typu bloku do śledzenia alokacji określonych typów.

- *Nazwa pliku*/*numer wiersza* informacji do ustalenia źródła żądań alokacji.

**_calloc_dbg —** przydziela każdy blok pamięci z nieco więcej miejsca niż żądany *rozmiar*. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Gdy blok zostanie przydzielony, część użytkownika bloku jest wypełniania wartościami 0xCD a każdy bufor zastąpienia jest wypełniany wartościami 0xFD.

**_calloc_dbg —** ustawia **errno** do **enomem —** Jeśli alokacja pamięci nie powiodło się; **Einval —** jest zwracany, jeśli ilość pamięci potrzebnej (łącznie z czynności wymienionych wcześniej) przekracza **_heap_maxreq —**. Aby uzyskać informacji dotyczących tego i innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywołanie funkcji standardowego stosu lub jego wersja do debugowania kompilacji debugowanej aplikacji, zobacz [debugowania wersji z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_calloc_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_callocd.c
// This program uses _calloc_dbg to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>
#include <crtdbg.h>

int main( void )
{
    long *bufferN, *bufferC;

    // Call _calloc_dbg to include the filename and line number
    // of our allocation request in the header and also so we can
    // allocate CLIENT type blocks specifically
    bufferN = (long *)_calloc_dbg( 40, sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );
    bufferC = (long *)_calloc_dbg( 40, sizeof(long), _CLIENT_BLOCK, __FILE__, __LINE__ );
    if( bufferN != NULL && bufferC != NULL )
        printf( "Allocated memory successfully\n" );
    else
        printf( "Problem allocating memory\n" );

    / _free_dbg must be called to free CLIENT type blocks
    free( bufferN );
    _free_dbg( bufferC, _CLIENT_BLOCK );
}
```

```Output
Allocated memory successfully
```

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[calloc](calloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
