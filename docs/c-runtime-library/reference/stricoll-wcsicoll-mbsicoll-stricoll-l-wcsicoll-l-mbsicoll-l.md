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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: d726d2d33f8f775d09e6197dfeda6abb91106a53
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355325"
---
# <a name="_stricoll-_wcsicoll-_mbsicoll-_stricoll_l-_wcsicoll_l-_mbsicoll_l"></a>_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l

Porównuje ciągi przy użyciu informacji specyficznych dla ustawień regionalnych.

> [!IMPORTANT]
> **_mbsicoll** i **_mbsicoll_l** nie mogą być używane w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość wskazującą relację *ciągu1* do *string2*, w następujący sposób.

|Wartość zwracana|Relacja ciągu1 do ciągu2|
|------------------|----------------------------------------|
|< 0|*ciąg1* mniej niż *ciąg2*|
|0|*string1* identyczny z *string2*|
|> 0|*ciąg1* większy niż *ciąg2*|
|**_NLSCMPERROR**|Wystąpił błąd.|

Każda z tych funkcji zwraca **_NLSCMPERROR**. Aby użyć **_NLSCMPERROR,** należy \<dołączyć> string.h \<lub mbstring.h>. **_wcsicoll** może zakończyć się niepowodzeniem, jeśli *ciąg1* lub *string2* zawiera kody znaków szerokich poza domeną sekwencji sortowania. W przypadku wystąpienia błędu **_wcsicoll** może ustawić **errno** na **EINVAL**. Aby sprawdzić, czy nie ma błędu w wywołaniu **_wcsicoll,** ustaw **errno** na 0, a następnie sprawdź **errno** po wywołaniu **_wcsicoll**.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji wykonuje porównanie bez uwzględniania wielkości liter *string1* i *string2* zgodnie ze stroną kodową aktualnie używaną. Te funkcje powinny być używane tylko wtedy, gdy istnieje różnica między kolejnością zestawu znaków a kolejnością znaków leksykograficznych na bieżącej stronie kodowej, a ta różnica jest interesująca dla porównania ciągów.

**_stricmp** różni się od **_stricoll** tym, że na porównanie **_stricmp** ma wpływ **LC_CTYPE,** podczas gdy porównanie **_stricoll** jest zgodne z **LC_CTYPE** i **LC_COLLATE** kategoriami ustawień regionalnych. Aby uzyskać więcej informacji na temat **kategorii LC_COLLATE,** zobacz [setlocale](setlocale-wsetlocale.md) i [Kategorie ustawień regionalnych](../../c-runtime-library/locale-categories.md). Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych; wersje z sufiksem **_l** są identyczne, z tą różnicą, że zamiast tego używają ustawień regionalnych przekazanych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Wszystkie te funkcje sprawdzają poprawność ich parametrów. Jeśli *ciąg1* lub *ciąg2* są wskaźnikami **NULL,** wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w programie [Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, funkcje te zwracają **_NLSCMPERROR** i ustawić **errno** na **EINVAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicoll**|**_stricoll**|**_mbsicoll**|**_wcsicoll**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_stricoll** **, _stricoll_l**|\<string.h>|
|**_wcsicoll** **, _wcsicoll_l**|\<wchar.h>, \<string.h>|
|**_mbsicoll**, **_mbsicoll_l**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
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
