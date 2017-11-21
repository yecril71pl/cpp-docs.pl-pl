---
title: "_strncoll —, _wcsncoll —, _mbsncoll —, _strncoll_l —, _wcsncoll_l —, _mbsncoll_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _strncoll
- _mbsncoll_l
- _wcsncoll
- _wcsncoll_l
- _mbsncoll
- _strncoll_l
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
- mbsncoll_l
- strncoll
- _wcsncoll
- _tcsnccoll
- _ftcsnccoll
- wcsncoll
- _mbsncoll
- wcsncoll_l
- strncoll_l
- _ftcsncoll
- _strncoll
- _tcsncoll
- mbsncoll
dev_langs: C++
helpviewer_keywords:
- _strncoll_l function
- code pages, using for string comparisons
- _strncoll function
- _mbsncoll function
- ftcsncoll function
- strncoll function
- _ftcsncoll function
- strncoll_l function
- wcsncoll function
- mbsncoll function
- _tcsncoll function
- _tcsnccoll function
- wcsncoll_l function
- tcsnccoll function
- mbsncoll_l function
- _mbsncoll_l function
- tcsncoll function
- _wcsncoll function
- strings [C++], comparing by code page
- _ftcsnccoll function
- ftcsnccoll function
- _wcsncoll_l function
ms.assetid: e659a5a4-8afe-4033-8e72-17ffd4bdd8e9
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 36c802c5406d4f142e4902ad75a7621f5a23ed70
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="strncoll-wcsncoll-mbsncoll-strncolll-wcsncolll-mbsncolll"></a>_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l
Porównanie ciągów za pomocą informacje specyficzne dla ustawień regionalnych.  
  
> [!IMPORTANT]
>  `_mbsncoll`i `_mbsncoll_l` nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _strncoll(  
   const char *string1,  
   const char *string2,  
   size_t count   
);  
int _wcsncoll(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   size_t count   
);  
int _mbsncoll(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _strncoll_l(  
   const char *string1,  
   const char *string2,  
   size_t count,  
   _locale_t locale  
);  
int _wcsncoll_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   size_t count,  
   _locale_t locale  
);  
int _mbsncoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `string1, string2`  
 Ciągi zakończone wartością null do porównania.  
  
 `count`  
 Liczba znaków do porównania.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji zwraca wartość wskazującą relacji podciągów `string1` i `string2`, wykonując następujące czynności.  
  
|Wartość zwracana|Relacja ciąg1 do ciąg2|  
|------------------|----------------------------------------|  
|< 0|`string1`jest mniejsza niż `string2`.|  
|0|`string1`jest taka sama jak `string2`.|  
|> 0|`string1`jest większa niż `string2`.|  
  
 Każdy z tych funkcji zwraca `_NLSCMPERROR`. Aby użyć `_NLSCMPERROR`, to STRING.h lub MBSTRING.h. `_wcsncoll`może się nie powieść, jeśli dowolny `string1` lub `string2` zawiera kody znaków dwubajtowych, znajdujących się poza domeną sekwencję sortowania. Po wystąpieniu błędu `_wcsncoll` mogą ustawiać `errno` do `EINVAL`. Aby sprawdzić, czy błąd w wywołaniu `_wcsncoll`ustaw `errno` 0, a następnie sprawdź `errno` po wywołaniu metody `_wcsncoll`.  
  
## <a name="remarks"></a>Uwagi  
 Każda z tych funkcji przeprowadza porównanie z uwzględnieniem wielkości liter pierwszego `count` znaków `string1` i `string2`, zgodnie z stronę kodową, która jest aktualnie używany. Ich używać tylko wtedy, gdy ma różnicy między kolejność zestaw znaków i kolejność lexicographic znaków w stronie kodowej, a ta różnica polega na istotnych dla porównania ciągów. Kolejność zestaw znaków jest zależny od ustawień regionalnych. Wersje tych funkcji, które nie mają `_l` Użyj sufiksu bieżące ustawienia regionalne, ale wersje, które mają `_l` ustawień regionalnych, który jest przekazywany w używać sufiksu. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 Wszystkie te funkcje walidację ich parametrów. Jeśli dowolny `string1` lub `string2` jest wskaźnika o wartości null, lub `count` jest większa niż `INT_MAX`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają `_NLSCMPERROR` i ustaw `errno` do `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsnccoll`|`_strncoll`|`_mbsncoll`|`_wcsncoll`|  
|`_tcsncoll`|`_strncoll`|[_mbsnbcoll —](../../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)|`_wcsncoll`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_strncoll`, `_strncoll_l`|\<String.h >|  
|`_wcsncoll`, `_wcsncoll_l`|\<WChar.h > lub \<string.h >|  
|`_mbsncoll`, `_mbsncoll_l`|\<mbstring.h >|  
  
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