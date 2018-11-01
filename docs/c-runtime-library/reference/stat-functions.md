---
title: _stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32
ms.date: 11/04/2016
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
ms.openlocfilehash: 316012479ec374cc5f40061384475008fe04e331
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637284"
---
# <a name="stat-stat32-stat64-stati64-stat32i64-stat64i32-wstat-wstat32-wstat64-wstati64-wstat32i64-wstat64i32"></a>_stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32

Uzyskaj informacje o stanie dla pliku.

## <a name="syntax"></a>Składnia

```C
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

### <a name="parameters"></a>Parametry

*Ścieżka*<br/>
Wskaźnik do ciągu zawierającego ścieżkę do istniejącego pliku lub katalogu.

*buffer*<br/>
Wskaźnik do struktury, która przechowuje wyniki.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość 0, jeżeli uzyskano informacje o stanie pliku. Zwracana wartość -1 wskazuje błąd, w którym to przypadku **errno** ustawiono **ENOENT**, wskazujący, że nazwa pliku lub ścieżka nie został odnaleziony. Zwracana wartość wynosząca **EINVAL** wskazuje nieprawidłowy parametr; **errno** jest również ustawiona na **EINVAL** w tym przypadku.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) kody powrotne — Aby uzyskać więcej informacji na temat tego i innych.

Może być reprezentowany sygnatura daty dla pliku, jeśli jest nowszy od północy 1 stycznia 1970 r., a przed 23:59:59, 31 grudnia 3000, czasu UTC, chyba że używasz **_stat32 —** lub **_wstat32 —**, lub zdefiniowano **_ USE_32BIT_TIME_T**, w którym to przypadku Data mogą być reprezentowane w taki sposób, tylko do 23:59:59 18 stycznia 2038 r. UTC.

## <a name="remarks"></a>Uwagi

**_Stat** funkcja uzyskuje informacje o pliku lub katalogu określonym przez *ścieżki* i zapisuje go w strukturze wskazywany przez *buforu*. **stałe pola_stat** automatycznie obsługuje argumenty ciągu znaków wielobajtowych zgodnie z potrzebami, rozpoznawaniu sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową wielobajtowe.

**_wstat —** to wersja znaku dwubajtowego **_stat**; *ścieżki* argument **_wstat —** jest ciągiem znaku dwubajtowego. **_wstat —** i **_stat** zachowują się identycznie, chyba że **_wstat —** nie obsługuje ciągi znaków wielobajtowych.

Różnice te funkcje obsługują typy czasu 32 - lub 64-bitowe i 32 - lub 64-bitowy plik długości. Pierwszy liczbowego sufiksu (**32** lub **64**) wskazuje rozmiar czasu używany typ; drugi sufiks jest **i32** lub **i64**, wskazująca, czy rozmiar pliku jest reprezentowany jako 32-bitowy lub 64-bitową liczbę całkowitą.

**stałe pola_stat** jest odpowiednikiem **_stat64i32 —**, i **struktury** **_stat** zawiera godzinę 64-bitowych. Jest to wartość true, chyba że **_USE_32BIT_TIME_T** jest zdefiniowany, w którym to przypadku stare zachowanie obowiązuje; **_stat** korzysta z danym 32-bitowe i **struktury** **_stat** zawiera godzinę 32-bitowych. Dotyczy to także **_stati64**.

> [!NOTE]
> **_wstat —** nie działa z łącza symbolicznego Windows Vista. W takich przypadkach **_wstat —** będzie zawsze raportu pliku o rozmiarze 0. **stałe pola_stat** działać poprawnie z łącza symbolicznego.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *ścieżki* lub *buforu* jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md).

### <a name="time-type-and-file-length-type-variations-of-stat"></a>Typ czasu i zmian typu długość pliku _stat

|Funkcje|_USE_32BIT_TIME_T zdefiniowane?|Typ czasu|Typ długość pliku|
|---------------|------------------------------------|---------------|----------------------|
|**stałe pola_stat**, **_wstat —**|Nie zdefiniowano|64-bitowy|32-bitowa|
|**stałe pola_stat**, **_wstat —**|Definicja|32-bitowa|32-bitowa|
|**_stat32 —**, **_wstat32 —**|Nie dotyczy definicji makra|32-bitowa|32-bitowa|
|**_stat64**, **_wstat64**|Nie dotyczy definicji makra|64-bitowy|64-bitowy|
|**_stati64**, **_wstati64**|Nie zdefiniowano|64-bitowy|64-bitowy|
|**_stati64**, **_wstati64**|Definicja|32-bitowa|64-bitowy|
|**_stat32i64 —**, **_wstat32i64 —**|Nie dotyczy definicji makra|32-bitowa|64-bitowy|
|**_stat64i32 —**, **_wstat64i32 —**|Nie dotyczy definicji makra|64-bitowy|32-bitowa|

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstat —**|**_stat**|**_stat**|**_wstat**|
|**_tstat64 —**|**_stat64**|**_stat64**|**_wstat64**|
|**_tstati64 —**|**_stati64**|**_stati64**|**_wstati64**|
|**_tstat32i64 —**|**_stat32i64**|**_stat32i64**|**_wstat32i64**|
|**_tstat64i32 —**|**_stat64i32**|**_stat64i32**|**_wstat64i32**|

**_Stat** struktury, zdefiniowanego w SYS\STAT. Godz., zawiera następujące pola.

|Pole||
|-|-|
**st_gid**|Identyfikator liczbowy grupy, który jest właścicielem pliku (specyficzne dla systemu UNIX) to pole jest zawsze zero w systemach Windows. Przekierowanego pliku zostanie sklasyfikowany jako pliku Windows.
**st_atime**|Czas ostatniego dostępu do pliku. Dyskach sformatowanych prawidłowe na systemu plików NTFS, ale nie w systemie FAT.
**st_ctime**|Godzina utworzenia pliku. Dyskach sformatowanych prawidłowe na systemu plików NTFS, ale nie w systemie FAT.
**st_dev**|Numer dysku z plikiem dysku (taka sama jak **st_rdev**).
**st_ino**|Liczba węzłów informacje ( **węzeł i**) dla pliku (specyficzne dla systemu UNIX). W systemach plików systemu UNIX **węzeł i** opisuje Data pliku i sygnatury czasowe, uprawnienia i zawartości. Jeśli pliki są twarde połączone ze sobą, mogą współużytkować ten sam **węzeł i**. **Węzeł i**i w związku z tym **st_ino**, nie ma znaczenia w systemach plików FAT, HPFS lub NTFS.
**st_mode**|Maska bitów informacji tryb pliku. **_S_IFDIR** Jeśli ustawiono bit *ścieżki* Określa katalog; **_S_IFREG** Jeśli ustawiono bit *ścieżki* określa to zwykły plik lub urządzenia. Użytkownik odczytu/zapisu bity są ustawione zgodnie z trybu uprawnienia pliku; Użytkownik wykonać bity są ustawione zgodnie z rozszerzeniem nazwy pliku.
**st_mtime**|Czas ostatniej modyfikacji pliku.
**st_nlink**|Zawsze 1 w systemach plików niż NTFS.
**st_rdev**|Numer dysku z plikiem dysku (taka sama jak **st_dev**).
**st_size**|Rozmiar pliku w bajtach; 64-bitową liczbę całkowitą dla zmian za pomocą **i64** sufiks.
**st_uid**|Identyfikator liczbowy użytkownika będącego właścicielem pliku (specyficzne dla systemu UNIX). To pole będzie zawsze zero w systemach Windows. Przekierowanego pliku zostanie sklasyfikowany jako pliku Windows.

Jeśli *ścieżki* odwołuje się do urządzenia, **st_size**, różnych pól godziny **st_dev**, i **st_rdev** pola w **_stat**  struktury są bez znaczenia. Ponieważ STAT. Zastosowań H [_dev_t](../../c-runtime-library/standard-types.md) typ typów zdefiniowanych w. Godz., musi zawierać typy. Godz. przed STAT. H w kodzie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**stałe pola_stat**, **_stat32 —**, **_stat64**, **_stati64**, **_stat32i64 —**, **_stat64i32 —**|\<sys/types.h > następuje \<sys/stat.h >|\<errno.h>|
|**_wstat —**, **_wstat32 —**, **_wstat64**, **_wstati64**, **_wstat32i64 —**, **_wstat64i32 —**|\<sys/types.h > następuje \<sys/stat.h > lub \<wchar.h >|\<errno.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
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

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_setmbcp](setmbcp.md)<br/>
