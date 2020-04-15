---
title: _utime, _utime32, _utime64, _wutime, _wutime32, _wutime64
ms.date: 4/2/2020
api_name:
- _utime64
- _utime
- _wutime
- _wutime64
- _wutime32
- _utime32
- _o__utime32
- _o__utime64
- _o__wutime32
- _o__wutime64
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
ms.openlocfilehash: 5c530f46877bdb23fc51fb49beab8abfc0c16b2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361205"
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

*Pod nazwą*<br/>
Wskaźnik do ciągu zawierającego ścieżkę lub nazwę pliku.

*Razy*<br/>
Wskaźnik do przechowywanych wartości czasu.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość 0, jeśli czas modyfikacji pliku został zmieniony. Zwracana wartość -1 oznacza błąd. Jeśli nieprawidłowy parametr jest przekazywany, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametru.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te funkcje zwracają -1 i **errno** jest ustawiona na jedną z następujących wartości:

|wartość errno|Warunek|
|-|-|
| **EACCES ( EACCES )** | Path określa katalog lub plik tylko do odczytu |
| **Einval** | Argument Nieprawidłowy *czas* |
| **EMFILE (EMFILE)** | Zbyt wiele otwartych plików (plik musi zostać otwarty, aby zmienić czas modyfikacji) |
| **Enoent** | Nie znaleziono ścieżki lub nazwy pliku |

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr,](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych.

Datę można zmienić dla pliku, jeśli data zmiany jest po północy, 1 stycznia 1970 r. i przed datą zakończenia używanej funkcji. **_utime** i **_wutime** użyć 64-bitowej wartości czasu, więc data zakończenia to 23:59:59, 31 grudnia 3000, UTC. Jeśli **_USE_32BIT_TIME_T** jest zdefiniowany w celu wymuszenia starego zachowania, data zakończenia jest 23:59:59 18 stycznia 2038, UTC. **_utime32** lub **_wutime32** używać 32-bitowego typu czasu, niezależnie od tego, czy **_USE_32BIT_TIME_T** jest zdefiniowany i zawsze mają wcześniejszą datę zakończenia. **_utime64** lub **_wutime64** zawsze używać typu czasu 64-bitowego, więc te funkcje zawsze obsługują późniejszą datę zakończenia.

## <a name="remarks"></a>Uwagi

Funkcja **_utime** ustawia czas modyfikacji pliku określonego przez *nazwę pliku*. Proces musi mieć dostęp do zapisu do pliku, aby zmienić czas. W systemie operacyjnym Windows można zmienić czas dostępu i czas modyfikacji w strukturze **_utimbuf.** Jeśli *czas* jest wskaźnikiem **NULL,** czas modyfikacji jest ustawiony na bieżący czas lokalny. W przeciwnym razie *czasy* muszą wskazywać strukturę typu **_utimbuf**, zdefiniowaną w SYS\UTIME. H.

Struktura **_utimbuf** przechowuje czasy dostępu do plików i modyfikacji używane przez **_utime** do zmiany dat modyfikacji pliku. Struktura ma następujące pola, które są zarówno typu **time_t:**

| Pole |   |
|-------|---|
| **actime** | Czas dostępu do pliku |
| **modtime** | Czas modyfikacji pliku |

Określone wersje struktury **_utimbuf** **(_utimebuf32** i **__utimbuf64)** są definiowane przy użyciu wersji 32-bitowych i 64-bitowych typu czasu. Są one używane w 32-bitowych i 64-bitowych wersjach tej funkcji. **_utimbuf** domyślnie używa 64-bitowego typu czasu, chyba że **zdefiniowano _USE_32BIT_TIME_T.**

**_utime** jest identyczna **z _futime** z tą różnicą, że argument *nazwy pliku* **_utime** jest nazwa pliku lub ścieżka do pliku, a nie deskryptor pliku otwartego pliku.

**_wutime** jest szerokoznakową wersją **_utime;** *argumentnazyt,* który **ma _wutime** jest ciągiem znaków o szerokim charakterze. Te funkcje zachowują się identycznie w przeciwnym razie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tutime**|**_utime**|**_utime**|**_wutime**|
|**_tutime32**|**_utime32**|**_utime32**|**_wutime32**|
|**_tutime64**|**_utime64**|**_utime64**|**_wutime64**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagane nagłówki|Opcjonalne nagłówki|
|-------------|----------------------|----------------------|
|**_utime** **, _utime32**, **_utime64**|\<sys/utime.h>|\<> errno.h|
|**_utime64**|\<sys/utime.h>|\<> errno.h|
|**_wutime**|\<utime.h> lub \<wchar.h>|\<> errno.h|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program używa **_utime,** aby ustawić czas modyfikacji pliku do bieżącego czasu.

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

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[_futime, _futime32, _futime64](futime-futime32-futime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_stat, funkcje _wstat](stat-functions.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
