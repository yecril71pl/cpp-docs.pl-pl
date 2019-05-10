---
title: Zarządzanie czasem
ms.date: 11/04/2016
f1_keywords:
- c.memory
helpviewer_keywords:
- dates, run-time library members
- time, time management
- date functions
- time functions
ms.assetid: 93599220-c011-45d5-978f-12182abfdd2f
ms.openlocfilehash: e9842d8c24089c7fbb33745c3bf5d4edb1d29343
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446787"
---
# <a name="time-management"></a>Zarządzanie czasem

Za pomocą tych funkcji można pobrać bieżącego czasu i konwersji, dostosować i zapisać ją w razie potrzeby. Bieżący czas to czas systemowy.

**_Ftime** i **localtime** użyć procedur **TZ** zmiennej środowiskowej. Jeśli **TZ** nie jest ustawiona, biblioteka środowiska uruchomieniowego podejmują próbę użycia informacji o strefie czasowej, określonych przez system operacyjny. Jeśli te informacje są niedostępne, te funkcje Użyj PST8PDT wartość domyślną. Aby uzyskać więcej informacji na temat **TZ**, zobacz [_tzset —](../c-runtime-library/reference/tzset.md); Zobacz też [_daylight, strefa czasowa i _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

### <a name="time-routines"></a>Procedury czasu

|Funkcja|Zastosowanie|
|--------------|---------|
|[asctime —, _wasctime —](../c-runtime-library/reference/asctime-wasctime.md), [asctime_s —, _wasctime_s —](../c-runtime-library/reference/asctime-s-wasctime-s.md)|Konwertuj czas z typu **tm struktury** do ciągu znaków. Wersje tych funkcji **_s** sufiksem są bardziej bezpieczne.|
|[clock](../c-runtime-library/reference/clock.md)|Zwróć czas czas zegarowy dla procesu.|
|[ctime, _ctime32 —, _ctime64, _wctime, _wctime32 —, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [_ctime_s, _ctime32_s, _ctime64_s —, _wctime_s —, _wctime32_s, _wctime64_s —](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)|Konwertuj czas z typu **time_t**, **__time32_t** lub **__time64_t —** do ciągu znaków. Wersje tych funkcji **_s** sufiksem są bardziej bezpieczne.|
|[difftime, _difftime32, _difftime64](../c-runtime-library/reference/difftime-difftime32-difftime64.md)|Obliczenia różnicy między dwiema wartościami godziny.|
|[_ftime, _ftime32, _ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md),[_ftime_s _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)|Store bieżący czas systemowy w zmiennej typu **_timeb — struktura** lub typ **__timeb64 — struktura** wersje tych funkcji **_s** sufiksem są bardziej bezpieczne.|
|[_futime, _futime32, _futime64](../c-runtime-library/reference/futime-futime32-futime64.md)|Ustaw czas modyfikacji na otwieranie pliku|
|[gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime_s, _gmtime32_s, _gmtime64_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|Konwertuj czasu z typu **time_t** do **tm struktury** lub z typu **__time64_t —** do **tm struktury**. Wersje tych funkcji **_s** sufiksem są bardziej bezpieczne.|
|[localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime_s —, _localtime32_s —, _localtime64_s —](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|Przekonwertowanie czasu z **time_t** do **tm struktury** lub z typu **__time64_t —** do **tm struktury** przy użyciu lokalnego korekty. Wersje tych funkcji **_s** sufiksem są bardziej bezpieczne.|
|[_mkgmtime, _mkgmtime32, _mkgmtime64](../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)|Konwertuj czasu na wartość kalendarza w czas uniwersalny Greenwich.|
|[mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)|Konwertuj czasu na wartość kalendarza.|
|[_strdate —, _wstrdate —](../c-runtime-library/reference/strdate-wstrdate.md), [_strdate_s —, _wstrdate_s —](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|Zwraca datę jako ciąg. Wersje tych funkcji **_s** sufiksem są bardziej bezpieczne.|
|[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Format ciągu daty i godziny do użytku międzynarodowego.|
|[_strtime —, _wstrtime —](../c-runtime-library/reference/strtime-wstrtime.md), [_strtime_s —, _wstrtime_s —](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|Zwraca bieżący czas systemowy jako ciąg. Wersje tych funkcji **_s** sufiksem są bardziej bezpieczne.|
|[time, _time32, _time64](../c-runtime-library/reference/time-time32-time64.md)|Pobierz bieżący czas systemowy, jako typ **time_t**, **__time32_t** lub jako typ **__time64_t —**.|
|[_tzset](../c-runtime-library/reference/tzset.md)|Ustaw zmienne czas zewnętrzny ze zmiennych czasu środowiska **TZ**.|
|[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)|Ustaw czas modyfikacji dla określonego pliku przy użyciu bieżącego czasu lub wartości godziny, zapisane w strukturze.|

> [!NOTE]
> We wszystkich wersjach programu Microsoft C/C++ z wyjątkiem w Microsoft C/C++ version 7.0 i we wszystkich wersjach programu Visual C++ funkcji czasu zwraca bieżącą godzinę jako liczbę sekund, który upłynął od północy 1 stycznia 1970. W programie Microsoft C/C++ 7.0 version **czasu** zwrócił bieżącą godzinę jako liczbę sekund, który upłynął od północy w dniu 31 grudnia 1899.

> [!NOTE]
> W wersjach programu Visual C++ i Microsoft C /C++ przed Visual Studio 2005, **time_t** został **długie** **int** (32-bitowy) i dlatego nie może zostać użyty dla ostatnich dat 3:14:07 19 stycznia 2038 r. UTC. **time_t** odpowiada teraz **__time64_t —** domyślnego, ale zdefiniowanie **_USE_32BIT_TIME_T** zmiany **time_t** do **__time32_t** i wymusza wiele funkcji czasu do wywołania wersje przyjmujące 32-bitowych **time_t**. Aby uzyskać więcej informacji, zobacz [standardowych typów](../c-runtime-library/standard-types.md) i komentarzy w dokumentacji dotyczącej funkcji czasu.

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
