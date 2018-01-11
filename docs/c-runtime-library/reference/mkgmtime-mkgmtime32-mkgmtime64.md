---
title: "_mkgmtime —, _mkgmtime32 —, _mkgmtime64 — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mkgmtime32
- _mkgmtime64
- _mkgmtime
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
- _mkgmtime64
- mkgmtime32
- _mkgmtime32
- mkgmtime
- mkgmtime64
- _mkgmtime
dev_langs: C++
helpviewer_keywords:
- mkgmtime32 function
- time functions
- mkgmtime function
- _mkgmtime function
- converting times
- mkgmtime64 function
- _mkgmtime64 function
- _mkgmtime32 function
- time, converting
ms.assetid: b4ca2b67-e198-4f43-b3e2-e8ad6bd01867
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f99e367d263d3ba49837b269fd04159a70cf549
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mkgmtime-mkgmtime32-mkgmtime64"></a>_mkgmtime, _mkgmtime32, _mkgmtime64
Konwertuje godzinę UTC reprezentowany przez `tm struct` czas UTC reprezentowany przez `time_t` typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      time_t _mkgmtime(  
   struct tm* timeptr  
);  
__time32_t _mkgmtime32(  
   struct tm* timeptr  
);  
__time64_t _mkgmtime64(  
   struct tm* timeptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `timeptr`  
 Wskaźnik do czasu UTC jako `struct tm` do przekonwertowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Liczba typu `__time32_t` lub `__time64_t` reprezentującą liczbę sekund, jaka upłynęła od północy, 1 stycznia 1970, uniwersalny czas koordynowany (UTC). Jeśli data jest poza zakresem (zobacz sekcję uwag) lub danych wejściowych nie może być interpretowane jako prawidłową godzinę, wartość zwracana jest wartość -1.  
  
## <a name="remarks"></a>Uwagi  
 `_mkgmtime32` i `_mkgmtime64` funkcji Konwertuje czas UTC `__time32_t` lub `__time64_t` typu reprezentującą godzinę w formacie UTC. Aby przekonwertować czasu lokalnego do czasu UTC, użyj `mktime`, `_mktime32`, i `_mktime64` zamiast tego.  
  
 `_mkgmtime`jest wbudowaną funkcją, która daje w wyniku `_mkgmtime64`, i `time_t` jest odpowiednikiem `__time64_t`. Aby wymusić kompilatora, aby zinterpretować `time_t` jako starego 32-bitowych `time_t`, można zdefiniować `_USE_32BIT_TIME_T`. Nie jest to zalecane, ponieważ aplikacja może zakończyć się niepowodzeniem po 18 stycznia 2038 (maksymalną wielkość zakresu 32-bitowa `time_t`), i jest niedozwolona w ogóle na platformach 64-bitowych.  
  
 Czas struktury przekazano zostanie zmieniona, w taki sam sposób jak zostały zmienione z `_mktime` funkcji: `tm_wday` i `tm_yday` pola są ustawione na nowe wartości na podstawie wartości z `tm_mday` i `tm_year`. Podczas określania `tm` struktury czasu, należy ustawić `tm_isdst` pole do:  
  
-   Zero (0), aby wskazać (czas standardowy) jest włączona.  
  
-   Wartość większą niż 0, aby wskazać czasu letniego jest włączona.  
  
-   Wartość mniejszą niż zero, aby kod biblioteki wykonawczej języka C obliczeniowe, czy (czas standardowy) lub czas letni jest włączona.  
  
 Biblioteki wykonawcze języka C używa zmiennej środowiskowej TZ w celu określenia czasu letniego poprawne. Jeśli TZ nie jest ustawiona, system operacyjny jest poddawany kwerendzie uzyskać poprawny letniego regionalnych zachowania w czasie. `tm_isdst`pole jest wymagane. Jeśli nie jest ustawiona, jej wartości są niezdefiniowane i wartość zwrotną z elementu `mktime` będzie nieprzewidywalny.  
  
 Zakres `_mkgmtime32` funkcji jest od północy, 1 stycznia 1970 UTC do 23:59:59 18 stycznia 2038 r., UTC. Zakres `_mkgmtime64` się od północy, 1 stycznia 1970 UTC na 23:59:59 31 grudnia 3000 UTC. Zwracana wartość -1 powoduje Data out-of-range. Zakres `_mkgmtime` zależy od tego, czy `_USE_32BIT_TIME_T` jest zdefiniowany. Jeśli nie zdefiniowano (ustawienie domyślne) zakres jest `_mkgmtime64`; w przeciwnym razie zakres jest ograniczona do zakresu 32-bitowych `_mkgmtime32`.  
  
 Należy pamiętać, że `gmtime` i `localtime` do konwersji użyj pojedynczego statycznie przydzielonego buforu. Jeśli podasz tego buforu do `mkgmtime`, poprzednia zawartość zostaną zniszczone.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_mkgmtime.c  
#include <stdio.h>  
#include <time.h>  
  
int main()  
{  
    struct tm t1, t2;  
    time_t now, mytime, gmtime;  
    char buff[30];  
  
    time( & now );  
  
    _localtime64_s( &t1, &now );  
    _gmtime64_s( &t2, &now );  
  
    mytime = mktime(&t1);  
    gmtime = _mkgmtime(&t2);  
  
    printf("Seconds since midnight, January 1, 1970\n");  
    printf("My time: %I64d\nGM time (UTC): %I64d\n\n", mytime, gmtime);  
  
    /* Use asctime_s to display these times. */  
  
    _localtime64_s( &t1, &mytime );  
    asctime_s( buff, sizeof(buff), &t1 );  
    printf( "Local Time: %s\n", buff );  
  
    _gmtime64_s( &t2, &gmtime );  
    asctime_s( buff, sizeof(buff), &t2 );  
    printf( "Greenwich Mean Time: %s\n", buff );  
  
}  
```  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
Seconds since midnight, January 1, 1970  
My time: 1171588492  
GM time (UTC): 1171588492  
  
Local Time: Thu Feb 15 17:14:52 2007  
  
Greenwich Mean Time: Fri Feb 16 01:14:52 2007  
```  
  
 W poniższym przykładzie pokazano, jak niekompletne struktury jest wypełniane przy obliczanej wartości dzień tygodnia i dzień roku.  
  
```  
// crt_mkgmtime2.c  
#include <stdio.h>  
#include <time.h>  
#include <memory.h>  
  
int main()  
{  
    struct tm t1, t2;  
    time_t gmtime;  
    char buff[30];  
  
    memset(&t1, 0, sizeof(struct tm));  
    memset(&t2, 0, sizeof(struct tm));  
  
    t1.tm_mon = 1;  
    t1.tm_isdst = 0;  
    t1.tm_year = 103;  
    t1.tm_mday = 12;  
  
    // The day of the week and year will be incorrect in the output here.  
    asctime_s( buff, sizeof(buff), &t1);  
    printf("Before calling _mkgmtime, t1 = %s t.tm_yday = %d\n",  
            buff, t1.tm_yday );  
  
    gmtime = _mkgmtime(&t1);  
  
    // The correct day of the week and year were determined.  
    asctime_s( buff, sizeof(buff), &t1);  
    printf("After calling _mkgmtime, t1 = %s t.tm_yday = %d\n",  
            buff, t1.tm_yday );  
  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003  
 t.tm_yday = 0  
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003  
 t.tm_yday = 42  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie czasem](../../c-runtime-library/time-management.md)   
 [asctime —, _wasctime —](../../c-runtime-library/reference/asctime-wasctime.md)   
 [asctime_s —, _wasctime_s —](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [gmtime —, _gmtime32 —, _gmtime64 —](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [gmtime_s —, _gmtime32_s —, _gmtime64_s —](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s —, _localtime32_s —, _localtime64_s —](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime —, _mktime32 —, _mktime64 —](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)