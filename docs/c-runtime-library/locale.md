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
ms.openlocfilehash: a747c60994afbf4293aca8e4a3290d20b4bc18a3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87189587"
---
# <a name="locale"></a>Regionalne

Ustawienia *regionalne* odnoszą się do ustawień kraju/regionu i języka, których można użyć do dostosowania programu. Niektóre kategorie zależne od ustawień regionalnych obejmują formaty wyświetlania dat i wartości pieniężnych. Aby uzyskać więcej informacji, zobacz [Kategorie ustawień regionalnych](../c-runtime-library/locale-categories.md).

Funkcja [setlocals](../c-runtime-library/reference/setlocale-wsetlocale.md) służy do zmiany lub wykonywania zapytań dotyczących niektórych lub wszystkich bieżących informacji o ustawieniach regionalnych programu lub wątku przy użyciu funkcji bez sufiksu **_l** . Funkcja z sufiksem **_l** będzie używać parametru ustawień regionalnych przekazaną w celu uzyskania informacji o ustawieniach regionalnych podczas wykonywania tej konkretnej funkcji. Aby utworzyć ustawienia regionalne do użycia z funkcją z sufiksem **_l** , użyj [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md). Aby zwolnić te ustawienia regionalne, użyj [_free_locale](../c-runtime-library/reference/free-locale.md). Aby uzyskać bieżące ustawienia regionalne, użyj [_get_current_locale](../c-runtime-library/reference/get-current-locale.md).

Użyj [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) , aby określić, czy każdy wątek ma własne ustawienia regionalne, lub wszystkie wątki w programie mają te same ustawienia regionalne. Aby uzyskać więcej informacji, zobacz sekcję [Ustawienia regionalne i strony kodowe](../text/locales-and-code-pages.md).

Dostępne są bardziej bezpieczne wersje funkcji w poniższej tabeli, wskazywane przez sufiks **_s** ("Secure"). Aby uzyskać więcej informacji, zobacz [funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md).

## <a name="locale-dependent-routines"></a>Procedury zależne od ustawień regionalnych

|Procedura|Zastosowanie|Ustaw zależność ustawienia kategorii **ustawień regionalnych**|
|-------------|---------|---------------------------------------------|
|[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Konwertuj znak na wartość zmiennoprzecinkową|**LC_NUMERIC**|
|[atoi, _atoi_l, _wtoi, _wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Konwertuj znak na wartość całkowitą|**LC_NUMERIC**|
|[_atoi64, _atoi64_l, _wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Konwertuj znak na 64-bitową wartość całkowitą|**LC_NUMERIC**|
|[atol, _atol_l, _wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Konwertuj znak na wartość długą|**LC_NUMERIC**|
|[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Konwertuj znak na wartość podwójnie długa|**LC_NUMERIC**|
|[jest procedurami](../c-runtime-library/is-isw-routines.md)|Test podaną liczbę całkowitą dla określonego warunku.|**LC_CTYPE**|
|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|Test dla bajtu potencjalnego klienta|**LC_CTYPE**|
|[localeconv](../c-runtime-library/reference/localeconv.md)|Odczytaj odpowiednie wartości w celu formatowania ilości liczbowych|`LC_MONETARY, LC_NUMERIC`|
|[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)|Maksymalna długość w bajtach dowolnego znaku wielobajtowego w bieżących ustawieniach regionalnych (makro zdefiniowane w STDLIB. C|**LC_CTYPE**|
|[_mbccpy, _mbccpy_l](../c-runtime-library/reference/mbccpy-mbccpy-l.md),[_mbccpy_s _mbccpy_s_l](../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)|Kopiowanie jednego znaku wielobajtowego|**LC_CTYPE**|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Weryfikuj i zwraca liczbę bajtów w znaku wielobajtowego|**LC_CTYPE**|
|[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|Dla ciągów znaków wielobajtowych: Weryfikuj każdy znak w ciągu; zwraca długość ciągu|**LC_CTYPE**|
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md),[mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Konwertuj sekwencję znaków wielobajtowych na odpowiadającą sekwencję szerokich znaków|**LC_CTYPE**|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Konwertuj znak wielobajtowy na odpowiedni znak szeroki|**LC_CTYPE**|
|funkcje [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|Zapisz sformatowane dane wyjściowe|**LC_NUMERIC** (określa wyjście znaku podstawy)|
|funkcje [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)|Czytaj sformatowane dane wejściowe|**LC_NUMERIC** (określa rozpoznawanie znaków podstawy)|
|[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)|Wybieranie ustawień regionalnych dla programu|Nie dotyczy|
|[strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|Porównaj znaki dwóch ciągów|**LC_COLLATE**|
|[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)|Porównaj dwa ciągi bez względu na wielkość liter|**LC_CTYPE**|
|[_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|Porównaj znaki dwóch ciągów (bez uwzględniania wielkości liter)|**LC_COLLATE**|
|[_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|Porównaj pierwsze **n** znaków z dwóch ciągów|**LC_COLLATE**|
|[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)|Porównaj znaki dwóch ciągów bez względu na wielkość liter.|**LC_CTYPE**|
|[_strnicoll, _wcsnicoll, _mbsnicoll, _strnicoll_l, _wcsnicoll_l, _mbsnicoll_l](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|Porównaj pierwsze **n** znaków z dwóch ciągów (bez uwzględniania wielkości liter)|**LC_COLLATE**|
|[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Formatowanie wartości daty i godziny zgodnie z podanym argumentem **formatu**|**LC_TIME**|
|[_strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md),[_strlwr_s, _strlwr_s_l, _mbslwr_s, _mbslwr_s_l, _wcslwr_s, _wcslwr_s_l](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|Konwertuj na miejsce każdą wielką literę w danym ciągu na małe litery|**LC_CTYPE**|
|[strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|Konwertuj ciąg znaków na **`double`** wartość|**LC_NUMERIC** (określa rozpoznawanie znaków podstawy)|
|[strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|Konwertuj ciąg znaków na **`long`** wartość|**LC_NUMERIC** (określa rozpoznawanie znaków podstawy)|
|[strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|Konwertuj ciąg znaków na wartość długą bez znaku|**LC_NUMERIC** (określa rozpoznawanie znaków podstawy)|
|[_strupr, _strupr_l, _mbsupr, _mbsupr_l, _wcsupr_l, _wcsupr](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md),[_strupr_s, _strupr_s_l, _mbsupr_s, _mbsupr_s_l, _wcsupr_s, _wcsupr_s_l](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|Konwertuj na miejsce każdą małą literę w ciągu na wielkie litery|**LC_CTYPE**|
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|Przekształć ciąg w postać posortowaną zgodnie z ustawieniami regionalnymi|**LC_COLLATE**|
|[ToLower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md),[_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Konwertuj dany znak na odpowiedni znak małymi literami|**LC_CTYPE**|
|[ToUpper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md),[_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Konwertuj dany znak na odpowiadającą wielką literę|**LC_CTYPE**|
|[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md),[wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Konwertuj sekwencję szerokich znaków do odpowiedniej sekwencji znaków wielobajtowych|**LC_CTYPE**|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md),[wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Konwertuj znak szeroki do odpowiedniego znaku wielobajtowego|**LC_CTYPE**|

> [!NOTE]
> W przypadku procedur wielobajtowych strona kodowa wielobajtowego musi być równoważna ustawieniom regionalnym ustawionym na wartość [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). [_setmbcp](../c-runtime-library/reference/setmbcp.md), z argumentem **_MB_CP_LOCALE** powoduje, że strona kodowa wielobajtowego jest taka sama jak strona kodowa **setlocale** .

## <a name="see-also"></a>Zobacz także

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Procedury środowiska uruchomieniowego języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
