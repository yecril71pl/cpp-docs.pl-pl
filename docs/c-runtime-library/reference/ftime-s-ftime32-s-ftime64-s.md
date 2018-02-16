---
title: "_ftime_s —, _ftime32_s —, _ftime64_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _ftime_s
- _ftime64_s
- _ftime32_s
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
- _ftime_s
- _ftime64_s
- ftime_s
- _ftime32_s
- ftime32_s
- ftime64_s
dev_langs:
- C++
helpviewer_keywords:
- ftime32_s function
- ftime_s function
- _ftime64_s function
- current time
- ftime64_s function
- time, getting current
- _ftime_s function
- _ftime32_s function
ms.assetid: d03080d9-a520-45be-aa65-504bdb197e8b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: baf4371e90dfe06a4896c33937f578a2483475d3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="ftimes-ftime32s-ftime64s"></a>_ftime_s, _ftime32_s, _ftime64_s
Pobiera bieżący czas. Są to wersje [_ftime —, _ftime32 —, _ftime64 —](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _ftime_s(   
   struct _timeb *timeptr   
);  
errno_t _ftime32_s(   
   struct __timeb32 *timeptr   
);  
errno_t _ftime64_s(   
   struct __timeb64 *timeptr   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `timeptr`  
 Wskaźnik do `_timeb`, `__timeb32`, lub `__timeb64` struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli to się powiedzie, kod błędu w przypadku awarii. Jeśli `timeptr` jest `NULL`, jest zwracana wartość `EINVAL`.  
  
## <a name="remarks"></a>Uwagi  
 `_ftime_s` Funkcja pobiera bieżącym czasem lokalnym i zapisuje go w strukturze wskazywana przez `timeptr`. `_timeb`, `__timeb32`, I `__timeb64` struktury są zdefiniowane w SYS\Timeb.h. Zawierają one cztery pola, które są wymienione w poniższej tabeli.  
  
 `dstflag`  
 Różna od zera, jeśli czasu letniego działa obecnie na podstawie lokalnej strefy czasowej. (Zobacz [_tzset —](../../c-runtime-library/reference/tzset.md) wyjaśnienie sposobu czasu jest określany.)  
  
 `millitm`  
 Ułamek sekund (w milisekundach).  
  
 `time`  
 Czas w sekundach od północy (00: 00:00), 1 stycznia 1970, uniwersalny czas koordynowany (UTC).  
  
 `timezone`  
 Różnica (w minutach), przenoszenie westward, między czasem UTC i czasem lokalnym. Wartość `timezone` jest ustawiany na wartość zmiennej globalnej `_timezone` (zobacz `_tzset`).  
  
 `_ftime64_s`, który korzysta z `__timeb64` struktury, umożliwia tworzenie plików daty wyrażane się za pośrednictwem 23:59:59 31 grudnia 3000 UTC; natomiast `_ftime32_s` tylko reprezentuje dat za pośrednictwem 23:59:59 18 stycznia 2038 r., UTC. Północy, 1 stycznia 1970 jest dolna granica zakresu dat dla tych funkcji.  
  
 `_ftime_s` jest odpowiednikiem `_ftime64_s` i `_timeb` zawiera czas 64-bitowych. Jest to wartość true, chyba że `_USE_32BIT_TIME_T` jest zdefiniowany w takim przypadku stare zachowanie jest włączona; `_ftime_s` używany czas 32-bitowe i `_timeb` zawiera czas 32-bitowych.  
  
 `_ftime_s` sprawdza poprawność parametrów. Jeśli przekazany wskaźnika o wartości null jako `timeptr`, funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, funkcja ustawia `errno` do `EINVAL`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`_ftime_s`|\<sys/types.h > i \<sys/timeb.h >|  
|`_ftime32_s`|\<sys/types.h > i \<sys/timeb.h >|  
|`_ftime64_s`|\<sys/types.h > i \<sys/timeb.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_ftime64_s.c  
// This program uses _ftime64_s to obtain the current  
// time and then stores this time in timebuffer.  
  
#include <stdio.h>  
#include <sys/timeb.h>  
#include <time.h>  
  
int main( void )  
{  
   struct _timeb timebuffer;  
   char timeline[26];  
   errno_t err;  
   time_t time1;  
   unsigned short millitm1;  
   short timezone1;  
   short dstflag1;  
  
   _ftime64_s( &timebuffer );  
  
    time1 = timebuffer.time;  
    millitm1 = timebuffer.millitm;  
    timezone1 = timebuffer.timezone;  
    dstflag1 = timebuffer.dstflag;  
  
   printf( "Seconds since midnight, January 1, 1970 (UTC): %I64d\n",   
   time1);  
   printf( "Milliseconds: %d\n", millitm1);  
   printf( "Minutes between UTC and local time: %d\n", timezone1);  
   printf( "Daylight savings time flag (1 means Daylight time is in "  
           "effect): %d\n", dstflag1);   
  
   err = ctime_s( timeline, 26, & ( timebuffer.time ) );  
   if (err)  
   {  
       printf("Invalid argument to ctime_s. ");  
   }  
   printf( "The time is %.19s.%hu %s", timeline, timebuffer.millitm,  
           &timeline[20] );  
}  
```  
  
```Output  
Seconds since midnight, January 1, 1970 (UTC): 1051553334  
Milliseconds: 230  
Minutes between UTC and local time: 480  
Daylight savings time flag (1 means Daylight time is in effect): 1  
The time is Mon Apr 28 11:08:54.230 2003  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie czasem](../../c-runtime-library/time-management.md)   
 [asctime —, _wasctime —](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [czas lokalny, _localtime32 —, _localtime64 —](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)