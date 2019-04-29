---
title: _recalloc_dbg
ms.date: 11/04/2016
apiname:
- _recalloc_dbg
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
- recalloc_dbg
- _recalloc_dbg
helpviewer_keywords:
- _recalloc_dbg function
- recalloc_dbg function
ms.assetid: 43c3e9b2-be6d-4508-9b0f-3220c8a47ca3
ms.openlocfilehash: e2782492d3338b5b548db0153b6123fb82ff5e72
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357691"
---
# <a name="recallocdbg"></a>_recalloc_dbg

Przydzieli tablicy i inicjuje jego elementy na 0 (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
void *_recalloc_dbg(
   void *userData,
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*userData*<br/>
Wskaźnik do bloku pamięci uprzednio przydzielony.

*Numer*<br/>
Żądana liczba bloków pamięci.

*Rozmiar*<br/>
Żądany rozmiar każdy blok pamięci (w bajtach).

*blockType*<br/>
Żądany typ bloku pamięci: **_CLIENT_BLOCK** lub **_NORMAL_BLOCK**.

Aby uzyskać informacje dotyczące alokacji typów bloków i sposobu ich używania, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który zażądał operacji alokacji lub **NULL**.

*numer wiersza*<br/>
Numer wiersza w pliku źródłowym, gdzie zażądano operacji alokacji lub **NULL**.

*Filename* i *linenumber* parametry są dostępne tylko podczas **_recalloc_dbg —** została jawnie wywołana lub [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) stała preprocesora został zdefiniowany.

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym zakończeniu ta funkcja zwraca wskaźnik do część użytkownika bloku pamięci ponownie przydzielane, wywołuje nową funkcję obsługi albo zwraca **NULL**. Pełny opis zachowania zwrotu zobacz następujące sekcji uwag. Aby uzyskać więcej informacji o sposobie korzystania z nowych funkcji obsługi, zobacz [_recalloc —](recalloc.md) funkcji.

## <a name="remarks"></a>Uwagi

**_recalloc_dbg —** jest wersją debugowania [_recalloc —](recalloc.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, każde wywołanie **_recalloc_dbg —** jest ograniczone do wywołania **_recalloc —**. Zarówno **_recalloc —** i **_recalloc_dbg —** ponownie przydzielić blok pamięci na stosie podstawowym, ale **_recalloc_dbg —** obsługuje kilka funkcji debugowania: bufory po obu stronach Blok część użytkownika bloku do testowania przecieków, wpisz parametr do śledzenia określonych typów alokacji i *filename*/*linenumber* informacji do ustalenia źródła pochodzenia żądania alokacji.

**_recalloc_dbg —** przydzieli blok określonego pamięci z nieco większą ilością miejsca niż żądany rozmiar (*numer* * *rozmiar*) który może być większa lub mniejsza niż rozmiar Blok pierwotnie alokacji pamięci. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Ponownej alokacji może spowodować przeniesienie oryginalnego bloku pamięci do innej lokalizacji w stercie, a także zmiana rozmiaru bloku pamięci. Część użytkownika bloku jest wypełniany wypełniania wartościami 0xcd a każdy bufor zastąpienia jest wypełniany wartościami 0xFD.

**_recalloc_dbg —** ustawia **errno** do **ENOMEM** Jeśli alokacja pamięci nie powiodło się; **EINVAL** jest zwracany, jeśli ilość pamięci potrzebnej (w tym obciążenie, o których wspomniano) przekracza **_heap_maxreq —**. Aby uzyskać informacji na temat tego i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Aby dowiedzieć się jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacji na temat różnic między wywołaniem funkcji sterty standard oraz jego wersję debugowania do kompilacji debugowanej aplikacji, zobacz [Debuguj wersje z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_recalloc_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
