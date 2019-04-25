---
title: _getdcwd_dbg, _wgetdcwd_dbg
ms.date: 11/04/2016
apiname:
- _getdcwd_dbg
- _wgetdcwd_dbg
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
- _getdcwd_dbg
- getdcwd_dbg
- _wgetdcwd_dbg
- wgetdcwd_dbg
helpviewer_keywords:
- working directory
- _getdcwd_dbg function
- wgetdcwd_dbg function
- current working directory
- getdcwd_dbg function
- _wgetdcwd_dbg function
- directories [C++], current working
ms.assetid: 266bf6f0-0417-497f-963d-2e0f306d9385
ms.openlocfilehash: 700cfe732dc390ca59a976694403bb3d91af5980
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331860"
---
# <a name="getdcwddbg-wgetdcwddbg"></a>_getdcwd_dbg, _wgetdcwd_dbg

Debuguj wersje [_getdcwd —, _wgetdcwd —](getdcwd-wgetdcwd.md) funkcji (dostępne tylko podczas debugowania).

## <a name="syntax"></a>Składnia

```C
char *_getdcwd_dbg(
   int drive,
   char *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wgetdcwd_dbg(
   int drive,
   wchar_t *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*drive*<br/>
Nazwa dysku.

*buffer*<br/>
Lokalizacja przechowywania dla ścieżki.

*maxlen*<br/>
Maksymalna długość ścieżki w znakach: **char** dla **_getdcwd_dbg —** i **wchar_t** dla **_wgetdcwd_dbg —**.

*blockType*<br/>
Żądany typ bloku pamięci: **_CLIENT_BLOCK** lub **_NORMAL_BLOCK**.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który zażądał operacji alokacji lub **NULL**.

*numer wiersza*<br/>
Numer wiersza w pliku źródłowym, gdzie zażądano operacji alokacji lub **NULL**.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do *buforu*. A **NULL** zwracana wartość wskazuje błąd, i **errno** ustawiono opcję **ENOMEM**, wskazujący, że jest za mało pamięci do przydzielenia *maxlen* bajtów (gdy **o wartości NULL** argument jest podawana jako *buforu*), lub **ERANGE**, wskazującą, czy ścieżka jest dłuższa niż *maxlen*  znaków. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Getdcwd_dbg —** i **_wgetdcwd_dbg —** funkcje są takie same jak **_getdcwd —** i **_wgetdcwd —** z tą różnicą, że gdy **_DEBUG** jest zdefiniowany, te funkcje używają wersji debugowania **— funkcja malloc** i **_malloc_dbg** można przydzielić pamięci, jeśli **NULL** jest przekazywany jako *buforu* parametru. Aby uzyskać więcej informacji, zobacz [_malloc_dbg](malloc-dbg.md).

Nie trzeba jawnie wywołać w większości przypadków te funkcje. Zamiast tego możesz zdefiniować **_CRTDBG_MAP_ALLOC** flagi. Gdy **_CRTDBG_MAP_ALLOC** jest zdefiniowany, wywołania **_getdcwd —** i **_wgetdcwd —** są mapowane ponownie do **_getdcwd_dbg —** i **_ wgetdcwd_dbg —**, odpowiednio, z *blockType* równa **_NORMAL_BLOCK**. Dzięki temu, nie trzeba jawnie wywołać te funkcje, chyba że chcesz oznaczyć bloki stosu jako **_CLIENT_BLOCK**. Aby uzyskać więcej informacji, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd_dbg**|**_getdcwd_dbg**|**_getdcwd_dbg**|**_wgetdcwd_dbg**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getdcwd_dbg**|\<crtdbg.h>|
|**_wgetdcwd_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[Wersje debugowania funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
