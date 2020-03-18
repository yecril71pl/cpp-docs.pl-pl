---
title: _putw
ms.date: 11/04/2016
api_name:
- _putw
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
- _putw
helpviewer_keywords:
- integers, writing to streams
- putw function
- streams, writing integers to
- _putw function
ms.assetid: 83d63644-249d-4a39-87e5-3b7aa313968d
ms.openlocfilehash: be2ee5c1b3706b1f2a0847415ab4a82a6a4bbe4f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443725"
---
# <a name="_putw"></a>_putw

Zapisuje liczbę całkowitą do strumienia.

## <a name="syntax"></a>Składnia

```C
int _putw(
   int binint,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*binint*<br/>
Binarna liczba całkowita, która ma być wyjściowa.

*produkcyjne*<br/>
Wskaźnik do struktury **pliku** .

## <a name="return-value"></a>Wartość zwracana

Zwraca zapisaną wartość. Wartość zwracana przez **eof** może wskazywać na błąd. Ponieważ **eof** jest również wiarygodną wartością całkowitą **, użyj obiektu** nadający się do sprawdzenia błędu. Jeśli *strumień* jest pustym wskaźnikiem, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca **znacznik EOF**.

Aby uzyskać informacje o tych i innych kodach błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_putw** zapisuje wartość binarną typu **int** do bieżącej pozycji *strumienia.* **_putw** nie wpływa na wyrównanie elementów w strumieniu ani nie przyjmuje żadnych specjalnych wyrównania. **_putw** jest przede wszystkim zgodne z poprzednimi bibliotekami. Mogą wystąpić problemy z przenośnością **_putw** , ponieważ rozmiar **int** i porządkowanie bajtów w ramach **int** różnią się w różnych systemach.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_putw**|\<stdio. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_putw.c
/* This program uses _putw to write a
* word to a stream, then performs an error check.
*/

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   unsigned u;
   if( fopen_s( &stream, "data.out", "wb" ) )
      exit( 1 );
   for( u = 0; u < 10; u++ )
   {
      _putw( u + 0x2132, stream );   /* Write word to stream. */
      if( ferror( stream ) )         /* Make error check. */
      {
         printf( "_putw failed" );
         clearerr_s( stream );
         exit( 1 );
      }
   }
   printf( "Wrote ten words\n" );
   fclose( stream );
}
```

### <a name="output"></a>Dane wyjściowe

```Output
Wrote ten words
```

## <a name="see-also"></a>Zobacz też

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_getw](getw.md)<br/>
