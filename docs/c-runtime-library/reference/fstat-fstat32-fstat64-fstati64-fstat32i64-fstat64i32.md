---
title: _fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32
ms.date: 4/2/2020
api_name:
- _fstat32
- _fstat64
- _fstati64
- _fstat
- _fstat64i32
- _fstat32i64
- _o__fstat32
- _o__fstat32i64
- _o__fstat64
- _o__fstat64i32
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
ms.openlocfilehash: 02d297fec2ada545a8b693abacfecc7981149dae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345673"
---
# <a name="_fstat-_fstat32-_fstat64-_fstati64-_fstat32i64-_fstat64i32"></a>_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32

Pobiera informacje o otwartym pliku.

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

*Fd*<br/>
Deskryptor pliku otwartego pliku.

*Buforu*<br/>
Wskaźnik do struktury do przechowywania wyników.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli uzyskano informacje o stanie pliku. Zwracana wartość -1 oznacza błąd. Jeśli deskryptor pliku jest nieprawidłowy lub *bufor* ma **wartość NULL,** wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w polu [Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **EBADF**, w przypadku nieprawidłowego deskryptora pliku lub **EINVAL**, jeśli *bufor* ma **wartość NULL**.

## <a name="remarks"></a>Uwagi

Funkcja **_fstat** uzyskuje informacje o otwartym pliku skojarzonym z *fd* i przechowuje go w strukturze wskazywionej przez *bufor*. Struktura **_stat,** zdefiniowana w pliku SYS\Stat.h, zawiera następujące pola.

|Pole|Znaczenie|
|-|-|
| **st_atime** | Czas ostatniego dostępu do pliku. |
| **st_ctime** | Czas utworzenia pliku. |
| **st_dev** | Jeśli urządzenie, *fd*; w przeciwnym razie 0. |
| **st_mode** | Maska bitowa do informacji o trybie pliku. Bit **_S_IFCHR** jest ustawiany, jeśli *fd* odnosi się do urządzenia. Bit **_S_IFREG** jest ustawiany, jeśli *fd* odwołuje się do zwykłego pliku. Bity odczytu/zapisu są ustawiane zgodnie z trybem uprawnień pliku. **_S_IFCHR** i inne stałe są zdefiniowane w pliku SYS\Stat.h. |
| **st_mtime** | Czas ostatniej modyfikacji pliku. |
| **st_nlink** | Zawsze 1 w systemach plików innych niż NTFS. |
| **st_rdev** | Jeśli urządzenie, *fd*; w przeciwnym razie 0. |
| **st_size** | Rozmiar pliku w bajtach. |

Jeśli *fd* odnosi się do urządzenia, **pola st_atime,** **st_ctime**, **st_mtime**i **st_size** nie mają znaczenia.

Ponieważ Stat.h używa [typu _dev_t,](../../c-runtime-library/standard-types.md) który jest zdefiniowany w Types.h, należy dołączyć Types.h przed Stat.h w kodzie.

**_fstat64**, która wykorzystuje strukturę **__stat64,** umożliwia wyrażenie dat tworzenia plików do 23:59:59, 31 grudnia 3000, UTC; podczas gdy pozostałe funkcje reprezentują tylko daty do 23:59:59 18 stycznia 2038, UTC. Północ, 1 stycznia 1970 r., jest dolną granicą zakresu dat dla wszystkich tych funkcji.

Odmiany tych funkcji obsługują 32-bitowe lub 64-bitowe typy czasu oraz 32-bitowe lub 64-bitowe długości plików. Pierwszy przyrostek numeryczny (**32** lub **64**) wskazuje rozmiar używanego typu czasu; drugi sufiks to **i32** lub **i64**, wskazujący, czy rozmiar pliku jest reprezentowany jako 32-bitowa czy 64-bitowa liczba całkowita.

**_fstat** jest odpowiednikiem **_fstat64i32,** a **_stat** **struktury** zawiera czas 64-bitowy. Jest to prawdą, chyba że **_USE_32BIT_TIME_T** jest zdefiniowany, w którym to przypadku stare zachowanie jest w mocy; **_fstat** używa czasu 32-bitowego, a **_stat** **struktury** zawiera czas 32-bitowy. To samo dotyczy **_fstati64**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_stat"></a>Zmiany typu i długości pliku _stat

|Funkcje|_USE_32BIT_TIME_T zdefiniowane?|Typ czasu|Typ długości pliku|
|---------------|------------------------------------|---------------|----------------------|
|**_fstat**|Nieokreślona|64-bitowy|32-bitowa|
|**_fstat**|Zdefiniowane|32-bitowa|32-bitowa|
|**_fstat32**|Definicja makra nie ma na nie wpływu|32-bitowa|32-bitowa|
|**_fstat64**|Definicja makra nie ma na nie wpływu|64-bitowy|64-bitowy|
|**_fstati64**|Nieokreślona|64-bitowy|64-bitowy|
|**_fstati64**|Zdefiniowane|32-bitowa|64-bitowy|
|**_fstat32i64**|Definicja makra nie ma na nie wpływu|32-bitowa|64-bitowy|
|**_fstat64i32**|Definicja makra nie ma na nie wpływu|64-bitowy|32-bitowa|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fstat**|\<sys/stat.h> i \<sys/types.h>|
|**_fstat32**|\<sys/stat.h> i \<sys/types.h>|
|**_fstat64**|\<sys/stat.h> i \<sys/types.h>|
|**_fstati64**|\<sys/stat.h> i \<sys/types.h>|
|**_fstat32i64**|\<sys/stat.h> i \<sys/types.h>|
|**_fstat64i32**|\<sys/stat.h> i \<sys/types.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_filelength, _filelengthi64](filelength-filelengthi64.md)<br/>
[_stat, funkcje _wstat](stat-functions.md)<br/>
