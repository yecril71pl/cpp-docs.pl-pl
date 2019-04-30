---
title: _write
ms.date: 11/04/2016
apiname:
- _write
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
- _write
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
ms.openlocfilehash: b3fa53b21d4ea23c5f8e59de673f4074deedb505
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383415"
---
# <a name="write"></a>_write

Zapisuje dane w pliku.

## <a name="syntax"></a>Składnia

```C
int _write(
   int fd,
   const void *buffer,
   unsigned int count
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Deskryptor pliku, do którego dane są zapisywane w pliku.

*buffer*<br/>
Dane do zapisania.

*Liczba*<br/>
Liczba bajtów.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **_write** zwraca liczbę bajtów, które rzeczywiście zapisanych. Jeśli rzeczywiste miejsce na dysku jest mniejszy niż rozmiar buforu, funkcja próbuje zapisać na dysku **_write** kończy się niepowodzeniem, a nie opróżnia dowolnej zawartości buforu na dysku. Zwracana wartość-1 wskazuje błąd. Jeśli zostaną przekazane nieprawidłowe parametry, funkcja wywoła procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca wartość -1 i **errno** jest ustawiony na jedną z trzech wartości: **EBADF**, co oznacza, że deskryptor pliku jest nieprawidłowa lub plik nie jest otwarty do zapisu; **ENOSPC**, co oznacza, że nie ma wystarczającej ilości miejsca na urządzeniu na potrzeby operacji; lub **EINVAL**, co oznacza, że *buforu* jest wskaźnikiem typu null lub który nietypowym *liczba* bajtów został przekazany do zapisania do pliku w trybie Unicode.

Aby uzyskać więcej informacji na temat tych i innych kodach powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Jeśli plik jest otwarty w trybie tekstowym, znak powrotu karetki - pary wysuwu wiersza w danych wyjściowych jest zastępowany każdego znaku wysuwu wiersza. Zastąpienie nie wpływa na wartość zwracaną.

Po otwarciu pliku w tryb translacji kodu Unicode — na przykład, jeśli *fd* jest otwarty za pomocą **_otwórz** lub **_sopen** i parametrem mode, która obejmuje **_O_ WTEXT**, **_O_U16TEXT**, lub **_O_U8TEXT**, lub jeśli jest otwarty za pomocą **fopen —** i parametrem mode, która obejmuje **ccs = UNICODE**, **ccs = UTF-16LE**, lub **ccs = UTF-8**, lub zmiana tryb na tryb translacji Unicode przy użyciu **_setmode —**—*buforu* jest interpretowany jako wskaźnik do tablicy **wchar_t** zawierający **UTF-16** danych. Błąd sprawdzania poprawności parametru powoduje, że próba zapisu nieparzystą liczbę bajtów w tym trybie.

## <a name="remarks"></a>Uwagi

**_Write** funkcja pisze *liczba* bajtów z *buforu* do pliku skojarzone z *fd*. Operacja zapisu rozpoczyna się w bieżącym położeniu wskaźnika pliku (jeśli istnieje), skojarzone z danego pliku. Jeśli plik jest otwarty do wykonania operacji dołączania, rozpocznie się wykonywanie operacji na końcu bieżącego pliku. Po wykonaniu operacji zapisu wskaźnikiem pliku jest zwiększana o liczbę bajtów, które rzeczywiście zapisanych.

Podczas zapisywania plików otwartych w trybie tekstowym **_write** traktuje znaku CTRL + Z jako logicznych końca z pliku. Podczas zapisywania na urządzeniu z systemem **_write** traktuje znaku CTRL + Z buforu jako terminator danych wyjściowych.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_write**|\<io.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt__write.c
//
// This program opens a file for output and uses _write to write
// some bytes to the file.

#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <errno.h>
#include <share.h>

char buffer[] = "This is a test of '_write' function";

int main( void )
{
   int         fileHandle = 0;
   unsigned    bytesWritten = 0;

   if ( _sopen_s(&fileHandle, "write.o", _O_RDWR | _O_CREAT,
                  _SH_DENYNO, _S_IREAD | _S_IWRITE) )
      return -1;

   if (( bytesWritten = _write( fileHandle, buffer, sizeof( buffer ))) == -1 )
   {
      switch(errno)
      {
         case EBADF:
            perror("Bad file descriptor!");
            break;
         case ENOSPC:
            perror("No space left on device!");
            break;
         case EINVAL:
            perror("Invalid parameter: buffer was NULL!");
            break;
         default:
            // An unrelated error occured
            perror("Unexpected error!");
      }
   }
   else
   {
      printf_s( "Wrote %u bytes to file.\n", bytesWritten );
   }
   _close( fileHandle );
}
```

```Output
Wrote 36 bytes to file.
```

## <a name="see-also"></a>Zobacz także

[Niskiego poziomu operacji We/Wy](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
