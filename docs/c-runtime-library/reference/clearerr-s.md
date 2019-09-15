---
title: clearerr_s
ms.date: 11/04/2016
api_name:
- clearerr_s
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
- clearerr_s
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr_s function
ms.assetid: b74d014d-b7a8-494a-a330-e5ffd5614772
ms.openlocfilehash: 12e76ba5133d99ed2d45d7cf15bada2ad1c5c38b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939150"
---
# <a name="clearerr_s"></a>clearerr_s

Resetuje wskaźnik błędu dla strumienia. Jest to wersja [clearerr](clearerr.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t clearerr_s(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Wskaźnik do struktury **plików**

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli pomyślne; **EINVAL** , jeśli *strumień* ma **wartość null**.

## <a name="remarks"></a>Uwagi

Funkcja **clearerr_s** resetuje wskaźnik błędu i wskaźnik końca pliku dla *strumienia*. Wskaźniki błędów nie są automatycznie czyszczone; gdy zostanie ustawiony wskaźnik błędu dla określonego strumienia, operacje w tym strumieniu nadal zwracają wartość błędu do momentu wywołania **clearerr_s**, **clearerr**, [fseek](fseek-fseeki64.md), **fsetpos**lub [przewijania do tyłu](rewind.md) .

Jeśli *strumień* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca **EINVAL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**clearerr_s**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_clearerr_s.c
// This program creates an error
// on the standard input stream, then clears
// it so that future reads won't fail.

#include <stdio.h>

int main( void )
{
   int c;
   errno_t err;

   // Create an error by writing to standard input.
   putc( 'c', stdin );
   if( ferror( stdin ) )
   {
      perror( "Write error" );
      err = clearerr_s( stdin );
      if (err != 0)
      {
         abort();
      }
   }

   // See if read causes an error.
   printf( "Will input cause an error? " );
   c = getc( stdin );
   if( ferror( stdin ) )
   {
      perror( "Read error" );
      err = clearerr_s( stdin );
      if (err != 0)
      {
         abort();
      }
   }
}
```

### <a name="input"></a>Dane wejściowe

```Input
n
```

### <a name="output"></a>Dane wyjściowe

```Output
Write error: Bad file descriptor
Will input cause an error? n
```

## <a name="see-also"></a>Zobacz także

[Obsługa błędów](../../c-runtime-library/error-handling-crt.md)<br/>
[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
