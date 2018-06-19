---
title: Konwersja danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/21/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- c.conversions
dev_langs:
- C++
helpviewer_keywords:
- data conversion routines [C++]
- converting data
ms.assetid: b15b5268-7467-49f1-bf95-5299b598f94c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a0260ebe37e0656f2078b247017d9f02ccc88474
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392448"
---
# <a name="data-conversion"></a>Konwersja danych

Te procedury konwersji danych z jednego formularza do innego. Zazwyczaj te procedury wykonywania szybciej niż konwersje, który może zapisać. Każda procedura zaczyna się od *do* prefiks jest zaimplementowany jako funkcję, a makra. Zobacz [wybierania pomiędzy funkcjami i makrami](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md) informacji o wybieraniu implementację.

## <a name="data-conversion-routines"></a>Procedury konwersji danych

|Procedura|Zastosowanie|
|-------------|---------|
|[ABS](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Zwraca wartość bezwzględną liczby całkowitej|
|[atof, _atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Konwertuj ciąg **liczb zmiennoprzecinkowych**|
|[atoi, _atoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Konwertowanie ciągu na **int**|
|[_atoi64, _atoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Konwertowanie ciągu na **__int64** lub **długi czas**|
|[atol, _atol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Konwertowanie ciągu na **długa**|
|[c16rtomb, c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|Konwertuj UTF-16 lub UTF-32 znaków na równoważne znaków wielobajtowych|
|[_ecvt](../c-runtime-library/reference/ecvt.md), [_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|Konwertuj **podwójne** ciąg znaków o określonej długości|
|[_fcvt](../c-runtime-library/reference/fcvt.md), [_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|Konwertuj **podwójne** do ciągu określonej liczby cyfr od punktu dziesiętnego|
|[_gcvt](../c-runtime-library/reference/gcvt.md), [_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|Konwertuj **podwójne** liczbę na ciąg; przechowywanie parametrów w buforze|
|[_itoa, _ltoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, ultow, _i64tow, _ui64tow](../c-runtime-library/reference/itoa-itow.md), [_itoa_s, _ltoa_s, _ultoa_s, _i64toa_s, _ui64toa_s, _itow_s, _ltow_s, _ultow_s, _i64tow_s, _ui64tow_s](../c-runtime-library/reference/itoa-s-itow-s.md)|Konwertowanie typów całkowitych na ciąg|
|[Labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Zwraca wartość bezwzględną **długi** liczba całkowita|
|[llabs —](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Zwraca wartość bezwzględną **długi czas** liczba całkowita|
|[_mbbtombc, _mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)|Konwertuj znaków wielobajtowych 1-bajtowych na odpowiednich 2-bajtowych znaków wielobajtowych|
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|Konwertuj znak Japonii branżowy Standard (JIS) na znak Japonii firmy Microsoft (JMS)|
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|Konwertuj JMS znaków JIS znaków|
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|Konwertuj znaków wielobajtowych hiragana 1-bajtowy kodu|
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|Konwertuj znaków wielobajtowych katakana 1-bajtowy kodu|
|[_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)|Konwertuj znaków wielobajtowych 2-bajtowych na odpowiednich 1-bajtowy znaków wielobajtowych|
|[mbrtoc16, mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|Konwertuj odpowiednik znaku UTF-16 lub UTF-32 znaków wielobajtowych|
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Konwertuj sekwencja znaków wielobajtowych sekwencji odpowiednie znaki dwubajtowe|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Konwertuj znaków wielobajtowych na odpowiednich znaków dwubajtowych|
|[strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|Konwertowanie ciągu na **podwójne**|
|[strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|Konwertowanie ciągu na **długi** liczba całkowita|
|[strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|Konwertowanie ciągu na **unsigned long** liczba całkowita|
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|Przekształć ciągu w formularzu sortowany w oparciu o informacje specyficzne dla ustawień regionalnych|
|[toascii, __toascii](../c-runtime-library/reference/toascii-toascii.md)|Konwertuj znak do kodu ASCII||
|[tolower, _tolower —, towlower —, _tolower_l —, _towlower_l —](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md), [_mbctolower —, _mbctolower_l —, _mbctoupper —, _mbctoupper_l —](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Testowanie znaków i przekonwertować na małe litery, jeśli aktualnie wielkie litery|
|[tolower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)|Konwertuj znaki na małe litery bezwarunkowo|[System::String::ToLower](https://msdn.microsoft.com/en-us/library/system.string.tolower.aspx)|
|[toupper, _toupper —, towupper —, _toupper_l —, _towupper_l —](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md), [_mbctolower —, _mbctolower_l —, _mbctoupper —, _mbctoupper_l —](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Testowanie znaków i przekonwertowania na wielkie litery, jeśli aktualnie małe litery|
|[toupper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|Konwertuj znaki na wielkie litery bezwarunkowo|
|[wcstombs —, _wcstombs_l —](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s —, _wcstombs_s_l —](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Konwertuj do odpowiedniej sekwencji znaków wielobajtowych sekwencji znaki dwubajtowe|
|[wctomb —, _wctomb_l —](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s —, _wctomb_s_l —](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Konwertuj znaków dwubajtowych na odpowiednich znaków wielobajtowych|
|[_wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Konwertuj ciąg znaków dwubajtowych **podwójne**|
|[_wtoi —, _wtoi_l —](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Konwertuj ciąg znaków dwubajtowych **int**|
|[_wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Konwertuj ciąg znaków dwubajtowych **__int64** lub **długi czas**|
|[_wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Konwertuj ciąg znaków dwubajtowych **długa**|

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
