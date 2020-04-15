---
title: localtime_s, _localtime32_s, _localtime64_s
ms.date: 4/2/2020
api_name:
- _localtime64_s
- _localtime32_s
- localtime_s
- _o__localtime32_s
- _o__localtime64_s
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
ms.openlocfilehash: 3c5d194da85eb5d008dfc9cf19f222ebb575747d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342123"
---
# <a name="localtime_s-_localtime32_s-_localtime64_s"></a>localtime_s, _localtime32_s, _localtime64_s

Konwertuje **wartość czasu time_t** na strukturę **tm** i koryguje dla lokalnej strefy czasowej. Są to wersje [czasu lokalnego, _localtime32, _localtime64](localtime-localtime32-localtime64.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w [programie Funkcje zabezpieczeń w programie CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*tmDest ( tmDest )*<br/>
Wskaźnik do struktury czasu, która ma zostać wypełniona.

*źródłoCzas*<br/>
Wskaźnik do zapisanego czasu.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie. Zwracana wartość jest kodem błędu w przypadku wystąpienia błędu. Kody błędów są zdefiniowane w errno.h. Aby uzyskać listę tych błędów, zobacz [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Warunki błędu

|*tmDest ( tmDest )*|*źródłoCzas*|Wartość zwracana|Wartość w *tmDest*|Wywołuje nieprawidłowy program obsługi parametrów|
|-----------|------------|------------------|--------------------|---------------------------------------|
|**Null**|Wszelki|**Einval**|Nie zmodyfikowano|Tak|
|Nie **NULL** (punkty do prawidłowej pamięci)|**Null**|**Einval**|Wszystkie pola ustawione na -1|Tak|
|Nie **NULL** (punkty do prawidłowej pamięci)|mniej niż 0 lub więcej niż **_MAX__TIME64_T**|**Einval**|Wszystkie pola ustawione na -1|Nie|

W przypadku pierwszych dwóch warunków błędu wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w obszarze [Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te funkcje **ustawiają errno** na **EINVAL** i zwracają **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **localtime_s** konwertuje czas przechowywany jako wartość [time_t](../../c-runtime-library/standard-types.md) i przechowuje wynik w strukturze typu [tm](../../c-runtime-library/standard-types.md). **Wartość time_t** *sourceTime* reprezentuje sekundy upłynęło od północy (00:00:00), 1 stycznia 1970, UTC. Ta wartość jest zwykle uzyskiwana z funkcji [czasu.](time-time32-time64.md)

**localtime_s** koryguje dla lokalnej strefy czasowej, jeśli użytkownik najpierw ustawia globalną zmienną środowiskową **TZ**. Po ustawieniu **TZ** automatycznie ustawiane są również trzy inne zmienne środowiskowe (**_timezone**, **_daylight**i **_tzname).** Jeśli zmienna **TZ** nie jest ustawiona, **localtime_s** próbuje użyć informacji o strefie czasowej określonej w aplikacji Data/Godzina w Panelu sterowania. Jeśli nie można uzyskać tych informacji, PST8PDT, który oznacza strefę czasową Pacyfiku, jest używany domyślnie. Opis tych zmiennych [można znaleźć w _tzset.](tzset.md) **TZ** jest rozszerzeniem firmy Microsoft i nie jest częścią standardowej definicji czasu **lokalnego**ANSI.

> [!NOTE]
> Środowisko docelowe należy spróbować ustalić, czy czas letni jest w mocy.

**_localtime64_s**, która wykorzystuje strukturę **__time64_t,** umożliwia wyrażenie dat do 23:59:59, 18 stycznia 3001, skoordynowany czas uniwersalny (UTC), podczas gdy **_localtime32_s** reprezentuje daty do 23:59:59 18 stycznia 2038, UTC.

**localtime_s** jest funkcją wbudowaną, która ocenia **_localtime64_s,** a **time_t** jest odpowiednikiem **__time64_t**. Jeśli konieczne jest wymuszenie, aby kompilator interpretował **time_t** jako stary **time_t**32-bitowy, można zdefiniować **_USE_32BIT_TIME_T**. Spowoduje **to, że localtime_s** oceni **_localtime32_s**. Nie jest to zalecane, ponieważ aplikacja może zakończyć się niepowodzeniem po 18 stycznia 2038 r. i nie jest dozwolona na platformach 64-bitowych.

Pola typu struktury [tm](../../c-runtime-library/standard-types.md) przechowują następujące wartości, z których każda jest **int**.

|Pole|Opis|
|-|-|
|**tm_sec**|Sekundy po minucie (0 - 59).|
|**tm_min**|Minuty po godzinie (0 - 59).|
|**tm_hour**|Godziny od północy (0 - 23).|
|**tm_mday**|Dzień miesiąca (1 - 31).|
|**tm_mon**|Miesiąc (0 - 11; styczeń = 0).|
|**tm_year**|rok (rok bieżący minus 1900).|
|**tm_wday**|Dzień tygodnia (0 - 6; niedziela = 0).|
|**tm_yday**|Dzień roku (0 - 365; 1 stycznia = 0).|
|**tm_isdst**|Wartość dodatnia, jeśli obowiązuje czas letni; 0, jeśli czas letni nie obowiązuje; wartość ujemna, jeśli stan czasu letniego jest nieznany.|

Jeśli ustawiona jest zmienna środowiskowa **TZ,** biblioteka wykonawcza języka C przyjmuje reguły odpowiednie dla Stanów Zjednoczonych do wdrażania obliczania czasu letniego (DST).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek C|Wymagany nagłówek języka C++|
|-------------|---------------------|-|
|**localtime_s** **_localtime32_s** **_localtime64_s**|\<> time.h|\<> czasu lub \<> czasu.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
