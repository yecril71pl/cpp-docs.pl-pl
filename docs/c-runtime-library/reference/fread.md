---
title: fread
ms.date: 11/04/2016
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
ms.openlocfilehash: d3516dc67047064b9293b1bb289888596736ed47
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468838"
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

*Stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

**fread —** zwraca liczbę elementów pełną odczytane, które mogą być mniej niż *liczba* Jeśli wystąpi błąd lub napotkano koniec pliku przed osiągnięciem *liczba*. Użyj **feof** lub **ferror** funkcję, aby odróżnić błąd odczytu z warunkiem końca pliku. Jeśli *rozmiar* lub *liczba* ma wartość 0, **fread —** zwraca 0 i zawartości buforu nie uległy zmianie. Jeśli *strumienia* lub *buforu* jest pustym wskaźnikiem, **fread —** wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca wartość 0.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędu,.

## <a name="remarks"></a>Uwagi

**Fread —** funkcja odczytuje maksymalnie *liczba* elementy *rozmiar* bajtów z danych wejściowych *strumienia* i zapisuje je w *buforu* . Skojarzony wskaźnik pliku *strumienia* (jeśli istnieje) jest zwiększana o liczbę faktycznie odczytanych bajtów. Jeśli dany strumień jest otwarty w trybie tekstowym, pary wysuwu wiersza powrotu karetki są zastępowane przez znaki wysuwu pojedynczego wiersza. Zastąpienie nie ma wpływu na wskaźnik pliku lub wartość zwracaną. Pozycja wskaźnika pliku jest nieokreślony, jeśli wystąpi błąd. Nie można określić wartość elementu częściowo odczytu.

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
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
