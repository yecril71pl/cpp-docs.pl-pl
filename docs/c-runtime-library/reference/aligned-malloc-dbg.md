---
title: _aligned_malloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_malloc_dbg
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
- _aligned_malloc_dbg
- aligned_malloc_dbg
helpviewer_keywords:
- aligned_malloc_dbg function
- _aligned_malloc_dbg function
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
ms.openlocfilehash: eb58313c892ffe13e9f8e34e98b7940022899d14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341642"
---
# <a name="alignedmallocdbg"></a>_aligned_malloc_dbg

Przydziela pamięć na określonej granicy wyrównania z dodatkowym miejscem dla nagłówka debugowania i zastąpienia buforów (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
void * _aligned_malloc_dbg(
    size_t size,
    size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Rozmiar żądanej alokacji pamięci.

*Wyrównanie*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który zażądał operacji alokacji lub NULL.

*numer wiersza*<br/>
Numer wiersza w pliku źródłowym, gdzie zażądano operacji alokacji lub NULL.

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do bloku pamięci, która została przydzielona lub wartość NULL, jeśli operacja nie powiodła się.

## <a name="remarks"></a>Uwagi

**_aligned_malloc_dbg —** jest wersją debugowania [_aligned_malloc](aligned-malloc.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, każde wywołanie **_aligned_malloc_dbg —** jest ograniczone do wywołania `_aligned_malloc`. Zarówno `_aligned_malloc` i **_aligned_malloc_dbg —** przydzielają blok pamięci w stosie podstawowym, ale **_aligned_malloc_dbg —** oferuje kilka funkcji debugowania: bufory po obu stronach część użytkownika blok do testowania przecieków, i *filename*/*linenumber* informacji do ustalenia źródła pochodzenia żądania alokacji. Śledzenie określonych typów alokacji z parametrem typu blok nie jest obsługiwane debugowania funkcji alokacji wyrównane. Alokacje wyrównany pojawi się jako typ _normal_block — blok.

**_aligned_malloc_dbg —** przydziela blok pamięci z nieco większą ilością miejsca niż żądane *rozmiar*. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Gdy blok zostanie przydzielony, część użytkownika bloku jest wypełniania wartościami 0xCD a każdy bufor zastąpienia jest wypełniany wartościami 0xFD.

**_aligned_malloc_dbg —** ustawia `errno` do `ENOMEM` Jeśli alokacja pamięci nie powiedzie się lub jeśli ilość pamięci potrzebnej (w tym obciążenie, o których wspomniano) przekracza `_HEAP_MAXREQ`. Aby uzyskać informacji na temat tego i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Ponadto **_aligned_malloc_dbg —** sprawdza poprawność parametrów. Jeśli *wyrównanie* nie jest potęgą liczby 2 lub *rozmiar* wynosi zero, funkcja wywoła procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja zwraca wartość NULL i ustawia `errno` do `EINVAL`.

Aby dowiedzieć się jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje dotyczące alokacji typów bloków i sposobu ich używania, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacji na temat różnic między wywołaniem funkcji sterty standard oraz jego wersję debugowania do kompilacji debugowanej aplikacji, zobacz [Debuguj wersje z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_malloc_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)