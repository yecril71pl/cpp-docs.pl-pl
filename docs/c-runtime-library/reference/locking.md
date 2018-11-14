---
title: _locking
ms.date: 11/04/2016
apiname:
- _locking
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
- _locking
helpviewer_keywords:
- locking function
- bytes [C++], locking file
- files [C++], locking bytes
- files [C++], locking
- _locking function
ms.assetid: 099aaac1-d4ca-4827-aed6-24dff9844150
ms.openlocfilehash: 90327ed3388d4f18e0f64f92c33112c9ddd800f5
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327047"
---
# <a name="locking"></a>_locking

Blokuje albo odblokowuje plik w bajtach.

## <a name="syntax"></a>Składnia

```C
int _locking(
   int fd,
   int mode,
   long nbytes
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Deskryptor pliku.

*Tryb*<br/>
Blokowanie Akcja do wykonania.

*nbytes*<br/>
Liczba bajtów do zablokowania.

## <a name="return-value"></a>Wartość zwracana

**_locking —** zwraca wartość 0, jeśli kończy się pomyślnie. Zwracana wartość-1 wskazuje błąd, w którym to przypadku [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) jest ustawiony na jedną z następujących wartości.

|errno wartość|Warunek|
|-|-|
| **EACCES** | Blokowanie naruszenie (plik już zablokowana, czy odblokowana). |
| **EBADF** | Nieprawidłowego deskryptora pliku. |
| **EDEADLOCK** | Naruszenie zasad blokowania. Zwracane, jeśli **_LK_LOCK** lub **_LK_RLCK** flaga zostanie określona, plik nie może być zablokowany po 10 próbach. |
| **EINVAL** | Podano nieprawidłowy argument do **_locking —**. |

W przypadku awarii ze względu na nieprawidłowe parametry, takie jak nieprawidłowego deskryptora pliku, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Uwagi

**_Locking —** funkcja blokuje albo odblokowuje *nbytes* bajtów w pliku określonym przez *fd*. Blokowanie bajtów w pliku uniemożliwia dostęp do tych bajtów przez inne procesy. Wszystkie blokowania i odblokowywania rozpoczyna się w bieżącym położeniu wskaźnika pliku, a przechodzi przez następne *nbytes* bajtów. Umożliwia blokowanie bajtów poza końcem pliku.

*tryb* musi mieć jedną z następujących stałych manifestu, które są zdefiniowane w Locking.h.

|*tryb* wartość|Efekt|
|-|-|
| **_LK_LOCK** | Blokuje określonych bajtów. Jeśli nie można zablokować bajtów, program natychmiast próbuje ponownie po 1 sekundę. Jeśli po 10 próbach bajtów nie może być zablokowany, stała zwraca błąd. |
| **_LK_NBLCK** | Blokuje określonych bajtów. Jeśli nie można zablokować bajtów, stała zwraca błąd. |
| **_LK_NBRLCK** | Taki sam jak **_LK_NBLCK**. |
| **_LK_RLCK** | Taki sam jak **_LK_LOCK**. |
| **_LK_UNLCK** | Odblokowuje określonych bajtów, które musisz wcześniej zablokowane. |

Można zablokować pliku wielu regionów, które nie nakładają się. Region trwa musi mieć wcześniej zablokowane. **_locking —** nie regionów sąsiadujących scalania; Jeśli sąsiadujących ze sobą dwa regiony zablokowane każdego regionu, musi być odblokowany oddzielnie. Regiony powinny być zablokowane krótko i powinien zostać odblokowany przed zamknięciem pliku lub zakończenia programu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_locking**|\<IO.h > i \<sys/locking.h >|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

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

### <a name="input-crtlockingtxt"></a>Dane wejściowe: crt_locking.txt

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
