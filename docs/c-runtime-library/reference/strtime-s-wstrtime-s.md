---
title: _strtime_s, _wstrtime_s
ms.date: 11/04/2016
apiname:
- _wstrtime_s
- _strtime_s
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
- _wstrtime_s
- strtime_s
- wstrtime_s
- _strtime_s
helpviewer_keywords:
- wstrtime_s function
- copying time to buffers
- strtime_s function
- _wstrtime_s function
- time, copying
- _strtime_s function
ms.assetid: 42acf013-c334-485d-b610-84c0af8a46ec
ms.openlocfilehash: 579c4a99b52c66bd14cea947eaa1f301cc1127e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642367"
---
# <a name="strtimes-wstrtimes"></a>_strtime_s, _wstrtime_s

Skopiuj bieżącą godzinę do buforu. Są to wersje [_strtime —, _wstrtime —](strtime-wstrtime.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _strtime_s(
   char *buffer,
   size_t numberOfElements
);
errno_t _wstrtime_s(
   wchar_t *buffer,
   size_t numberOfElements
);
template <size_t size>
errno_t _strtime_s(
   char (&buffer)[size]
); // C++ only
template <size_t size>
errno_t _wstrtime_s(
   wchar_t (&buffer)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Bufor, co najmniej 10 bajtów, gdzie zostanie zapisany czas.

*numberOfElements*<br/>
Rozmiar buforu.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie.

Jeśli wystąpi błąd, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Wartość zwracana jest kod błędu, jeśli wystąpi awaria. Kody błędów są definiowane w numer błędu. GODZ.; Zobacz w poniższej tabeli dokładnie błędy generowane przez tę funkcję. Aby uzyskać więcej informacji o kodach błędów, zobacz [errno — stałe](../../c-runtime-library/errno-constants.md).

### <a name="error-conditions"></a>Warunki błędów

|*buffer*|*numberOfElements*|Wróć|Zawartość *buforu*|
|--------------|------------------------|------------|--------------------------|
|**NULL**|(wszystkie)|**EINVAL**|Nie zmodyfikowano|
|Nie **NULL** (kierujący do prawidłowego buforu)|0|**EINVAL**|Nie zmodyfikowano|
|Nie **NULL** (kierujący do prawidłowego buforu)|0 < rozmiar < 9|**EINVAL**|Pusty ciąg|
|Nie **NULL** (kierujący do prawidłowego buforu)|Rozmiar > 9|0|Bieżąca godzina w formacie określonym w uwagi|

## <a name="security-issues"></a>Problemy dotyczące zabezpieczeń

Przekazywanie nieprawidłowy non -**NULL** wartość dla buforu spowoduje powoduje naruszenie zasad dostępu, jeśli *numberOfElements* parametr jest większe niż 9.

Przekazywanie wartości dla *numberOfElements* jest większa niż rzeczywisty rozmiar buforu spowoduje przepełnienie buforu.

## <a name="remarks"></a>Uwagi

Te funkcje zapewniają bardziej bezpieczne wersje [_strtime —](strtime-wstrtime.md) i [_wstrtime —](strtime-wstrtime.md). **_Strtime_s —** funkcja kopiuje bieżący czas lokalny do bufor wskazywany przez *timestr*. Czas jest w formacie **: mm: ss** gdzie **hh** to dwie cyfry reprezentująca godzinę w 24-godzinnego **mm** to dwie cyfry reprezentujący minut po pełnej godziny i **ss** to dwie cyfry reprezentujący sekund. Na przykład ciąg **18:23:44** reprezentuje 23 minuty i 44 sekund po pełnej godzinie 6 Rozmiar buforu musi wynosić co najmniej 9 bajtów długie. Rzeczywisty rozmiar jest określony przez drugi parametr.

**_wstrtime —** to wersja znaku dwubajtowego **_strtime —**; argument i wartość zwracana przez **_wstrtime —** są ciągami znaków dwubajtowych. Funkcje te zachowują się identycznie.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując potrzebę określenia argumentu rozmiaru) oraz ich mogą automatycznie zastąpić starsze, niezabezpieczone funkcje ich nowsze, bezpieczne odpowiedniki. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mapping"></a>Mapowania procedur zwykłego tekstu:

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime_s**|**_strtime_s**|**_strtime_s**|**_wstrtime_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strtime_s**|\<time.h>|
|**_wstrtime_s**|\<Time.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// strtime_s.c

#include <time.h>
#include <stdio.h>

int main()
{
    char tmpbuf[9];
    errno_t err;

    // Set time zone from TZ environment variable. If TZ is not set,
    // the operating system is queried to obtain the default value
    // for the variable.
    //
    _tzset();

    // Display operating system-style date and time.
    err = _strtime_s( tmpbuf, 9 );
    if (err)
    {
       printf("_strdate_s failed due to an invalid argument.");
      exit(1);
    }
    printf( "OS time:\t\t\t\t%s\n", tmpbuf );
    err = _strdate_s( tmpbuf, 9 );
    if (err)
    {
       printf("_strdate_s failed due to an invalid argument.");
       exit(1);
    }
    printf( "OS date:\t\t\t\t%s\n", tmpbuf );

}
```

```Output
OS time:            14:37:49
OS date:            04/25/03
```

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
