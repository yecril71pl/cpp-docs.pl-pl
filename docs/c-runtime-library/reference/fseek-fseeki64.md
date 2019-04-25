---
title: fseek, _fseeki64
ms.date: 11/04/2016
apiname:
- _fseeki64
- fseek
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
- fseek
- _fseeki64
helpviewer_keywords:
- _fseeki64 function
- fseeki64 function
- fseek function
- file pointers [C++], moving
- file pointers [C++]
- seek file pointers
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
ms.openlocfilehash: e5f775eab370f8f4a3b6a5c1d7f0918ec7efa3ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287589"
---
# <a name="fseek-fseeki64"></a>fseek, _fseeki64

Przenosi wskaźnik pliku do określonej lokalizacji.

## <a name="syntax"></a>Składnia

```C
int fseek(
   FILE *stream,
   long offset,
   int origin
);
int _fseeki64(
   FILE *stream,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Wskaźnik do **pliku** struktury.

*offset*<br/>
Liczba bajtów z *pochodzenia*.

*Punkt początkowy*<br/>
Pozycja początkowa.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **fseek** i **_fseeki64 —** zwraca wartość 0. W przeciwnym razie zwraca wartość różną od zera. Na urządzeniach bez możliwości wyszukiwania wartość zwracana jest niezdefiniowane. Jeśli *strumienia* jest wskaźnikiem typu null, lub jeśli *pochodzenia* nie jest jednym z dozwolonych wartości opisanych poniżej, **fseek** i **_fseeki64 —** wywołania nieprawidłowy Procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają wartość -1.

## <a name="remarks"></a>Uwagi

**Fseek** i **_fseeki64 —** funkcje przenosi skojarzony wskaźnik pliku (jeśli istnieje) *strumienia* do nowej lokalizacji, która jest *przesunięcie* bajty z *pochodzenia*. Następnej operacji na strumieniu odbywa się w nowej lokalizacji. W strumieniu otwarte na potrzeby aktualizacji następnej operacji może być Odczyt lub zapis. Argument *pochodzenia* musi mieć jedną z następujących stałych, zdefiniowane w stdio —. GODZ.:

|Wartość źródła|Znaczenie|
|-|-|
| **SEEK_CUR** | Bieżąca pozycja wskaźnika pliku. |
| **SEEK_END** | Koniec pliku. |
| **SEEK_SET** | Początek pliku. |

Możesz użyć **fseek** i **_fseeki64 —** można przesunąć kursor w dowolnym miejscu w pliku. Wskaźnik również może być umieszczony poza końcem pliku. **fseek** i **_fseeki64 —** czyści wskaźnik końca pliku i neguje efekt dowolnej wcześniejszej [ungetc —](ungetc-ungetwc.md) wywołuje względem *strumienia*.

Po otwarciu pliku do wykonania operacji dołączania danych bieżącej pozycji w pliku zależy od ostatniej operacji We/Wy nie, gdzie może wystąpić następnego zapisu. Jeśli jeszcze wystąpił żadnej operacji We/Wy na pliku otwartego do wykonania operacji dołączania, położenie pliku jest początku pliku.

Dla strumieni otwarty w trybie tekstowym **fseek** i **_fseeki64 —** mają ograniczony użycia, ponieważ może spowodować tłumaczenia wysuwu wiersza powrotu karetki **fseek** i **_ fseeki64 —** dają nieoczekiwane wyniki. Tylko **fseek** i **_fseeki64 —** operacje gwarantowane strumieni otwarty w trybie tekstowym:

- Wyszukiwanie z przesunięciem 0 względem wartości pochodzenia.

- Wyszukiwanie od początku pliku wartość przesunięcia zwrócony z wywołania do [ftell —](ftell-ftelli64.md) przy użyciu **fseek** lub [_ftelli64 —](ftell-ftelli64.md) przy użyciu **_fseeki64 —**.

Również w trybie tekstowym, CTRL + Z jest interpretowany jako znak końca pliku na wejściu. W przypadku plików otwartych do odczytu/zapisu [fopen —](fopen-wfopen.md) i wszystkie powiązane procedury Sprawdź klawisze CTRL + Z końcem pliku i usuń go, jeśli jest to możliwe. Odbywa się, ponieważ używa kombinacji **fseek** i [ftell —](ftell-ftelli64.md) lub **_fseeki64 —** i [_ftelli64 —](ftell-ftelli64.md), aby przenieść w pliku, która kończy się CTRL + Z może spowodować, że **fseek** lub **_fseeki64 —** działać nieprawidłowo w pobliżu końca pliku.

Gdy CRT otwiera plik, który rozpocznie się za pomocą znacznika kolejności bajtów (BOM), wskaźnik pliku znajduje się po znaku BOM (oznacza to, na początku pliku rzeczywistej zawartości). Jeśli zajdzie potrzeba **fseek** na początku pliku, użyj [ftell —](ftell-ftelli64.md) uzyskać położenie początkowe i **fseek** do niego, a nie do pozycji 0.

Ta funkcja blokuje innych wątków podczas wykonywania i dlatego jest metodą o bezpiecznych wątkach. Dla wersji bez blokady, zobacz [_fseek_nolock —, _fseeki64_nolock —](fseek-nolock-fseeki64-nolock.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fseek**|\<stdio.h>|
|**_fseeki64**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fseek.c
// This program opens the file FSEEK.OUT and
// moves the pointer to the file's beginning.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[81];
   int  result;

   if ( fopen_s( &stream, "fseek.out", "w+" ) != 0 )
   {
      printf( "The file fseek.out was not opened\n" );
      return -1;
   }
   fprintf( stream, "The fseek begins here: "
                    "This is the file 'fseek.out'.\n" );
   result = fseek( stream, 23L, SEEK_SET);
   if( result )
      perror( "Fseek failed" );
   else
   {
      printf( "File pointer is set to middle of first line.\n" );
      fgets( line, 80, stream );
      printf( "%s", line );
    }
   fclose( stream );
}
```

```Output
File pointer is set to middle of first line.
This is the file 'fseek.out'.
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>
