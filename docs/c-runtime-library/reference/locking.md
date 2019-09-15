---
title: _locking
ms.date: 11/04/2016
api_name:
- _locking
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
- _locking
helpviewer_keywords:
- locking function
- bytes [C++], locking file
- files [C++], locking bytes
- files [C++], locking
- _locking function
ms.assetid: 099aaac1-d4ca-4827-aed6-24dff9844150
ms.openlocfilehash: 4450c511b9d98c31b7e6a777f54f3bd8e0affbb7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953269"
---
# <a name="_locking"></a>_locking

Blokuje lub odblokowuje bajty pliku.

## <a name="syntax"></a>Składnia

```C
int _locking(
   int fd,
   int mode,
   long nbytes
);
```

### <a name="parameters"></a>Parametry

*proces*<br/>
Deskryptor pliku.

*wyst*<br/>
Akcja blokowania do wykonania.

*nbytes*<br/>
Liczba bajtów do zablokowania.

## <a name="return-value"></a>Wartość zwracana

**_locking** zwraca wartość 0, jeśli powodzenie. Zwracana wartość-1 oznacza niepowodzenie, w tym przypadku [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) jest ustawiony na jedną z następujących wartości.

|errno wartość|Warunek|
|-|-|
| **EACCES** | Naruszenie blokowania (plik jest już zablokowany lub odblokowany). |
| **EBADF** | Nieprawidłowy deskryptor pliku. |
| **EDEADLOCK** | Naruszenie zasad blokowania. Zwracany, gdy została określona flaga **_LK_LOCK** lub **_LK_RLCK** , a plik nie może być zablokowany po 10 próbach. |
| **EINVAL** | Podano nieprawidłowy argument **_locking**. |

Jeśli błąd jest spowodowany nieprawidłowym parametrem, takim jak nieprawidłowy deskryptor pliku, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Uwagi

Funkcja **_locking** blokuje lub odblokowuje *nBytes* bajty pliku określonego przez *FD*. Zablokowanie bajtów w pliku uniemożliwia dostęp do tych bajtów przez inne procesy. Wszystkie blokady lub odblokowywanie zaczynają się na bieżącym miejscu wskaźnika pliku i przechodzą do następnych *nBytes* bajtów. Istnieje możliwość zablokowania bajtów poza końcem pliku.

*tryb* musi być jednym z następujących stałych manifestu, które są zdefiniowane w bloku. h.

|wartość *trybu*|Efekt|
|-|-|
| **_LK_LOCK** | Blokuje określone bajty. Jeśli bajty nie mogą być zablokowane, program natychmiast ponowi próbę po 1 sekundzie. Jeśli po 10 próbach nie będzie można zablokować bajtów, stała zwraca błąd. |
| **_LK_NBLCK** | Blokuje określone bajty. Jeśli bajty nie mogą być zablokowane, stała zwraca błąd. |
| **_LK_NBRLCK** | Analogicznie jak **_LK_NBLCK**. |
| **_LK_RLCK** | Analogicznie jak **_LK_LOCK**. |
| **_LK_UNLCK** | Odblokowuje określone bajty, które muszą być wcześniej zablokowane. |

Nie można zablokować wielu regionów pliku, który nie nakłada się na siebie. Odblokowany region musi być wcześniej zablokowany. **_locking** nie scala sąsiadujących regionów; Jeśli dwa zablokowane regiony są przyległe, należy odblokować każdy region osobno. Regiony powinny być blokowane tylko na krótko i powinny być odblokowane przed zamknięciem pliku lub zamknięciem programu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_locking**|\<IO. h > i \<sys/blokowanie. h >|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_locking.c
/* This program opens a file with sharing. It locks
* some bytes before reading them, then unlocks them. Note that the
* program works correctly only if the file exists.
*/

#include <sys/types.h>
#include <sys/stat.h>
#include <sys/locking.h>
#include <share.h>
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include <io.h>

int main( void )
{
   int  fh, numread;
   char buffer[40];

   /* Quit if can't open file or system doesn't
    * support sharing.
    */
   errno_t err = _sopen_s( &fh, "crt_locking.txt", _O_RDONLY, _SH_DENYNO,
                          _S_IREAD | _S_IWRITE );
   printf( "%d %d\n", err, fh );
   if( err != 0 )
      exit( 1 );

   /* Lock some bytes and read them. Then unlock. */
   if( _locking( fh, LK_NBLCK, 30L ) != -1 )
   {
      long lseek_ret;
      printf( "No one can change these bytes while I'm reading them\n" );
      numread = _read( fh, buffer, 30 );
      buffer[30] = '\0';
      printf( "%d bytes read: %.30s\n", numread, buffer );
      lseek_ret = _lseek( fh, 0L, SEEK_SET );
      _locking( fh, LK_UNLCK, 30L );
      printf( "Now I'm done. Do what you will with them\n" );
   }
   else
      perror( "Locking failed\n" );

   _close( fh );
}
```

### <a name="input-crt_lockingtxt"></a>Dane wejściowe: crt_locking. txt

```Input
The first thirty bytes of this file will be locked.
```

## <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
No one can change these bytes while I'm reading them
30 bytes read: The first thirty bytes of this
Now I'm done. Do what you will with them
```

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
