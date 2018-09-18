---
title: _futime _futime32, _futime64 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cdd7b68ac9e3bf55f64b9a68f7b8075eab640faa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056823"
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
Deskryptor pliku do otwartego pliku.

*FileTime*<br/>
Wskaźnik do struktury, zawierający nową datę modyfikacji.

## <a name="return-value"></a>Wartość zwracana

Zwraca 0, jeśli kończy się pomyślnie. Jeśli wystąpi błąd, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca wartość -1 i **errno** jest ustawiona na **EBADF**, wskazujący nieprawidłowego deskryptora pliku, lub **EINVAL**, wskazując nieprawidłowy parametr.

## <a name="remarks"></a>Uwagi

**_Futime** procedury ustawia datę modyfikacji i czas dostępu do otwartego pliku, które są skojarzone z *fd*. **_futime** jest taka sama jak [_utime](utime-utime32-utime64-wutime-wutime32-wutime64.md), z tą różnicą, że jej argument ma deskryptor pliku otwartego pliku, a nie nazwę pliku lub ścieżkę do pliku. **_Utimbuf —** struktura zawiera pola nową datę modyfikacji i dostępu do godziny. Oba pola muszą zawierać prawidłowe wartości. **_utimbuf32** i **_utimbuf64** są takie same jak **_utimbuf —** z wyjątkiem używanie typów 32-bitowych i 64-bitowych czasu, odpowiednio. **_futime** i **_utimbuf —** używania typu czasu 64-bitowych i **_futime** jest taka sama w zachowanie **_futime64**. Jeśli potrzebujesz wymusić stare zachowanie, zdefiniuj **_USE_32BIT_TIME_T**. Powoduje to, że takie postępowania **_futime** być identyczne w zachowanie **_futime32** i powoduje, że **_utimbuf —** struktury w celu używania typu czasu 32-bitowych, upodabniając te parametry do **__utimbuf32**.

**_futime64**, który używa **__utimbuf64 —** struktury, może odczytywać i modyfikować daty pliku do 23:59:59, 31 grudnia 3000, UTC, natomiast wywołanie **_futime32** zakończy się niepowodzeniem, jeśli data w pliku jest później niż 23:59:59 18 stycznia 2038 r. UTC. Północy 1 stycznia 1970 r., to dolna granica zakresu dat dla tych funkcji.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|
|--------------|---------------------|---------------------|
|**_futime**|\<sys/utime.h>|\<errno.h>|
|**_futime32**|\<sys/utime.h>|\<errno.h>|
|**_futime64**|\<sys/utime.h>|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
