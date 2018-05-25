---
title: _create_locale, _wcreate_locale | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- locales, creating
- _create_locale function
- create_locale function
- __create_locale function
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9be41a2d156a522c74349c3457295502ae6d4f43
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
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

Jeśli jest to prawidłowy *ustawień regionalnych* i *kategorii* podano, zwraca ustawień regionalnych określonych jako **_locale_t —** obiektu. Bieżące ustawienia regionalne programu nie są zmieniane.

## <a name="remarks"></a>Uwagi

**_Create_locale** funkcja służy do tworzenia obiektu, który reprezentuje niektóre ustawienia specyficzne dla regionu, do użycia w wersji ustawień regionalnych wielu funkcji CRT (działa z **_l** sufiks ). Zachowanie jest podobne do **setlocale**, ale zamiast stosować ustawienia regionalne określonego w bieżącym środowisku, ustawienia są zapisywane w **_locale_t —** struktury, która jest zwracana. **_Locale_t —** struktury powinny zostać zwolniony za pomocą [_free_locale —](free-locale.md) po jest już potrzebne.

**_wcreate_locale** jest wersja znaków dwubajtowych **_create_locale**; *ustawień regionalnych* argument **_wcreate_locale** jest ciągiem znaków dwubajtowych. **_wcreate_locale** i **_create_locale** zachowują się tak samo w przeciwnym razie wartość.

*Kategorii* argument określa części zachowanie specyficzne dla ustawień regionalnych, których dotyczy problem. Flagi używany do *kategorii* i części programu wpływają na są opisane w poniższej tabeli.

|*Kategoria* flagi|Dotyczy|
|-|-|
**LC_ALL —**|Wszystkie kategorie, wymienione poniżej.
**LC_COLLATE —**|**Strcoll —**, **_stricoll —**, **wcscoll —**, **_wcsicoll —**, **strxfrm —**, **_ strncoll —**, **_strnicoll —**, **_wcsncoll —**, **_wcsnicoll —**, i **wcsxfrm —** funkcji.
**LC_CTYPE —**|Funkcje obsługi znaków (z wyjątkiem **isdigit —**, **isxdigit —**, **mbstowcs —**, i **mbtowc —**, którego dotyczy to).
**LC_MONETARY —**|Formatowanie walutowa informacje zwracane przez **localeconv —** funkcji.
**LC_NUMERIC —**|Dziesiętnego znak dla procedury sformatowane dane wyjściowe (takich jak **printf**) dla procedury konwersji danych i -pieniężnego formatowania informacje zwracane przez **localeconv —**. Oprócz znaku dziesiętnego **lc_numeric —** ciągu zwróconego przez kontrolę separator tysięcy zestawów i grupowanie [localeconv —](localeconv.md).
**LC_TIME —**|**Strftime —** i **wcsftime —** funkcji.

Ta funkcja weryfikuje *kategorii* i *ustawień regionalnych* parametrów. Jeśli parametr kategorii nie jest jedną z wartości podane w poprzedniej tabeli lub *ustawień regionalnych* jest **NULL**, funkcja zwraca **NULL**.

*Ustawień regionalnych* argument jest wskaźnikiem do ciągu, który określa ustawienia regionalne. Informacje o formacie *ustawień regionalnych* argumentu, zobacz [nazwy lokalne, języki i ciągi Kraj/Region](../../c-runtime-library/locale-names-languages-and-country-region-strings.md).

*Ustawień regionalnych* argument może zająć Nazwa ustawień regionalnych, ciąg języka ciąg języka i kod kraju/regionu, stronę kodową lub ciąg języka, kod kraju/regionu i strony kodowej. Zbiór nazwy dostępne lokalne, języki kodów kraju/regionu i strony kodowe obejmuje wszystkie punkty, które są obsługiwane przez interfejs API NLS systemu Windows z wyjątkiem stron kodowych, które wymagają więcej niż dwa bajty na znak — na przykład, UTF-7 i UTF-8. Jeśli podasz stronę kodową, takich jak UTF-7 lub UTF-8, **_create_locale** spowoduje niepowodzenie i zwracać **NULL**. Zestaw nazw ustawień regionalnych obsługiwane przez **_create_locale** opisanym w [nazwy lokalne, języki i ciągi Kraj/Region](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Ciągi kraj/region i język obsługiwany przez zestaw **_create_locale** są wymienione w [ciągi języka](../../c-runtime-library/language-strings.md) i [ciągi Kraj/Region](../../c-runtime-library/country-region-strings.md).

Aby uzyskać więcej informacji na temat ustawień regionalnych, zobacz [setlocale, _wsetlocale —](setlocale-wsetlocale.md).

Poprzednia nazwa ta funkcja **__create_locale** (za pomocą dwóch wiodące znaki podkreślenia), jest przestarzała.

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
