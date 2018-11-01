---
title: fgetpos
ms.date: 11/04/2016
apiname:
- fgetpos
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
- fgetpos
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
ms.openlocfilehash: e213c9830ffe6edf04b12a80828f14cc48f77524
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658422"
---
# <a name="fgetpos"></a>fgetpos

Pobiera strumień, wskaźnik pozycji pliku.

## <a name="syntax"></a>Składnia

```C
int fgetpos(
   FILE *stream,
   fpos_t *pos
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Strumień docelowy.

*punktu sprzedaży*<br/>
Wskaźnik położenia magazynu.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **fgetpos** zwraca wartość 0. W przypadku awarii, funkcja zwraca wartość różną od zera i ustawia **errno** do jednej z następujących manifestu stałych (zdefiniowany w stdio —. Godz.): **EBADF**, co oznacza, że określonego strumienia nie jest prawidłowym plikiem wskaźnikiem lub nie jest dostępny, lub **EINVAL**, co oznacza, że *strumienia* wartość lub wartość *pos* jest nieprawidłowy, np. Jeśli jest wskaźnikiem typu null. Jeśli *strumienia* lub *pos* jest **NULL** wskaźnikiem, funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Uwagi

**Fgetpos** funkcja pobiera bieżącą wartość *strumienia* wskaźnik położenia pliku argumentu i magazyny w obiekt wskazywany przez *pos*. **Fsetpos** funkcja mógł później użyć informacji przechowywanych w *pos* zresetować *strumienia* wskaźnik argumentu do jego pozycja w czas **fgetpos** została wywołana. *Pos* wartość jest przechowywana w wewnętrznym formacie i jest przeznaczony do użytku tylko przez **fgetpos** i **fsetpos**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fgetpos**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fgetpos.c
// This program uses fgetpos and fsetpos to
// return to a location in a file.

#include <stdio.h>

int main( void )
{
   FILE   *stream;
   fpos_t pos;
   char   buffer[20];

   if( fopen_s( &stream, "crt_fgetpos.txt", "rb" ) ) {
      perror( "Trouble opening file" );
      return -1;
   }

   // Read some data and then save the position.
   fread( buffer, sizeof( char ), 8, stream );
   if( fgetpos( stream, &pos ) != 0 ) {
      perror( "fgetpos error" );
      return -1;
   }

   fread( buffer, sizeof( char ), 13, stream );
   printf( "after fgetpos: %.13s\n", buffer );

   // Restore to old position and read data
   if( fsetpos( stream, &pos ) != 0 ) {
      perror( "fsetpos error" );
      return -1;
   }

   fread( buffer, sizeof( char ), 13, stream );
   printf( "after fsetpos: %.13s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crtfgetpostxt"></a>Dane wejściowe: crt_fgetpos.txt

```Input
fgetpos gets a stream's file-position indicator.
```

### <a name="output-crtfgetpostxt"></a>Dane wyjściowe crt_fgetpos.txt

```Output
after fgetpos: gets a stream
after fsetpos: gets a stream
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fsetpos](fsetpos.md)<br/>
