---
title: Klasyfikacja znaków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.types.character
dev_langs:
- C++
helpviewer_keywords:
- character classification routines
- characters, testing
ms.assetid: 3b6c8f0b-9701-407a-b384-9086698773f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7fc19fcdab40dd135338949d1c06ec48cbaf1cca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="character-classification"></a>Klasyfikacja znaków

Każdy z tych procedur testy określonego znaków, znaków typu wide lub znaków wielobajtowych do spełnienia warunku. (Zgodnie z definicją zestaw znaków ASCII od 0 do 127 są podzbiorem wszystkich zestawów znaków wielobajtowych. Na przykład japoński katakana dotyczy również ASCII jako znaki również w innych niż ASCII).

 Ustawienie dotyczy warunkach **lc_ctype —** ustawienie kategorii ustawień regionalnych; zobacz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji bez **_l** Użyj sufiksu bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersje z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych Przekazano zamiast tego.

 Zazwyczaj te procedury szybciej niż testy należy favored za pośrednictwem i zapisu może wykonać. Na przykład następujący kod wykonuje wolniej niż wywołanie `isalpha(c)`:

```C
if ((c >= 'A') && (c <= 'Z')) || ((c >= 'a') && (c <= 'z'))
    return TRUE;
```

## <a name="character-classification-routines"></a>Procedury klasyfikacji znaków

|Procedura|Znak warunku|
|-------------|------------------------------|
|[isalnum —, iswalnum —, _isalnum_l —, _iswalnum_l —](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md), [_ismbcalnum —, _ismbcalnum_l —, _ismbcalpha —, _ismbcalpha_l —, _ismbcdigit —, _ismbcdigit_l —](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfanumeryczne|
|[_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfanumeryczne|
|[isalpha —, iswalpha —, _isalpha_l —, _iswalpha_l —](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md), [_ismbcalnum —, _ismbcalnum_l —, _ismbcalpha —, _ismbcalpha_l —, _ismbcdigit —, _ismbcdigit_l —](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfabetyczne|
|[isascii, __isascii, iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|ASCII|
|[ISBLANK, iswblank, _isblank_l, _iswblank_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md), [_ismbcsblank, _ismbcsblank_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Puste (spację lub tabulator poziomy)|
|[iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|Formant|
|[iscsym —, iscsymf —, __iscsym —, \__iswcsym, \__iscsymf, \__iswcsymf, _iscsym_l —, _iswcsym_l —, _iscsymf_l —, _iswcsymf_l —](../c-runtime-library/reference/iscsym-functions.md)|Litera, podkreślenie lub cyfra|
|[iscsym —, iscsymf —, __iscsym —, \__iswcsym, \__iscsymf, \__iswcsymf, _iscsym_l —, _iswcsym_l —, _iscsymf_l —, _iswcsymf_l —](../c-runtime-library/reference/iscsym-functions.md)|Literą lub podkreśleniem|
|[isdigit —, iswdigit —, _isdigit_l —, _iswdigit_l —](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md), [_ismbcalnum —, _ismbcalnum_l —, _ismbcalpha —, _ismbcalpha_l —, _ismbcdigit —, _ismbcdigit_l —](../c-runtime-library/reference/ismbcalnum-functions.md)|Cyfry dziesiętne|
|[isgraph —, iswgraph —, _isgraph_l —, _iswgraph_l —](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md), [_ismbcgraph —, _ismbcgraph_l —, _ismbcprint —, _ismbcprint_l —, _ismbcpunct —, _ismbcpunct_l —, _ismbcblank, _ismbcblank_l, _ismbcspace —, _ismbcspace_l —](../c-runtime-library/reference/ismbcgraph-functions.md)|Inne niż miejsce drukowania|
|[islower —, iswlower —, _islower_l —, _iswlower_l —](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md), [_ismbclower —, _ismbclower_l —, _ismbcupper —, _ismbcupper_l —](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Małe litery|
|[_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Hiragana|
|[_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Katakana|
|[_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Prawne znaków wielobajtowych|
|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Znaki wielobajtowe 0 Japonii poziomie|
|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Znaki wielobajtowe 1 poziom Japonii|
|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Znaków wielobajtowych 2 Japonii poziomie|
|[_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Inne niż alfanumeryczne znaków wielobajtowych|
|[isprint —, iswprint —, _isprint_l —, _iswprint_l —](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md), [_ismbcgraph —, _ismbcgraph_l —, _ismbcprint —, _ismbcprint_l —, _ismbcpunct —, _ismbcpunct_l —, _ismbcblank, _ismbcblank_l, _ismbcspace —, _ismbcspace_l —](../c-runtime-library/reference/ismbcgraph-functions.md)|Do druku|
|[ispunct —, iswpunct —, _ispunct_l —, _iswpunct_l —](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md), [_ismbcgraph —, _ismbcgraph_l —, _ismbcprint —, _ismbcprint_l —, _ismbcpunct —, _ismbcpunct_l —, _ismbcblank, _ismbcblank_l, _ismbcspace —, _ismbcspace_l —](../c-runtime-library/reference/ismbcgraph-functions.md)|Znaki interpunkcyjne|[System::char::IsPunctuation](https://msdn.microsoft.com/en-us/library/system.char.ispunctuation.aspx)|
|[isspace —, iswspace —, _isspace_l —, _iswspace_l —](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md), [_ismbcgraph —, _ismbcgraph_l —, _ismbcprint —, _ismbcprint_l —, _ismbcpunct —, _ismbcpunct_l —, _ismbcblank, _ismbcblank_l, _ismbcspace —, _ismbcspace_l —](../c-runtime-library/reference/ismbcgraph-functions.md)|Biały znak|[System::char::IsWhiteSpace](https://msdn.microsoft.com/en-us/library/system.char.iswhitespace.aspx)|
|[Isupper —, iswupper —](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md), [_ismbclower —, _ismbclower_l —, _ismbcupper —, _ismbcupper_l —](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Wielkie litery|
|[_isctype, iswctype, _isctype_l, _iswctype_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|Określona przez właściwość *desc* argumentu|
|[isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|Szesnastkowy|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Zwraca długość prawidłowy znaków wielobajtowych; wynik zależy od **lc_ctype —** ustawienie kategorii bieżące ustawienia regionalne|

## <a name="see-also"></a>Zobacz też

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>