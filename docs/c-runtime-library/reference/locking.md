---
title: _locking
ms.date: 4/2/2020
api_name:
- _locking
- _o__locking
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
- _locking
helpviewer_keywords:
- locking function
- bytes [C++], locking file
- files [C++], locking bytes
- files [C++], locking
- _locking function
ms.assetid: 099aaac1-d4ca-4827-aed6-24dff9844150
ms.openlocfilehash: 2c6ee763a1491a744b25cbb517886e9354ca6152
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342061"
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

*Fd*<br/>
Deskryptor pliku.

*Tryb*<br/>
Blokowanie akcji do wykonania.

*nbajty*<br/>
Liczba bajtów do zablokowania.

## <a name="return-value"></a>Wartość zwracana

**_locking** zwraca wartość 0, jeśli zakończy się pomyślnie. Zwracana wartość -1 wskazuje błąd, w którym to przypadku [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) jest ustawiona na jedną z następujących wartości.

|wartość errno|Warunek|
|-|-|
| **EACCES ( EACCES )** | Naruszenie blokowania (plik już zablokowany lub odblokowany). |
| **EBADF** | Nieprawidłowy deskryptor pliku. |
| **EDEADLOCK ( EDEADLOCK )** | Naruszenie blokujące. Zwracany po określeniu **flagi _LK_LOCK** lub **_LK_RLCK** i nie można zablokować pliku po 10 próbach. |
| **Einval** | Nieważność argument został podany do **_locking**. |

Jeśli błąd jest spowodowany złym parametrem, takim jak nieprawidłowy deskryptor pliku, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [polu Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md)

## <a name="remarks"></a>Uwagi

Funkcja **_locking** blokuje lub odblokowuje *bajty nbytes* pliku określonego przez *fd*. Blokowanie bajtów w pliku uniemożliwia dostęp do tych bajtów przez inne procesy. Wszystkie blokowanie lub odblokowywanie rozpoczyna się w bieżącym położeniu wskaźnika pliku i przechodzi do następnego *bajtów nbytes.* Istnieje możliwość zablokowania bajtów przeszłości koniec pliku.

*tryb* musi być jedną z następujących stałych manifestu, które są zdefiniowane w Locking.h.

|wartość *trybu*|Efekt|
|-|-|
| **_LK_LOCK** | Blokuje określone bajty. Jeśli bajtów nie można zablokować, program natychmiast próbuje ponownie po 1 sekundzie. Jeśli po 10 próbach bajtów nie można zablokować, stała zwraca błąd. |
| **_LK_NBLCK** | Blokuje określone bajty. Jeśli bajtów nie można zablokować, stała zwraca błąd. |
| **_LK_NBRLCK** | Tak samo jak **_LK_NBLCK**. |
| **_LK_RLCK** | Tak samo jak **_LK_LOCK**. |
| **_LK_UNLCK** | Odblokowuje określone bajty, które muszą być wcześniej zablokowane. |

Wiele regionów pliku, które nie nakładają się na siebie, można zablokować. Odblokowany region musi być wcześniej zablokowany. **_locking** nie łączy sąsiednich regionów; Jeśli sąsiadują dwa zablokowane regiony, każdy region musi być odblokowany oddzielnie. Regiony powinny być zablokowane tylko na krótko i powinny zostać odblokowane przed zamknięciem pliku lub zamknięciem programu.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_locking**|\<io.h> i \<sys/locking.h>|\<> errno.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

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

### <a name="input-crt_lockingtxt"></a>Dane wejściowe: crt_locking.txt

```Input
The first thirty bytes of this file will be locked.
```

## <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
No one can change these bytes while I'm reading them
30 bytes read: The first thirty bytes of this
Now I'm done. Do what you will with them
```

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
