---
title: _strnicoll, _wcsnicoll, _mbsnicoll, _strnicoll_l, _wcsnicoll_l, _mbsnicoll_l
ms.date: 11/04/2016
apiname:
- _mbsnicoll_l
- _mbsnicoll
- _wcsnicoll_l
- _strnicoll
- _strnicoll_l
- _wcsnicoll
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
- wcshicoll_l
- _ftcsncicoll
- strnicoll_l
- _wcsnicoll
- mbsnicoll_l
- _strnicoll
- mbsnicoll
- _ftcsnicoll
- wcsnicoll
- _tcsnicoll
- _mbsnicoll
- strinicoll
- _tcsncicoll
helpviewer_keywords:
- code pages, using for string comparisons
- ftcsncicoll function
- mbsnicoll_l function
- _ftcsnicoll function
- mbsnicoll function
- _tcsnicoll function
- _wcsnicoll_l function
- _mbsnicoll function
- tcsncicoll function
- strnicoll function
- _ftcsncicoll function
- wcsnicoll_l function
- _mbsnicoll_l function
- _tcsncicoll function
- strnicoll_l function
- wcsnicoll function
- _strnicoll_l function
- _wcsnicoll function
- ftcsnicoll function
- strings [C++], comparing by code page
- tcsnicoll function
- _strnicoll function
ms.assetid: abf0c569-725b-428d-9ff2-924f430104b4
ms.openlocfilehash: 6b3562dd077b9aa80b9d188e9b2c43282e797af3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50606040"
---
# <a name="strnicoll-wcsnicoll-mbsnicoll-strnicolll-wcsnicolll-mbsnicolll"></a>_strnicoll, _wcsnicoll, _mbsnicoll, _strnicoll_l, _wcsnicoll_l, _mbsnicoll_l

Porównuje ciągi przy użyciu informacji specyficznych dla ustawień regionalnych.

> [!IMPORTANT]
> **_mbsnicoll —** i **_mbsnicoll_l —** nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _strnicoll(
   const char *string1,
   const char *string2,
   size_t count
);
int _wcsnicoll(
   const wchar_t *string1,
   const wchar_t *string2 ,
   size_t count
);
int _mbsnicoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _strnicoll_l(
   const char *string1,
   const char *string2,
   size_t count,
   _locale_t locale
);
int _wcsnicoll_l(
   const wchar_t *string1,
   const wchar_t *string2 ,
   size_t count,
   _locale_t locale
);
int _mbsnicoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*ciąg1*, *ciąg2*<br/>
Ciągi zakończone wartością null do porównania

*Liczba*<br/>
Liczba znaków do porównania

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość wskazującą związek podciągów *ciąg1* i *ciąg2*, wykonując następujące czynności.

|Wartość zwracana|Relacja ciąg1 do ciąg2|
|------------------|----------------------------------------|
|< 0|*ciąg1* mniej niż *ciąg2*|
|0|*ciąg1* taka sama jak *ciąg2*|
|> 0|*ciąg1* większa *ciąg2*|

Każda z tych funkcji zwraca **_NLSCMPERROR**. Aby użyć **_NLSCMPERROR**, Dołącz albo ciąg. H lub MBSTRING. H. **_wcsnicoll —** może zakończyć się niepowodzeniem, jeśli *ciąg1* lub *ciąg2* zawiera kody znaków dwubajtowych spoza domeny sekwencji sortowania. Gdy wystąpi błąd, **_wcsnicoll —** mogą ustawiać **errno** do **EINVAL**. Aby sprawdzić, czy błąd w wywołaniu **_wcsnicoll —** ustaw **errno** na 0, a następnie sprawdź **errno** po wywołaniu **_wcsnicoll —**.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji wykonuje porównania bez uwzględniania pierwszego *liczba* znaki w *ciąg1* i *ciąg2* zgodnie ze stroną kodową. Te funkcje powinny być używane tylko wtedy, gdy istnieje różnica pomiędzy znak zestawu kolejności i kolejnością znaków leksykograficznych w stronie kodowej, a różnica ta ma znaczenie dla porównania ciągu. Wersje tych funkcji, bez **_l** sufiksa używa bieżącej strony ustawień regionalnych i kodu. Wersje **_l** sufiksem są identyczne, z tą różnicą, że używają w zamian przekazanych ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Wszystkie te funkcje sprawdzają poprawność swoich parametrów. Jeśli *ciąg1* lub *ciąg2* jest wskaźnikiem wartości null lub jeżeli liczba jest większa niż **INT_MAX**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [ Walidacja parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, te funkcje zwracają **_NLSCMPERROR** i ustaw **errno** do **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncicoll —**|**_strnicoll**|**_mbsnbicoll —**|**_wcsnicoll**|
|**_tcsnicoll —**|**_strnicoll**|[_mbsnbicoll —](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)|**_wcsnicoll**|
|**_tcsnicoll_l**|**_strnicoll_l**|**_mbsnbicoll_l —**|**_wcsnicoll_l —**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strnicoll —**, **_strnicoll_l —**|\<string.h>|
|**_wcsnicoll —**, **_wcsnicoll_l —**|\<WChar.h > lub \<string.h >|
|**_mbsnicoll —**, **_mbsnicoll_l —**|\<mbstring.h>|

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
