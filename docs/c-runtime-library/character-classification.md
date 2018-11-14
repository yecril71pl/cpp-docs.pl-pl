---
title: Klasyfikacja znaków
ms.date: 11/04/2016
f1_keywords:
- c.types.character
helpviewer_keywords:
- character classification routines
- characters, testing
ms.assetid: 3b6c8f0b-9701-407a-b384-9086698773f5
ms.openlocfilehash: b1516aaa5cdb22ecee3895978f1e9c085367a935
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326449"
---
# <a name="character-classification"></a>Klasyfikacja znaków

Każda z tych procedur testuje określony znak Jednobajtowy, znak dwubajtowy lub znak wielobajtowy dla spełnienia warunku. (Zgodnie z definicją, zestaw znaków ASCII od 0 do 127 jest podzestawem wszystkich zestawów znaków wielobajtowych. Na przykład Japonsko-katakana zawiera znaki ASCII oraz jak znaki spoza ASCII.)

Warunki testowe są zależne od ustawienia **LC_CTYPE** ustawienia kategorii ustawień regionalnych; zobacz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji, bez **_l** sufiks używają bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; wersje **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych w zamian przekazanych.

Zazwyczaj procedury te działają szybciej niż testy, można napisać i powinny być preferowane. Na przykład, poniższy kod wykonuje wolniej niż wywołanie `isalpha(c)`:

```C
if ((c >= 'A') && (c <= 'Z')) || ((c >= 'a') && (c <= 'z'))
    return TRUE;
```

## <a name="character-classification-routines"></a>Procedury klasyfikacji znaków

|Procedura|Warunek testu znaków|
|-------------|------------------------------|
|[isalnum, iswalnum —, _isalnum_l —, _iswalnum_l —](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md), [_ismbcalnum —, _ismbcalnum_l —, _ismbcalpha —, _ismbcalpha_l —, _ismbcdigit —, _ismbcdigit_l —](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfanumeryczne|
|[_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfanumeryczne znaków wielobajtowych|
|[isalpha, iswalpha —, _isalpha_l —, _iswalpha_l —](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md), [_ismbcalnum —, _ismbcalnum_l —, _ismbcalpha —, _ismbcalpha_l —, _ismbcdigit —, _ismbcdigit_l —](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfabetyczne|
|[isascii, __isascii, iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|ASCII|
|[ISBLANK, iswblank, _isblank_l, _iswblank_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md), [_ismbcsblank, _ismbcsblank_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Pusty (spacja lub tabulator poziomy)|
|[iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|Formant|
|[iscsym —, iscsymf —, __iscsym —, \__iswcsym, \__iscsymf, \__iswcsymf, _iscsym_l —, _iswcsym_l —, _iscsymf_l —, _iswcsymf_l —](../c-runtime-library/reference/iscsym-functions.md)|Litera, podkreślenie lub cyfra|
|[iscsym —, iscsymf —, __iscsym —, \__iswcsym, \__iscsymf, \__iswcsymf, _iscsym_l —, _iswcsym_l —, _iscsymf_l —, _iswcsymf_l —](../c-runtime-library/reference/iscsym-functions.md)|Litera lub podkreślenie|
|[isdigit, iswdigit —, _isdigit_l —, _iswdigit_l —](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md), [_ismbcalnum —, _ismbcalnum_l —, _ismbcalpha —, _ismbcalpha_l —, _ismbcdigit —, _ismbcdigit_l —](../c-runtime-library/reference/ismbcalnum-functions.md)|Cyfry dziesiętne|
|[isgraph, iswgraph —, _isgraph_l —, _iswgraph_l —](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md), [_ismbcgraph —, _ismbcgraph_l —, _ismbcprint —, _ismbcprint_l —, _ismbcpunct —, _ismbcpunct_l —, _ismbcblank, _ismbcblank_l, _ismbcspace —, _ismbcspace_l —](../c-runtime-library/reference/ismbcgraph-functions.md)|Druku inny niż spacja|
|[islower, iswlower —, _islower_l —, _iswlower_l —](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md), [_ismbclower —, _ismbclower_l —, _ismbcupper —, _ismbcupper_l —](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Małe litery|
|[_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Hiragana|
|[_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Katakana|
|[_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Legalny znak wielobajtowy|
|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Znak wielobajtowy 0 poziomu|
|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Znak wielobajtowy 1 poziomu|
|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Znak wielobajtowy 2 poziomu|
|[_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Niealfanumeryczne znaków wielobajtowych|
|[isprint, iswprint —, _isprint_l —, _iswprint_l —](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md), [_ismbcgraph —, _ismbcgraph_l —, _ismbcprint —, _ismbcprint_l —, _ismbcpunct —, _ismbcpunct_l —, _ismbcblank, _ismbcblank_l, _ismbcspace —, _ismbcspace_l —](../c-runtime-library/reference/ismbcgraph-functions.md)|Druku|
|[ispunct, iswpunct —, _ispunct_l —, _iswpunct_l —](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md), [_ismbcgraph —, _ismbcgraph_l —, _ismbcprint —, _ismbcprint_l —, _ismbcpunct —, _ismbcpunct_l —, _ismbcblank, _ismbcblank_l, _ismbcspace —, _ismbcspace_l —](../c-runtime-library/reference/ismbcgraph-functions.md)|Znaki interpunkcyjne|
|[isspace, iswspace —, _isspace_l —, _iswspace_l —](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md), [_ismbcgraph —, _ismbcgraph_l —, _ismbcprint —, _ismbcprint_l —, _ismbcpunct —, _ismbcpunct_l —, _ismbcblank, _ismbcblank_l, _ismbcspace —, _ismbcspace_l —](../c-runtime-library/reference/ismbcgraph-functions.md)|Znak odstępu|
|[isupper, iswupper —](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md), [_ismbclower —, _ismbclower_l —, _ismbcupper —, _ismbcupper_l —](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Wielkie litery|
|[_isctype, iswctype, _isctype_l, _iswctype_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|Określona przez właściwość *desc* argumentu|
|[isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|Cyfra szesnastkowa|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Zwraca długość prawidłowych znaków wielobajtowych; wynik zależy od **LC_CTYPE** kategorii ustawienia bieżącego ustawienia regionalnego|

## <a name="see-also"></a>Zobacz też

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>