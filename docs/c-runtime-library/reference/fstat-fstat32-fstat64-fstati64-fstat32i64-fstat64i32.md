---
title: "_fstat —, _fstat32 —, _fstat64 —, _fstati64 —, _fstat32i64 —, _fstat64i32 — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fstat32
- _fstat64
- _fstati64
- _fstat
- _fstat64i32
- _fstat32i64
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
- _fstat32i64
- fstat
- fstat64i32
- _fstat64
- _fstati64
- fstat64
- _fstat32
- fstat32i64
- fstati64
- _fstat
- fstat32
- _fstat64i32
dev_langs: C++
helpviewer_keywords:
- _fstat64 function
- fstati64 function
- _fstat64i32 function
- _fstat32i64 function
- _fstat32 function
- file information
- fstat64i32 function
- fstat32 function
- fstat function
- fstat64 function
- _fstat function
- _fstati64 function
- fstat32i64 function
ms.assetid: 088f5e7a-9636-4cf7-ab8e-e28d2aa4280a
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b148bbda218e5f357d7cd5c771073f2d91b87c4c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32"></a>_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32
Pobiera informacje o otwartego pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _fstat(   
   int fd,  
   struct _stat *buffer   
);  
int _fstat32(   
   int fd,  
   struct __stat32 *buffer   
);  
int _fstat64(   
   int fd,  
   struct __stat64 *buffer   
);  
int _fstati64(   
   int fd,  
   struct _stati64 *buffer   
);  
int _fstat32i64(   
   int fd,  
   struct _stat32i64 *buffer   
);  
int _fstat64i32(   
   int fd,  
   struct _stat64i32 *buffer   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fd`  
 Deskryptorów plików otwartych plików.  
  
 `buffer`  
 Wskaźnik do struktury do przechowywania wyników.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość 0, jeśli są uzyskiwane z informacji o stanie pliku. Zwracana wartość -1 wskazuje błąd. Jeśli deskryptorów plików jest nieprawidłowy lub `buffer` jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EBADF`, w przypadku deskryptora nieprawidłowy plik lub do `EINVAL`, jeśli `buffer` jest `NULL`.  
  
## <a name="remarks"></a>Uwagi  
 `_fstat` Funkcja uzyskuje informacje o otwartego pliku skojarzone z `fd` i zapisuje go w strukturze wskazywana przez `buffer`. `_stat` Struktury zdefiniowane w SYS\Stat.h, zawiera następujące pola.  
  
 `st_atime`  
 Czas ostatniego dostępu do pliku.  
  
 `st_ctime`  
 Godzina utworzenia pliku.  
  
 `st_dev`  
 Jeśli urządzenie, `fd`; w przeciwnym razie wartość 0.  
  
 `st_mode`  
 Maska bitowa dla informacji o trybie pliku. `_S_IFCHR` Jeśli ustawiono bit `fd` odwołuje się do urządzenia. `_S_IFREG` Jeśli ustawiono bit `fd` odwołuje się do zwykłego pliku. Bity odczytu/zapisu są ustawione zgodnie z trybu uprawnienia pliku. `_S_IFCHR`i inne stałe są zdefiniowane w SYS\Stat.h.  
  
 `st_mtime`  
 Czas ostatniej modyfikacji pliku.  
  
 `st_nlink`  
 Zawsze 1 w systemach plików z systemem innym niż NTFS.  
  
 `st_rdev`  
 Jeśli urządzenie, `fd`; w przeciwnym razie wartość 0.  
  
 `st_size`  
 Rozmiar pliku w bajtach.  
  
 Jeśli `fd` odwołuje się do urządzenia, `st_atime`, `st_ctime`, `st_mtime`, i `st_size` pola nie są istotne.  
  
 Ponieważ używa Stat.h [_dev_t —](../../c-runtime-library/standard-types.md) typu, który jest zdefiniowany w Types.h, musi zawierać Types.h przed Stat.h w kodzie.  
  
 `_fstat64`, który korzysta z `__stat64` struktury, umożliwia tworzenie plików daty wyrażane się za pośrednictwem 23:59:59 31 grudnia 3000 UTC; inne funkcje tylko stanowią dat za pośrednictwem 23:59:59 18 stycznia 2038 r., UTC. Północy, 1 stycznia 1970 jest dolna granica zakresu dat dla tych funkcji.  
  
 Zmiany tych funkcji obsługuje typy czasu 32-bitowy lub 64-bitowe i 32-bitowy lub 64-bitowego pliku długości. Pierwszy liczbowego sufiksu (`32` lub `64`) wskazuje rozmiar czasu używany typ; druga sufiks jest `i32` lub `i64`, wskazujące Określa, czy rozmiar pliku jest reprezentowany jako 32-bitowy lub 64-bitowej liczby całkowitej.  
  
 `_fstat`jest odpowiednikiem `_fstat64i32`, i `struct _stat` zawiera czas 64-bitowych. Jest to wartość true, chyba że `_USE_32BIT_TIME_T` jest zdefiniowany w takim przypadku stare zachowanie jest włączona; `_fstat` używany czas 32-bitowych, i `struct _stat` zawiera czas 32-bitowych. Dotyczy to także `_fstati64`.  
  
### <a name="time-type-and-file-length-type-variations-of-stat"></a>Typ czasu i zmian typu długość pliku _stat  
  
|Funkcje|_USE_32BIT_TIME_T zdefiniowane?|Typu czasu|Typ długość pliku|  
|---------------|------------------------------------|---------------|----------------------|  
|`_fstat`|Nie zdefiniowano|64-bitowy|32-bitowa|  
|`_fstat`|Definicja|32-bitowa|32-bitowa|  
|`_fstat32`|Nie dotyczy definicji makra|32-bitowa|32-bitowa|  
|`_fstat64`|Nie dotyczy definicji makra|64-bitowy|64-bitowy|  
|`_fstati64`|Nie zdefiniowano|64-bitowy|64-bitowy|  
|`_fstati64`|Definicja|32-bitowa|64-bitowy|  
|`_fstat32i64`|Nie dotyczy definicji makra|32-bitowa|64-bitowy|  
|`_fstat64i32`|Nie dotyczy definicji makra|64-bitowy|32-bitowa|  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`_fstat`|\<sys/stat.h > i \<sys/types.h >|  
|`_fstat32`|\<sys/stat.h > i \<sys/types.h >|  
|`_fstat64`|\<sys/stat.h > i \<sys/types.h >|  
|`_fstati64`|\<sys/stat.h > i \<sys/types.h >|  
|`_fstat32i64`|\<sys/stat.h > i \<sys/types.h >|  
|`_fstat64i32`|\<sys/stat.h > i \<sys/types.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_fstat.c  
// This program uses _fstat to report  
// the size of a file named F_STAT.OUT.  
  
#include <io.h>  
#include <fcntl.h>  
#include <time.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <errno.h>  
#include <share.h>  
  
int main( void )  
{  
   struct _stat buf;  
   int fd, result;  
   char buffer[] = "A line to output";  
   char timebuf[26];  
   errno_t err;  
  
   _sopen_s( &fd,  
             "f_stat.out",  
             _O_CREAT | _O_WRONLY | _O_TRUNC,  
             _SH_DENYNO,  
             _S_IREAD | _S_IWRITE );  
   if( fd != -1 )  
      _write( fd, buffer, strlen( buffer ) );  
  
   // Get data associated with "fd":   
   result = _fstat( fd, &buf );  
  
   // Check if statistics are valid:   
   if( result != 0 )  
   {  
      if (errno == EBADF)  
        printf( "Bad file descriptor.\n" );  
      else if (errno == EINVAL)  
        printf( "Invalid argument to _fstat.\n" );  
   }  
   else  
   {  
      printf( "File size     : %ld\n", buf.st_size );  
      err = ctime_s(timebuf, 26, &buf.st_mtime);  
      if (err)  
      {  
         printf("Invalid argument to ctime_s.");  
         exit(1);  
      }  
      printf( "Time modified : %s", timebuf );  
   }  
   _close( fd );  
}  
```  
  
```Output  
File size     : 16  
Time modified : Wed May 07 15:25:11 2003  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa plików](../../c-runtime-library/file-handling.md)   
 [_access —, _waccess —](../../c-runtime-library/reference/access-waccess.md)   
 [_chmod —, _wchmod —](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_filelength —, _filelengthi64 —](../../c-runtime-library/reference/filelength-filelengthi64.md)   
 [_stat, _wstat — funkcje](../../c-runtime-library/reference/stat-functions.md)