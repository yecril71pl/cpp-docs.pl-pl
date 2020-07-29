---
title: Konwertowanie ciągów na wartości
ms.date: 11/04/2016
api_location:
- msvcr80.dll
- msvcr110.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcstoui64
- _tcstoi64
helpviewer_keywords:
- parsing, numeric strings
- string conversion, to numeric values
ms.assetid: 11cbd9ce-033b-4914-bf66-029070e7e385
ms.openlocfilehash: b4936e09de5ee26356b71b66154071a93e252b6f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213466"
---
# <a name="string-to-numeric-value-functions"></a>Konwertowanie ciągów na wartości

- [strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)

- [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)

- [strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)

- [_strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l](../c-runtime-library/reference/strtoi64-wcstoi64-strtoi64-l-wcstoi64-l.md)

- [_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l](../c-runtime-library/reference/strtoui64-wcstoui64-strtoui64-l-wcstoui64-l.md)

## <a name="remarks"></a>Uwagi

Każda funkcja w rodzinie **strtod** konwertuje ciąg zakończony znakiem null na wartość liczbową. Dostępne funkcje są wymienione w poniższej tabeli.

|Funkcja|Opis|
|--------------|-----------------|
|`strtod`|Konwertuj ciąg na wartość zmiennoprzecinkową o podwójnej precyzji|
|`strtol`|Konwertuj ciąg na długą liczbę całkowitą|
|`strtoul`|Konwertuj ciąg na długą liczbę całkowitą bez znaku|
|`_strtoi64`|Konwertuj ciąg na 64-bitową **`__int64`** liczbę całkowitą|
|`_strtoui64`|Konwertuj ciąg na niepodpisany 64-bitową **`__int64`** liczbę całkowitą|

`wcstod`, `wcstol` , `wcstoul` i `_wcstoi64` są wersjami znaków dwubajtowych `strtod` , `strtol` , `strtoul` , i `_strtoi64` , odpowiednio. Argument ciągu dla każdej z tych funkcji o szerokim znaku jest ciągiem znaków dwubajtowych; Każda funkcja zachowuje się identycznie z jego odpowiednikiem pojedynczego bajtu, w przeciwnym razie.

`strtod`Funkcja przyjmuje dwa argumenty: pierwszy to ciąg wejściowy, a drugi wskaźnik do znaku kończącego proces konwersji. `strtol`, `strtoul` , **_strtoi64** i **_strtoui64** przyjmuje trzeci argument jako numer bazowy do użycia w procesie konwersji.

Ciąg wejściowy jest sekwencją znaków, które mogą być interpretowane jako wartość liczbowa określonego typu. Każda funkcja przestaje odczytywać ciąg przy pierwszym znaku, którego nie może rozpoznać jako części liczby. Może to być kończący znak null. Dla `strtol` , `strtoul` , `_strtoi64` , i `_strtoui64` , ten znak kończący może być również pierwszym znakiem numerycznym większym niż lub równym podstawie liczby dostarczonej przez użytkownika.

Jeśli wskaźnik dostarczony przez użytkownika do znaku końca konwersji nie ma ustawionej **wartości null** w czasie wywołania, zamiast tego zostanie zapisany wskaźnik do znaku, który zatrzymał skanowanie. Jeśli konwersja nie może być wykonywana (nie znaleziono prawidłowych cyfr lub określono nieprawidłową podstawę), wartość wskaźnika ciągu jest przechowywana na tym adresie.

`strtod`oczekuje ciągu z następującej formy:

[*odstęp*] [*Sign*] [`digits`] [**.**`digits`] [{**d** &#124; **d** &#124; **e** &#124; **e**} [*Sign*] `digits` ]

*Odstępy* mogą zawierać spacje lub znaki tabulacji, które są ignorowane; *znak* jest znakiem plus ( **+** ) lub minus ( **-** ); i `digits` jest jedną lub większą liczbą cyfr dziesiętnych. Jeśli żadne cyfry nie pojawiają się przed znakiem podstawy, co najmniej jeden musi występować po znaku podstawy. Po cyfrach dziesiętnych można stosować wykładnikę, która składa się z litery wprowadzającej (**d**, **d**, **e**lub **e**) i opcjonalnie podpisanej liczby całkowitej. Jeśli nie zostanie wyświetlona żadna część wykładnika ani znak podstawy, przyjmuje się, że znak podstawy będzie podążać za ostatnią cyfrą w ciągu. Pierwszy znak, który nie pasuje do tego formularza, zatrzyma skanowanie.

`strtol`Funkcje, `strtoul` , `_strtoi64` i `_strtoui64` oczekują ciągu w następującej postaci:

[*odstęp*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **x** }]] [ `digits` ]

Jeśli argument podstawowy należy do zakresu od 2 do 36, jest używany jako podstawa liczby. Jeśli wartość wynosi 0, początkowe znaki, do których odwołuje się wskaźnik końca konwersji, są używane do określenia podstawy. Jeśli pierwszym znakiem jest 0, a drugi znak nie jest "x" lub "X", ciąg jest interpretowany jako ósemkowa liczba całkowita; w przeciwnym razie jest interpretowana jako liczba dziesiętna. Jeśli pierwszy znak to "0", a drugi znak to "x" lub "X", ciąg jest interpretowany jako Szesnastkowa liczba całkowita. Jeśli pierwszym znakiem jest "1" do "9", ciąg jest interpretowany jako dziesiętna liczba całkowita. Litery od "a" do "z" (lub "A" do "z") mają przypisane wartości od 10 do 35; dozwolone są tylko litery, których przypisane wartości są mniejsze niż *podstawowe* . `strtoul`i `_strtoui64` zezwalają na prefiks znaku plus () **+** lub minus ( **-** ); wiodący znak minus wskazuje, że wartość zwracana jest Negacja.

Wartość wyjściowa jest zależna od ustawienia kategorii ustawień `LC_NUMERIC` regionalnych; zobacz [setlocaling](../c-runtime-library/reference/setlocale-wsetlocale.md) , aby uzyskać więcej informacji. Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych. wersje z sufiksem **_l** są identyczne, z tą różnicą, że korzystają z przekazaną w zamian parametru ustawień regionalnych.

Gdy wartość zwracana przez te funkcje spowodowałoby przepełnienie lub niedomiar, lub jeśli konwersja nie jest możliwa, w przypadku wartości specjalnych zwracane są następujące dane:

|Funkcja|Warunek|Zwrócona wartość|
|--------------|---------------|--------------------|
|`strtod`|Przepływ|+/- `HUGE_VAL`|
|`strtod`|Niedopełnienie lub brak konwersji|0|
|`strtol`|+ Przepełnienie|**LONG_MAX**|
|`strtol`|-Overflow|**LONG_MIN**|
|`strtol`|Niedopełnienie lub brak konwersji|0|
|`_strtoi64`|+ Przepełnienie|**_I64_MAX**|
|`_strtoi64`|-Overflow|**_I64_MIN**|
|`_strtoi64`|Brak konwersji|0|
|`_strtoui64`|Przepływ|**_UI64_MAX**|
|`_strtoui64`|Brak konwersji|0|

**_I64_MAX**, _**I64_MIN**i **_UI64_MAX** są zdefiniowane w limitach. C.

`wcstod`, `wcstol` , `wcstoul` , `_wcstoi64` i `_wcstoui64` są wersjami znaków dwubajtowych `strtod` , `strtol` , `strtoul` , `_strtoi64` i `_strtoui64` , odpowiednio; wskaźnik do argumentu końca konwersji dla każdej z tych funkcji szerokiego znaku jest ciągiem znaków dwubajtowych. W przeciwnym razie każda z tych funkcji o szerokim znaku zachowuje się identycznie ze swoim odpowiednikiem pojedynczego bajtu.

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../c-runtime-library/data-conversion.md)<br/>
[Regionalne](../c-runtime-library/locale.md)<br/>
[Interpretacja sekwencji znaków wielobajtowych](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Obsługa zmiennoprzecinkowa](../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)
