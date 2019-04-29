---
title: clearerr
ms.date: 11/04/2016
apiname:
- clearerr
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
- clearerr
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr function
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
ms.openlocfilehash: c282a577bb7496f899f18abeac857c08388d12f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340564"
---
# <a name="clearerr"></a>clearerr

Resetuje wskaźnik błędu dla strumienia. Bardziej bezpieczna wersja ta funkcja jest dostępna; zobacz [clearerr_s —](clearerr-s.md).

## <a name="syntax"></a>Składnia

```C
void clearerr(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="remarks"></a>Uwagi

**Clearerr —** funkcja resetuje wskaźnik błędów i wskaźnik końca pliku *strumienia*. Wskaźniki błędów nie zostaną automatycznie wyczyszczone; Po ustawieniu wskaźnika błędu dla określonego strumienia operacje na strumieniu w dalszym ciągu zwraca wartości błędu do czasu **clearerr —**, [fseek](fseek-fseeki64.md), **fsetpos**, lub [rewind](rewind.md) jest wywoływana.

Jeśli *strumienia* jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca. Aby uzyskać więcej informacji na temat **errno** i kodach błędów, zobacz [errno — stałe](../../c-runtime-library/errno-constants.md).

Bardziej bezpieczna wersja ta funkcja jest dostępna; zobacz [clearerr_s —](clearerr-s.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**clearerr**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
