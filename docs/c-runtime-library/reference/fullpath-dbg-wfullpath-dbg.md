---
title: _fullpath_dbg, _wfullpath_dbg
ms.date: 11/04/2016
api_name:
- _wfullpath_dbg
- _fullpath_dbg
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
ms.openlocfilehash: 9271e26bcf4a78ff8d2e4fcf108f1e483c22c1d7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956311"
---
# <a name="_fullpath_dbg-_wfullpath_dbg"></a>_fullpath_dbg, _wfullpath_dbg

Wersje programu [_fullpath, _wfullpath](fullpath-wfullpath.md) , które używają wersji do debugowania programu **malloc** do przydzielenia pamięci.

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
Wskaźnik do buforu zawierającego bezwzględną lub pełną nazwę ścieżki lub **wartość null**.

*relPath*<br/>
Nazwa ścieżki względnej.

*maxLength*<br/>
Maksymalna długość buforu nazw ścieżek bezwzględnych (*absPath*). Ta długość jest wyrażona w bajtach dla **_fullpath** , ale w postaci szerokich znaków (**wchar_t**) dla **_wfullpath**.

*BlockType*<br/>
Żądany typ bloku pamięci: **_CLIENT_BLOCK** lub **_NORMAL_BLOCK**.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który żądał operacji alokacji lub **ma wartość null**.

*LineNumber*<br/>
Numer wiersza w pliku źródłowym, w którym zażądano operacji alokacji lub **ma wartość null**.

## <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca wskaźnik do buforu zawierającego bezwzględną nazwę ścieżki (*absPath*). Jeśli wystąpi błąd (na przykład w przypadku, gdy wartość przeniesiona w *relPath* zawiera literę dysku, która jest nieprawidłowa lub nie można jej znaleźć lub jeśli długość utworzonej ścieżki bezwzględnej (*absPath*) jest większa niż *MaxLength*), funkcja zwraca  **Wartość NULL**.

## <a name="remarks"></a>Uwagi

Funkcje **_fullpath_dbg** i **_wfullpath_dbg** są identyczne z **_fullpath** i **_wfullpath** , z tą różnicą, że w przypadku zdefiniowania elementu **_DEBUG** te funkcje korzystają z wersji, która jest debugowana **,** **_malloc_dbg**, w celu przydzielenia pamięci, jeśli **wartość null** jest przenoszona jako pierwszy parametr. Aby uzyskać informacje na temat funkcji debugowania **_malloc_dbg**, zobacz [_malloc_dbg](malloc-dbg.md).

Nie trzeba jawnie wywoływać tych funkcji w większości przypadków. Zamiast tego można zdefiniować flagę **_CRTDBG_MAP_ALLOC** . Gdy **_CRTDBG_MAP_ALLOC** jest zdefiniowany, wywołania **_fullpath** i **_wfullpath** są ponownie mapowane odpowiednio do **_fullpath_dbg** i **_wfullpath_dbg**, z atrybutem *BlockType* ustawionym na wartość **_NORMAL_BLOCK**. W ten sposób nie trzeba wywoływać tych funkcji jawnie, chyba że chcesz oznaczyć bloki sterty jako **_CLIENT_BLOCK**. Aby uzyskać więcej informacji, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath_dbg**|**_fullpath_dbg**|**_fullpath_dbg**|**_wfullpath_dbg**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fullpath_dbg**|\<crtdbg.h>|
|**_wfullpath_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[Wersje debugowania funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
