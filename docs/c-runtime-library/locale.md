---
title: Regionalne
ms.date: 04/11/2018
f1_keywords:
- c.international
helpviewer_keywords:
- localization, locale
- country information
- language information routines
- setlocale function
- locale routines
ms.assetid: 442f8112-9288-44d7-be3c-15d22652093a
ms.openlocfilehash: b5096d0b0f0990a89789993a12f383d060b91b3e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571486"
---
# <a name="locale"></a>Regionalne

*Ustawienia regionalne* odwołuje się do ustawień kraj/region i język, które umożliwia dostosowywanie programu. Niektóre kategorie zależne od ustawień regionalnych obejmują formaty wyświetlania dat i wartości pieniężne. Aby uzyskać więcej informacji, zobacz [kategorie ustawień regionalnych](../c-runtime-library/locale-categories.md).

Użyj [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) funkcję, aby zmienić lub sprawdzić niektóre lub wszystkie bieżące informacje ustawień regionalnych programu lub wątku podczas korzystania z funkcji, które nie **_l** sufiks. Funkcje z **_l** sufiks użyje parametru ustawień regionalnych, przekazywane do swoich informacji o ustawieniach regionalnych podczas wykonywania tych tylko określonych funkcji. Aby utworzyć ustawienia regionalne do użycia przy użyciu funkcji z **_l** sufiksu domeny, należy użyć [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md). Aby zwolnić tych ustawień regionalnych, należy użyć [_free_locale —](../c-runtime-library/reference/free-locale.md). Aby uzyskać bieżące ustawienia regionalne, użyj [_get_current_locale —](../c-runtime-library/reference/get-current-locale.md).

Użyj [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) tego, czy do kontrolowania każdy wątek ma swoje własne ustawienia regionalne lub wszystkie wątki w programie udostępnianie tych samych ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawienia regionalne i strony kodowe](../text/locales-and-code-pages.md).

Bardziej bezpieczne wersje funkcji w poniższej tabeli są dostępne, wskazywanym przez **_s** sufiks ("bezpieczne"). Aby uzyskać więcej informacji, zobacz [funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md).

## <a name="locale-dependent-routines"></a>Procedury zależne od ustawień regionalnych

|Procedura|Zastosowanie|**setLocale** uzależnieniu od ustawienia kategorii|
|-------------|---------|---------------------------------------------|
|[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Konwertuj znaków na wartość zmiennoprzecinkową|**LC_NUMERIC**|
|[atoi, _atoi_l, _wtoi, _wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Konwertuj znaków na wartość całkowitą|**LC_NUMERIC**|
|[_atoi64, _atoi64_l, _wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Konwertuj znaków na wartość 64-bitowa liczba całkowita|**LC_NUMERIC**|
|[atol, _atol_l, _wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Konwertuj znaków na wartość typu long|**LC_NUMERIC**|
|[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Konwertuj znaków na wartość double long|**LC_NUMERIC**|
|[jest procedury](../c-runtime-library/is-isw-routines.md)|Testu danej liczby całkowitej dla określonego warunku.|**LC_CTYPE**|
|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|Test na bajt|**LC_CTYPE**|
|[localeconv](../c-runtime-library/reference/localeconv.md)|Przeczytaj odpowiednie wartości dla formatowanie liczbowe ilości|`LC_MONETARY, LC_NUMERIC`|
|[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)|Maksymalna długość w bajtach jakiegokolwiek znaku wielobajtowego w bieżących ustawień regionalnych (makro zdefiniowane w STDLIB. GODZ.)|**LC_CTYPE**|
|[_mbccpy —, _mbccpy_l —](../c-runtime-library/reference/mbccpy-mbccpy-l.md),[_mbccpy_s —, _mbccpy_s_l —](../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)|Skopiuj jeden znak wielobajtowy|**LC_CTYPE**|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Zweryfikuj i zwraca liczbę bajtów w znaków wielobajtowych|**LC_CTYPE**|
|[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|Dla ciągów znaków wielobajtowych: Sprawdź poprawność każdego znaku w ciągu; Zwraca długość ciągu|**LC_CTYPE**|
|[mbstowcs, _mbstowcs_l —](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md),[mbstowcs_s —, _mbstowcs_s_l —](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Konwertowanie sekwencji znaków wielobajtowych do odpowiedniej sekwencji znaków dwubajtowych|**LC_CTYPE**|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Konwertuj znak wielobajtowy do odpowiedniego znaku dwubajtowego|**LC_CTYPE**|
|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) funkcji|Zapis sformatowane wyniki|**LC_NUMERIC** (określa znaku podstawy w danych wyjściowych)|
|[scanf —](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) funkcji|Odczyt sformatowane dane wejściowe|**LC_NUMERIC** (określa rozpoznawanie znaku podstawy)|
|[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)|Wybierz ustawienia regionalne dla programu|Nie dotyczy|
|[strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|Porównaj z dwóch ciągów znaków|**LC_COLLATE**|
|[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)|Porównuje dwa ciągi bez uwzględniania wielkości liter|**LC_CTYPE**|
|[_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|Porównywanie znaków dwa ciągi (wielkich liter)|**LC_COLLATE**|
|[_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|Porównaj najpierw **n** z dwóch ciągów znaków|**LC_COLLATE**|
|[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)|Porównywanie znaków z dwóch ciągów bez uwzględniania wielkości liter.|**LC_CTYPE**|
|[_strnicoll, _wcsnicoll, _mbsnicoll, _strnicoll_l, _wcsnicoll_l, _mbsnicoll_l](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|Porównaj najpierw **n** znaki z dwóch ciągów (wielkich liter)|**LC_COLLATE**|
|[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Podana wartość daty i godziny zgodnie z opisem w formacie **format** argumentu|**LC_TIME**|
|[_strlwr, _wcslwr —, _mbslwr —, _strlwr_l —, _wcslwr_l —, _mbslwr_l —](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md),[_strlwr_s —, _strlwr_s_l —, _mbslwr_s —, _mbslwr_s_l —, _wcslwr_s —, _wcslwr_s_l —](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|Konwertuj na miejscu, każdy wielkiej litery w danym ciągu na małe litery.|**LC_CTYPE**|
|[strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|Konwertuj ciąg znaków do **double** wartość|**LC_NUMERIC** (określa rozpoznawanie znaku podstawy)|
|[strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|Konwertuj ciąg znaków do **długie** wartość|**LC_NUMERIC** (określa rozpoznawanie znaku podstawy)|
|[strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|Konwertuj ciąg znaków na wartość typu unsigned long|**LC_NUMERIC** (określa rozpoznawanie znaku podstawy)|
|[_strupr —, _strupr_l —, _mbsupr —, _mbsupr_l —, _wcsupr_l —, _wcsupr —](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md),[_strupr_s —, _strupr_s_l —, _mbsupr_s —, _mbsupr_s_l —, _wcsupr_s —, _wcsupr_s_l —](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|Konwertuj na miejscu, każdą małą literę w ciągu na wielkie litery|**LC_CTYPE**|
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|Przekształć ciąg w formie sortowany w zależności od ustawień regionalnych|**LC_COLLATE**|
|[tolower, _tolower —, towlower —, _tolower_l —, _towlower_l —](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md),[_mbctolower —, _mbctolower_l —, _mbctoupper —, _mbctoupper_l —](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Dokonać konwersji podanego znaków do odpowiedniego znaku małe litery|**LC_CTYPE**|
|[toupper, _toupper —, towupper —, _toupper_l —, _towupper_l —](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md),[_mbctolower —, _mbctolower_l —, _mbctoupper —, _mbctoupper_l —](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Dokonać konwersji podanego znaków do odpowiedniego wielką literą|**LC_CTYPE**|
|[wcstombs —, _wcstombs_l —](../c-runtime-library/reference/wcstombs-wcstombs-l.md),[wcstombs_s —, _wcstombs_s_l —](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Konwertowanie sekwencji znaków dwubajtowych do odpowiedniej sekwencji znaków wielobajtowych|**LC_CTYPE**|
|[wctomb —, _wctomb_l —](../c-runtime-library/reference/wctomb-wctomb-l.md),[wctomb_s —, _wctomb_s_l —](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Konwertuj szerokich znaków do odpowiedniego znaku wielobajtowego|**LC_CTYPE**|

> [!NOTE]
> Dla wielobajtowego procedur wielobajtowa strona kodowa musi być odpowiednikiem zestawu przy użyciu ustawień regionalnych [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). [_setmbcp](../c-runtime-library/reference/setmbcp.md), z argumentem **_MB_CP_LOCALE** sprawia, że kodowe wielobajtowe strony taka sama jak **setlocale** strony kodowej.

## <a name="see-also"></a>Zobacz też

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
