---
title: asctime_s, _wasctime_s
ms.date: 4/2/2020
api_name:
- _wasctime_s
- asctime_s
- _o__wasctime_s
- _o_asctime_s
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
ms.openlocfilehash: 529663a8c36a1b934a4dd99852aee19fb1a1e6e6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217015"
---
# <a name="asctime_s-_wasctime_s"></a>asctime_s, _wasctime_s

Konwertuj strukturę czasu **TM** na ciąg znaków. Te funkcje są wersjami [asctime, _wasctime](asctime-wasctime.md) z ulepszonymi zabezpieczeniami, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*buforu*<br/>
Wskaźnik do buforu do przechowywania wyniku ciągu znaków. Ta funkcja przyjmuje wskaźnik do prawidłowej lokalizacji w pamięci o rozmiarze określonym przez *NumberOfElements*.

*numberOfElements*<br/>
Rozmiar buforu używany do przechowywania wyniku.

*tmSource*<br/>
Struktura czasu/daty. Ta funkcja przyjmuje wskaźnik do prawidłowego **`struct`** obiektu **TM** .

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli powodzenie. Jeśli wystąpi awaria, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, zwracaną wartością jest kod błędu. Kody błędów są zdefiniowane w ERRNO. C. Aby uzyskać więcej informacji, zobacz [errno stałe](../../c-runtime-library/errno-constants.md). W poniższej tabeli przedstawiono rzeczywiste kody błędów zwracane dla każdego warunku błędu.

### <a name="error-conditions"></a>Warunki błędów

|*buforu*|*numberOfElements*|*tmSource*|Przesłać|Wartość w *buforze*|
|--------------|------------------------|----------|------------|-----------------------|
|**NULL**|Dowolne|Dowolne|**EINVAL**|Nie zmodyfikowano|
|Nie **ma wartości null** (wskazuje na prawidłową pamięć)|0|Dowolne|**EINVAL**|Nie zmodyfikowano|
|Nie **ma wartości null**|0< rozmiar < 26|Dowolne|**EINVAL**|Pusty ciąg|
|Nie **ma wartości null**|>= 26|**NULL**|**EINVAL**|Pusty ciąg|
|Nie **ma wartości null**|>= 26|Nieprawidłowa struktura czasu lub wartości spoza zakresu dla składników czasu|**EINVAL**|Pusty ciąg|

> [!NOTE]
> Warunki błędów dla **wasctime_s** są podobne do **asctime_s** z wyjątkiem tego, że limit rozmiaru jest mierzony w wyrazach.

## <a name="remarks"></a>Uwagi

Funkcja **asctime** konwertuje godzinę przechowywaną jako strukturę do ciągu znaków. Wartość *tmSource* jest zazwyczaj uzyskiwana z wywołania **gmtime** lub **localtime**. Obie funkcje mogą służyć do wypełnienia struktury **TM** zgodnie z definicją w czasie. C.

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

Przekonwertowany ciąg znaków jest również dostosowywany zgodnie z ustawieniami lokalnej strefy czasowej. Zapoznaj się [z funkcjami](tzset.md) [Time, _time32, _time64](time-time32-time64.md), [_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)i localtime_s, _localtime32_s [, _localtime64_s,](localtime-s-localtime32-s-localtime64-s.md) Aby uzyskać informacje na temat konfigurowania środowiska strefy czasowej i zmiennych globalnych.

Wynik ciągu utworzony przez **asctime_s** zawiera dokładnie 26 znaków i ma postać `Wed Jan 02 02:03:55 1980\n\0` . Używany jest zegar 24-godzinny. Wszystkie pola mają stałą szerokość. Nowy znak linii i znak null zajmują ostatnie dwa pozycje ciągu. Wartość, która została przeniesiona jako drugi parametr, musi mieć co najmniej wartość Big. Jeśli jest mniejsza, zostanie zwrócony kod błędu, **EINVAL**.

**_wasctime_s** to dwubajtowa wersja **asctime_s**. **_wasctime_s** i **asctime_s** zachowują się identycznie w inny sposób.

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Mapowanie procedury tekstu ogólnego

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s**|**asctime_s**|**asctime_s**|**_wasctime_s**|

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość buforu, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**asctime_s**|\<time.h>|
|**_wasctime_s**|\<time.h> lub \<wchar.h>|

## <a name="security"></a>Zabezpieczenia

Jeśli wskaźnik buforu ma wartość inną niż **null** , a wskaźnik nie wskazuje prawidłowego buforu, funkcja zostanie zastąpiona, niezależnie od lokalizacji. Może to również spowodować naruszenie zasad dostępu.

[Przepełnienie buforu](/windows/win32/SecBP/avoiding-buffer-overruns) może wystąpić, jeśli długość argumentu rozmiaru przebiegła jest większa niż rzeczywisty rozmiar buforu.

## <a name="example"></a>Przykład

Ten program umieszcza czas systemowy w **aclockej**liczbie całkowitej, tłumaczy je na strukturę **newtime** , a następnie konwertuje ją na postać ciągu dla danych wyjściowych przy użyciu funkcji **asctime_s** .

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
