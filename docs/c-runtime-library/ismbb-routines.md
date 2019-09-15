---
title: _ismbb — Procedury
ms.date: 11/04/2016
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbb
- ismbb
helpviewer_keywords:
- ismbb routines
- _ismbb routines
ms.assetid: d63c232e-3fe4-4844-aafd-2133846ece4b
ms.openlocfilehash: 374c78ca222f9c63f6b37f26d4cf3a00f48f845e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944529"
---
# <a name="_ismbb-routines"></a>_ismbb — Procedury

Testuje daną wartość `c` całkowitą dla określonego warunku przy użyciu bieżących ustawień regionalnych lub określonych kategorii stanu konwersji LC_CTYPE.

|||
|-|-|
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|
|[_ismbbblank, _ismbbblank_l](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|

## <a name="remarks"></a>Uwagi

Każda procedura w `_ismbb` rodzinie testuje daną wartość `c` całkowitą dla określonego warunku. Wynik testu zależy od strony kodu wielobajtowego, która obowiązuje. Domyślnie strona kodowa wielobajtowego jest ustawiona na stronę kodową ANSI, która jest uzyskiwana z systemu operacyjnego podczas uruchamiania programu. Możesz użyć [_getmbcp](../c-runtime-library/reference/getmbcp.md) , aby wykonać zapytanie o stronę kodową wielobajtowego, która jest używana, lub [_setmbcp](../c-runtime-library/reference/setmbcp.md) , aby ją zmienić.

Wartość wyjściowa jest zależna od ustawienia `LC_CTYPE` kategorii ustawień regionalnych; Aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Wersje tych funkcji, które nie mają sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych; wersje, które mają sufiks **_l** są identyczne, z tą różnicą, że zamiast nich używają parametru ustawień regionalnych, który jest przesyłany.

Procedury w `_ismbb` rodzinie testują daną liczbę całkowitą `c` w następujący sposób.

|Procedura|Warunek testu bajtowego|
|-------------|-------------------------|
|[_ismbbalnum](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|`isalnum` &#124;&#124; `_ismbbkalnum`.|
|[_ismbbalpha](reference/ismbbalpha-ismbbalpha-l.md)|`isalpha` &#124;&#124; `_ismbbkalnum`.|
|[_ismbbblank](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|`isblank`|
|[_ismbbgraph](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|Taki sam `_ismbbprint`jak, `_ismbbgraph` ale nie zawiera znaku spacji (0x20).|
|[_ismbbkalnum](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Symbol tekstu spoza zestawu ASCII inny niż interpunkcja. Na przykład, na stronie kodowej 932, `_ismbbkalnum` testy dla znaków alfanumerycznych katakana.|
|[_ismbbkana](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Katakana (0xA1-0xDF). Specyficzne dla strony kodowej 932.|
|[_ismbbkprint](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Tekst spoza ASCII lub symbol interpunkcyjny spoza ASCII. Na przykład, na stronie kodowej 932 tylko `_ismbbkprint` , testy dla interpunkcji alfanumerycznej katakana lub Katakana (zakres: 0xA1 – 0xDF).|
|[_ismbbkpunct](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Znaki interpunkcyjne inne niż ASCII. Na przykład, na stronie kodowej 932 tylko `_ismbbkpunct` , testy dla interpunkcji katakana.|
|[_ismbblead](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|Pierwszy bajt znaku wielobajtowego. Na przykład, na stronie kodowej 932, prawidłowymi zakresami są 0x81-0x9F, wartość 0xE0-0xFC.|
|[_ismbbprint](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|`isprint` &#124;&#124; `_ismbbkprint`. **ismbbprint** zawiera znak spacji (0x20).|
|[_ismbbpunct](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|`ispunct` &#124;&#124; `_ismbbkpunct`.|
|[_ismbbtrail](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Drugi bajt znaku wielobajtowego. Na przykład, na stronie kodowej 932, prawidłowymi zakresami są 0x40-0x7E, 0x80-0xEC.|

W poniższej tabeli przedstawiono wartości logicznie, które tworzą warunki testu dla tych procedur. Stałe `_BLANK`manifestu `_DIGIT` ,`_PUNCT`,, i`_UPPER` są zdefiniowane w CType. h. `_LOWER`

|Procedura|_BLANK|_DIGIT|DOŁU|_PUNCT|PRAWYM GÓRNYM|Które<br /><br /> ASCII<br /><br /> tekst|Które<br /><br /> ASCII<br /><br /> punct|
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

`_ismbb` Procedury są implementowane zarówno jako funkcje, jak i makra. Aby uzyskać więcej informacji na temat wybierania implementacji, zobacz [zalecenia dotyczące wybierania funkcji i makr](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja bajtów](../c-runtime-library/byte-classification.md)<br/>
[is, isw, procedury](../c-runtime-library/is-isw-routines.md)<br/>
[_mbbtombc, _mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)<br/>
[_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)
