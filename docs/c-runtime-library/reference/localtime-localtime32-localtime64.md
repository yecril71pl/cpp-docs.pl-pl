---
title: localtime, _localtime32, _localtime64
ms.date: 11/04/2016
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
helpviewer_keywords:
- localtime32 function
- _localtime32 function
- _localtime64 function
- localtime64 function
- localtime function
- time, converting values
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
ms.openlocfilehash: d34a45ff20cb74d61a8eb189282bfdce4d8954ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629973"
---
# <a name="localtime-localtime32-localtime64"></a>localtime, _localtime32, _localtime64

Konwertuje wartość czasu i koryguje dla lokalnej strefy czasowej. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [localtime_s —, _localtime32_s —, _localtime64_s —](localtime-s-localtime32-s-localtime64-s.md).

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

Zwraca wskaźnik do wyniku struktury lub **NULL** Jeśli data przekazany do funkcji jest:

- Wcześniejszą niż północ 1 stycznia 1970.

- Po 03:14:07, 19 stycznia 2038 r. UTC (przy użyciu **_time32 —** i **time32_t**).

- Po 23:59:59, 31 grudnia 3000, czasu UTC (przy użyciu **_time64** i **__time64_t —**).

**_localtime64**, który używa **__time64_t —** strukturę oraz umożliwia daty do za pośrednictwem 23:59:59, 31 grudnia 3000, uniwersalny czas koordynowany (UTC), natomiast **_localtime32** reprezentuje daty do 23:59:59 18 stycznia 2038 r. UTC.

**localtime** jest funkcją śródwierszową, co jest ewaluowane jako **_localtime64**, i **time_t** jest odpowiednikiem **__time64_t —**. Jeśli chcesz wymusić na kompilatorze interpretowanie **time_t** jako stary 32-bitowy **time_t**, można zdefiniować **_USE_32BIT_TIME_T**. Takie działanie spowoduje **localtime** na **_localtime32**. Nie jest to zalecane, ponieważ aplikacja może przestać działać po 18 stycznia 2038 r. i nie jest dozwolone na platformach 64-bitowych.

Pola typu struktury [tm](../../c-runtime-library/standard-types.md) przechowywać następujące wartości, z których każdy jest **int**:

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

Jeśli **TZ** zmienna środowiskowa jest ustawiona, biblioteka środowiska uruchomieniowego języka C przyjmie reguły odpowiednie do Stanów Zjednoczonych obliczeń czasu letniego (DST).

## <a name="remarks"></a>Uwagi

**Localtime** funkcja konwertuje czas przechowywane jako [time_t](../../c-runtime-library/standard-types.md) wartości i zapisuje wynik w postaci struktury typu [tm](../../c-runtime-library/standard-types.md). **Długie** wartość *sourceTime* reprezentuje sekund, które upłynęły od północy (00: 00:00), 1 stycznia 1970 r., UTC. Ta wartość jest zazwyczaj uzyskiwane z [czasu](time-time32-time64.md) funkcji.

Zarówno 32-bitowych i 64-bitowe wersje [gmtime](gmtime-gmtime32-gmtime64.md), [mktime](mktime-mktime32-mktime64.md), [mkgmtime —](mkgmtime-mkgmtime32-mkgmtime64.md), i **localtime** wszystkie używane pojedyncze **tm** struktury na wątek dla konwersji. Każde wywołanie jednej z tych procedur niszczy wynik poprzedniego wywołania.

**localtime** poprawia dla lokalnej strefy czasowej, gdy użytkownik najpierw ustawia zmienną środowiskową globalnego **TZ**. Gdy **TZ** jest ustawiona, trzy inne zmienne środowiskowe (**_timezone**, **_daylight**, i **_tzname**) również są automatycznie ustawiane. Jeśli **TZ** zmienna nie jest ustawiona, **localtime** próbuje użyć informacji o strefie czasowej, określone w aplikacji Data/Godzina w Panelu sterowania. Jeśli nie można uzyskać te informacje, PST8PDT, co oznacza strefy czasu pacyficznego, jest używany domyślnie. Zobacz [_tzset —](tzset.md) opis tych zmiennych. **TZ** rozszerzeń firmy Microsoft i nie jest częścią definicji standard ANSI z **localtime**.

> [!NOTE]
> Aby ustalić, czy czas letni obowiązuje starać środowiska docelowego.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *sourceTime* jest wskaźnikiem typu null, lub jeśli *sourceTime* wartość jest ujemna, te wywołają procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, te funkcje zwracają **NULL** i ustaw **errno** do **EINVAL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek języka C|Wymagany nagłówek C++|
|-------------|---------------------|-|
|**localtime**, **_localtime32**, **_localtime64**|\<time.h>|\<ctime — > lub \<time.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
