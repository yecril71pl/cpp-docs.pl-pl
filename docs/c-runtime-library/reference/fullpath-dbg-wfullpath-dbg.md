---
title: "_fullpath_dbg —, _wfullpath_dbg — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- _fullpath_dbg function
- relative file paths
- absolute paths
- fullpath_dbg function
- _wfullpath_dbg function
- wfullpath_dbg function
ms.assetid: 81f72f85-07da-4f5c-866a-598e0fb03f6b
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d4a89e5599823bb60d65f0845044185fbbe560dd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fullpathdbg-wfullpathdbg"></a>_fullpath_dbg, _wfullpath_dbg
Wersje [_fullpath —, _wfullpath —](../../c-runtime-library/reference/fullpath-wfullpath.md) korzystające z wersji do debugowania `malloc` można przydzielić pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `absPath`  
 Wskaźnik do bufor zawierający nazwę ścieżki bezwzględnej lub pełnego lub `NULL`.  
  
 `relPath`  
 Nazwa ścieżki względnej.  
  
 `maxLength`  
 Maksymalna długość buforu nazwy ścieżkę bezwzględną (`absPath`). Jest to długość w bajtach dla `_fullpath` , ale w znaki dwubajtowe (`wchar_t`) dla `_wfullpath`.  
  
 `blockType`  
 Żądany typ bloku pamięci: `_CLIENT_BLOCK` lub `_NORMAL_BLOCK`.  
  
 `filename`  
 Wskaźnik do nazwy pliku źródłowego, który żądanej operacji alokacji lub `NULL`.  
  
 `linenumber`  
 Numer w pliku źródłowym, której zażądano operacji alokacji wiersza lub `NULL`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda funkcja zwraca wskaźnik do buforu, zawierający nazwę ścieżki bezwzględnej (`absPath`). Jeśli błąd (na przykład, jeśli wartość przekazano `relPath` zawiera literę dysku, który jest nieprawidłowy lub nie można znaleźć, lub jeśli długość nazwy utworzonego ścieżkę bezwzględną (`absPath`) jest większa niż `maxLength`) funkcja zwraca `NULL`.  
  
## <a name="remarks"></a>Uwagi  
 `_fullpath_dbg` i `_wfullpath_dbg` funkcje są takie same jak `_fullpath` i `_wfullpath` z wyjątkiem tego, gdy `_DEBUG` jest zdefiniowane, te funkcje przy użyciu wersji debugowania `malloc`, `_malloc_dbg`, można przydzielić pamięci, jeśli ma wartość NULL przekazany jako pierwszym parametrem. Aby uzyskać informacje dotyczące debugowania funkcji `_malloc_dbg`, zobacz [_malloc_dbg —](../../c-runtime-library/reference/malloc-dbg.md).  
  
 Nie trzeba jawnie wywołana w większości przypadków te funkcje. Zamiast tego można zdefiniować `_CRTDBG_MAP_ALLOC` flagi. Gdy `_CRTDBG_MAP_ALLOC` jest zdefiniowany, wywołań `_fullpath` i `_wfullpath` są mapowane ponownie do `_fullpath_dbg` i `_wfullpath_dbg`odpowiednio z `blockType` ustawioną `_NORMAL_BLOCK`. W związku z tym nie trzeba jawnie wywoływać te funkcje, chyba że chcesz oznaczyć bloki sterty jako `_CLIENT_BLOCK`. Aby uzyskać więcej informacji, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfullpath_dbg`|`_fullpath_dbg`|`_fullpath_dbg`|`_wfullpath_dbg`|  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`_fullpath_dbg`|\<crtdbg.h >|  
|`_wfullpath_dbg`|\<crtdbg.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa plików](../../c-runtime-library/file-handling.md)   
 [_fullpath —, _wfullpath —](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [Wersja debugowania funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)