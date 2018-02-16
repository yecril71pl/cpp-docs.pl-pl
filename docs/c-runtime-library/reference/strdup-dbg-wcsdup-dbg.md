---
title: _strdup_dbg, _wcsdup_dbg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7865335eb5b483ca722e06c31b935751c92c80bd
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="strdupdbg-wcsdupdbg"></a>_strdup_dbg, _wcsdup_dbg
Wersje [_strdup — i _wcsdup —](../../c-runtime-library/reference/strdup-wcsdup-mbsdup.md) korzystające z wersji do debugowania `malloc`.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `strSource`  
 Ciąg źródłowy zerem.  
  
 `blockType`  
 Żądany typ bloku pamięci: `_CLIENT_BLOCK` lub `_NORMAL_BLOCK`.  
  
 `filename`  
 Wskaźnik do nazwy pliku, który jest Żądana operacja alokacji ani mieć wartości NULL.  
  
 `linenumber`  
 Numer wiersza na plik źródłowy, której zażądano operacji alokacji, lub wartość NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji zwraca wskaźnik do lokalizacji magazynu dla skopiowanego ciągu lub `NULL` , jeśli nie można przydzielić pamięci masowej.  
  
## <a name="remarks"></a>Uwagi  
 `_strdup_dbg` i `_wcsdup_dbg` funkcje są takie same jak `_strdup` i `_wcsdup` z wyjątkiem tego, kiedy `_DEBUG` jest zdefiniowana, te funkcje przy użyciu wersji debugowania `malloc`, `_malloc_dbg`, można przydzielić pamięci dla Zduplikowane parametry. Aby uzyskać informacje dotyczące debugowania funkcji `_malloc_dbg`, zobacz [_malloc_dbg —](../../c-runtime-library/reference/malloc-dbg.md).  
  
 Nie trzeba jawnie wywołana w większości przypadków te funkcje. Zamiast tego można określić flagę `_CRTDBG_MAP_ALLOC`. Gdy `_CRTDBG_MAP_ALLOC` jest zdefiniowany, wywołań `_strdup` i `_wcsdup` są mapowane ponownie do `_strdup_dbg` i `_wcsdup_dbg`odpowiednio z `blockType` ustawioną `_NORMAL_BLOCK`. W związku z tym nie trzeba jawnie wywoływać te funkcje, chyba że chcesz oznaczyć bloki sterty jako `_CLIENT_BLOCK`. Aby uzyskać więcej informacji o typach bloku, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsdup_dbg`|`_strdup_dbg`|`_mbsdup`|`_wcsdup_dbg`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_strdup_dbg`, `_wcsdup_dbg`|\<crtdbg.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Debuguj wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)   
 [_strdup, _wcsdup, _mbsdup](../../c-runtime-library/reference/strdup-wcsdup-mbsdup.md)   
 [Wersja debugowania funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)