---
title: _tell, _telli64
ms.date: 11/04/2016
api_name:
- _telli64
- _tell
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
- tell
- telli64
- _telli64
- _tell
helpviewer_keywords:
- tell function
- file pointers [C++], getting
- _tell function
- file pointers [C++]
- telli64 function
- _telli64 function
ms.assetid: 1500e8f9-8fec-4253-9eec-ec66125dfc9b
ms.openlocfilehash: 54f672a1b230103d6f9ae1c45d2c9e487764939e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946261"
---
# <a name="_tell-_telli64"></a>_tell, _telli64

Pobierz pozycję wskaźnika pliku.

## <a name="syntax"></a>Składnia

```C
long _tell(
   int handle
);
__int64 _telli64(
   int handle
);
```

### <a name="parameters"></a>Parametry

*uchwyty*<br/>
Deskryptor pliku odwołujący się do otwartego pliku.

## <a name="return-value"></a>Wartość zwracana

Bieżąca pozycja wskaźnika pliku. Na urządzeniach, które nie mogą przeszukiwania, wartość zwracana jest niezdefiniowana.

Wartość zwracana parametru-1L wskazuje na błąd. Jeśli *dojście* jest nieprawidłowym deskryptorem pliku, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EBADF** i Return-1L.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) , aby uzyskać więcej informacji na ten temat, a inne kody powrotne.

## <a name="remarks"></a>Uwagi

Funkcja **_tell** pobiera bieżącą pozycję wskaźnika pliku (jeśli istnieje) skojarzoną z argumentem *uchwytu* . Pozycja jest wyrażona jako liczba bajtów od początku pliku. Dla funkcji **_telli64** ta wartość jest wyrażona jako 64-bitowa liczba całkowita.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_tell**, **_telli64**|\<io.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_tell.c
// This program uses _tell to tell the
// file pointer position after a file read.
//

#include <io.h>
#include <stdio.h>
#include <fcntl.h>
#include <share.h>
#include <string.h>

int main( void )
{
   int  fh;
   char buffer[500];

   if ( _sopen_s( &fh, "crt_tell.txt", _O_RDONLY, _SH_DENYNO, 0) )
   {
      char buff[50];
      _strerror_s( buff, sizeof(buff), NULL );
      printf( buff );
      exit( -1 );
   }

   if( _read( fh, buffer, 500 ) > 0 )
      printf( "Current file position is: %d\n", _tell( fh ) );
   _close( fh );
}
```

### <a name="input-crt_telltxt"></a>Dane wejściowe: crt_tell. txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Dane wyjściowe

```Output
Current file position is: 20
```

## <a name="see-also"></a>Zobacz także

[We/wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
