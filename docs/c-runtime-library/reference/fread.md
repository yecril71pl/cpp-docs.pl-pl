---
title: fread
ms.date: 11/28/2018
api_name:
- fread
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
- fread
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
ms.openlocfilehash: 7cf4542a656798f7e2431b2f939df1b5d6396144
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956818"
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

*buffer*<br/>
Lokalizacja magazynu dla danych.

*zmienia*<br/>
Rozmiar elementu w bajtach.

*liczbą*<br/>
Maksymalna liczba elementów, które mają zostać odczytane.

*stream*<br/>
Wskaźnik do struktury **pliku** .

## <a name="return-value"></a>Wartość zwracana

**fread** zwraca liczbę pełnych elementów, które są faktycznie odczytywane, co może być mniejsze niż *Count* , jeśli wystąpi błąd lub jeśli koniec pliku zostanie napotkany przed osiągnięciem *liczby*. Użyj funkcji **feof** lub odwołującej, aby odróżnić błąd odczytu od stanu końca pliku. Jeśli *rozmiar* lub *Liczba* to 0, **fread** zwraca 0, a zawartość buforu nie jest zmieniana. Jeśli *strumień* lub *bufor* jest wskaźnikiem o wartości null, **fread** wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca wartość 0.

Zobacz [ \_\_doserrno, errno, \_sys errlist i sys\_NERR, aby uzyskać więcej informacji na temat tych kodów błędów. \_](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>Uwagi

Funkcja **fread** odczytuje do *liczby* elementów *w bajtach* *wejściowych i* zapisuje je w *buforze*. Wskaźnik pliku skojarzony ze *strumieniem* (jeśli istnieje) jest zwiększany o liczbę bajtów rzeczywiście odczytanych. Jeśli dany strumień jest otwarty w [trybie tekstowym](../../c-runtime-library/text-and-binary-mode-file-i-o.md), nowy wiersz w stylu systemu Windows jest konwertowany na znaki nowego wiersza systemu UNIX. Oznacza to, że podwójne znaki wysuwu wiersza (CRLF) są zastępowane znakami pojedynczego znaku wysuwu wiersza (LF). Zastąpienie nie ma wpływu na wskaźnik pliku lub wartość zwracaną. Pozycja wskaźnika pliku jest nieokreślona w przypadku wystąpienia błędu. Nie można określić wartości częściowo odczytanego elementu.

W przypadku użycia w strumieniu trybu tekstu, jeśli ilość żądanych danych (czyli *licznik* *rozmiaru* \* ) jest większa lub równa rozmiarowi wewnętrznego buforu **plików** \* (domyślnie jest to 4096 bajtów, można skonfigurować za pomocą [ setvbuf —](../../c-runtime-library/reference/setvbuf.md)) dane przesyłane strumieniowo są kopiowane bezpośrednio do buforu dostarczonego przez użytkownika, a konwersja nowego wiersza jest wykonywana w tym buforze. Ponieważ przekonwertowane dane mogą być krótsze niż dane strumienia skopiowane do bufora, *rozmiar* *RETURN_VALUE* \* *bufora*\[danych poprzedzających] (gdzie *RETURN_VALUE* jest wartością zwracaną z **fread**) może zawierają nieskonwertowane dane z pliku. Z tego powodu zalecamy, aby dane o znakach kończących wartość null w *buforze*\[*RETURN_VALUE* \* *rozmiar*], jeśli celem buforu jest działanie jako ciąg w stylu języka C. Zobacz [fopen](fopen-wfopen.md) , aby uzyskać szczegółowe informacje na temat skutków trybu tekstowego i trybu binarnego.

Ta funkcja blokuje inne wątki. Jeśli potrzebujesz wersji, która nie jest blokowana, użyj **_fread_nolock**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fread**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[We/wy plików tekstowych i binarnych](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[fopen](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
