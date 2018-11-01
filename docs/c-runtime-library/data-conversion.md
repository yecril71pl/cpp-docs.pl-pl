---
title: Konwersja danych
ms.date: 03/21/2018
f1_keywords:
- c.conversions
helpviewer_keywords:
- data conversion routines [C++]
- converting data
ms.assetid: b15b5268-7467-49f1-bf95-5299b598f94c
ms.openlocfilehash: 070949d064d1835970c1f671cf0e5337342fdca1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547403"
---
# <a name="data-conversion"></a>Konwersja danych

Te procedury konwersji danych z jednego formularza do innego. Zazwyczaj procedury te działają szybciej niż konwersji, który może zapisać. Każdej procedury, która rozpoczyna się od *do* prefiks jest implementowana jako funkcja i makra. Zobacz [wybierania pomiędzy funkcjami i makrami](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md) informacji o wybieraniu implementację.

## <a name="data-conversion-routines"></a>Procedur konwersji danych

|Procedura|Zastosowanie|
|-------------|---------|
|[ABS](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Znajdź wartość bezwzględną liczby całkowitej|
|[atof, _atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Konwertuj ciąg na na **float**|
|[atoi, _atoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Konwertuj ciąg na na **int**|
|[_atoi64, _atoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Konwertuj ciąg na na **__int64** lub **długi długi**|
|[atol, _atol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Konwertuj ciąg na na **długi**|
|[c16rtomb, c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|Konwertuj znaku UTF-16 lub UTF-32 na równoważne znak wielobajtowy|
|[_ecvt](../c-runtime-library/reference/ecvt.md), [_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|Konwertuj **double** ciąg znaków o określonej długości.|
|[_fcvt](../c-runtime-library/reference/fcvt.md), [_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|Konwertuj **double** na ciąg przy użyciu określonej liczby cyfr od punktu dziesiętnego|
|[_gcvt](../c-runtime-library/reference/gcvt.md), [_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|Konwertuj **double** liczbę na ciąg; przechowywanie parametrów w buforze|
|[_itoa, _ltoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, ultow, _i64tow, _ui64tow](../c-runtime-library/reference/itoa-itow.md), [_itoa_s, _ltoa_s, _ultoa_s, _i64toa_s, _ui64toa_s, _itow_s, _ltow_s, _ultow_s, _i64tow_s, _ui64tow_s](../c-runtime-library/reference/itoa-s-itow-s.md)|Konwertowanie typów całkowitych na ciąg|
|[Warsztaty](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Znajdź wartość bezwzględną liczby **długie** liczba całkowita|
|[llabs —](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Znajdź wartość bezwzględną liczby **long long** liczba całkowita|
|[_mbbtombc, _mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)|Konwertuj 1-bajtowe znak wielobajtowy do odpowiedniego znaku wielobajtowego 2-bajtowych|
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|Konwertuj znak Japan Industry Standard (JIS) na znak Japan firmy Microsoft (JMS)|
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|Konwertuj JMS znak JIS znak|
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|Konwertuj znaków wielobajtowych do kodu hiragana 1-bajtowe|
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|Konwertuj znaków wielobajtowych do 1-bajtowe znaki katakana kodu|
|[_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)|Konwertuj 2-bajtowych znak wielobajtowy do odpowiedniego znaku wielobajtowego 1-bajtowe|
|[mbrtoc16, mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|Znak wielobajtowy, który należy przekonwertować odpowiadające znaki UTF-16 lub UTF-32|
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Konwertowanie sekwencji znaków wielobajtowych do odpowiedniej sekwencji znaków dwubajtowych|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Konwertuj znak wielobajtowy do odpowiedniego znaku dwubajtowego|
|[strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|Konwertuj ciąg na na **double**|
|[strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|Konwertuj ciąg na na **długie** liczba całkowita|
|[strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|Konwertuj ciąg na na **unsigned long** liczba całkowita|
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|Przekształć ciąg w postaci sortowany w oparciu o informacje specyficzne dla ustawień regionalnych|
|[toascii, __toascii](../c-runtime-library/reference/toascii-toascii.md)|Konwertuj znak kodowi ASCII||
|[tolower, _tolower —, towlower —, _tolower_l —, _towlower_l —](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md), [_mbctolower —, _mbctolower_l —, _mbctoupper —, _mbctoupper_l —](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Testowanie znaków i przekonwertowania na małe litery, jeśli jest to obecnie wielkie litery|
|[tolower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)|Konwertuj znaków na małe litery, bezwarunkowo|[System::String::ToLower](https://msdn.microsoft.com/library/system.string.tolower.aspx)|
|[toupper, _toupper —, towupper —, _toupper_l —, _towupper_l —](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md), [_mbctolower —, _mbctolower_l —, _mbctoupper —, _mbctoupper_l —](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Testowanie znaków i przekonwertowania na wielkie litery, jeśli jest to obecnie małe litery|
|[toupper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|Konwertuj znaków na wielkie litery bezwarunkowo|
|[wcstombs —, _wcstombs_l —](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s —, _wcstombs_s_l —](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Konwertowanie sekwencji znaków dwubajtowych do odpowiedniej sekwencji znaków wielobajtowych|
|[wctomb —, _wctomb_l —](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s —, _wctomb_s_l —](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Konwertuj szerokich znaków do odpowiedniego znaku wielobajtowego|
|[_wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Konwertuj ciąg znaków dwubajtowych **double**|
|[_wtoi —, _wtoi_l —](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Konwertuj ciąg znaków dwubajtowych **int**|
|[_wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Konwertuj ciąg znaków dwubajtowych **__int64** lub **długi długi**|
|[_wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Konwertuj ciąg znaków dwubajtowych **długi**|

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
