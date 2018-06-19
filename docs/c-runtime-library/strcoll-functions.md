---
title: strcoll — funkcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- strcoll
dev_langs:
- C++
helpviewer_keywords:
- code pages, using for string comparisons
- string comparison [C++], culture-specific
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: c09eeff3-8aba-4cfb-a524-752436d85573
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e97e16ec3360764411b36bf129c344a3455ce6a6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418188"
---
# <a name="strcoll-functions"></a>strcoll — Funkcje
Każdy z `strcoll` i `wcscoll` funkcje porównuje dwa ciągi zgodnie z `LC_COLLATE` ustawienie kategorii Strona kodowa ustawień lokalnych obecnie w użyciu. Każdy z `_mbscoll` funkcji porównuje dwa ciągi zgodnie ze strony kodowe wielobajtowe obecnie w użyciu. Użyj `coll` funkcje do porównywnania ciągów, gdy ma różnicy między kolejność zestaw znaków i kolejność lexicographic znaków w bieżącej stronie kodowej i różnica jest przydatne do porównania. Użyj odpowiedniej `cmp` funkcji, aby przetestować tylko w przypadku ciągu równości.  
  
### <a name="strcoll-functions"></a>strcoll — Funkcje  
  
|SBCS|Unicode|MBCS|Opis|  
|----------|-------------|----------|-----------------|  
|[strcoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[wcscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[_mbscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|Porównuje dwa ciągi|  
|[_stricoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_wcsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_mbsicoll —](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|Porównuje dwa ciągi (bez uwzględniania wielkości liter)|  
|[_strncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_wcsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_mbsncoll —](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|COLLATE — najpierw `count` znaki z dwóch ciągów|  
|[_strnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_wcsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_mbsnicoll —](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|COLLATE — najpierw `count` znaki z dwóch ciągów (bez uwzględniania wielkości liter)|  
  
## <a name="remarks"></a>Uwagi  
 Funkcje te wersje znaków jednobajtowych (SBCS) (`strcoll`, `stricoll`, `_strncoll`, i `_strnicoll`) porównania `string1` i `string2` zgodnie z `LC_COLLATE` ustawienie kategorii bieżące ustawienia regionalne. Funkcje te różnią się od odpowiadającego `strcmp` funkcje, w tym `strcoll` funkcje używają kodu strony informacji o ustawieniach regionalnych udostępniający sekwencji sortowania. Do porównywania ciągów znaków w lokalizacjach, w których zestawu znaków, kolejności i kolejność lexicographic znaków są różne `strcoll` można używać funkcji, zamiast odpowiadającego `strcmp` funkcji. Aby uzyskać więcej informacji na temat `LC_COLLATE`, zobacz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
 Niektóre strony kodowe i odpowiednich zestawów znaków kolejność znaków w zestawie znaków może być inna niż kolejność lexicographic znaków. Zgodnie z ustawieniami regionalnymi "C", nie jest to to: kolejność znaków w zestawie znaków ASCII, jest taka sama jak lexicographic kolejność znaków. Jednak w niektórych stron kodowych Europejskich, na przykład znak "" (wartość 0x61) poprzedzające znak "ź" (0xE4) znaków wartość, ale znak "ź" poprzedza znak "" lexicographically. Aby przeprowadzić lexicographic porównanie na takie wystąpienie, użyj `strcoll` zamiast `strcmp`. Alternatywnie można użyć `strxfrm` na oryginalnym ciągi, następnie użyć `strcmp` wynikowy ciągów.  
  
 `strcoll`, `stricoll`, `_strncoll`, i `_strnicoll` obsługiwać automatycznie ciągi znaków wielobajtowych zgodnie z strona kodowa ustawień lokalnych obecnie w użyciu, jak ich odpowiedniki znaków dwubajtowych (Unicode). Wersje znaków wielobajtowych (MBCS) z tych funkcji, jednak sortowanie ciągów na podstawie znaków zgodnie ze strony kodowe wielobajtowe obecnie w użyciu.  
  
 Ponieważ `coll` funkcje sortowanie ciągów lexicographically do porównania, podczas gdy `cmp` funkcji po prostu testu równości ciąg `coll` funkcji jest znacznie mniejsza niż odpowiadający mu `cmp` wersji. W związku z tym `coll` funkcje powinny być używane tylko wtedy, gdy ma różnicy między kolejność zestaw znaków i kolejność lexicographic znaków w bieżącej stronie kodowej i ta różnica polega na istotnych dla porównania ciągów.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia regionalne](../c-runtime-library/locale.md)   
 [Manipulowanie ciągami](../c-runtime-library/string-manipulation-crt.md)   
 [localeconv —](../c-runtime-library/reference/localeconv.md)   
 [_mbsnbcoll —, _mbsnbcoll_l —, _mbsnbicoll — _mbsnbicoll_l —](../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)   
 [setLocale, _wsetlocale —](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcmp —, wcscmp —, _mbscmp —](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncmp —, wcsncmp —, _mbsncmp — _mbsncmp_l —](../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [_strnicmp —, _wcsnicmp —, _mbsnicmp —, _strnicmp_l — _wcsnicmp_l —, _mbsnicmp_l —](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)