---
title: "Czas zarządzania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.memory
dev_langs: C++
helpviewer_keywords:
- dates, run-time library members
- time, time management
- date functions
- time functions
ms.assetid: 93599220-c011-45d5-978f-12182abfdd2f
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6a634d748a0960e0eda56f89bcca66463780f08f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="time-management"></a>Zarządzanie czasem
Aby pobrać bieżącego czasu i przekonwertować, Dostosuj i zapisz go w razie potrzeby korzystania z tych funkcji. Bieżący czas to czas systemowy.  
  
 `_ftime` i `localtime` użyć procedury `TZ` zmiennej środowiskowej. Jeśli `TZ` nie jest ustawiona, biblioteki wykonawczej próbuje użyć informacji o strefie czasowej, określony przez system operacyjny. Jeśli te informacje są niedostępne, te funkcje użyć wartości domyślnej PST8PDT. Aby uzyskać więcej informacji na temat `TZ`, zobacz [_tzset —](../c-runtime-library/reference/tzset.md); Zobacz też [_daylight, strefa czasowa i _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).  
  
### <a name="time-routines"></a>Procedury czasu  
  
|Funkcja|Zastosowanie|  
|--------------|---------|  
|[asctime —, _wasctime —](../c-runtime-library/reference/asctime-wasctime.md), [asctime_s —, _wasctime_s —](../c-runtime-library/reference/asctime-s-wasctime-s.md)|Konwertować z typu czasu `struct tm` do ciągu znaków. Wersje tych funkcji z `_s` sufiks są bardziej bezpieczne.|  
|[zegara](../c-runtime-library/reference/clock.md)|Zwraca czas zegara wall czas procesu.|  
|[ctime —, _ctime32 —, _ctime64 —, _wctime —, _wctime32 —, _wctime64 —](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [_ctime_s, _ctime32_s —, _ctime64_s —, _wctime_s —, _wctime32_s —, _wctime64_s —](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)|Konwertować z typu czasu `time_t`, `__time32_t` lub `__time64_t` do ciągu znaków. Wersje tych funkcji z `_s` sufiks są bardziej bezpieczne.|  
|[difftime —, _difftime32 —, _difftime64 —](../c-runtime-library/reference/difftime-difftime32-difftime64.md)|Oblicza różnicę między dwiema wartościami godziny.|[System::DateTime:: odejmowania](https://msdn.microsoft.com/en-us/library/system.datetime.subtract.aspx)|  
|[_ftime —, _ftime32 —, _ftime64 —](../c-runtime-library/reference/ftime-ftime32-ftime64.md),[_ftime_s —, _ftime32_s —, _ftime64_s —](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)|Przechowywanie bieżący czas systemowy w zmiennej typu `struct _timeb` lub typ `struct __timeb64` wersje tych funkcji z `_s` sufiks są bardziej bezpieczne.|  
|[_futime —, _futime32 —, _futime64 —](../c-runtime-library/reference/futime-futime32-futime64.md)|Ustaw czas modyfikacji pliku otwarte|  
|[gmtime —, _gmtime32 —, _gmtime64 —](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime_s —, _gmtime32_s —, _gmtime64_s —](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|Konwertować z typu czasu `time_t` do `struct tm` lub z typu `__time64_t` do `struct tm`. Wersje tych funkcji z `_s` sufiks są bardziej bezpieczne.|  
|[czas lokalny, _localtime32 —, _localtime64 —](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime_s —, _localtime32_s —, _localtime64_s —](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|Konwertować z typu czasu `time_t` do `struct tm` lub z typu `__time64_t` do `struct tm` z lokalnym korekty. Wersje tych funkcji z `_s` sufiks są bardziej bezpieczne.|  
|[_mkgmtime —, _mkgmtime32 —, _mkgmtime64 —](../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)|Konwertuj czasu na wartość kalendarza w czas uniwersalny Greenwich.|  
|[mktime —, _mktime32 —, _mktime64 —](../c-runtime-library/reference/mktime-mktime32-mktime64.md)|Konwertuj czasu na wartość kalendarza.|  
|[_strdate —, _wstrdate —](../c-runtime-library/reference/strdate-wstrdate.md), [_strdate_s —, _wstrdate_s —](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|Zwraca bieżącą datę systemową w postaci ciągu. Wersje tych funkcji z `_s` sufiks są bardziej bezpieczne.|  
|[strftime —, wcsftime —, _strftime_l — _wcsftime_l —](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Ciąg daty i godziny do użytku międzynarodowego formatu.|  
|[_strtime —, _wstrtime —](../c-runtime-library/reference/strtime-wstrtime.md), [_strtime_s —, _wstrtime_s —](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|Zwraca bieżący czas systemowy jako ciąg. Wersje tych funkcji z `_s` sufiks są bardziej bezpieczne.|  
|[czas, _time32 —, _time64 —](../c-runtime-library/reference/time-time32-time64.md)|Pobierz bieżący czas systemowy jako typ `time_t`, `__time32_t` lub jako typ `__time64_t`.|  
|[_tzset —](../c-runtime-library/reference/tzset.md)|Ustaw zmienne czas zewnętrzny w zmiennej środowiskowej czas `TZ`.|  
|[_utime —, _utime32 —, _utime64 —, _wutime — _wutime32 —, _wutime64 —](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)|Ustawianie czasu modyfikacji określonego pliku, przy użyciu bieżącego czasu lub wartość czasu przechowywaną w strukturze.|  
  
> [!NOTE]
>  We wszystkich wersjach systemu Microsoft C/C++ z wyjątkiem Microsoft C/C++ version 7.0 i we wszystkich wersjach programu Visual C++ funkcja czasu zwraca bieżącą godzinę jako liczbę sekund, jaka upłynęła od północy na 1 stycznia 1970. W programie Microsoft C/C++ version 7.0 `time` zwrócił bieżącą godzinę jako liczbę sekund, jaka upłynęła od północy na 31 grudnia 1899.  
  
> [!NOTE]
>  W wersjach programu Visual C++ i Microsoft C/C++ przed Visual C++ 2005 `time_t` został `long int` (32-bitowy) i dlatego nie może zostać użyty dla dat poza 3:14:07 19 stycznia 2038 r., UTC. `time_t`teraz jest odpowiednikiem `__time64_t` przez domyślny, ale definiowanie `_USE_32BIT_TIME_T` zmiany `time_t` do `__time32_t` i wymusza wiele czasu funkcji do wywołania wersje, które przyjmują 32-bitową `time_t`. Aby uzyskać więcej informacji, zobacz [standardowych typów](../c-runtime-library/standard-types.md) i komentarze w dokumentacji dotyczącej funkcji czasu.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)