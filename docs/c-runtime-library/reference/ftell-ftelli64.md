---
title: ftell, _ftelli64
ms.date: 11/04/2016
apiname:
- _ftelli64
- ftell
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
- _ftelli64
- ftell
helpviewer_keywords:
- ftell function
- ftelli64 function
- _ftelli64 function
- file pointers [C++], getting current position
- file pointers [C++]
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
ms.openlocfilehash: cc76ad0776ae82637b95d32cdc6254d3c40da5b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660528"
---
# <a name="ftell-ftelli64"></a>ftell, _ftelli64

Pobiera bieżącą pozycję wskaźnika pliku.

## <a name="syntax"></a>Składnia

```C
long ftell(
   FILE *stream
);
__int64 _ftelli64(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Docelowy **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

**ftell —** i **_ftelli64 —** zwraca bieżącą pozycję w pliku. Wartość zwrócona przez obiekt **ftell —** i **_ftelli64 —** mogą nie odzwierciedlać przesunięcie bajtu fizycznych dla strumieni otwarty w trybie tekstowym, ponieważ tryb tekstu powoduje tłumaczenie wysuwu wiersza powrotu karetki. Użyj **ftell —** z [fseek](fseek-fseeki64.md) lub **_ftelli64 —** z [_fseeki64 —](fseek-fseeki64.md) Aby powrócić do lokalizacji plików poprawnie. W przypadku błędu **ftell —** i **_ftelli64 —** wywołują nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość-1 L i ustawiają **errno** do jednej z dwóch stałych, zdefiniowane w numer błędu. H. **EBADF** oznacza, że stała *strumienia* argument nie jest prawidłowym plikiem wartość wskaźnika lub odwołuje się do otwartego pliku. **EINVAL** oznacza nieprawidłową *strumienia* argumentów została przekazana do funkcji. Na urządzeniach bez możliwości wyszukiwania (na przykład terminale i drukarki) lub gdy *strumienia* nie odwołuje się do otwartego pliku, wartością zwracaną jest niezdefiniowany.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) kody powrotne — Aby uzyskać więcej informacji na temat tych i innych.

## <a name="remarks"></a>Uwagi

**Ftell —** i **_ftelli64 —** funkcje pobrać bieżącą pozycję wskaźnika pliku (jeśli istnieje), skojarzone z *strumienia*. Pozycja jest wyrażona jako przesunięcie względem początku strumienia.

Należy pamiętać, że po otwarciu pliku do wykonania operacji dołączania danych bieżącej pozycji w pliku nie jest określany przez ostatnią operację We/Wy przez gdzie następnego zapisu może mieć miejsce. Na przykład jeśli plik jest otwarty w celu dołączania, a ostatnia operacja została odczytu, położenie pliku jest punkt, w którym następnej operacji odczytu chce się uruchomić, nie, gdzie następnego zapisu czy uruchomić. (Po plik jest otwarty do wykonania operacji dołączania, położenie pliku zostaje przeniesiony na koniec pliku przed wykonaniem żadnych operacji zapisu). Jeśli jeszcze wystąpił żadnej operacji We/Wy na pliku otwartego do wykonania operacji dołączania, położenie pliku jest na początku pliku.

W trybie tekstowym CTRL + Z jest interpretowany jako znak końca pliku na wejściu. W przypadku plików otwartych do odczytu/zapisu **fopen —** i wszystkie powiązane procedury Sprawdź klawisze CTRL + Z końcem pliku i usuń go, jeśli jest to możliwe. Odbywa się, ponieważ używa kombinacji **ftell —** i [fseek](fseek-fseeki64.md) lub **_ftelli64 —** i [_fseeki64 —](fseek-fseeki64.md), aby przenieść w pliku, która kończy się CTRL + Z może spowodować, że **ftell —** lub **_ftelli64 —** działać nieprawidłowo w pobliżu końca pliku.

Ta funkcja umożliwia zablokowanie wątku wywołującego podczas wykonywania i dlatego jest metodą o bezpiecznych wątkach. Dla wersji bez blokady, zobacz **_ftell_nolock —**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|
|--------------|---------------------|----------------------|
|**ftell**|\<stdio.h>|\<errno.h>|
|**_ftelli64**|\<stdio.h>|\<errno.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_ftell.c
// This program opens a file named CRT_FTELL.C
// for reading and tries to read 100 characters. It
// then uses ftell to determine the position of the
// file pointer and displays this position.

#include <stdio.h>

FILE *stream;

int main( void )
{
   long position;
   char list[100];
   if( fopen_s( &stream, "crt_ftell.c", "rb" ) == 0 )
   {
      // Move the pointer by reading data:
      fread( list, sizeof( char ), 100, stream );
      // Get position after read:
      position = ftell( stream );
      printf( "Position after trying to read 100 bytes: %ld\n",
              position );
      fclose( stream );
   }
}
```

```Output
Position after trying to read 100 bytes: 100
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[fgetpos](fgetpos.md)<br/>
[fseek, _fseeki64](fseek-fseeki64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
