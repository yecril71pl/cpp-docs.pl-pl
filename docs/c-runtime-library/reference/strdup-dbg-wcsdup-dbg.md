---
title: _strdup_dbg, _wcsdup_dbg
ms.date: 11/04/2016
apiname:
- _strdup_dbg
- _wcsdup_dbg
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
- _wcsdup_dbg
- strdup_dbg
- _strdup_dbg
- wcsdup_dbg
helpviewer_keywords:
- _wcsdup_dbg function
- stdup_dbg function
- copying strings
- duplicating strings
- strings [C++], copying
- strings [C++], duplicating
- _strdup_dbg function
- wcsdup_dbg function
ms.assetid: 681db70c-d124-43ab-b83e-5eeea9035097
ms.openlocfilehash: 3092c27df1e39c7b719f6e7037efa202d29c9e81
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353892"
---
# <a name="strdupdbg-wcsdupdbg"></a>_strdup_dbg, _wcsdup_dbg

Wersje [_strdup — i _wcsdup —](strdup-wcsdup-mbsdup.md) które korzystają z wersji debugowania **— funkcja malloc**.

## <a name="syntax"></a>Składnia

```C
char *_strdup_dbg(
   const char *strSource,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wcsdup_dbg(
   const wchar_t *strSource,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*strSource*<br/>
Ciąg źródłowy zakończony wartością null.

*blockType*<br/>
Żądany typ bloku pamięci: **_CLIENT_BLOCK** lub **_NORMAL_BLOCK**.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który zażądał operacji alokacji lub **NULL**.

*numer wiersza*<br/>
Numer wiersza w pliku źródłowym, gdzie zażądano operacji alokacji lub **NULL**.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do lokalizacji przechowywania skopiowany ciąg lub **NULL** Jeśli nie można przydzielić pamięci masowej.

## <a name="remarks"></a>Uwagi

**_Strdup_dbg —** i **_wcsdup_dbg —** funkcje są takie same jak **_strdup —** i **_wcsdup —** z tą różnicą, że gdy **_ DEBUGOWANIE** jest zdefiniowany, te funkcje używają wersji debugowania **— funkcja malloc**, **_malloc_dbg**, można przydzielić pamięci dla zduplikowane parametry. Instrukcje dotyczące debugowania funkcji **_malloc_dbg**, zobacz [_malloc_dbg](malloc-dbg.md).

Nie trzeba jawnie wywołać w większości przypadków te funkcje. Zamiast tego można określić flagę **_CRTDBG_MAP_ALLOC**. Gdy **_CRTDBG_MAP_ALLOC** jest zdefiniowany, wywołania **_strdup —** i **_wcsdup —** są mapowane ponownie do **_strdup_dbg —** i **_ wcsdup_dbg —**, odpowiednio, z *blockType* równa **_NORMAL_BLOCK**. Dzięki temu, nie trzeba jawnie wywołać te funkcje, chyba że chcesz oznaczyć bloki stosu jako **_CLIENT_BLOCK**. Aby uzyskać więcej informacji na temat typów bloków, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsdup_dbg**|**_strdup_dbg**|**_mbsdup —**|**_wcsdup_dbg**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strdup_dbg**, **_wcsdup_dbg**|\<crtdbg.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strdup, _wcsdup, _mbsdup](strdup-wcsdup-mbsdup.md)<br/>
[Wersje debugowania funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
