---
title: "_makepath_s —, _wmakepath_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wmakepath_s
- _makepath_s
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
- _wmakepath_s
- makepath_s
- _makepath_s
- wmakepath_s
dev_langs: C++
helpviewer_keywords:
- _makepath_s function
- wmakepath_s function
- paths
- _wmakepath_s function
- makepath_s function
ms.assetid: 4405e43c-3d63-4697-bb80-9b8dcd21d027
caps.latest.revision: "29"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9b808d41bfb0d9da3f709f8f655a86c168b15e00
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="makepaths-wmakepaths"></a>_makepath_s, _wmakepath_s
Tworzy nazwę ścieżki ze składników. Są to wersje [_makepath —, _wmakepath —](../../c-runtime-library/reference/makepath-wmakepath.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _makepath_s(  
   char *path,  
   size_t sizeInBytes,  
   const char *drive,  
   const char *dir,  
   const char *fname,  
   const char *ext   
);  
errno_t _wmakepath_s(  
   wchar_t *path,  
   size_t sizeInWords,  
   const wchar_t *drive,  
   const wchar_t *dir,  
   const wchar_t *fname,  
   const wchar_t *ext   
);  
template <size_t size>  
errno_t _makepath_s(  
   char (&path)[size],  
   const char *drive,  
   const char *dir,  
   const char *fname,  
   const char *ext   
); // C++ only  
template <size_t size>  
errno_t _wmakepath_s(  
   wchar_t (&path)[size],  
   const wchar_t *drive,  
   const wchar_t *dir,  
   const wchar_t *fname,  
   const wchar_t *ext   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`path`  
 Pełna ścieżka buforu.  
  
 [in]`sizeInWords`  
 Rozmiar buforu w wyrazy.  
  
 [in]`sizeInBytes`  
 Rozmiar buforu w bajtach.  
  
 [in]`drive`  
 Zawiera litery (A, B i tak dalej) odpowiadający żądany dysk i opcjonalny dwukropek końcowe. `_makepath_s`automatycznie wstawia dwukropkiem w ścieżce złożonego, jeśli jest on niedostępny. Jeśli `drive` jest `NULL` lub punktów na pusty ciąg, litera nie występuje w złożone `path` ciągu.  
  
 [in]`dir`  
 Zawiera ścieżkę katalogi nie łącznie z określeniem dysku lub rzeczywiste nazwy plików. Wiodący ukośnik jest opcjonalne, a albo ukośnika (/) ani ukośnika odwrotnego (\\) lub może być używany zarówno w jednej `dir` argumentu. Jeśli nie ma ukośników (/ lub \\) jest określona, zostanie on włożony automatycznie. Jeśli `dir` jest `NULL` lub wskazuje na pusty ciąg, nie ma ścieżki katalogu jest wstawiana złożone `path` ciągu.  
  
 [in]`fname`  
 Zawiera nazwę pliku podstawowego bez żadnych rozszerzeń nazw plików. Jeśli `fname` jest `NULL` lub wskazuje na pusty ciąg, nazwa pliku nie jest wkładana złożone `path` ciągu.  
  
 [in]`ext`  
 Zawiera rozszerzenie nazwy pliku, z lub bez poprzedzającej go kropki (.). `_makepath_s`Wstawia okresu automatycznie, jeśli nie ma w `ext`. Jeśli `ext` jest `NULL` lub wskazuje na pusty ciąg, bez rozszerzenia jest wstawiana złożone `path` ciągu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero w przypadku powodzenia; błąd o kodzie błędu.  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|`path`|`sizeInWords` / `sizeInBytes`|Zwraca|Zawartość`path`|  
|------------|------------------------------------|------------|------------------------|  
|`NULL`|wszystkie|`EINVAL`|Nie zmodyfikowano|  
|wszystkie|<= 0|`EINVAL`|Nie zmodyfikowano|  
  
 Jeśli dowolne z powyższych warunków błąd wystąpi, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EINVAL` i funkcji zwraca `EINVAL`. `NULL`jest dozwolony dla parametrów `drive`, `fname`, i `ext`. Aby uzyskać informacje o zachowaniu gdy te parametry są wskaźniki o wartości null lub pusty ciąg, sekcji uwag.  
  
## <a name="remarks"></a>Uwagi  
 `_makepath_s` Funkcja tworzy ciąg ścieżki złożone z poszczególnych składników zapisywania wyniku w `path`. `path` Może zawierać litery dysku, ścieżki katalogu, nazwa pliku i rozszerzenie nazwy pliku. `_wmakepath_s`jest to wersja znaków dwubajtowych `_makepath_s`; argumenty `_wmakepath_s` są ciągami znaków dwubajtowych. `_wmakepath_s`i `_makepath_s` zachowują się tak samo w przeciwnym razie wartość.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tmakepath_s`|`_makepath_s`|`_makepath_s`|`_wmakepath_s`|  
  
 `path` Argumentu musi wskazywać na pusty buforu wystarczająco duży, aby pomieścić pełną ścieżkę. Złożone `path` nie może być większa niż `_MAX_PATH` stałą, zdefiniowane w Stdlib.h.  
  
 Jeśli ścieżka jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Ponadto `errno` ma ustawioną wartość `EINVAL`. `NULL`wartości są dozwolone dla wszystkich innych parametrów.  
  
 W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (wyeliminowanie konieczności określania argumentem rozmiaru) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
 Wersje tych funkcji do debugowania najpierw wprowadzić bufor 0xFD. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_makepath_s`|\<stdlib.h >|  
|`_wmakepath_s`|\<stdlib.h > lub \<wchar.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_makepath_s.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char path_buffer[_MAX_PATH];  
   char drive[_MAX_DRIVE];  
   char dir[_MAX_DIR];  
   char fname[_MAX_FNAME];  
   char ext[_MAX_EXT];  
   errno_t err;  
  
   err = _makepath_s( path_buffer, _MAX_PATH, "c", "\\sample\\crt\\",  
                      "crt_makepath_s", "c" );  
   if (err != 0)  
   {  
      printf("Error creating path. Error code %d.\n", err);  
      exit(1);  
   }  
   printf( "Path created with _makepath_s: %s\n\n", path_buffer );  
   err = _splitpath_s( path_buffer, drive, _MAX_DRIVE, dir, _MAX_DIR, fname,  
                       _MAX_FNAME, ext, _MAX_EXT );  
   if (err != 0)  
   {  
      printf("Error splitting the path. Error code %d.\n", err);  
      exit(1);  
   }  
   printf( "Path extracted with _splitpath_s:\n" );  
   printf( "  Drive: %s\n", drive );  
   printf( "  Dir: %s\n", dir );  
   printf( "  Filename: %s\n", fname );  
   printf( "  Ext: %s\n", ext );  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
Path created with _makepath_s: c:\sample\crt\crt_makepath_s.c  
  
Path extracted with _splitpath_s:  
  Drive: c:  
  Dir: \sample\crt\  
  Filename: crt_makepath_s  
  Ext: .c  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa plików](../../c-runtime-library/file-handling.md)   
 [_fullpath —, _wfullpath —](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_splitpath_s —, _wsplitpath_s —](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)   
 [_makepath, _wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)