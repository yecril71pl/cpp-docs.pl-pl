---
title: localtime, _localtime32, _localtime64
ms.date: 4/2/2020
api_name:
- _localtime64
- _localtime32
- localtime
- _o__localtime32
- _o__localtime64
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- localtime64
- _localtime64
- localtime32
- localtime
- _localtime32
helpviewer_keywords:
- localtime32 function
- _localtime32 function
- _localtime64 function
- localtime64 function
- localtime function
- time, converting values
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
ms.openlocfilehash: 764a3768610d97df2eb3af4ed0425065aba4b4fa
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916421"
---
# <a name="localtime-_localtime32-_localtime64"></a>localtime, _localtime32, _localtime64

Konwertuje wartość czasu i koryguje dla lokalnej strefy czasowej. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md).

## <a name="syntax"></a>Składnia

```C
struct tm *localtime( const time_t *sourceTime );
struct tm *_localtime32( const __time32_t *sourceTime );
struct tm *_localtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parametry

*sourceTime*<br/>
Wskaźnik na czas przechowywania.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do wyniku struktury lub **wartość null** , jeśli data przekazywania do funkcji to:

- Przed północy, 1 stycznia 1970.

- Po 03:14:07 stycznia, 2038, UTC (przy użyciu **_time32** i **time32_t**).

- Po 23:59:59, 31 grudnia 3000, UTC (przy użyciu **_time64** i **__time64_t**).

**_localtime64**, która korzysta ze struktury **__time64_t** , umożliwia określenie dat do 23:59:59, 31 grudnia 3000, uniwersalny czas koordynowany (UTC), a **_localtime32** reprezentuje daty do 23:59:59 18 stycznia, 2038, UTC.

**localtime** to wbudowana funkcja, która oblicza **_localtime64**, a **time_t** jest równoważna **__time64_t**. Jeśli trzeba wymusić, aby kompilator interpretował **time_t** jako stary **time_t**32-bitowy, można zdefiniować **_USE_32BIT_TIME_T**. To spowoduje, że **localtime** będzie obliczać **_localtime32**. Nie jest to zalecane, ponieważ aplikacja może zakończyć się niepowodzeniem po 18 stycznia 2038 i nie jest dozwolona na platformach 64-bitowych.

Pola typu struktury [TM](../../c-runtime-library/standard-types.md) przechowują następujące wartości, z których każdy **jest liczbą całkowitą**:

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

Jeśli zmienna **środowiskowa** $ jest ustawiona, Biblioteka wykonawcza C przyjmuje reguły odpowiednie dla Stany Zjednoczone w celu wykonania obliczeń czasu letniego (DST).

## <a name="remarks"></a>Uwagi

Funkcja **localtime** konwertuje czas przechowywania jako wartość [time_t](../../c-runtime-library/standard-types.md) i zapisuje wynik w strukturze typu [TM](../../c-runtime-library/standard-types.md). Wartość **Long** *sourceTime* reprezentuje sekundy, które upłynęły od północy (00:00:00), 1 stycznia 1970, UTC. Ta wartość jest zazwyczaj uzyskiwana z funkcji [Time](time-time32-time64.md) .

Zarówno 32-bitowe, jak i 64-bitowe wersje [gmtime](gmtime-gmtime32-gmtime64.md), [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)i **localtime** używają pojedynczej struktury **TM** dla każdej wątku dla konwersji. Każde wywołanie jednej z tych procedur niszczy wynik poprzedniego wywołania.

**localtime** jest poprawna dla lokalnej strefy czasowej, jeśli użytkownik najpierw ustawi globalną **zmienną**środowiskową. Gdy **jest ustawiona wartość opcji** $, trzy inne zmienne środowiskowe (**_timezone**, **_daylight**i **_tzname**) również są ustawiane automatycznie. Jeśli zmienna **$** nie jest ustawiona, **localtime** próbuje użyć informacji o strefie czasowej określonych w aplikacji Data/godzina w panelu sterowania. Jeśli te informacje nie zostaną uzyskane, PST8PDT, który oznacza strefę czasową pacyficznego, jest używany domyślnie. Aby uzyskać opis tych zmiennych, zobacz [_tzset](tzset.md) . $ **To rozszerzenie** firmy Microsoft, a nie część standardowej definicji ANSI **localtime**.

> [!NOTE]
> Środowisko docelowe powinno próbować określić, czy obowiązuje czas letni.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *sourceTime* jest wskaźnikiem typu null lub jeśli wartość *sourceTime* jest ujemna, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcje zwracają **wartość null** i ustawiają **errno** na **EINVAL**.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek C|Wymagany nagłówek C++|
|-------------|---------------------|-|
|**localtime**, **_localtime32**, **_localtime64**|\<> godziny. h|\<CTime> lub \<Time. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_localtime.cpp
// compile with: /W3
// This program uses _time64 to get the current time
// and then uses localtime64() to convert this time to a structure
// representing the local time. The program converts the result
// from a 24-hour clock to a 12-hour clock and determines the
// proper extension (AM or PM).

#include <stdio.h>
#include <string.h>
#include <time.h>

int main( void )
{
    struct tm *newtime;
    char am_pm[] = "AM";
    __time64_t long_time;

    _time64( &long_time );             // Get time as 64-bit integer.
                                       // Convert to local time.
    newtime = _localtime64( &long_time ); // C4996
    // Note: _localtime64 deprecated; consider _localetime64_s

    if( newtime->tm_hour > 12 )        // Set up extension.
        strcpy_s( am_pm, sizeof(am_pm), "PM" );
    if( newtime->tm_hour > 12 )        // Convert from 24-hour
        newtime->tm_hour -= 12;        //   to 12-hour clock.
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

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
