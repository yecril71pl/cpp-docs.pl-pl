---
title: "_dupenv_s_dbg —, _wdupenv_s_dbg — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _dupenv_s_dbg
- _wdupenv_s_dbg
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
- _tdupenv_s_dbg
- _dupenv_s_dbg
- _wdupenv_s_dbg
dev_langs: C++
helpviewer_keywords:
- _tdupenv_s_dbg function
- dupenv_s_dbg function
- _wdupenv_s_dbg function
- environment variables
- tdupenv_s_dbg function
- wdupenv_s_dbg function
- _dupenv_s_dbg function
ms.assetid: e3d81148-e24e-46d0-a21d-fd87b5e6256c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 72412790fc7bd71d25d0a77fdb0ede8d7b9e31a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="dupenvsdbg-wdupenvsdbg"></a>_dupenv_s_dbg, _wdupenv_s_dbg
Pobieranie wartości z bieżącego środowiska.  Wersje [_dupenv_s —, _wdupenv_s —](../../c-runtime-library/reference/dupenv-s-wdupenv-s.md) który przydzielić pamięci z [_malloc_dbg —](../../c-runtime-library/reference/malloc-dbg.md) o podanie dodatkowych informacji debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _dupenv_s_dbg(  
   char **buffer,  
   size_t *numberOfElements,  
   const char *varname,  
   int blockType,  
   const char *filename,  
   int linenumber  
);  
errno_t _wdupenv_s_dbg(  
   wchar_t **buffer,  
   size_t * numberOfElements,  
   const wchar_t *varname,  
   int blockType,  
   const char *filename,  
   int linenumber  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Bufor do przechowywania wartość zmiennej.  
  
 `numberOfElements`  
 Rozmiar `buffer`.  
  
 `varname`  
 Nazwa zmiennej środowiskowej.  
  
 `blockType`  
 Żądany typ bloku pamięci: `_CLIENT_BLOCK` lub `_NORMAL_BLOCK`.  
  
 `filename`  
 Wskaźnik do nazwy pliku źródłowego lub `NULL`.  
  
 `linenumber`  
 Numer wiersza na pliku źródłowego lub `NULL`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero w przypadku powodzenia, kod błędu w przypadku awarii.  
  
 Te funkcje walidację ich parametrów; Jeśli `buffer` lub `varname` jest `NULL`, zgodnie z opisem w wywołaniu program obsługi nieprawidłowych parametrów [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, Ustaw funkcje `errno` do `EINVAL` i zwracać `EINVAL`.  
  
 Jeśli te funkcje nie może przydzielić wystarczającej ilości pamięci, sami ustawiają `buffer` do `NULL` i `numberOfElements` 0 i powrotu `ENOMEM`.  
  
## <a name="remarks"></a>Uwagi  
 `_dupenv_s_dbg` i `_wdupenv_s_dbg` funkcje są takie same jak `_dupenv_s` i `_wdupenv_s` z wyjątkiem tego, kiedy `_DEBUG` jest zdefiniowana, te funkcje przy użyciu wersji debugowania [— funkcja malloc](../../c-runtime-library/reference/malloc.md), [_ malloc_dbg —](../../c-runtime-library/reference/malloc-dbg.md), można przydzielić pamięci dla wartości zmiennej środowiskowej. Aby uzyskać informacje dotyczące debugowania funkcji `_malloc_dbg`, zobacz [_malloc_dbg —](../../c-runtime-library/reference/malloc-dbg.md).  
  
 Nie trzeba jawnie wywołana w większości przypadków te funkcje. Zamiast tego można określić flagę `_CRTDBG_MAP_ALLOC`. Gdy `_CRTDBG_MAP_ALLOC` jest zdefiniowany, wywołań `_dupenv_s` i `_wdupenv_s` są mapowane ponownie do `_dupenv_s_dbg` i `_wdupenv_s_dbg`odpowiednio z `blockType` ustawioną `_NORMAL_BLOCK`. W związku z tym nie trzeba jawnie wywoływać te funkcje, chyba że chcesz oznaczyć bloki sterty jako `_CLIENT_BLOCK`. Aby uzyskać więcej informacji o typach bloku, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tdupenv_s_dbg`|`_dupenv_s_dbg`|`_dupenv_s_dbg`|`_wdupenv_s_dbg`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_dupenv_s_dbg`|\<crtdbg.h >|  
|`_wdupenv_s_dbg`|\<crtdbg.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_dupenv_s_dbg.c  
#include  <stdlib.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
   char *pValue;  
   size_t len;  
   errno_t err = _dupenv_s_dbg( &pValue, &len, "pathext",  
      _NORMAL_BLOCK, __FILE__, __LINE__ );  
   if ( err ) return -1;  
   printf( "pathext = %s\n", pValue );  
   free( pValue );  
   err = _dupenv_s_dbg( &pValue, &len, "nonexistentvariable",  
      _NORMAL_BLOCK, __FILE__, __LINE__ );  
   if ( err ) return -1;  
   printf( "nonexistentvariable = %s\n", pValue );  
   free( pValue ); // It's OK to call free with NULL  
}  
```  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl  
nonexistentvariable = (null)  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Proces i kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)   
 [Stałe środowiska](../../c-runtime-library/environmental-constants.md)   
 [getenv_s —, _wgetenv_s —](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [_putenv_s —, _wputenv_s —](../../c-runtime-library/reference/putenv-s-wputenv-s.md)