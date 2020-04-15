---
title: clearerr
ms.date: 4/2/2020
api_name:
- clearerr
- _o_clearerr
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
- clearerr
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr function
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
ms.openlocfilehash: 174c94136cdc8b603416ff1dd239703489925bae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350028"
---
# <a name="clearerr"></a>clearerr

Resetuje wskaźnik błędu dla strumienia. Dostępna jest bezpieczniejsza wersja tej funkcji; patrz [clearerr_s](clearerr-s.md).

## <a name="syntax"></a>Składnia

```C
void clearerr(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

## <a name="remarks"></a>Uwagi

Funkcja **clearerr** resetuje wskaźnik błędu i wskaźnik końca pliku dla *strumienia*. Wskaźniki błędów nie są automatycznie czyszczone; po ustawieniu wskaźnika błędu dla określonego strumienia operacje na tym strumieniu będą nadal zwracać wartość błędu, dopóki nie zostanie wywołana **wartość clearerr**, [fseek](fseek-fseeki64.md), **fsetpos**lub [rewind.](rewind.md)

Jeśli *strumień* ma **wartość NULL**, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [yd.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **EINVAL** i zwraca. Aby uzyskać więcej informacji na temat kodów **błędów** i błędów, zobacz [errno Constants](../../c-runtime-library/errno-constants.md).

Dostępna jest bezpieczniejsza wersja tej funkcji; patrz [clearerr_s](clearerr-s.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**clearerr**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Obsługa błędów](../../c-runtime-library/error-handling-crt.md)<br/>
[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
