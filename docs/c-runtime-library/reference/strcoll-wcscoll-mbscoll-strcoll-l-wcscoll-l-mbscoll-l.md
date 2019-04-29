---
title: strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l
ms.date: 11/04/2016
apiname:
- wcscoll
- _mbscoll
- _mbscoll_l
- strcoll
- _strcoll_l
- _wcscoll_l
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
- wcscoll
- _mbscoll
- _tcscoll
- _ftcscoll
helpviewer_keywords:
- code pages, using for string comparisons
- mbscoll function
- wcscoll_l function
- ftcscoll function
- wcscoll function
- _strcoll_l function
- tcscoll function
- _ftcscoll function
- _tcscoll function
- _wcscoll_l function
- _mbscoll function
- strcoll_l function
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: 900a7540-c7ec-4c2f-b292-7a85f63e3fe8
ms.openlocfilehash: ae72b4cbb2b001a332d41a74883a0e2a9d20a181
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62354213"
---
# <a name="strcoll-wcscoll-mbscoll-strcolll-wcscolll-mbscolll"></a>strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l

Porównuje ciągi przy użyciu bieżących ustawień regionalnych lub określonej kategorii stanu konwersji LC_COLLATE.

> [!IMPORTANT]
> **_mbscoll —** i **_mbscoll_l** nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int strcoll(
   const char *string1,
   const char *string2
);
int wcscoll(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbscoll(
   const unsigned char *string1,
   const unsigned char *string2
);
int _strcoll_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int wcscoll_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbscoll_l(
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

Każda z tych funkcji zwraca **_NLSCMPERROR** w przypadku błędu. Aby użyć **_NLSCMPERROR**, Dołącz albo ciąg. H lub MBSTRING. H. **wcscoll —** może zakończyć się niepowodzeniem, jeśli *ciąg1* lub *ciąg2* jest **NULL** lub zawiera kody znaków dwubajtowych spoza domeny sekwencji sortowania. Gdy wystąpi błąd, **wcscoll —** mogą ustawiać **errno** do **EINVAL**. Aby sprawdzić, czy błąd w wywołaniu **wcscoll —** ustaw **errno** na 0, a następnie sprawdź **errno** po wywołaniu **wcscoll —**.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji wykonuje porównania uwzględniającego wielkość liter z *ciąg1* i *ciąg2* zgodnie z aktualnie używaną stroną kodową. Te funkcje powinny być używane tylko wtedy, gdy istnieje różnica pomiędzy znak zestawu kolejności i kolejnością znaków leksykograficznych w bieżącej stronie kodowej, a różnica ta ma znaczenie dla porównania ciągu.

Wszystkie te funkcje sprawdzają poprawność swoich parametrów. Jeśli *ciąg1* lub *ciąg2* jest wskaźnikiem typu null, lub jeśli *liczba* jest większa niż **INT_MAX**, zostanie wywołany nieprawidłowy parametr uchwytu , zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, te funkcje zwracają **_NLSCMPERROR** i ustaw **errno** do **EINVAL**.

Porównanie dwóch ciągów jest operacją zależne od ustawień regionalnych, ponieważ poszczególnych ustawień regionalnych ma różne reguły do ustalania kolejności znaków. Wersje tych funkcji, bez **_l** sufiksa używa bieżącego wątku ustawień regionalnych, to zachowań zależnych od ustawień regionalnych; wersje **_l** sufiksem są identyczne z odpowiednimi funkcjami bez sufiksu, chyba że używają ustawień regionalnych przekazanych jako parametr zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscoll —**|**strcoll**|**_mbscoll**|**wcscoll**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strcoll**|\<string.h>|
|**wcscoll**|\<WChar.h >, \<string.h >|
|**_mbscoll**, **_mbscoll_l**|\<mbstring.h>|
|**_strcoll_l**|\<string.h>|
|**_wcscoll_l**|\<WChar.h >, \<string.h >|

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
