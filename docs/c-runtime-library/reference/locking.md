---
title: _locking — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- locking function
- bytes [C++], locking file
- files [C++], locking bytes
- files [C++], locking
- _locking function
ms.assetid: 099aaac1-d4ca-4827-aed6-24dff9844150
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1666f631d9bceccb8925b2002b797753e024ab9d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="locking"></a>_locking

Umożliwia zablokowanie lub odblokowanie pliku w bajtach.

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
Plik deskryptora.

*Tryb*<br/>
Blokowanie akcję do wykonania.

*nbytes*<br/>
Liczba bajtów do zablokowania.

## <a name="return-value"></a>Wartość zwracana

**_locking —** zwraca wartość 0, jeśli to się powiedzie. Zwracana wartość -1 wskazuje błąd, w którym to przypadku [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) ustawiono na jedną z następujących wartości.

|errno wartość|Warunek|
|-|-|
**EACCES**|Blokowanie naruszenie (plik już zablokowana, czy odblokowana).
**EBADF —**|Nieprawidłowy plik deskryptora.
**EDEADLOCK —**|Naruszenie zasad blokowania. Zwracane, jeśli **_lk_lock —** lub **_lk_rlck —** określono flagę i pliku nie może być zablokowany po 10 próbach.
**EINVAL —**|Podano nieprawidłowy argument do **_locking —**.

Jeśli niepowodzenie jest spowodowane zły parametr, takich jak deskryptora nieprawidłowy plik program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Uwagi

**_Locking —** funkcji powoduje zablokowanie lub odblokowanie *nbytes* bajtów pliku określonego przez *fd*. Blokowanie bajtów w pliku uniemożliwia dostęp do tych bajtów przez inne procesy. Wszystkie blokowania i odblokowywania rozpoczyna się w bieżącym położeniu wskaźnika pliku i przechodzi do następnego *nbytes* bajtów. Umożliwia blokowanie bajtów poza końcem pliku.

*tryb* musi mieć jedną z następujących stałych manifestu, które są zdefiniowane w Locking.h.

|*tryb* wartość|Efekt|
|-|-|
**_LK_LOCK —**|Umożliwia zablokowanie określonych bajtów. Jeśli bajtów nie może być zablokowany, program natychmiast podejmie próbę 1 sekundę. Jeśli po 10 próbach bajtów nie może być zablokowany, stała zwraca błąd.
**_LK_NBLCK —**|Umożliwia zablokowanie określonych bajtów. Jeśli bajtów nie może być zablokowany, stała zwraca błąd.
**_LK_NBRLCK —**|Taki sam jak **_lk_nblck —**.
**_LK_RLCK —**|Taki sam jak **_lk_lock —**.
**_LK_UNLCK —**|Umożliwia odblokowanie określonych bajtów, które należy wcześniej zablokowane.

Można zablokować pliku wielu regionach, które nie nakładają się. Trwa odblokowywanie region musi zostały wcześniej zablokowane. **_locking —** nie scalania sąsiadujących ze sobą regionów; Jeśli dwóch regionach zablokowanym sąsiadujących ze sobą, każdy region musi być odblokowany oddzielnie. Regiony ma zostać zablokowana krótko i powinien zostać odblokowany przed zamknięciem pliku lub zakończenia programu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_locking**|\<IO.h > i \<sys/locking.h >|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

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
