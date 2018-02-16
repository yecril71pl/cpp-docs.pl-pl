---
title: "_utime —, _utime32 —, _utime64 —, _wutime —, _wutime32 —, _wutime64 — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f94c67fe75f5675192dbd0f306d8eef0aace70f5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="utime-utime32-utime64-wutime-wutime32-wutime64"></a>_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64
Ustaw czas modyfikacji pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Wskaźnik do ciąg, który zawiera ścieżkę lub nazwę pliku.  
  
 `times`  
 Wskaźnik do wartości przechowywanej czasu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji zwraca wartość 0, jeśli czas modyfikacji pliku została zmieniona. Zwracana wartość -1 wskazuje błąd. Jeżeli nie przekazano nieprawidłowy parametr, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli wykonanie może kontynuować, następujące funkcje i `errno` ustawiono na jedną z następujących wartości:  
  
 `EACCES`  
 Określa ścieżkę katalogu lub pliku tylko do odczytu  
  
 `EINVAL`  
 Nieprawidłowy `times` argumentu  
  
 `EMFILE`  
 Zbyt wiele otwartych plików (Aby zmienić czas jego modyfikacji musi można otworzyć pliku)  
  
 `ENOENT`  
 Ścieżka lub nazwa pliku nie można odnaleźć  
  
 Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) kody powrotne — Aby uzyskać więcej informacji na temat tych i innych.  
  
 Jeśli zmiana daty jest po północy 1 stycznia 1970 i przed datą zakończenia używana funkcja można zmienić daty dla pliku. `_utime` i `_wutime` używać wartość czasu 64-bitowym, dlatego Data zakończenia jest 23:59:59 31 grudnia 3000 UTC. Jeśli `_USE_32BIT_TIME_T` zdefiniowano Aby wymusić stare zachowanie, Data zakończenia jest 23:59:59 18 stycznia 2038 r., UTC. `_utime32` lub `_wutime32` Użyj typu czasu 32-bitowy, niezależnie od tego, czy `_USE_32BIT_TIME_T` jest zdefiniowana i zawsze mają wcześniejszą datę zakończenia. `_utime64` lub `_wutime64` zawsze używany jest typ czas 64-bitowych, więc te funkcje zawsze obsługuje nowszych Data zakończenia.  
  
## <a name="remarks"></a>Uwagi  
 `_utime` Funkcja ustawia czas modyfikacji pliku określonego przez `filename` *.* Proces musi mieć dostęp do zapisu do pliku, aby zmienić czas. W systemie operacyjnym Windows, można zmienić czas dostępu i czas modyfikacji w `_utimbuf` struktury. Jeśli `times` jest `NULL` wskaźnika, czas modyfikacji jest ustawiony na bieżącym czasem lokalnym. W przeciwnym razie `times` musi wskazywać struktura typu `_utimbuf`zdefiniowanej w SYS\UTIME. H.  
  
 `_utimbuf` Struktury zapisuje godziny dostępu i modyfikacji pliku używany przez `_utime` zmiany daty modyfikacji pliku. Struktura ma następujące pola, które są typu `time_t`:  
  
 `actime`  
 Czas dostępu do pliku  
  
 `modtime`  
 Czas modyfikacji pliku  
  
 Określonych wersji `_utimbuf` struktury (`_utimebuf32` i `__utimbuf64`) są definiowane przy użyciu 32-bitowe i 64-bitowe wersje typu time. Są one używane w 32-bitowych i 64-bitowych wersjach określonych tej funkcji. `_utimbuf` się domyślnie korzysta z typu czasu 64-bitowych, chyba że `_USE_32BIT_TIME_T` jest zdefiniowany.  
  
 `_utime` jest taka sama jak `_futime` z tą różnicą, że `filename` argumentu `_utime` jest nazwa pliku lub ścieżkę do pliku, a nie deskryptorów plików, otwórz plik.  
  
 `_wutime` jest to wersja znaków dwubajtowych `_utime`; `filename` argument `_wutime` jest ciągiem znaków dwubajtowych. Funkcje te działają tak samo w przeciwnym razie wartość.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tutime`|`_utime`|`_utime`|`_wutime`|  
|`_tutime32`|`_utime32`|`_utime32`|`_wutime32`|  
|`_tutime64`|`_utime64`|`_utime64`|`_wutime64`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagane nagłówki|Opcjonalne nagłówki|  
|-------------|----------------------|----------------------|  
|`_utime`, `_utime32`, `_utime64`|\<sys/utime.h>|\<errno.h>|  
|`_utime64`|\<sys/utime.h>|\<errno.h>|  
|`_wutime`|\<utime.h > lub \<wchar.h >|\<errno.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Ten program używa `_utime` Aby ustawić czas modyfikacji pliku do bieżącego czasu.  
  
```  
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
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
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
 [Zarządzanie czasem](../../c-runtime-library/time-management.md)   
 [asctime —, _wasctime —](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [_futime, _futime32, _futime64](../../c-runtime-library/reference/futime-futime32-futime64.md)   
 [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [czas lokalny, _localtime32 —, _localtime64 —](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [_stat, _wstat — funkcje](../../c-runtime-library/reference/stat-functions.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)