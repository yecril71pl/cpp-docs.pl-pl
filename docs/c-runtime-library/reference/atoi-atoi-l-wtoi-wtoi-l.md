---
title: atoi, _atoi_l, _wtoi, _wtoi_l
ms.date: 11/04/2016
apiname:
- _wtoi
- _wtoi_l
- atoi
- _atoi_l
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
- _tstoi
- _wtoi
- _ttoi
- atoi
- _atoi_l
- _wtoi_l
helpviewer_keywords:
- _atoi_l function
- ttoi function
- atoi_l function
- string conversion, to integers
- _wtoi function
- wtoi_l function
- tstoi function
- _ttoi function
- _tstoi function
- _wtoi_l function
- atoi function
- wtoi function
ms.assetid: ad7fda30-28ab-421f-aaad-ef0b8868663a
ms.openlocfilehash: 5c03f2766701f7e360ad0bf4f0fc701d2a7e983c
ms.sourcegitcommit: b401a05c5c0f5cc4b32893d7382c05a51e4ab783
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "50999989"
---
# <a name="atoi-atoil-wtoi-wtoil"></a>atoi, _atoi_l, _wtoi, _wtoi_l

Konwertowanie ciągu na liczbę całkowitą.

## <a name="syntax"></a>Składnia

```C
int atoi(
   const char *str
);
int _wtoi(
   const wchar_t *str
);
int _atoi_l(
   const char *str,
   _locale_t locale
);
int _wtoi_l(
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

Każda funkcja zwraca **int** wartość generowana przez zinterpretowanie wprowadzonych znaków jako liczby. Wartość zwracana to 0 dla **atoi —** i **_wtoi —**, jeśli dane wejściowe nie można przekonwertować na wartość tego typu.

W przypadku przepełnienia o dużych ujemnych wartościach całkowitych **LONG_MIN** jest zwracana. **atoi —** i **_wtoi —** zwracają **INT_MAX** i **INT_MIN** na te warunki. We wszystkich przypadkach spoza zakresu **errno** ustawiono **ERANGE**. Jeśli parametr przekazany w **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają 0.

## <a name="remarks"></a>Uwagi

Te funkcje konwertują ciąg znaków na wartość całkowitą (**atoi —** i **_wtoi —**). Ciąg wejściowy jest sekwencją znaków, które mogą być interpretowane jako wartość liczbowa określonego typu. Funkcja przestaje odczytywać ciąg wejściowy przy pierwszym znaku, który nie może rozpoznać jako elementu liczby. Ten znak może być znakiem null ('\0' lub L '\0') zakończenie ciągu.

*Str* argument **atoi —** i **_wtoi —** ma następującą postać:

> [*odstępu*] [*logowania*] [*cyfr*]]

A *odstępu* składa się ze znaków spacji lub tabulatorów, które są ignorowane. *logowania* jest plus (+) lub minus (-); i *cyfr* to jedna lub więcej cyfr.

Wersje tych funkcji **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstoi —**|**atoi**|**atoi**|**_wtoi**|
|**_ttoi —**|**atoi**|**atoi**|**_wtoi**|

## <a name="requirements"></a>Wymagania

|Procedury|Wymagany nagłówek|
|--------------|---------------------|
|**atoi**|\<stdlib.h>|
|**_atoi_l —**, **_wtoi —**, **_wtoi_l —**|\<stdlib.h > lub \<wchar.h >|

## <a name="example"></a>Przykład

Ten program ilustruje, jak liczb przechowywanych jako ciągi można przekonwertować wartości liczbowych przy użyciu **atoi —** funkcji.

```C
// crt_atoi.c
// This program shows how numbers
// stored as strings can be converted to
// numeric values using the atoi functions.

#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
    char    *str = NULL;
    int     value = 0;

    // An example of the atoi function.
    str = "  -2309 ";
    value = atoi( str );
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );

    // Another example of the atoi function.
    str = "31412764";
    value = atoi( str );
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );

    // Another example of the atoi function
    // with an overflow condition occurring.
    str = "3336402735171707160320";
    value = atoi( str );
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );
    if (errno == ERANGE)
    {
       printf("Overflow condition occurred.\n");
    }
}
```

```Output
Function: atoi( "  -2309 " ) = -2309
Function: atoi( "31412764" ) = 31412764
Function: atoi( "3336402735171707160320" ) = 2147483647
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
