---
title: _tempnam_dbg, _wtempnam_dbg
ms.date: 11/04/2016
apiname:
- _wtempnam_dbg
- _tempnam_dbg
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
- wtempnam_dbg
- tempnam_dbg
- _tempnam_dbg
- _wtempnam_dbg
helpviewer_keywords:
- file names [C++], creating temporary
- tempnam_dbg function
- temporary files, creating
- file names [C++], temporary
- wtempnam_dbg function
- _tempnam_dbg function
- _wtempnam_dbg function
ms.assetid: e3760bb4-bb01-4808-b689-2c45af56a170
ms.openlocfilehash: 804c8ad1f17c6ee1df563cafc69ee7aef494d1cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596462"
---
# <a name="tempnamdbg-wtempnamdbg"></a>_tempnam_dbg, _wtempnam_dbg

Funkcja wersje [_tempnam —, _wtempnam —, tmpnam —, _wtmpnam —](tempnam-wtempnam-tmpnam-wtmpnam.md) które korzystają z wersji debugowania **— funkcja malloc**, **_malloc_dbg**.

## <a name="syntax"></a>Składnia

```C
char *_tempnam_dbg(
   const char *dir,
   const char *prefix,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wtempnam_dbg(
   const wchar_t *dir,
   const wchar_t *prefix,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*dir*<br/>
Ścieżka użyte w nazwie pliku, jeśli zmienna środowiskowa nie TMP lub TMP nie jest prawidłowym katalogiem.

*Prefiks*<br/>
Ciąg, który będzie pre oczekującego nazw zwróconych przez **_tempnam —**.

*blockType*<br/>
Żądany typ bloku pamięci: **_CLIENT_BLOCK** lub **_NORMAL_BLOCK**.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który zażądał operacji alokacji lub **NULL**.

*numer wiersza*<br/>
Numer wiersza w pliku źródłowym, gdzie zażądano operacji alokacji lub **NULL**.

## <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca wskaźnik do nazwy wygenerowanej lub **NULL** w przypadku awarii. Błąd może wystąpić, jeśli ma nieprawidłową nazwę katalogu określonego w zmiennej środowiskowej TMP i w *dir* parametru.

> [!NOTE]
> **bezpłatne** (lub **free_dbg —**) muszą zostać wywołane dla wskaźników przydzielonej przez **_tempnam_dbg —** i **_wtempnam_dbg —**.

## <a name="remarks"></a>Uwagi

**_Tempnam_dbg —** i **_wtempnam_dbg —** funkcje są takie same jak **_tempnam —** i **_wtempnam —** z tą różnicą, że gdy **_DEBUG** jest zdefiniowany, te funkcje używają wersji debugowania **— funkcja malloc** i **_malloc_dbg**, można przydzielić pamięci, jeśli **NULL** jest przekazywany jako pierwszy parametr. Aby uzyskać więcej informacji, zobacz [_malloc_dbg](malloc-dbg.md).

Nie trzeba jawnie wywołać w większości przypadków te funkcje. Zamiast tego można określić flagę **_CRTDBG_MAP_ALLOC**. Gdy **_CRTDBG_MAP_ALLOC** jest zdefiniowany, wywołania **_tempnam —** i **_wtempnam —** są mapowane ponownie do **_tempnam_dbg —** i **_ wtempnam_dbg —**, odpowiednio, z *blockType* równa **_NORMAL_BLOCK**. Dzięki temu, nie trzeba jawnie wywołać te funkcje, chyba że chcesz oznaczyć bloki stosu jako **_CLIENT_BLOCK**. Aby uzyskać więcej informacji, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttempnam_dbg**|**_tempnam_dbg**|**_tempnam_dbg**|**_wtempnam_dbg**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_tempnam_dbg —**, **_wtempnam_dbg —**|\<crtdbg.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[Wersje debugowania funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
