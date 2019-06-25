---
title: _malloc_dbg
ms.date: 11/04/2016
apiname:
- _malloc_dbg
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
- malloc_dbg
- _malloc_dbg
helpviewer_keywords:
- malloc_dbg function
- memory allocation
- _malloc_dbg function
ms.assetid: c97eca51-140b-4461-8bd2-28965b49ecdb
ms.openlocfilehash: b126678a9aecf6ae4041764576e8d06d1557dcc1
ms.sourcegitcommit: fc6bdffcf7d5521609da629621cc8459b200b004
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67351783"
---
# <a name="mallocdbg"></a>_malloc_dbg

Przydziela blok pamięci w stosie przy użyciu dodatkowego miejsca dla nagłówka debugowania i zastąpienia buforów (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
void *_malloc_dbg(
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Żądany rozmiar bloku pamięci (w bajtach).

*blockType*<br/>
Żądany typ bloku pamięci: **_CLIENT_BLOCK** lub **_NORMAL_BLOCK**.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który zażądał operacji alokacji lub **NULL**.

*numer wiersza*<br/>
Numer wiersza w pliku źródłowym, gdzie zażądano operacji alokacji lub **NULL**.

*Filename* i *linenumber* parametry są dostępne tylko podczas **_malloc_dbg** została jawnie wywołana lub [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)stała preprocesora został zdefiniowany.

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym zakończeniu ta funkcja zwraca wskaźnik do część użytkownika bloku pamięci przydzielone, wywołuje funkcję obsługi nowych lub zwraca **NULL**. Pełny opis zachowania zwrotu zobacz następujące sekcji uwag. Aby uzyskać więcej informacji o sposobie korzystania z nowych funkcji obsługi, zobacz [— funkcja malloc](malloc.md) funkcji.

## <a name="remarks"></a>Uwagi

**_malloc_dbg** jest wersją debugowania [— funkcja malloc](malloc.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, każde wywołanie **_malloc_dbg** jest ograniczone do wywołania **— funkcja malloc**. Zarówno **— funkcja malloc** i **_malloc_dbg** przydzielają blok pamięci na stosie podstawowym, ale **_malloc_dbg** oferuje kilka funkcji debugowania: bufory po obu stronach użytkownika część bloku do testowania przecieków, parametr typu blok do śledzenia określonych typów alokacji i *filename*/*linenumber* informacji do ustalenia źródła pochodzenia żądania alokacji.

**_malloc_dbg** przydziela blok pamięci z nieco większą ilością miejsca niż żądane *rozmiar*. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Gdy blok zostanie przydzielony, część użytkownika bloku jest wypełniania wartościami 0xCD a każdy bufor zastąpienia jest wypełniany wartościami 0xFD.

**_malloc_dbg** ustawia **errno** do **ENOMEM** Jeśli alokacja pamięci nie powiedzie się lub jeśli ilość pamięci potrzebnej (w tym obciążenie, o których wspomniano) przekracza **_HEAP_ MAXREQ**. Aby uzyskać informacji na temat tego i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Aby dowiedzieć się jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje dotyczące alokacji typów bloków i sposobu ich używania, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacji na temat różnic między wywołaniem funkcji sterty standard oraz jego wersję debugowania do kompilacji debugowanej aplikacji, zobacz [Debuguj wersje z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_malloc_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

Przykład sposobu użycia **_malloc_dbg**, zobacz [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[malloc](malloc.md)<br/>
[_calloc_dbg](calloc-dbg.md)<br/>
