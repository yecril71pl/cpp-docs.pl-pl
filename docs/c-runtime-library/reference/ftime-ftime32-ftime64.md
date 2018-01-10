---
title: "_ftime —, _ftime32 —, _ftime64 — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ftime64
- _ftime
- _ftime32
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
- _ftime32
- _ftime
- _ftime64
- ftime64
- ftime
- ftime32
dev_langs: C++
helpviewer_keywords:
- ftime64 function
- _ftime64 function
- current time
- _ftime function
- ftime function
- _ftime32 function
- ftime32 function
- time, getting current
ms.assetid: 96bc464c-3bcd-41d5-a212-8bbd836b814a
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 75e363d786459d2188da3567b130a8a0ad183963
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ftime-ftime32-ftime64"></a>_ftime, _ftime32, _ftime64
Pobierz bieżący czas. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_ftime_s —, _ftime32_s —, _ftime64_s —](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
void _ftime(   
   struct _timeb *timeptr   
);  
void _ftime32(   
   struct __timeb32 *timeptr   
);  
void _ftime64(   
   struct __timeb64 *timeptr   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `timeptr`  
 Wskaźnik do `_timeb`,`__timeb32` lub `__timeb64` struktury.  
  
## <a name="remarks"></a>Uwagi  
 `_ftime` Funkcja pobiera bieżącym czasem lokalnym i zapisuje go w strukturze wskazywana przez `timeptr`. `_timeb`, `__timeb32`, I `__timeb64` struktury są zdefiniowane w SYS\Timeb.h. Zawierają one cztery pola, które są wymienione w poniższej tabeli.  
  
 `dstflag`  
 Różna od zera, jeśli czasu letniego działa obecnie na podstawie lokalnej strefy czasowej. (Zobacz [_tzset —](../../c-runtime-library/reference/tzset.md) wyjaśnienie sposobu czasu jest określany.)  
  
 `millitm`  
 Ułamek sekund (w milisekundach).  
  
 `time`  
 Czas w sekundach od północy (00: 00:00), 1 stycznia 1970, uniwersalny czas koordynowany (UTC).  
  
 `timezone`  
 Różnica (w minutach), przenoszenie westward, między czasem UTC i czasem lokalnym. Wartość `timezone` jest ustawiany na wartość zmiennej globalnej `_timezone` (zobacz `_tzset`).  
  
 `_ftime64`, który korzysta z `__timeb64` struktury, umożliwia tworzenie plików daty wyrażane się za pośrednictwem 23:59:59 31 grudnia 3000 UTC; natomiast `_ftime32` tylko reprezentuje dat za pośrednictwem 23:59:59 18 stycznia 2038 r., UTC. Północy, 1 stycznia 1970 jest dolna granica zakresu dat dla tych funkcji.  
  
 `_ftime`jest odpowiednikiem `_ftime64` i `_timeb` zawiera czas 64-bitowych. Jest to wartość true, chyba że `_USE_32BIT_TIME_T` jest zdefiniowany w takim przypadku stare zachowanie jest włączona; `_ftime` używany czas 32-bitowe i `_timeb` zawiera czas 32-bitowych.  
  
 `_ftime`sprawdza poprawność parametrów. Jeśli przekazany wskaźnika o wartości null jako `timeptr`, funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, funkcja ustawia `errno` do `EINVAL`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`_ftime`|\<sys/types.h > i \<sys/timeb.h >|  
|`_ftime32`|\<sys/types.h > i \<sys/timeb.h >|  
|`_ftime64`|\<sys/types.h > i \<sys/timeb.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_ftime.c  
// compile with: /W3  
// This program uses _ftime to obtain the current  
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
  
   _ftime( &timebuffer ); // C4996  
   // Note: _ftime is deprecated; consider using _ftime_s instead  
  
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
 [ctime —, _ctime32 —, _ctime64 —, _wctime — _wctime32 —, _wctime64 —](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime —, _gmtime32 —, _gmtime64 —](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [czas lokalny, _localtime32 —, _localtime64 —](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)