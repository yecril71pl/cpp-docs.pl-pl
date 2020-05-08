---
title: _futime, _futime32, _futime64
ms.date: 4/2/2020
api_name:
- _futime64
- _futime32
- _futime
- _o__futime32
- _o__futime64
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- futime
- _futime
- futime64
- _futime64
helpviewer_keywords:
- _futime function
- futime32 function
- futime64 function
- file modification time [C++]
- _futime64 function
- futime function
- _futime32 function
ms.assetid: b942ce8f-5cc7-4fa8-ab47-de5965eded53
ms.openlocfilehash: 615e436abf9d763e73d26db61d9063d5e586232b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909923"
---
# <a name="_futime-_futime32-_futime64"></a>_futime, _futime32, _futime64

Ustawia czas modyfikacji w otwartym pliku.

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

*proces*<br/>
Deskryptor pliku w otwartym pliku.

*FILETIME*<br/>
Wskaźnik do struktury zawierającej nową datę modyfikacji.

## <a name="return-value"></a>Wartość zwracana

Zwróć wartość 0, jeśli powodzenie. Jeśli wystąpi błąd, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca wartość-1, a **errno** jest ustawiona na **EBADF**, wskazującą nieprawidłowy deskryptor pliku lub **EINVAL**wskazujący nieprawidłowy parametr.

## <a name="remarks"></a>Uwagi

Procedura **_futime** ustawia datę modyfikacji i godzinę dostępu w otwartym pliku skojarzonym z *FD*. **_futime** jest taka sama jak [_utime](utime-utime32-utime64-wutime-wutime32-wutime64.md), z tą różnicą, że jej argument jest deskryptorem pliku otwartego pliku, a nie nazwą pliku lub ścieżką do pliku. Struktura **_utimbuf** zawiera pola dla nowej daty modyfikacji i czasu dostępu. Oba pola muszą zawierać prawidłowe wartości. **_utimbuf32** i **_utimbuf64** są takie same, jak w przypadku **_utimbuf** z wyjątkiem użycia odpowiednio 32-bitowych i 64-bitowych typów czasu. **_futime** i **_utimbuf** użyć 64-bitowego typu czasu, a **_futime** jest taka sama jak w przypadku **_futime64**. Jeśli musisz wymusić stare zachowanie, zdefiniuj **_USE_32BIT_TIME_T**. Powoduje to, że **_futime** być identyczne w zachowaniu **_futime32** i powoduje, że struktura **_utimbuf** będzie używać typu czasu 32-bitowego, co jest równoznaczne z **__utimbuf32**.

**_futime64**, który używa struktury **__utimbuf64** , może odczytywać i modyfikować daty plików do 23:59:59 grudnia, 3000, UTC; wywołanie **_futime32** kończy się niepowodzeniem, jeśli data pliku jest późniejsza niż 23:59:59 stycznia 18, 2038, UTC. Północ, 1 stycznia 1970, jest dolną granicą zakresu dat dla tych funkcji.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalny nagłówek|
|--------------|---------------------|---------------------|
|**_futime**|\<sys/utime. h>|\<errno. h>|
|**_futime32**|\<sys/utime. h>|\<errno. h>|
|**_futime64**|\<sys/utime. h>|\<errno. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

### <a name="input-crt_futimec_input"></a>Dane wejściowe: crt_futime. c_input

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

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
