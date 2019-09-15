---
title: _lseek, _lseeki64
ms.date: 11/04/2016
api_name:
- _lseeki64
- _lseek
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
- _lseeki64
- _lseek
- lseeki64
helpviewer_keywords:
- lseek function
- _lseek function
- _lseeki64 function
- lseeki64 function
- file pointers [C++], moving
- seek file pointers
ms.assetid: aba8a768-d40e-48c3-b38e-473dbd782f93
ms.openlocfilehash: 67bcce2a9936cd09973e8ddf1828704944866439
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952987"
---
# <a name="_lseek-_lseeki64"></a>_lseek, _lseeki64

Przenosi wskaźnik pliku do określonej lokalizacji.

## <a name="syntax"></a>Składnia

```C
long _lseek(
   int fd,
   long offset,
   int origin
);
__int64 _lseeki64(
   int fd,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>Parametry

*proces*<br/>
Deskryptor pliku odwołujący się do otwartego pliku.

*offset*<br/>
Liczba bajtów od *początku*.

*źródł*<br/>
Pozycja początkowa.

## <a name="return-value"></a>Wartość zwracana

**_lseek** zwraca przesunięcie (w bajtach) nowej pozycji od początku pliku. **_lseeki64** zwraca przesunięcie w 64-bitowej liczbie całkowitej. Funkcja zwraca wartość-1L, aby wskazać błąd. Jeśli przeszedł nieprawidłowy parametr, taki jak zły deskryptor pliku lub wartość *pochodzenia* jest nieprawidłowa lub pozycja określona przez *przesunięcie* jest przed początkiem pliku, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [parametrze Sprawdzanie poprawności](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EBADF** i Return-1L. Na urządzeniach bez możliwości wyszukiwania (takich jak terminale i drukarki) zwracana wartość jest niezdefiniowana.

Aby uzyskać więcej informacji o tych i innych kodach błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_lseek** przenosi wskaźnik pliku skojarzony z *FD* do nowej lokalizacji, która jest *przesunięta* bajtów od *początku*. Kolejna operacja w pliku występuje w nowej lokalizacji. Argument *Origin* musi być jedną z następujących stałych, które są zdefiniowane w stdio. h.

|wartość *pochodzenia*||
|-|-|
| **SEEK_SET** | Początek pliku. |
| **SEEK_CUR** | Bieżąca pozycja wskaźnika pliku. |
| **SEEK_END** | Koniec pliku. |

Możesz użyć **_lseek** , aby zmienić położenie wskaźnika w dowolnym miejscu pliku lub poza końcem pliku.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lseek**|\<io.h>|
|**_lseeki64**|\<io.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_lseek.c
/* This program first opens a file named lseek.txt.
* It then uses _lseek to find the beginning of the file,
* to find the current position in the file, and to find
* the end of the file.
*/

#include <io.h>
#include <fcntl.h>
#include <stdlib.h>
#include <stdio.h>
#include <share.h>

int main( void )
{
   int fh;
   long pos;               /* Position of file pointer */
   char buffer[10];

   _sopen_s( &fh, "crt_lseek.c_input", _O_RDONLY, _SH_DENYNO, 0 );

   /* Seek the beginning of the file: */
   pos = _lseek( fh, 0L, SEEK_SET );
   if( pos == -1L )
      perror( "_lseek to beginning failed" );
   else
      printf( "Position for beginning of file seek = %ld\n", pos );

   /* Move file pointer a little */
    _read( fh, buffer, 10 );

   /* Find current position: */
   pos = _lseek( fh, 0L, SEEK_CUR );
   if( pos == -1L )
      perror( "_lseek to current position failed" );
   else
      printf( "Position for current position seek = %ld\n", pos );

   /* Set the end of the file: */
   pos = _lseek( fh, 0L, SEEK_END );
   if( pos == -1L )
      perror( "_lseek to end failed" );
   else
      printf( "Position for end of file seek = %ld\n", pos );

   _close( fh );
}
```

### <a name="input-crt_lseekc_input"></a>Dane wejściowe: crt_lseek. c_input

```Input
Line one.
Line two.
Line three.
Line four.
Line five.
```

### <a name="output"></a>Dane wyjściowe

```Output
Position for beginning of file seek = 0
Position for current position seek = 10
Position for end of file seek = 57
```

## <a name="see-also"></a>Zobacz także

[We/wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[fseek, _fseeki64](fseek-fseeki64.md)<br/>
[_tell, _telli64](tell-telli64.md)<br/>
