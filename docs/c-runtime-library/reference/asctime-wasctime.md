---
title: asctime, _wasctime
ms.date: 11/04/2016
apiname:
- _wasctime
- asctime
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
- _tasctime
- asctime
- _wasctime
helpviewer_keywords:
- asctime function
- tasctime function
- wasctime function
- _tasctime function
- _wasctime function
- time structure conversion
- time, converting
ms.assetid: 974f1727-10ff-4ed4-8cac-2eb2d681f576
ms.openlocfilehash: bc2d7a50442d9000eaaebf7a06bf336b3317e4df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577911"
---
# <a name="asctime-wasctime"></a>asctime, _wasctime

Konwertuj **tm** czasu struktury do ciągu znaków. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [asctime_s —, _wasctime_s —](asctime-s-wasctime-s.md).

## <a name="syntax"></a>Składnia

```C
char *asctime(
   const struct tm *timeptr
);
wchar_t *_wasctime(
   const struct tm *timeptr
);
```

### <a name="parameters"></a>Parametry

*timeptr*<br/>
Daty/godziny struktury.

## <a name="return-value"></a>Wartość zwracana

**asctime —** zwraca wskaźnik do wynikowy ciąg znaków; **_wasctime —** zwraca wskaźnik do wynikowy ciąg znaków dwubajtowych. Nie ma błędów zwracane wartości.

## <a name="remarks"></a>Uwagi

Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [asctime_s —, _wasctime_s —](asctime-s-wasctime-s.md).

**Asctime —** funkcja konwertuje czas przechowywane jako struktura do ciągu znaków. *Timeptr* wartość zwykle jest uzyskiwana w wyniku wywołania **gmtime** lub **localtime**, które zwracają wskaźnik do **tm** struktury zdefiniowane w czasie. H.

|element członkowski timeptr|Wartość|
|--------------------|-----------|
|**tm_hour**|Godziny od północy (0-23)|
|**tm_isdst**|Dodatnie, jeśli czas letni obowiązuje; 0, jeśli czas letni nie jest włączone; ujemna, jeśli stan czasu jest nieznany. Biblioteki wykonawczej C zakłada zasady Stanów Zjednoczonych wykonywania obliczeń czasu letniego (DST).|
|**tm_mday**|Dzień miesiąca (1-31)|
|**tm_min**|Min. po godzinie (0-59)|
|**tm_mon**|Miesiąc (0-11; Styczeń = 0)|
|**tm_sec**|Sekundy po minucie (0-59)|
|**tm_wday**|Dzień tygodnia (0 – 6; Niedziela = 0)|
|**tm_yday**|Dzień roku (0 – 365; Od 1 stycznia = 0)|
|**tm_year**|Rok (bieżący roku minus 1900)|

Ciąg przekonwertowany znak również jest dostosowywany zgodnie z ustawieniami strefy czasu lokalnego. Aby uzyskać informacji o konfigurowaniu czasu lokalnego, zobacz [czasu](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md), i [localtime](localtime-localtime32-localtime64.md) funkcje i [_tzset —](tzset.md) — funkcja Aby uzyskać informacji na temat definiowania środowiska strefy czasowej i zmienne globalne.

Wynikowy ciąg utworzony przez **asctime —** zawiera dokładnie 26 znaków i ma postać `Wed Jan 02 02:03:55 1980\n\0`. Używany jest zegar 24-godzinny. Wszystkie pola są stałej szerokości. Znak nowego wiersza i znak null zajmują się dwie ostatnie pozycje ciągu. **asctime —** używa pojedynczego, statycznie przydzielanego bufor do przechowywania zwracanego ciągu. Każde wywołanie tej funkcji niszczy wynik poprzedniego wywołania.

**_wasctime —** to wersja znaku dwubajtowego **asctime —**. **_wasctime —** i **asctime —** zachowują się identycznie.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *timeptr* jest wskaźnikiem typu null lub jeśli zawiera on wartości spoza zakresu, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca **NULL** i ustawia **errno** do **EINVAL**.

### <a name="generic-text-routine-mapping"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime —**|**asctime —**|**asctime —**|**_wasctime**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**asctime —**|\<time.h>|
|**_wasctime**|\<Time.h > lub \<wchar.h >|

## <a name="example"></a>Przykład

Ten program umieszcza czas systemowy w długich liczb całkowitych **aclock**, przekształca je w strukturze **newtime** i konwertuje je do postaci ciągu dla danych wyjściowych, przy użyciu **asctime —** funkcji.

```C
// crt_asctime.c
// compile with: /W3

#include <time.h>
#include <stdio.h>

int main( void )
{
    struct tm   *newTime;
    time_t      szClock;

    // Get time in seconds
    time( &szClock );

    // Convert time to struct tm form
    newTime = localtime( &szClock );

    // Print local time as a string.
    printf_s( "Current date and time: %s", asctime( newTime ) ); // C4996
    // Note: asctime is deprecated; consider using asctime_s instead
}
```

```Output
Current date and time: Sun Feb 03 11:38:58 2002
```

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
