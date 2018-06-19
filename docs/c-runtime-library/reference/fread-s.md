---
title: fread_s | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fread_s
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
- fread_s
- stdio/fread_s
dev_langs:
- C++
ms.assetid: ce735de0-f005-435d-a8f2-6f4b80ac775e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: febfab21889afab773dd9a8405b1e07dc7798f5c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401896"
---
# <a name="freads"></a>fread_s

Odczytuje dane ze strumienia. Ta wersja [fread —](fread.md) zawiera ulepszenia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
size_t fread_s(
   void *buffer,
   size_t bufferSize,
   size_t elementSize,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Lokalizacja magazynu danych.

*BufferSize*<br/>
Rozmiar buforu docelowego w bajtach.

*elementSize*<br/>
Rozmiar elementu do odczytu w bajtach.

*Liczba*<br/>
Maksymalna liczba elementów do odczytu.

*Strumień*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

**fread_s** zwraca numer (pełne), elementy, które zostały odczytane w buforze, który może być mniejsza niż *liczba* Jeśli błąd odczytu lub na końcu pliku napotkano przed *liczba* zostanie osiągnięty. Użyj **feof —** lub **ferror —** funkcja odróżnienia błąd warunku końcowego pliku. Jeśli *rozmiar* lub *liczba* ma wartość 0, **fread_s** zwraca 0 i zawartości buforu nie uległy zmianie. Jeśli *strumienia* lub *buforu* wskaźnika o wartości null, jest **fread_s** wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może kontynuować, ta funkcja ustawia **errno** do **einval —** i zwraca wartość 0.

Aby uzyskać więcej informacji o kodach błędów, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**Fread_s** funkcja odczytuje do *liczba* elementów *elementSize* bajtów z danych wejściowych *strumienia* i zapisuje je w *buforu*.  Wskaźnika pliku, z którym skojarzony jest *strumienia* (jeśli istnieje) jest zwiększana o liczba bajtów odczytanych w rzeczywistości. Jeśli dany strumień jest otwarty w trybie tekstowym, pary wysuwu wiersza powrotu karetki są zastępowane wysuwu wiersza pojedynczy znaki. Zastąpienie nie ma wpływu na wskaźnika pliku lub wartości zwracanej. Położenie pliku wskaźnika jest nieokreślony, jeśli wystąpi błąd. Nie można określić wartość elementu częściowo odczytu.

Ta funkcja blokuje inne wątki. Jeśli potrzebujesz wersji — blokowanie użycia **_fread_nolock —**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fread_s**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```cpp
// crt_fread_s.c
// Command line: cl /EHsc /nologo /W4 crt_fread_s.c
//
// This program opens a file that's named FREAD.OUT and
// writes characters to the file. It then tries to open
// FREAD.OUT and read in characters by using fread_s. If the attempt succeeds,
// the program displays the number of actual items read.

#include <stdio.h>

#define BUFFERSIZE 30
#define DATASIZE 22
#define ELEMENTCOUNT 2
#define ELEMENTSIZE (DATASIZE/ELEMENTCOUNT)
#define FILENAME "FREAD.OUT"

int main( void )
{
   FILE *stream;
   char list[30];
   int  i, numread, numwritten;

   for ( i = 0; i < DATASIZE; i++ )
      list[i] = (char)('z' - i);
   list[DATASIZE] = '\0'; // terminal null so we can print it

   // Open file in text mode:
   if( fopen_s( &stream, FILENAME, "w+t" ) == 0 )
   {
      // Write DATASIZE characters to stream
      printf( "Contents of buffer before write/read:\n\t%s\n\n", list );
      numwritten = fwrite( list, sizeof( char ), DATASIZE, stream );
      printf( "Wrote %d items\n\n", numwritten );
      fclose( stream );
   } else {
      printf( "Problem opening the file\n" );
      return -1;
   }

   if( fopen_s( &stream, FILENAME, "r+t" ) == 0 )   {
      // Attempt to read in characters in 2 blocks of 11
      numread = fread_s( list, BUFFERSIZE, ELEMENTSIZE, ELEMENTCOUNT, stream );
      printf( "Number of %d-byte elements read = %d\n\n", ELEMENTSIZE, numread );
      printf( "Contents of buffer after write/read:\n\t%s\n", list );
      fclose( stream );
   } else {
      printf( "File could not be opened\n" );
      return -1;
   }
}
```

```Output
Contents of buffer before write/read:
        zyxwvutsrqponmlkjihgfe

Wrote 22 items

Number of 11-byte elements read = 2

Contents of buffer after write/read:
        zyxwvutsrqponmlkjihgfe
```

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
