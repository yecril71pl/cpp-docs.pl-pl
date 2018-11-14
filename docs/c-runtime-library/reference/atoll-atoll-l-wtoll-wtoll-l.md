---
title: atoll, _atoll_l, _wtoll, _wtoll_l
ms.date: 11/04/2016
apiname:
- _wtoll
- _atoll_l
- _wtoll_l
- atoll
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
- _tstoll_l
- _wtoll
- _atoll_l
- _ttoll
- _tstoll
- _wtoll_l
- atoll
helpviewer_keywords:
- atoll function
- _wtoll_l function
- _wtoll function
- _atoll_l function
ms.assetid: 5e85fcac-b351-4882-bff2-6e7c469b7fa8
ms.openlocfilehash: 7933b3e25185b5abdbd10c1b3fd616742bb28f92
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521573"
---
# <a name="atoll-atolll-wtoll-wtolll"></a>atoll, _atoll_l, _wtoll, _wtoll_l

Konwertuje ciąg na **długie** **długie** liczby całkowitej.

## <a name="syntax"></a>Składnia

```C
long long atoll(
   const char *str
);
long long _wtoll(
   const wchar_t *str
);
long long _atoll_l(
   const char *str,
   _locale_t locale
);
long long _wtoll_l(
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

Każda funkcja zwraca **długie** **długie** wartość, która jest generowana przez zinterpretowanie wprowadzonych znaków jako liczby. Wartość zwracana dla **Atol** wynosi 0, jeśli dane wejściowe nie można przekonwertować na wartość tego typu.

Dla przepełnienia z dużymi dodatnimi wartościami całkowitymi **Atol** zwraca **LLONG_MAX**, a dla przepełnienia o dużych ujemnych wartościach całkowitych, zwraca **LLONG_MIN**.

We wszystkich przypadkach spoza zakresu **errno** ustawiono **ERANGE**. Jeśli parametr, który jest przekazywany jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają 0.

## <a name="remarks"></a>Uwagi

Te funkcje konwertują ciąg znaków do **długie** **długie** wartość całkowitą.

Ciąg wejściowy jest sekwencją znaków, które mogą być interpretowane jako wartość liczbowa określonego typu. Funkcja przestaje odczytywać ciąg wejściowy przy pierwszym znaku, który nie może rozpoznać jako elementu liczby. Ten znak może być znakiem null ('\0' lub L '\0'), który kończy ciąg.

*Str* argument **Atol** ma następującą postać:

> [*odstępu*] [*logowania*] [*cyfr*]

A *odstępu* składa się ze znaków spacji lub tabulatorów, które są ignorowane. *logowania* jest plus (+) lub minus (-); i *cyfr* to jedna lub więcej cyfr.

**_wtoll —** jest taka sama jak **Atol** z tą różnicą, że wykorzystuje ciąg znaku dwubajtowego jako parametr.

Wersje tych funkcji, które mają **_l** sufiksem są identyczne z wersjami, które nie mają, z tą różnicą, że używają parametru ustawień regionalnych, który jest przekazywany zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tstoll**|**atoll**|**atoll**|**_wtoll**|
|**_tstoll_l**|**_atoll_l**|**_atoll_l**|**_wtoll_l**|
|**_ttoll**|**_atoll**|**_atoll**|**_wtoll**|

## <a name="requirements"></a>Wymagania

|Procedury|Wymagany nagłówek|
|--------------|---------------------|
|**Atol**, **_atoll_l —**|\<stdlib.h>|
|**_wtoll —**, **_wtoll_l —**|\<stdlib.h > lub \<wchar.h >|

## <a name="example"></a>Przykład

Ten program ilustruje sposób używania **Atol** funkcje do konwersji liczb przechowywanych jako ciągi liczbowe na wartości liczbowe.

```C
// crt_atoll.c
// Build with: cl /W4 /Tc crt_atoll.c
// This program shows how to use the atoll
// functions to convert numbers stored as
// strings to numeric values.
#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main(void)
{
    char *str = NULL;
    long long value = 0;

    // An example of the atoll function
    // with leading and trailing white spaces.
    str = "  -27182818284 ";
    value = atoll(str);
    printf("Function: atoll(\"%s\") = %lld\n", str, value);

    // Another example of the atoll function
    // with an arbitrary decimal point.
    str = "314127.64";
    value = atoll(str);
    printf("Function: atoll(\"%s\") = %lld\n", str, value);

    // Another example of the atoll function
    // with an overflow condition occurring.
    str = "3336402735171707160320";
    value = atoll(str);
    printf("Function: atoll(\"%s\") = %lld\n", str, value);
    if (errno == ERANGE)
    {
       printf("Overflow condition occurred.\n");
    }
}
```

```Output
Function: atoll("  -27182818284 ") = -27182818284
Function: atoll("314127.64") = 314127
Function: atoll("3336402735171707160320") = 9223372036854775807
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
