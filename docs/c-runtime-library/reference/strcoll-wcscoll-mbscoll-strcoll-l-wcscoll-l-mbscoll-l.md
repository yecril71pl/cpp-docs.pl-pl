---
title: strcoll —, wcscoll —, _mbscoll —, _strcoll_l —, _wcscoll_l —, _mbscoll_l | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eaddf52459ccc9af2009d04e95416d2613a5d77b
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="strcoll-wcscoll-mbscoll-strcolll-wcscolll-mbscolll"></a>strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l

Porównanie ciągów przy użyciu bieżących ustawień regionalnych lub określonej kategorii lc_collate — stan konwersji.

> [!IMPORTANT]
> **_mbscoll —** i **_mbscoll_l** nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ciągi zakończone wartością null do porównania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość wskazującą relacji z *ciąg1* do *ciąg2*, wykonując następujące czynności.

|Wartość zwracana|Relacja ciąg1 do ciąg2|
|------------------|----------------------------------------|
|< 0|*ciąg1* mniej niż *ciąg2*|
|0|*ciąg1* taki sam jak *ciąg2*|
|> 0|*ciąg1* większe *ciąg2*|

Każdy z tych funkcji zwraca **_NLSCMPERROR** w przypadku wystąpienia błędu. Aby użyć **_NLSCMPERROR**, obejmują typu STRING. H lub MBSTRING. H. **wcscoll —** może zakończyć się niepowodzeniem, jeśli dowolny *ciąg1* lub *ciąg2* ma wartość NULL lub zawiera kody znaków dwubajtowych spoza domeny sekwencję sortowania. Po wystąpieniu błędu **wcscoll —** mogą ustawiać **errno** do **einval —**. Aby sprawdzić, czy błąd w wywołaniu **wcscoll —**ustaw **errno** 0, a następnie sprawdź **errno** po wywołaniu **wcscoll —**.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji przeprowadza porównanie z uwzględnieniem wielkości liter *ciąg1* i *ciąg2* zgodnie z aktualnie używanej strony kodowej. Można używać tych funkcji, tylko wtedy, gdy istnieje następująca różnica między znak Ustaw kolejność i kolejność lexicographic znak w bieżącej stronie kodowej i ta różnica polega na istotnych dla porównania ciągów.

Wszystkie te funkcje walidację ich parametrów. Jeśli dowolny *ciąg1* lub *ciąg2* jest wskaźnika o wartości null, lub jeśli *liczba* jest większa niż **int_max —**, jest wywoływana przez program obsługi nieprawidłowych parametrów , zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają **_NLSCMPERROR** i ustaw **errno** do **einval —**.

Porównywania dwóch ciągów jest operacją zależnych od ustawień regionalnych, ponieważ każdy ustawień regionalnych mają różne zasady porządkowania znaków. Wersje tych funkcji bez **_l** sufiks używany bieżący wątek ustawienia regionalne to zachowanie zależnych od ustawień regionalnych; wersje z **_l** sufiks są identyczne z odpowiednich funkcji sufiksu z wyjątkiem używają ustawień regionalnych przekazany jako parametr zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscoll —**|**strcoll**|**_mbscoll**|**wcscoll**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strcoll**|\<string.h>|
|**wcscoll**|\<WChar.h >, \<string.h >|
|**_mbscoll —**, **_mbscoll_l**|\<mbstring.h>|
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
