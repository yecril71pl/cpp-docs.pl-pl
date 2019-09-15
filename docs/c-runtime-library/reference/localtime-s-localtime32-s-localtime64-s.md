---
title: localtime_s, _localtime32_s, _localtime64_s
ms.date: 07/09/2019
api_name:
- _localtime64_s
- _localtime32_s
- localtime_s
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
ms.openlocfilehash: c00a5d23441612d0e70bfafd571bcb25250edb09
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953335"
---
# <a name="localtime_s-_localtime32_s-_localtime64_s"></a>localtime_s, _localtime32_s, _localtime64_s

Konwertuje wartość czasu **time_t** na strukturę **TM** i koryguje ją dla lokalnej strefy czasowej. Są to wersje [localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md) z zabezpieczeniami, jak opisano w [funkcjach zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Wskaźnik do struktury czasu, która ma zostać wypełniona.

*sourceTime*<br/>
Wskaźnik na czas przechowywania.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli powodzenie. Wartość zwracana jest kodem błędu w przypadku wystąpienia błędu. Kody błędów są zdefiniowane w errno. h. Aby uzyskać listę tych błędów, zobacz [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Warunki błędów

|*tmDest*|*sourceTime*|Wartość zwracana|Wartość w *tmDest*|Wywołuje procedurę obsługi nieprawidłowego parametru|
|-----------|------------|------------------|--------------------|---------------------------------------|
|**NULL**|Ile|**EINVAL**|nie zmodyfikowano|Tak|
|Nie **ma wartości null** (wskazuje na prawidłową pamięć)|**NULL**|**EINVAL**|Wszystkie pola ustawione na wartość-1|Tak|
|Nie **ma wartości null** (wskazuje na prawidłową pamięć)|mniejsze niż 0 lub większe niż **_MAX__TIME64_T**|**EINVAL**|Wszystkie pola ustawione na wartość-1|Nie|

W przypadku pierwszych dwóch warunków błędu procedura obsługi nieprawidłowego parametru jest wywoływana, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EINVAL** i zwracają **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **localtime_s** konwertuje czas przechowywania jako wartość [time_t](../../c-runtime-library/standard-types.md) i zapisuje wynik w strukturze typu [TM](../../c-runtime-library/standard-types.md). Wartość **Time_t** *sourceTime* reprezentuje sekundy, które upłynęły od północy (00:00:00), 1 stycznia 1970, UTC. Ta wartość jest zazwyczaj uzyskiwana z funkcji [Time](time-time32-time64.md) .

**localtime_s** jest poprawna dla lokalnej strefy czasowej, jeśli użytkownik najpierw ustawi globalną **zmienną**środowiskową. W **przypadku ustawienia opcji $ są również** automatycznie ustawiane trzy inne zmienne środowiskowe ( **_timezone**, **_daylight**i **_tzname**). Jeśli zmienna **$** nie jest ustawiona, **localtime_s** próbuje użyć informacji o strefie czasowej określonych w aplikacji Data/godzina w panelu sterowania. Jeśli te informacje nie zostaną uzyskane, PST8PDT, który oznacza strefę czasową pacyficznego, jest używany domyślnie. Zobacz [_tzset](tzset.md) , aby uzyskać opis tych zmiennych. $ **To rozszerzenie** firmy Microsoft, a nie część standardowej definicji ANSI **localtime**.

> [!NOTE]
> Środowisko docelowe powinno próbować określić, czy obowiązuje czas letni.

**_localtime64_s**, który korzysta ze struktury **__time64_t** , umożliwia określenie dat, które mają być wyrażone do 23:59:59, 18 stycznia, 3001, Universal czas koordynowany (UTC), natomiast **_localtime32_s** reprezentuje daty do 23:59:59 18 stycznia, 2038, UTC.

**localtime_s** jest funkcją wbudowaną, która jest obliczana do **_localtime64_s**, a **time_t** jest równoznaczna z **__time64_t**. Jeśli trzeba wymusić, aby kompilator interpretował **time_t** jako stary 32-bitowy **time_t**, można zdefiniować **_USE_32BIT_TIME_T**. Spowoduje to **localtime_s** do **_localtime32_s**. Nie jest to zalecane, ponieważ aplikacja może zakończyć się niepowodzeniem po 18 stycznia 2038 i nie jest dozwolona na platformach 64-bitowych.

Pola typu struktury [TM](../../c-runtime-library/standard-types.md) przechowują następujące wartości, z których każdy **jest liczbą całkowitą**.

|Pole|Opis|
|-|-|
|**tm_sec**|Sekund po minucie (0-59).|
|**tm_min**|Minut po godzinie (0-59).|
|**tm_hour**|Godz. od północy (0-23).|
|**tm_mday**|Dzień miesiąca (1-31).|
|**tm_mon**|Miesiąc (0-11; Styczeń = 0).|
|**tm_year**|Year (bieżący rok minus 1900).|
|**tm_wday**|Dzień tygodnia (0-6; Niedziela = 0).|
|**tm_yday**|Dzień roku (0-365; 1 stycznia = 0).|
|**tm_isdst**|Wartość dodatnia, jeśli obowiązuje zmiana czasu letniego; 0, jeśli czas letni nie jest stosowany; wartość ujemna, jeśli stan czasu letniego jest nieznany.|

Jeśli jest **ustawiona zmienna środowiskowa** $, Biblioteka wykonawcza C przyjmuje reguły odpowiednie dla Stany Zjednoczone w celu wdrożenia obliczeń czasu letniego (DST).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek C|Wymagany C++ nagłówek|
|-------------|---------------------|-|
|**localtime_s**, **_localtime32_s**, **_localtime64_s**|\<time.h>|\<CTime > lub \<Time. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
