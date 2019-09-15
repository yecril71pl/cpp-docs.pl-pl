---
title: mktime, _mktime32, _mktime64
ms.date: 11/04/2016
api_name:
- _mktime32
- mktime
- _mktime64
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
- mktime
- _mktime64
helpviewer_keywords:
- _mktime32 function
- mktime function
- time functions
- mktime64 function
- converting times
- mktime32 function
- _mktime64 function
- time, converting
ms.assetid: 284ed5d4-7064-48a2-bd50-15effdae32cf
ms.openlocfilehash: a282e9f27a0e8f2a91219facda96a5929d3982ea
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951523"
---
# <a name="mktime-_mktime32-_mktime64"></a>mktime, _mktime32, _mktime64

Przekonwertuj czas lokalny na wartość kalendarza.

## <a name="syntax"></a>Składnia

```C
time_t mktime(
   struct tm *timeptr
);
__time32_t _mktime32(
   struct tm *timeptr
);
__time64_t _mktime64(
   struct tm *timeptr
);
```

### <a name="parameters"></a>Parametry

*timeptr*<br/>
Wskaźnik na strukturę czasową; Zobacz [asctime](asctime-wasctime.md).

## <a name="return-value"></a>Wartość zwracana

**_mktime32** zwraca określony czas kalendarza zakodowany jako wartość typu [time_t](../../c-runtime-library/standard-types.md). Jeśli *timeptr* odwołuje się do daty sprzed północy, 1 stycznia 1970 lub jeśli czas kalendarza nie może być reprezentowany, **_mktime32** zwraca-1 rzutowanie do typu **time_t**. W przypadku korzystania z **_mktime32** i jeśli *timeptr* odwołuje się do daty po 23:59:59 stycznia 18, 2038, uniwersalnym czasie koordynowanym (UTC), zwróci-1 rzutowanie na typ **time_t**.

**_mktime64** zwróci wartość-1 rzutowanie na typ **__time64_t** , jeśli *timeptr* odwołuje się do daty 23:59:59, 31 grudnia 3000, UTC.

## <a name="remarks"></a>Uwagi

Funkcje **mktime**, **_mktime32** i **_mktime64** konwertują określoną strukturę czasową (prawdopodobnie niekompletną) wskazywaną przez *timeptr* w w pełni zdefiniowaną strukturę z znormalizowanymi wartościami, a następnie konwertuje ją na **time_t** wartość czasu kalendarza. Konwertowany czas ma takie samo kodowanie jak wartości zwracane przez funkcję [Time](time-time32-time64.md) . Oryginalne wartości składników **tm_wday** i **tm_yday** struktury *timeptr* są ignorowane, a oryginalne wartości innych składników nie są ograniczone do ich normalnych zakresów.

**mktime** to wbudowana funkcja, która jest równoważna z **_mktime64**, chyba że **_USE_32BIT_TIME_T** jest zdefiniowany, w takim przypadku jest równoważne **_mktime32**.

Po dostosowaniu do czasu UTC **_mktime32** obsługuje daty z północy, od 1 stycznia 1970 do 23:59:59 stycznia 18, 2038, UTC. **_mktime64** obsługuje daty z północy, 1 stycznia 1970 do 23:59:59, 31 grudnia 3000. Ta korekta może spowodować, że te funkcje zwracają wartość-1 (rzutowanie do **time_t**, **__time32_t** lub **__time64_t**), nawet jeśli określona data znajduje się w zakresie. Na przykład, jeśli używasz programu Kair, Egipt, który jest dwie godziny przed czasem UTC, dwie godziny zostaną najpierw odjęte od daty określonej w *timeptr*; to może teraz spowodować, że data jest poza zakresem.

Te funkcje mogą służyć do sprawdzania poprawności i wypełnienia struktury TM. Jeśli to się powiedzie, te funkcje ustawiają wartości **tm_wday** i **tm_yday** odpowiednio i ustawiają inne składniki do reprezentowania określonego czasu kalendarzowego, ale z ich wartościami wymuszonymi do normalnych zakresów. Końcowa wartość **tm_mday** nie jest ustawiona do momentu określenia wartości **tm_mon** i **tm_year** . Podczas określania czasu struktury **TM** ustaw wartość pola **tm_isdst** na:

- Zero (0), aby wskazać, że obowiązuje czas standardowy.

- Wartość większa od 0 wskazuje, że obowiązuje czas letni.

- Wartość mniejsza od zera, aby można było obliczyć kod biblioteki wykonawczej C, niezależnie od tego, czy obowiązuje czas standardowy czy czas letni.

Biblioteka środowiska uruchomieniowego C określi zachowanie czasu letniego [ze zmiennej](tzset.md) środowiskowej $. Jeśli **nie ustawiono opcji** /$, Win32 API wywołanie [GetTimeZoneInformation](/windows/win32/api/timezoneapi/nf-timezoneapi-gettimezoneinformation) służy do uzyskiwania informacji o czasie letnim z systemu operacyjnego. Jeśli to się nie powiedzie, biblioteka zakłada, że używane są reguły Stany Zjednoczone w celu wykonania obliczeń czasu letniego. **tm_isdst** jest polem wymaganym. Jeśli nie zostanie ustawiona, jego wartość jest niezdefiniowana i wartość zwracana z tych funkcji jest nieprzewidywalne. Jeśli *timeptr* wskazuje strukturę **TM** zwróconą przez poprzednie wywołanie do [asctime](asctime-wasctime.md), [gmtime](gmtime-gmtime32-gmtime64.md)lub [localtime](localtime-localtime32-localtime64.md) (lub warianty tych funkcji), pole **tm_isdst** zawiera poprawną wartość.

Należy zauważyć, że **gmtime** i **localtime** (oraz **_gmtime32**, **_gmtime64**, **_localtime32**i **_localtime64**) używają jednego buforu dla każdej wątku dla konwersji. Jeśli podasz ten bufor do **mktime**, **_mktime32** lub **_mktime64**, poprzednia zawartość zostanie zniszczona.

Te funkcje sprawdzają poprawność parametru. Jeśli *timeptr* jest pustym wskaźnikiem, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcje zwracają wartość-1 i ustawiają **errno** na **EINVAL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mktime**|\<time.h>|
|**_mktime32**|\<time.h>|
|**_mktime64**|\<time.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_mktime.c
/* The example takes a number of days
* as input and returns the time, the current
* date, and the specified number of days.
*/

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm  when;
   __time64_t now, result;
   int        days;
   char       buff[80];

   time( &now );
   _localtime64_s( &when, &now );
   asctime_s( buff, sizeof(buff), &when );
   printf( "Current time is %s\n", buff );
   days = 20;
   when.tm_mday = when.tm_mday + days;
   if( (result = mktime( &when )) != (time_t)-1 ) {
      asctime_s( buff, sizeof(buff), &when );
      printf( "In %d days the time will be %s\n", days, buff );
   } else
      perror( "mktime failed" );
}
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
Current time is Fri Apr 25 13:34:07 2003

In 20 days the time will be Thu May 15 13:34:07 2003
```

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
