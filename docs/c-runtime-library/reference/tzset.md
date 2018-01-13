---
title: "_tzset — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _tzset
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
f1_keywords: _tzset
dev_langs: C++
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f103da7ca67721f6c654c593746b9427954c6930
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tzset"></a>_tzset
Ustawia czas zmiennych środowiskowych.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
void _tzset( void );  
```  
  
## <a name="remarks"></a>Uwagi  
 `_tzset` Funkcja używa bieżące ustawienie zmiennej środowiskowej `TZ` można przypisać wartości do trzy zmienne globalne: `_daylight`, `_timezone`, i `_tzname`. Te zmienne są używane przez [_ftime —](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) i [konwersję](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) funkcji, aby wprowadzić poprawki z uniwersalnego czasu koordynowanego (UTC), do czasu lokalnego, a w `time` funkcji do obliczenia UTC z systemu czas. Użyj następującej składni, aby ustawić `TZ` zmiennej środowiskowej:  
  
 `set` `TZ`=`tzn`[+ &#124; -]`hh`[`:mm`[`:ss`] ][`dzn`]  
  
 `tzn`  
 Nazwa strefy czasowej trzyliterowy, takich jak PST. Należy określić prawidłowe przesunięcie od lokalnego czasu na czas UTC.  
  
 `hh`  
 Różnica w godzinach między czasem UTC i czasem lokalnym. Znak (+) opcjonalny w przypadku wartości dodatnie.  
  
 `mm`  
 Minut. Oddzielona od `hh` dwukropkiem (`:`).  
  
 `ss`  
 Liczba sekund. Oddzielona od `mm` dwukropkiem (`:`).  
  
 `dzn`  
 Strefa zmiany czasu trzyliterowy, takich jak PDT. Jeśli czasu letniego, nigdy nie są włączone w tej lokalizacji, ustaw `TZ` bez wartości dla `dzn`. Biblioteki wykonawcze języka C zakłada Stanów Zjednoczonych zasady wykonywania obliczenia czasu (DST).  
  
> [!NOTE]
>  Należy ostrożnie znak odstęp czasu przetwarzania. Ponieważ odstęp czasu jest przesunięcie od lokalnego czasu UTC (a nie odwrotnie), jego logowania może być przeciwieństwem może intuicyjnie oczekiwań. Dla stref czasowych wcześniejsze UTC odstęp czasu jest ujemna dla tych za UTC różnica jest dodatnia.  
  
 Na przykład, aby ustawić `TZ` zmiennej środowiskowej odpowiadają bieżącej strefy czasowej w Niemczech, wprowadź następujące polecenie w wierszu polecenia:  
  
```  
set TZ=GST-1GDT  
```  
  
 To polecenie używa GST, aby wskazać, niemiecki (czas standardowy), zakłada, że UTC godzinę za Niemcy (lub innymi słowy, które Niemcy to jedna godzina wcześniejsze UTC). przyjęto założenie, że Niemcy przestrzega czasu letniego —.  
  
 Jeśli `TZ` wartość nie jest ustawiona, `_tzset` próbuje użyć informacji o strefie czasowej określonej przez system operacyjny. W systemie operacyjnym Windows te informacje jest określona w aplikacji daty/godziny w Panelu sterowania. Jeśli `_tzset` nie może uzyskać te informacje PST8PDT używa domyślnie, co wskazuje na strefę czasową Pacyfiku.  
  
 Na podstawie `TZ` wartości zmiennej środowiskowej następujące wartości są przypisane do zmiennych globalnych `_daylight`, `_timezone`, i `_tzname` podczas `_tzset` nosi nazwę:  
  
|Zmienna globalna|Opis|Wartość domyślna|  
|---------------------|-----------------|-------------------|  
|`_daylight`|Wartość niezerowa, jeśli strefa zmiany czasu został określony w `TZ` ustawienie; w przeciwnym razie wartość 0.|1|  
|`_timezone`|Różnica w sekundach między czasem lokalnym i w formacie UTC.|28800 (28800 sekund równa 8 godzin)|  
|`_tzname`[0]|Wartość Nazwa strefy czasowej z ciągu `TZ` zmiennej środowiskowej; Jeśli pusty `TZ` nie została ustawiona.|PST|  
|`_tzname`[1]|Wartość ciągu strefy zmiany czasu; pusty w przypadku pominięcia strefy zmiany czasu z `TZ` zmiennej środowiskowej.|PDT|  
  
 Domyślne wartości widoczne w tej tabeli `_daylight` i `_tzname` tablicy odpowiadają "PST8PDT." W przypadku pominięcia strefy czasu letniego z `TZ` zmiennej środowiskowej, wartość `_daylight` 0 i `_ftime`, `gmtime`, i `localtime` zwracają wartość 0 dla ich flag czasu letniego.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_tzset`|\<Time.h >|  
  
 Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
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
 [Zarządzanie czasem](../../c-runtime-library/time-management.md)   
 [asctime —, _wasctime —](../../c-runtime-library/reference/asctime-wasctime.md)   
 [_ftime —, _ftime32 —, _ftime64 —](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime —, _gmtime32 —, _gmtime64 —](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [czas lokalny, _localtime32 —, _localtime64 —](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [czas, _time32 —, _time64 —](../../c-runtime-library/reference/time-time32-time64.md)   
 [_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](../../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)