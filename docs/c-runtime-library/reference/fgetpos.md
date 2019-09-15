---
title: fgetpos
ms.date: 11/04/2016
api_name:
- fgetpos
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
- fgetpos
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
ms.openlocfilehash: 27d25b29f656d1df889e5f83857ca437f609a07a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940844"
---
# <a name="fgetpos"></a>fgetpos

Pobiera wskaźnik położenia pliku strumienia.

## <a name="syntax"></a>Składnia

```C
int fgetpos(
   FILE *stream,
   fpos_t *pos
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Strumień docelowy.

*Terminal*<br/>
Miejsce — magazyn wskaźnika.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia funkcja **fgetpos** zwraca wartość 0. W przypadku niepowodzenia zwraca wartość różną od zera i ustawia **errno** na jedną z następujących stałych manifestu (zdefiniowanej w stdio. H): **EBADF**, co oznacza, że określony strumień nie jest prawidłowym wskaźnikiem pliku lub jest niedostępny lub **EINVAL**, co oznacza, że wartość *strumienia* lub wartość *punktu sprzedaży* jest nieprawidłowa, na przykład jeśli jest wskaźnikiem typu null. Jeśli *strumień* lub *pos* jest wskaźnikiem typu **null** , funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Uwagi

Funkcja **fgetpos** pobiera bieżącą wartość wskaźnika położenia plików argumentu *strumienia* i zapisuje ją w obiekcie wskazywanym przez *punkt sprzedaży*. Funkcja **fsetpos** może później używać informacji przechowywanych w *punkcie sprzedaży* do resetowania wskaźnika argumentu *strumienia* do jego pozycji w czasie, gdy **fgetpos** został wywołany. Wartość *pos* jest przechowywana w formacie wewnętrznym i jest przeznaczona do użycia tylko przez **fgetpos** i **fsetpos**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fgetpos**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="input-crt_fgetpostxt"></a>Dane wejściowe: crt_fgetpos. txt

```Input
fgetpos gets a stream's file-position indicator.
```

### <a name="output-crt_fgetpostxt"></a>Output crt_fgetpos. txt

```Output
after fgetpos: gets a stream
after fsetpos: gets a stream
```

## <a name="see-also"></a>Zobacz także

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fsetpos](fsetpos.md)<br/>
