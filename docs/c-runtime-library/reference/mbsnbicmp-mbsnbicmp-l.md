---
title: "_mbsnbicmp —, _mbsnbicmp_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsnbicmp_l
- _mbsnbicmp
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
- _strnicmp
- _wcsnicmp_l
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _tcsnicmp
- _strnicmp_l
- _tcsnicmp_l
- _wcsnicmp
- _mbsnbicmp_l
dev_langs: C++
helpviewer_keywords:
- _tcsnicmp_l function
- _strnicmp function
- mbsnbicmp_l function
- _wcsnicmp_l function
- _mbsnbicmp function
- _mbsnbicmp_l function
- _tcsnicmp function
- _strnicmp_l function
- mbsnbicmp function
- _wcsnicmp function
ms.assetid: ddb44974-8b0c-42f0-90d0-56c9350bae0c
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2ba2bd2e7b4857d6c1bd57f608c20e4a2a7a85d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mbsnbicmp-mbsnbicmpl"></a>_mbsnbicmp, _mbsnbicmp_l
Porównuje `n` bajtów dwóch znaków wielobajtowych ciągi i ignoruje wielkość liter.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _mbsnbicmp(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `string1, string2`  
 Ciągi zakończone wartością null do porównania.  
  
 `count`  
 Liczba bajtów do porównania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartości zwracanej wskazuje relację między podciągów.  
  
|Wartość zwracana|Opis|  
|------------------|-----------------|  
|< 0|`string1`substring mniej niż `string2` podciąg.|  
|0|`string1`taki sam jak podciąg `string2` podciąg.|  
|> 0|`string1`substring większe `string2` podciąg.|  
  
 W przypadku wystąpienia błędu `_mbsnbcmp` zwraca `_NLSCMPERROR`, która jest zdefiniowana w String.h i Mbstring.h.  
  
## <a name="remarks"></a>Uwagi  
 `_mbsnbicmp` Funkcja przeprowadza porównanie liczby porządkowej co najwyżej pierwszego `count` bajtów `string1` i `string2`. Porównanie odbywa się za pomocą konwersji na małe litery; każdy znak `_mbsnbcmp` jest rozróżniana wielkość liter wersja `_mbsnbicmp`. Porównanie kończy się po osiągnięciu znak końcowy null w każdym ciągu przed `count` znaki są porównywane. Jeśli ciągi są takie same po znak końcowy null osiągnięciu w każdym ciągu przed `count` znaki są porównywane, krótszego ciągu jest mniejsza.  
  
 `_mbsnbicmp`przypomina `_mbsnicmp`, ale do porównywania ciągów `count` bajtów zamiast znaków.  
  
 Dwa ciągi zawierające znaki znajdujące się między "Z" i "" w tabeli ASCII ('[','\\","] "," ^ ","_", i"\`") porównania w różny sposób, w zależności od ich przypadku. Na przykład dwa ciągi "`ABCDE`"i"`ABCD^`" porównanie jedną z metod, jeśli wynikiem porównania jest małe litery ("`abcde`" > "`abcd^`") i w inny sposób ("`ABCDE`" < "`ABCD^`") jeśli wielkie litery.  
  
 `_mbsnbicmp`rozpoznaje wielobajtowych sekwencji znaków zgodnie z [strony kodowe wielobajtowe](../../c-runtime-library/code-pages.md) obecnie w użyciu. Nie dotyczy on bieżących ustawień regionalnych.  
  
 Jeśli dowolny `string1` lub `string2` wskaźnika o wartości null, jest `_mbsnbicmp` wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcja zwraca `_NLSCMPERROR` i ustawia `errno` do `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcsnicmp`|`_strnicmp`|`_mbsnbicmp`|`_wcsnicmp`|  
|`_tcsnicmp_l`|`_strnicmp_l`|`_mbsnbicmp_l`|`_wcsnicmp_l`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_mbsnbicmp`|< mbstring.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [_mbsnbcmp —, _mbsnbcmp_l —](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)   
 [_mbsnbcat —, _mbsnbcat_l —](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [_mbsnbcmp —, _mbsnbcmp_l —](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)