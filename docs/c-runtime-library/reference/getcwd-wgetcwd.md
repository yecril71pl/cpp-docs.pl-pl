---
title: "_getcwd —, _wgetcwd — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wgetcwd
- _getcwd
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getcwd
- wgetcwd
- _wgetcwd
- tgetcwd
- _tgetcwd
dev_langs: C++
helpviewer_keywords:
- getcwd function
- working directory
- _wgetcwd function
- _getcwd function
- current working directory
- wgetcwd function
- directories [C++], current working
ms.assetid: 888dc8c6-5595-4071-be55-816b38e3e739
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e72618467666a98bdda5867b23d9ef2ce37319f2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="getcwd-wgetcwd"></a>_getcwd, _wgetcwd
Pobiera bieżący katalog roboczy.  
  
## <a name="syntax"></a>Składnia  
  
```  
char *_getcwd(   
   char *buffer,  
   int maxlen   
);  
wchar_t *_wgetcwd(   
   wchar_t *buffer,  
   int maxlen   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Lokalizacja magazynu dla ścieżki.  
  
 `maxlen`  
 Maksymalna długość ścieżki w znakach: `char` dla `_getcwd` i `wchar_t` dla `_wgetcwd`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do `buffer`. A `NULL` zwracana wartość wskazuje błąd i `errno` ma ustawioną opcję `ENOMEM`, wskazująca, że jest za mało pamięci do przydzielenia `maxlen` bajtów (gdy `NULL` argument jest podawana jako `buffer`), lub `ERANGE`, wskazujący, że ścieżka jest dłuższa niż `maxlen` znaków. Jeśli `maxlen` jest mniejsza lub równa zero, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).  
  
 Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `_getcwd` Funkcja pobiera pełną ścieżkę bieżącego katalogu roboczego na domyślnym dysku i zapisuje go w `buffer`. Argument całkowitą `maxlen` określa maksymalną długość ścieżki. Błąd występuje, gdy przekracza długość ścieżki (w tym znak końcowy null) `maxlen`. `buffer` Argument może być `NULL`; bufor o rozmiarze co najmniej `maxlen` (więcej tylko wtedy, gdy jest to konieczne) jest automatycznie przydzielone, przy użyciu `malloc`, aby przechowywać ścieżkę. Bufor później może zostać zwolniony przez wywołanie metody `free` i przekazanie jej `_getcwd` zwrócić wartość (wskaźnik do przydzielonego buforu).  
  
 `_getcwd`Zwraca ciąg reprezentujący ścieżkę bieżącego katalogu roboczego. Jeśli bieżący katalog roboczy jest katalogiem głównym, ciąg kończy się znakiem kreski ułamkowej odwróconej ( `\` ). Jeśli bieżący katalog roboczy jest katalogiem innego niż root, ciąg kończy się nazwą katalogu i nie kreski ułamkowej odwróconej.  
  
 `_wgetcwd`jest to wersja znaków dwubajtowych `_getcwd`; `buffer` argumentów i wartości `_wgetcwd` są ciągami znaków dwubajtowych. `_wgetcwd`i `_getcwd` zachowują się tak samo w przeciwnym razie wartość.  
  
 Gdy `_DEBUG` i `_CRTDBG_MAP_ALLOC` są zdefiniowane, wywołań `_getcwd` i `_wgetcwd` zastępuje wywołań `_getcwd_dbg` i `_wgetcwd_dbg` umożliwiające profilowanie przydziału pamięci. Aby uzyskać więcej informacji, zobacz [_getcwd_dbg —, _wgetcwd_dbg —](../../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tgetcwd`|`_getcwd`|`_getcwd`|`_wgetcwd`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_getcwd`|\<Direct.h >|  
|`_wgetcwd`|\<Direct.h > lub \<wchar.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_getcwd.c  
// This program places the name of the current directory in the   
// buffer array, then displays the name of the current directory   
// on the screen. Passing NULL as the buffer forces getcwd to allocate  
// memory for the path, which allows the code to support file paths  
// longer than _MAX_PATH, which are supported by NTFS.  
  
#include <direct.h>  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char* buffer;  
  
   // Get the current working directory:   
   if( (buffer = _getcwd( NULL, 0 )) == NULL )  
      perror( "_getcwd error" );  
   else  
   {  
      printf( "%s \nLength: %d\n", buffer, strnlen(buffer) );  
      free(buffer);  
   }  
}  
```  
  
```Output  
C:\Code  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola katalogu](../../c-runtime-library/directory-control.md)   
 [_chdir —, _wchdir —](../../c-runtime-library/reference/chdir-wchdir.md)   
 [_mkdir —, _wmkdir —](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [_rmdir —, _wrmdir —](../../c-runtime-library/reference/rmdir-wrmdir.md)