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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 2f43fc54a0092afc6ab5855c160a7879747faef7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919516"
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

*proces*<br/>
Deskryptor pliku odwołujący się do otwartego pliku.

*buforu*<br/>
Lokalizacja magazynu dla danych.

*buffer_size*<br/>
Maksymalna liczba bajtów do odczytania.

## <a name="return-value"></a>Wartość zwracana

**_read** zwraca liczbę odczytanych bajtów, która może być mniejsza niż *buffer_size* , jeśli w pliku znajduje się mniej niż *buffer_size* bajtów lub plik został otwarty w trybie tekstowym. W trybie tekstowym każda para `\r\n` wysuwu wiersza jest zastępowana pojedynczym znakiem `\n`wysuwu wiersza. W zwracanej wartości jest uwzględniany tylko pojedynczy znak wysuwu wiersza. Zastąpienie nie ma wpływu na wskaźnik pliku.

Jeśli funkcja próbuje odczytać na końcu pliku, zwraca 0. Jeśli *FD* jest nieprawidłowy, plik nie jest otwarty do odczytu lub plik jest zablokowany, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca wartość-1 i ustawia **errno** na **EBADF**.

Jeśli *bufor* ma **wartość null**lub jeśli *buffer_size* > **INT_MAX**, zostanie wywołana procedura obsługi nieprawidłowego parametru. Jeśli wykonanie może być kontynuowane, funkcja zwraca wartość-1, a **errno** jest ustawiona na **EINVAL**.

Aby uzyskać więcej informacji na temat tego i innych kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_read** odczytuje maksymalnie *buffer_size* bajtów do *buforu* z pliku skojarzonego z *FD*. Operacja odczytu rozpoczyna się na bieżącym miejscu wskaźnika pliku skojarzonego z danym plikiem. Po operacji odczytu wskaźnik pliku wskazuje na Następny nieprzeczytany znak.

Jeśli plik został otwarty w trybie tekstowym, odczyt kończy się, gdy **_read** NAPOTKA znak Ctrl + Z, który jest traktowany jako wskaźnik końca pliku. Użyj [_lseek](lseek-lseeki64.md) , aby wyczyścić wskaźnik końca pliku.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_read**|\<IO. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

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

### <a name="input-crt_readtxt"></a>Dane wejściowe: crt_read. txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Dane wyjściowe

```Output
Read 19 bytes from file
```

## <a name="see-also"></a>Zobacz też

[We/wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fread](fread.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_write](write.md)<br/>
