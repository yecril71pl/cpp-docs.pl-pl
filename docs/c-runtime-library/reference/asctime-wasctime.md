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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 00c6be8ee409d76b80d323102950f8c1d6420ba3
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909422"
---
# <a name="asctime-_wasctime"></a>asctime, _wasctime

Konwertuj strukturę czasu **TM** na ciąg znaków. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [asctime_s, _wasctime_s](asctime-s-wasctime-s.md).

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

**asctime** zwraca wskaźnik do wyniku ciągu znaków; **_wasctime** zwraca wskaźnik do wyniku ciągu znaków dwubajtowych. Brak zwracanej wartości błędu.

## <a name="remarks"></a>Uwagi

Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [asctime_s, _wasctime_s](asctime-s-wasctime-s.md).

Funkcja **asctime** konwertuje godzinę przechowywaną jako strukturę do ciągu znaków. Wartość *timeptr* jest zazwyczaj uzyskiwana z wywołania **gmtime** lub **localtime**, które zwracają wskaźnik do struktury **TM** , zdefiniowane w czasie. C.

|timeptr element członkowski|Wartość|
|--------------------|-----------|
|**tm_hour**|Godz. od północy (0-23)|
|**tm_isdst**|Pozytywna, jeśli obowiązuje zmiana czasu letniego; 0, jeśli czas letni nie jest stosowany; wartość ujemna, jeśli stan czasu letniego jest nieznany. Biblioteka środowiska uruchomieniowego C przyjmuje reguły Stany Zjednoczone "na potrzeby wykonywania obliczeń czasu letniego (DST).|
|**tm_mday**|Dzień miesiąca (1-31)|
|**tm_min**|Minuty po godzinie (0-59)|
|**tm_mon**|Miesiąc (0-11; Styczeń = 0)|
|**tm_sec**|Sekund po minucie (0-59)|
|**tm_wday**|Dzień tygodnia (0-6; Niedziela = 0)|
|**tm_yday**|Dzień roku (0-365; 1 stycznia = 0)|
|**tm_year**|Year (bieżący rok minus 1900)|

Przekonwertowany ciąg znaków jest również dostosowywany zgodnie z ustawieniami lokalnej strefy czasowej. Aby uzyskać informacje o konfigurowaniu czasu lokalnego, zobacz funkcje [Time](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md)i [localtime](localtime-localtime32-localtime64.md) oraz funkcja [_tzset](tzset.md) , aby uzyskać informacje na temat definiowania środowiska strefy czasowej i zmiennych globalnych.

Wynik ciągu utworzony przez **asctime** zawiera dokładnie 26 znaków i ma postać `Wed Jan 02 02:03:55 1980\n\0`. Używany jest zegar 24-godzinny. Wszystkie pola mają stałą szerokość. Znak nowego wiersza i znak null zajmują ostatnie dwa pozycje ciągu. **asctime** używa pojedynczego, przydzieloną statycznie buforu do przechowywania zwracanego ciągu. Każde wywołanie tej funkcji niszczy wynik poprzedniego wywołania.

**_wasctime** to dwubajtowa wersja **asctime**. **_wasctime** i **asctime** zachowują się identycznie w inny sposób.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *timeptr* jest wskaźnikiem typu null lub jeśli zawiera wartości spoza zakresu, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca **wartość null** i ustawia **errno** na **EINVAL**.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Mapowanie procedury tekstu ogólnego

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime**|**asctime**|**asctime**|**_wasctime**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**asctime**|\<> godziny. h|
|**_wasctime**|\<Time. h> lub \<WCHAR. h>|

## <a name="example"></a>Przykład

Ten program umieszcza czas systemowy w **aclockej**liczbie całkowitej, tłumaczy je na strukturę **newtime** , a następnie konwertuje ją na format ciągu dla danych wyjściowych przy użyciu funkcji **asctime** .

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
