---
title: "_makepath —, _wmakepath — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _makepath
- _wmakepath
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wmakepath
- _tmakepath
- makepath
- tmakepath
- wmakepath
- _makepath
dev_langs:
- C++
helpviewer_keywords:
- _makepath function
- wmakepath function
- makepath function
- _tmakepath function
- paths
- _wmakepath function
- tmakepath function
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bbbaa2f4191d36fb92af5e157990fde6f053df55
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="makepath-wmakepath"></a>_makepath, _wmakepath
Utwórz nazwę ścieżki ze składników. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_makepath_s —, _wmakepath_s —](../../c-runtime-library/reference/makepath-s-wmakepath-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
void _makepath(  
   char *path,  
   const char *drive,  
   const char *dir,  
   const char *fname,  
   const char *ext   
);  
void _wmakepath(  
   wchar_t *path,  
   const wchar_t *drive,  
   const wchar_t *dir,  
   const wchar_t *fname,  
   const wchar_t *ext   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `path`  
 Pełna ścieżka buforu.  
  
 `drive`  
 Zawiera litery (A, B i tak dalej) odpowiadający żądany dysk i opcjonalny dwukropek końcowe. `_makepath` automatycznie wstawia dwukropkiem w ścieżce złożonego, jeśli jest on niedostępny. Jeśli `drive` jest `NULL` lub punktów na pusty ciąg, litera nie występuje w złożone `path` ciągu.  
  
 `dir`  
 Zawiera ścieżkę katalogi nie łącznie z określeniem dysku lub rzeczywiste nazwy plików. Wiodący ukośnik jest opcjonalne, a albo ukośnika (/) ani ukośnika odwrotnego (\\) lub może być używany zarówno w jednej `dir` argumentu. Jeśli nie ma ukośników (/ lub \\) jest określona, zostanie on włożony automatycznie. Jeśli `dir` jest `NULL` lub wskazuje na pusty ciąg, nie ma ścieżki katalogu jest wstawiana złożone `path` ciągu.  
  
 `fname`  
 Zawiera nazwę pliku podstawowego bez żadnych rozszerzeń nazw plików. Jeśli `fname` jest `NULL` lub wskazuje na pusty ciąg, nazwa pliku nie jest wkładana złożone `path` ciągu.  
  
 `ext`  
 Zawiera rozszerzenie nazwy pliku, z lub bez poprzedzającej go kropki (.). `_makepath` Wstawia okresu automatycznie, jeśli nie ma w `ext`. Jeśli `ext` jest `NULL` lub wskazuje na pusty ciąg, bez rozszerzenia jest wstawiana złożone `path` ciągu.  
  
## <a name="remarks"></a>Uwagi  
 `_makepath` Funkcja tworzy ciąg ścieżki złożone z poszczególnych składników zapisywania wyniku w `path`. `path` Może zawierać litery dysku, ścieżki katalogu, nazwę pliku i rozszerzenie nazwy pliku. `_wmakepath` jest to wersja znaków dwubajtowych `_makepath`; argumenty `_wmakepath` są ciągami znaków dwubajtowych. `_wmakepath` i `_makepath` zachowują się tak samo w przeciwnym razie wartość.  
  
 **Uwaga dotycząca zabezpieczeń** użyć ciągu zakończonego wartością null. Aby uniknąć przepełnienia buforu, zerem ciągu nie może przekraczać wielkości `path` buforu. `_makepath` zapewnienia, że długość ciągu złożony ścieżki przekracza `_MAX_PATH`. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tmakepath`|`_makepath`|`_makepath`|`_wmakepath`|  
  
 `path` Argumentu musi wskazywać na pusty buforu wystarczająco duży, aby pomieścić pełną ścieżkę. Złożone `path` nie może być większa niż `_MAX_PATH` stałą, zdefiniowane w Stdlib.h.  
  
 Jeśli ścieżka jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Ponadto `errno` ma ustawioną wartość `EINVAL`. `NULL` wartości są dozwolone dla wszystkich innych parametrów.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_makepath`|\<stdlib.h>|  
|`_wmakepath`|\<stdlib.h > lub \<wchar.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_makepath.c  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char path_buffer[_MAX_PATH];  
   char drive[_MAX_DRIVE];  
   char dir[_MAX_DIR];  
   char fname[_MAX_FNAME];  
   char ext[_MAX_EXT];  
  
   _makepath( path_buffer, "c", "\\sample\\crt\\", "makepath", "c" ); // C4996  
   // Note: _makepath is deprecated; consider using _makepath_s instead  
   printf( "Path created with _makepath: %s\n\n", path_buffer );  
   _splitpath( path_buffer, drive, dir, fname, ext ); // C4996  
   // Note: _splitpath is deprecated; consider using _splitpath_s instead  
   printf( "Path extracted with _splitpath:\n" );  
   printf( "  Drive: %s\n", drive );  
   printf( "  Dir: %s\n", dir );  
   printf( "  Filename: %s\n", fname );  
   printf( "  Ext: %s\n", ext );  
}  
```  
  
```Output  
Path created with _makepath: c:\sample\crt\makepath.c  
  
Path extracted with _splitpath:  
  Drive: c:  
  Dir: \sample\crt\  
  Filename: makepath  
  Ext: .c  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa plików](../../c-runtime-library/file-handling.md)   
 [_fullpath, _wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_splitpath, _wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)   
 [_makepath_s, _wmakepath_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md)