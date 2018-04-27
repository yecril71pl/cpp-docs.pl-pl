---
title: _getcwd_dbg —, _wgetcwd_dbg — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wgetcwd_dbg
- _getcwd_dbg
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getcwd_dbg
- _wgetcwd_dbg
- getcwd_dbg
- wgetcwd_dbg
dev_langs:
- C++
helpviewer_keywords:
- wgetcwd_dbg function
- working directory
- _getcwd_dbg function
- getcwd_dbg function
- current working directory
- _wgetcwd_dbg function
- directories [C++], current working
ms.assetid: 8d5d151f-d844-4aa6-a28c-1c11a22dc00d
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 59bf95e03891f787ec8271d35d4b922d8641dda2
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="getcwddbg-wgetcwddbg"></a>_getcwd_dbg, _wgetcwd_dbg

Wersja debugowania [_getcwd —, _wgetcwd —](getcwd-wgetcwd.md) funkcje (Ta funkcja jest dostępna tylko podczas debugowania).

## <a name="syntax"></a>Składnia

```C
char *_getcwd_dbg(
   char *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wgetcwd_dbg(
   wchar_t *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Lokalizacja magazynu dla ścieżki.

*maxlen*<br/>
Maksymalna długość ścieżki w znakach: **char** dla **_getcwd_dbg —** i **wchar_t** dla **_wgetcwd_dbg —**.

*blockType*<br/>
Żądany typ bloku pamięci: **_client_block —** lub **_normal_block —**.

*Nazwa pliku*<br/>
Wskaźnik do nazwy pliku źródłowego, który żądanej operacji alokacji lub **NULL**.

*numer wiersza*<br/>
Numer w pliku źródłowym, której zażądano operacji alokacji wiersza lub **NULL**.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do *buforu*. A **NULL** zwracana wartość wskazuje błąd i **errno** ma ustawioną opcję **enomem —**, wskazujące, że jest za mało pamięci do przydzielenia *maxlen* bajtów (gdy **NULL** argument jest podawana jako *buforu*), lub do **erange —**, wskazujący, że ścieżka jest dłuższa niż *maxlen*  znaków.

Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Getcwd_dbg —** i **_wgetcwd_dbg —** funkcje są takie same jak **_getcwd —** i **_wgetcwd —** z wyjątkiem tego, kiedy **_ DEBUGOWANIE** jest zdefiniowany, te funkcje przy użyciu wersji debugowania **— funkcja malloc** i **_malloc_dbg —** można przydzielić pamięci, jeśli **NULL** jest przekazywany jako pierwszy parametr. Aby uzyskać więcej informacji, zobacz [_malloc_dbg —](malloc-dbg.md).

Nie trzeba jawnie wywołana w większości przypadków te funkcje. Zamiast tego można zdefiniować **_crtdbg_map_alloc —** flagi. Gdy **_crtdbg_map_alloc —** jest zdefiniowany, wywołań **_getcwd —** i **_wgetcwd —** są mapowane ponownie do **_getcwd_dbg —** i **_ wgetcwd_dbg —**odpowiednio z *blockType* ustawioną **_normal_block —**. W związku z tym nie trzeba jawnie wywoływać te funkcje, chyba że chcesz oznaczyć bloki sterty jako **_client_block —**. Aby uzyskać więcej informacji, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).

## <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd_dbg**|**_getcwd_dbg**|**_getcwd_dbg**|**_wgetcwd_dbg**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getcwd_dbg**|\<crtdbg.h>|
|**_wgetcwd_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[Wersja debugowania funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
