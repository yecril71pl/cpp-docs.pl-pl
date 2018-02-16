---
title: "localtime_s —, _localtime32_s —, _localtime64_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _localtime64_s
- _localtime32_s
- localtime_s
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
- _localtime32_s
- localtime32_s
- localtime_s
- localtime64_s
- _localtime64_s
dev_langs:
- C++
helpviewer_keywords:
- _localtime64_s function
- localtime32_s function
- _localtime32_s function
- localtime64_s function
- time, converting values
- localtime_s function
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e30705867a9114fd44b8850d5cf950c2c1d8c4ce
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="localtimes-localtime32s-localtime64s"></a>localtime_s, _localtime32_s, _localtime64_s
Konwertuje wartość czasu i poprawia na podstawie lokalnej strefy czasowej. Są to wersje [konwersję _localtime32 —, _localtime64 —](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t localtime_s(  
   struct tm* _tm,  
   const time_t *time   
);  
errno_t _localtime32_s(  
   struct tm* _tm,  
   const time32_t *time   
);  
errno_t _localtime64_s(  
   struct tm* _tm,  
   const _time64_t *time   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `_tm`  
 Wskaźnik do struktury czasu zostać wypełnione.  
  
 `time`  
 Wskaźnik do czasu przechowywane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli to się powiedzie. Wartość zwracana jest kod błędu w przypadku awarii. Kody błędów są definiowane w Errno.h. Aby uzyskać listę tych błędów, zobacz [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|`_tm`|`time`|Wartość zwracana|Wartość w `_tm`|Wywołuje program obsługi nieprawidłowych parametrów|  
|-----------|------------|------------------|--------------------|---------------------------------------|  
|`NULL`|wszystkie|`EINVAL`|Nie zmodyfikowano|Tak|  
|nie `NULL` (wskazuje prawidłowy pamięci)|`NULL`|`EINVAL`|Wszystkie pola ustawioną wartość -1|Tak|  
|nie `NULL` (wskazuje prawidłowy pamięci)|mniejsza niż 0 lub większą niż `_MAX__TIME64_T`|`EINVAL`|Wszystkie pola ustawioną wartość -1|Nie|  
  
 W przypadku pierwszego warunków dwóch błędów, zostanie wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL` i zwracać `EINVAL`.  
  
## <a name="remarks"></a>Uwagi  
 `_localtime32_s` Funkcja konwertuje godzinę przechowywane jako [time_t —](../../c-runtime-library/standard-types.md) wartość i zapisuje wynik w strukturze typu `tm`. `long` Wartość `timer` reprezentuje sekund, jaka upłynęła od północy (00: 00:00), 1 stycznia 1970, UTC. Ta wartość jest zazwyczaj uzyskiwane z `time` funkcji.  
  
 `_localtime32_s` usunięcie strefy czasu lokalnego, jeśli użytkownik najpierw ustawia zmienną środowiskową globalne `TZ`. Gdy `TZ` ustawiono trzy zmienne środowiskowe (`_timezone`, `_daylight`, i `_tzname`) są automatycznie ustawiane również. Jeśli `TZ` zmienna nie jest ustawiona, `localtime32_s` próbuje użyć informacji o strefie czasowej określonej w aplikacji daty/godziny w Panelu sterowania. Jeśli te informacje nie można uzyskać, PST8PDT, co wskazuje na strefę czasową Pacyfiku, jest używany domyślnie. Zobacz [_tzset —](../../c-runtime-library/reference/tzset.md) opis tych zmiennych. `TZ` rozszerzenia Microsoft i nie jest częścią ANSI standardowe definicji `localtime`.  
  
> [!NOTE]
>  Środowisko docelowe należy spróbować ustalić, czy czasu letniego jest włączona.  
  
 `_localtime64_s`, który korzysta z `__time64_t` struktury, umożliwia daty wyrażane w górę do 23:59:59, 18 stycznia 3001, uniwersalny czas koordynowany (UTC), podczas gdy `_localtime32_s` reprezentuje dat za pośrednictwem 23:59:59 18 stycznia 2038 r., UTC.  
  
 `localtime_s` jest wbudowaną funkcją, która daje w wyniku `_localtime64_s`, i `time_t` jest odpowiednikiem `__time64_t`. Aby wymusić kompilatora, aby zinterpretować `time_t` jako starego 32-bitowych `time_t`, można zdefiniować `_USE_32BIT_TIME_T`. To spowoduje `localtime_s` mogła zwrócić `_localtime32_s`. Nie jest to zalecane, ponieważ aplikacja może zakończyć się niepowodzeniem po 18 stycznia 2038 r., a nie jest dozwolona na platformach 64-bitowych.  
  
 Pola typu struktury [tm](../../c-runtime-library/standard-types.md) przechowywać następujące wartości, z których każdy jest `int`.  
  
 `tm_sec`  
 Sekund po minucie (0 - 59).  
  
 `tm_min`  
 Minut po godziny (0 - 59).  
  
 `tm_hour`  
 Godziny po północy (0 - 23).  
  
 `tm_mday`  
 Dzień miesiąca (1-31).  
  
 `tm_mon`  
 Miesiąc (0 - 11; Stycznia = 0).  
  
 `tm_year`  
 Rok (bieżącego roku minus 1900).  
  
 `tm_wday`  
 Dzień tygodnia (0 – 6; Niedziela = 0).  
  
 `tm_yday`  
 Dzień roku (0 - 365; 1 stycznia = 0).  
  
 `tm_isdst`  
 Wartość dodatnią, jeśli czas letni są włączone; 0, jeśli czas letni nie jest włączone; wartość ujemna, jeśli stan okresu obowiązywania czasu letniego jest nieznany. Jeśli `TZ` ustawiono zmiennej środowiskowej, biblioteki wykonawczej języka C przyjmie zasady właściwe dla Stanów Zjednoczonych wykonywania obliczenia czasu (DST).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`localtime_s`|\<time.h>|  
|`_localtime32_s`|\<time.h>|  
|`_localtime64_s`|\<time.h>|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_localtime_s.c  
/* This program uses _time64 to get the current time   
 * and then uses _localtime64_s() to convert this time to a structure   
 * representing the local time. The program converts the result   
 * from a 24-hour clock to a 12-hour clock and determines the   
 * proper extension (AM or PM).  
 */  
  
#include <stdio.h>  
#include <string.h>  
#include <time.h>  
  
int main( void )  
{  
        struct tm newtime;  
        char am_pm[] = "AM";  
        __time64_t long_time;  
        char timebuf[26];  
        errno_t err;  
  
        // Get time as 64-bit integer.  
        _time64( &long_time );   
        // Convert to local time.  
        err = _localtime64_s( &newtime, &long_time );   
        if (err)  
        {  
            printf("Invalid argument to _localtime64_s.");  
            exit(1);  
        }  
        if( newtime.tm_hour > 12 )        // Set up extension.   
                strcpy_s( am_pm, sizeof(am_pm), "PM" );  
        if( newtime.tm_hour > 12 )        // Convert from 24-hour   
                newtime.tm_hour -= 12;    // to 12-hour clock.   
        if( newtime.tm_hour == 0 )        // Set hour to 12 if midnight.  
                newtime.tm_hour = 12;  
  
        // Convert to an ASCII representation.   
        err = asctime_s(timebuf, 26, &newtime);  
        if (err)  
        {  
           printf("Invalid argument to asctime_s.");  
           exit(1);  
        }  
        printf( "%.19s %s\n", timebuf, am_pm );  
}  
```  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
Fri Apr 25 01:19:27 PM  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie czasem](../../c-runtime-library/time-management.md)   
 [asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [czas lokalny, _localtime32 —, _localtime64 —](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)
