---
title: _futime —, _futime32 —, _futime64 — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _futime64
- _futime32
- _futime
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- futime
- _futime
- futime64
- _futime64
dev_langs:
- C++
helpviewer_keywords:
- _futime function
- futime32 function
- futime64 function
- file modification time [C++]
- _futime64 function
- futime function
- _futime32 function
ms.assetid: b942ce8f-5cc7-4fa8-ab47-de5965eded53
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d87d00a255901a1c21d1723a1850dfc4797c90cb
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="futime-futime32-futime64"></a>_futime, _futime32, _futime64

Ustawia czas modyfikacji otwartego pliku.

## <a name="syntax"></a>Składnia

```C
int _futime(
   int fd,
   struct _utimbuf *filetime
);
int _futime32(
   int fd,
   struct __utimbuf32 *filetime
);
int _futime64(
   int fd,
   struct __utimbuf64 *filetime
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Deskryptorów plików do otwartego pliku.

*FileTime*<br/>
Wskaźnik do struktury, zawierający nowe Data modyfikacji.

## <a name="return-value"></a>Wartość zwracana

Zwraca 0 w przypadku powodzenia. Jeśli wystąpi błąd, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, funkcja zwraca wartość -1 i **errno** ma ustawioną wartość **ebadf —**, wskazujący deskryptora nieprawidłowy plik lub **einval —**, wskazujący nieprawidłowy parametr.

## <a name="remarks"></a>Uwagi

**_Futime —** procedury ustawia datę modyfikacji i czas dostępu dla otwartego pliku skojarzone z *fd*. **_futime —** jest taka sama jak [_utime —](utime-utime32-utime64-wutime-wutime32-wutime64.md), ale jej argument jest deskryptorów plików otwartego pliku, a nie nazwę pliku lub ścieżkę do pliku. **_Utimbuf —** struktura zawiera pola, Nowa data modyfikacji i czas dostępu. Oba pola musi zawierać prawidłowe wartości. **_utimbuf32** i **_utimbuf64** są takie same jak **_utimbuf —** odpowiednio z wyjątkiem użycie typów czasu 32-bitowe i 64-bitowych. **_futime —** i **_utimbuf —** Użyj typu czasu 64-bitowe i **_futime —** jest identyczna w zachowaniu do **_futime64 —**. Aby wymusić stare zachowanie należy zdefiniować **_USE_32BIT_TIME_T**. Powoduje to wykonanie tej **_futime —** być identyczne w zachowaniu do **_futime32 —** i powoduje, że **_utimbuf —** struktury w celu używania typu czasu 32-bitowy, dzięki czemu odpowiadające **__utimbuf32**.

**_futime64 —**, który korzysta z **__utimbuf64 —** struktury, można odczytywać i modyfikować daty pliku za pośrednictwem 23:59:59 31 grudnia 3000 UTC; podczas gdy wywołanie **_futime32 —** zakończy się niepowodzeniem, jeśli jest data w pliku później niż 23:59:59 18 stycznia 2038 r., UTC. Północy, 1 stycznia 1970 jest dolna granica zakresu dat dla tych funkcji.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|
|--------------|---------------------|---------------------|
|**_futime**|\<sys/utime.h>|\<errno.h>|
|**_futime32**|\<sys/utime.h>|\<errno.h>|
|**_futime64**|\<sys/utime.h>|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_futime.c
// This program uses _futime to set the
// file-modification time to the current time.

#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <io.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <sys/utime.h>
#include <share.h>

int main( void )
{
   int hFile;

   // Show file time before and after.
   system( "dir crt_futime.c_input" );

   _sopen_s( &hFile, "crt_futime.c_input", _O_RDWR, _SH_DENYNO, 0 );

   if( _futime( hFile, NULL ) == -1 )
      perror( "_futime failed\n" );
   else
      printf( "File time modified\n" );

   _close (hFile);

   system( "dir crt_futime.c_input" );
}
```

### <a name="input-crtfutimecinput"></a>Dane wejściowe: crt_futime.c_input

```Input
Arbitrary file contents.
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
 Volume in drive Z has no label.
 Volume Serial Number is 5C68-57C1

 Directory of Z:\crt

 03/25/2004  10:40 AM                24 crt_futime.c_input
               1 File(s)             24 bytes
               0 Dir(s)  24,268,476,416 bytes free
 Volume in drive Z has no label.
 Volume Serial Number is 5C68-57C1

 Directory of Z:\crt

 03/25/2004  10:41 AM                24 crt_futime.c_input
               1 File(s)             24 bytes
               0 Dir(s)  24,268,476,416 bytes free
File time modified
```

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
