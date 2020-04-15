---
title: _strdate, _wstrdate
ms.date: 4/2/2020
api_name:
- _strdate
- _wstrdate
- _o__strdate
- _o__wstrdate
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
- _tstrdate
- wstrdate
- _wstrdate
- _strdate
- strdate
helpviewer_keywords:
- strdate function
- dates, copying
- tstrdate function
- _wstrdate function
- wstrdate function
- _strdate function
- _tstrdate function
- copying dates
ms.assetid: de8e4097-58f8-42ba-9dcd-cb4d9a9f1696
ms.openlocfilehash: 9b4b6d3b81dd1dda968cc42448ab2e53bdd44433
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361280"
---
# <a name="_strdate-_wstrdate"></a>_strdate, _wstrdate

Skopiuj bieżącą datę systemową do buforu. Dostępne są bezpieczniejsze wersje tych funkcji; patrz [_strdate_s, _wstrdate_s](strdate-s-wstrdate-s.md).

## <a name="syntax"></a>Składnia

```C
char *_strdate(
   char *datestr
);
wchar_t *_wstrdate(
   wchar_t *datestr
);
template <size_t size>
char *_strdate(
   char (&datestr)[size]
); // C++ only
template <size_t size>
wchar_t *_wstrdate(
   wchar_t (&datestr)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*datestr*<br/>
Wskaźnik do buforu zawierającego sformatowany ciąg daty.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do wynikowego ciągu znaku *datestr*.

## <a name="remarks"></a>Uwagi

Dostępne są bezpieczniejsze wersje tych funkcji; patrz [_strdate_s, _wstrdate_s](strdate-s-wstrdate-s.md). Zaleca się, aby w miarę możliwości używać bezpieczniejszych funkcji.

Funkcja **_strdate** kopiuje bieżącą datę systemową do buforu wskazytego przez *datestr*, sformatowany **mm**/**dd**/**yy**, gdzie **mm** jest dwiema cyframi reprezentującymi miesiąc, **dd** to dwie cyfry reprezentujące dzień, a **yy** to dwie ostatnie cyfry roku. Na przykład ciąg **12/05/99** reprezentuje 5 grudnia 1999. Bufor musi mieć długość co najmniej 9 bajtów.

Jeśli *datestr* jest wskaźnikiem **NULL,** wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w programie [Sprawdzanie poprawności parametru.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te funkcje zwracają -1 i ustawić **errno** na **EINVAL**.

**_wstrdate** jest szerokoznakową wersją **_strdate**; argument i zwraca wartość **_wstrdate** są ciągami znaków o szerokich znakach. Te funkcje zachowują się identycznie w przeciwnym razie.

W języku C++ te funkcje mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate**|**_strdate**|**_strdate**|**_wstrdate**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strdate**|\<> time.h|
|**_wstrdate**|\<time.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// strdate.c
// compile with: /W3
#include <time.h>
#include <stdio.h>
int main()
{
    char tmpbuf[9];

    // Set time zone from TZ environment variable. If TZ is not set,
    // the operating system is queried to obtain the default value
    // for the variable.
    //
    _tzset();

    printf( "OS date: %s\n", _strdate(tmpbuf) ); // C4996
    // Note: _strdate is deprecated; consider using _strdate_s instead
}
```

```Output
OS date: 04/25/03
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
