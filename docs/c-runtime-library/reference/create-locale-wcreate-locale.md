---
title: _create_locale, _wcreate_locale
ms.date: 11/04/2016
apiname:
- _create_locale
- __create_locale
- _wcreate_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 109a1d93692d0c65269b40fd0559381907ce1cab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340368"
---
# <a name="createlocale-wcreatelocale"></a>_create_locale, _wcreate_locale

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

*category*<br/>
Kategoria.

*Ustawienia regionalne*<br/>
Specyfikator ustawień regionalnych.

## <a name="return-value"></a>Wartość zwracana

Jeśli jest to prawidłowy *ustawień regionalnych* i *kategorii* otrzymują, zwraca określone ustawienia regionalne jako **_locale_t —** obiektu. Bieżące ustawienia regionalne programu nie ulegną zmianie.

## <a name="remarks"></a>Uwagi

**_Create_locale** funkcja pozwala utworzyć obiekt, który reprezentuje niektóre ustawienia specyficzne dla regionu, do użytku w wersjach specyficznych dla ustawień regionalnych wielu funkcji CRT (funkcje z **_l** sufiks ). Zachowanie jest podobne do **setlocale**, z tą różnicą, że zamiast stosowania ustawień regionalnych określonych dla bieżącego środowiska, ustawienia te są zapisywane w **_locale_t —** strukturę, która jest zwracana. **_Locale_t —** struktura powinna zostać uwolniona za pomocą [_free_locale —](free-locale.md) gdy jest już potrzebny.

**_wcreate_locale** to wersja znaku dwubajtowego **_create_locale**; *ustawień regionalnych* argument **_wcreate_locale** jest ciągiem znaku dwubajtowego. **_wcreate_locale** i **_create_locale** zachowują się identycznie.

*Kategorii* argument określa części zachowania specyficzne dla ustawień regionalnych, których to dotyczy. Flagi używane do *kategorii* i części program wpływają na to, jak pokazano w poniższej tabeli:

| *Kategoria* flagi | Dotyczy |
|-----------------|---------|
| **LC_ALL** |Wszystkie kategorie, wymienione poniżej. |
| **LC_COLLATE** |**Strcoll —**, **_stricoll —**, **wcscoll —**, **_wcsicoll —**, **strxfrm —**, **_ strncoll —**, **_strnicoll —**, **_wcsncoll —**, **_wcsnicoll —**, i **wcsxfrm —** funkcji. |
| **LC_CTYPE** | Funkcje obsługi znaków (z wyjątkiem **isdigit**, **isxdigit**, **mbstowcs**, i **mbtowc**, które są bez zmian). |
| **LC_MONETARY** | Informacje o formatowaniu walutowym zwracane przez **localeconv** funkcji. |
| **LC_NUMERIC** | Dziesiętny znak dla sformatowanych procedur danych wyjściowych (takich jak **printf**), dla procedur konwersji danych i dla niepieniężnych informacji formatowania zwracanych przez **localeconv**. Oprócz znaku dziesiętnego **LC_NUMERIC** ustawia separator tysięcy i sterujący grupowaniem zwracany przez ciąg [localeconv](localeconv.md). |
| **LC_TIME** | **Strftime** i **wcsftime** funkcji. |

Ta funkcja sprawdza poprawność *kategorii* i *ustawień regionalnych* parametrów. Jeśli parametr kategorii nie jest jedną z wartości podanych w powyższej tabeli lub *ustawień regionalnych* jest **NULL**, funkcja zwraca **NULL**.

*Ustawień regionalnych* argument jest wskaźnikiem do ciągu, który określa ustawienia regionalne. Aby uzyskać informacje o formacie parametru *ustawień regionalnych* argumentów, zobacz [nazwy lokalne, języki i ciągi Kraj/Region](../../c-runtime-library/locale-names-languages-and-country-region-strings.md).

*Ustawień regionalnych* argument może przyjąć nazwy ustawień regionalnych, ciąg języka, ciąg języka i kraju/regionu, stronę kodową lub ciąg języka, kod kraju/regionu i stronę kodową. Zestaw dostępnych nazw ustawień regionalnych, języków, kodów krajów/regionów i stron kodowych zawiera wszystkie opcje, które są obsługiwane przez API Windows NLS, z wyjątkiem stron kodowych, które wymagają więcej niż dwóch bajtów na znak — na przykład, UTF-7 i UTF-8. Jeżeli podasz stronę kodową, taką jak UTF-7 lub UTF-8, **_create_locale** będą się niepowodzeniem i zwróci **NULL**. Zestaw nazw ustawień regionalnych obsługiwanych przez **_create_locale** są opisane w [nazwy lokalne, języki i ciągi Kraj/Region](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Zestaw ciągów języka i kraju/regionu, obsługiwany przez **_create_locale** są wymienione w [Language Strings](../../c-runtime-library/language-strings.md) i [ciągi Kraj/Region](../../c-runtime-library/country-region-strings.md).

Aby uzyskać więcej informacji na temat ustawień regionalnych, zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md).

Poprzednia nazwa tej funkcji **__create_locale** (z dwoma wiodącymi podkreśleniami), jest przestarzała.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_create_locale**|\<locale.h>|
|**_wcreate_locale**|\<Locale.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Nazwy lokalne, języki i ciągi Kraj/Region](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Ciągi języka](../../c-runtime-library/language-strings.md)<br/>
[Ciągi Kraj/Region](../../c-runtime-library/country-region-strings.md)<br/>
[_free_locale](free-locale.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strcoll, funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
