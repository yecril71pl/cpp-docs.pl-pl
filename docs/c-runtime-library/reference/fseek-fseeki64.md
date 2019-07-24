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
ms.openlocfilehash: 4cfb4bcea4a110cf8a9c9db664c42d6603328cf0
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376081"
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
Wskaźnik do struktury **pliku** .

*offset*<br/>
Liczba bajtów od *początku*.

*źródł*<br/>
Pozycja początkowa.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, **fseek** i **_fseeki64** zwraca 0. W przeciwnym razie zwraca wartość różną od zera. Na urządzeniach, które nie mogą przeszukiwania, wartość zwracana jest niezdefiniowana. Jeśli *strumień* jest wskaźnikiem typu null lub jeśli *Źródło* nie jest jedną z dozwolonych wartości opisanych poniżej, **fseek** i **_fseeki64** Wywołaj procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EINVAL** i Return-1.

## <a name="remarks"></a>Uwagi

Funkcje **fseek** i **_fseeki64** przesuwają wskaźnik pliku (jeśli istnieje) skojarzony ze *strumieniem* do nowej lokalizacji, która jest przesunięta o bajty od *początku*. Kolejna operacja w strumieniu odbywa się w nowej lokalizacji. W przypadku otwartego strumienia na potrzeby aktualizacji kolejną operacją może być odczyt lub zapis. Pochodzenie  argumentu musi być jedną z następujących stałych zdefiniowanych w stdio. C

|wartość pochodzenia|Znaczenie|
|-|-|
| **SEEK_CUR** | Bieżąca pozycja wskaźnika pliku. |
| **SEEK_END** | Koniec pliku. |
| **SEEK_SET** | Początek pliku. |

Możesz użyć **fseek** i **_fseeki64** , aby zmienić położenie wskaźnika w dowolnym miejscu w pliku. Wskaźnik może być również umieszczony poza końcem pliku. **fseek** i **_fseeki64** czyści wskaźnik końca pliku i wyklucza efekt wszystkich wcześniejszych wywołań [ungetc —](ungetc-ungetwc.md) do *strumienia*.

Gdy plik jest otwierany do dołączania danych, bieżąca pozycja w pliku jest określana przez ostatnią operację we/wy, a nie przez miejsce wystąpienia następnego zapisu. Jeśli nie wykonano jeszcze operacji we/wy na pliku otwartym do dołączenia, pozycja w pliku jest początkiem pliku.

W przypadku strumieni otwartych w trybie tekstowym **fseek** i **_fseeki64** mają ograniczone użycie, ponieważ przetłumaczenia kanałów powrotu karetki mogą spowodować nieoczekiwane wyniki **fseek** i **_fseeki64** . Jedyną operacją **fseek** i **_fseeki64** zagwarantowaną do pracy nad strumieniami otwartymi w trybie tekstowym są:

- Wyszukiwanie z przesunięciem równym 0 względem którejkolwiek z wartości pochodzenia.

- Wyszukiwanie od początku pliku z wartością przesunięcia zwracaną z wywołania do [ftell](ftell-ftelli64.md) przy użyciu **fseek** lub [_ftelli64](ftell-ftelli64.md) podczas korzystania z **_fseeki64**.

Ponadto w trybie tekstowym klawisze CTRL + Z są interpretowane jako znak końca pliku na wejściu. W plikach otwartych do odczytu/zapisu, [fopen](fopen-wfopen.md) i wszystkie powiązane procedury sprawdź, czy Ctrl + Z na końcu pliku i usuń go, jeśli to możliwe. Dzieje się tak, ponieważ przy użyciu kombinacji **fseek** i [ftell](ftell-ftelli64.md) lub **_fseeki64** i [_ftelli64](ftell-ftelli64.md)do przenoszenia w pliku, który kończy się na Ctrl + z, może spowodować, że **fseek** lub **_fseeki64** zachowuje się nieprawidłowo blisko końca rozszerzeniem.

Gdy CRT otwiera plik zaczynający się od znaku kolejności bajtów (BOM), wskaźnik pliku jest umieszczony po BOM (czyli na początku rzeczywistej zawartości pliku). Jeśli musisz **fseek** na początku pliku, użyj [ftell](ftell-ftelli64.md) , aby pobrać początkową pozycję i **fseek** do niej, a nie pozycję 0.

Ta funkcja blokuje inne wątki podczas wykonywania i dlatego jest bezpieczna wątkowo. W przypadku wersji, która nie jest blokowana, zobacz [_fseek_nolock, _fseeki64_nolock](fseek-nolock-fseeki64-nolock.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fseek**|\<stdio.h>|
|**_fseeki64**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>
