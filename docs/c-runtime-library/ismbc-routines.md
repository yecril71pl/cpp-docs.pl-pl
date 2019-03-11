---
title: _ismbc — Procedury
ms.date: 11/04/2016
apilocation:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- _ismbc
helpviewer_keywords:
- ismbc routines
- _ismbc routines
ms.assetid: b8995391-7857-4ac3-9a1e-de946eb4464d
ms.openlocfilehash: dd187be93b5df0160686fe765f65c25e14800b75
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748687"
---
# <a name="ismbc-routines"></a>_ismbc — Procedury

Każdy **_ismbc** procedury testuje dany znak wielobajtowy `c` dla określonego warunku.

|||
|-|-|
|[_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|
|[_ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|[_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|
|[_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|[_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|

## <a name="remarks"></a>Uwagi

Wynik testu każdego **_ismbc** rutyny zależnej od stronę kodu wielobajtowego w praktyce. Wielobajtowe strony kodowe mają jednobajtowe znaki alfabetu. Domyślnie wielobajtowa strona kodowa jest ustawiona na stronę kodową ANSI systemu domyślnego uzyskiwaną z systemu operacyjnego w momencie uruchamiania programu. Można zbadać lub zmienić stronę kodu wielobajtowego w użyciu [_getmbcp](../c-runtime-library/reference/getmbcp.md) lub [_setmbcp](../c-runtime-library/reference/setmbcp.md), odpowiednio.

Wartość wyjściowa jest zależna od `LC_CTYPE` ustawienia kategorii ustawień regionalnych; zobacz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji, bez **_l** sufiks używają bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; wersje **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych w zamian przekazanych.

|Procedura|Testowanie warunku|Przykład strony kodu 932|
|-------------|--------------------|---------------------------|
|[_ismbcalnum —, _ismbcalnum_l —](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfanumeryczne|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy `c` jest reprezentacją jednobajtowego jednobajtową litery angielskiej ASCII: Zobacz przykłady dla `_ismbcdigit` i `_ismbcalpha`.|
|[_ismbcalpha —, _ismbcalpha_l —](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfabetyczne|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy `c` jest reprezentacją jednobajtowego jednobajtową litery angielskiej ASCII: Zobacz przykłady dla `_ismbcupper` i `_ismbclower`; lub literę katakana: 0xA6<=`c`<=0xDF.|
|[_ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|cyfra|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy `c` jest reprezentacją jednobajtowego cyfr ASCII: 0x30<=`c`<=0x39.|
|[_ismbcgraph —, _ismbcgraph_l —](../c-runtime-library/reference/ismbcgraph-functions.md)|Grafika|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy `c` jest reprezentacją jednobajtowego znaku wszelkie ASCII lub katakana drukowalnego z wyjątkiem (biały). Zobacz przykłady dla `_ismbcdigit`, `_ismbcalpha`, i `_ismbcpunct`.|
|[_ismbclegal —, _ismbclegal_l —](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Prawidłowy znak wielobajtowy|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy pierwszy bajt `c` znajduje się w zakresach 0x81-0x9F lub wartość 0xE0 — 0xFC, podczas gdy drugi bajt jest w zakresach 0x40-0x7E lub 0x80 - FC.|
|[_ismbclower —, _ismbclower_l —](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Małe litery alfabetycznie|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy `c` jest reprezentacją jednobajtowego małe litery angielskiej ASCII: 0x61<=`c`<=0x7A.|
|[_ismbcprint, _ismbcprint_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Druku|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy `c` jest reprezentacją jednobajtowego jakiegokolwiek ASCII lub katakana znaku drukowalnego łącznie (biały): Zobacz przykłady dla `_ismbcspace`, `_ismbcdigit`, `_ismbcalpha`, i `_ismbcpunct`.|
|[_ismbcpunct —, _ismbcpunct_l —](../c-runtime-library/reference/ismbcgraph-functions.md)|Znaki interpunkcyjne|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy `c` jest reprezentacją jednobajtowego ASCII lub katakana znak interpunkcyjny.|
|[_ismbcblank, _ismbcblank_l,](../c-runtime-library/reference/ismbcgraph-functions.md)|SPACJA lub tabulator|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy `c` jest reprezentacją jednobajtowego znaku spacji lub znaku tabulacji poziomej: `c`= 0x20 lub `c`= 0x09.|
|[_ismbcspace —, _ismbcspace_l —](../c-runtime-library/reference/ismbcgraph-functions.md)|Białe znaki|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy `c` to znak odstępu: `c`= 0x20 lub 0x09 < =`c`< = 0x0D.|
|[_ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Symbol wielobajtowy|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy 0x8141 < =`c`< = 0x81AC.|
|[_ismbcupper —, _ismbcupper_l —](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Wielkie litery alfabetycznie|Zwraca wartość różną od zera wtedy i tylko wtedy, gdy `c` jest reprezentacją jednobajtowego wielkie litery angielskiej ASCII: 0x41<=`c`<=0x5A.|

**Dla strony kodu 932**

Poniższe procedury są specyficzne dla strony kodu 932.

|Procedura|Testowanie warunku (strona kodowa 932 tylko)|
|-------------|-------------------------------------------|
|[_ismbchira —, _ismbchira_l —](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Znaki dwubajtowe Hiragana: 0x829F<=`c`<=0x82F1.|
|[_ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Znaki dwubajtowe katakana: 0x8340<=`c`<=0x8396.|
|[_ismbcl0 —, _ismbcl0_l —](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Kanji-JIS niż: 0x8140<=`c`<=0x889E.|
|[_ismbcl1 —, _ismbcl1_l —](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Poziom JIS-1: 0x889F<=`c`<=0x9872.|
|[_ismbcl2 —, _ismbcl2_l —](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Poziom JIS-2: 0x989F<=`c`<=0xEA9E.|

`_ismbcl0`, `_ismbcl1`, i `_ismbcl2` Sprawdź, czy określona wartość `c` dopasowuje warunki badania opisane w poprzedniej tabeli, le nie sprawdzają, czy `c` jest prawidłowym znakiem wielobajtowym. Jeśli niższy bajt jest w zakresach 0x00-0x3F, 0x7F lub 0xFD - 0xFF, te funkcje zwracają wartość różną od zera, wskazując, że znak spełnia warunek testu. Użyj [_ismbbtrail, _ismbbtrail_l —](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) do sprawdzenia, czy zdefiniowano znaki wielobajtowe.

**ZAKOŃCZENIA dla strony kodu 932**

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../c-runtime-library/character-classification.md)<br/>
[is, isw, procedury](../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb, procedury](../c-runtime-library/ismbb-routines.md)
