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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 81c272187c681010e7b8560d43f2fad87e1e0fdc
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910125"
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

*proces*<br/>
Deskryptor pliku otwartego pliku.

*buforu*<br/>
Wskaźnik na strukturę, w której mają być przechowywane wyniki.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli informacje o stanie pliku są uzyskiwane. Zwracana wartość-1 wskazuje na błąd. Jeśli deskryptor pliku jest nieprawidłowy lub *bufor* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EBADF**, w przypadku nieprawidłowego deskryptora pliku lub do **EINVAL**, jeśli *buffer* ma **wartość null**.

## <a name="remarks"></a>Uwagi

Funkcja **_fstat** uzyskuje informacje o otwartym pliku skojarzonym z *FD* i zapisuje je w strukturze wskazywanej przez *bufor*. Struktura **_stat** , zdefiniowana w SYS\Stat.h, zawiera następujące pola.

|Pole|Znaczenie|
|-|-|
| **st_atime** | Godzina ostatniego dostępu do pliku. |
| **st_ctime** | Czas utworzenia pliku. |
| **st_dev** | Jeśli urządzenie, *FD*; w przeciwnym razie 0. |
| **st_mode** | Maska bitów dla informacji w trybie plików. **_S_IFCHR** bit jest ustawiony, jeśli *FD* odwołuje się do urządzenia. **_S_IFREG** bit jest ustawiony, jeśli *FD* odwołuje się do zwykłego pliku. Bity odczytu/zapisu są ustawiane zgodnie z trybem uprawnień pliku. **_S_IFCHR** i inne stałe są zdefiniowane w SYS\Stat.h. |
| **st_mtime** | Godzina ostatniej modyfikacji pliku. |
| **st_nlink** | Zawsze 1 w systemach plików innych niż NTFS. |
| **st_rdev** | Jeśli urządzenie, *FD*; w przeciwnym razie 0. |
| **st_size** | Rozmiar pliku w bajtach. |

Jeśli *FD* odwołuje się do urządzenia, pola **st_atime**, **st_ctime**, **st_mtime**i **st_size** nie mają znaczenia.

Ponieważ stat. h używa typu [_dev_t](../../c-runtime-library/standard-types.md) , który jest zdefiniowany w typach. h, należy dołączyć typy. h przed stat. h w kodzie.

**_fstat64**, który używa struktury **__stat64** , umożliwia określenie dat tworzenia plików do 23:59:59, 31 grudnia 3000, UTC; natomiast inne funkcje reprezentują daty do 23:59:59 stycznia 18, 2038, UTC. Północ, 1 stycznia 1970, to Dolna granica zakresu dat dla wszystkich tych funkcji.

Różnice tych funkcji obsługują 32-bitowe lub 64-bitowe typy czasu i 32-bitowe lub 64-bitowe długości plików. Pierwszy sufiks numeryczny (**32** lub **64**) wskazuje rozmiar używanego typu czasu; drugi sufiks jest **I32** lub **I64**, wskazując, czy rozmiar pliku jest reprezentowany jako 32-bitowa czy 64-bitowa liczba całkowita.

**_fstat** jest odpowiednikiem **_fstat64i32**, a **Struktura** **_stat** zawiera czas 64-bitowy. Jest to prawdziwe, chyba że **_USE_32BIT_TIME_T** jest zdefiniowany, w takim przypadku stare zachowanie jest stosowane; **_fstat** używa czasu 32-bitowego, a **struktura** **_stat** zawiera 32-bitowy czas. Ta sama wartość dotyczy **_fstati64**.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_stat"></a>Typ czasu i typ długości pliku Wariacje _stat

|Funkcje|_USE_32BIT_TIME_T zdefiniowane?|Typ czasu|Typ długości pliku|
|---------------|------------------------------------|---------------|----------------------|
|**_fstat**|Nieokreślona|64-bitowa|32-bitowa|
|**_fstat**|Określonych|32-bitowa|32-bitowa|
|**_fstat32**|Nie dotyczy definicji makra|32-bitowa|32-bitowa|
|**_fstat64**|Nie dotyczy definicji makra|64-bitowa|64-bitowa|
|**_fstati64**|Nieokreślona|64-bitowa|64-bitowa|
|**_fstati64**|Określonych|32-bitowa|64-bitowa|
|**_fstat32i64**|Nie dotyczy definicji makra|32-bitowa|64-bitowa|
|**_fstat64i32**|Nie dotyczy definicji makra|64-bitowa|32-bitowa|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fstat**|\<sys/stat. h> i \<sys/Types. h>|
|**_fstat32**|\<sys/stat. h> i \<sys/Types. h>|
|**_fstat64**|\<sys/stat. h> i \<sys/Types. h>|
|**_fstati64**|\<sys/stat. h> i \<sys/Types. h>|
|**_fstat32i64**|\<sys/stat. h> i \<sys/Types. h>|
|**_fstat64i32**|\<sys/stat. h> i \<sys/Types. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
