---
title: Konwersja danych
ms.date: 03/21/2018
f1_keywords:
- c.conversions
helpviewer_keywords:
- data conversion routines [C++]
- converting data
ms.assetid: b15b5268-7467-49f1-bf95-5299b598f94c
ms.openlocfilehash: 94e6a8182e12ecd74f9d2cd5dddaa84a1e3eb847
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218770"
---
# <a name="data-conversion"></a>Konwersja danych

Te procedury konwertują dane z jednej formy na inną. Zwykle te procedury są wykonywane szybciej niż konwersje, które można napisać. Każda procedura rozpoczynająca się od prefiksu *do* jest implementowana jako funkcja i jako makro. Aby uzyskać informacje na temat wybierania implementacji [, zobacz Wybieranie funkcji i makr](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md) .

## <a name="data-conversion-routines"></a>Procedury konwersji danych

|Procedura|Zastosowanie|
|-------------|---------|
|[ABS](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Znajdź wartość bezwzględną liczby całkowitej|
|[atof, _atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Konwertuj ciąg na**`float`**|
|[atoi, _atoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Konwertuj ciąg na**`int`**|
|[_atoi64, _atoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Konwertuj ciąg na **`__int64`** lub**`long long`**|
|[Atol, _atol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Konwertuj ciąg na**`long`**|
|[c16rtomb, c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|Konwertowanie znaku UTF-16 lub UTF-32 na odpowiednik znaku wielobajtowego|
|[_ecvt](../c-runtime-library/reference/ecvt.md), [_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|Konwertuj **`double`** na ciąg o określonej długości|
|[_fcvt](../c-runtime-library/reference/fcvt.md), [_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|Konwertuj **`double`** na ciąg z określoną liczbą cyfr po przecinku|
|[_gcvt](../c-runtime-library/reference/gcvt.md), [_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|Konwertuj **`double`** liczbę na ciąg; Przechowaj ciąg w buforze|
|[_itoa, _ltoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, ultow,](../c-runtime-library/reference/itoa-itow.md)_i64tow, _ui64tow, [_itoa_s, _ltoa_s, _ultoa_s, _i64toa_s, _ui64toa_s, _itow_s, _ltow_s, _ultow_s, _i64tow_s, _ui64tow_s](../c-runtime-library/reference/itoa-s-itow-s.md)|Konwertuj typy całkowite na ciąg|
|[Labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Znajdź wartość bezwzględną **`long`** liczby całkowitej|
|[llabs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Znajdź wartość bezwzględną **`long long`** liczby całkowitej|
|[_mbbtombc, _mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)|Konwertuj 1-bajtowy znak wieloznaczny na odpowiedni dwubajtowy znak wielobajtowy|
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|Konwertowanie znaku w języku Japonia Industry Standard (JIS) na Japonia Microsoft (JMS) znak|
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|Konwertuj znak JMS na znak JIS|
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|Konwertowanie znaku wielobajtowego na 1-bajtowy kod Hiragana|
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|Konwertowanie znaku wielobajtowego na 1-bajtowy kod katakana|
|[_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)|Konwertuj 2-bajtowe znaki wielobajtowe na odpowiadające 1-bajtowe znaki wielobajtowe|
|[mbrtoc16, mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|Konwertowanie znaku wielobajtowego na odpowiednik znaku UTF-16 lub UTF-32|
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Konwertuj sekwencję znaków wielobajtowych na odpowiadającą sekwencję szerokich znaków|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Konwertuj znak wielobajtowy na odpowiedni znak szeroki|
|[strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|Konwertuj ciąg na**`double`**|
|[strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|Konwertuj ciąg na **`long`** liczbę całkowitą|
|[strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|Konwertuj ciąg na **`unsigned long`** liczbę całkowitą|
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|Przekształć ciąg na posortowaną postać na podstawie informacji specyficznych dla ustawień regionalnych|
|[toascii, __toascii](../c-runtime-library/reference/toascii-toascii.md)|Konwertowanie znaku na kod ASCII|
|[ToLower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md), [_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Przetestuj znak i Konwertuj na małe litery, jeśli obecnie są pisane wielką literą|
|[tolower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)|Konwertuj znaki na małe litery bezwarunkowo|
|[ToUpper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md), [_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Przetestuj znak i Konwertuj na wielkie litery, jeśli obecnie jest to małe litery|
|[toupper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|Konwertuj znak na wielkie litery bez warunku|
|[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Konwertuj sekwencję szerokich znaków do odpowiedniej sekwencji znaków wielobajtowych|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Konwertuj znak szeroki do odpowiedniego znaku wielobajtowego|
|[_wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Konwertuj ciąg znaków dwubajtowych na**`double`**|
|[_wtoi, _wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Konwertuj ciąg znaków dwubajtowych na**`int`**|
|[_wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Konwertuj ciąg znaków dwubajtowych na **`__int64`** lub**`long long`**|
|[_wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Konwertuj ciąg znaków dwubajtowych na**`long`**|

## <a name="see-also"></a>Zobacz także

[Procedury środowiska uruchomieniowego języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
