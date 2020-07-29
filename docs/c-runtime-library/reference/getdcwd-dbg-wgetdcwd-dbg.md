---
title: _getdcwd_dbg, _wgetdcwd_dbg
ms.date: 11/04/2016
api_name:
- _getdcwd_dbg
- _wgetdcwd_dbg
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
ms.openlocfilehash: a31617445ccb0640042be41ee4f710e528b9ceb7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229457"
---
# <a name="_getdcwd_dbg-_wgetdcwd_dbg"></a>_getdcwd_dbg, _wgetdcwd_dbg

Wersje debugowania [_getdcwd, funkcje _wgetdcwd](getdcwd-wgetdcwd.md) (dostępne tylko podczas debugowania).

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

*litera*<br/>
Nazwa stacji dysków.

*buforu*<br/>
Lokalizacja przechowywania dla ścieżki.

*MaxLen*<br/>
Maksymalna długość ścieżki w znakach: **`char`** dla **_getdcwd_dbg** i **`wchar_t`** **_wgetdcwd_dbg**.

*BlockType*<br/>
Żądany typ bloku pamięci: **_CLIENT_BLOCK** lub **_NORMAL_BLOCK**.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który zażądał operacji alokacji lub **ma wartość null**.

*LineNumber*<br/>
Numer wiersza w pliku źródłowym, w którym zażądano operacji alokacji lub **ma wartość null**.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do *buforu*. Wartość zwracana **null** wskazuje na błąd, a **errno** jest ustawiona na **ENOMEM**, co oznacza, że za mało pamięci do przydzielenia bajtów *MaxLen* (gdy argument o **wartości null** jest podawany jako *bufor*) lub do **ERANGE**, co oznacza, że ścieżka jest dłuższa niż *MaxLen* znaków. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Getdcwd_dbg** i **_wgetdcwd_dbg** funkcje są takie same jak **_getdcwd** i **_wgetdcwd** , z wyjątkiem tego, że w przypadku zdefiniowania **_DEBUG** te funkcje używają wersji i **_Malloc_dbg** **debugowania w celu** przydzielenia pamięci, jeśli **wartość null** jest przenoszona jako parametr *buforu* . Aby uzyskać więcej informacji, zobacz [_malloc_dbg](malloc-dbg.md).

Nie trzeba jawnie wywoływać tych funkcji w większości przypadków. Zamiast tego można zdefiniować flagę **_CRTDBG_MAP_ALLOC** . Gdy **_CRTDBG_MAP_ALLOC** jest zdefiniowany, wywołania **_getdcwd** i **_wgetdcwd** są ponownie mapowane do **_getdcwd_dbg** i **_wgetdcwd_dbg**, z ustawieniem *BlockType* na **_NORMAL_BLOCK**. W ten sposób nie trzeba wywoływać tych funkcji jawnie, chyba że chcesz oznaczyć bloki sterty jako **_CLIENT_BLOCK**. Aby uzyskać więcej informacji, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd_dbg**|**_getdcwd_dbg**|**_getdcwd_dbg**|**_wgetdcwd_dbg**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getdcwd_dbg**|\<crtdbg.h>|
|**_wgetdcwd_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[Kontrolka katalogu](../../c-runtime-library/directory-control.md)<br/>
[Wersja debugowania funkcji alokacji stosu](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
