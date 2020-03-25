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
ms.openlocfilehash: 7272170bd3a1e765e728451afc245947111ee947
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171570"
---
# <a name="byte-classification"></a>Klasyfikacja bajtów

Każda z tych procedur testuje określony bajt znaku wielobajtowego w celu spełnienia warunku. O ile nie określono inaczej, wartość wyjściowa jest zależna od ustawienia ustawienia kategorii **LC_CTYPE** ustawień regionalnych; Aby uzyskać więcej informacji, zobacz [setlocals](../c-runtime-library/reference/setlocale-wsetlocale.md) . Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych. wersje z sufiksem **_l** są identyczne, z tą różnicą, że korzystają z przekazaną w zamian parametru ustawień regionalnych.

> [!NOTE]
> Zgodnie z definicją znaki ASCII między 0 a 127 są podzbiorem wszystkich zestawów znaków wielobajtowych. Na przykład japoński zestaw znaków katakana zawiera kod ASCII i znaki inne niż ASCII.

Wstępnie zdefiniowane stałe w poniższej tabeli są zdefiniowane w \<CType. h >.

## <a name="multibyte-character-byte-classification-routines"></a>Wielobajtowe znaki procedury klasyfikacji

|Procedura|Warunek testu bajtowego|
|-------------|-------------------------|
|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|Bajt wiodący; wyniki testu zależą od ustawienia kategorii **LC_CTYPE** bieżących ustawień regionalnych|
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|**isalnum** &#124; isalnum &#124; **_ismbbkalnum**|
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|**_ismbbkalnum** **isalpha** &#124; &#124;|
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|Analogicznie jak **_ismbbprint**, ale **_ismbbgraph** nie zawiera znaku spacji (0x20)|
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Symbol tekstu spoza zestawu ASCII inny niż interpunkcja. Na przykład, na stronie kodowej 932 tylko, **_ismbbkalnum** testy dla znaków alfanumerycznych katakana|
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Katakana (0xA1-0xDF), strona kodowa 932 tylko|
|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Tekst spoza ASCII lub symbol interpunkcyjny spoza ASCII. Na przykład, na stronie kodowej 932, **_ismbbkprint** testy dla interpunkcji alfanumerycznej katakana lub Katakana (zakres: 0XA1-0xDF).|
|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Znaki interpunkcyjne inne niż ASCII. Na przykład, na stronie kodowej 932, **_ismbbkpunct** testy dla interpunkcji katakana.|
|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|Pierwszy bajt znaku wielobajtowego. Na przykład, na stronie kodowej 932, prawidłowymi zakresami są 0x81-0x9F, wartość 0xE0-0xFC.|
|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|&#124; **_ismbbkprint** **isprint** &#124; _ismbbkprint. **ismbbprint** zawiera znak spacji (0x20)|
|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|**ispunct** &#124; ispunct &#124; **_ismbbkpunct**|
|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Drugi bajt znaku wielobajtowego. Na przykład, na stronie kodowej 932, prawidłowymi zakresami są 0x40-0x7E, 0x80-0xEC.|
|[_ismbslead, _ismbslead_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Bajt wiodący (w kontekście ciągu)|
|[ismbstrail, _ismbstrail_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Bajt końcowy (w kontekście ciągu)|
|[_mbbtype, _mbbtype_l](../c-runtime-library/reference/mbbtype-mbbtype-l.md)|Zwracany typ bajtu na podstawie poprzedniego bajtu|
|[_mbsbtype, _mbsbtype_l](../c-runtime-library/reference/mbsbtype-mbsbtype-l.md)|Zwracany typ bajtu w ciągu|
|[mbsinit](../c-runtime-library/reference/mbsinit.md)|Śledzi stan konwersji znaków wielobajtowych.|

Makro **MB_LEN_MAX** zdefiniowane w \<Limits. h > rozszerza maksymalną długość w bajtach, jaką może mieć dowolny znak wielobajtowy. **MB_CUR_MAX**zdefiniowane w \<STDLIB. h > rozszerza do maksymalnej długości w bajtach dowolnego znaku wielobajtowego w bieżącym ustawieniach regionalnych.

## <a name="see-also"></a>Zobacz też

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)
