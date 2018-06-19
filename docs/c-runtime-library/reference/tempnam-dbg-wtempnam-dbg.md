---
title: _tempnam_dbg —, _wtempnam_dbg — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- file names [C++], creating temporary
- tempnam_dbg function
- temporary files, creating
- file names [C++], temporary
- wtempnam_dbg function
- _tempnam_dbg function
- _wtempnam_dbg function
ms.assetid: e3760bb4-bb01-4808-b689-2c45af56a170
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8509d9f4b8be5771abc7dfb3d4deacc9ae61494
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412052"
---
# <a name="tempnamdbg-wtempnamdbg"></a>_tempnam_dbg, _wtempnam_dbg

Funkcja wersji [_tempnam —, _wtempnam —, tmpnam —, _wtmpnam —](tempnam-wtempnam-tmpnam-wtmpnam.md) korzystające z wersji do debugowania **— funkcja malloc**, **_malloc_dbg —**.

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

*Dir*<br/>
Ścieżka używana w nazwie pliku, jeśli istnieje zmienna środowiskowa nie TMP lub TMP nie jest prawidłowym katalogiem.

*Prefiks*<br/>
Ciąg, który będzie pre oczekującego na nazwy zwrócony przez **_tempnam —**.

*blockType*<br/>
Żądany typ bloku pamięci: **_client_block —** lub **_normal_block —**.

*Nazwa pliku*<br/>
Wskaźnik do nazwy pliku źródłowego, który żądanej operacji alokacji lub **NULL**.

*numer wiersza*<br/>
Numer w pliku źródłowym, której zażądano operacji alokacji wiersza lub **NULL**.

## <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca wskaźnik do Nazwa wygenerowana lub **NULL** w przypadku awarii. Błąd może wystąpić, jeśli istnieje nieprawidłową nazwę katalogu określonym w zmiennej środowiskowej TMP i w *dir* parametru.

> [!NOTE]
> **bezpłatne** (lub **free_dbg —**) musi być wywoływany dla wskaźników przydzielonej przez **_tempnam_dbg —** i **_wtempnam_dbg —**.

## <a name="remarks"></a>Uwagi

**_Tempnam_dbg —** i **_wtempnam_dbg —** funkcje są takie same jak **_tempnam —** i **_wtempnam —** z wyjątkiem tego, kiedy **_DEBUG** jest zdefiniowany, te funkcje przy użyciu wersji debugowania **— funkcja malloc** i **_malloc_dbg —**, można przydzielić pamięci, jeśli **NULL** jest przekazany jako pierwszym parametrem. Aby uzyskać więcej informacji, zobacz [_malloc_dbg —](malloc-dbg.md).

Nie trzeba jawnie wywołana w większości przypadków te funkcje. Zamiast tego można określić flagę **_crtdbg_map_alloc —**. Gdy **_crtdbg_map_alloc —** jest zdefiniowany, wywołań **_tempnam —** i **_wtempnam —** są mapowane ponownie do **_tempnam_dbg —** i **_ wtempnam_dbg —** odpowiednio z *blockType* ustawioną **_normal_block —**. W związku z tym nie trzeba jawnie wywoływać te funkcje, chyba że chcesz oznaczyć bloki sterty jako **_client_block —**. Aby uzyskać więcej informacji, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttempnam_dbg**|**_tempnam_dbg**|**_tempnam_dbg**|**_wtempnam_dbg**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_tempnam_dbg —**, **_wtempnam_dbg —**|\<crtdbg.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[Wersja debugowania funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
