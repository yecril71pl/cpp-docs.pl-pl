---
title: Interpretacja wielobajtowych sekwencji znaków
ms.date: 04/11/2018
f1_keywords:
- c.character.multibyte
helpviewer_keywords:
- MBCS [C++], locale code page
ms.assetid: da9150de-70ea-4d2f-90e6-ddb9202dd80b
ms.openlocfilehash: 79d053029edcb357f791dade1ec20f562dce3c16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615002"
---
# <a name="interpretation-of-multibyte-character-sequences"></a>Interpretacja wielobajtowych sekwencji znaków

Większość obsługi znaków wielobajtowych w bibliotece wykonawczej Microsoft rozpoznaje sekwencje znaków wielobajtowych odnoszących się do strony kodowe wielobajtowe. Wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** ustawienia kategorii ustawień regionalnych; zobacz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji, bez **_l** sufiks używają bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; wersje **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych w zamian przekazanych.

## <a name="locale-dependent-multibyte-routines"></a>Procedury wielobajtowych zależne od ustawień regionalnych

|Procedura|Zastosowanie|
|-------------|---------|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Zweryfikuj i zwraca liczbę bajtów w znaków wielobajtowych|
|[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|Dla ciągów znaków wielobajtowych: Sprawdź poprawność każdego znaku w ciągu; Zwraca długość ciągu. Ciągi znaków dwubajtowych: zwraca długość ciągu.|
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Konwertowanie sekwencji znaków wielobajtowych do odpowiedniej sekwencji znaków dwubajtowych|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Konwertuj znak wielobajtowy do odpowiedniego znaku dwubajtowego|
|[wcstombs —, _wcstombs_l —](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s —, _wcstombs_s_l —](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Konwertowanie sekwencji znaków dwubajtowych do odpowiedniej sekwencji znaków wielobajtowych|
|[wctomb —, _wctomb_l —](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s —, _wctomb_s_l —](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Konwertuj szerokich znaków do odpowiedniego znaku wielobajtowego|
|[mbrtoc16, mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|Znak wielobajtowy, który należy przekonwertować odpowiadające znaki UTF-16 lub UTF-32|
|[c16rtomb, c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|Konwertuj znaku UTF-16 lub UTF-32 na równoważne znak wielobajtowy|

## <a name="see-also"></a>Zobacz też

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
