---
title: atoi, _atoi_l, _wtoi, _wtoi_l
ms.date: 4/2/2020
api_name:
- _wtoi
- _wtoi_l
- atoi
- _atoi_l
- _o__atoi_l
- _o__wtoi
- _o__wtoi_l
- _o_atoi
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: ef65f8986cf02b6385cbce71e5e81fa690b38b2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348865"
---
# <a name="atoi-_atoi_l-_wtoi-_wtoi_l"></a>atoi, _atoi_l, _wtoi, _wtoi_l

Konwertuj ciąg na całkowitą.

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

*Str*<br/>
Ciąg do konwersji.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca wartość **int** wyprodukowaną przez interpretację znaków wejściowych jako liczby. Zwracana wartość wynosi 0 dla **atoi** i **_wtoi**, jeśli nie można przekonwertować danych wejściowych na wartość tego typu.

W przypadku przepełnienia z dużymi ujemnymi wartościami całkowitymi zwracany jest **LONG_MIN.** **atoi** i **_wtoi** zwracają **INT_MAX** i **INT_MIN** na tych warunkach. We wszystkich przypadkach poza zasięgiem **errno** jest ustawiony na **ERANGE**. Jeśli parametr przekazywany w ma **wartość NULL,** wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [yd.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te funkcje ustawić **errno** **na EINVAL** i zwracać 0.

## <a name="remarks"></a>Uwagi

Te funkcje konwertują ciąg znaków na wartość całkowitą **(atoi** i **_wtoi**). Ciąg wejściowy jest sekwencją znaków, które mogą być interpretowane jako wartość liczbowa określonego typu. Funkcja zatrzymuje odczytywanie ciągu wejściowego przy pierwszym znaku, który nie może rozpoznać jako część liczby. Ten znak może być znakiem zerowym ('\0' lub L'\0') kończącym ciąg.

Argument *str* **do atoi** i **_wtoi** ma następującą formę:

> [*odstępy*] [*znak*] [*cyfry*]]

Odstęp *składa* się ze znaków spacji lub tabulacji, które są ignorowane; *znak* jest plus (+) lub minus (-); i *cyfry* są jedną lub więcej cyfr.

Wersje tych funkcji z sufiksem **_l** są identyczne, z tą różnicą, że używają parametru ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstoi**|**atoi ( atoi )**|**atoi ( atoi )**|**_wtoi**|
|**_ttoi**|**atoi ( atoi )**|**atoi ( atoi )**|**_wtoi**|

## <a name="requirements"></a>Wymagania

|Procedur|Wymagany nagłówek|
|--------------|---------------------|
|**atoi ( atoi )**|\<>|
|**_atoi_l** **_wtoi** **_wtoi_l**|\<> lub \<wchar.h>|

## <a name="example"></a>Przykład

Ten program pokazuje, jak liczby przechowywane jako ciągi mogą być konwertowane na wartości liczbowe za pomocą funkcji **atoi.**

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

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
