---
title: "_mbsnbcoll —, _mbsnbcoll_l —, _mbsnbicoll —, _mbsnbicoll_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsnbicoll_l
- _mbsnbcoll_l
- _mbsnbcoll
- _mbsnbicoll
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
apitype: DLLExport
f1_keywords:
- mbsnbicoll
- mbsnbcoll
- mbsnbicoll_l
- _mbsnbcoll
- _mbsnbicoll
- _ftcsnicoll
- _ftcsncoll
- mbsnbcoll_l
dev_langs: C++
helpviewer_keywords:
- _mbsnbcoll_l function
- mbsnbcoll_l function
- _mbsnbcoll function
- _tcsnicoll function
- mbsnbcoll function
- mbsnbicoll_l function
- mbsnbicoll function
- _tcsncoll function
- _mbsnbicoll function
- _mbsnbicoll_l function
- tcsncoll function
- tcsnicoll function
ms.assetid: d139ed63-ccba-4458-baa2-61cbcef03e94
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b0ab65644f4a7bcb93ceb2156a5354a81358e47c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mbsnbcoll-mbsnbcolll-mbsnbicoll-mbsnbicolll"></a>_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l
Porównuje `n` bajtów dwa ciągi znaków wielobajtowych przy użyciu informacji wielobajtowe stronę kodową.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _mbsnbcoll(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _mbsnbcoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,  
   _locale_t locale  
);  
int _mbsnbicoll(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _mbsnbicoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `string1, string2`  
 Ciągi do porównania.  
  
 `count`  
 Liczba bajtów do porównania.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartości zwracanej wskazuje relacja podciągów `string1` i `string2`.  
  
|Wartość zwracana|Opis|  
|------------------|-----------------|  
|< 0|`string1`substring mniej niż `string2` podciąg.|  
|0|`string1`taki sam jak podciąg `string2` podciąg.|  
|> 0|`string1`substring większe `string2` podciąg.|  
  
 Jeśli `string1` lub `string2` jest `NULL` lub `count` jest większa niż `INT_MAX`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają `_NLSCMPERROR` i ustaw `errno` do `EINVAL`. Aby użyć `_NLSCMPERROR`, to String.h lub Mbstring.h.  
  
## <a name="remarks"></a>Uwagi  
 Każda z tych funkcji posortuje, co najwyżej pierwszy `count` bajtów w `string1` i `string2` i zwraca wartość wskazującą relacji między wynikowy podciągów `string1` i `string2`. Jeśli końcowego bajtów w podciąg `string1` lub `string2` jest bajtu, nie znajduje się w porównaniu; tylko pełną znaków podciągów porównanie tych funkcji. `_mbsnbicoll`jest to wersja bez uwzględniania wielkości liter `_mbsnbcoll`. Podobnie jak `_mbsnbcmp` i `_mbsnbicmp`, `_mbsnbcoll` i `_mbsnbicoll` porównuje dwa ciągi znaków wielobajtowych zgodnie z kolejnością lexicographic określoną przez wielobajtowe [strona kodowa](../../c-runtime-library/code-pages.md) obecnie w użyciu.  
  
 Dla niektórych stron kodowych i odpowiednich zestawów znaków kolejność znaków w zestawie znaków mogą różnić się od kolejność lexicographic znaków. Zgodnie z ustawieniami regionalnymi "C", nie jest to to: kolejność znaków w zestawie znaków ASCII, jest taka sama jak lexicographic kolejność znaków. Jednak w niektórych stron kodowych Europejskich, na przykład znak "" (wartość 0x61) poprzedzające znak "ź" (0xE4) znaków wartość, ale znak "ź" poprzedza znak "" lexicographically. Aby wykonać lexicographic porównania ciągów przy bajtów w takie wystąpienie, użyj `_mbsnbcoll` zamiast `_mbsnbcmp`; Aby sprawdzić tylko pod względem równości ciągu, użyj `_mbsnbcmp`.  
  
 Ponieważ `coll` funkcje sortowanie ciągów lexicographically do porównania, podczas gdy `cmp` funkcji po prostu testu równości ciąg `coll` funkcji jest znacznie mniejsza niż odpowiadający mu `cmp` wersji. W związku z tym `coll` funkcje powinny być używane tylko wtedy, gdy ma różnicy między kolejność zestaw znaków i kolejność lexicographic znaków w bieżącej stronie kodowej i różnica jest przydatne do porównania.  
  
 Wartość wyjściowa jest zagrożony ustawienie `LC_CTYPE` ustawienie kategorii ustawień regionalnych; zobacz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji bez `_l` Użyj sufiksu bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersje z `_l` sufiks są identyczne, z wyjątkiem tego, aby były używane zamiast przekazany parametr ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcsncoll`|[_strncoll —](../../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|`_mbsnbcoll`|[_wcsncoll —](../../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|  
|`_tcsncoll_l`|[_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l](../../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|`_mbsnbcoll_l`|[_wcsncoll_l —](../../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|  
|`_tcsnicoll`|[_strnicoll —](../../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|`_mbsnbicoll`|[_wcsnicoll —](../../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|  
|`_tcsnicoll_l`|[_strnicoll_l —](../../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|`_mbsnbicoll_l`|[_wcsnicoll_l —](../../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_mbsnbcoll`|\<mbstring.h >|  
|`_mbsnbcoll_l`|\<mbstring.h >|  
|`_mbsnbicoll`|\<mbstring.h >|  
|`_mbsnbicoll_l`|\<mbstring.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)   
 [_mbsnbcat —, _mbsnbcat_l —](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [_mbsnbcmp —, _mbsnbcmp_l —](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [_mbsnbicmp —, _mbsnbicmp_l —](../../c-runtime-library/reference/mbsnbicmp-mbsnbicmp-l.md)   
 [strcoll — funkcje](../../c-runtime-library/strcoll-functions.md)   
 [strncmp —, wcsncmp —, _mbsncmp — _mbsncmp_l —](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)