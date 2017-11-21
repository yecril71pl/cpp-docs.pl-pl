---
title: "_stat, _stat32 —, _stat64 —, _stati64 —, _stat32i64 —, _stat64i32 —, _wstat —, _wstat32 —, _wstat64 —, _wstati64 —, _wstat32i64 —, _wstat64i32 — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wstat64
- _stati64
- _stat32
- _stat32i64
- _stat
- _wstati64
- _wstat32
- _wstat64i32
- _wstat
- _stat64
- _stat64i32
- _wstat32i64
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
- tstat32
- tstat
- _tstat64i32
- tstati64
- _wstat64
- _wstat32
- wstati64
- tstat64
- _stati64
- _wstat
- wstat64i32
- stat32i64
- tstat32i64
- _tstat
- _wstati64
- _tstati64
- _wstat32i64
- wstat32
- _wstat64i32
- _stat
- _tstat32
- stat64i32
- wstat64
- stat
- _stat32i64
- _stat32
- stati64
- wstat
- _stat64i32
- stat32
- _tstat32i64
- tstat64i32
- _tstat64
- _stat64
- stat/_stat
- stat/_stat32
- stat/_stat64
- stat/_stati64
- stat/_stat32i64
- stat/_stat64i32
- stat/_wstat
- stat/_wstat32
- stat/_wstat64
- stat/_wstati64
- stat/_wstat32i64
- stat/_wstat64i32
dev_langs: C++
helpviewer_keywords:
- files [C++], status information
- _stat function
- _wstat function
- _stat64i32 function
- tstat function
- _tstat64i32 function
- _stati64 function
- _stat64 function
- tstati64 function
- wstati64 function
- wstat64 function
- _wstat64i32 function
- _tstat32i64 function
- _stat32i64 function
- stat function
- status of files
- _tstat32 function
- tstat64 function
- _wstat64 function
- _tstat function
- _stat32 function
- wstat function
- _wstat32i64 function
- _tstati64 function
- _wstat32 function
- stat64 function
- stati64 function
- _wstati64 function
- _tstat64 function
- files [C++], getting status information
ms.assetid: 99a75ae6-ff26-47ad-af70-5ea7e17226a5
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 18cfdda310149c18ef8983b10afb5c901b256510
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="stat-stat32-stat64-stati64-stat32i64-stat64i32-wstat-wstat32-wstat64-wstati64-wstat32i64-wstat64i32"></a>_stat, _stat32 —, _stat64 —, _stati64 —, _stat32i64 —, _stat64i32 —, _wstat —, _wstat32 —, _wstat64 —, _wstati64 —, _wstat32i64 —, _wstat64i32 —
Pobierz informacje o stanie pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _stat(  
   const char *path,  
   struct _stat *buffer   
);  
int _stat32(  
   const char *path,  
   struct __stat32 *buffer   
);  
int _stat64(  
   const char *path,  
   struct __stat64 *buffer   
);  
int _stati64(  
   const char *path,  
   struct _stati64 *buffer   
);  
int _stat32i64(  
   const char *path,  
   struct _stat32i64 *buffer   
);  
int _stat64i32(  
   const char *path,  
   struct _stat64i32 *buffer   
);  
int _wstat(  
   const wchar_t *path,  
   struct _stat *buffer   
);  
int _wstat32(  
   const wchar_t *path,  
   struct __stat32 *buffer   
);  
int _wstat64(  
   const wchar_t *path,  
   struct __stat64 *buffer   
);  
int _wstati64(  
   const wchar_t *path,  
   struct _stati64 *buffer   
);  
int _wstat32i64(  
   const wchar_t *path,  
   struct _stat32i64 *buffer   
);  
int _wstat64i32(  
   const wchar_t *path,  
   struct _stat64i32 *buffer   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `path`  
 Wskaźnik do ciąg zawierający ścieżkę do istniejącego pliku lub katalogu.  
  
 `buffer`  
 Wskaźnik do struktury, która przechowuje wyniki.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji zwraca wartość 0, jeśli uzyskano informacje o stanie pliku. Zwracana wartość -1 wskazuje błąd, w którym to przypadku `errno` ma ustawioną wartość `ENOENT`, wskazując, że nazwa pliku lub ścieżka nie można odnaleźć. Zwracana wartość `EINVAL` wskazuje nieprawidłowy parametr; `errno` również ustawiono `EINVAL` w takim przypadku.  
  
 Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) kody powrotne — Aby uzyskać więcej informacji na ten i inne.  
  
 Może być reprezentowany sygnaturę daty w pliku, jeśli jest nowsze niż północy, 1 stycznia 1970 i przed 23:59:59 31 grudnia 3000 UTC, chyba że są używane `_stat32` lub `_wstat32`, lub zdefiniowano `_USE_32BIT_TIME_T`, w którym to przypadku Data mogą być przedstawiane tylko do 23:59:59 18 stycznia 2038 r., UTC.  
  
## <a name="remarks"></a>Uwagi  
 `_stat` Funkcja uzyskuje informacje o pliku lub katalogu określonego przez `path` i zapisuje go w strukturze wskazywana przez `buffer`. `_stat`automatycznie obsługuje argumentów ciągów znaków wielobajtowych zgodnie z potrzebami, rozpoznawanie wielobajtowych sekwencji znaków zgodnie ze strony kodowe wielobajtowe obecnie w użyciu.  
  
 `_wstat`jest to wersja znaków dwubajtowych `_stat`; `path` argument `_wstat` jest ciągiem znaków dwubajtowych. `_wstat`i `_stat` zachowują się tak samo, z wyjątkiem `_wstat` nie obsługuje ciągów znaków wielobajtowych.  
  
 Zmiany tych funkcji obsługuje typy czasu 32 - lub 64-bitowe i 32 - lub 64-bitowy plik długości. Pierwszy liczbowego sufiksu (`32` lub `64`) wskazuje rozmiar czasu używany typ; druga sufiks jest `i32` lub `i64`, wskazujące Określa, czy rozmiar pliku jest reprezentowany jako 32-bitowy lub 64-bitowej liczby całkowitej.  
  
 `_stat`jest odpowiednikiem `_stat64i32`, i `struct _stat` zawiera czas 64-bitowych. Jest to wartość true, chyba że `_USE_32BIT_TIME_T` jest zdefiniowany w takim przypadku stare zachowanie jest włączona; `_stat` używany czas 32-bitowych, i `struct _stat` zawiera czas 32-bitowych. Dotyczy to także `_stati64`.  
  
> [!NOTE]
>  `_wstat`nie działa z [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] łącza symbolicznego. W takich przypadkach `_wstat` będzie zawsze raportu w pliku o rozmiarze 0. `_stat`działa poprawnie z łącza symbolicznego.  
  
 Ta funkcja weryfikuje jego parametrów. Jeśli dowolny `path` lub `buffer` jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).  
  
### <a name="time-type-and-file-length-type-variations-of-stat"></a>Typ czasu i zmian typu długość pliku _stat  
  
|Funkcje|_USE_32BIT_TIME_T zdefiniowane?|Typu czasu|Typ długość pliku|  
|---------------|------------------------------------|---------------|----------------------|  
|`_stat`, `_wstat`|Nie zdefiniowano|64-bitowy|32-bitowa|  
|`_stat`, `_wstat`|Definicja|32-bitowa|32-bitowa|  
|`_stat32`, `_wstat32`|Nie dotyczy definicji makra|32-bitowa|32-bitowa|  
|`_stat64`, `_wstat64`|Nie dotyczy definicji makra|64-bitowy|64-bitowy|  
|`_stati64`, `_wstati64`|Nie zdefiniowano|64-bitowy|64-bitowy|  
|`_stati64`, `_wstati64`|Definicja|32-bitowa|64-bitowy|  
|`_stat32i64`, `_wstat32i64`|Nie dotyczy definicji makra|32-bitowa|64-bitowy|  
|`_stat64i32`, `_wstat64i32`|Nie dotyczy definicji makra|64-bitowy|32-bitowa|  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tstat`|`_stat`|`_stat`|`_wstat`|  
|`_tstat64`|`_stat64`|`_stat64`|`_wstat64`|  
|`_tstati64`|`_stati64`|`_stati64`|`_wstati64`|  
|`_tstat32i64`|`_stat32i64`|`_stat32i64`|`_wstat32i64`|  
|`_tstat64i32`|`_stat64i32`|`_stat64i32`|`_wstat64i32`|  
  
 `_stat` Struktury zdefiniowane w SYS\STAT. H, zawiera następujące pola.  
  
 `st_gid`  
 Identyfikator numeryczny grupy, który jest właścicielem pliku (specyficzne dla systemu UNIX) to pole będzie zawsze równa zero w systemach Windows. Przekierowanego pliku zostanie sklasyfikowany jako pliku systemu Windows.  
  
 `st_atime`  
 Czas ostatniego dostępu do pliku. Dyskach sformatowanych obowiązuje w systemu plików NTFS, ale nie w systemie plików FAT.  
  
 `st_ctime`  
 Godzina utworzenia pliku. Dyskach sformatowanych obowiązuje w systemu plików NTFS, ale nie w systemie plików FAT.  
  
 `st_dev`  
 Numer dysku z plikiem dysku (taki sam jak `st_rdev`).  
  
 `st_ino`  
 Liczba węzłów informacji ( `inode`) dla pliku (specyficzne dla systemu UNIX). W systemach UNIX plików `inode` opisano Data plików i sygnatury czasowe, uprawnienia i zawartości. Jeśli pliki są twarde połączone ze sobą, mają takie same `inode`. `inode`i w związku z tym `st_ino`, nie ma znaczenia w systemie plików FAT, HPFS lub NTFS.  
  
 `st_mode`  
 Maska bitowa dla informacji o trybie pliku. `_S_IFDIR` Jeśli ustawiono bit `path` Określa katalog; `_S_IFREG` Jeśli ustawiono bit `path` określa to zwykły plik lub urządzenia. Bity odczytu/zapisu użytkownika są ustawione zgodnie z trybu uprawnienia pliku; Użytkownik uruchomić usługi bits są ustawione zgodnie z rozszerzeniem nazwy pliku.  
  
 `st_mtime`  
 Czas ostatniej modyfikacji pliku.  
  
 `st_nlink`  
 Zawsze 1 w systemach plików z systemem innym niż NTFS.  
  
 `st_rdev`  
 Numer dysku z plikiem dysku (taki sam jak `st_dev`).  
  
 `st_size`  
 Rozmiar pliku w bajtach; 64-bitową liczbę całkowitą dla zmian z `i64` sufiks**.**  
  
 `st_uid`  
 Identyfikator numeryczny użytkownika, który jest właścicielem pliku (specyficzne dla systemu UNIX). To pole zawsze będzie zerem w systemie Windows. Przekierowanego pliku zostanie sklasyfikowany jako pliku systemu Windows.  
  
 Jeśli `path` odwołuje się do urządzenia, `st_size`, różnych pól Godzina, `st_dev`, i `st_rdev` pól w `_stat` struktury nie mają znaczenia. Ponieważ STAT. Używa H [_dev_t —](../../c-runtime-library/standard-types.md) typ typy zdefiniowane w. H, musi zawierać typów. H przed STAT. H w kodzie.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|----------------------|  
|`_stat`, `_stat32`, `_stat64`, `_stati64`, `_stat32i64`, `_stat64i32`|\<sys/types.h > następuje \<sys/stat.h >|\<errno.h >|  
|`_wstat`, `_wstat32`, `_wstat64`, `_wstati64`, `_wstat32i64`, `_wstat64i32`|\<sys/types.h > następuje \<sys/stat.h > lub \<wchar.h >|\<errno.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_stat.c  
// This program uses the _stat function to  
// report information about the file named crt_stat.c.  
  
#include <time.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
   struct _stat buf;  
   int result;  
   char timebuf[26];  
   char* filename = "crt_stat.c";  
   errno_t err;  
  
   // Get data associated with "crt_stat.c":   
   result = _stat( filename, &buf );  
  
   // Check if statistics are valid:   
   if( result != 0 )  
   {  
      perror( "Problem getting information" );  
      switch (errno)  
      {  
         case ENOENT:  
           printf("File %s not found.\n", filename);  
           break;  
         case EINVAL:  
           printf("Invalid parameter to _stat.\n");  
           break;  
         default:  
           /* Should never be reached. */  
           printf("Unexpected error in _stat.\n");  
      }  
   }  
   else  
   {  
      // Output some of the statistics:   
      printf( "File size     : %ld\n", buf.st_size );  
      printf( "Drive         : %c:\n", buf.st_dev + 'A' );  
      err = ctime_s(timebuf, 26, &buf.st_mtime);  
      if (err)  
      {  
         printf("Invalid arguments to ctime_s.");  
         exit(1);  
      }  
      printf( "Time modified : %s", timebuf );  
   }  
}  
```  
  
```Output  
File size     : 732  
Drive         : C:  
Time modified : Thu Feb 07 14:39:36 2002  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa plików](../../c-runtime-library/file-handling.md)   
 [_access —, _waccess —](../../c-runtime-library/reference/access-waccess.md)   
 [_fstat —, _fstat32 —, _fstat64 —, _fstati64 — _fstat32i64 —, _fstat64i32 —](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [_getmbcp —](../../c-runtime-library/reference/getmbcp.md)   
 [_setmbcp —](../../c-runtime-library/reference/setmbcp.md)