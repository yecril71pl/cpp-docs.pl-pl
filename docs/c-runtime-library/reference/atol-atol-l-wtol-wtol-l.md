---
title: atol, _atol_l, _wtol, _wtol_l
ms.date: 11/04/2016
apiname:
- atol
- _wtol_l
- _wtol
- _atol_l
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
- _atol_l
- _ttol_l
- _tstol_l
- _tstol
- _wtol
- _ttol
- _wtol_l
helpviewer_keywords:
- tstol function
- atol function
- ttol function
- _atol_l function
- _tstol_l function
- string conversion, to integers
- _tstol function
- _ttol function
- _ttol_l function
- atol_l function
- wtol_l function
- _wtol_l function
- wtol function
- _wtol function
ms.assetid: cedfc21c-2d64-4e9c-bd04-bdf60b12db46
ms.openlocfilehash: 486b6dc3bdfbbaf4b7becadde76768a0bb1c7c00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537192"
---
# <a name="atol-atoll-wtol-wtoll"></a>atol, _atol_l, _wtol, _wtol_l

Konwertuj ciąg na liczba całkowita typu long.

## <a name="syntax"></a>Składnia

```C
long atol(
   const char *str
);
long _atol_l(
   const char *str,
   _locale_t locale
);
long _wtol(
   const wchar_t *str
);
long _wtol_l(
   const wchar_t *str,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Ciąg, który ma zostać przekonwertowany.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca **długie** wartość generowana przez zinterpretowanie wprowadzonych znaków jako liczby. Wartość zwracana jest 0L- **Atol —** Jeśli danych wejściowych nie można przekonwertować na wartość tego typu.

W przypadku przepełnienia z dużymi dodatnimi wartościami całkowitymi **Atol —** zwraca **LONG_MAX**; w przypadku przepełnienia o dużych ujemnych wartościach całkowitych **LONG_MIN** jest zwracane. We wszystkich przypadkach spoza zakresu **errno** ustawiono **ERANGE**. Jeśli parametr przekazany w **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają 0.

## <a name="remarks"></a>Uwagi

Te funkcje konwertują ciąg znaków na wartość typu Liczba całkowita typu long (**Atol —**).

Ciąg wejściowy jest sekwencją znaków, które mogą być interpretowane jako wartość liczbowa określonego typu. Funkcja przestaje odczytywać ciąg wejściowy przy pierwszym znaku, który nie może rozpoznać jako elementu liczby. Ten znak może być znakiem null ('\0' lub L '\0') zakończenie ciągu.

*Str* argument **Atol —** ma następującą postać:

> [*odstępu*] [*logowania*] [*cyfr*]]

A *odstępu* składa się ze znaków spacji lub tabulatorów, które są ignorowane. *logowania* jest plus (+) lub minus (-); i *cyfr* to jedna lub więcej cyfr.

**_wtol —** jest taka sama jak **Atol —** z tą różnicą, że wykorzystuje ciąg znaku dwubajtowego.

Wersje tych funkcji **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstol —**|**atol**|**atol**|**_wtol**|
|**_ttol —**|**atol**|**atol**|**_wtol**|

## <a name="requirements"></a>Wymagania

|Procedury|Wymagany nagłówek|
|--------------|---------------------|
|**atol**|\<stdlib.h>|
|**_atol_l —**, **_wtol —**, **_wtol_l —**|\<stdlib.h > i \<wchar.h >|

## <a name="example"></a>Przykład

Ten program ilustruje, jak liczb przechowywanych jako ciągi można przekonwertować wartości liczbowych przy użyciu **Atol —** funkcji.

```C
// crt_atol.c
// This program shows how numbers stored as
// strings can be converted to numeric values
// using the atol functions.
#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
    char    *str = NULL;
    long    value = 0;

    // An example of the atol function
    // with leading and trailing white spaces.
    str = "  -2309 ";
    value = atol( str );
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );

    // Another example of the atol function
    // with an arbitrary decimal point.
    str = "314127.64";
    value = atol( str );
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );

    // Another example of the atol function
    // with an overflow condition occurring.
    str = "3336402735171707160320";
    value = atol( str );
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );
    if (errno == ERANGE)
    {
       printf("Overflow condition occurred.\n");
    }
}
```

```Output
Function: atol( "  -2309 " ) = -2309
Function: atol( "314127.64" ) = 314127
Function: atol( "3336402735171707160320" ) = 2147483647
Overflow condition occurred.
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
