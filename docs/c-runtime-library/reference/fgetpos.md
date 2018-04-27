---
title: fgetpos — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 10734497ac8db77e09f6e3077aa5eb123a179f88
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="fgetpos"></a>fgetpos

Pobiera strumienia wskaźnika położenia pliku.

## <a name="syntax"></a>Składnia

```C
int fgetpos(
   FILE *stream,
   fpos_t *pos
);
```

### <a name="parameters"></a>Parametry

*Strumień*<br/>
Strumień docelowy.

*POS*<br/>
Wskaźnik położenia magazynu.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **fgetpos —** zwraca wartość 0. W przypadku awarii, zwraca wartość różną od zera i ustawia **errno** do jednej z następujących manifestu — stałe (zdefiniowany w stdio —. H): **ebadf —**, co oznacza, że określonego obiektu stream nie jest prawidłowym plikiem wskaźnikiem lub nie jest dostępny, lub **einval —**, co oznacza, że *strumienia* wartość lub wartość *pos* jest nieprawidłowy, np. Jeśli to jest wskaźnika o wartości null. Jeśli *strumienia* lub *pos* jest **NULL** wskaźnika, funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Uwagi

**Fgetpos —** funkcja pobiera bieżącą wartość *strumienia* wskaźnika położenia pliku argumentu i magazyny go w obiekcie wskazywana przez *pos*. **Fsetpos —** funkcja mógł później użyć informacji przechowywanych w *pos* zresetować *strumienia* argumentu wskaźnik do położenia w czasie **fgetpos —** została wywołana. *Pos* wartości są przechowywane w wewnętrznym formacie i jest przeznaczona do użycia tylko poprzez **fgetpos —** i **fsetpos —**.

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

### <a name="output-crtfgetpostxt"></a>Crt_fgetpos.txt danych wyjściowych

```Output
after fgetpos: gets a stream
after fsetpos: gets a stream
```

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fsetpos](fsetpos.md)<br/>
