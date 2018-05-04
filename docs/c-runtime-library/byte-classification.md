---
title: Klasyfikacja bajtów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/04/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.types.bytes
dev_langs:
- C++
helpviewer_keywords:
- code page 932
- byte classification routines
- bytes, testing
ms.assetid: 1cb52d71-fb0c-46ca-aad7-6472c1103370
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f1051ea7b8d4cc3a3f38a5a95f015674ac3e35c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="byte-classification"></a>Klasyfikacja bajtów

Każdy z tych procedur testy określonym bajcie znaków wielobajtowych do spełnienia warunku. Z wyjątkiem w przypadku, gdy określono inaczej, ma to wpływ na wartość wyjściowa przez ustawienie **lc_ctype —** ustawienie kategorii ustawień regionalnych; zobacz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji bez **_l** Użyj sufiksu bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersje z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych Przekazano zamiast tego.

> [!NOTE]
> Zgodnie z definicją od 0 do 127 znaków ASCII są podzbiorem wszystkich zestawów znaków wielobajtowych. Na przykład zestaw znaków japoński katakana zawiera ASCII, a także znaki spoza zestawu ASCII.

Stałe wstępnie zdefiniowane w poniższej tabeli są definiowane w \<ctype.h >.

## <a name="multibyte-character-byte-classification-routines"></a>Procedury klasyfikacji bajtów znaków wielobajtowych

|Procedura|Bajt warunku|
|-------------|-------------------------|
|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|Prowadzić bajt; wynik testu jest zależna od **lc_ctype —** ustawienie kategorii bieżące ustawienia regionalne|
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|**isalnum —** &#124; &#124; **_ismbbkalnum —**|
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|**isalpha —** &#124; &#124; **_ismbbkalnum —**|
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|Taki sam jak **_ismbbprint —**, ale **_ismbbgraph —** nie zawiera znak spacji (0x20)|
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Symbol spoza zestawu ASCII tekstu innego niż znaków interpunkcyjnych. Na przykład w strona kodowa 932 tylko **_ismbbkalnum —** testów dla katakana alfanumeryczne|
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Katakana (0xA1 - 0xDF), strona kodowa 932 tylko|
|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Tekst spoza zestawu ASCII lub symbol interpunkcyjny spoza zestawu ASCII. Na przykład w strona kodowa 932 tylko **_ismbbkprint —** testów katakana alfanumeryczne lub znaki interpunkcyjne katakana (zakres: 0xA1 - 0xDF).|
|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Znaki interpunkcyjne spoza zestawu ASCII. Na przykład w strona kodowa 932 tylko **_ismbbkpunct —** testów dla katakana znaków interpunkcyjnych.|
|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|Pierwszy bajt znaków wielobajtowych. Na przykład w kodzie strony 932 tylko, prawidłowe zakresy są 0x81 - 0x9F, wartość 0xE0 - 0xFC.|
|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|**isprint —** &#124; &#124; **_ismbbkprint —**. **ismbbprint —** zawiera znak spacji (0x20)|
|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|**ispunct —** &#124; &#124; **_ismbbkpunct —**|
|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Drugi bajt znaków wielobajtowych. Na przykład w kodzie strony 932 tylko, prawidłowe zakresy są 0x40 - 0x7E, 0x80 - 0xEC.|
|[_ismbslead —, _ismbslead_l —](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Prowadzić bajtów (w kontekście ciąg)|
|[ismbstrail —, _ismbstrail_l —](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Bajt (w kontekście ciąg)|
|[_mbbtype, _mbbtype_l](../c-runtime-library/reference/mbbtype-mbbtype-l.md)|Oparte na bajt poprzedniego typu zwracanego typu byte|
|[_mbsbtype, _mbsbtype_l](../c-runtime-library/reference/mbsbtype-mbsbtype-l.md)|Zwracany typ bajtów ciągu|
|[mbsinit](../c-runtime-library/reference/mbsinit.md)|Śledzi stan konwersji znaków wielobajtowych.|

**Mb_len_max —** makra zdefiniowane w \<Limits.h — >, rozwijany do maksymalna długość w bajtach, które może zawierać żadnych znaków wielobajtowych. **Mb_cur_max —**zdefiniowanej w \<stdlib.h >, rozwijany do maksymalna długość w bajtach znaków wielobajtowych w bieżących ustawień regionalnych.

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)