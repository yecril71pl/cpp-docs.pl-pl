---
title: fread
ms.date: 4/2/2020
api_name:
- fread
- _o_fread
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
- fread
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
ms.openlocfilehash: 26ffd56072f1a5fddc3131a42cd47c145e437b60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346066"
---
# <a name="fread"></a>fread

Odczytuje dane ze strumienia.

## <a name="syntax"></a>Składnia

```C
size_t fread(
   void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Buforu*<br/>
Lokalizacja przechowywania danych.

*Rozmiar*<br/>
Rozmiar elementu w bajtach.

*Liczba*<br/>
Maksymalna liczba elementów do odczytania.

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

## <a name="return-value"></a>Wartość zwracana

**fread** zwraca liczbę pełnych elementów faktycznie przeczytanych, która może być mniejsza niż *liczba,* jeśli wystąpi błąd lub jeśli napotkany koniec pliku przed osiągnięciem *liczby*. Użyj funkcji **feof** lub **ferror,** aby odróżnić błąd odczytu od stanu końca pliku. Jeśli *rozmiar* lub *liczba* wynosi 0, **fread** zwraca 0, a zawartość buforu pozostaje niezmieniona. Jeśli *strumień* lub *bufor* jest wskaźnikiem null, **fread** wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **EINVAL** i zwraca 0.

Zobacz [ \_ \_doserrno, errno,\_sys \_errlist\_i sys nerr,](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) aby uzyskać więcej informacji na temat tych kodów błędów.

## <a name="remarks"></a>Uwagi

Funkcja **fread** odczytuje do *zliczania* elementów bajtów *rozmiaru* ze *strumienia* wejściowego i przechowuje je w *buforze*. Wskaźnik pliku skojarzony ze *strumieniem* (jeśli istnieje) jest zwiększany o liczbę faktycznie odczytanych bajtów. Jeśli dany strumień jest otwierany w [trybie tekstowym,](../../c-runtime-library/text-and-binary-mode-file-i-o.md)nowe linie w stylu windows są konwertowane na nowe linie w stylu Uniksa. Oznacza to, że pary wiersza powrotu karetki (CRLF) pary są zastępowane znakami pojedynczego wiersza kanału informacyjnego (LF). Zastąpienie nie ma wpływu na wskaźnik pliku lub wartość zwracaną. Pozycja wskaźnika pliku jest nieokreślona w przypadku wystąpienia błędu. Nie można określić wartości elementu częściowo odczytanego.

Jeśli jest używana w strumieniu trybu tekstowego, jeśli ilość żądanych danych (czyli liczba **FILE** \* \* *rozmiarów)* jest większa lub równa rozmiarowi wewnętrznego buforu PLIKÓW (domyślnie jest to 4096 bajtów, konfigurowalne przy użyciu [setvbuf),](../../c-runtime-library/reference/setvbuf.md)dane strumienia są kopiowane bezpośrednio do buforu dostarczonego przez użytkownika, a konwersja nowego tekstu odbywa się w tym buforze. *size* Ponieważ przekonwertowane dane mogą być krótsze niż dane *buffer*\[strumienia skopiowane do buforu, dane przeszłe*return_value* \* *rozmiar*] (gdzie *return_value* jest wartością zwracaną z **fread)** mogą zawierać nieprzekonwertowane dane z pliku. Z tego powodu zaleca się zero-terminate danych znaków w *buforze*\[*return_value* \* *rozmiar*], jeśli intencją buforu jest działać jako ciąg w stylu C. Szczegółowe informacje na temat efektów trybu tekstowego i trybu binarnego można znaleźć na [stronie fopen.](fopen-wfopen.md)

Ta funkcja blokuje inne wątki. Jeśli potrzebujesz wersji bez blokowania, użyj **_fread_nolock**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fread**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fread.c
// This program opens a file named FREAD.OUT and
// writes 25 characters to the file. It then tries to open
// FREAD.OUT and read in 25 characters. If the attempt succeeds,
// the program displays the number of actual items read.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char list[30];
   int  i, numread, numwritten;

   // Open file in text mode:
   if( fopen_s( &stream, "fread.out", "w+t" ) == 0 )
   {
      for ( i = 0; i < 25; i++ )
         list[i] = (char)('z' - i);
      // Write 25 characters to stream
      numwritten = fwrite( list, sizeof( char ), 25, stream );
      printf( "Wrote %d items\n", numwritten );
      fclose( stream );

   }
   else
      printf( "Problem opening the file\n" );

   if( fopen_s( &stream, "fread.out", "r+t" ) == 0 )
   {
      // Attempt to read in 25 characters
      numread = fread( list, sizeof( char ), 25, stream );
      printf( "Number of items read = %d\n", numread );
      printf( "Contents of buffer = %.25s\n", list );
      fclose( stream );
   }
   else
      printf( "File could not be opened\n" );
}
```

```Output
Wrote 25 items
Number of items read = 25
Contents of buffer = zyxwvutsrqponmlkjihgfedcb
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[We/Wy pliku tekstowego i binarnego](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[Fopen](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
