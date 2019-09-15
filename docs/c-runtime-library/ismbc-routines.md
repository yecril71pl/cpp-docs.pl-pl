---
title: _ismbc — Procedury
ms.date: 11/04/2016
api_location:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbc
helpviewer_keywords:
- ismbc routines
- _ismbc routines
ms.assetid: b8995391-7857-4ac3-9a1e-de946eb4464d
ms.openlocfilehash: 6dc14f269cafa8ccc343c5403ab0e23d319c71c3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940168"
---
# <a name="_ismbc-routines"></a>_ismbc — Procedury

Każda procedura **_ismbc** testuje dany znak `c` wielobajtowy dla określonego warunku.

|||
|-|-|
|[_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|
|[_ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|[_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|
|[_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|[_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|

## <a name="remarks"></a>Uwagi

Wynik testu dla każdej procedury **_ismbc** zależy od strony kodu wielobajtowego. Strony kodowe wielobajtowe mają jednobajtowe znaki alfabetu. Domyślnie strona kodowa wielobajtowego jest ustawiona na stronę kodową ANSI w systemie, uzyskaną od systemu operacyjnego podczas uruchamiania programu. Można wykonywać zapytania lub zmieniać stronę kodową wielobajtowego odpowiednio do [_getmbcp](../c-runtime-library/reference/getmbcp.md) lub [_setmbcp](../c-runtime-library/reference/setmbcp.md).

Wartość wyjściowa jest zależna `LC_CTYPE` od ustawienia kategorii ustawień regionalnych; zobacz [setlocaling](../c-runtime-library/reference/setlocale-wsetlocale.md) , aby uzyskać więcej informacji. Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych. wersje z sufiksem **_l** są identyczne, z tą różnicą, że w zamian korzystają z przekazaną parametrem ustawień regionalnych.

|Procedura|Warunek testu|Przykładowa strona kodowa 932|
|-------------|--------------------|---------------------------|
|[_ismbcalnum, _ismbcalnum_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Pełnej|Zwraca wartość różną od zera, jeśli `c` i tylko wtedy, gdy jest reprezentacją jednobajtowej litery angielskiej ASCII: Zobacz przykłady dla `_ismbcdigit` i `_ismbcalpha`.|
|[_ismbcalpha, _ismbcalpha_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfabetyczne|Zwraca wartość różną od zera, jeśli `c` i tylko wtedy, gdy jest reprezentacją jednobajtowej litery angielskiej ASCII: Zobacz przykłady dla `_ismbcupper` i `_ismbclower`; lub literę katakana: 0xA6<=`c`<=0xDF.|
|[_ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Kontrol|Zwraca wartość różną od zera, jeśli `c` i tylko wtedy, gdy jest reprezentacją jednobajtowej cyfry ASCII: 0x30 < =`c`< = 0x39.|
|[_ismbcgraph, _ismbcgraph_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Graphic|Zwraca wartość różną od zera, jeśli `c` i tylko wtedy, gdy jest reprezentacją dowolnego znaku ASCII lub Katakana drukowalnego, z wyjątkiem odstępu (). Zobacz przykłady dla `_ismbcdigit`, `_ismbcalpha`, i `_ismbcpunct`.|
|[_ismbclegal, _ismbclegal_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Prawidłowy znak wielobajtowy|Zwraca wartość różną od zera, jeśli i tylko wtedy, `c` gdy pierwszy bajt jest w zakresie 0x81-0x9F lub wartość 0xE0-0xFC, podczas gdy drugi bajt znajduje się w zakresie 0x40-0x7E lub 0x80-FC.|
|[_ismbclower, _ismbclower_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Małe litery alfabetu|Zwraca wartość różną od zera, jeśli `c` i tylko wtedy, gdy jest reprezentacją jednobajtowej litery alfabetu angielskiego w formacie ASCII: 0x61<=`c`<=0x7A.|
|[_ismbcprint, _ismbcprint_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Drukowalnych|Zwraca wartość różną od zera, jeśli `c` i tylko wtedy, gdy jest reprezentacją dowolnego znaku ASCII lub Katakana drukowalnego, w tym odstępu (): Zobacz przykłady dla `_ismbcspace`, `_ismbcdigit`, `_ismbcalpha`i. `_ismbcpunct`|
|[_ismbcpunct, _ismbcpunct_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Znaki interpunkcyjne|Zwraca wartość różną od zera, jeśli `c` i tylko wtedy, gdy jest reprezentacją pojedynczego bajtu znaków interpunkcyjnych ASCII lub Katakana.|
|[_ismbcblank, _ismbcblank_l,](../c-runtime-library/reference/ismbcgraph-functions.md)|Spacja lub tabulator poziomy|Zwraca wartość różną od zera, jeśli `c` i tylko wtedy, gdy jest reprezentacją jednobajtowego znaku spacji lub znaku `c`tabulacji poziomej: = 0x20 lub `c`= 0x09.|
|[_ismbcspace, _ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Odstępu|Zwraca wartość różną od zera, jeśli `c` i tylko wtedy, gdy jest `c`znakiem odstępu: =`c`0x20 lub 0x09 < = < = 0x0D.|
|[_ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Symbol wielobajtowy|Zwraca wartość różną od zera, jeśli i tylko wtedy`c`, gdy 0x8141 < = < = 0x81AC.|
|[_ismbcupper, _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Wielkie litery|Zwraca wartość różną od zera, jeśli `c` i tylko wtedy, gdy jest reprezentacją jednobajtowej wielkiej litery alfabetu ASCII: 0x41 < =`c`< = 0x5a.|

**Specyficzne dla strony kodowej 932**

Poniższe procedury są specyficzne dla strony kodowej 932.

|Procedura|Warunek testu (tylko strona kodowa 932)|
|-------------|-------------------------------------------|
|[_ismbchira, _ismbchira_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Podwójne bajty Hiragana: 0x829F < =`c`< = 0x82F1.|
|[_ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Dwubajtowa katakana: 0x8340<=`c`<=0x8396.|
|[_ismbcl0, _ismbcl0_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS nie Kanji: 0x8140<=`c`<=0x889E.|
|[_ismbcl1, _ismbcl1_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Poziom JIS-1: 0x889F < =`c`< = 0x9872.|
|[_ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Poziom JIS-2: 0x989F<=`c`<=0xEA9E.|

`_ismbcl0`, `_ismbcl1` `c` `c` i `_ismbcl2` sprawdzają, czy określona wartość jest zgodna z warunkami testu opisanymi w powyższej tabeli, ale nie sprawdzają, czy jest prawidłowym znakiem wielobajtowym. Jeśli dolny bajt znajduje się w zakresach 0x00-0x3F, 0x7F lub 0xFD-0xFF, te funkcje zwracają wartość różną od zera, wskazując, że znak spełnia warunek testu. Użyj [_ismbbtrail, _ismbbtrail_l,](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) aby sprawdzić, czy jest zdefiniowany znak wielobajtowy.

**Konkretna strona kodowa 932**

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../c-runtime-library/character-classification.md)<br/>
[is, isw, procedury](../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb, procedury](../c-runtime-library/ismbb-routines.md)
