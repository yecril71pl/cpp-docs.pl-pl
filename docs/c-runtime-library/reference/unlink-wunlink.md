---
title: "_unlink —, _wunlink — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _unlink
- _wunlink
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
- _tunlink
- _unlink
- wunlink
- _wunlink
dev_langs: C++
helpviewer_keywords:
- files [C++], deleting
- _wunlink function
- wunlink function
- unlink function
- _unlink function
- tunlink function
- files [C++], removing
- _tunlink function
ms.assetid: 5e4f5f1b-1e99-4391-9b18-9ac63c32fae8
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8494b4a379f0e484ed98f6240dd76ccd4ef15bbd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="unlink-wunlink"></a>_unlink, _wunlink
Usuń plik.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _unlink(  
   const char *filename   
);  
int _wunlink(  
   const wchar_t *filename   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Nazwa pliku do usunięcia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji zwraca wartość 0 w przypadku powodzenia. W przeciwnym razie funkcja zwraca wartość -1 i zestawy `errno` do `EACCES`, co oznacza, że ścieżka Określa plik tylko do odczytu lub `ENOENT`, co oznacza pliku lub ścieżka nie zostanie znaleziony, lub określona ścieżka katalogu.  
  
 Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) kody powrotne — Aby uzyskać więcej informacji na temat tych i innych.  
  
## <a name="remarks"></a>Uwagi  
 `_unlink` Funkcja usuwa plik określony przez `filename`. `_wunlink`jest to wersja znaków dwubajtowych `_unlink`; `filename` argument `_wunlink` jest ciągiem znaków dwubajtowych. Funkcje te działają tak samo w przeciwnym razie wartość.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tunlink`|`_unlink`|`_unlink`|`_wunlink`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_unlink`|\<IO.h > i \<stdio.h >|  
|`_wunlink`|\<IO.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="code-example"></a>Przykład kodu  
 _Unlink — jest używane do usuwania CRT_UNLINK. TXT.  
  
```  
// crt_unlink.c  
  
#include <stdio.h>  
  
int main( void )  
{  
   if( _unlink( "crt_unlink.txt" ) == -1 )  
      perror( "Could not delete 'CRT_UNLINK.TXT'" );  
   else  
      printf( "Deleted 'CRT_UNLINK.TXT'\n" );  
}  
```  
  
### <a name="input-crtunlinktxt"></a>Dane wejściowe: crt_unlink.txt  
  
```  
This file will be deleted.  
```  
  
### <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
Deleted 'CRT_UNLINK.TXT'  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa plików](../../c-runtime-library/file-handling.md)   
 [_zamknij](../../c-runtime-library/reference/close.md)   
 [remove, _wremove](../../c-runtime-library/reference/remove-wremove.md)