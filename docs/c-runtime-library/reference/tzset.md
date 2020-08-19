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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 0791fe6002b751906c6bc6f83dafe1ccf202bc8b
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562028"
---
# <a name="_tzset"></a>_tzset

Ustawia zmienne środowiskowe czasu.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
void _tzset( void );
```

## <a name="remarks"></a>Uwagi

Funkcja **_tzset** używa bieżącego ustawienia zmiennej środowiskowej $ do przypisywania **wartości do trzech** zmiennych globalnych: **_daylight**, **_timezone**i **_tzname**. Te zmienne są używane przez funkcje [_ftime](ftime-ftime32-ftime64.md) i [localtime](localtime-localtime32-localtime64.md) w celu wprowadzania poprawek od uniwersalnego czasu koordynowanego (UTC) do czasu lokalnego, a przez funkcję [Time](time-time32-time64.md) do obliczania czasu UTC z godziny systemowej. Aby ustawić **zmienną środowiskową** programu, należy użyć następującej składni:

> **Set $ =**_tzn_ \[ **+**&#124;**-** ]*hh* \[ **:**_mm_ \[ **:**_SS_]] [*dzn*]

 *tzn* \
 3-literowa nazwa strefy czasowej, na przykład PST. Należy określić prawidłowe przesunięcie od czasu lokalnego na UTC.

 *formacie* \
 Różnica w godzinach między czasem UTC i czasem lokalnym. Znak (+) opcjonalny dla wartości dodatnich.

 *–* \
 Minut. Oddzielona od *hh* przez dwukropek (**:**).

 *RR* \
 S. Oddzielone od *mm* średnikiem (**:**).

 *dzn* \
 Trzy litery strefy czasowej zmiany czasu, takie jak PDT. Jeśli czas letni nigdy nie obowiązuje **, ustaw wartość** opcji UstawWartość bez wartości dla *dzn*. Biblioteka środowiska uruchomieniowego C przyjmuje reguły Stany Zjednoczone "na potrzeby wykonywania obliczeń czasu letniego (DST).

> [!NOTE]
> Weź pod uwagę obliczanie znaku różnicy czasu. Ze względu na to, że różnica czasu jest przesunięta od czasu lokalnego na UTC (a nie odwrotnie), jego znak może być przeciwieństwem do tego, co można intuicyjnie oczekiwać. Dla stref czasowych przed czasem UTC różnica czasu jest ujemna; różnica jest dodatnia dla tych za czas UTC.

Na przykład, aby ustawić zmienną **środowiskową** , która odpowiada bieżącej strefie czasowej w Niemczech, wprowadź następujące polecenie w wierszu polecenia:

> **Set $ = GST (-1GDT**

To polecenie używa GST (do wskazania niemieckiego czasu standardowego, zakłada, że czas UTC jest godzinę za Niemcy (lub innymi słowy, że Niemcy to godzina przed czasem UTC) i zakłada, że Niemcy obserwują czas letni.

Jeśli wartość **nie** jest ustawiona, **_tzset** próbuje użyć informacji o strefie czasowej określonych przez system operacyjny. W systemie operacyjnym Windows te informacje są określone w aplikacji Data/godzina w panelu sterowania. Jeśli **_tzset** nie może uzyskać tych informacji, domyślnie używa PST8PDT, co oznacza strefę czasową pacyficznego.

Na podstawie wartości **zmiennej środowiskowej** $ następujące wartości są przypisywane do zmiennych globalnych **_daylight**, **_timezone**i **_tzname** po wywołaniu **_tzset** :

|Zmienna globalna|Opis|Wartość domyślna|
|---------------------|-----------------|-------------------|
|**_daylight**|Wartość różna od zera, jeśli **w ustawieniu $** jest określona strefa czasu letniego. w przeciwnym razie 0.|1|
|**_timezone**|Różnica w sekundach między czasem lokalnym i czasem UTC.|28800 (28800 s = 8 godzin)|
|**_tzname**[0]|Wartość ciągu nazwy strefy czasowej z zmiennej **w środowisku** . puste, **Jeśli nie ustawiono opcji** $.|KOPIA|
|**_tzname**[1]|Wartość ciągu strefy czasowej zmiany czasu; puste, jeśli strefa czasowa zmiany czasu jest pomijana z **zmiennej** środowiskowej.|PDT|

Wartości domyślne pokazane w powyższej tabeli dla **_daylight** , a tablica **_tznamea** odpowiada "PST8PDT". Jeśli strefa czasowa została pominięta ze zmiennej **środowiskowej** $, wartość **_daylight** jest równa 0, a funkcje [_ftime](ftime-ftime32-ftime64.md), [gmtime](gmtime-gmtime32-gmtime64.md)i [localtime](localtime-localtime32-localtime64.md) zwracają wartość 0 dla ich flag DST.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_tzset**|\<time.h>|

Funkcja **_tzset** jest specyficzna dla firmy Microsoft. Aby uzyskać więcej informacji, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
