---
title: _stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l
ms.date: 4/2/2020
api_name:
- _mbsicoll_l
- _stricoll_l
- _mbsicoll
- _wcsicoll_l
- _wcsicoll
- _stricoll
- _o__mbsicoll
- _o__mbsicoll_l
- _o__stricoll
- _o__stricoll_l
- _o__wcsicoll
- _o__wcsicoll_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- stricoll
- _stricoll
- _wcsicoll
- mbsicoll_l
- _mbsicoll
- _ftcsicoll
- wcsicoll_l
- _tcsicoll
- mbsicoll
- stricoll_l
helpviewer_keywords:
- code pages, using for string comparisons
- _ftcsicoll function
- _mbsicoll_l function
- _mbsicoll function
- mbsicoll function
- stricoll function
- tcsicoll function
- string comparison [C++], culture-specific
- _tcsicoll function
- _stricoll function
- _stricoll_l function
- _wcsicoll function
- mbsicoll_l function
- stricoll_l function
- strings [C++], comparing by code page
- ftcsicoll function
ms.assetid: 8ec93016-5a49-49d2-930f-721566661d82
ms.openlocfilehash: 9c023405043dea1c0a1d8e6d7f6fcc6505677583
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919993"
---
# <a name="_stricoll-_wcsicoll-_mbsicoll-_stricoll_l-_wcsicoll_l-_mbsicoll_l"></a>_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l

Porównuje ciągi przy użyciu informacji specyficznych dla ustawień regionalnych.

> [!IMPORTANT]
> **_mbsicoll** i **_mbsicoll_l** nie mogą być używane w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _stricoll(
   const char *string1,
   const char *string2
);
int _wcsicoll(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbsicoll(
   const unsigned char *string1,
   const unsigned char *string2
);
int _stricoll_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int _wcsicoll_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbsicoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*ciąg1*, *ciąg2*<br/>
Ciągi zakończone wartością null do porównania.

*locale*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość wskazującą, że jest to relacja *ciąg1* do *ciąg2*, jak pokazano poniżej.

|Wartość zwracana|Relacja ciąg1 do ciąg2|
|------------------|----------------------------------------|
|< 0|*ciąg1* mniejszy niż *ciąg2*|
|0|*ciąg1* identyczny z *ciąg2*|
|> 0|*ciąg1* większy niż *ciąg2*|
|**_NLSCMPERROR**|Wystąpił błąd.|

Każda z tych funkcji zwraca **_NLSCMPERROR**. Aby użyć **_NLSCMPERROR**, Uwzględnij \<zarówno ciąg. h> \<, jak i mbstring. h>. **_wcsicoll** może zakończyć się niepowodzeniem, jeśli *ciąg1* lub *ciąg2* zawiera kody znaków dwubajtowych spoza domeny sekwencji sortowania. Gdy wystąpi błąd, **_wcsicoll** może ustawić **errno** na **EINVAL**. Aby sprawdzić, czy wystąpił błąd w wywołaniu **_wcsicoll**, ustaw wartość **errno** na 0, a następnie sprawdź **errno** po wywołaniu **_wcsicoll**.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji wykonuje porównanie wartości typu *ciąg1* i *ciąg2* bez uwzględniania wielkości liter zgodnie z aktualnie używaną stroną kodową. Te funkcje powinny być używane tylko wtedy, gdy istnieje różnica pomiędzy kolejnością zestawu znaków i kolejnością znaków leksykograficznych w bieżącej stronie kodowej, a różnica jest istotna dla porównania ciągów.

**_stricmp** różni się **od _stricoll** , w którym **LC_CTYPE**jest wpływ na porównanie **_stricmp** , podczas gdy porównanie **_stricoll** jest zgodne z kategoriami **LC_CTYPE** i **LC_COLLATE** ustawień regionalnych. Aby uzyskać więcej informacji na temat kategorii **LC_COLLATE** , zobacz sekcję [setlocale](setlocale-wsetlocale.md) i [locale](../../c-runtime-library/locale-categories.md). Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych; wersje z sufiksem **_l** są identyczne, z tą różnicą, że w zamian korzystają z przekazaną ustawieniami regionalnymi. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Wszystkie te funkcje sprawdzają poprawność swoich parametrów. Jeśli *ciąg1* lub *ciąg2* ma wskaźniki **null** , zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **_NLSCMPERROR** i ustawiają **errno** na **EINVAL**.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicoll**|**_stricoll**|**_mbsicoll**|**_wcsicoll**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_stricoll**, **_stricoll_l**|\<> String. h|
|**_wcsicoll**, **_wcsicoll_l**|\<WCHAR. h>, \<String. h>|
|**_mbsicoll**, **_mbsicoll_l**|\<mbstring. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Ustawienie](../../c-runtime-library/locale.md)<br/>
[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll — Funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
