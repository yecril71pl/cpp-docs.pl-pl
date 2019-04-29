---
title: _stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l
ms.date: 11/04/2016
apiname:
- _mbsicoll_l
- _stricoll_l
- _mbsicoll
- _wcsicoll_l
- _wcsicoll
- _stricoll
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: bd2406751fd2855afd02743c98938e530398e7d1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353667"
---
# <a name="stricoll-wcsicoll-mbsicoll-stricolll-wcsicolll-mbsicolll"></a>_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l

Porównuje ciągi przy użyciu informacji specyficznych dla ustawień regionalnych.

> [!IMPORTANT]
> **_mbsicoll —** i **_mbsicoll_l —** nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ciągi zakończony wartością null do porównania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość wskazującą związek *ciąg1* do *ciąg2*, wykonując następujące czynności.

|Wartość zwracana|Relacja ciąg1 do ciąg2|
|------------------|----------------------------------------|
|< 0|*ciąg1* mniej niż *ciąg2*|
|0|*ciąg1* taka sama jak *ciąg2*|
|> 0|*ciąg1* większa *ciąg2*|
|**_NLSCMPERROR**|Wystąpił błąd.|

Każda z tych funkcji zwraca **_NLSCMPERROR**. Aby użyć **_NLSCMPERROR**, zawierać albo \<string.h > lub \<mbstring.h >. **_wcsicoll —** może zakończyć się niepowodzeniem, jeśli *ciąg1* lub *ciąg2* zawiera kody znaków dwubajtowych spoza domeny sekwencji sortowania. Gdy wystąpi błąd, **_wcsicoll —** mogą ustawiać **errno** do **EINVAL**. Aby sprawdzić, czy błąd w wywołaniu **_wcsicoll —** ustaw **errno** na 0, a następnie sprawdź **errno** po wywołaniu **_wcsicoll —**.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji wykonuje porównania bez uwzględniania wielkości *ciąg1* i *ciąg2* zgodnie z aktualnie używaną stroną kodową. Te funkcje powinny być używane tylko wtedy, gdy istnieje różnica pomiędzy znak zestawu kolejności i kolejnością znaków leksykograficznych w bieżącej stronie kodowej, a różnica ta ma znaczenie dla porównania ciągu.

**_stricmp —** różni się od **_stricoll —** , **_stricmp —** porównania jest zależna od **LC_CTYPE**, podczas gdy **_stricoll —** porównania, zgodnie z **LC_CTYPE** i **LC_COLLATE** kategorie ustawień regionalnych. Aby uzyskać więcej informacji na temat **LC_COLLATE** kategorii, zobacz [setlocale](setlocale-wsetlocale.md) i [kategorie ustawień regionalnych](../../c-runtime-library/locale-categories.md). Wersje tych funkcji, bez **_l** sufiksa używa bieżących ustawień regionalnych; wersje **_l** sufiksem są identyczne, z tą różnicą, że używają w zamian przekazanych ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Wszystkie te funkcje sprawdzają poprawność swoich parametrów. Jeśli *ciąg1* lub *ciąg2* są **NULL** wskaźników, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **_NLSCMPERROR** i ustaw **errno** do **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicoll —**|**_stricoll**|**_mbsicoll**|**_wcsicoll**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_stricoll —**, **_stricoll_l —**|\<string.h>|
|**_wcsicoll**, **_wcsicoll_l**|\<WChar.h >, \<string.h >|
|**_mbsicoll**, **_mbsicoll_l**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll, funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
