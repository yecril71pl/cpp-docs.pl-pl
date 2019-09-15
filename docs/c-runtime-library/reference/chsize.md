---
title: _chsize
ms.date: 03/29/2018
api_name:
- _chsize
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _chsize
helpviewer_keywords:
- size
- _chsize function
- size, changing file
- files [C++], changing size
- chsize function
ms.assetid: b3e881c5-7b27-4837-a3d4-c51591ab10ff
ms.openlocfilehash: 7fe07b2261396be491b833ff52186024edd0b919
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942976"
---
# <a name="_chsize"></a>_chsize

Zmienia rozmiar pliku. Dostępna jest bezpieczniejsza wersja; Zobacz [_chsize_s](chsize-s.md).

## <a name="syntax"></a>Składnia

```C
int _chsize(
   int fd,
   long size
);
```

### <a name="parameters"></a>Parametry

*proces*<br/>
Deskryptor pliku odwołujący się do otwartego pliku.

*zmienia*<br/>
Nowa długość pliku w bajtach.

## <a name="return-value"></a>Wartość zwracana

**_chsize** zwraca wartość 0, jeśli rozmiar pliku został pomyślnie zmieniony. Zwracana wartość-1 wskazuje błąd: **errno** jest ustawiona na **EACCES** , jeśli określony plik jest tylko do odczytu lub określony plik jest zablokowany w celu uzyskania dostępu, do **EBADF** , jeśli deskryptor jest nieprawidłowy, **ENOSPC** Jeśli na urządzeniu nie ma miejsca. **EINVAL** , jeśli *rozmiar* jest mniejszy od zera.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) , aby uzyskać więcej informacji na temat tych i innych kodów powrotu.

## <a name="remarks"></a>Uwagi

Funkcja **_chsize** rozszerza lub obcina plik skojarzony z *FD* do długości określonej przez *rozmiar*. Plik musi być otwarty w trybie, który umożliwia zapisywanie. Jeśli plik zostanie rozszerzony, dołączane są znaki null (' \ 0 '). Jeśli plik zostanie obcięty, wszystkie dane od końca skróconego pliku do oryginalnej długości pliku zostaną utracone.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *rozmiar* jest mniejszy niż zero lub *FD* jest nieprawidłowym deskryptorem pliku, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_chsize**|\<io.h>|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_chsize.c
// This program uses _filelength to report the size
// of a file before and after modifying it with _chsize.

#include <io.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <share.h>

int main( void )
{
   int fh, result;
   unsigned int nbytes = BUFSIZ;

   // Open a file
   if( _sopen_s( &fh, "data", _O_RDWR | _O_CREAT, _SH_DENYNO,
                 _S_IREAD | _S_IWRITE ) == 0 )
   {
      printf( "File length before: %ld\n", _filelength( fh ) );
      if( ( result = _chsize( fh, 329678 ) ) == 0 )
         printf( "Size successfully changed\n" );
      else
         printf( "Problem in changing the size\n" );
      printf( "File length after:  %ld\n", _filelength( fh ) );
      _close( fh );
   }
}
```

```Output
File length before: 0
Size successfully changed
File length after:  329678
```

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
