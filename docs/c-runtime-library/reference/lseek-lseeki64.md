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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: d35b3db157d4f33e3a8490c6620a08000ff090f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341620"
---
# <a name="_lseek-_lseeki64"></a>_lseek, _lseeki64

Przenosi wskaźnik pliku w określoną lokalizację.

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

*Fd*<br/>
Deskryptora pliku odwołującego się do otwartego pliku.

*Przesunięcie*<br/>
Liczba bajtów od *początku .*

*Pochodzenia*<br/>
Pozycja początkowa.

## <a name="return-value"></a>Wartość zwracana

**_lseek** zwraca przesunięcie w bajtach nowej pozycji od początku pliku. **_lseeki64** zwraca przesunięcie w 64-bitowej całkowitej. Funkcja zwraca wartość -1L, aby wskazać błąd. Jeśli przeszedł nieprawidłowy parametr, taki jak zły deskryptor pliku lub wartość *pochodzenia* jest nieprawidłowa lub pozycja określona przez *przesunięcie* jest przed rozpoczęciem pliku, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [polu Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te funkcje ustawić **errno** do **EBADF** i zwracać -1L. Na urządzeniach niezdolnych do poszukiwania (takich jak terminale i drukarki) wartość zwracana jest niezdefiniowana.

Aby uzyskać więcej informacji na temat tych i innych kodów błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_lseek** przenosi wskaźnik pliku skojarzony z *fd* do nowej lokalizacji, która jest *odsunięty* bajtów od *początku .* Następna operacja w pliku występuje w nowej lokalizacji. Argument *pochodzenia* musi być jedną z następujących stałych, które są zdefiniowane w Stdio.h.

|wartość *początku*||
|-|-|
| **SEEK_SET** | Początek pliku. |
| **SEEK_CUR** | Bieżące położenie wskaźnika pliku. |
| **SEEK_END** | Koniec pliku. |

Za pomocą **_lseek** można zmienić położenie wskaźnika w dowolnym miejscu w pliku lub poza nim.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_lseek**|\<> io.h|
|**_lseeki64**|\<> io.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

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

### <a name="input-crt_lseekc_input"></a>Dane wejściowe: crt_lseek.c_input

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

[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[fseek, _fseeki64](fseek-fseeki64.md)<br/>
[_tell, _telli64](tell-telli64.md)<br/>
