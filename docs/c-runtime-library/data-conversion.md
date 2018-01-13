---
title: Konwersja danych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.conversions
dev_langs: C++
helpviewer_keywords:
- data conversion routines [C++]
- converting data
ms.assetid: b15b5268-7467-49f1-bf95-5299b598f94c
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 11b28793e5e659e3135061e3a6fd410d9b1c9f3c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="data-conversion"></a>Konwersja danych
Te procedury konwersji danych z jednego formularza do innego. Zazwyczaj te procedury wykonywania szybciej niż konwersje, który może zapisać. Każda procedura zaczyna się od `to` prefiks jest zaimplementowany jako funkcję, a makra. Zobacz [wybierania pomiędzy funkcjami i makrami](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md) informacji o wybieraniu implementację.  
  
### <a name="data-conversion-routines"></a>Procedury konwersji danych  
  
|Procedura|Zastosowanie|  
|-------------|---------|  
|[ABS](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Zwraca wartość bezwzględną liczby całkowitej|  
|[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Konwertowanie ciągów do`float`|  
|[atoi, _atoi_l, _wtoi, _wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Konwertowanie ciągów do`int`|  
|[_atoi64, _atoi64_l, _wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Konwertowanie ciągów do`__int64`|  
|[atol, _atol_l, _wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Konwertowanie ciągów do`long`|  
|[c16rtomb, c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|Konwertuj UTF-16 lub UTF-32 znaków na równoważne znaków wielobajtowych|  
|[_ecvt —](../c-runtime-library/reference/ecvt.md), [_ecvt_s —](../c-runtime-library/reference/ecvt-s.md)|Konwertuj `double` ciąg znaków o określonej długości|  
|[_fcvt —](../c-runtime-library/reference/fcvt.md), [_fcvt_s —](../c-runtime-library/reference/fcvt-s.md)|Konwertuj `double` do ciągu określonej liczby cyfr od punktu dziesiętnego|  
|[_gcvt —](../c-runtime-library/reference/gcvt.md), [_gcvt_s —](../c-runtime-library/reference/gcvt-s.md)|Konwertuj `double` liczbę na ciąg; przechowywanie parametrów w buforze|  
|[_itoa —, _i64toa —, _ui64toa —, _itow —, _i64tow —, _ui64tow —](../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md), [_itoa_s —, _i64toa_s —, _ui64toa_s —, _itow_s —, _i64tow_s —, _ui64tow_s —](../c-runtime-library/reference/itoa-s-i64toa-s-ui64toa-s-itow-s-i64tow-s-ui64tow-s.md)|Konwertuj `int` lub `__int64` na ciąg|  
|[Labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Zwraca wartość bezwzględną `long` liczba całkowita|  
|[llabs —](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Zwraca wartość bezwzględną `long long` liczba całkowita|  
|[_ltoa —, _ltow —](../c-runtime-library/reference/ltoa-ltow.md), [_ltoa_s —, _ltow_s —](../c-runtime-library/reference/ltoa-s-ltow-s.md)|Konwertuj `long` na ciąg|  
|[_mbbtombc, _mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)|Konwertuj znaków wielobajtowych 1-bajtowych na odpowiednich 2-bajtowych znaków wielobajtowych|  
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|Konwertuj znak Japonii branżowy Standard (JIS) na znak Japonii firmy Microsoft (JMS)|  
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|Konwertuj JMS znaków JIS znaków|  
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|Konwertuj znaków wielobajtowych hiragana 1-bajtowy kodu|  
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|Konwertuj znaków wielobajtowych katakana 1-bajtowy kodu|  
|[_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)|Konwertuj znaków wielobajtowych 2-bajtowych na odpowiednich 1-bajtowy znaków wielobajtowych|  
|[mbrtoc16, mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|Konwertuj odpowiednik znaku UTF-16 lub UTF-32 znaków wielobajtowych|  
|[mbstowcs —, _mbstowcs_l —](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s —, _mbstowcs_s_l —](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Konwertuj sekwencja znaków wielobajtowych sekwencji odpowiednie znaki dwubajtowe|  
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Konwertuj znaków wielobajtowych na odpowiednich znaków dwubajtowych|  
|[strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|Konwertowanie ciągów do`double`|  
|[strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|Konwertowanie ciągu na `long` liczba całkowita|  
|[strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|Konwertowanie ciągu na `unsigned long` liczba całkowita|  
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|Przekształć ciągu w formularzu sortowany w oparciu o informacje specyficzne dla ustawień regionalnych|  
|[toascii, __toascii](../c-runtime-library/reference/toascii-toascii.md)|Konwertuj znak do kodu ASCII||  
|[tolower, _tolower —, towlower —, _tolower_l —, _towlower_l —](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md), [_mbctolower —, _mbctolower_l —, _mbctoupper —, _mbctoupper_l —](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Testowanie znaków i przekonwertować na małe litery, jeśli aktualnie wielkie litery|  
|[tolower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)|Konwertuj znaki na małe litery bezwarunkowo|[System::String::ToLower](https://msdn.microsoft.com/en-us/library/system.string.tolower.aspx)|  
|[toupper, _toupper —, towupper —, _toupper_l —, _towupper_l —](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md), [_mbctolower —, _mbctolower_l —, _mbctoupper —, _mbctoupper_l —](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Testowanie znaków i przekonwertowania na wielkie litery, jeśli aktualnie małe litery|  
|[toupper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|Konwertuj znaki na wielkie litery bezwarunkowo|  
|[_ultoa —, _ultow —](../c-runtime-library/reference/ultoa-ultow.md), [_ultoa_s —, _ultow_s —](../c-runtime-library/reference/ultoa-s-ultow-s.md)|Konwertuj `unsigned long` na ciąg|  
|[wcstombs —, _wcstombs_l —](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s —, _wcstombs_s_l —](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Konwertuj do odpowiedniej sekwencji znaków wielobajtowych sekwencji znaki dwubajtowe|  
|[wctomb —, _wctomb_l —](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s —, _wctomb_s_l —](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Konwertuj znaków dwubajtowych na odpowiednich znaków wielobajtowych|  
|[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Konwertuj ciąg znaków dwubajtowych`double`|   
|[atoi, _atoi_l, _wtoi, _wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Konwertuj ciąg znaków dwubajtowych`int`|  
|[_atoi64, _atoi64_l, _wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Konwertuj ciąg znaków dwubajtowych`__int64`|  
|[atol, _atol_l, _wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Konwertuj ciąg znaków dwubajtowych`long`|  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)