---
title: fread
ms.date: 11/28/2018
apiname:
- fread
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
- fread
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
ms.openlocfilehash: 7248eb08409b50d855dbb70c7638a856302b345b
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849974"
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
Lokalizacja magazynowa danych.

*Rozmiar*<br/>
Rozmiar elementu w bajtach.

*Liczba*<br/>
Maksymalna liczba elementów, które mają być odczytywane.

*stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

**fread —** zwraca liczbę elementów pełną odczytane, które mogą być mniej niż *liczba* Jeśli wystąpi błąd lub napotkano koniec pliku przed osiągnięciem *liczba*. Użyj **feof** lub **ferror** funkcję, aby odróżnić błąd odczytu z warunkiem końca pliku. Jeśli *rozmiar* lub *liczba* ma wartość 0, **fread —** zwraca 0 i zawartości buforu nie uległy zmianie. Jeśli *strumienia* lub *buforu* jest pustym wskaźnikiem, **fread —** wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca wartość 0.

Zobacz [ \_doserrno —, errno, \_sys\_errlist, i \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) więcej informacji na temat tych kodów błędu.

## <a name="remarks"></a>Uwagi

**Fread —** funkcja odczytuje maksymalnie *liczba* elementy *rozmiar* bajtów z danych wejściowych *strumienia* i zapisuje je w *buforu* . Skojarzony wskaźnik pliku *strumienia* (jeśli istnieje) jest zwiększana o liczbę faktycznie odczytanych bajtów. Jeśli dany strumień jest otwarty w [tryb tekstu](../../c-runtime-library/text-and-binary-mode-file-i-o.md), newlines Windows style są konwertowane na oddzielane stylu systemu Unix. Oznacza to powrót karetki return wysuwu wiersza (CRLF) pary zastępuje znaki pojedynczego wysuwu wiersza (LF). Zastąpienie nie ma wpływu na wskaźnik pliku lub wartość zwracaną. Pozycja wskaźnika pliku jest nieokreślony, jeśli wystąpi błąd. Nie można określić wartość elementu częściowo odczytu.

Gdy jest używana w trybie strumienia tekstu, jeśli żądana ilość danych (oznacza to, *rozmiar* \* *liczba*) jest większa niż lub równa wewnętrzny **pliku** \*rozmiar buforu (wartość domyślna wynosi 4096 bajtów, które można konfigurować za pomocą [setvbuf —](../../c-runtime-library/reference/setvbuf.md)), przesyłanie strumieniowe danych jest kopiowana bezpośrednio do bufora podanego przez użytkownika i nowego wiersza konwersji odbywa się w tym buforu. Ponieważ przekonwertowanego danych może być krótszy niż przesyłanie strumieniowe danych skopiowanych do bufora danych w ciągu ostatnich *buforu*\[*wartość_zwracana* \* *rozmiar*] () gdzie *wartość_zwracana* jest wartość zwrotną z elementu **fread —**) mogą zawierać nieprzekonwertowane dane z pliku. Z tego powodu zaleca się, zostanie przerwane wartością null — dane znakowe na *buforu*\[*wartość_zwracana* \* *rozmiar*] Jeśli celem buforu do działania jako ciąg stylu C. Zobacz [fopen —](fopen-wfopen.md) szczegółowe informacje dotyczące efektów w trybie tekstowym i binarnym.

Ta funkcja blokuje inne wątki. Jeśli potrzebujesz wersji bez blokady, użyj **_fread_nolock —**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fread**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[We/Wy tekstu i pliku binarnego](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[fopen —](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
