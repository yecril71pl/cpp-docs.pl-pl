---
title: Interpretacja wielobajtowych sekwencji znaków
ms.date: 10/22/2019
f1_keywords:
- c.character.multibyte
helpviewer_keywords:
- MBCS [C++], locale code page
ms.assetid: da9150de-70ea-4d2f-90e6-ddb9202dd80b
ms.openlocfilehash: 7431f0c63df60414af192ea38103318c775c430d
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811078"
---
# <a name="interpretation-of-multibyte-character-sequences"></a>Interpretacja wielobajtowych sekwencji znaków

Większość procedur znaków wielobajtowych w bibliotece Microsoft Run-Time rozpoznaje sekwencje znaków wielobajtowych odnoszące się do wielobajtowej strony kodowej. Wartość wyjściowa jest zależna od ustawienia ustawienia kategorii **LC_CTYPE** ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych. Wersje z sufiksem **_l** są identyczne, z tą różnicą, że korzystają z parametru locale zamiast bieżących ustawień regionalnych.

## <a name="locale-dependent-multibyte-routines"></a>Procedury wielobajtowe zależne od ustawień regionalnych

|Procedura|Zastosowanie|
|-------------|---------|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Weryfikuj i zwraca liczbę bajtów w znaku wielobajtowego|
|[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|W przypadku ciągów znaków wielobajtowych: Sprawdź poprawność każdego znaku w ciągu; zwraca długość ciągu. Dla ciągów szerokich znaków: zwraca długość ciągu.|
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Konwertuj sekwencję znaków wielobajtowych na odpowiadającą sekwencję szerokich znaków|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Konwertuj znak wielobajtowy na odpowiedni znak szeroki|
|[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Konwertuj sekwencję szerokich znaków do odpowiedniej sekwencji znaków wielobajtowych|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Konwertuj znak szeroki do odpowiedniego znaku wielobajtowego|

## <a name="locale-independent-multibyte-routines"></a>Niezależne od ustawień regionalnych procedury wielobajtowe

|Procedura|Zastosowanie|
|-------------|---------|
|[mbrtoc16, mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|Konwertowanie znaku wielobajtowego UTF-8 na odpowiednik znaku UTF-16 lub UTF-32|
|[c16rtomb, c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|Konwertowanie znaku UTF-16 lub UTF-32 na odpowiednik znaku wielobajtowego UTF-8|

## <a name="see-also"></a>Zobacz także

\ [międzynarodowe](../c-runtime-library/internationalization.md)
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)
