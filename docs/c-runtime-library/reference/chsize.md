---
title: _chsize — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/29/2018
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _chsize
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _chsize
dev_langs:
- C++
helpviewer_keywords:
- size
- _chsize function
- size, changing file
- files [C++], changing size
- chsize function
ms.assetid: b3e881c5-7b27-4837-a3d4-c51591ab10ff
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cec2d058b356cbb7624ee6dd0bbecdfb55c64813
ms.sourcegitcommit: cdd4808dcb274bbb29618286df4d1d4acd35b9bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2018
---
# <a name="chsize"></a>_chsize

Zmienia rozmiar pliku. Bezpieczniejsza wersja jest dostępna; zobacz [_chsize_s —](../../c-runtime-library/reference/chsize-s.md).

## <a name="syntax"></a>Składnia

```C
int _chsize(
   int fd,
   long size
);
```

### <a name="parameters"></a>Parametry
*FD*<br/>
Plik deskryptora odwołujących się do otwartego pliku.

*Rozmiar*<br/>
Długość nowego pliku w bajtach.

## <a name="return-value"></a>Wartość zwracana

_chsize —` returns the value 0 if the file size is successfully changed. A return value of -1 indicates an error: `errno` is set to `eacces —` if the specified file is read-only or the specified file is locked against access, to `ebadf —` if the descriptor is invalid, `enospc —` if no space is left on the device, or `einval —` if `rozmiar "jest mniejsza od zera.

Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) kody powrotne — Aby uzyskać więcej informacji na temat tych i innych.

## <a name="remarks"></a>Uwagi

`_chsize` Funkcja rozszerza lub obcina plik skojarzony z `fd` do długości określonej przez `size`. Plik musi być otwarty w trybie umożliwiającym zapis. Znaki null ('\0') są dołączane, jeśli plik zostanie rozszerzony. Jeśli plik został obcięty, wszystkie dane na końcu pliku skróconą długość oryginalnego pliku zostaną utracone.

Ta funkcja weryfikuje jego parametrów. Jeśli `size` jest mniejszy od zera lub `fd` deskryptor nieprawidłowego pliku, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|`_chsize`|\<io.h>|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
[_close](../../c-runtime-library/reference/close.md)<br/>
[_sopen, _wsopen](../../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_open, _wopen](../../c-runtime-library/reference/open-wopen.md)<br/>
