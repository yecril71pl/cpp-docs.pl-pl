---
title: atof, _atof_l, _wtof, _wtof_l
ms.date: 04/05/2018
apiname:
- _wtof_l
- atof
- _atof_l
- _wtof
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: 6c2ec158ac0b75a861b5b226d33de113d76988cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471178"
---
# <a name="atof-atofl-wtof-wtofl"></a>atof, _atof_l, _wtof, _wtof_l

Konwertuj ciąg na podwójny.

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
Ciąg, który ma zostać przekonwertowany.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca **double** wartość generowana przez zinterpretowanie wprowadzonych znaków jako liczby. Wartość zwracana jest 0,0, jeśli dane wejściowe nie można przekonwertować na wartość tego typu.

We wszystkich przypadkach spoza zakresu **errno** ustawiono **ERANGE**. Jeśli parametr przekazany w **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają 0.

## <a name="remarks"></a>Uwagi

Te funkcje konwertują ciąg znaków na wartość podwójnej precyzji, zmiennoprzecinkowych.

Ciąg wejściowy jest sekwencją znaków, które mogą być interpretowane jako wartość liczbowa określonego typu. Funkcja przestaje odczytywać ciąg wejściowy przy pierwszym znaku, który nie może rozpoznać jako elementu liczby. Ten znak może być znakiem null ('\0' lub L '\0') zakończenie ciągu.

*Str* argument **atof —** i **_wtof —** ma następującą postać:

[*odstępu*] [*logowania*] [*cyfr*] [__.__ *cyfr*] [{**e** &#124; **E** } [*logowania*]*cyfr*]

A *odstępu* składa się ze znaków spacji lub tabulatorów, które są ignorowane. *logowania* jest plus (+) lub minus (-); i *cyfr* są co najmniej jedna cyfra dziesiętna. Jeśli żadna cyfra pojawia się przed przecinkiem dziesiętnym, co najmniej jedna musi znajdować się po punkcie dziesiętnym. Cyfr dziesiętnych może następować wykładnik, który składa się z litery wprowadzającej (**e**, lub **E**) i opcjonalnie podpisem dziesiętna liczba całkowita.

UCRT wersje tych funkcji nie obsługują konwersję Fortran stylu (**d** lub **D**) litery wykładnika. To rozszerzenie niestandardowe była obsługiwana przez wcześniejsze wersje CRT i może być istotnej zmiany w kodzie.

Wersje tych funkcji **_l** sufiksem są identyczne, z tą różnicą, że używają one *ustawień regionalnych* przekazany parametr zamiast bieżących ustawień regionalnych.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstof —**|**atof**|**atof**|**_wtof**|
|**_ttof —**|**atof**|**atof**|**_wtof**|

## <a name="requirements"></a>Wymagania

|Routine(s)|Wymagany nagłówek|
|------------------|---------------------|
|**atof —**, **_atof_l —**|C: \<math.h > lub \<stdlib.h > C++: \<cstdlib — >, \<stdlib.h >, \<cmath > lub \<math.h >|
|**_wtof —**, **_wtof_l —**|C: \<stdlib.h > lub \<wchar.h > C++: \<cstdlib — >, \<stdlib.h > lub \<wchar.h >|

## <a name="example"></a>Przykład

Ten program ilustruje, jak liczb przechowywanych jako ciągi można przekonwertować wartości liczbowych przy użyciu **atof —** i **_atof_l —** funkcji.

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
[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
