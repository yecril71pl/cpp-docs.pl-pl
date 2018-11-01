---
title: localtime_s, _localtime32_s, _localtime64_s
ms.date: 11/04/2016
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
helpviewer_keywords:
- _localtime64_s function
- localtime32_s function
- _localtime32_s function
- localtime64_s function
- time, converting values
- localtime_s function
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
ms.openlocfilehash: 44b2eb2515035d56143a2aab251437a92515e652
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492784"
---
# <a name="localtimes-localtime32s-localtime64s"></a>localtime_s, _localtime32_s, _localtime64_s

Konwertuje **time_t** czasu wartość **tm** struktury i usuwa dla lokalnej strefy czasowej. Są to wersje [localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t localtime_s(
   struct tm* const tmDest,
   time_t const* const sourceTime
);
errno_t _localtime32_s(
   struct tm* tmDest,
   __time32_t const* sourceTime
);
errno_t _localtime64_s(
   struct tm* tmDest,
   __time64_t const* sourceTime
);
```

### <a name="parameters"></a>Parametry

*tmDest*<br/>
Wskaźnik do struktury czasu należy wypełnić.

*sourceTime*<br/>
Wskaźnik na czas przechowywania.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie. Wartość zwracana jest kod błędu, jeśli wystąpi awaria. Kody błędów są definiowane w Errno.h. Aby uzyskać listę tych błędów, zobacz [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Warunki błędów

|*tmDest*|*sourceTime*|Wartość zwracana|Wartość w *tmDest*|Wywołuje program obsługi nieprawidłowych parametrów|
|-----------|------------|------------------|--------------------|---------------------------------------|
|**NULL**|Wszystkie|**EINVAL**|Nie zmodyfikowano|Tak|
|Nie **NULL** (wskazuje prawidłowy pamięci)|**NULL**|**EINVAL**|Wszystkie pola ustawione na wartość -1|Tak|
|Nie **NULL** (wskazuje prawidłowy pamięci)|mniejszy niż 0 lub większy niż **_MAX__TIME64_T**|**EINVAL**|Wszystkie pola ustawione na wartość -1|Nie|

W przypadku pierwszego warunków błędów dwóch, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają **EINVAL**.

## <a name="remarks"></a>Uwagi

**_Localtime32_s —** funkcja konwertuje czas przechowywane jako [time_t](../../c-runtime-library/standard-types.md) wartości i zapisuje wynik w postaci struktury typu [tm](../../c-runtime-library/standard-types.md). **Długie** wartość *sourceTime* reprezentuje sekund, które upłynęły od północy (00: 00:00), 1 stycznia 1970 r., UTC. Ta wartość jest zazwyczaj uzyskiwane z [czasu](time-time32-time64.md) funkcji.

**_localtime32_s —** poprawia dla lokalnej strefy czasowej, gdy użytkownik najpierw ustawia zmienną środowiskową globalnego **TZ**. Gdy **TZ** jest ustawiona, trzy inne zmienne środowiskowe (**_timezone**, **_daylight**, i **_tzname**) również są automatycznie ustawiane. Jeśli **TZ** zmienna nie jest ustawiona, **localtime32_s —** próbuje użyć informacji o strefie czasowej, określone w aplikacji Data/Godzina w Panelu sterowania. Jeśli nie można uzyskać te informacje, PST8PDT, co oznacza strefy czasu pacyficznego, jest używany domyślnie. Zobacz [_tzset —](tzset.md) opis tych zmiennych. **TZ** rozszerzeń firmy Microsoft i nie jest częścią definicji standard ANSI z **localtime**.

> [!NOTE]
> Aby ustalić, czy czas letni obowiązuje starać środowiska docelowego.

**_localtime64_s —**, który używa **__time64_t —** strukturę oraz umożliwia daty do do 23:59:59, 18 stycznia 3001, uniwersalny czas koordynowany (UTC), natomiast **_localtime32_s —** reprezentuje daty do 23:59:59 18 stycznia 2038 r. UTC.

**localtime_s —** jest funkcją śródwierszową, co jest ewaluowane jako **_localtime64_s —**, i **time_t** jest odpowiednikiem **__time64_t —**. Jeśli chcesz wymusić na kompilatorze interpretowanie **time_t** jako stary 32-bitowy **time_t**, można zdefiniować **_USE_32BIT_TIME_T**. Takie działanie spowoduje **localtime_s —** na **_localtime32_s —**. Nie jest to zalecane, ponieważ aplikacja może przestać działać po 18 stycznia 2038 r. i nie jest dozwolone na platformach 64-bitowych.

Pola typu struktury [tm](../../c-runtime-library/standard-types.md) przechowywać następujące wartości, z których każdy jest **int**.

|Pole|Opis|
|-|-|
|**tm_sec**|Sekundy po minucie (0 - 59).|
|**tm_min**|Min. po godzinie (0 - 59).|
|**tm_hour**|Godziny od północy (0 - 23).|
|**tm_mday**|Dzień miesiąca (1-31).|
|**tm_mon**|Miesiąc (0 - 11; Styczeń = 0).|
|**tm_year**|Rok (bieżący roku minus 1900).|
|**tm_wday**|Dzień tygodnia (0 – 6; Niedziela = 0).|
|**tm_yday**|Dzień roku (0 – 365; Od 1 stycznia = 0).|
|**tm_isdst**|Wartość dodatnią, jeśli czas letni obowiązuje; 0, jeśli czas letni nie jest włączone; wartość ujemna, jeśli stan czasu jest nieznany.|

Jeśli **TZ** zmienna środowiskowa jest ustawiona, biblioteki wykonawczej C przyjmie reguły odpowiednie do Stanów Zjednoczonych wykonywania obliczeń czasu letniego (DST).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek języka C|Wymagany nagłówek C++|
|-------------|---------------------|-|
|**localtime_s —**, **_localtime32_s —**, **_localtime64_s —**|\<time.h>|\<ctime — > lub \<time.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_localtime_s.c
// This program uses _time64 to get the current time
// and then uses _localtime64_s() to convert this time to a structure
// representing the local time. The program converts the result
// from a 24-hour clock to a 12-hour clock and determines the
// proper extension (AM or PM).

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
        newtime.tm_hour -= 12;        // to 12-hour clock.
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

```Output
Fri Apr 25 01:19:27 PM
```

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
