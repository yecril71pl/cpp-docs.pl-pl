---
title: _realloc_dbg
ms.date: 11/04/2016
api_name:
- _realloc_dbg
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
- _realloc_dbg
- realloc_dbg
helpviewer_keywords:
- reallocating memory blocks
- realloc_dbg function
- memory blocks, reallocating
- memory, reallocating
- _realloc_dbg function
ms.assetid: 7c3cb780-51ed-4d9c-9929-cdde606d846a
ms.openlocfilehash: 58d12ed6f4b013996f3f59cba1b146b823adbee6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949511"
---
# <a name="_realloc_dbg"></a>_realloc_dbg

Ponownie przydziela określony blok pamięci w stercie, przenosząc i/lub zmieniając rozmiar bloku (tylko wersja do debugowania).

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
Wskaźnik do wcześniej przydzielony blok pamięci.

*newSize*<br/>
Żądany rozmiar bloku ponownie przydzielony (bajty).

*BlockType*<br/>
Żądany typ dla zaalokowanych bloków: **_CLIENT_BLOCK** lub **_NORMAL_BLOCK**.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który zażądał operacji **przealokacji** lub **wartości null**.

*LineNumber*<br/>
Numer wiersza w pliku źródłowym, w którym zażądano operacji **realokacji** lub **ma ona wartość null**.

Parametry *filename* i *LineNumber* są dostępne tylko wtedy, gdy **_realloc_dbg** została wywołana jawnie lub została zdefiniowana stała preprocesora [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) .

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym zakończeniu ta funkcja zwraca wskaźnik do części użytkownika ponownie przydzieloną pamięć, wywołuje nową funkcję obsługi lub zwraca **wartość null**. Pełny opis zachowania zwrotnego znajduje się w sekcji poniższe uwagi. Aby uzyskać więcej informacji o sposobie używania nowej funkcji obsługi, zobacz [realloc](realloc.md) Function.

## <a name="remarks"></a>Uwagi

**_realloc_dbg** to wersja debugowania funkcji [realloc](realloc.md) . Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, każde wywołanie **_realloc_dbg** jest ograniczone do wywołania **realloc**. Zarówno zmiana **alokacji** , jak i **_realloc_dbg** przydzielenie bloku pamięci w stercie podstawowej, ale **_realloc_dbg** obsługuje kilka funkcji debugowania: bufory po obu stronach części bloku, aby przetestować pod kątem wycieków, parametr typu bloku do Śledź określone typy *alokacji i*/*LineNumber* informacje w celu ustalenia pochodzenia żądań alokacji.

**_realloc_dbg** ponownie przydziela określony blok pamięci o nieco większym miejscu niż żądany *NewSize*. wartość *NewSize* może być większa lub mniejsza od rozmiaru pierwotnie przydzielonych bloków pamięci. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Ponowna Alokacja może spowodować przeniesienie oryginalnego bloku pamięci do innej lokalizacji w stercie, a także zmianę rozmiaru bloku pamięci. Jeśli blok pamięci jest przenoszony, zawartość oryginalnego bloku zostanie zapisywana.

**_realloc_dbg** ustawia **errno** na **ENOMEM** , jeśli alokacja pamięci nie powiedzie się lub jeśli ilość wymaganej pamięci (łącznie z powyższym obciążeniem) przekracza **_HEAP_MAXREQ**. Aby uzyskać informacje o tym i innych kodach błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Aby uzyskać informacje o tym, jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania sterty podstawowej, zobacz [szczegóły sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o typach bloków alokacji i sposobach ich użycia, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywołaniem standardowej funkcji sterty i jej wersji debugowania w kompilacji debugowania aplikacji, zobacz [debugowanie wersji funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_realloc_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje wyłącznie [bibliotek uruchomieniowych C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Przykład

Zobacz przykład w temacie [_msize_dbg](msize-dbg.md) .

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
