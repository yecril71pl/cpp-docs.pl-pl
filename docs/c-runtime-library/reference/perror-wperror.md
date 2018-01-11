---
title: "perror, _wperror — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wperror
- perror
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wperror
- _tperror
- perror
dev_langs: C++
helpviewer_keywords:
- _tperror function
- tperror function
- wperror function
- error messages, printing
- printing error messages
- _wperror function
- perror function
ms.assetid: 34fce792-16fd-4673-9849-cd88b54b6cd5
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bb8dc68154c9a1302fe69dd8416309bf377bdd3f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="perror-wperror"></a>perror, _wperror
Drukuj komunikat o błędzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      void perror(  
   const char *string   
);  
void _wperror(  
   const wchar_t *string   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `string`  
 Ciąg komunikatu do drukowania.  
  
## <a name="remarks"></a>Uwagi  
 `perror` Funkcja wyświetla komunikat o błędzie `stderr`. `_wperror`jest to wersja znaków dwubajtowych **_perror**; `string` argument `_wperror` jest ciągiem znaków dwubajtowych. `_wperror`i **_perror** zachowują się tak samo w przeciwnym razie wartość.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tperror`|`perror`|`perror`|`_wperror`|  
  
 `string`drukowania najpierw, a następnie dwukropek, a następnie system komunikat o błędzie dla ostatniego wywołania biblioteki, które spowodowało błąd, a na końcu znakiem nowego wiersza. Jeśli `string` wskaźnika o wartości null lub wskaźnikiem do ciągu wartości null, `perror` wyświetla tylko system komunikat o błędzie.  
  
 Numer błędu jest przechowywana w zmiennej [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) (zdefiniowany w numer błędu. H). Komunikaty o błędach systemu są dostępne za pośrednictwem zmiennej [_sys_errlist —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), która jest tablicę komunikatów uporządkowanych według numer błędu. `perror`Drukuje wiadomości odpowiednie błąd przy użyciu `errno` wartość jako indeks `_sys_errlist`. Wartość zmiennej [_sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) jest zdefiniowany jako maksymalną liczbę elementów w `_sys_errlist` tablicy.  
  
 Aby uzyskać dokładne wyniki wywołania `perror` natychmiast po procedury biblioteki zwraca błąd. W przeciwnym razie można zastąpić wezwań `errno` wartość.  
  
 W oknach systemu operacyjnego, niektóre `errno` wartości na liście numer błędu. H są używane. Wartości te są zarezerwowane do użytku przez system operacyjny UNIX. Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) listę `errno` wartości używane przez system operacyjny Windows. `perror`Wyświetla ciąg pusty dla każdego `errno` wartość nie jest używana przez tych platform.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`perror`|\<stdio.h > lub \<stdlib.h >|  
|`_wperror`|\<stdio.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_perror.c  
// compile with: /W3  
/* This program attempts to open a file named  
 * NOSUCHF.ILE. Because this file probably doesn't exist,  
 * an error message is displayed. The same message is  
 * created using perror, strerror, and _strerror.  
 */  
  
#include <fcntl.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <io.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <string.h>  
#include <share.h>  
  
int main( void )  
{  
   int  fh;  
  
   if( _sopen_s( &fh, "NOSUCHF.ILE", _O_RDONLY, _SH_DENYNO, 0 ) != 0 )  
   {  
      /* Three ways to create error message: */  
      perror( "perror says open failed" );  
      printf( "strerror says open failed: %s\n",  
         strerror( errno ) ); // C4996  
      printf( _strerror( "_strerror says open failed" ) ); // C4996  
      // Note: strerror and _strerror are deprecated; consider  
      // using strerror_s and _strerror_s instead.  
   }  
   else  
   {  
      printf( "open succeeded on input file\n" );  
      _close( fh );  
   }  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
perror says open failed: No such file or directory  
strerror says open failed: No such file or directory  
_strerror says open failed: No such file or directory  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Proces i kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)   
 [clearerr —](../../c-runtime-library/reference/clearerr.md)   
 [ferror —](../../c-runtime-library/reference/ferror.md)   
 [strerror —, _strerror —, _wcserror —, \__wcserror —](../../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)