---
title: "_ismbc — procedury | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords: _ismbc
dev_langs: C++
helpviewer_keywords:
- ismbc routines
- _ismbc routines
ms.assetid: b8995391-7857-4ac3-9a1e-de946eb4464d
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8b512bad001ed86ad0720002cd49c54b21b6e555
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ismbc-routines"></a>_ismbc — Procedury
Każdy **_ismbc —** procedury testów danego znaków wielobajtowych `c` dla określonego warunku.  
  
|||  
|-|-|  
|[_ismbcalnum —, _ismbcalnum_l —, _ismbcalpha —, _ismbcalpha_l — _ismbcdigit —, _ismbcdigit_l —](../c-runtime-library/reference/ismbcalnum-functions.md)|[_ismbcl0 —, _ismbcl0_l —, _ismbcl1 —, _ismbcl1_l — _ismbcl2 —, _ismbcl2_l —](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|  
|[_ismbcgraph — _ismbcgraph_l —, _ismbcprint —, _ismbcprint_l —, _ismbcpunct —, _ismbcpunct_l —, _ismbcblank, _ismbcblank_l, _ismbcspace —, _ismbcspace_l —](../c-runtime-library/reference/ismbcgraph-functions.md)|[_ismbclegal —, _ismbclegal_l —, _ismbcsymbol — _ismbcsymbol_l —](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|  
|[_ismbchira —, _ismbchira_l —, _ismbckata — _ismbckata_l —](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|[_ismbclower —, _ismbclower_l —, _ismbcupper — _ismbcupper_l —](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|  
  
## <a name="remarks"></a>Uwagi  
 Wynik testu każdego **_ismbc —** procedura zależy od strony kodowe wielobajtowe obowiązywać. Strony kodowe wielobajtowe ma alfabetyczne znaki jednobajtowe. Strony kodowe wielobajtowe domyślnie system domyślną stronę kodową ANSI uzyskane z systemu operacyjnego podczas uruchamiania programu. Zapytań, lub Zmień strony kodowe wielobajtowe używany z [_getmbcp —](../c-runtime-library/reference/getmbcp.md) lub [_setmbcp —](../c-runtime-library/reference/setmbcp.md)odpowiednio.  
  
 Wartość wyjściowa jest zagrożony `LC_CTYPE` ustawienie kategorii ustawień regionalnych; zobacz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji bez **_l** Użyj sufiksu bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersje z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych Przekazano zamiast tego.  
  
|Procedura|Stan testu|Przykład kodu strony 932|  
|-------------|--------------------|---------------------------|  
|[_ismbcalnum —, _ismbcalnum_l —](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfanumeryczne|Zwraca różną od zera w przypadku i tylko wtedy, gdy `c` odzwierciedla jednobajtowe litery angielskie ASCII: Zobacz przykłady `_ismbcdigit` i `_ismbcalpha`.|  
|[_ismbcalpha —, _ismbcalpha —\_](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfabetyczne|Zwraca różną od zera w przypadku i tylko wtedy, gdy `c` odzwierciedla jednobajtowe litery angielskie ASCII: Zobacz przykłady `_ismbcupper` i `_ismbclower`; lub list katakana: 0xA6 < =`c`< = 0xDF.|  
|[_ismbcdigit —, _ismbcdigit_l —](../c-runtime-library/reference/ismbcalnum-functions.md)|Cyfra|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy `c` odzwierciedla jednobajtowe cyfr ASCII: 0x30 < =`c`< = 0x39.|  
|[_ismbcgraph —, _ismbcgraph_l —](../c-runtime-library/reference/ismbcgraph-functions.md)|Grafika|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy `c` odzwierciedla jednobajtowe znaków ASCII lub katakana drukowania z wyjątkiem (biały znak). Przykłady dla `_ismbcdigit`, `_ismbcalpha`, i `_ismbcpunct`.|  
|[_ismbclegal —, _ismbclegal_l —](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Nieprawidłowa znaków wielobajtowych|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy pierwszy bajt `c` jest w zakresie 0x81-0x9F lub wartość 0xE0 - 0xFC, gdy drugi bajt znajduje się w zakresie 0x40-0x7E lub 0x80 - FC.|  
|[_ismbclower —, _ismbclower_l —](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Małe litery|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy `c` odzwierciedla jednobajtowe małe litery angielskie ASCII: 0x61 < =`c`< = 0x7A.|  
|[_ismbcprint —, _ismbcprint_l —](../c-runtime-library/reference/ismbcgraph-functions.md)|Do druku|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy `c` odzwierciedla jednobajtowe ASCII lub katakana drukowalnych znaków włącznie (biały znak): przykłady dla `_ismbcspace`, `_ismbcdigit`, `_ismbcalpha`, i `_ismbcpunct`.|  
|[_ismbcpunct —, _ismbcpunct_l —](../c-runtime-library/reference/ismbcgraph-functions.md)|Znaki interpunkcyjne|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy `c` odzwierciedla jednobajtowe ASCII lub katakana znak interpunkcyjny.|  
|[_ismbcblank, _ismbcblank_l,](../c-runtime-library/reference/ismbcgraph-functions.md)|Spację lub tabulator poziomy|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy `c` odzwierciedla jednobajtowe znak spacji lub znaku tabulator poziomy: `c`= 0x20 lub `c`= 0x09.|  
|[_ismbcspace —, _ismbcspace_l —](../c-runtime-library/reference/ismbcgraph-functions.md)|Odstępu|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy `c` jest biały znak: `c`= 0x20 lub 0x09 < =`c`< = 0x0D.|  
|[_ismbcsymbol —, _ismbcsymbol_l —](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Symbol wielobajtowe|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy 0x8141 < =`c`< = 0x81AC.|  
|[_ismbcupper —, _ismbcupper_l —](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Wielkie litery|Zwraca wartość niezerową w przypadku i tylko wtedy, gdy `c` odzwierciedla jednobajtowe wielkiej litery angielskie ASCII: 0x41 < =`c`< = 0x5A.|  
  
 **Kod określonych 932 strony**  
  
 Poniższe procedury dotyczą strona kodowa 932.  
  
|Procedura|Testowanie warunku (strona kodowa 932 tylko)|  
|-------------|-------------------------------------------|  
|[_ismbchira —, _ismbchira_l —](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Hiragana znaków dwubajtowych: 0x829F < =`c`< = 0x82F1.|  
|[_ismbckata —, _ismbckata_l —](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Katakana znaków dwubajtowych: 0x8340 < =`c`< = 0x8396.|  
|[_ismbcl0 —, _ismbcl0_l —](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Z systemem innym niż Kanji JIS: 0x8140 < =`c`< = 0x889E.|  
|[_ismbcl1 —, _ismbcl1_l —](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Poziomem JIS-1: 0x889F < =`c`< = 0x9872.|  
|[_ismbcl2 —, _ismbcl2_l —](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Poziomem JIS-2: 0x989F < =`c`< = 0xEA9E.|  
  
 `_ismbcl0`, `_ismbcl1`, i `_ismbcl2` Sprawdź, czy określona wartość `c` dopasowań w warunkach opisanych w poprzednim tabeli, ale nie Sprawdź, czy `c` jest prawidłowym znakiem wielobajtowe. Jeśli niższy bajt jest w zakresach 0x00-0x3F, 0x7F lub 0xFD - 0xFF, te zwracają wartość różną od zera, wskazującą, czy znak spełnia warunek testu. Użyj [_ismbbtrail —, _ismbbtrail_l —](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) Aby sprawdzić, czy znaków wielobajtowych jest zdefiniowany.  
  
 **Strony 932 określonego kodu zakończenia**  
  
## <a name="see-also"></a>Zobacz też  
 [Klasyfikacja znaków](../c-runtime-library/character-classification.md)   
 [jest isw — procedury](../c-runtime-library/is-isw-routines.md)   
 [_ismbb — procedury](../c-runtime-library/ismbb-routines.md)