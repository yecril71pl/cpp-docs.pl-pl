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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 611eaf342776b9a0f57c4f55c52a841c3fd13fb5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348251"
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

*Kategorii*<br/>
Kategorii.

*Ustawień regionalnych*<br/>
Specyfikator ustawień regionalnych.

## <a name="return-value"></a>Wartość zwracana

Jeśli podano *prawidłowe ustawienia regionalne* i *kategorię,* zwraca określone ustawienia regionalne jako obiekt **_locale_t.** Bieżące ustawienia regionalne programu nie zostaną zmienione.

## <a name="remarks"></a>Uwagi

Funkcja **_create_locale** umożliwia utworzenie obiektu reprezentującego określone ustawienia specyficzne dla regionu, do użycia w wersjach specyficznych dla ustawień regionalnych wielu funkcji CRT (funkcji z **_l** sufiksem). Zachowanie jest podobne do **setlocale**, z tą różnicą, że zamiast stosowania określonych ustawień regionalnych do bieżącego środowiska, ustawienia są zapisywane w **strukturze _locale_t,** która jest zwracana. Struktura **_locale_t** powinna zostać zwolniona przy użyciu [_free_locale,](free-locale.md) gdy nie jest już potrzebna.

**_wcreate_locale** jest szerokoznakową wersją **_create_locale**; argument ustawień *regionalnych* do **_wcreate_locale** jest ciągiem znaków o szerokim charakterze. **_wcreate_locale** i **_create_locale** zachowują się identycznie w przeciwnym razie.

Argument *kategorii* określa części zachowania specyficzne dla ustawień regionalnych, których dotyczy problem. Flagi używane dla *kategorii* i części programu, których dotyczą, są pokazane w tej tabeli:

| flaga *kategorii* | Wpływa |
|-----------------|---------|
| **LC_ALL** |Wszystkie kategorie, jak podano poniżej. |
| **LC_COLLATE** |**Strcoll**, **_stricoll**, **wcscoll**, **_wcsicoll**, **strxfrm**, **_strncoll**, **_strnicoll**, **_wcsncoll**, **_wcsnicoll**i **wcsxfrm** funkcji. |
| **Lc_ctype** | Funkcje obsługi znaków (z wyjątkiem **isdigit**, **isxdigit**, **mbstowcs**i **mbtowc**, które pozostają nienaruszone). |
| **LC_MONETARY** | Informacje o formacie monetaryskowym zwracane przez funkcję **localeconv.** |
| **LC_NUMERIC** | Znak dziesiętny dla sformatowanych procedur wyjściowych (takich jak **printf),** dla procedur konwersji danych i dla informacji o formatowaniu niepieniężnym zwracanych przez **localeconv**. Oprócz znaku dziesiętnego **LC_NUMERIC** ustawia separator tysięcy i ciąg kontrolny grupowania zwracany przez [localeconv](localeconv.md). |
| **LC_TIME** | **Strftime** i **wcsftime** funkcje. |

Ta funkcja sprawdza poprawność parametrów *kategorii* i *ustawień regionalnych.* Jeśli parametr kategorii nie jest jedną z wartości podanych w poprzedniej tabeli lub jeśli *ustawienia regionalne* to **NULL,** funkcja zwraca **wartość NULL**.

Argument *ustawień regionalnych* jest wskaźnikiem do ciągu, który określa ustawienia regionalne. Aby uzyskać informacje o formacie argumentu *ustawień regionalnych,* zobacz [Nazwy ustawień regionalnych, języki i ciągi kraju/regionu](../../c-runtime-library/locale-names-languages-and-country-region-strings.md).

Argument *ustawień regionalnych* może mieć nazwę ustawień regionalnych, ciąg języka, ciąg języka i kod kraju/regionu, stronę kodową lub ciąg języka, kod kraju/regionu i stronę kodową. Zestaw dostępnych nazw ustawień regionalnych, języków, kodów krajów/regionów i stron kodowych zawiera wszystkie obsługiwane przez interfejs API systemu Windows NLS. Zestaw nazw ustawień regionalnych obsługiwanych przez **_create_locale** są opisane w [nazwach regionalnych, językach i ciągach kraju/regionu](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Zestaw ciągów języka i kraju/regionu obsługiwanych przez **_create_locale** są wymienione w [ciągach językowych](../../c-runtime-library/language-strings.md) i [ciągach kraju/regionu](../../c-runtime-library/country-region-strings.md).

Aby uzyskać więcej informacji o ustawieniach regionalnych, zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md).

Poprzednia nazwa tej funkcji, **__create_locale** (z dwoma wiodącymi podkreśleniami), została przestarzała.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_create_locale**|\<>|
|**_wcreate_locale**|\<>> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

[Nazwy ustawień regionalnych, języki i ciągi kraju/regionu](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Ciągi językowe](../../c-runtime-library/language-strings.md)<br/>
[Ciągi kraju/regionu](../../c-runtime-library/country-region-strings.md)<br/>
[_free_locale](free-locale.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[Setlocale](../../preprocessor/setlocale.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
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
