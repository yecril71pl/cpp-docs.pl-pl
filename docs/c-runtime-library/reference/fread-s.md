---
title: fread_s
ms.date: 4/2/2020
api_name:
- fread_s
- _o_fread_s
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
- fread_s
- stdio/fread_s
ms.assetid: ce735de0-f005-435d-a8f2-6f4b80ac775e
ms.openlocfilehash: 97f7ca80d4b458b952393a5b1f72bebe0bdb0d9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346122"
---
# <a name="fread_s"></a>fread_s

Odczytuje dane ze strumienia. Ta wersja [fread](fread.md) ma ulepszenia zabezpieczeń, zgodnie z opisem w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Buforu*<br/>
Lokalizacja przechowywania danych.

*Buffersize*<br/>
Rozmiar buforu docelowego w bajtach.

*elementSize*<br/>
Rozmiar elementu do odczytu w bajtach.

*Liczba*<br/>
Maksymalna liczba elementów do odczytania.

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

## <a name="return-value"></a>Wartość zwracana

**fread_s** zwraca liczbę (całych) elementów, które zostały odczytane do buforu, które mogą być mniejsze niż *liczba,* jeśli wystąpi błąd odczytu lub koniec pliku przed *osiągnięciem liczby.* Użyj funkcji **feof** lub **ferror,** aby odróżnić błąd od stanu końca pliku. Jeśli *rozmiar* lub *liczba* wynosi 0, **fread_s** zwraca 0, a zawartość buforu pozostaje niezmieniona. Jeśli *strumień* lub *bufor* jest wskaźnikiem zerowym, **fread_s** wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **EINVAL** i zwraca 0.

Aby uzyskać więcej informacji na temat kodów błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **fread_s** odczytuje do *zliczania* elementów *rozmiarów bajtów* z *strumienia* wejściowego i przechowuje je w *buforze*.  Wskaźnik pliku, który jest skojarzony ze *strumieniem* (jeśli istnieje) jest zwiększany o liczbę faktycznie odczytywanych bajtów. Jeśli dany strumień jest otwierany w trybie tekstowym, pary kanałów powrotu karetki są zastępowane pojedynczymi znakami podawania wiersza. Zastąpienie nie ma wpływu na wskaźnik pliku lub wartość zwracaną. Pozycja wskaźnika pliku jest nieokreślona w przypadku wystąpienia błędu. Nie można określić wartości elementu częściowo odczytanego.

Ta funkcja blokuje inne wątki. Jeśli potrzebujesz wersji niezablokującej, użyj **_fread_nolock**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fread_s**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
