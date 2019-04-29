---
title: asctime_s, _wasctime_s
ms.date: 11/04/2016
apiname:
- _wasctime_s
- asctime_s
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
- asctime_s
- _wasctime_s
- _tasctime_s
helpviewer_keywords:
- tasctime_s function
- _tasctime_s function
- time structure conversion
- wasctime_s function
- time, converting
- _wasctime_s function
- asctime_s function
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
ms.openlocfilehash: 350d8c7b1dcf61272a3cfee884dff8a63b455f1c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349478"
---
# <a name="asctimes-wasctimes"></a>asctime_s, _wasctime_s

Konwertuj **tm** czasu struktury do ciągu znaków. Te funkcje są wersjami [asctime —, _wasctime —](asctime-wasctime.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t asctime_s(
   char* buffer,
   size_t numberOfElements,
   const struct tm *tmSource
);
errno_t _wasctime_s(
   wchar_t* buffer,
   size_t numberOfElements
   const struct tm *tmSource
);
template <size_t size>
errno_t asctime_s(
   char (&buffer)[size],
   const struct tm *tmSource
); // C++ only
template <size_t size>
errno_t _wasctime_s(
   wchar_t (&buffer)[size],
   const struct tm *tmSource
); // C++ only
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Wskaźnik do buforu do przechowywania wynikowy ciąg znaków. Ta funkcja zakłada wskaźnik do lokalizacji w pamięci prawidłowe o rozmiarze określonym przez *numberOfElements*.

*numberOfElements*<br/>
Rozmiar buforu używany do przechowywania wyników.

*tmSource*<br/>
Daty/godziny struktury. Ta funkcja przyjęto założenie, wskaźnik do prawidłowego **struktury** **tm** obiektu.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie. Jeśli wystąpi awaria, program obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, wartość zwracana jest kod błędu. Kody błędów są definiowane w numer błędu. H. Aby uzyskać więcej informacji, zobacz [errno — stałe](../../c-runtime-library/errno-constants.md). W poniższej tabeli przedstawiono faktyczne kody błędów zwracane dla poszczególnych warunków wystąpienia błędu.

### <a name="error-conditions"></a>Warunki błędów

|*buffer*|*numberOfElements*|*tmSource*|Wróć|Wartość w *buforu*|
|--------------|------------------------|----------|------------|-----------------------|
|**NULL**|Dowolne|Dowolne|**EINVAL**|Nie zmodyfikowano|
|Nie **NULL** (wskazuje prawidłowy pamięci)|0|Dowolne|**EINVAL**|Nie zmodyfikowano|
|Nie **o wartości NULL**|0 < < 26 rozmiar|Dowolne|**EINVAL**|Pusty ciąg|
|Nie **o wartości NULL**|>= 26|**NULL**|**EINVAL**|Pusty ciąg|
|Nie **o wartości NULL**|>= 26|Nieprawidłowa godzina struktury lub wartości spoza zakresu dla składników czasu|**EINVAL**|Pusty ciąg|

> [!NOTE]
> Błąd warunki dla **wasctime_s —** są podobne do **asctime_s —** z wyjątkiem, że limit rozmiaru jest mierzony w słowach.

## <a name="remarks"></a>Uwagi

**Asctime —** funkcja konwertuje czas przechowywane jako struktura do ciągu znaków. *TmSource* wartość zwykle jest uzyskiwana w wyniku wywołania **gmtime** lub **localtime**. Obu tych funkcji można wypełnić **tm** struktury, zgodnie z definicją w czasie. H.

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

Ciąg przekonwertowany znak również jest dostosowywany zgodnie z ustawieniami strefy czasu lokalnego. Zobacz [czasu, _time32 —, _time64](time-time32-time64.md), [_ftime _ftime32, _ftime64](ftime-ftime32-ftime64.md), i [localtime_s —, _localtime32_s —, _localtime64_s —](localtime-s-localtime32-s-localtime64-s.md) funkcji dla informacji o konfigurowaniu czas lokalny i [_tzset —](tzset.md) funkcji dla informacji na temat definiowania środowiska strefy czasowej i zmienne globalne.

Wynikowy ciąg utworzony przez **asctime_s —** zawiera dokładnie 26 znaków i ma postać `Wed Jan 02 02:03:55 1980\n\0`. Używany jest zegar 24-godzinny. Wszystkie pola są stałej szerokości. Znak nowego wiersza i znak null zajmują się dwie ostatnie pozycje ciągu. Wartości przekazanej w jako drugi parametr powinien wynosić co najmniej tak dużego. Jeśli jest mniej kodu błędu, **EINVAL**, zostaną zwrócone.

**_wasctime_s —** to wersja znaku dwubajtowego **asctime_s —**. **_wasctime_s —** i **asctime_s —** zachowują się identycznie.

### <a name="generic-text-routine-mapping"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s**|**asctime_s**|**asctime_s**|**_wasctime_s**|

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**asctime_s**|\<time.h>|
|**_wasctime_s**|\<Time.h > lub \<wchar.h >|

## <a name="security"></a>Zabezpieczenia

Jeśli wskaźnik bufor nie jest **NULL** i wskaźnik nie wskazuje prawidłowego buforu, funkcja spowoduje zastąpienie, niezależnie od rodzaju znajduje się w lokalizacji. Może to również spowodować naruszenie zasad dostępu.

A [przepełnienie buforu](/windows/desktop/SecBP/avoiding-buffer-overruns) może wystąpić, jeśli rozmiar przekazanego argumentu jest większa niż rzeczywisty rozmiar buforu.

## <a name="example"></a>Przykład

Ten program umieszcza czas systemowy w długich liczb całkowitych **aclock**, przekształca je w strukturze **newtime** i konwertuje je do postaci ciągu dla danych wyjściowych, przy użyciu **asctime_s —** funkcji.

```C
// crt_asctime_s.c
#include <time.h>
#include <stdio.h>

struct tm newtime;
__time32_t aclock;

int main( void )
{
   char buffer[32];
   errno_t errNum;
   _time32( &aclock );   // Get time in seconds.
   _localtime32_s( &newtime, &aclock );   // Convert time to struct tm form.

   // Print local time as a string.

   errNum = asctime_s(buffer, 32, &newtime);
   if (errNum)
   {
       printf("Error code: %d", (int)errNum);
       return 1;
   }
   printf( "Current date and time: %s", buffer );
   return 0;
}
```

```Output
Current date and time: Wed May 14 15:30:17 2003
```

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
