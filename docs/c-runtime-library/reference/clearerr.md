---
title: clearerr
ms.date: 11/04/2016
api_name:
- clearerr
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
- clearerr
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr function
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
ms.openlocfilehash: 9fd2f7e7dfcf272e806a887b356418b7555913f5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942951"
---
# <a name="clearerr"></a>clearerr

Resetuje wskaźnik błędu dla strumienia. Dostępna jest bezpieczniejsza wersja tej funkcji; Zobacz [clearerr_s](clearerr-s.md).

## <a name="syntax"></a>Składnia

```C
void clearerr(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Wskaźnik do struktury **pliku** .

## <a name="remarks"></a>Uwagi

Funkcja **clearerr** resetuje wskaźnik błędu i wskaźnik końca pliku dla *strumienia*. Wskaźniki błędów nie są automatycznie czyszczone; gdy zostanie ustawiony wskaźnik błędu dla określonego strumienia, operacje w tym strumieniu nadal zwracają wartość błędu do momentu wywołania **clearerr**, [fseek](fseek-fseeki64.md), **fsetpos**lub [przewijania do tyłu](rewind.md) .

Jeśli *strumień* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca. Aby uzyskać więcej informacji o **errno** i kodach błędów, zobacz [errno stałe](../../c-runtime-library/errno-constants.md).

Dostępna jest bezpieczniejsza wersja tej funkcji; Zobacz [clearerr_s](clearerr-s.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**clearerr**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_clearerr.c
// This program creates an error
// on the standard input stream, then clears
// it so that future reads won't fail.

#include <stdio.h>

int main( void )
{
   int c;
   // Create an error by writing to standard input.
   putc( 'c', stdin );
   if( ferror( stdin ) )
   {
      perror( "Write error" );
      clearerr( stdin );
   }

   // See if read causes an error.
   printf( "Will input cause an error? " );
   c = getc( stdin );
   if( ferror( stdin ) )
   {
      perror( "Read error" );
      clearerr( stdin );
   }
   else
      printf( "No read error\n" );
}
```

### <a name="input"></a>Dane wejściowe

```Input
n
```

### <a name="output"></a>Dane wyjściowe

```Output
Write error: No error
Will input cause an error? n
No read error
```

## <a name="see-also"></a>Zobacz także

[Obsługa błędów](../../c-runtime-library/error-handling-crt.md)<br/>
[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
