---
title: Ustawienia regionalne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.international
dev_langs:
- C++
helpviewer_keywords:
- localization, locale
- country information
- language information routines
- setlocale function
- locale routines
ms.assetid: 442f8112-9288-44d7-be3c-15d22652093a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 638d4fbe6fd4dfce1fb3eeb246ef85c5b60fada0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392513"
---
# <a name="locale"></a>Regionalne

*Ustawienia regionalne* odwołuje się do ustawienia kraj/region i język, które umożliwiają dostosowanie programu. Niektóre kategorie zależnych od ustawień regionalnych obejmują formatu daty i wartości monetarnych. Aby uzyskać więcej informacji, zobacz [kategorie regionalne](../c-runtime-library/locale-categories.md).

 Użyj [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) funkcji, aby zmienić lub zbadać niektórych lub wszystkich bieżących informacji ustawień regionalnych program lub wątku podczas korzystania z funkcji bez **_l** sufiks. Funkcje z **_l** sufiks użyje parametr ustawień regionalnych przekazana dla swoich informacji o ustawieniach regionalnych podczas wykonywania tych tylko określonych funkcji. Można utworzyć ustawień regionalnych do użycia z funkcją z **_l** sufiks, użyj [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md). Aby zwolnić tych ustawień regionalnych, należy użyć [_free_locale —](../c-runtime-library/reference/free-locale.md). Aby uzyskać bieżące ustawienia regionalne, użyj [_get_current_locale —](../c-runtime-library/reference/get-current-locale.md).

 Użyj [_configthreadlocale —](../c-runtime-library/reference/configthreadlocale.md) czy do kontrolowania każdy wątek ma własną ustawień regionalnych, lub wszystkie wątki w programie udostępnianie tych samych ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawienia regionalne i strony kodowe](../text/locales-and-code-pages.md).

 Bardziej bezpieczne funkcje w poniższej tabeli są dostępne wersje, wskazane przez **_s** sufiks ("zabezpieczenia"). Aby uzyskać więcej informacji, zobacz [funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md).

## <a name="locale-dependent-routines"></a>Procedury zależne od ustawień regionalnych

|Procedura|Zastosowanie|**setLocale** zależność ustawienie kategorii|
|-------------|---------|---------------------------------------------|
|[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Konwertuj znak na wartości zmiennoprzecinkowe|**LC_NUMERIC —**|
|[atoi, _atoi_l, _wtoi, _wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Konwertuj znaków na wartość całkowitą|**LC_NUMERIC —**|
|[_atoi64, _atoi64_l, _wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Konwertuj znaków na wartość 64-bitową liczbę całkowitą|**LC_NUMERIC —**|
|[atol, _atol_l, _wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Konwertuj znaków na wartość typu long|**LC_NUMERIC —**|
|[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Konwertuj znaków na wartość o podwójnej precyzji long|**LC_NUMERIC —**|
|[is — procedury](../c-runtime-library/is-isw-routines.md)|Test podanej liczby całkowitej dla określonego warunku.|**LC_CTYPE —**|
|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|Testowanie bajtu|**LC_CTYPE —**|
|[localeconv](../c-runtime-library/reference/localeconv.md)|Przeczytaj odpowiednie wartości liczbowe ilości formatowania|`LC_MONETARY, LC_NUMERIC`|
|[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)|Maksymalna długość w bajtach znaków wielobajtowych w bieżących ustawień regionalnych (zdefiniowany w STDLIB makra. H)|**LC_CTYPE —**|
|[_mbccpy —, _mbccpy_l —](../c-runtime-library/reference/mbccpy-mbccpy-l.md),[_mbccpy_s —, _mbccpy_s_l —](../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)|Kopiowanie znaków wielobajtowych jeden|**LC_CTYPE —**|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Sprawdzanie poprawności i zwraca liczbę bajtów w znaków wielobajtowych|**LC_CTYPE —**|
|[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|Ciągi znaków wielobajtowych: Sprawdzanie poprawności każdego znaku w ciągu; Zwraca długość ciągu|**LC_CTYPE —**|
|[mbstowcs —, _mbstowcs_l —](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md),[mbstowcs_s —, _mbstowcs_s_l —](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Konwertuj sekwencja znaków wielobajtowych sekwencji odpowiednie znaki dwubajtowe|**LC_CTYPE —**|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Konwertuj znaków wielobajtowych na odpowiednich znaków dwubajtowych|**LC_CTYPE —**|
|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) funkcji|Zapisywanie sformatowanego danych wyjściowych|**Lc_numeric —** (określa dane wyjściowe znak podstawa)|
|[scanf —](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) funkcji|Odczyt sformatowane dane wejściowe|**Lc_numeric —** (określa rozpoznawania znaków podstawa)|
|[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)|Wybierz ustawienia regionalne dla programu|Nie dotyczy|
|[strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|Porównywanie znaków dwa ciągi|**LC_COLLATE —**|
|[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)|Porównuje dwa ciągi bez uwzględniania wielkości liter|**LC_CTYPE —**|
|[_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|Porównywanie znaków dwa ciągi (bez uwzględniania wielkości liter)|**LC_COLLATE —**|
|[_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|Porównanie najpierw **n** znaki z dwóch ciągów|**LC_COLLATE —**|
|[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)|Porównywanie znaków dwa ciągi bez uwzględniania wielkości liter.|**LC_CTYPE —**|
|[_strnicoll, _wcsnicoll, _mbsnicoll, _strnicoll_l, _wcsnicoll_l, _mbsnicoll_l](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|Porównanie najpierw **n** znaki z dwóch ciągów (bez uwzględniania wielkości liter)|**LC_COLLATE —**|
|[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Podana wartość daty i godziny zgodnie z formatu **format** argumentu|**LC_TIME —**|
|[_strlwr —, _wcslwr —, _mbslwr —, _strlwr_l —, _wcslwr_l —, _mbslwr_l —](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md),[_strlwr_s —, _strlwr_s_l —, _mbslwr_s —, _mbslwr_s_l —, _wcslwr_s —, _wcslwr_s_l —](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|Konwertuj na miejscu, każdy wielkiej litery w podany ciąg na małe litery.|**LC_CTYPE —**|
|[strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|Konwertowanie ciągu znaków na **podwójne** wartość|**Lc_numeric —** (określa rozpoznawania znaków podstawa)|
|[strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|Konwertowanie ciągu znaków na **długi** wartość|**Lc_numeric —** (określa rozpoznawania znaków podstawa)|
|[strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|Konwertuj ciąg znaków na wartość typu long bez znaku|**Lc_numeric —** (określa rozpoznawania znaków podstawa)|
|[_strupr —, _strupr_l —, _mbsupr —, _mbsupr_l —, _wcsupr_l —, _wcsupr —](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md),[_strupr_s —, _strupr_s_l —, _mbsupr_s —, _mbsupr_s_l —, _wcsupr_s —, _wcsupr_s_l —](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|Konwertuj na miejscu, każdy małej litery w ciągu na wielkie litery|**LC_CTYPE —**|
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|Przekształcanie ciągów do postaci sortowany w zależności od ustawień regionalnych|**LC_COLLATE —**|
|[tolower, _tolower —, towlower —, _tolower_l —, _towlower_l —](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md),[_mbctolower —, _mbctolower_l —, _mbctoupper —, _mbctoupper_l —](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Dokonać konwersji podanego znak odpowiedniego małą literę|**LC_CTYPE —**|
|[toupper, _toupper —, towupper —, _toupper_l —, _towupper_l —](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md),[_mbctolower —, _mbctolower_l —, _mbctoupper —, _mbctoupper_l —](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Dokonać konwersji podanego znak odpowiedniego wielką literę|**LC_CTYPE —**|
|[wcstombs —, _wcstombs_l —](../c-runtime-library/reference/wcstombs-wcstombs-l.md),[wcstombs_s —, _wcstombs_s_l —](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Konwertuj do odpowiedniej sekwencji znaków wielobajtowych sekwencji znaki dwubajtowe|**LC_CTYPE —**|
|[wctomb —, _wctomb_l —](../c-runtime-library/reference/wctomb-wctomb-l.md),[wctomb_s —, _wctomb_s_l —](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Konwertuj znaków dwubajtowych na odpowiednich znaków wielobajtowych|**LC_CTYPE —**|

> [!NOTE]
> Procedury wielobajtowe strony kodowe wielobajtowe musi być równoważne z ustawieniami regionalnymi z [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). [_setmbcp —](../c-runtime-library/reference/setmbcp.md), z argumentem **_MB_CP_LOCALE** sprawia, że kodowe wielobajtowe strony taka sama jak **setlocale** stronę kodową.

## <a name="see-also"></a>Zobacz też

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
 [Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
