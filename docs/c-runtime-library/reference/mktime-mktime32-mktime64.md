---
title: mktime, _mktime32, _mktime64
ms.date: 4/2/2020
api_name:
- _mktime32
- mktime
- _mktime64
- _o__mktime32
- _o__mktime64
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
ms.openlocfilehash: b0981f33d70945083eacd28eb7517e80b3f2539f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338700"
---
# <a name="mktime-_mktime32-_mktime64"></a>mktime, _mktime32, _mktime64

Konwertuj czas lokalny na wartość kalendarza.

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
Wskaźnik do struktury czasu; zobacz [asctime](asctime-wasctime.md).

## <a name="return-value"></a>Wartość zwracana

**_mktime32** zwraca określony czas kalendarza zakodowany jako wartość [typu time_t](../../c-runtime-library/standard-types.md). Jeśli *timeptr* odwołuje się do daty przed północą, 1 stycznia 1970 r. lub jeśli nie można przedstawić czasu kalendarzowego, **_mktime32** zwraca rzut -1, aby wpisać **time_t**. W przypadku korzystania **z _mktime32** i jeśli *timeptr* odwołuje się do daty po 23:59:59 18 stycznia 2038, Skoordynowany czas uniwersalny (UTC), zwróci -1 oddanych do typu **time_t**.

**_mktime64** zwróci rzut -1, aby wpisać **__time64_t** jeśli *timeptr* odwołuje się do daty po 23:59:59, 31 grudnia 3000, UTC.

## <a name="remarks"></a>Uwagi

Funkcje **_mktime32,** **_mktime32** i **_mktime64** przekształcają dostarczoną strukturę czasu (prawdopodobnie niekompletną) wskazywanych przez *timepter* w w pełni zdefiniowaną strukturę z znormalizowanymi wartościami, a następnie konwertuje ją na **time_t** wartość czasu kalendarzowego. Przekonwertowany czas ma takie samo kodowanie jak wartości zwracane przez funkcję [czasu.](time-time32-time64.md) Oryginalne wartości **tm_wday** i **tm_yday** komponentów struktury *timeptra* są ignorowane, a oryginalne wartości innych komponentów nie są ograniczone do ich normalnych zakresów.

**mktime** jest funkcją wbudowaną, która jest równoważna **_mktime64**, chyba że **_USE_32BIT_TIME_T** jest zdefiniowana, w którym to przypadku jest odpowiednikiem **_mktime32**.

Po dostosowaniu do czasu UTC **_mktime32** obsługuje dat od północy, 1 stycznia 1970 r. do 23:59:59 18 stycznia 2038 r., UTC. **_mktime64** obsługuje dat od północy, 1 stycznia 1970 do 23:59:59, 31 grudnia 3000. Ta korekta może spowodować, że te funkcje powrócą do -1 (rzut do **time_t** **, __time32_t** lub **__time64_t),** nawet jeśli określona data mieści się w zakresie. Na przykład, jeśli jesteś w Kairze, Egipt, który jest dwie godziny przed UTC, dwie godziny zostaną najpierw odjęta od daty określonej w *timeptr;* może to teraz umieścić datę poza zasięgiem.

Funkcje te mogą służyć do sprawdzania poprawności i wypełniania struktury tm. Jeśli się powiedzie, te funkcje ustawić wartości **tm_wday** i **tm_yday** odpowiednio i ustawić inne składniki do reprezentowania określonego czasu kalendarza, ale z ich wartości zmuszony do normalnych zakresów. Ostateczna wartość **tm_mday** nie jest ustawiana, dopóki nie zostaną określone **tm_mon** i **tm_year.** Określając czas struktury **tm,** ustaw pole **tm_isdst** na:

- Zero (0), aby wskazać, że obowiązuje czas standardowy.

- Wartość większa niż 0, aby wskazać, że czas letni jest w mocy.

- Wartość mniejsza niż zero, aby kod biblioteki w czasie wykonywania języka C obliczył, czy obowiązuje czas standardowy czy czas letni.

Biblioteka czasu wykonywania języka C określi zachowanie czasu letniego ze zmiennej środowiskowej [TZ.](tzset.md) Jeśli **TZ** nie jest ustawiona, wywołanie interfejsu API Win32 [GetTimeZoneInformation](/windows/win32/api/timezoneapi/nf-timezoneapi-gettimezoneinformation) jest używane do uzyskania informacji o czasie letnim z systemu operacyjnego. Jeśli to się nie powiedzie, biblioteka zakłada, że używane są reguły Stanów Zjednoczonych dotyczące implementowania obliczania czasu letniego. **tm_isdst** jest wymagane pole. Jeśli nie jest ustawiona, jego wartość jest niezdefiniowana, a zwracana wartość z tych funkcji jest nieprzewidywalna. Jeśli *timeptr* wskazuje strukturę **tm** zwróconą przez poprzednie [wywołanie asctime](asctime-wasctime.md), [gmtime](gmtime-gmtime32-gmtime64.md)lub [localtime](localtime-localtime32-localtime64.md) (lub warianty tych funkcji), pole **tm_isdst** zawiera poprawną wartość.

Należy zauważyć, że **czas gmtime** i **czas lokalny** (i **_gmtime32**, **_gmtime64**, **_localtime32**i **_localtime64**) używają jednego bufora na wątek do konwersji. Jeśli ten bufor zostanie podasz **do mktime,** **_mktime32** lub **_mktime64,** poprzednia zawartość zostanie zniszczona.

Te funkcje sprawdzają poprawność ich parametru. Jeśli *timepter* jest wskaźnikiem null, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametru.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, funkcje zwracają -1 i ustawić **errno** na **EINVAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mktime**|\<> time.h|
|**_mktime32**|\<> time.h|
|**_mktime64**|\<> time.h|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
