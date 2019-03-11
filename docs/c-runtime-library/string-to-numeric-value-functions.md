---
title: Konwertowanie ciągów na wartości
ms.date: 11/04/2016
apilocation:
- msvcr80.dll
- msvcr110.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- _tcstoui64
- _tcstoi64
helpviewer_keywords:
- parsing, numeric strings
- string conversion, to numeric values
ms.assetid: 11cbd9ce-033b-4914-bf66-029070e7e385
ms.openlocfilehash: 3f24b75c2fdb3aa0d84b16874d2d01f1cb96d4b9
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743887"
---
# <a name="string-to-numeric-value-functions"></a>Konwertowanie ciągów na wartości

- [strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)

- [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)

- [strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)

- [_strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l](../c-runtime-library/reference/strtoi64-wcstoi64-strtoi64-l-wcstoi64-l.md)

- [_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l](../c-runtime-library/reference/strtoui64-wcstoui64-strtoui64-l-wcstoui64-l.md)

## <a name="remarks"></a>Uwagi

Każda funkcja w **strtod** rodziny konwertuje ciąg zakończony znakiem null, wartość liczbową. W poniższej tabeli wymieniono dostępne funkcje.

|Funkcja|Opis|
|--------------|-----------------|
|`strtod`|Konwertuj ciąg na wartość zmiennoprzecinkową podwójnej precyzji|
|`strtol`|Konwertuj ciąg na liczba całkowita typu long|
|`strtoul`|Konwertuj ciąg na niepodpisane długa liczba całkowita|
|`_strtoi64`|Konwertuj ciąg na 64-bitowych `__int64` liczba całkowita|
|`_strtoui64`|Przekonwertować ciągu na niepodpisane 64-bitowych `__int64` liczba całkowita|

`wcstod`, `wcstol`, `wcstoul`, i `_wcstoi64` są wersjami znaków dwubajtowych `strtod`, `strtol`, `strtoul`, i `_strtoi64`, odpowiednio. Argument typu string każda z tych funkcji znaków dwubajtowych to ciąg znaku dwubajtowego. Każda funkcja zachowuje się tak samo z jego odpowiednikiem pojedynczych bajtów znaków w przeciwnym razie.

`strtod` Funkcja przyjmuje dwa argumenty: pierwsza to ciąg wejściowy, a drugi wskaźnik znaku, który kończy się proces konwersji. `strtol`, `strtoul`, **_strtoi64 —** i **_strtoui64 —** pobrane trzeci argument numer podstawowy do użycia w procesie konwersji.

Ciąg wejściowy jest sekwencją znaków, które mogą być interpretowane jako wartość liczbowa określonego typu. Każda funkcja przestaje odczytywać ciąg przy pierwszym znaku, który nie może rozpoznać jako elementu liczby. Może to być kończący znak null. Aby uzyskać `strtol`, `strtoul`, `_strtoi64`, i `_strtoui64`, to kończącego znaku można też pierwszy znak numeryczny, większa niż lub równa dostarczone przez użytkownika numer podstawowy.

Jeśli nie ustawiono Wskaźnik dostarczone przez użytkownika, aby znak zakończenia z konwersji **NULL** w momencie wywołania, wskaźnik znaku, który zatrzymał skanowanie będzie znajdować się zamiast tego. Jeśli konwersja nie może być wykonywana (nie znaleziono żadnych prawidłowych cyfr lub określono nieprawidłową podstawę), wartość wskaźnika ciągu jest przechowywany pod tym adresem.

`strtod` oczekuje, że ciąg o następującej postaci:

[*odstępu*] [*logowania*] [`digits`] [**.** `digits`] [{**d** &#124; **D** &#124; **e** &#124; **E**} [*logowania*] `digits`]

A *odstępu* może składać się ze znaków spacji lub tabulatorów, które są ignorowane. *logowania* jest plus (**+**) lub minus (**-**); i `digits` są co najmniej jedna cyfra dziesiętna. Jeśli żadna cyfra pojawia się przed znakiem podstawy, co najmniej jedna musi występować po znaku podstawy. Cyfr dziesiętnych może następować wykładnik, który składa się z litery wprowadzającej (**d**, **D**, **e**, lub **E**) i opcjonalnie liczby całkowitej ze znakiem. Jeśli wykładnik ani znak podstawy nie pojawia się, znak podstawy zakłada się, że ostatniej cyfrze w ciągu. Pierwszy znak, który nie mieści się tym formularzu zatrzymuje skanowanie.

`strtol`, `strtoul`, `_strtoi64`, I `_strtoui64` funkcje oczekiwany ciąg o następującej postaci:

[*odstępu*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [`digits`]

Jeśli argument podstawowy jest między 2 a 36, następnie jest używany jako podstawa numeru. Jeśli jest 0, początkowe znaki, które odwołuje się do wskaźnika typu "end konwersji" są używane do określenia podstawy. Jeśli pierwszym znakiem jest 0, a drugim znakiem nie jest,, x"lub,, X", ciąg jest interpretowany jako ósemkowa liczba całkowita; w przeciwnym razie jest interpretowany jako liczba dziesiętna. Jeśli pierwszym znakiem jest "0", a drugim znakiem jest,, x"lub,, X", ciąg jest interpretowany jako szesnastkowa liczba całkowita. Jeśli pierwszym znakiem jest,, 1 "do,, 9", ciąg jest interpretowany jako dziesiętna liczba całkowita. Litery od "" do "z" (lub "" – "Z") są przypisane wartości od 10 do 35; tylko litery, w których przypisane wartości są mniej niż *podstawowy* są dozwolone. `strtoul` i `_strtoui64` Zezwalaj znakiem plus (**+**) lub minus (**-**) prefiksu logowania; wiodący znak minus wskazuje, że wartość zwracana jest ujemna.

Wartość wyjściowa jest zależna od ustawienia `LC_NUMERIC` ustawienia kategorii ustawień regionalnych; zobacz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji, bez **_l** sufiks używają bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; wersje **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych w zamian przekazanych.

Jeśli wartość zwracana przez te funkcje spowodowałoby przepełnienie lub niedopełnienie lub Jeśli konwersja nie jest możliwe, specjalnych przypadków wartości są zwracane, jak pokazano:

|Funkcja|Warunek|Wartość zwracana|
|--------------|---------------|--------------------|
|`strtod`|przepełnienia|+/- `HUGE_VAL`|
|`strtod`|Niedopełnienie lub bez konwersji|0|
|`strtol`|+ Przepełnienia|**LONG_MAX**|
|`strtol`|-Przepełnienia|**LONG_MIN**|
|`strtol`|Niedopełnienie lub bez konwersji|0|
|`_strtoi64`|+ Przepełnienia|**_I64_MAX**|
|`_strtoi64`|-Przepełnienia|**_I64_MIN**|
|`_strtoi64`|Brak konwersji|0|
|`_strtoui64`|przepełnienia|**_UI64_MAX**|
|`_strtoui64`|Brak konwersji|0|

**_I64_MAX**, _**I64_MIN**, i **_UI64_MAX** są zdefiniowane w granicach. H.

`wcstod`, `wcstol`, `wcstoul`, `_wcstoi64`, i `_wcstoui64` są wersjami znaków dwubajtowych `strtod`, `strtol`, `strtoul`, `_strtoi64`, i `_strtoui64`odpowiednio; wskaźnik do zakończenia z konwersji przez Każda z tych funkcji znaków dwubajtowych argument jest ciągiem znaku dwubajtowego. W przeciwnym wypadku każda z tych funkcji znaków dwubajtowych działa identycznie do jego odpowiednika pojedynczych bajtów znaków.

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Obsługa liczb zmiennoprzecinkowych](../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)
