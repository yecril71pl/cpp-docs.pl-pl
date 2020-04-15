---
title: fseek, _fseeki64
ms.date: 4/2/2020
api_name:
- _fseeki64
- fseek
- _o__fseeki64
- _o_fseek
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
ms.openlocfilehash: e8f6021a0b770f6b435653c190d5968f9ac50a57
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345766"
---
# <a name="fseek-_fseeki64"></a>fseek, _fseeki64

Przenosi wskaźnik pliku w określoną lokalizację.

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

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

*Przesunięcie*<br/>
Liczba bajtów od *początku .*

*Pochodzenia*<br/>
Pozycja początkowa.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, **fseek** i **_fseeki64** zwraca 0. W przeciwnym razie zwraca wartość niezerową. Na urządzeniach, których nie można szukać, zwracana wartość jest niezdefiniowana. Jeśli *strumień* jest wskaźnikiem zerowym lub jeśli *pochodzenie* nie jest jedną z dozwolonych wartości opisanych poniżej, **fseek** i **_fseeki64** wywołać nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, te funkcje ustawić **errno** na **EINVAL** i zwracać -1.

## <a name="remarks"></a>Uwagi

Funkcje **fseek** i **_fseeki64** przenosi wskaźnik pliku (jeśli istnieje) skojarzony ze *strumieniem* do nowej lokalizacji, która jest *odsunięty* bajtami od *początku .* Następna operacja na strumieniu odbywa się w nowej lokalizacji. W strumieniu otwartym do aktualizacji następna operacja może być odczytem lub zapisem. Początek *argumentu* musi być jedną z następujących stałych, zdefiniowanych w STDIO. H:

|wartość początku|Znaczenie|
|-|-|
| **SEEK_CUR** | Bieżąca pozycja wskaźnika pliku. |
| **SEEK_END** | Koniec pliku. |
| **SEEK_SET** | Początek pliku. |

Można użyć **fseek** i **_fseeki64,** aby zmienić położenie wskaźnika w dowolnym miejscu w pliku. Wskaźnik można również umieścić poza końcem pliku. **fseek** i **_fseeki64** czyści wskaźnik końca pliku i neguje efekt wszelkich wcześniejszych [wywołań ungetc](ungetc-ungetwc.md) przeciwko *strumieniu*.

Po otwarciu pliku do dołączania danych bieżąca pozycja pliku jest określana przez ostatnią operację we/wy, a nie przez to, gdzie nastąpi następny zapis. Jeśli w pliku otwartym do dołączenia nie wystąpiła żadna operacja we/wy, pozycja pliku jest początkiem pliku.

W przypadku strumieni otwieranych w trybie tekstowym **fseek** i **_fseeki64** mają ograniczone zastosowanie, ponieważ tłumaczenia wiersza powrotu karetki mogą **powodować, że fseek** i **_fseeki64** dają nieoczekiwane wyniki. Jedynymi **operacjami fseek** i **_fseeki64** gwarantowanymi do pracy na strumieniach otwieranych w trybie tekstowym są:

- Poszukiwanie z przesunięciem równym 0 względem dowolnej wartości pochodzenia.

- Szukam od początku pliku z wartością przesunięcia zwróconą z wywołania [ftell](ftell-ftelli64.md) podczas korzystania **z fseek** lub [_ftelli64](ftell-ftelli64.md) podczas korzystania **z _fseeki64**.

Również w trybie tekstowym ctrl+Z jest interpretowany jako znak końca pliku na danych wejściowych. W plikach otwartych do odczytu / zapisu, [fopen](fopen-wfopen.md) i wszystkie powiązane procedury sprawdzić CTRL + Z na końcu pliku i usunąć go, jeśli to możliwe. Odbywa się to, ponieważ za pomocą kombinacji **fseek** i [ftell](ftell-ftelli64.md) lub **_fseeki64** i [_ftelli64](ftell-ftelli64.md), aby przejść w pliku, który kończy się CTRL + Z może spowodować **fseek** lub **_fseeki64** zachowywać się nieprawidłowo na końcu pliku.

Gdy CRT otwiera plik rozpoczynający się od znaku BOM, wskaźnik pliku jest umieszczany za BOM (czyli na początku rzeczywistej zawartości pliku). Jeśli musisz **fseek** do początku pliku, użyj [ftell,](ftell-ftelli64.md) aby uzyskać początkową pozycję i **fseek** do niego, a nie do pozycji 0.

Ta funkcja blokuje inne wątki podczas wykonywania i dlatego jest bezpieczne dla wątków. Aby uzyskać wersję niezablokującą, zobacz [_fseek_nolock, _fseeki64_nolock](fseek-nolock-fseeki64-nolock.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**Fseek**|\<stdio.h>|
|**_fseeki64**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>
