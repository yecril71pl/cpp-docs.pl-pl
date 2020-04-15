---
title: _read
ms.date: 4/2/2020
api_name:
- _read
- _o__read
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
- _read
helpviewer_keywords:
- data [CRT]
- _read function
- read function
- data [C++], reading
- reading data [C++]
- files [C++], reading
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
ms.openlocfilehash: db3726b85bb4ba7c8e9a691bef3fb063ec5709c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338133"
---
# <a name="_read"></a>_read

Odczytuje dane z pliku.

## <a name="syntax"></a>Składnia

```C
int _read(
   int const fd,
   void * const buffer,
   unsigned const buffer_size
);
```

### <a name="parameters"></a>Parametry

*Fd*<br/>
Deskryptora pliku odnoszącego się do otwartego pliku.

*Buforu*<br/>
Lokalizacja przechowywania danych.

*buffer_size*<br/>
Maksymalna liczba bajtów do odczytania.

## <a name="return-value"></a>Wartość zwracana

**_read** zwraca liczbę odczytanych bajtów, która może być mniejsza niż *buffer_size* jeśli w pliku pozostało mniej niż *buffer_size* bajtów lub jeśli plik został otwarty w trybie tekstowym. W trybie tekstowym każda para `\r\n` wiersza powrotu karetki `\n`jest zastępowana pojedynczym znakiem wysuwu wiersza . W wartości zwracanej jest liczony jest tylko pojedynczy znak źródła danych. Zastąpienie nie wpływa na wskaźnik pliku.

Jeśli funkcja próbuje odczytać na końcu pliku, zwraca 0. Jeśli *fd* jest nieprawidłowy, plik nie jest otwarty do odczytu lub plik jest zablokowany, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, funkcja zwraca wartość -1 i ustawia **errno** na **EBADF**.

Jeśli *bufor* ma **wartość NULL**lub *buffer_size* > **INT_MAX,** wywoływany jest nieprawidłowy program obsługi parametrów. Jeśli wykonanie jest dozwolone, funkcja zwraca -1 i **errno** jest ustawiona na **EINVAL**.

Aby uzyskać więcej informacji na temat tego i innych kodów zwrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_read** odczytuje maksymalnie *buffer_size* bajtów do *buforu* z pliku skojarzonego z *fd*. Operacja odczytu rozpoczyna się w bieżącym położeniu wskaźnika pliku skojarzonego z danym plikiem. Po operacji odczytu wskaźnik pliku wskazuje następny nieprzeczytany znak.

Jeśli plik został otwarty w trybie tekstowym, odczyt kończy się, gdy **_read** napotka znak CTRL+Z, który jest traktowany jako wskaźnik końca pliku. Użyj [_lseek,](lseek-lseeki64.md) aby wyczyścić wskaźnik końca pliku.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_read**|\<> io.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_read.c
/* This program opens a file named crt_read.txt
* and tries to read 60,000 bytes from
* that file using _read. It then displays the
* actual number of bytes read.
*/

#include <fcntl.h>      /* Needed only for _O_RDWR definition */
#include <io.h>
#include <stdlib.h>
#include <stdio.h>
#include <share.h>

char buffer[60000];

int main( void )
{
   int fh, bytesread;
   unsigned int nbytes = 60000;

   /* Open file for input: */
   if ( _sopen_s( &fh, "crt_read.txt", _O_RDONLY, _SH_DENYNO, 0 ))
   {
      perror( "open failed on input file" );
      exit( 1 );
   }

   /* Read in input: */
   if (( bytesread = _read( fh, buffer, nbytes )) <= 0 )
      perror( "Problem reading file" );
   else
      printf( "Read %u bytes from file\n", bytesread );

   _close( fh );
}
```

### <a name="input-crt_readtxt"></a>Dane wejściowe: crt_read.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Dane wyjściowe

```Output
Read 19 bytes from file
```

## <a name="see-also"></a>Zobacz też

[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fread](fread.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_write](write.md)<br/>
