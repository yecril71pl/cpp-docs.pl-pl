---
title: _putw
ms.date: 11/04/2016
apiname:
- _putw
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
- _putw
- putw
helpviewer_keywords:
- integers, writing to streams
- putw function
- streams, writing integers to
- _putw function
ms.assetid: 83d63644-249d-4a39-87e5-3b7aa313968d
ms.openlocfilehash: 3fd18c2a8869d6b09703547f50ee6e096bd72395
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358056"
---
# <a name="putw"></a>_putw

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
Binarny liczba całkowita ma być danych wyjściowych.

*stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zapisywane. Zwracana wartość wynosząca **EOF** może wskazywać na błąd. Ponieważ **EOF** jest również wartość całkowitą uzasadnione, użyj **ferror** Aby sprawdzić, wystąpił błąd. Jeśli *strumienia* jest pustym wskaźnikiem, wywoływany nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca **EOF**.

Aby uzyskać informacje na temat tych i innych kodów błędu, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Putw —** funkcja zapisuje wartość binarna typu **int** do bieżącego położenia obiektu *strumienia.* **_putw —** wyrównania elementów w strumieniu nie wpływa ani nie założono żadnych specjalnych wyrównania. **_putw —** jest przeznaczone głównie dla zachowania zgodności z poprzedniej biblioteki. Za pomocą mogą wystąpić problemy z przenośnością **_putw —** ponieważ rozmiar **int** i kolejność bajtów w ramach **int** różne w różnych systemach.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_putw**|\<stdio.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[_getw](getw.md)<br/>
