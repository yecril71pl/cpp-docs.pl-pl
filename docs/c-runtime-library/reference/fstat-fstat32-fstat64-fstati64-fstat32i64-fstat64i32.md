---
title: _fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32
ms.date: 11/04/2016
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
ms.openlocfilehash: 36d8b0d6480266f86136119a470fb7af5859a5b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332800"
---
# <a name="fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32"></a>_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32

Pobiera informacje o otwartego pliku.

## <a name="syntax"></a>Składnia

```C
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

### <a name="parameters"></a>Parametry

*FD*<br/>
Deskryptor pliku otwartego pliku.

*buffer*<br/>
Wskaźnik do struktury do przechowywania wyników.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeżeli uzyskano informacje o stanie pliku. Zwracana wartość-1 wskazuje błąd. Jeżeli deskryptor pliku jest nieprawidłowa lub *buforu* jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EBADF**, w przypadku nieprawidłowego deskryptora pliku lub do **EINVAL**, jeśli *buforu* jest **NULL**.

## <a name="remarks"></a>Uwagi

**_Fstat** funkcja uzyskuje informacje o otwartego pliku, które są skojarzone z *fd* i zapisuje go w strukturze wskazywany przez *buforu*. **_Stat** struktury, zdefiniowanego w SYS\Stat.h, zawiera następujące pola.

|Pole|Znaczenie|
|-|-|
| **st_atime** | Czas ostatniego dostępu do plików. |
| **st_ctime** | Godzina utworzenia pliku. |
| **st_dev** | Jeśli urządzenie, *fd*; w przeciwnym razie 0. |
| **st_mode** | Maska bitów informacji tryb pliku. **_S_IFCHR** Jeśli ustawiono bit *fd* odwołuje się do urządzenia. **_S_IFREG** Jeśli ustawiono bit *fd* odwołuje się do zwykłego pliku. Bity odczytu/zapisu są ustawione zgodnie z trybu uprawnienia pliku. **_S_IFCHR** i inne stałe są definiowane w SYS\Stat.h. |
| **st_mtime** | Czas ostatniej modyfikacji pliku. |
| **st_nlink** | Zawsze 1 w systemach plików niż NTFS. |
| **st_rdev** | Jeśli urządzenie, *fd*; w przeciwnym razie 0. |
| **st_size** | Rozmiar pliku w bajtach. |

Jeśli *fd* odwołuje się do urządzenia, **st_atime**, **st_ctime**, **st_mtime**, i **st_size** pola są nie ma istotnego znaczenia.

Ponieważ używa Stat.h [_dev_t](../../c-runtime-library/standard-types.md) typ, który jest zdefiniowany w Types.h, musi zawierać Types.h przed Stat.h w kodzie.

**_fstat64**, który używa **__stat64 —** struktury, umożliwia tworzenie pliku daty do za pośrednictwem 23:59:59, 31 grudnia 3000, UTC, podczas gdy inne funkcje przedstawia tylko daty do 23:59:59 18 stycznia 2038 R. UTC. Północy 1 stycznia 1970 r., to dolna granica zakresu dat dla tych funkcji.

Różnice te funkcje obsługują typy czasu 32-bitową lub 64-bitowe i 32-bitową lub 64-bitowego pliku długości. Pierwszy liczbowego sufiksu (**32** lub **64**) wskazuje rozmiar czasu używany typ; drugi sufiks jest **i32** lub **i64**, wskazująca, czy rozmiar pliku jest reprezentowany jako 32-bitowy lub 64-bitową liczbę całkowitą.

**_fstat** jest odpowiednikiem **_fstat64i32 —**, i **struktury** **_stat** zawiera godzinę 64-bitowych. Jest to wartość true, chyba że **_USE_32BIT_TIME_T** jest zdefiniowany, w którym to przypadku stare zachowanie obowiązuje; **_fstat** korzysta z danym 32-bitowe i **struktury** **_stat** zawiera godzinę 32-bitowych. Dotyczy to także **_fstati64**.

### <a name="time-type-and-file-length-type-variations-of-stat"></a>Typ czasu i zmian typu długość pliku _stat

|Funkcje|_USE_32BIT_TIME_T zdefiniowane?|Typ czasu|Typ długość pliku|
|---------------|------------------------------------|---------------|----------------------|
|**_fstat**|Nie zdefiniowano|64-bitowy|32-bitowa|
|**_fstat**|Definicja|32-bitowa|32-bitowa|
|**_fstat32**|Nie dotyczy definicji makra|32-bitowa|32-bitowa|
|**_fstat64**|Nie dotyczy definicji makra|64-bitowy|64-bitowy|
|**_fstati64**|Nie zdefiniowano|64-bitowy|64-bitowy|
|**_fstati64**|Definicja|32-bitowa|64-bitowy|
|**_fstat32i64**|Nie dotyczy definicji makra|32-bitowa|64-bitowy|
|**_fstat64i32**|Nie dotyczy definicji makra|64-bitowy|32-bitowa|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fstat**|\<sys/stat.h > i \<sys/types.h >|
|**_fstat32**|\<sys/stat.h > i \<sys/types.h >|
|**_fstat64**|\<sys/stat.h > i \<sys/types.h >|
|**_fstati64**|\<sys/stat.h > i \<sys/types.h >|
|**_fstat32i64**|\<sys/stat.h > i \<sys/types.h >|
|**_fstat64i32**|\<sys/stat.h > i \<sys/types.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
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

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_filelength, _filelengthi64](filelength-filelengthi64.md)<br/>
[_stat, _wstat — funkcje](stat-functions.md)<br/>
