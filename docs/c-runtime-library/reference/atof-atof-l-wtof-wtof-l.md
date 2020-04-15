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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 492719a0cc0f8ac079b257ec8d7aa1014c5b2a86
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348921"
---
# <a name="atof-_atof_l-_wtof-_wtof_l"></a>atof, _atof_l, _wtof, _wtof_l

Konwertuj ciąg na podwójną.

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

*Str*<br/>
Ciąg do konwersji.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca **podwójną** wartość wyprodukowaną przez interpretację znaków wejściowych jako liczby. Zwracana wartość wynosi 0,0, jeśli nie można przekonwertować danych wejściowych na wartość tego typu.

We wszystkich przypadkach poza zasięgiem **errno** jest ustawiony na **ERANGE**. Jeśli parametr przekazywany w ma **wartość NULL,** wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [yd.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te funkcje ustawić **errno** **na EINVAL** i zwracać 0.

## <a name="remarks"></a>Uwagi

Te funkcje konwertuje ciąg znaków na podwójną precyzję, wartość zmiennoprzecinkowa.

Ciąg wejściowy jest sekwencją znaków, które mogą być interpretowane jako wartość liczbowa określonego typu. Funkcja zatrzymuje odczytywanie ciągu wejściowego przy pierwszym znaku, który nie może rozpoznać jako część liczby. Ten znak może być znakiem zerowym ('\0' lub L'\0') kończącym ciąg.

Argument *str* do **atof** i **_wtof** ma następującą formę:

[*odstępy*] [*znak*] [*cyfry*] [__.__ *cyfry*] [ {**e** &#124; **E** }[*znak*]*cyfry*]

Odstęp *składa* się ze znaków spacji lub tabulacji, które są ignorowane; *znak* jest plus (+) lub minus (-); i *cyfry* są jedną lub więcej cyfr dziesiętnych. Jeśli przed przecinem dziesiętnym nie pojawią się żadne cyfry, po przecinku musi pojawić się co najmniej jedna cyfra. Po cyfrach dziesiętnych może następować wykładnik, który składa się z litery wprowadzającej (**e**lub **E)** i opcjonalnie podpisanej liczby dziesiętnej.

Wersje UCRT tych funkcji nie obsługują konwersji liter wykładniczych w stylu Fortran **(d** lub **D).** To niestandardowe rozszerzenie było obsługiwane przez wcześniejsze wersje CRT i może być przełomową zmianą dla kodu.

Wersje tych funkcji z sufiksem **_l** są *identyczne,* z tą różnicą, że używają parametru ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstof**|**atof**|**atof**|**_wtof**|
|**_ttof**|**atof**|**atof**|**_wtof**|

## <a name="requirements"></a>Wymagania

|Rutyna(-y)|Wymagany nagłówek|
|------------------|---------------------|
|**atof**, **_atof_l**|C: \<math.h> lub \<stdlib.h> C++: \<cstdlib>, \<stdlib.h>, \<cmath> lub \<math.h>|
|**_wtof** **, _wtof_l**|C: \< \<> lub wchar.h> C++: \<cstdlib>, \<stdlib.h> lub \<wchar.h>|

## <a name="example"></a>Przykład

Ten program pokazuje, jak liczby przechowywane jako ciągi mogą być konwertowane na wartości liczbowe za pomocą funkcji **atof** i **_atof_l.**

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

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
