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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 21496b71c354c7bed7b87526dc40bc9b24865da2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342135"
---
# <a name="localtime-_localtime32-_localtime64"></a>localtime, _localtime32, _localtime64

Konwertuje wartość czasu i koryguje dla lokalnej strefy czasowej. Dostępne są bezpieczniejsze wersje tych funkcji; zobacz [localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md).

## <a name="syntax"></a>Składnia

```C
struct tm *localtime( const time_t *sourceTime );
struct tm *_localtime32( const __time32_t *sourceTime );
struct tm *_localtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parametry

*źródłoCzas*<br/>
Wskaźnik do przechowywanego czasu.

## <a name="return-value"></a>Wartość zwracana

Powrót wskaźnika do wyniku struktury lub **NULL,** jeśli data przekazana do funkcji jest:

- Przed północą, 1 stycznia 1970 roku.

- Po 03:14:07, 19 stycznia 2038, UTC (z wykorzystaniem **_time32** i **time32_t**).

- Po 23:59:59, 31 grudnia 3000, UTC (z wykorzystaniem **_time64** i **__time64_t**).

**_localtime64**, która wykorzystuje strukturę **__time64_t,** umożliwia wyrażenie dat do 23:59:59, 31 grudnia 3000, skoordynowany czas uniwersalny (UTC), podczas gdy **_localtime32** reprezentuje daty do 23:59:59 18 stycznia 2038, UTC.

**localtime** jest funkcją wbudowaną, która ocenia **_localtime64,** a **time_t** jest odpowiednikiem **__time64_t**. Jeśli konieczne jest wymuszenie, aby kompilator interpretował **time_t** jako stary **time_t**32-bitowy, można zdefiniować **_USE_32BIT_TIME_T**. Spowoduje **to,** że czas lokalny oceni **_localtime32**. Nie jest to zalecane, ponieważ aplikacja może zakończyć się niepowodzeniem po 18 stycznia 2038 r. i nie jest dozwolona na platformach 64-bitowych.

Pola typu struktury [tm](../../c-runtime-library/standard-types.md) przechowują następujące wartości, z których każda jest **int:**

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

Jeśli ustawiona jest zmienna środowiskowa **TZ,** biblioteka wykonawcza języka C przyjmuje reguły odpowiednie dla Stanów Zjednoczonych do implementowania obliczania czasu letniego (DST).

## <a name="remarks"></a>Uwagi

Funkcja **localtime** konwertuje czas przechowywany jako wartość [time_t](../../c-runtime-library/standard-types.md) i przechowuje wynik w strukturze typu [tm](../../c-runtime-library/standard-types.md). **Long** value *sourceTime* reprezentuje sekundy upłynęło od północy (00:00:00), 1 stycznia 1970, UTC. Ta wartość jest zwykle uzyskiwana z funkcji [czasu.](time-time32-time64.md)

Zarówno 32-bitowe, jak i 64-bitowe wersje [gmtime](gmtime-gmtime32-gmtime64.md), [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)i **localtime** używają jednej struktury **tm** na wątek do konwersji. Każde wywołanie jednej z tych procedur niszczy wynik poprzedniego wywołania.

**localtime** koryguje dla lokalnej strefy czasowej, jeśli użytkownik najpierw ustawia globalną zmienną środowiskową **TZ**. Po ustawieniu **TZ** automatycznie ustawiane są również trzy inne zmienne środowiskowe (**_timezone**, **_daylight**i **_tzname).** Jeśli zmienna **TZ** nie jest ustawiona, **czas lokalny** próbuje użyć informacji o strefie czasowej określonej w aplikacji Data/Godzina w Panelu sterowania. Jeśli nie można uzyskać tych informacji, PST8PDT, który oznacza pacyficznej strefy czasowej, jest używany domyślnie. Opis tych zmiennych [można znaleźć w _tzset.](tzset.md) **TZ** jest rozszerzeniem firmy Microsoft i nie jest częścią standardowej definicji czasu **lokalnego**ANSI.

> [!NOTE]
> Środowisko docelowe należy spróbować ustalić, czy czas letni jest w mocy.

Te funkcje sprawdzają ich parametry. Jeśli *sourceTime* jest wskaźnikiem null lub jeśli *sourceTime* wartość jest ujemna, te funkcje wywołać nieprawidłowy program obsługi parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, funkcje zwracają **null** i ustawić **errno** do **EINVAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek C|Wymagany nagłówek języka C++|
|-------------|---------------------|-|
|**lokalnie**, **_localtime32**, **_localtime64**|\<> time.h|\<> czasu lub \<> czasu.h|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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
