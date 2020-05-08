---
title: _chsize
ms.date: 4/2/2020
api_name:
- _chsize
- _o__chsize
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 5b9b58cf3ca4e167b5d54f871ac31c5295adc48b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917203"
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

*size*<br/>
Nowa długość pliku w bajtach.

## <a name="return-value"></a>Wartość zwracana

**_chsize** zwraca wartość 0, jeśli rozmiar pliku został pomyślnie zmieniony. Zwracana wartość-1 wskazuje błąd: **errno** jest ustawiona na **EACCES** , jeśli określony plik jest tylko do odczytu lub określony plik jest zablokowany w celu uzyskania dostępu do **EBADF** , jeśli deskryptor jest nieprawidłowy, **ENOSPC** , jeśli na urządzeniu nie pozostawiono miejsca, lub **EINVAL** , jeśli *rozmiar* jest mniejszy od zera.

Aby uzyskać więcej informacji na temat tych i innych kodów powrotu, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Uwagi

Funkcja **_chsize** rozszerza lub obcina plik skojarzony z *FD* do długości określonej przez *rozmiar*. Plik musi być otwarty w trybie, który umożliwia zapisywanie. Jeśli plik zostanie rozszerzony, dołączane są znaki null (' \ 0 '). Jeśli plik zostanie obcięty, wszystkie dane od końca skróconego pliku do oryginalnej długości pliku zostaną utracone.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *rozmiar* jest mniejszy niż zero lub *FD* jest nieprawidłowym deskryptorem pliku, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_chsize**|\<IO. h>|\<errno. h>|

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

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
