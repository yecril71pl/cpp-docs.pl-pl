---
title: _calloc_dbg
ms.date: 11/04/2016
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
helpviewer_keywords:
- _calloc_dbg function
- calloc_dbg function
ms.assetid: 7f62c42b-eb9f-4de5-87d0-df57036c87de
ms.openlocfilehash: c525aa2f19b39ba3cb8304c59c96196707ad859c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454395"
---
# <a name="callocdbg"></a>_calloc_dbg

Przydziela liczba bloków pamięci w stosie przy użyciu dodatkowego miejsca dla nagłówka debugowania i zastąpienia buforów (tylko wersja debugowania).

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
Żądany rozmiar każdy blok pamięci (w bajtach).

*blockType*<br/>
Żądany typ bloku pamięci: **_CLIENT_BLOCK** lub **_NORMAL_BLOCK**.

Aby uzyskać informacje dotyczące alokacji typów bloków i sposobu ich używania, zobacz[typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który zażądał operacji alokacji lub **NULL**.

*numer wiersza*<br/>
Numer wiersza w pliku źródłowym, gdzie zażądano operacji alokacji lub **NULL**.

*Filename* i *linenumber* parametry są dostępne tylko podczas **_calloc_dbg —** została jawnie wywołana lub [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)stała preprocesora został zdefiniowany.

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym zakończeniu ta funkcja zwraca wskaźnik do ostatniego bloku ilość przydzielonej pamięci część użytkownika, wywołuje funkcję obsługi nowych lub zwraca **NULL**. Pełny opis zachowania zwrotu zobacz sekcję Uwagi. Aby uzyskać więcej informacji o sposobie korzystania z nowych funkcji obsługi, zobacz [calloc](calloc.md) funkcji.

## <a name="remarks"></a>Uwagi

**_calloc_dbg —** jest wersją debugowania [calloc](calloc.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, każde wywołanie **_calloc_dbg —** jest ograniczone do wywołania **calloc**. Zarówno **calloc** i **_calloc_dbg —** przydzielić *numer* pamięci bloków w stosie podstawowym, ale **_calloc_dbg —** oferuje kilka debugowania funkcje:

- Buforów po obu stronach części bloku do testowania przecieków użytkownika.

- Parametr typu blok do śledzenia określonych typów alokacji.

- *Nazwa pliku*/*linenumber* informacji do ustalenia źródła pochodzenia żądania alokacji.

**_calloc_dbg —** przydziela każdy blok pamięci z nieco większą ilością miejsca niż żądane *rozmiar*. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Gdy blok zostanie przydzielony, część użytkownika bloku jest wypełniania wartościami 0xCD a każdy bufor zastąpienia jest wypełniany wartościami 0xFD.

**_calloc_dbg —** ustawia **errno** do **ENOMEM** Jeśli alokacja pamięci nie powiodło się; **EINVAL** jest zwracany, jeśli ilość pamięci potrzebnej (w tym obciążenie, o których wspomniano) przekracza **_heap_maxreq —**. Aby uzyskać informacji na temat tego i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Aby dowiedzieć się jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywołanie funkcji sterty standardowa a jego wersja do debugowania do kompilacji debugowanej aplikacji, zobacz [Debuguj wersje z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_calloc_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
