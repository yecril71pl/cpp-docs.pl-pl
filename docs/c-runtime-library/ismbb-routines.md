---
title: _ismbb — procedury | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
dev_langs:
- C++
helpviewer_keywords:
- ismbb routines
- _ismbb routines
ms.assetid: d63c232e-3fe4-4844-aafd-2133846ece4b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86587495353090ced63d0487991f4275d3d0d5d5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092533"
---
# <a name="ismbb-routines"></a>_ismbb — Procedury

Sprawdza daną wartość całkowitą `c` dla określonego warunku, przy użyciu bieżących ustawień regionalnych lub określonej kategorii stanu konwersji LC_CTYPE.

|||
|-|-|
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|
|[_ismbbblank, _ismbbblank_l](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|

## <a name="remarks"></a>Uwagi

Każda procedura w `_ismbb` rodziny sprawdza daną wartość całkowitą `c` dla określonego warunku. Wynik badania jest zależny od stronę kodu wielobajtowego, który jest wynikiem. Domyślnie wielobajtowa strona kodowa jest ustawiona na stronę kodową ANSI uzyskiwaną z systemu operacyjnego w momencie uruchamiania programu. Możesz użyć [_getmbcp](../c-runtime-library/reference/getmbcp.md) utworzyć zapytanie dotyczące stronę kodu wielobajtowego, który jest używany, lub [_setmbcp](../c-runtime-library/reference/setmbcp.md) go zmienić.

Wartość wyjściowa jest zależna od ustawienia `LC_CTYPE` kategorii ustawień regionalnych; Aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Wersje tych funkcji, które nie mają **_l** sufiks używają bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; wersje, które mają **_l** sufiksem są identyczne, z wyjątkiem sytuacji, to zamiast nich Użyj parametru ustawień regionalnych, które zostały przekazane.

Procedury w `_ismbb` rodziny testu danej liczby całkowitej `c` w następujący sposób.

|Procedura|Warunki testu bajtu|
|-------------|-------------------------|
|[_ismbbalnum](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|`isalnum` &#124;&#124; `_ismbbkalnum`.|
|[_ismbbalpha](reference/ismbbalpha-ismbbalpha-l.md)|`isalpha` &#124;&#124; `_ismbbkalnum`.|
|[_ismbbblank](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|`isblank`|
|[_ismbbgraph —](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|Taki sam jak `_ismbbprint`, ale `_ismbbgraph` nie zawiera znaku spacji (0x20).|
|[_ismbbkalnum](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Niż znak interpunkcyjny symbol tekstu spoza zestawu ASCII. Na przykład na stronie kodowej 932 tylko `_ismbbkalnum` testy na znaki katakana alfanumeryczne.|
|[_ismbbkana](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Katakana (0xA1 - 0xDF). Specyficzne dla strony kodu 932.|
|[_ismbbkprint](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Tekst inny niż ASCII lub symbolem interpunkcji spoza zestawu ASCII. Na przykład na stronie kodowej 932 tylko `_ismbbkprint` testy na znaki katakana alfanumeryczne lub katakana interpunkcyjne (zakres: 0xA1 - 0xDF).|
|[_ismbbkpunct](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Znak interpunkcyjny spoza zestawu ASCII. Na przykład na stronie kodowej 932 tylko `_ismbbkpunct` testy na znaki katakana interpunkcyjne.|
|[_ismbblead](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|Pierwszy bajt znaku wielobajtowego. Na przykład na stronie kodowej 932 tylko, prawidłowymi zakresami są 0x81 - 0x9F, 0xE0 — 0xFC.|
|[_ismbbprint](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|`isprint` &#124;&#124; `_ismbbkprint`. **ismbbprint** zawiera znak spacji (0x20).|
|[_ismbbpunct](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|`ispunct` &#124;&#124; `_ismbbkpunct`.|
|[_ismbbtrail](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Drugi bajt znaku wielobajtowego. Na przykład na stronie kodowej 932 tylko, prawidłowymi zakresami są 0x40 - 0x7E, 0x80 - 0xEC.|

W poniższej tabeli przedstawiono wartości / / zsumowanie logiczne, które tworzą warunki sprawdzania dla tych procedur. Stałe manifestu `_BLANK`, `_DIGIT`, `_LOWER`, `_PUNCT`, i `_UPPER` są zdefiniowane w Ctype.h.

|Procedura|_PUSTY|_DIGIT|NIŻSZY|_PUNCT|GÓRNY|Non-<br /><br /> ASCII<br /><br /> tekst|Non-<br /><br /> ASCII<br /><br /> punct|
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

`_ismbb` Procedury są wykonywane zarówno jako funkcje, jak i makra. Aby uzyskać więcej informacji dotyczących sposoby wyboru każdej implementacji, zobacz [zalecenia dotyczące wybierania pomiędzy funkcjami i makrami](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja bajtów](../c-runtime-library/byte-classification.md)<br/>
[is, isw, procedury](../c-runtime-library/is-isw-routines.md)<br/>
[_mbbtombc, _mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)<br/>
[_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)