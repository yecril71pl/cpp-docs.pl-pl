---
title: _create_locale, _wcreate_locale
ms.date: 4/2/2020
api_name:
- _create_locale
- __create_locale
- _wcreate_locale
- _o__create_locale
- _o__wcreate_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- create_locale
- _create_locale
- __create_locale
helpviewer_keywords:
- locales, creating
- _create_locale function
- create_locale function
- __create_locale function
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
ms.openlocfilehash: 31bde3d032bdb47d63db5730ba53016de573332c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912091"
---
# <a name="_create_locale-_wcreate_locale"></a>_create_locale, _wcreate_locale

Tworzy obiekt ustawień regionalnych.

## <a name="syntax"></a>Składnia

```C
_locale_t _create_locale(
   int category,
   const char *locale
);
_locale_t _wcreate_locale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>Parametry

*kategorii*<br/>
Kategorii.

*locale*<br/>
Specyfikator ustawień regionalnych.

## <a name="return-value"></a>Wartość zwracana

Jeśli podano prawidłowe ustawienia *regionalne* i *Kategorie* , program zwraca określone ustawienia regionalne jako obiekt **_locale_t** . Bieżące ustawienia regionalne programu nie są zmieniane.

## <a name="remarks"></a>Uwagi

Funkcja **_create_locale** umożliwia utworzenie obiektu, który reprezentuje określone ustawienia specyficzne dla regionu, do użycia w wersjach specyficznych dla ustawień regionalnych wielu funkcji CRT (funkcje z sufiksem **_l** ). Zachowanie jest podobne do **setlocaling**, z tą różnicą, że zamiast zastosowania określonych ustawień regionalnych do bieżącego środowiska, te ustawienia są zapisywane w strukturze **_locale_t** , która jest zwracana. Strukturę **_locale_t** należy zwolnić przy użyciu [_free_locale](free-locale.md) , gdy nie jest już potrzebne.

**_wcreate_locale** to dwubajtowa wersja **_create_locale**; argument *locale* **_wcreate_locale** jest ciągiem znaków dwubajtowych. **_wcreate_locale** i **_create_locale** zachowują się identycznie w inny sposób.

Argument *kategorii* określa części zachowań specyficznych dla ustawień regionalnych, których dotyczy problem. Flagi używane dla *kategorii* i części programu, których one dotyczą, są przedstawione w poniższej tabeli:

| Flaga *kategorii* | Mową |
|-----------------|---------|
| **LC_ALL** |Wszystkie kategorie, jak wymieniono poniżej. |
| **LC_COLLATE** |Funkcje **strcoll —**, **_stricoll**, **wcscoll**, **_wcsicoll**, **strxfrm**, **_strncoll**, **_strnicoll**, **_wcsncoll**, **_wcsnicoll**i **wcsxfrm** . |
| **LC_CTYPE** | Funkcje obsługi znaków (z wyjątkiem **iscyfr**, **isxdigit**, **mbstowcs**i **mbtowc**, których nie dotyczy). |
| **LC_MONETARY** | Informacje o formatowaniu pieniężnym zwracane przez funkcję **localeconv** . |
| **LC_NUMERIC** | Znak dziesiętny dla sformatowanych procedur danych wyjściowych (takich jak **printf**), dla procedur konwersji danych i dla niepieniężnych informacji o formatowaniu zwracanych przez **localeconv**. Oprócz znaku dziesiętnego, **LC_NUMERIC** ustawia separator tysięcy i ciąg sterujący grupowania zwracanego przez [localeconv](localeconv.md). |
| **LC_TIME** | Funkcje **strftime** i **wcsftime** . |

Ta funkcja sprawdza poprawność *kategorii* i parametrów *ustawień regionalnych* . Jeśli parametr kategorii nie jest jedną z wartości podanej w poprzedniej tabeli lub jeśli *Ustawienia regionalne* mają **wartość null**, funkcja zwróci **wartość null**.

Argument *locale* jest wskaźnikiem do ciągu, który określa ustawienia regionalne. Aby uzyskać informacje na temat formatu argumentu *ustawień regionalnych* , zobacz [nazwy ustawień regionalnych, Języki i ciągi kraj/region](../../c-runtime-library/locale-names-languages-and-country-region-strings.md).

Argument *locale* może przyjmować nazwę ustawień regionalnych, ciąg języka, ciąg języka i kod kraju/regionu, stronę kodową lub ciąg języka, kod kraju/regionu i stronę kodową. Zestaw dostępnych nazw ustawień regionalnych, języków, kodów krajów/regionów i stron kodowych zawiera wszystkie, które są obsługiwane przez NLS API systemu Windows. Zestaw nazw ustawień regionalnych obsługiwanych przez **_create_locale** są opisane w temacie [nazwy regionalne, Języki i ciągi kraj/region](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Zestaw ciągów języka i kraju/regionu obsługiwanych przez **_create_locale** są wymienione w [ciągach języka](../../c-runtime-library/language-strings.md) i w [ciągach kraju/regionu](../../c-runtime-library/country-region-strings.md).

Aby uzyskać więcej informacji na temat ustawień regionalnych, zobacz [setlocals, _wsetlocale](setlocale-wsetlocale.md).

Poprzednia nazwa tej funkcji, **__create_locale** (z dwoma podkreśleniami wiodącymi), jest przestarzała.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_create_locale**|\<locale. h>|
|**_wcreate_locale**|\<locale. h> \<lub WCHAR. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_create_locale.c
// Sets the current locale to "de-CH" using the
// setlocale function and demonstrates its effect on the strftime
// function.

#include <stdio.h>
#include <locale.h>
#include <time.h>

int main(void)
{
    time_t ltime;
    struct tm thetime;
    unsigned char str[100];
    _locale_t locale;

    // Create a locale object representing the German (Switzerland) locale
    locale = _create_locale(LC_ALL, "de-CH");
    time (&ltime);
    _gmtime64_s(&thetime, &ltime);

    // %#x is the long date representation, appropriate to
    // the current locale
    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In de-CH locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);

    // Create a locale object representing the default C locale
    locale = _create_locale(LC_ALL, "C");
    time(&ltime);
    _gmtime64_s(&thetime, &ltime);

    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In 'C' locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);
}
```

```Output
In de-CH locale, _strftime_l returns 'Samstag, 9. Februar 2002'
In 'C' locale, _strftime_l returns 'Saturday, February 09, 2002'
```

## <a name="see-also"></a>Zobacz też

[Nazwy lokalne, Języki i ciągi kraj/region](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Ciągi języka](../../c-runtime-library/language-strings.md)<br/>
[Ciągi kraju/regionu](../../c-runtime-library/country-region-strings.md)<br/>
[_free_locale](free-locale.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[Ustawienie](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strcoll — Funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
