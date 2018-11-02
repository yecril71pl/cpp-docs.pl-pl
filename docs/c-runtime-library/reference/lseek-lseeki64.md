---
title: _lseek, _lseeki64
ms.date: 11/04/2016
apiname:
- _lseeki64
- _lseek
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
ms.openlocfilehash: 19a312bcc3cdeea82bcebce6da95e26ef88992b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541690"
---
# <a name="lseek-lseeki64"></a>_lseek, _lseeki64

Przesuwa wskaźnik pliku do określonej lokalizacji.

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

*FD*<br/>
Deskryptor pliku odnoszące się do otwartego pliku.

*offset*<br/>
Liczba bajtów z *pochodzenia*.

*Punkt początkowy*<br/>
Pozycja początkowa.

## <a name="return-value"></a>Wartość zwracana

**_lseek —** zwraca przesunięcie w bajtach, stanowisko od początku pliku. **_lseeki64 —** zwraca przesunięcie na 64-bitową liczbę całkowitą. Funkcja zwraca wartość-1 L, aby wskazać błąd. Jeśli przekazano nieprawidłowy parametr, takich jak deskryptora nieprawidłowego pliku lub wartość *pochodzenia* jest nieprawidłowy lub pozycji określonej przez *przesunięcie* jest przed rozpoczęciem plik jest nieprawidłowy parametr uchwytu wywoływana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EBADF** i zwracają wartość-1 L. Na urządzeniach bez możliwości wyszukiwania (takich jak terminale i drukarki) wartość zwracana jest niezdefiniowane.

Aby uzyskać więcej informacji na temat tych i innych kodów błędu, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Lseek —** funkcja przesuwa wskaźnik myszy plików skojarzonych z *fd* do nowej lokalizacji, która jest *przesunięcie* bajtów z *pochodzenia*. Następnej operacji na pliku występuje w nowej lokalizacji. *Pochodzenia* argument musi być jednym z następujących stałych, które są zdefiniowane w Stdio.h.

|*pochodzenie* wartość||
|-|-|
**SEEK_SET**|Początek pliku.
**SEEK_CUR**|Bieżąca pozycja wskaźnika pliku.
**SEEK_END**|Koniec pliku.

Możesz użyć **_lseek —** można przesunąć kursor w dowolnym miejscu w pliku lub znajduje się poza koniec pliku.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lseek —**|\<io.h>|
|**_lseeki64 —**|\<io.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

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

### <a name="input-crtlseekcinput"></a>Dane wejściowe: crt_lseek.c_input

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

[Niskiego poziomu operacji We/Wy](../../c-runtime-library/low-level-i-o.md)<br/>
[fseek, _fseeki64](fseek-fseeki64.md)<br/>
[_tell, _telli64](tell-telli64.md)<br/>
