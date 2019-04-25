---
title: _utime, _utime32, _utime64, _wutime, _wutime32, _wutime64
ms.date: 11/04/2016
apiname:
- _utime64
- _utime
- _wutime
- _wutime64
- _wutime32
- _utime32
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
ms.openlocfilehash: 8e52845a828e272ff3b8458b299c3757b8def748
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155449"
---
# <a name="utime-utime32-utime64-wutime-wutime32-wutime64"></a>_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64

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

*czasy*<br/>
Wskaźnik do wartości przechowywanej czasu.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość 0, jeśli czas modyfikacji pliku została zmieniona. Zwracana wartość-1 wskazuje błąd. Jeśli nieprawidłowy parametr został przekazany, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość -1 i **errno** jest ustawiony na jedną z następujących wartości:

|errno wartość|Warunek|
|-|-|
| **EACCES** | Ścieżka Określa katalog lub plik tylko do odczytu |
| **EINVAL** | Nieprawidłowy *razy* argumentu |
| **EMFILE** | Zbyt wiele otwartych plików (musi można otworzyć pliku, aby zmienić czas jego modyfikacji) |
| **ENOENT** | Ścieżka lub nazwa pliku nie można odnaleźć |

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) kody powrotne — Aby uzyskać więcej informacji na temat tych i innych.

Plik można zmienić z datą pod warunkiem, że zmiana daty jest po północy 1 stycznia 1970 r., a wcześniejsza od daty zakończenia funkcji używane. **_utime** i **_wutime** Użyj wartość czasu 64-bitowym, aby data zakończenia jest 23:59:59, 31 grudnia 3000, czasu UTC. Jeśli **_USE_32BIT_TIME_T** zdefiniowano Aby wymusić stare zachowanie, Data zakończenia jest 23:59:59 18 stycznia 2038 r. UTC. **_utime32** lub **_wutime32** używania typu czasu 32-bitowych, niezależnie od tego, czy **_USE_32BIT_TIME_T** jest zdefiniowana i zawsze mieć wcześniej Data zakończenia. **_utime64** lub **_wutime64** zawsze używany jest typ czasu 64-bitowych, więc te funkcje zawsze obsługuje nowszych Data zakończenia.

## <a name="remarks"></a>Uwagi

**_Utime** funkcja ustawia czas modyfikacji pliku określonego przez *filename*. Proces musi mieć dostęp do zapisu do pliku, aby można było zmienić czas. W systemie operacyjnym Windows, możesz zmienić czas dostępu i czas modyfikacji w **_utimbuf —** struktury. Jeśli *razy* jest **NULL** wskaźnik, czas modyfikacji jest ustawiony na bieżącym czasem lokalnym. W przeciwnym razie *razy* musi się odnosić do struktury typu **_utimbuf —** zdefiniowaną w SYS\UTIME. H.

**_Utimbuf —** struktury przechowuje czasy dostępu i modyfikacji plików używane przez **_utime** celu zmiany daty modyfikacji pliku. Struktura zawiera następujące pola, które są zarówno typ **time_t**:

| Pole |   |
|-------|---|
| **actime** | Czas dostępu do plików |
| **modtime** | Czas modyfikacji pliku |

Określone wersje **_utimbuf —** struktury (**_utimebuf32** i **__utimbuf64 —**) są definiowane przy użyciu 32-bitowych i 64-bitowe wersje typu time. Są one używane w 32-bitowych i 64-bitowych określonych wersji tej funkcji. **_utimbuf —** sam domyślnie korzysta z typu czasu 64-bitowych, chyba że **_USE_32BIT_TIME_T** jest zdefiniowana.

**_utime** jest taka sama jak **_futime** z tą różnicą, że *filename* argument **_utime** jest nazwa pliku lub ścieżkę do pliku, zamiast deskryptor pliku Otwórz plik.

**_wutime** to wersja znaku dwubajtowego **_utime**; *filename* argument **_wutime** jest ciągiem znaku dwubajtowego. Funkcje te zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tutime —**|**_utime**|**_utime**|**_wutime**|
|**_tutime32**|**_utime32**|**_utime32**|**_wutime32**|
|**_tutime64**|**_utime64**|**_utime64**|**_wutime64**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagane nagłówki|Opcjonalne nagłówki|
|-------------|----------------------|----------------------|
|**_utime**, **_utime32**, **_utime64**|\<sys/utime.h>|\<errno.h>|
|**_utime64**|\<sys/utime.h>|\<errno.h>|
|**_wutime**|\<utime.h > lub \<wchar.h >|\<errno.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program używa **_utime** Aby ustawić czas modyfikacji pliku do bieżącego czasu.

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
[_stat, _wstat — funkcje](stat-functions.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
