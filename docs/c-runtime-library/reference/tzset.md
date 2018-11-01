---
title: _tzset
ms.date: 11/04/2016
apiname:
- _tzset
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
- _tzset
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
ms.openlocfilehash: 33fd1cc0a618fccc4a59e5aff059d3f2cdeec8fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661763"
---
# <a name="tzset"></a>_tzset

Ustawia czas zmiennych środowiskowych.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
void _tzset( void );
```

## <a name="remarks"></a>Uwagi

**_Tzset —** funkcja używa bieżącego ustawienia zmiennej środowiskowej **TZ** do przypisywania wartości do trzech zmiennych globalnych: **_daylight**, **_timezone** , i **_tzname**. Te zmienne są używane przez [_ftime](ftime-ftime32-ftime64.md) i [localtime](localtime-localtime32-localtime64.md) funkcje do wprowadzania poprawek od skoordynowanego czasu uniwersalnego (UTC), do czasu lokalnego oraz [czasu](time-time32-time64.md) funkcja obliczania czasu UTC od czasu systemowego. Użyj następującej składni, aby ustawić **TZ** zmienną środowiskową:

> **Ustaw TZ =**_tzn_ \[ **+** &#124; **-**]*hh* \[ **:**_mm_\[**:**_ss_]] [*dzn*]

|Parametr|Opis|
|-|-|
*tzn*|Nazwa strefy czasowej trzyliterowy, taka jak PDT. Należy określić poprawne przesunięcie od lokalnego czasu na czas UTC.
*hh*|Różnica w godzinach między czasem UTC i czasem lokalnym. Znak (+) opcjonalny wartości dodatnich.
*mm*|Minuty. Oddzielony od *hh* za pomocą dwukropka (**:**).
*ss*|Liczba sekund. Oddzielony od *mm* za pomocą dwukropka (**:**).
*dzn*|Trzyliterowe strefy zmiany czasu takie jak PDT. Jeśli czas letni nigdy nie jest włączone w tej lokalizacji, ustaw **TZ** bez wartości dla *dzn*. Biblioteki wykonawczej C zakłada zasady Stanów Zjednoczonych wykonywania obliczeń czasu letniego (DST).

> [!NOTE]
> Ostrożny przy obliczaniu znaku różnicy czasu. Ponieważ różnica czasu jest przesunięta względem czasu lokalnego do UTC (a nie odwrotnie), jej znak może być przeciwieństwem co można intuicyjnie oczekiwać. Dla stref czasowych przed UTC różnica czasu jest ujemna; dla tych za UTC różnica jest dodatnia.

Na przykład, aby ustawić **TZ** zmiennej środowiskowej, aby odpowiadać bieżącej strefy czasowej w Niemczech, wprowadź następujące polecenie w wierszu polecenia:

> **Ustaw TZ = GST 1GDT**

To polecenie używa GST do wskazania niemieckiego czasu standardowego przyjęto założenie, że UTC jest jedną godzinę Niemcami (lub innymi słowy, których Niemicy są jedną godzinę wcześniej przed UTC) i zakłada się, że Niemcy przestrzegają czasu letniego.

Jeśli **TZ** wartość nie jest ustawiona, **_tzset —** próbuje użyć informacji o strefie czasowej określonej przez system operacyjny. W systemie operacyjnym Windows informacja ta jest określona w aplikacji Data/Godzina w Panelu sterowania. Jeśli **_tzset —** nie może uzyskać tych informacji, używa PST8PDT domyślnie, co oznacza strefy czasu pacyficznego.

Na podstawie **TZ** wartości zmiennej środowiskowej, następujące wartości są przypisane do zmiennych globalnych **_daylight**, **_timezone**, i **_tzname** podczas **_tzset —** nosi nazwę:

|Zmienna globalna|Opis|Wartość domyślna|
|---------------------|-----------------|-------------------|
|**_daylight**|Wartość różną od zera, jeśli strefa zmiany czasu jest określana w **TZ** ustawienie; w przeciwnym razie 0.|1|
|**_timezone**|Różnica w sekundach między czasem lokalnym i czasem UTC.|28800 (28800 sekund jest równych 8 godzinom)|
|**_tzname**[0]|Wartość nazwy strefy czasowej z ciągu **TZ** zmiennej środowiskowej; pusta Jeżeli **TZ** nie została ustawiona.|PST|
|**_tzname**[1]|Wartość ciągu zmiany czasu strefy; pusty w przypadku zmiany czasu strefy pominięto w **TZ** zmiennej środowiskowej.|PDT|

Wartości domyślne, pokazana w powyższej tabeli dla **_daylight** i **_tzname** tablicy odpowiada "PST8PDT." Jeśli pominięto strefę czasu letniego w **TZ** zmiennej środowiskowej, wartość **_daylight** wynosi 0 i [_ftime](ftime-ftime32-ftime64.md), [gmtime](gmtime-gmtime32-gmtime64.md)i [localtime](localtime-localtime32-localtime64.md) funkcje zwracają wartość 0 dla swoich flag czasu letniego.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_tzset**|\<time.h>|

**_Tzset —** funkcja jest specyficzne dla firmy Microsoft. Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
