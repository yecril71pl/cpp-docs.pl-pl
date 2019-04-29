---
title: _realloc_dbg
ms.date: 11/04/2016
apiname:
- _realloc_dbg
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
- _realloc_dbg
- realloc_dbg
helpviewer_keywords:
- reallocating memory blocks
- realloc_dbg function
- memory blocks, reallocating
- memory, reallocating
- _realloc_dbg function
ms.assetid: 7c3cb780-51ed-4d9c-9929-cdde606d846a
ms.openlocfilehash: 9b30dfd6fbae9a4831ff53e7896aeb995657da03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357749"
---
# <a name="reallocdbg"></a>_realloc_dbg

Przydzieli określony blok pamięci w stercie, przenoszenie i/lub zmiany rozmiaru bloku (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
void *_realloc_dbg(
   void *userData,
   size_t newSize,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*userData*<br/>
Wskaźnik do bloku pamięci uprzednio przydzielony.

*newsize:*<br/>
Żądany rozmiar reallocated bloku (w bajtach).

*blockType*<br/>
Żądany typ bloku reallocated: **_CLIENT_BLOCK** lub **_NORMAL_BLOCK**.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który zażądał **realloc** operacji lub **NULL**.

*numer wiersza*<br/>
Numer wiersza w pliku źródłowym gdzie **realloc** zażądano operacji lub **NULL**.

*Filename* i *linenumber* parametry są dostępne tylko podczas **_realloc_dbg —** została jawnie wywołana lub [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) stała preprocesora został zdefiniowany.

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym zakończeniu ta funkcja zwraca wskaźnik do część użytkownika bloku pamięci ponownie przydzielane, wywołuje nową funkcję obsługi albo zwraca **NULL**. Pełny opis zachowania zwrotu zobacz następujące sekcji uwag. Aby uzyskać więcej informacji o sposobie korzystania z nowych funkcji obsługi, zobacz [realloc](realloc.md) funkcji.

## <a name="remarks"></a>Uwagi

**_realloc_dbg —** jest wersją debugowania [realloc](realloc.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, każde wywołanie **_realloc_dbg —** jest ograniczone do wywołania **realloc**. Zarówno **realloc** i **_realloc_dbg —** ponownie przydzielić blok pamięci na stosie podstawowym, ale **_realloc_dbg —** obsługuje kilka funkcji debugowania: bufory po obu stronach część użytkownika bloku do testowania przecieków, parametr typu blok do śledzenia określonych typów alokacji i *filename*/*linenumber* informacji do ustalenia źródła pochodzenia żądania alokacji.

**_realloc_dbg —** przydzieli blok określonego pamięci z nieco większą ilością miejsca niż żądane *newSize*. *newSize* może być większa lub mniejsza niż rozmiar bloku pamięci pierwotnie przydzielone. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Ponownej alokacji może spowodować przeniesienie oryginalnego bloku pamięci do innej lokalizacji w stercie, a także zmiana rozmiaru bloku pamięci. Jeśli blok pamięci jest przenoszona, zawartość oryginalnego bloku zostaną zastąpione.

**_realloc_dbg —** ustawia **errno** do **ENOMEM** Jeśli alokacja pamięci nie powiedzie się lub jeśli ilość pamięci potrzebnej (w tym obciążenie, o których wspomniano) przekracza **_HEAP_ MAXREQ**. Aby uzyskać informacji na temat tego i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Aby dowiedzieć się jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje dotyczące alokacji typów bloków i sposobu ich używania, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacji na temat różnic między wywołaniem funkcji sterty standard oraz jego wersję debugowania do kompilacji debugowanej aplikacji, zobacz [Debuguj wersje z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_realloc_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

Zobacz przykład w [_msize_dbg —](msize-dbg.md) tematu.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
