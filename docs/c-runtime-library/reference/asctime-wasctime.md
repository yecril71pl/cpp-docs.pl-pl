---
title: asctime, _wasctime
ms.date: 4/2/2020
api_name:
- _wasctime
- asctime
- _o__wasctime
- _o_asctime
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
ms.openlocfilehash: bda14f3b6046378ad23148371f354bb910163d3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350483"
---
# <a name="asctime-_wasctime"></a>asctime, _wasctime

Konwertowanie struktury czasu **tm** na ciąg znaków. Dostępne są bezpieczniejsze wersje tych funkcji; patrz [asctime_s, _wasctime_s](asctime-s-wasctime-s.md).

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
Struktura czasu/daty.

## <a name="return-value"></a>Wartość zwracana

**asctime** zwraca wskaźnik do wyniku ciągu znaku; **_wasctime** zwraca wskaźnik do wyniku ciągu szerokoznakowego. Nie ma wartości zwracanej błędu.

## <a name="remarks"></a>Uwagi

Dostępne są bezpieczniejsze wersje tych funkcji; patrz [asctime_s, _wasctime_s](asctime-s-wasctime-s.md).

Funkcja **asctime** konwertuje czas przechowywany jako struktura na ciąg znaków. Wartość *timeptr* jest zwykle uzyskiwana z wywołania **gmtime** lub **localtime**, które zwracają wskaźnik do struktury **tm,** zdefiniowanej w czas. H.

|Element członkowski timeptr|Wartość|
|--------------------|-----------|
|**tm_hour**|Godziny od północy (0-23)|
|**tm_isdst**|Dodatnie, jeśli obowiązuje czas letni; 0, jeśli czas letni nie obowiązuje; ujemny, jeśli stan czasu letniego jest nieznany. Biblioteka wykonawcza języka C przyjmuje reguły Stanów Zjednoczonych dotyczące implementowania obliczania czasu letniego (DST).|
|**tm_mday**|Dzień miesiąca (1-31)|
|**tm_min**|Minuty po godzinie (0-59)|
|**tm_mon**|Miesiąc (0-11; Styczeń = 0)|
|**tm_sec**|Sekundy po minucie (0-59)|
|**tm_wday**|Dzień tygodnia (0-6; Niedziela = 0)|
|**tm_yday**|Dzień roku (0-365; 1 stycznia = 0)|
|**tm_year**|Rok (rok bieżący minus 1900)|

Przekonwertowany ciąg znaków jest również dostosowywany zgodnie z ustawieniami lokalnej strefy czasowej. Aby uzyskać informacje dotyczące konfigurowania czasu lokalnego, zobacz [czas](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md)i funkcje [czasu lokalnego](localtime-localtime32-localtime64.md) oraz funkcję [_tzset,](tzset.md) aby uzyskać informacje na temat definiowania środowiska strefy czasowej i zmiennych globalnych.

Wynik ciągu wyprodukowany przez **asctime** zawiera dokładnie 26 znaków i ma formularz `Wed Jan 02 02:03:55 1980\n\0`. Używany jest zegar 24-godzinny. Wszystkie pola mają stałą szerokość. Znak nowego i znak null zajmują dwie ostatnie pozycje ciągu. **asctime** używa pojedynczego buforu statycznie przydzielonego do przechowywania ciągu zwracanego. Każde wywołanie tej funkcji niszczy wynik poprzedniego wywołania.

**_wasctime** jest szerokoznakową wersją **asctime.** **_wasctime** i **asctime** zachowują się identycznie inaczej.

Te funkcje sprawdzają ich parametry. Jeśli *timepter* jest wskaźnikiem zerowym lub jeśli zawiera wartości poza zakresem, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [polu Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, funkcja zwraca **wartość NULL** i ustawia **errno** na **Wartość EINVAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Mapowanie rutynowych tekstu ogólnego

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime**|**asctime (czas na szemoc**|**asctime (czas na szemoc**|**_wasctime**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**asctime (czas na szemoc**|\<> time.h|
|**_wasctime**|\<time.h> lub \<wchar.h>|

## <a name="example"></a>Przykład

Ten program umieszcza czas systemowy w długim **całkowitym blokadie,** przekłada go na **newtime** struktury, a następnie konwertuje go do postaci ciągu dla danych wyjściowych, przy użyciu funkcji **asctime.**

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

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
