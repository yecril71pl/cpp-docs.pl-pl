---
title: _Write | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- _write
dev_langs:
- C++
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f800c42480b6518c7482c15bfa18646b1988dc8a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="write"></a>_write

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

*FD*<br/>
Plik deskryptora pliku, w którym zapisywane są dane.

*buffer*<br/>
Dane do zapisania.

*Liczba*<br/>
Liczba bajtów.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **_write** zwraca liczbę bajtów zapisana. Jeśli rzeczywiste miejsce na dysku jest mniejszy niż rozmiar buforu funkcji próbuje zapisać na dysku, **_write** kończy się niepowodzeniem i nie mogło opróżnić dowolnej zawartości buforu na dysku. Zwracana wartość -1 wskazuje błąd. Jeżeli nie przekazano nieprawidłowe parametry, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, funkcja zwraca wartość -1 i **errno** ustawiono na jedną z trzech wartości: **ebadf —**, co oznacza, że deskryptorów plików jest nieprawidłowy lub plik nie jest otwarty do zapisu; **Enospc —**, co oznacza, że nie ma wystarczającej ilości miejsca na urządzeniu dla operacji; lub **einval —**, co oznacza, że *buforu* wskaźnika o wartości null lub który nietypowym *liczba* przekazano bajtów do zapisania pliku w trybie Unicode.

Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Jeśli plik jest otwarty w trybie tekstowym, każdy znak wysuwu wiersza jest zastępowany powrotu karetki - pary wysuwu wiersza w danych wyjściowych. Zastąpienie nie ma wpływu na wartość zwracaną.

Po otwarciu pliku w trybie translacji Unicode — na przykład, jeśli *fd* jest otwarty przy użyciu **_otwórz** lub **_sopen —** i parametr tryb, który obejmuje **_O_ WTEXT**, **_O_U16TEXT**, lub **_O_U8TEXT**, lub jeśli został on otwarty przy użyciu **fopen —** i parametr tryb, który obejmuje **ccs = UNICODE**, **ccs = UTF-16LE**, lub **ccs = UTF-8**, lub jeśli tryb jest zmienione na tryb tłumaczenia Unicode za pomocą **_setmode —**—*buforu* jest interpretowany jako wskaźnik do tablicy **wchar_t** zawierający **UTF-16** danych. Próba zapisu nieparzystą liczbę bajtów w tym trybie powoduje błąd sprawdzania poprawności parametru.

## <a name="remarks"></a>Uwagi

**_Write** funkcji zapisy *liczba* bajtów z *buforu* do pliku skojarzone z *fd*. Operacja zapisu rozpoczyna się w bieżącym położeniu wskaźnika pliku (jeśli istnieje), skojarzone z danym pliku. Jeśli plik jest otwarty do dołączenia, operacja rozpoczyna się od końca bieżącego pliku. Po wykonaniu operacji zapisu wskaźnika pliku zwiększa się o liczba bajtów zapisanych w rzeczywistości.

Podczas zapisywania pliki otwarte w trybie tekstowym **_write** traktuje znaku CTRL + Z jako logiczne końca z pliku. Podczas zapisu na urządzeniu, **_write** traktuje znaku CTRL + Z buforu jako terminatora danych wyjściowych.

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

[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
