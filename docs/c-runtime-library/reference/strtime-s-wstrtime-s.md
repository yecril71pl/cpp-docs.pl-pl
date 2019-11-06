---
title: _strtime_s, _wstrtime_s
ms.date: 11/04/2016
api_name:
- _wstrtime_s
- _strtime_s
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: c74e7359f68469fd8322ba1c9348acffd636282a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625919"
---
# <a name="_strtime_s-_wstrtime_s"></a>_strtime_s, _wstrtime_s

Skopiuj bieżący czas do buforu. Są to wersje [_strtime, _wstrtime](strtime-wstrtime.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*buforu*<br/>
Bufor o długości co najmniej 10 bajtów, gdzie zostanie zapisany czas.

*numberOfElements*<br/>
Rozmiar buforu.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli powodzenie.

Jeśli wystąpi błąd, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Wartość zwracana jest kodem błędu w przypadku wystąpienia błędu. Kody błędów są zdefiniowane w ERRNO. C w poniższej tabeli przedstawiono dokładne błędy wygenerowane przez tę funkcję. Aby uzyskać więcej informacji na temat kodów błędów, zobacz [errno — stałe](../../c-runtime-library/errno-constants.md).

### <a name="error-conditions"></a>Warunki błędów

|*buforu*|*numberOfElements*|przesłać|Zawartość *buforu*|
|--------------|------------------------|------------|--------------------------|
|**NULL**|ile|**EINVAL**|nie zmodyfikowano|
|Nie **ma wartości null** (wskazuje na prawidłowy bufor)|0|**EINVAL**|nie zmodyfikowano|
|Nie **ma wartości null** (wskazuje na prawidłowy bufor)|0 < rozmiar < 9|**EINVAL**|Pusty ciąg|
|Nie **ma wartości null** (wskazuje na prawidłowy bufor)|Rozmiar > 9|0|Bieżący czas sformatowany zgodnie z opisem w uwagach|

## <a name="security-issues"></a>Problemy dotyczące zabezpieczeń

Przekazanie nieprawidłowej wartości innej niż**null** dla buforu spowoduje naruszenie zasad dostępu, jeśli parametr *NumberOfElements* jest większy niż 9.

Przekazywanie wartości dla *NumberOfElements* , która jest większa niż rzeczywisty rozmiar buforu, spowoduje przepełnienie buforu.

## <a name="remarks"></a>Uwagi

Te funkcje zapewniają bezpieczniejsze wersje [_strtime](strtime-wstrtime.md) i [_wstrtime](strtime-wstrtime.md). Funkcja **_strtime_s** Kopiuje bieżący czas lokalny do buforu wskazywanym przez *timestr*. Godzina jest formatowana jako **hh: mm: SS** , gdzie **hh** ma dwie cyfry reprezentujące godzinę w notacji 24-godzinnej, **mm** to dwie cyfry reprezentujące minuty poza godzinę, a **SS** to dwie cyfry reprezentujące sekundy. Na przykład ciąg **18:23:44** reprezentuje 23 minuty i 44 s ostatnich 6 godzin Długość buforu musi wynosić co najmniej 9 bajtów; rzeczywisty rozmiar jest określany przez drugi parametr.

**_wstrtime** to dwubajtowa wersja **_strtime**; argument i wartość zwracana przez **_wstrtime** są ciągami znaków dwubajtowych. Funkcje te zachowują się identycznie w inny sposób.

W C++programie korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując konieczność określenia argumentu rozmiaru) i mogą automatycznie zastąpić starsze, niezabezpieczone funkcje z ich nowszymi, bezpiecznymi odpowiednikami. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mapping"></a>Mapowanie procedury tekstu ogólnego:

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime_s**|**_strtime_s**|**_strtime_s**|**_wstrtime_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strtime_s**|\<time. h >|
|**_wstrtime_s**|\<Time. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
