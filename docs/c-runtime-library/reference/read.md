---
title: _przeczytaj | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _read
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
- _read
dev_langs:
- C++
helpviewer_keywords:
- data [CRT]
- _read function
- read function
- data [C++], reading
- reading data [C++]
- files [C++], reading
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c67ce8ac0e754bf3003b23c56cd1d3f428be903
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="read"></a>_read

Odczytuje dane z pliku.

## <a name="syntax"></a>Składnia

```C
int _read(
   int fd,
   void *buffer,
   unsigned int count
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Plik deskryptora odwołujących się do otwartego pliku.

*buffer*<br/>
Lokalizacja magazynu danych.

*Liczba*<br/>
Maksymalna liczba bajtów.

## <a name="return-value"></a>Wartość zwracana

**_przeczytaj** zwraca liczbę bajtów odczytanych, który może być mniejsza niż *liczba* Jeśli jest dostępnych mniej niż *liczba* pozostałych bajtów w pliku lub jeśli plik został otwarty w trybie tekstowym, w takim przypadku każdy karetki LF pary "\r\n" jest zastępowany wysuwu wiersza pojedynczy znak "\n". Tylko znak pojedynczego wysuwu wiersza jest liczony w wartości zwracanej. Zastąpienie nie ma wpływu na wskaźnika pliku.

Jeśli funkcja próbuje odczytać na końcu pliku, zwraca wartość 0. Jeśli *fd* jest nieprawidłowy, plik nie jest otwarty do odczytu, lub plik jest zablokowany, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcja zwraca wartość -1 i zestawy **errno** do **ebadf —**.

Jeśli *buforu* jest **NULL**, program obsługi nieprawidłowych parametrów jest wywoływany. Jeśli wykonanie może kontynuować, funkcja zwraca wartość -1 i **errno** ustawiono **einval —**.

Aby uzyskać więcej informacji dotyczących tego i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Przeczytaj** funkcja odczytuje maksymalnie *liczba* bajtów do *buforu* z pliku skojarzone z *fd*. Operacja odczytu rozpoczyna się w bieżącym położeniu wskaźnika pliku skojarzone z danym pliku. Po wykonaniu operacji odczytu wskaźnika pliku wskazuje na następny znak nieprzeczytana.

Jeśli plik został otwarty w trybie tekstowym, Odczyt kończy kiedy **_przeczytaj** napotka CTRL + Z znak, który jest traktowany jako plik końcowy wskaźnika. Użyj [_lseek —](lseek-lseeki64.md) wyczyść wskaźnik końca pliku.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_read**|\<io.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

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
   int fh;
   unsigned int nbytes = 60000, bytesread;

   /* Open file for input: */
   if( _sopen_s( &fh, "crt_read.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
   {
      perror( "open failed on input file" );
      exit( 1 );
   }

   /* Read in input: */
   if( ( bytesread = _read( fh, buffer, nbytes ) ) <= 0 )
      perror( "Problem reading file" );
   else
      printf( "Read %u bytes from file\n", bytesread );

   _close( fh );
}
```

### <a name="input-crtreadtxt"></a>Dane wejściowe: crt_read.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Dane wyjściowe

```Output
Read 19 bytes from file
```

## <a name="see-also"></a>Zobacz także

[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fread](fread.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_write](write.md)<br/>
