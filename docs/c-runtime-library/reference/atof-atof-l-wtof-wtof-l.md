---
title: atof, _atof_l, _wtof, _wtof_l
ms.date: 4/2/2020
api_name:
- _wtof_l
- atof
- _atof_l
- _wtof
- _o__atof_l
- _o__wtof
- _o__wtof_l
- _o_atof
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tstof
- _ttof
- atof
- stdlib/atof
- math/atof
- _atof_l
- stdlib/_atof_l
- math/_atof_l
- _wtof
- corecrt_wstdlib/_wtof
- _wtof_l
- corecrt_wstdlib/_wtof_l
helpviewer_keywords:
- tstof function
- atof_l function
- _atof_l function
- atof function
- _tstof function
- _ttof function
- wtof function
- _wtof_l function
- ttof function
- wtof_l function
- _wtof function
- string conversion, to floating point values
ms.assetid: eb513241-c9a9-4f5c-b7e7-a49b14abfb75
ms.openlocfilehash: 8eee8db691b3b652768980237fc90bd675bac89b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232589"
---
# <a name="atof-_atof_l-_wtof-_wtof_l"></a>atof, _atof_l, _wtof, _wtof_l

Konwertuj ciąg na wartość typu Double.

## <a name="syntax"></a>Składnia

```C
double atof(
   const char *str
);
double _atof_l(
   const char *str,
   _locale_t locale
);
double _wtof(
   const wchar_t *str
);
double _wtof_l(
   const wchar_t *str,
   _locale_t locale
);
```

## <a name="parameters"></a>Parametry

*str*<br/>
Ciąg do przekonwertowania.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca **`double`** wartość wygenerowaną przez interpretowanie znaków wejściowych jako liczby. Wartość zwracana to 0,0, jeśli dane wejściowe nie mogą być konwertowane na wartość tego typu.

We wszystkich przypadkach poza zakresem **errno** jest ustawiony na **ERANGE**. Jeśli przekazanie parametru ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EINVAL** i zwracają 0.

## <a name="remarks"></a>Uwagi

Te funkcje konwertują ciąg znaków na podwójną precyzję wartości zmiennoprzecinkowej.

Ciąg wejściowy jest sekwencją znaków, które mogą być interpretowane jako wartość liczbowa określonego typu. Funkcja przestaje odczytywać ciąg wejściowy przy pierwszym znaku, którego nie może rozpoznać jako część liczby. Ten znak może być znakiem null (' \ 0 ' lub L ' \ 0 '), który kończy ciąg.

Ciąg *str* do **atof** i **_wtof** ma następującą postać:

[*odstęp*] [*Sign*] [*cyfry*] [__.__ *cyfry*] [{**e** &#124; **e** } [*Sign*]*cyfry*]

*Odstęp* składa się ze znaków spacji lub tabulatora, które są ignorowane; *znak* jest znakiem plus (+) lub minus (-); i *cyfry* są jedną lub większą liczbą cyfr dziesiętnych. Jeśli żadne cyfry nie pojawiają się przed punktem dziesiętnym, co najmniej jeden musi pojawić się po przecinku dziesiętnym. Po cyfrach dziesiętnych mogą występować wykładnika, która składa się z litery wprowadzającej (**e**lub **e**) i opcjonalnie cyfry dziesiętnej ze znakiem.

Wersje UCRT tych funkcji nie obsługują konwersji liter wykładnika Pascal (**d** lub **d**). To niestandardowe rozszerzenie było obsługiwane przez wcześniejsze wersje CRT i może być istotną zmianą dla kodu.

Wersje tych funkcji z sufiksem **_l** są identyczne, z tą różnicą, że korzystają z przekazaną parametrem *ustawień regionalnych* zamiast bieżących ustawień regionalnych.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstof**|**atof**|**atof**|**_wtof**|
|**_ttof**|**atof**|**atof**|**_wtof**|

## <a name="requirements"></a>Wymagania

|Procedury (s)|Wymagany nagłówek|
|------------------|---------------------|
|**atof**, **_atof_l**|C: \<math.h> lub \<stdlib.h> C++: \<cstdlib> , \<stdlib.h> \<cmath> lub\<math.h>|
|**_wtof**, **_wtof_l**|C: \<stdlib.h> lub \<wchar.h> C++: \<cstdlib> , \<stdlib.h> lub\<wchar.h>|

## <a name="example"></a>Przykład

Ten program pokazuje, jak liczby przechowywane jako ciągi mogą być konwertowane na wartości liczbowe przy użyciu funkcji **atof** i **_atof_l** .

```C
// crt_atof.c
//
// This program shows how numbers stored as
// strings can be converted to numeric
// values using the atof and _atof_l functions.

#include <stdlib.h>
#include <stdio.h>
#include <locale.h>

int main(void)
{
    char    *str = NULL;
    double value = 0;
    _locale_t fr = _create_locale(LC_NUMERIC, "fr-FR");

    // An example of the atof function
    // using leading and training spaces.
    str = "  3336402735171707160320 ";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);

    // Another example of the atof function
    // using the 'E' exponential formatting keyword.
    str = "3.1412764583E210";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);

    // An example of the atof and _atof_l functions
    // using the 'e' exponential formatting keyword
    // and showing different decimal point interpretations.
    str = "  -2,309e-25";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);
    value = _atof_l(str, fr);
    printf("Function: _atof_l(\"%s\", fr)) = %e\n", str, value);
}
```

```Output
Function: atof("  3336402735171707160320 ") = 3.336403e+21
Function: atof("3.1412764583E210") = 3.141276e+210
Function: atof("  -2,309e-25") = -2.000000e+00
Function: _atof_l("  -2,309e-25", fr)) = -2.309000e-25
```

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[Regionalne](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
