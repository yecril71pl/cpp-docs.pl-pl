---
title: _stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32
ms.date: 4/2/2020
api_name:
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
- _o__stat32
- _o__stat32i64
- _o__stat64
- _o__stat64i32
- _o__wstat32
- _o__wstat32i64
- _o__wstat64
- _o__wstat64i32
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 32a96a93eb8a18e366ac7a075b414dbca732fb61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355418"
---
# <a name="_stat-_stat32-_stat64-_stati64-_stat32i64-_stat64i32-_wstat-_wstat32-_wstat64-_wstati64-_wstat32i64-_wstat64i32"></a>_stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32

Uzyskaj informacje o stanie w pliku.

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
Wskaźnik do ciągu zawierającego ścieżkę istniejącego pliku lub katalogu.

*Buforu*<br/>
Wskaźnik do struktury, która przechowuje wyniki.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość 0, jeśli zostaną uzyskane informacje o stanie pliku. Zwracana wartość -1 wskazuje błąd, w którym to przypadku **errno** jest ustawiona na **ENOENT,** wskazując, że nie można odnaleźć nazwy pliku lub ścieżki. Zwracana wartość **EINVAL** wskazuje nieprawidłowy parametr; **errno** jest również ustawiony na **EINVAL** w tym przypadku.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr,](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) aby uzyskać więcej informacji na ten temat i inne kody zwrotne.

Stempel daty w pliku może być reprezentowany, jeśli jest późniejszy niż północ, 1 stycznia 1970 r. i przed 23:59:59, 31 grudnia 3000, UTC, chyba że używasz **_stat32** lub **_wstat32**lub zdefiniowałeś **_USE_32BIT_TIME_T**, w którym to przypadku data może być reprezentowana tylko do 23:59:59 18 stycznia 2038, UTC.

## <a name="remarks"></a>Uwagi

Funkcja **_stat** uzyskuje informacje o pliku lub katalogu określonym przez *ścieżkę* i przechowuje je w strukturze wskazywowej przez *bufor*. **_stat** automatycznie obsługuje argumenty ciągów wielobajtowych, rozpoznając sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową wielobajtową.

**_wstat** jest szerokoznakową wersją **_stat**; argument *path* do **_wstat** jest ciągiem znaków o szerokim charakterze. **_wstat** i **_stat** zachowywać się identycznie, z tą różnicą, że **_wstat** nie obsługuje ciągów znaków wielobajtowych.

Odmiany tych funkcji obsługują typy czasu 32- lub 64-bitowego oraz 32- lub 64-bitowe długości plików. Pierwszy przyrostek numeryczny (**32** lub **64**) wskazuje rozmiar używanego typu czasu; drugi sufiks to **i32** lub **i64**, wskazujący, czy rozmiar pliku jest reprezentowany jako 32-bitowa czy 64-bitowa liczba całkowita.

**_stat** jest odpowiednikiem **_stat64i32,** a **struct** **_stat** struktury zawiera czas 64-bitowy. Jest to prawdą, chyba że **_USE_32BIT_TIME_T** jest zdefiniowany, w którym to przypadku stare zachowanie jest w mocy; **_stat** używa czasu 32-bitowego, a **_stat** **struktury** zawiera czas 32-bitowy. To samo dotyczy **_stati64**.

> [!NOTE]
> **_wstat** nie działa z łączami symbolicznymi systemu Windows Vista. W takich przypadkach **_wstat** zawsze zgłasza rozmiar pliku 0. **_stat** działa poprawnie z dowiązań symbolicznych.

Ta funkcja sprawdza poprawność jego parametrów. Jeśli *ścieżka* lub *bufor* ma **wartość NULL**, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [yd.](../../c-runtime-library/parameter-validation.md)

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_stat"></a>Zmiany typu i długości pliku _stat

|Funkcje|_USE_32BIT_TIME_T zdefiniowane?|Typ czasu|Typ długości pliku|
|---------------|------------------------------------|---------------|----------------------|
|**_stat** **, _wstat**|Nieokreślona|64-bitowy|32-bitowa|
|**_stat** **, _wstat**|Zdefiniowane|32-bitowa|32-bitowa|
|**_stat32** **, _wstat32**|Definicja makra nie ma na nie wpływu|32-bitowa|32-bitowa|
|**_stat64** **, _wstat64**|Definicja makra nie ma na nie wpływu|64-bitowy|64-bitowy|
|**_stati64**, **_wstati64**|Nieokreślona|64-bitowy|64-bitowy|
|**_stati64**, **_wstati64**|Zdefiniowane|32-bitowa|64-bitowy|
|**_stat32i64** **, _wstat32i64**|Definicja makra nie ma na nie wpływu|32-bitowa|64-bitowy|
|**_stat64i32** **, _wstat64i32**|Definicja makra nie ma na nie wpływu|64-bitowy|32-bitowa|

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstat**|**_stat**|**_stat**|**_wstat**|
|**_tstat64**|**_stat64**|**_stat64**|**_wstat64**|
|**_tstati64**|**_stati64**|**_stati64**|**_wstati64**|
|**_tstat32i64**|**_stat32i64**|**_stat32i64**|**_wstat32i64**|
|**_tstat64i32**|**_stat64i32**|**_stat64i32**|**_wstat64i32**|

Struktura **_stat,** zdefiniowana w pliku SYS\STAT. H, zawiera następujące pola.

|Pole||
|-|-|
| **st_gid** | Numeryczny identyfikator grupy, która jest właścicielem pliku (specyficzne dla systemu UNIX) To pole będzie zawsze zerowe w systemach Windows. Przekierowany plik jest klasyfikowany jako plik systemu Windows. |
| **st_atime** | Czas ostatniego dostępu do pliku. Jest prawidłowy w systemie plików NTFS, ale nie na dyskach sformatowanych w formacie FAT. |
| **st_ctime** | Czas tworzenia pliku. Jest prawidłowy w systemie plików NTFS, ale nie na dyskach sformatowanych w formacie FAT. |
| **st_dev** | Numer dysku zawierającego plik (taki sam jak **st_rdev**). |
| **st_ino** | Numer węzła informacyjnego **(i-węzła)** dla pliku (specyficzny dla systemu UNIX). W systemach plików systemu UNIX **i-węzła** opisano datę pliku i sygnatury czasowe, uprawnienia i zawartość. Gdy pliki są ze sobą mocno powiązane, mają ten sam **i-węzł**. **I-węzła**, a zatem **st_ino**, nie ma znaczenia w systemach plików FAT, HPFS lub NTFS. |
| **st_mode** | Maska bitowa do informacji o trybie pliku. Bit **_S_IFDIR** jest ustawiany, jeśli *ścieżka* określa katalog; **bit _S_IFREG** jest ustawiany, jeśli *ścieżka* określa zwykły plik lub urządzenie. Bity odczytu/zapisu użytkownika są ustawiane zgodnie z trybem uprawnień pliku; bity wykonania użytkownika są ustawiane zgodnie z rozszerzeniem nazwy pliku. |
| **st_mtime** | Czas ostatniej modyfikacji pliku. |
| **st_nlink** | Zawsze 1 w systemach plików innych niż NTFS. |
| **st_rdev** | Numer dysku zawierającego plik (taki sam jak **st_dev**). |
| **st_size** | Rozmiar pliku w bajtach; 64-bitową całkowitej liczby dla odmian z przyrostkiem **i64.** |
| **st_uid** | Numeryczny identyfikator użytkownika, który jest właścicielem pliku (specyficzny dla systemu UNIX). To pole będzie zawsze zerowe w systemach Windows. Przekierowany plik jest klasyfikowany jako plik systemu Windows. |

Jeśli *ścieżka* odnosi się do urządzenia, **st_size,** różne pola czasu, **st_dev**i **st_rdev** pola w **strukturze _stat** są bez znaczenia. Ponieważ STAT. H używa [typu _dev_t](../../c-runtime-library/standard-types.md) zdefiniowanego w typach. H, należy dołączyć TYPY. H przed STAT. H w kodzie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**_stat** **, _stat32,** **_stat64,** **_stati64,** **_stat32i64,** **_stat64i32**|\<sys/types.h> następuje \<sys/stat.h>|\<> errno.h|
|**_wstat** **, _wstat32,** **_wstat64,** **_wstati64,** **_wstat32i64,** **_wstat64i32**|\<sys/types.h> następuje \<sys/stat.h> \<lub wchar.h>|\<> errno.h|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_setmbcp](setmbcp.md)<br/>
