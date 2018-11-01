---
title: clearerr_s
ms.date: 11/04/2016
apiname:
- clearerr_s
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
- clearerr_s
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr_s function
ms.assetid: b74d014d-b7a8-494a-a330-e5ffd5614772
ms.openlocfilehash: 140d984c470bd505f347aa43065b033339ed38a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665026"
---
# <a name="clearerrs"></a>clearerr_s

Resetuje wskaźnik błędu dla strumienia. To jest wersja [clearerr —](clearerr.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t clearerr_s(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Wskaźnik do **pliku** struktury

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie; **EINVAL** Jeśli *strumienia* jest **NULL**.

## <a name="remarks"></a>Uwagi

**Clearerr_s —** funkcja resetuje wskaźnik błędów i wskaźnik końca pliku *strumienia*. Wskaźniki błędów nie zostaną automatycznie wyczyszczone; Po ustawieniu wskaźnika błędu dla określonego strumienia operacje na strumieniu w dalszym ciągu zwraca wartości błędu do czasu **clearerr_s —**, **clearerr —**, [fseek](fseek-fseeki64.md), **fsetpos**, lub [rewind](rewind.md) jest wywoływana.

Jeśli *strumienia* jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca **EINVAL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**clearerr_s**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

```Output

n

```

```Output

      nWrite error: Bad file descriptor
Will input cause an error? n
```

## <a name="see-also"></a>Zobacz także

[Obsługa błędów](../../c-runtime-library/error-handling-crt.md)<br/>
[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
