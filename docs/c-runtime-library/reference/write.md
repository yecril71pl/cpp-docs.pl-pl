---
title: _write
ms.date: 11/04/2016
api_name:
- _write
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _write
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
ms.openlocfilehash: 2c483df8e07b9496a0a22c1a1ebccf2b40d129cb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944856"
---
# <a name="_write"></a>_write

Zapisuje dane do pliku.

## <a name="syntax"></a>Składnia

```C
int _write(
   int fd,
   const void *buffer,
   unsigned int count
);
```

### <a name="parameters"></a>Parametry

*proces*<br/>
Deskryptor pliku pliku, w którym są zapisywane dane.

*buffer*<br/>
Dane do zapisania.

*liczbą*<br/>
Liczba bajtów.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia funkcja **_write** zwraca liczbę zapisanych bajtów. Jeśli rzeczywiste miejsce pozostało na dysku jest mniejsze niż rozmiar buforu, który funkcja próbuje zapisać na dysku, **_write** kończy się niepowodzeniem i nie opróżnia żadnego z zawartości buforu na dysk. Zwracana wartość-1 wskazuje na błąd. Jeśli przechodzą nieprawidłowe parametry, ta funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca wartość-1, a **errno** jest ustawiona na jedną z trzech wartości: **EBADF**, co oznacza, że deskryptor pliku jest nieprawidłowy lub plik nie jest otwierany do zapisu; **ENOSPC**, co oznacza, że na urządzeniu nie ma wystarczającej ilości miejsca na operację; lub **EINVAL**, co oznacza, że *bufor* był wskaźnikiem typu null lub że nieparzysta *Liczba* bajtów została przeniesiona do zapisu w pliku w trybie Unicode.

Aby uzyskać więcej informacji na temat tych i innych kodów powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Jeśli plik jest otwarty w trybie tekstowym, każdy znak wysuwu wiersza zostanie zastąpiony parą wysuwu wiersza powrotu karetki w danych wyjściowych. Zastąpienie nie ma wpływu na wartość zwracaną.

Gdy plik zostanie otwarty w trybie translacji Unicode — na przykład, jeśli *FD* zostanie otwarty przy użyciu **_open** lub **_sopen** i parametru trybu, który obejmuje **_O_WTEXT**, **_O_U16TEXT**lub **_O_U8TEXT**, lub jeśli zostanie otwarty za pomocą **fopen** i parametr trybu, który obejmuje **CCS = Unicode**, **CCS = UTF-16LE**lub **CCS = UTF-8**, lub jeśli tryb zostanie zmieniony na tryb tłumaczenia Unicode przy użyciu **_setmode**—*bufor* jest interpretowany jako wskaźnik do Tablica **wchar_t** , która zawiera dane w **formacie UTF-16** . Próba zapisania nieparzystej liczby bajtów w tym trybie powoduje błąd walidacji parametru.

## <a name="remarks"></a>Uwagi

Funkcja **_write** zapisuje *liczbę* bajtów z *buforu* do pliku skojarzonego z *FD*. Operacja zapisu rozpoczyna się na bieżącym miejscu wskaźnika pliku (jeśli istnieje) skojarzonego z danym plikiem. Jeśli plik jest otwarty do dołączenia, operacja rozpoczyna się od bieżącego końca pliku. Po operacji zapisu wskaźnik pliku jest zwiększany o liczbę zapisanych bajtów.

Podczas zapisywania do plików otwartych w trybie tekstowym **_write** traktuje znak Ctrl + z jako logiczny koniec pliku. Podczas zapisywania na urządzeniu **_write** traktuje znak Ctrl + z w buforze jako terminator wyjściowy.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_write**|\<io.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

[We/wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
