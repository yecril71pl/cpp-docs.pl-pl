---
title: _fullpath_dbg, _wfullpath_dbg
ms.date: 11/04/2016
apiname:
- _wfullpath_dbg
- _fullpath_dbg
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
- wfullpath_dbg
- _wfullpath_dbg
- _fullpath_dbg
- fullpath_dbg
helpviewer_keywords:
- _fullpath_dbg function
- relative file paths
- absolute paths
- fullpath_dbg function
- _wfullpath_dbg function
- wfullpath_dbg function
ms.assetid: 81f72f85-07da-4f5c-866a-598e0fb03f6b
ms.openlocfilehash: b84c5b77d0a9bfb298d4c597e372cd39a92441f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332952"
---
# <a name="fullpathdbg-wfullpathdbg"></a>_fullpath_dbg, _wfullpath_dbg

Wersje [_fullpath —, _wfullpath —](fullpath-wfullpath.md) które korzystają z wersji debugowania **— funkcja malloc** można przydzielić pamięci.

## <a name="syntax"></a>Składnia

```C
char *_fullpath_dbg(
   char *absPath,
   const char *relPath,
   size_t maxLength,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wfullpath_dbg(
   wchar_t *absPath,
   const wchar_t *relPath,
   size_t maxLength,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*absPath*<br/>
Wskaźnik do buforu, zawierające nazwę ścieżki bezwzględnej lub pełnego lub **NULL**.

*relPath*<br/>
Nazwa ścieżki względnej.

*maxLength*<br/>
Maksymalna długość buforu nazwy ścieżkę bezwzględną (*absPath*). To długość jest w bajtach dla **_fullpath —** , ale w znaków dwubajtowych (**wchar_t**) dla **_wfullpath —**.

*blockType*<br/>
Żądany typ bloku pamięci: **_CLIENT_BLOCK** lub **_NORMAL_BLOCK**.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który zażądał operacji alokacji lub **NULL**.

*numer wiersza*<br/>
Numer wiersza w pliku źródłowym, gdzie zażądano operacji alokacji lub **NULL**.

## <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca wskaźnik do buforu, zawierający nazwę ścieżkę bezwzględną (*absPath*). Jeśli wystąpi błąd (na przykład, jeśli wartość przekazywana w *relPath* zawiera literę dysku, który jest nieprawidłowy lub nie można odnaleźć, lub jeśli długość nazwy utworzona ścieżka bezwzględna (*absPath*) jest większa niż *maxLength*) funkcja zwraca **NULL**.

## <a name="remarks"></a>Uwagi

**_Fullpath_dbg —** i **_wfullpath_dbg —** funkcje są takie same jak **_fullpath —** i **_wfullpath —** z tą różnicą, że gdy **_DEBUG** jest zdefiniowany, te funkcje używają wersji debugowania **— funkcja malloc**, **_malloc_dbg**, można przydzielić pamięci, jeśli **NULL** jest przekazywany jako pierwszy parametr. Instrukcje dotyczące debugowania funkcji **_malloc_dbg**, zobacz [_malloc_dbg](malloc-dbg.md).

Nie trzeba jawnie wywołać w większości przypadków te funkcje. Zamiast tego możesz zdefiniować **_CRTDBG_MAP_ALLOC** flagi. Gdy **_CRTDBG_MAP_ALLOC** jest zdefiniowany, wywołania **_fullpath —** i **_wfullpath —** są mapowane ponownie do **_fullpath_dbg —** i **_wfullpath_dbg —**, odpowiednio, z *blockType* równa **_NORMAL_BLOCK**. Dzięki temu, nie trzeba jawnie wywołać te funkcje, chyba że chcesz oznaczyć bloki stosu jako **_CLIENT_BLOCK**. Aby uzyskać więcej informacji, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath_dbg**|**_fullpath_dbg**|**_fullpath_dbg**|**_wfullpath_dbg**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fullpath_dbg**|\<crtdbg.h>|
|**_wfullpath_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[Wersje debugowania funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
