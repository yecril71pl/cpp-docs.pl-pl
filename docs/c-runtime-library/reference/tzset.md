---
title: _tzset
ms.date: 4/2/2020
api_name:
- _tzset
- _o__tzset
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
- _tzset
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
ms.openlocfilehash: b2537a3bbfd2b5cec6bdf149c520aac7e3344b1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362185"
---
# <a name="_tzset"></a>_tzset

Ustawia zmienne środowiskowe czasu.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
void _tzset( void );
```

## <a name="remarks"></a>Uwagi

Funkcja **_tzset** używa bieżącego ustawienia zmiennej środowiskowej **TZ** do przypisywania wartości do trzech zmiennych globalnych: **_daylight**, **_timezone**i **_tzname**. Zmienne te są używane przez [funkcje _ftime](ftime-ftime32-ftime64.md) i [czasu lokalnego](localtime-localtime32-localtime64.md) do wprowadzania poprawek od skoordynowanego czasu uniwersalnego (UTC) do czasu lokalnego oraz przez funkcję [czasu](time-time32-time64.md) obliczenia czasu UTC z czasu systemowego. Aby ustawić zmienną środowiskową **TZ,** użyj następującej składni:

> **zestaw TZ=**_tzn_ \[ **+**&#124;**-**]*hh*\[**:**_mm_\[**:**_ss_] ][*dzn*]

|Parametr|Opis|
|-|-|
| *tzn* | Trzyliterowa nazwa strefy czasowej, na przykład PST. Należy określić poprawne przesunięcie od czasu lokalnego do czasu UTC. |
| *hh* | Różnica godzin między czasem UTC a czasem lokalnym. Podpisz (+) opcjonalnie dla wartości dodatnich. |
| *Mm* | Minut. Oddzielone od *hh* przez dwukropek (**:**). |
| *Ss* | Sekund. Oddzielony od *mm* dwukropkiem (**:**). |
| *dzn* | Trzyliterowa strefa czasu letniego, taka jak PDT. Jeśli czas letni nigdy nie obowiązuje w miejscowości, ustaw **TZ** bez wartości *dla dzn*. Biblioteka wykonawcza języka C przyjmuje reguły Stanów Zjednoczonych dotyczące implementowania obliczania czasu letniego (DST). |

> [!NOTE]
> Należy uważać na obliczenie znaku różnicy czasu. Ponieważ różnica czasu jest przesunięcie od czasu lokalnego do czasu UTC (a nie odwrotnie), jego znak może być przeciwieństwem tego, co można intuicyjnie oczekiwać. W przypadku stref czasowych przed utc różnica czasu jest ujemna; dla osób za UTC, różnica jest dodatnia.

Na przykład, aby ustawić zmienną środowiskową **TZ** odpowiadającą bieżącej strefie czasowej w Niemczech, wprowadź w wierszu polecenia następujące elementy:

> **zestaw TZ=GST-1GDT**

To polecenie używa podatku GST do wskazania niemieckiego czasu standardowego, zakłada, że utc jest jedną godzinę za Niemcami (lub innymi słowy, że Niemcy jest jedną godzinę przed UTC) i zakłada, że Niemcy przestrzega czasu letniego.

Jeśli wartość **TZ** nie jest ustawiona, **_tzset** próbuje użyć informacji o strefie czasowej określonej przez system operacyjny. W systemie operacyjnym Windows te informacje są określone w aplikacji Data/godzina w Panelu sterowania. Jeśli **_tzset** nie może uzyskać tych informacji, domyślnie używa PST8PDT, co oznacza strefę czasową Pacyfiku.

Na podstawie wartości zmiennej środowiskowej **TZ** do zmiennych globalnych przypisane są następujące wartości **_daylight** **, _timezone**i **_tzname,** gdy nazywana jest **_tzset:**

|Zmienna globalna|Opis|Wartość domyślna|
|---------------------|-----------------|-------------------|
|**_daylight**|Wartość niezerowa, jeśli strefa czasu letniego jest określona w ustawieniu **TZ;** w przeciwnym razie 0.|1|
|**_timezone**|Różnica w sekundach między czasem lokalnym a czasem UTC.|28800 (28800 sekund to 8 godzin)|
|**_tzname**[0]|Wartość ciągu nazwy strefy czasowej ze zmiennej środowiskowej **TZ;** pusty, jeśli **TZ** nie został ustawiony.|Pst|
|**_tzname**[1]|Wartość ciągu strefy czasu letniego; puste, jeśli strefa czasu letniego zostanie pominięta w zmiennej środowiskowej **TZ.**|Pdt|

Wartości domyślne wyświetlane w powyższej tabeli dla **_daylight** i **tablicy _tzname** odpowiadają "PST8PDT". Jeśli strefa czasu dem gncia nie jest pominięta ze zmiennej środowiskowej **TZ,** wartość **_daylight** wynosi 0, a [_ftime](ftime-ftime32-ftime64.md), [gmtime](gmtime-gmtime32-gmtime64.md)i funkcje [czasu lokalnego](localtime-localtime32-localtime64.md) zwracają 0 dla swoich flag czasu du lokalnego.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_tzset**|\<> time.h|

Funkcja **_tzset** jest specyficzna dla firmy Microsoft. Aby uzyskać więcej informacji, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_tzset.cpp
// This program uses _tzset to set the global variables
// named _daylight, _timezone, and _tzname. Since TZ is
// not being explicitly set, it uses the system time.

#include <time.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
    _tzset();
    int daylight;
    _get_daylight( &daylight );
    printf( "_daylight = %d\n", daylight );
    long timezone;
    _get_timezone( &timezone );
    printf( "_timezone = %ld\n", timezone );
    size_t s;
    char tzname[100];
    _get_tzname( &s, tzname, sizeof(tzname), 0 );
    printf( "_tzname[0] = %s\n", tzname );
    exit( 0 );
}
```

```Output
_daylight = 1
_timezone = 28800
_tzname[0] = Pacific Standard Time
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
