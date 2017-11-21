---
title: "_stricoll —, _wcsicoll —, _mbsicoll —, _stricoll_l —, _wcsicoll_l, _mbsicoll_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9508eacf1e361f3e87353f7ceb6dc00270982212
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="stricoll-wcsicoll-mbsicoll-stricolll-wcsicolll-mbsicolll"></a>_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l
Porównanie ciągów za pomocą informacje specyficzne dla ustawień regionalnych.  
  
> [!IMPORTANT]
>  `_mbsicoll`i `_mbsicoll_l` nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `string1, string2`  
 Ciągi zakończone wartością null do porównania.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji zwraca wartość wskazującą relacji z `string1` do `string2`, wykonując następujące czynności.  
  
|Wartość zwracana|Relacja ciąg1 do ciąg2|  
|------------------|----------------------------------------|  
|< 0|`string1`mniej niż`string2`|  
|0|`string1`taki sam jak`string2`|  
|> 0|`string1`większa niż`string2`|  
|`_NLSCMPERROR`|Wystąpił błąd.|  
  
 Każdy z tych funkcji zwraca `_NLSCMPERROR`. Aby użyć `_NLSCMPERROR`, zawiera `STRING.H` lub `MBSTRING.H`. `_wcsicoll`może się nie powieść, jeśli dowolny `string1` lub `string2` zawiera kody znaków dwubajtowych spoza domeny sekwencję sortowania. Po wystąpieniu błędu `_wcsicoll` mogą ustawiać `errno` do `EINVAL`. Aby sprawdzić, czy błąd w wywołaniu `_wcsicoll`ustaw `errno` 0, a następnie sprawdź `errno` po wywołaniu `_wcsicoll`.  
  
## <a name="remarks"></a>Uwagi  
 Każda z tych funkcji wykonuje porównania bez uwzględniania wielkości liter `string1` i `string2` zgodnie z aktualnie używanej strony kodowej. Można używać tych funkcji, tylko wtedy, gdy istnieje następująca różnica między znak Ustaw kolejność i kolejność lexicographic znak w bieżącej stronie kodowej i ta różnica polega na istotnych dla porównania ciągów.  
  
 `_stricmp`różni się od `_stricoll` w tym `_stricmp` dotyczy porównanie `LC_CTYPE`, podczas gdy `_stricoll` porównania jest zgodne z `LC_CTYPE` i `LC_COLLATE` kategorii ustawień regionalnych. Aby uzyskać więcej informacji na temat `LC_COLLATE` kategorii, zobacz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) i [kategorie regionalne](../../c-runtime-library/locale-categories.md). Wersje tych funkcji bez `_l` sufiks Użyj bieżących ustawień regionalnych; wersji z `_l` sufiks są identyczne, z wyjątkiem tego, aby używały przekazano zamiast tego ustawienia regionalne. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 Wszystkie te funkcje walidację ich parametrów. Jeśli dowolny `string1` lub `string2` są `NULL` wskaźniki, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają `_NLSCMPERROR` i ustaw `errno` do `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsicoll`|`_stricoll`|`_mbsicoll`|`_wcsicoll`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_stricoll`, `_stricoll_l`|\<String.h >|  
|`_wcsicoll`, `_wcsicoll_l`|\<WChar.h >, \<string.h >|  
|`_mbsicoll`, `_mbsicoll_l`|\<mbstring.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)   
 [strcoll — funkcje](../../c-runtime-library/strcoll-functions.md)   
 [localeconv —](../../c-runtime-library/reference/localeconv.md)   
 [_mbsnbcoll —, _mbsnbcoll_l —, _mbsnbicoll — _mbsnbicoll_l —](../../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)   
 [setLocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcmp —, wcscmp —, _mbscmp —](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [_stricmp —, _wcsicmp —, _mbsicmp —, _stricmp_l — _wcsicmp_l —, _mbsicmp_l —](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)   
 [strncmp —, wcsncmp —, _mbsncmp — _mbsncmp_l —](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [_strnicmp —, _wcsnicmp —, _mbsnicmp —, _strnicmp_l — _wcsnicmp_l —, _mbsnicmp_l —](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strxfrm —, wcsxfrm —, _strxfrm_l — _wcsxfrm_l —](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)