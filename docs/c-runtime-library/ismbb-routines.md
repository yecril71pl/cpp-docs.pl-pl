---
title: "_ismbb — procedury | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _ismbb
- ismbb
dev_langs: C++
helpviewer_keywords:
- ismbb routines
- _ismbb routines
ms.assetid: d63c232e-3fe4-4844-aafd-2133846ece4b
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad7e454af3ff8923d60315cd74d48daf9bd665a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ismbb-routines"></a>_ismbb — Procedury
Testy danego całkowitą `c` dla konkretnego warunku, używając bieżących ustawień regionalnych lub określona kategoria Stan konwersji lc_ctype —.  
  
|||  
|-|-|  
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|  
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|  
|[_ismbbblank, _ismbbblank_l](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|  
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|  
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|  
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|  
  
## <a name="remarks"></a>Uwagi  
 Procedury co w `_ismbb` rodziny testów danego całkowitą `c` dla określonego warunku. Wynik testu jest zależna od strony kodowe wielobajtowe, który jest włączona. Strony kodowe wielobajtowe domyślnie na stronę kodową ANSI są uzyskiwane z systemu operacyjnego podczas uruchamiania programu. Można użyć [_getmbcp —](../c-runtime-library/reference/getmbcp.md) kwerendy strony kodowe wielobajtowe, który jest używany, lub [_setmbcp —](../c-runtime-library/reference/setmbcp.md) je zmienić.  
  
 Wartość wyjściowa jest zagrożony ustawienie `LC_CTYPE` kategorii ustawienie ustawień regionalnych; Aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale —](../c-runtime-library/reference/setlocale-wsetlocale.md). Wersje tych funkcji, które nie mają **_l** Użyj sufiksu bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersje, które mają **_l** sufiks są identyczne z wyjątkiem to zamiast nich Użyj parametru ustawień regionalnych, który jest przekazywany w.  
  
 Procedury w `_ismbb` rodziny test danego całkowitą `c` w następujący sposób.  
  
|Procedura|Bajt warunku|  
|-------------|-------------------------|  
|[_ismbbalnum —](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|`isalnum` &#124;&#124; `_ismbbkalnum`.|  
|[_ismbbalpha —](reference/ismbbalpha-ismbbalpha-l.md)|`isalpha` &#124;&#124; `_ismbbkalnum`.|  
|[_ismbbblank](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|`isblank`|  
|[_ismbbgraph —](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|Taki sam jak `_ismbbprint`, ale `_ismbbgraph` nie zawiera znak spacji (0x20).|  
|[_ismbbkalnum —](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Symbol spoza zestawu ASCII tekstu innego niż znaków interpunkcyjnych. Na przykład w strona kodowa 932 tylko `_ismbbkalnum` testów dla katakana alfanumeryczne.|  
|[_ismbbkana —](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Katakana (0xA1 - 0xDF). Specyficzne dla strona kodowa 932.|  
|[_ismbbkprint —](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Tekst spoza zestawu ASCII lub symbol interpunkcyjny spoza zestawu ASCII. Na przykład w strona kodowa 932 tylko `_ismbbkprint` testów katakana alfanumeryczne lub znaki interpunkcyjne katakana (zakres: 0xA1 - 0xDF).|  
|[_ismbbkpunct —](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Znaki interpunkcyjne spoza zestawu ASCII. Na przykład w strona kodowa 932 tylko `_ismbbkpunct` testów dla katakana znaków interpunkcyjnych.|  
|[_ismbblead —](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|Pierwszy bajt znaków wielobajtowych. Na przykład w kodzie strony 932 tylko, prawidłowe zakresy są 0x81 - 0x9F, wartość 0xE0 - 0xFC.|  
|[_ismbbprint —](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|`isprint` &#124;&#124; `_ismbbkprint`. **ismbbprint —** zawiera znak spacji (0x20).|  
|[_ismbbpunct —](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|`ispunct` &#124;&#124; `_ismbbkpunct`.|  
|[_ismbbtrail —](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Drugi bajt znaków wielobajtowych. Na przykład w kodzie strony 932 tylko, prawidłowe zakresy są 0x40 - 0x7E, 0x80 - 0xEC.|  
  
 W poniższej tabeli przedstawiono ORed wartości, które wchodzą procedury te warunki testu. Stałe manifestu `_BLANK`, `_DIGIT`, `_LOWER`, `_PUNCT`, i `_UPPER` są zdefiniowane w Ctype.h.  
  
|Procedura|_BLANK|_DIGIT|NIŻSZE|_PUNCT|GÓRNY|Z systemem innym niż<br /><br /> ASCII<br /><br /> tekst|Z systemem innym niż<br /><br /> ASCII<br /><br /> punct|  
|-------------|-------------|-------------|-----------|-------------|-----------|------------------------------|-------------------------------|  
|`_ismbbalnum`|—|x|x|—|x|x|—|  
|`_ismbbalpha`|—|—|x|—|x|x|—|  
|`_ismbbblank`|x|—|—|—|—|—|—|  
|`_ismbbgraph`|—|x|x|x|x|x|x|  
|`_ismbbkalnum`|—|—|—|—|—|x|—|  
|`_ismbbkprint`|—|—|—|—|—|x|x|  
|`_ismbbkpunct`|—|—|—|—|—|—|x|  
|`_ismbbprint`|x|x|x|x|x|x|x|  
|`_ismbbpunct`|—|—|—|x|—|—|x|  
  
 `_ismbb` Procedury są wykonywane, funkcji oraz w makra. Aby uzyskać więcej informacji o wybieraniu albo implementacji, zobacz [zalecenia dotyczące wybierania pomiędzy funkcjami i makrami](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasyfikacja bajtów](../c-runtime-library/byte-classification.md)   
 [jest isw — procedury](../c-runtime-library/is-isw-routines.md)   
 [_mbbtombc —, _mbbtombc_l —](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)   
 [_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)