---
title: fgetpos
ms.date: 4/2/2020
api_name:
- fgetpos
- _o_fgetpos
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
- fgetpos
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
ms.openlocfilehash: 0c16150a6240068e1453ec90b396c87ab9ece5a4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346924"
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

*Strumienia*<br/>
Strumień docelowy.

*Poz*<br/>
Przechowywanie wskaźnika położenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, **fgetpos** zwraca 0. W przypadku niepowodzenia zwraca wartość niezerową i ustawia **errno** na jedną z następujących stałych manifestu (zdefiniowaną w STDIO. H): **EBADF**, co oznacza, że określony strumień nie jest prawidłowym wskaźnikiem pliku lub nie jest dostępny, lub **EINVAL**, co oznacza, że wartość *strumienia* lub wartość *poz* jest nieprawidłowa, na przykład jeśli jest wskaźnikiem null. Jeśli *stream* lub *pos* jest wskaźnikiem **NULL,** funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Uwagi

Funkcja **fgetpos** pobiera bieżącą wartość wskaźnika położenia pliku *argumentu strumienia* i przechowuje go w obiekcie wskazywał *przez poz*. Funkcja **fsetpos** może później użyć informacji przechowywanych w *pos,* aby zresetować wskaźnik *argumentu strumienia* do jego pozycji w czasie **wywoływania fgetpos.** Wartość *pos* jest przechowywana w formacie wewnętrznym i jest przeznaczona do użytku tylko przez **fgetpos** i **fsetpos**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fgetpos**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="input-crt_fgetpostxt"></a>Dane wejściowe: crt_fgetpos.txt

```Input
fgetpos gets a stream's file-position indicator.
```

### <a name="output-crt_fgetpostxt"></a>Dane wyjściowe crt_fgetpos.txt

```Output
after fgetpos: gets a stream
after fsetpos: gets a stream
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fsetpos](fsetpos.md)<br/>
