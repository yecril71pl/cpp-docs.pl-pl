---
title: _utime, _utime32, _utime64, _wutime, _wutime32, _wutime64
ms.date: 11/04/2016
api_name:
- _utime64
- _utime
- _wutime
- _wutime64
- _wutime32
- _utime32
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tutime
- _utime64
- wutime
- utime32
- wutime64
- _utime
- wutime32
- _wutime
- utime
- utime64
- _wutime64
- _utime32
- _tutime64
- _wutime32
helpviewer_keywords:
- tutime function
- utime32 function
- utime64 function
- _utime function
- _tutime32 function
- time [C++], file modification
- wutime function
- _wutime function
- _wutime32 function
- _tutime64 function
- _tutime function
- files [C++], modification time
- _wutime64 function
- _utime32 function
- utime function
- _utime64 function
- wutime64 function
- wutime32 function
- tutime64 function
- tutime32 function
ms.assetid: 8d482d40-19b9-4591-bfee-5d7f601d1a9e
ms.openlocfilehash: d55261b59dbf201be9869f3ab9ced2d2cbab5e02
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945734"
---
# <a name="_utime-_utime32-_utime64-_wutime-_wutime32-_wutime64"></a>_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64

Ustaw czas modyfikacji pliku.

## <a name="syntax"></a>Składnia

```C
int _utime(
   const char *filename,
   struct _utimbuf *times
);
int _utime32(
   const char *filename,
   struct __utimbuf32 *times
);
int _utime64(
   const char *filename,
   struct __utimbuf64 *times
);
int _wutime(
   const wchar_t *filename,
   struct _utimbuf *times
);
int _wutime32(
   const wchar_t *filename,
   struct __utimbuf32 *times
);
int _wutime64(
   const wchar_t *filename,
   struct __utimbuf64 *times
);
```

### <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Wskaźnik na ciąg, który zawiera ścieżkę lub nazwę pliku.

*trzykrotn*<br/>
Wskaźnik do przechowywanych wartości czasu.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość 0, jeśli czas modyfikacji pliku został zmieniony. Zwracana wartość-1 wskazuje na błąd. Jeśli przeszedł nieprawidłowy parametr, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość-1 i **errno** na jedną z następujących wartości:

|errno wartość|Warunek|
|-|-|
| **EACCES** | Ścieżka Określa plik katalogu lub tylko do odczytu |
| **EINVAL** | Nieprawidłowy *czas* argumentu |
| **EMFILE** | Zbyt wiele otwartych plików (plik musi być otwarty, aby zmienić jego czas modyfikacji) |
| **ENOENT** | Nie znaleziono ścieżki lub nazwy pliku |

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) , aby uzyskać więcej informacji na temat tych i innych kodów powrotu.

Datę można zmienić dla pliku, jeśli data zmiany przypada po północy, 1 stycznia 1970 i przed datą końcową używanej funkcji. **_utime** i **_wutime** używają 64-bitowej wartości czasu, więc data końcowa to 23:59:59, 31 grudnia 3000, UTC. Jeśli **_USE_32BIT_TIME_T** jest zdefiniowany w celu wymuszenia starego zachowania, Data końcowa to 23:59:59 stycznia 18, 2038, UTC. **_utime32** lub **_wutime32** używają 32-bitowego typu czasu, niezależnie od tego, czy **_USE_32BIT_TIME_T** jest zdefiniowany, i zawsze mają wcześniejszą datę końcową. **_utime64** lub **_wutime64** zawsze używają 64-bitowego typu czasu, dzięki czemu te funkcje zawsze obsługują późniejszą datę zakończenia.

## <a name="remarks"></a>Uwagi

Funkcja **_utime** ustawia czas modyfikacji pliku określonego przez *filename*. Aby można było zmienić czas, proces musi mieć dostęp do zapisu w pliku. W systemie operacyjnym Windows można zmienić czas dostępu i czas modyfikacji w strukturze **_utimbuf** . Jeśli *czas* jest wskaźnikiem o **wartości null** , czas modyfikacji jest ustawiany na bieżący czas lokalny. W przeciwnym razie *czasy* muszą wskazywać na strukturę typu **_utimbuf**, zdefiniowane w SYS\UTIME. C.

W strukturze **_utimbuf** są przechowywane czasy dostępu i modyfikacji plików używane przez **_utime** w celu zmiany daty modyfikacji pliku. Struktura zawiera następujące pola, które są zarówno typu **time_t**:

| Pole |   |
|-------|---|
| **actime** | Czas dostępu do pliku |
| **modtime** | Godzina modyfikacji pliku |

Określone wersje struktury **_utimbuf** ( **_utimebuf32** i **__utimbuf64**) są zdefiniowane przy użyciu 32-bitowych i 64-bitowych wersji typu czasu. Są one używane w 32-bitowych i 64-bitowych wersjach tej funkcji. **_utimbuf** domyślnie używa typu czasu 64-bitowego, chyba że **_USE_32BIT_TIME_T** jest zdefiniowany.

**_utime** jest identyczny z **_futime** , z tą różnicą, że argument *filename* **_utime** jest nazwą pliku lub ścieżką do pliku, a nie deskryptorem pliku otwartego pliku.

**_wutime** to dwubajtowa wersja **_utime**; argumentem *filename* **_wutime** jest ciąg znaków dwubajtowych. Funkcje te zachowują się identycznie w inny sposób.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tutime**|**_utime**|**_utime**|**_wutime**|
|**_tutime32**|**_utime32**|**_utime32**|**_wutime32**|
|**_tutime64**|**_utime64**|**_utime64**|**_wutime64**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagane nagłówki|Opcjonalne nagłówki|
|-------------|----------------------|----------------------|
|**_utime**, **_utime32**, **_utime64**|\<sys/utime.h>|\<errno.h>|
|**_utime64**|\<sys/utime.h>|\<errno.h>|
|**_wutime**|\<utime. h > lub \<WCHAR. h >|\<errno.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program używa **_utime** do ustawienia czasu modyfikacji pliku na bieżącą godzinę.

```C
// crt_utime.c
#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/utime.h>
#include <time.h>

int main( void )
{
   struct tm tma = {0}, tmm = {0};
   struct _utimbuf ut;

   // Fill out the accessed time structure
   tma.tm_hour = 12;
   tma.tm_isdst = 0;
   tma.tm_mday = 15;
   tma.tm_min = 0;
   tma.tm_mon = 0;
   tma.tm_sec = 0;
   tma.tm_year = 103;

   // Fill out the modified time structure
   tmm.tm_hour = 12;
   tmm.tm_isdst = 0;
   tmm.tm_mday = 15;
   tmm.tm_min = 0;
   tmm.tm_mon = 0;
   tmm.tm_sec = 0;
   tmm.tm_year = 102;

   // Convert tm to time_t
   ut.actime = mktime(&tma);
   ut.modtime = mktime(&tmm);

   // Show file time before and after
   system( "dir crt_utime.c" );
   if( _utime( "crt_utime.c", &ut ) == -1 )
      perror( "_utime failed\n" );
   else
      printf( "File time modified\n" );
   system( "dir crt_utime.c" );
}
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
Volume in drive C has no label.
Volume Serial Number is 9CAC-DE74

Directory of C:\test

01/09/2003  05:38 PM               935 crt_utime.c
               1 File(s)            935 bytes
               0 Dir(s)  20,742,955,008 bytes free
File time modified
Volume in drive C has no label.
Volume Serial Number is 9CAC-DE74

Directory of C:\test

01/15/2002  12:00 PM               935 crt_utime.c
               1 File(s)            935 bytes
               0 Dir(s)  20,742,955,008 bytes free
```

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[_futime, _futime32, _futime64](futime-futime32-futime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_stat, _wstat Functions](stat-functions.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
