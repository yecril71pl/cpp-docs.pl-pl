---
title: Zarządzanie czasem
ms.date: 11/04/2016
helpviewer_keywords:
- dates, run-time library members
- time, time management
- date functions
- time functions
ms.assetid: 93599220-c011-45d5-978f-12182abfdd2f
ms.openlocfilehash: 24859a0b35274881b03b960807904ed38b19e354
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444591"
---
# <a name="time-management"></a>Zarządzanie czasem

Użyj tych funkcji, aby pobrać bieżącą godzinę i przekonwertować ją, dostosować ją i zapisać w razie potrzeby. Bieżąca godzina to czas systemowy.

Procedury **_ftime** i **localtime** korzystają ze **zmiennej środowiskowej** $. Jeśli **nie ustawiono opcji** lt, biblioteka czasu wykonywania próbuje użyć informacji o strefie czasowej określonych przez system operacyjny. Jeśli te informacje są niedostępne, te funkcje używają wartości domyślnej PST8PDT. Aby uzyskać więcej informacji **o programie, zobacz** [_tzset](../c-runtime-library/reference/tzset.md); Zobacz również [_daylight, strefę czasową i _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

### <a name="time-routines"></a>Procedury czasu

|Funkcja|Użycie|
|--------------|---------|
|[asctime, _wasctime](../c-runtime-library/reference/asctime-wasctime.md), [asctime_s, _wasctime_s](../c-runtime-library/reference/asctime-s-wasctime-s.md)|Przekształć czas z typu **struct TM** na ciąg znaków. Wersje tych funkcji z sufiksem **_s** są bezpieczniejsze.|
|[clock](../c-runtime-library/reference/clock.md)|Zwróć czas, który upłynął dla procesu.|
|[CTime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), _ctime_s, _ctime32_s, [_ctime64_s,](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md) _wctime_s, _wctime32_s, _wctime64_s|Przekształć godzinę z typu **time_t**, **__time32_t** lub **__time64_t** na ciąg znaków. Wersje tych funkcji z sufiksem **_s** są bezpieczniejsze.|
|[difftime, _difftime32, _difftime64](../c-runtime-library/reference/difftime-difftime32-difftime64.md)|Różnica obliczeniowa między dwoma razy.|
|[_ftime, _ftime32, _ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md),[_ftime_s, _ftime32_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) _ftime64_s|Przechowuj bieżącą godzinę systemową w zmiennej typu **struct _timeb** lub **struct typu __timeb64** wersje tych funkcji z sufiksem **_sm** są bezpieczniejsze.|
|[_futime, _futime32, _futime64](../c-runtime-library/reference/futime-futime32-futime64.md)|Ustawianie czasu modyfikacji w otwartym pliku|
|[gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime_s, _gmtime32_s, _gmtime64_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|Przekonwertuj czas z typu **time_t** na **strukturę TM** lub z typu **__time64_t** na **strukturę TM**. Wersje tych funkcji z sufiksem **_s** są bezpieczniejsze.|
|[localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime_s, _localtime32_s, _localtime64_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|Przekonwertuj czas z typu **time_t** na **strukturę tm** lub z **__time64_t** typu na **strukturę TM** z korektą lokalną. Wersje tych funkcji z sufiksem **_s** są bezpieczniejsze.|
|[_mkgmtime, _mkgmtime32, _mkgmtime64](../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)|Konwertuj czas na wartość kalendarza w czasie Greenwich.|
|[mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)|Konwertuj czas na wartość kalendarza.|
|[_strdate, _wstrdate](../c-runtime-library/reference/strdate-wstrdate.md), [_strdate_s _wstrdate_s](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|Zwróć bieżącą datę systemową jako ciąg. Wersje tych funkcji z sufiksem **_s** są bezpieczniejsze.|
|[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Sformatuj ciąg daty i godziny dla użytku międzynarodowego.|
|[_strtime, _wstrtime](../c-runtime-library/reference/strtime-wstrtime.md), [_strtime_s _wstrtime_s](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|Zwróć bieżącą godzinę systemową jako ciąg. Wersje tych funkcji z sufiksem **_s** są bezpieczniejsze.|
|[time, _time32, _time64](../c-runtime-library/reference/time-time32-time64.md)|Pobierz bieżącą godzinę systemową jako typ **time_t**, **__time32_t** lub jako **__time64_t**typu.|
|[_tzset](../c-runtime-library/reference/tzset.md)|Ustaw zewnętrzne zmienne czasowe w zmiennej czasowej **środowiska.**|
|[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)|Ustawianie czasu modyfikacji dla określonego pliku przy użyciu bieżącej wartości czasu lub godziny przechowywanej w strukturze.|

> [!NOTE]
> We wszystkich wersjach systemu Microsoft C/C++ z wyjątkiem Microsoft cC++ /wersja 7,0 i we wszystkich wersjach wizualizacji C++funkcja Time zwraca bieżącą godzinę jako liczbę sekund, które upłynęły od północy 1 stycznia 1970. W firmie Microsoft CC++ /w wersji 7,0 **czas** zwrócił bieżący czas jako liczbę sekund, które upłynęły od północy 31 grudnia 1899.

> [!NOTE]
> W wersjach wizualizacji C++ i Microsoft C/C++ przed Visual Studio 2005 **time_t** była **długa** **int** (32 bity), dlatego nie można jej użyć dla dat wcześniejszych niż 3:14:07 19 stycznia 2038, UTC. **time_t** jest teraz odpowiednikiem **__time64_t** domyślnie, ale zdefiniowanie **_USE_32BIT_TIME_T** zmian **time_t** w **__time32_t** i zmusza wiele funkcji czasu do wywoływania wersji, które mają 32-bitowe **time_t**. Aby uzyskać więcej informacji, zobacz [typy standardowe](../c-runtime-library/standard-types.md) i komentarze w dokumentacji dotyczące poszczególnych funkcji czasu.

## <a name="see-also"></a>Zobacz też

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
