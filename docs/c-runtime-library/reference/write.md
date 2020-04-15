---
title: _write
ms.date: 4/2/2020
api_name:
- _write
- _o__write
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
- _write
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
ms.openlocfilehash: a616df570d266c335337d897da59a2a0ec69b40e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367393"
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

*Fd*<br/>
Deskryptor pliku, w którym zapisywane są dane.

*Buforu*<br/>
Dane do zapisania.

*Liczba*<br/>
Liczba bajtów.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, **_write** zwraca liczbę zapisanych bajtów. Jeśli rzeczywista ilość miejsca pozostającego na dysku jest mniejsza niż rozmiar buforu, który funkcja próbuje zapisać na dysku, **_write** nie powiedzie się i nie opróżnia żadnej zawartości buforu na dysk. Zwracana wartość -1 oznacza błąd. Jeśli nieprawidłowe parametry są przekazywane, ta funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, funkcja zwraca -1 i **errno** jest ustawiona na jedną z trzech wartości: **EBADF**, co oznacza, że deskryptor pliku jest nieprawidłowy lub plik nie jest otwarty do zapisu; **ENOSPC**, co oznacza, że na urządzeniu nie ma wystarczającej ilości miejsca na operację; lub **EINVAL**, co oznacza, że *bufor* był wskaźnikiem null lub że nieparzysta *liczba* bajtów została przekazana do zapisania do pliku w trybie Unicode.

Aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Jeśli plik jest otwierany w trybie tekstowym, każdy znak kanału wiersza jest zastępowany parą kanału zwrotnego karetki na wyjściu. Zastąpienie nie wpływa na wartość zwracaną.

Gdy plik jest otwierany w trybie tłumaczenia Unicode — na przykład, jeśli *fd* jest otwierany przy użyciu **_open** lub **_sopen** i parametru trybu, który zawiera **_O_WTEXT**, **_O_U16TEXT**lub **_O_U8TEXT**, lub jeśli jest otwarty za pomocą **fopen** i parametru trybu, który zawiera **ccs =UNICODE**, **ccs=UTF-16LE**lub **ccs=UTF-8**, lub jeśli tryb zostanie zmieniony na tryb tłumaczenia Unicode przy użyciu **_setmode**—*bufor* jest interpretowany jako wskaźnik do tablicy **wchar_t** zawierającej dane **UTF-16.** Próba zapisania nieparzystej liczby bajtów w tym trybie powoduje błąd sprawdzania poprawności parametru.

## <a name="remarks"></a>Uwagi

Funkcja **_write** zapisuje bajty *zliczania* z *bufora* do pliku skojarzonego z *fd*. Operacja zapisu rozpoczyna się w bieżącym położeniu wskaźnika pliku (jeśli istnieje) skojarzonego z danym plikiem. Jeśli plik jest otwarty do do załączenia, operacja rozpoczyna się na bieżącym końcu pliku. Po operacji zapisu wskaźnik pliku jest zwiększany o liczbę zapisanych bajtów.

Podczas zapisywania do plików otwartych w trybie tekstowym **_write** traktuje znak CTRL+Z jako logiczny koniec pliku. Podczas zapisywania na urządzeniu **_write** traktuje znak CTRL+Z w buforze jako terminator wyjściowy.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_write**|\<> io.h|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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
            // An unrelated error occurred
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

## <a name="see-also"></a>Zobacz też

[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
