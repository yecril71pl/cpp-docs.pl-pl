---
title: Klasyfikacja bajtów
ms.date: 04/04/2018
f1_keywords:
- c.types.bytes
helpviewer_keywords:
- code page 932
- byte classification routines
- bytes, testing
ms.assetid: 1cb52d71-fb0c-46ca-aad7-6472c1103370
ms.openlocfilehash: 9c00d0c0165bdae15ba5fc413d00a99bf4601b21
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290277"
---
# <a name="byte-classification"></a>Klasyfikacja bajtów

Każda z tych procedur testuje określoną liczbę bajtów z znak wielobajtowy dla spełnienia warunku. Z wyjątkiem w przypadku, gdy określono inaczej, wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** ustawienia kategorii ustawień regionalnych; zobacz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji, bez **_l** sufiks używają bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; wersje **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych w zamian przekazanych.

> [!NOTE]
> Zgodnie z definicją znaki ASCII od 0 do 127 jest podzestawem wszystkich zestawów znaków wielobajtowych. Na przykład zestaw znaków Japonsko-katakana zawiera ASCII, a także znaki spoza zestawu ASCII.

Wstępnie zdefiniowanych stałych w poniższej tabeli są zdefiniowane w \<ctype.h >.

## <a name="multibyte-character-byte-classification-routines"></a>Procedury klasyfikacji bajtów znaków wielobajtowych

|Procedura|Warunki testu bajtu|
|-------------|-------------------------|
|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|Bajt; wynik badania jest zależny od **LC_CTYPE** kategorii ustawienia bieżącego ustawienia regionalnego|
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|**isalnum** &#124; &#124; **_ismbbkalnum —**|
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|**isalpha** &#124; &#124; **_ismbbkalnum —**|
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|Taki sam jak **_ismbbprint —**, ale **_ismbbgraph —** nie zawiera znaku spacji (0x20)|
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Niż znak interpunkcyjny symbol tekstu spoza zestawu ASCII. Na przykład na stronie kodowej 932 tylko **_ismbbkalnum —** testy na znaki katakana alfanumeryczne|
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Katakana (0xA1 - 0xDF), strona kodowa 932 tylko|
|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Tekst inny niż ASCII lub symbolem interpunkcji spoza zestawu ASCII. Na przykład na stronie kodowej 932 tylko **_ismbbkprint —** testy na znaki katakana alfanumeryczne lub katakana interpunkcyjne (zakres: 0xA1 - 0xDF).|
|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Znak interpunkcyjny spoza zestawu ASCII. Na przykład na stronie kodowej 932 tylko **_ismbbkpunct —** testy na znaki katakana interpunkcyjne.|
|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|Pierwszy bajt znaku wielobajtowego. Na przykład na stronie kodowej 932 tylko, prawidłowymi zakresami są 0x81 - 0x9F, 0xE0 — 0xFC.|
|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|**isprint** &#124; &#124; **_ismbbkprint —**. **ismbbprint** zawiera znak spacji (0x20)|
|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|**ispunct** &#124; &#124; **_ismbbkpunct —**|
|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Drugi bajt znaku wielobajtowego. Na przykład na stronie kodowej 932 tylko, prawidłowymi zakresami są 0x40 - 0x7E, 0x80 - 0xEC.|
|[_ismbslead —, _ismbslead_l —](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Bajt (w kontekście ciąg)|
|[ismbstrail —, _ismbstrail_l —](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Bajt (w kontekście ciąg)|
|[_mbbtype, _mbbtype_l](../c-runtime-library/reference/mbbtype-mbbtype-l.md)|Typ zwracany bajt oparte na poprzednich bajtowych|
|[_mbsbtype, _mbsbtype_l](../c-runtime-library/reference/mbsbtype-mbsbtype-l.md)|Zwracany typ bajtu wewnątrz ciągu|
|[mbsinit](../c-runtime-library/reference/mbsinit.md)|Śledzi stan konwersji znaków wielobajtowych.|

**MB_LEN_MAX** makro, zdefiniowane w \<limits.h >, rozszerza się do maksymalnej długości w bajtach, jaką może mieć jakiegokolwiek znaku wielobajtowego. **MB_CUR_MAX**zdefiniowaną w \<stdlib.h >, rozszerza się do maksymalnej długości w bajtach jakiegokolwiek znaku wielobajtowego przy bieżących ustawieniach regionalnych.

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)