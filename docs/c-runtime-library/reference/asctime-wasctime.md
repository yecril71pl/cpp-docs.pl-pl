---
title: asctime —, _wasctime — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- asctime function
- tasctime function
- wasctime function
- _tasctime function
- _wasctime function
- time structure conversion
- time, converting
ms.assetid: 974f1727-10ff-4ed4-8cac-2eb2d681f576
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 08390638fafff75674324d111445b44c64d8bf53
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="asctime-wasctime"></a>asctime, _wasctime

Konwertuj **tm** czasu struktury do ciągu znaków. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [asctime_s —, _wasctime_s —](asctime-s-wasctime-s.md).

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
Godzina i Data struktury.

## <a name="return-value"></a>Wartość zwracana

**asctime —** zwraca wskaźnik do wyniku ciąg znaków; **_wasctime —** zwraca wskaźnik do wyniku ciąg znaków dwubajtowych. Nie istnieje wartość zwracany błąd.

## <a name="remarks"></a>Uwagi

Bezpieczniejsza wersje te funkcje są dostępne; zobacz [asctime_s —, _wasctime_s —](asctime-s-wasctime-s.md).

**Asctime —** funkcja konwertuje godzinę przechowywane jako struktura na ciąg znaków. *Timeptr* wartość zazwyczaj jest uzyskiwana w wyniku wywołania **gmtime —** lub **konwersję**, które zwraca wskaźnik do **tm** struktury zdefiniowany w czasie. H.

|element członkowski timeptr|Wartość|
|--------------------|-----------|
|**tm_hour**|Godziny od północy (0-23)|
|**tm_isdst**|Dodatnie, jeśli czas letni są włączone; 0, jeśli czas letni nie jest włączone; ujemna, jeśli stan okresu obowiązywania czasu letniego jest nieznany. Biblioteki wykonawcze języka C zakłada Stanów Zjednoczonych zasady wykonywania obliczeń czasu (DST).|
|**tm_mday**|Dzień miesiąca (1-31)|
|**tm_min**|Minut po godziny (0-59)|
|**tm_mon**|Miesiąc (0-11; Stycznia = 0)|
|**tm_sec**|Sekund po minucie (0-59)|
|**tm_wday**|Dzień tygodnia (0 – 6; Niedziela = 0)|
|**tm_yday**|Dzień roku (0-365; 1 stycznia = 0)|
|**tm_year**|Roku (bieżącego roku minus 1900)|

Ciąg przekonwertowany znaków jest również dostosowywana zgodnie z ustawieniami strefy czasu lokalnego. Informacje o konfigurowaniu czasu lokalnego, zobacz [czasu](time-time32-time64.md), [_ftime —](ftime-ftime32-ftime64.md), i [konwersję](localtime-localtime32-localtime64.md) funkcje i [_tzset —](tzset.md) — funkcja Aby uzyskać informacji na temat definiowania strefy czasowej środowiska i zmiennych globalnych.

Wynik ciąg utworzony przez **asctime —** zawiera dokładnie 26 znaków i ma postać `Wed Jan 02 02:03:55 1980\n\0`. 24-godzinnym jest używany. Wszystkie pola mają stałej szerokości. Znak nowego wiersza i znaku null zajmują ostatnich dwóch pozycji w ciągu. **asctime —** używa buforu jednej, statycznie przydzielonego do przechowywania zwracany ciąg. Każde wywołanie tej funkcji niszczy wynik poprzedniego wywołania.

**_wasctime —** jest wersja znaków dwubajtowych **asctime —**. **_wasctime —** i **asctime —** zachowują się tak samo w przeciwnym razie wartość.

Te funkcje walidację ich parametrów. Jeśli *timeptr* jest wskaźnika o wartości null lub zawiera wartości spoza zakresu, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcja zwraca **NULL** i ustawia **errno** do **einval —**.

### <a name="generic-text-routine-mapping"></a>Rutynowe mapowanie — zwykły tekst

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime —**|**asctime —**|**asctime —**|**_wasctime**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**asctime —**|\<time.h>|
|**_wasctime**|\<Time.h > lub \<wchar.h >|

## <a name="example"></a>Przykład

Ten program umieszcza czasu systemowego w długich liczb całkowitych **aclock**, tłumaczy go do struktury **newtime** i konwertuje ją do postaci ciągu dla danych wyjściowych, używając **asctime —**funkcji.

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
