---
title: "czas lokalny, _localtime32 —, _localtime64 — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _localtime64
- _localtime32
- localtime
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
- localtime64
- _localtime64
- localtime32
- localtime
- _localtime32
dev_langs:
- C++
helpviewer_keywords:
- localtime32 function
- _localtime32 function
- _localtime64 function
- localtime64 function
- localtime function
- time, converting values
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1fa4d1b9c0f33df5f172500195edd4f50321d4e5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="localtime-localtime32-localtime64"></a>localtime, _localtime32, _localtime64
Konwertuj na godzinę i popraw na podstawie lokalnej strefy czasowej. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [localtime_s —, _localtime32_s —, _localtime64_s —](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
struct tm *localtime(  
   const time_t *timer   
);  
struct tm *_localtime32(  
   const __time32_t *timer  
);  
struct tm *_localtime64(  
   const __time64_t *timer   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `timer`  
 Wskaźnik do czasu przechowywane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do wyniku struktury lub `NULL` jeśli daty przekazany do funkcji jest:  
  
-   Przed północy, 1 stycznia 1970.  
  
-   Po 03:14:07, 19 stycznia 2038 r., UTC (przy użyciu `_time32` i `time32_t`).  
  
-   Po 23:59:59 31 grudnia 3000 UTC (przy użyciu `_time64` i `__time64_t`).  
  
 `_localtime64`, który korzysta z `__time64_t` struktury, umożliwia daty wyrażane się za pośrednictwem 23:59:59 31 grudnia 3000 uniwersalny czas koordynowany (UTC), podczas gdy `_localtime32` reprezentuje dat za pośrednictwem 23:59:59 18 stycznia 2038 r., UTC.  
  
 `localtime` jest wbudowaną funkcją, która daje w wyniku `_localtime64`, i `time_t` jest odpowiednikiem `__time64_t`. Aby wymusić kompilatora, aby zinterpretować `time_t` jako starego 32-bitowych `time_t`, można zdefiniować `_USE_32BIT_TIME_T`. To spowoduje `localtime` mogła zwrócić `_localtime32`. Nie jest to zalecane, ponieważ aplikacja może zakończyć się niepowodzeniem po 18 stycznia 2038 r., a nie jest dozwolona na platformach 64-bitowych.  
  
 Pola typu struktury [tm](../../c-runtime-library/standard-types.md) przechowywać następujące wartości, z których każdy jest `int`:  
  
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
 Wartość dodatnią, jeśli czas letni są włączone; 0, jeśli czas letni nie jest włączone; wartość ujemna, jeśli stan okresu obowiązywania czasu letniego jest nieznany. Jeśli `TZ` ustawiono zmiennej środowiskowej, biblioteki wykonawczej języka C przyjmie zasady właściwe dla Stanów Zjednoczonych wykonywania obliczenia — czasu (DST).  
  
## <a name="remarks"></a>Uwagi  
 `localtime` Funkcja konwertuje godzinę przechowywane jako [time_t —](../../c-runtime-library/standard-types.md) wartość i zapisuje wynik w strukturze typu `tm`. `long` Wartość `timer` reprezentuje sekund, jaka upłynęła od północy (00: 00:00), 1 stycznia 1970, UTC. Ta wartość jest zazwyczaj uzyskiwane z `time` funkcji.  
  
 Zarówno 32-bitowe i 64-bitowe wersje `gmtime`, `mktime`, `mkgmtime`, i `localtime` używają pojedynczy `tm` struktury na wątek przy konwersji. Każde wywołanie do jednej z tych procedur niszczy wynik poprzedniego wywołania.  
  
 `localtime` usunięcie strefy czasu lokalnego, jeśli użytkownik najpierw ustawia zmienną środowiskową globalne `TZ`. Gdy `TZ` ustawiono trzy zmienne środowiskowe (`_timezone`, `_daylight`, i `_tzname`) są automatycznie ustawiane również. Jeśli `TZ` zmienna nie jest ustawiona, `localtime` próbuje użyć informacji o strefie czasowej określonej w aplikacji daty/godziny w Panelu sterowania. Jeśli te informacje nie można uzyskać, PST8PDT, co wskazuje na strefę czasową Pacyfiku, jest używany domyślnie. Zobacz [_tzset —](../../c-runtime-library/reference/tzset.md) opis tych zmiennych. `TZ` rozszerzenia Microsoft i nie jest częścią ANSI standardowe definicji `localtime`.  
  
> [!NOTE]
>  Środowisko docelowe należy spróbować ustalić, czy czasu letniego jest włączona.  
  
 Te funkcje walidację ich parametrów. Jeśli `timer` jest wskaźnika o wartości null, lub jeśli wartość czasomierza jest ujemna, te funkcje wywołanie program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcje zwracają `NULL` i ustaw `errno` do `EINVAL`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`localtime`|\<time.h>|  
|`_localtime32`|\<time.h>|  
|`_localtime64`|\<time.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_localtime.cpp  
// compile with: /W3  
/* This program uses _time64 to get the current time   
 * and then uses localtime64() to convert this time to a structure   
 * representing the local time. The program converts the result   
 * from a 24-hour clock to a 12-hour clock and determines the   
 * proper extension (AM or PM).  
 */  
  
#include <stdio.h>  
#include <string.h>  
#include <time.h>  
  
int main( void )  
{  
        struct tm *newtime;  
        char am_pm[] = "AM";  
        __time64_t long_time;  
  
        _time64( &long_time );           // Get time as 64-bit integer.  
                                         // Convert to local time.  
        newtime = _localtime64( &long_time ); // C4996  
        // Note: _localtime64 deprecated; consider _localetime64_s  
  
        if( newtime->tm_hour > 12 )        // Set up extension.  
                strcpy_s( am_pm, sizeof(am_pm), "PM" );  
        if( newtime->tm_hour > 12 )        // Convert from 24-hour  
                newtime->tm_hour -= 12;    //   to 12-hour clock.  
        if( newtime->tm_hour == 0 )        // Set hour to 12 if midnight.  
                newtime->tm_hour = 12;  
  
        char buff[30];  
        asctime_s( buff, sizeof(buff), newtime );  
        printf( "%.19s %s\n", buff, am_pm );  
}  
```  
  
```Output  
Tue Feb 12 10:05:58 AM  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie czasem](../../c-runtime-library/time-management.md)   
 [asctime —, _wasctime —](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime_s —, _localtime32_s —, _localtime64_s —](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)