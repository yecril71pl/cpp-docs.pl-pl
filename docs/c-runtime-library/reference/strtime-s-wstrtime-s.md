---
title: _strtime_s, _wstrtime_s
ms.date: 4/2/2020
api_name:
- _wstrtime_s
- _strtime_s
- _o__strtime_s
- _o__wstrtime_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 771dfdb6bd8035fe8683d62d52b3b4980ecda215
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316935"
---
# <a name="_strtime_s-_wstrtime_s"></a>_strtime_s, _wstrtime_s

Skopiuj bieżący czas do buforu. Są to wersje [_strtime, _wstrtime](strtime-wstrtime.md) z ulepszeniami zabezpieczeń, jak opisano w [programie Funkcje zabezpieczeń w programie CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Buforu*<br/>
Bufor o długości co najmniej 10 bajtów, w którym zostanie zapisany czas.

*liczbaOfElements*<br/>
Rozmiar buforu.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie.

Jeśli wystąpi warunek błędu, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [obszarze Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Zwracana wartość jest kodem błędu w przypadku wystąpienia błędu. Kody błędów są zdefiniowane w ERRNO. H; zobacz poniższą tabelę dokładnych błędów generowanych przez tę funkcję. Aby uzyskać więcej informacji na temat kodów [błędów, zobacz errno Constants](../../c-runtime-library/errno-constants.md).

### <a name="error-conditions"></a>Warunki błędu

|*Buforu*|*liczbaOfElements*|Zwraca|Zawartość *buforu*|
|--------------|------------------------|------------|--------------------------|
|**Null**|(dowolny)|**Einval**|Nie zmodyfikowano|
|Nie **NULL** (wskażając prawidłowy bufor)|0|**Einval**|Nie zmodyfikowano|
|Nie **NULL** (wskażając prawidłowy bufor)|0 < rozmiar < 9|**Einval**|Pusty ciąg znaków|
|Nie **NULL** (wskażając prawidłowy bufor)|Rozmiar > 9|0|Bieżący czas sformatowany zgodnie z uwagami|

## <a name="security-issues"></a>Problemy z zabezpieczeniami

Przekazywanie nieprawidłowej wartości**innej niż NULL** dla buforu spowoduje naruszenie zasad dostępu, jeśli parametr *numberOfElements* jest większy niż 9.

Przekazywanie wartości *numberOfElements,* która jest większa niż rzeczywisty rozmiar buforu spowoduje przepełnienie buforu.

## <a name="remarks"></a>Uwagi

Funkcje te zapewniają bezpieczniejsze wersje [_strtime](strtime-wstrtime.md) i [_wstrtime.](strtime-wstrtime.md) Funkcja **_strtime_s** kopiuje bieżący czas lokalny do buforu wskazanego przez *timestr*. Czas jest formatowany jako **hh:mm:ss** gdzie **hh** jest dwiema cyframi reprezentującymi godzinę w notacji 24-godzinnej, **mm** to dwie cyfry reprezentujące minuty po godzinie, a **ss** to dwie cyfry reprezentujące sekundy. Na przykład ciąg **18:23:44** reprezentuje 23 minut i 44 sekundy po 18:00. Bufor musi mieć długość co najmniej 9 bajtów; rzeczywisty rozmiar jest określony przez drugi parametr.

**_wstrtime** jest szerokoznakową wersją **_strtime;** argument i zwraca wartość **_wstrtime** są ciągami znaków o szerokich znakach. Te funkcje zachowują się identycznie w przeciwnym razie.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia można wywnioskować długość buforu automatycznie (eliminując konieczność określenia argumentu rozmiaru) i mogą automatycznie zastąpić starsze, niezabezpieczone funkcje z ich nowszych, bezpiecznych odpowiedników. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Rutynowe mapowanie tekstu ogólnego:

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime_s**|**_strtime_s**|**_strtime_s**|**_wstrtime_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strtime_s**|\<> time.h|
|**_wstrtime_s**|\<time.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
