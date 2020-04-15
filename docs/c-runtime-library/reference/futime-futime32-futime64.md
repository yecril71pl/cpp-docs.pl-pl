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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 1f60bb3b366c48e3d53368f81ebc2528694794f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345505"
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

*Fd*<br/>
Deskryptor pliku do otwartego pliku.

*Filetime*<br/>
Wskaźnik do struktury zawierającej nową datę modyfikacji.

## <a name="return-value"></a>Wartość zwracana

Zwróć 0, jeśli zakończy się pomyślnie. Jeśli wystąpi błąd, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [obszarze Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, funkcja zwraca -1 i **errno** jest ustawiona na **EBADF**, wskazując nieprawidłowy deskryptor pliku lub **EINVAL**, wskazując nieprawidłowy parametr.

## <a name="remarks"></a>Uwagi

Procedura **_futime** określa datę modyfikacji i czas dostępu do otwartego pliku skojarzonego z *fd*. **_futime** jest identyczny [z _utime](utime-utime32-utime64-wutime-wutime32-wutime64.md), z tą różnicą, że jego argumentem jest deskryptor pliku otwartego pliku, a nie nazwa pliku lub ścieżka do pliku. Struktura **_utimbuf** zawiera pola dla nowej daty modyfikacji i godziny dostępu. Oba pola muszą zawierać prawidłowe wartości. **_utimbuf32** i **_utimbuf64** są identyczne **z _utimbuf,** z wyjątkiem użycia typów czasu 32-bitowego i 64-bitowego. **_futime** i **_utimbuf** używać 64-bitowego typu czasu, a **_futime** jest identyczny w zachowaniu **_futime64**. Jeśli chcesz wymusić stare zachowanie, zdefiniuj **_USE_32BIT_TIME_T**. Powoduje **to, że _futime** jest identyczny w zachowaniu **_futime32** i powoduje, że struktura **_utimbuf** używa 32-bitowego typu czasu, co odpowiada **__utimbuf32**.

**_futime64**, który używa struktury **__utimbuf64,** może odczytywać i modyfikować daty plików do 23:59:59, 31 grudnia 3000, UTC; mając na uwadze, że wywołanie **_futime32** nie powiedzie się, jeśli data w pliku jest późniejsza niż 23:59:59 18 stycznia 2038, UTC. Północ, 1 stycznia 1970 r., jest dolną granicą zakresu dat dla tych funkcji.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalny nagłówek|
|--------------|---------------------|---------------------|
|**_futime**|\<sys/utime.h>|\<> errno.h|
|**_futime32**|\<sys/utime.h>|\<> errno.h|
|**_futime64**|\<sys/utime.h>|\<> errno.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

### <a name="input-crt_futimec_input"></a>Dane wejściowe: crt_futime.c_input

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
