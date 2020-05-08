---
title: _lseek, _lseeki64
ms.date: 4/2/2020
api_name:
- _lseeki64
- _lseek
- _o__lseek
- _o__lseeki64
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
ms.openlocfilehash: b99793c7d3f16eceec20c90f29824bca8321fb12
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911304"
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

*Przesunięcie*<br/>
Liczba bajtów od *początku*.

*źródł*<br/>
Pozycja początkowa.

## <a name="return-value"></a>Wartość zwracana

**_lseek** zwraca przesunięcie (w bajtach) nowej pozycji od początku pliku. **_lseeki64** zwraca przesunięcie w 64-bitowej liczbie całkowitej. Funkcja zwraca wartość-1L, aby wskazać błąd. Jeśli przeszedł nieprawidłowy parametr, taki jak zły deskryptor pliku lub wartość *pochodzenia* jest nieprawidłowa lub pozycja określona przez *przesunięcie* jest przed początkiem pliku, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EBADF** i Return-1L. Na urządzeniach bez możliwości wyszukiwania (takich jak terminale i drukarki) zwracana wartość jest niezdefiniowana.

Aby uzyskać więcej informacji o tych i innych kodach błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_lseek** przenosi wskaźnik pliku skojarzony z *FD* do nowej lokalizacji, która jest *przesunięta* bajtów od *początku*. Kolejna operacja w pliku występuje w nowej lokalizacji. Argument *Origin* musi być jedną z następujących stałych, które są zdefiniowane w stdio. h.

|wartość *pochodzenia*||
|-|-|
| **SEEK_SET** | Początek pliku. |
| **SEEK_CUR** | Bieżąca pozycja wskaźnika pliku. |
| **SEEK_END** | Koniec pliku. |

Za pomocą **_lseek** można zmienić położenie wskaźnika w dowolnym miejscu pliku lub poza końcem pliku.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lseek**|\<IO. h>|
|**_lseeki64**|\<IO. h>|

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

## <a name="see-also"></a>Zobacz też

[We/wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[fseek, _fseeki64](fseek-fseeki64.md)<br/>
[_tell, _telli64](tell-telli64.md)<br/>
