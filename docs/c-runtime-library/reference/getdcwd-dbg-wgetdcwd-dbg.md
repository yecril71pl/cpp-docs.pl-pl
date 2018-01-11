---
title: "_getdcwd_dbg —, _wgetdcwd_dbg — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- working directory
- _getdcwd_dbg function
- wgetdcwd_dbg function
- current working directory
- getdcwd_dbg function
- _wgetdcwd_dbg function
- directories [C++], current working
ms.assetid: 266bf6f0-0417-497f-963d-2e0f306d9385
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2009a88f522b60305c6f910a155faa8e675e2147
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="getdcwddbg-wgetdcwddbg"></a>_getdcwd_dbg, _wgetdcwd_dbg
Wersja debugowania [_getdcwd —, _wgetdcwd —](../../c-runtime-library/reference/getdcwd-wgetdcwd.md) funkcje (Ta funkcja jest dostępna tylko podczas debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `drive`  
 Nazwa dysku.  
  
 `buffer`  
 Lokalizacja magazynu dla ścieżki.  
  
 `maxlen`  
 Maksymalna długość ścieżki w znakach: `char` dla `_getdcwd_dbg` i `wchar_t` dla `_wgetdcwd_dbg`.  
  
 `blockType`  
 Żądany typ bloku pamięci: `_CLIENT_BLOCK` lub `_NORMAL_BLOCK`.  
  
 `filename`  
 Wskaźnik do nazwy pliku źródłowego, który żądanej operacji alokacji lub `NULL`.  
  
 `linenumber`  
 Numer w pliku źródłowym, której zażądano operacji alokacji wiersza lub `NULL`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do `buffer`. A `NULL` zwracana wartość wskazuje błąd i `errno` ma ustawioną opcję `ENOMEM`, wskazująca, że jest za mało pamięci do przydzielenia `maxlen` bajtów (gdy `NULL` argument jest podawana jako `buffer`), lub `ERANGE`, wskazujący, że ścieżka jest dłuższa niż `maxlen` znaków. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `_getdcwd_dbg` i `_wgetdcwd_dbg` funkcje są takie same jak `_getdcwd` i `_wgetdcwd` z wyjątkiem tego, kiedy `_DEBUG` jest zdefiniowana, te funkcje przy użyciu wersji debugowania `malloc` i `_malloc_dbg` można przydzielić pamięci, jeśli `NULL` jest przekazywany jako `buffer` parametru. Aby uzyskać więcej informacji, zobacz [_malloc_dbg —](../../c-runtime-library/reference/malloc-dbg.md).  
  
 Nie trzeba jawnie wywołana w większości przypadków te funkcje. Zamiast tego można zdefiniować `_CRTDBG_MAP_ALLOC` flagi. Gdy `_CRTDBG_MAP_ALLOC` jest zdefiniowany, wywołań `_getdcwd` i `_wgetdcwd` są mapowane ponownie do `_getdcwd_dbg` i `_wgetdcwd_dbg`odpowiednio z `blockType` ustawioną `_NORMAL_BLOCK`. W związku z tym nie trzeba jawnie wywoływać te funkcje, chyba że chcesz oznaczyć bloki sterty jako `_CLIENT_BLOCK`. Aby uzyskać więcej informacji, zobacz [typów bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tgetdcwd_dbg`|`_getdcwd_dbg`|`_getdcwd_dbg`|`_wgetdcwd_dbg`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_getdcwd_dbg`|\<crtdbg.h >|  
|`_wgetdcwd_dbg`|\<crtdbg.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [_getdcwd —, _wgetdcwd —](../../c-runtime-library/reference/getdcwd-wgetdcwd.md)   
 [Kontrola katalogu](../../c-runtime-library/directory-control.md)   
 [Wersja debugowania funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)