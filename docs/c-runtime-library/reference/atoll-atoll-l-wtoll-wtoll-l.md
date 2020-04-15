---
title: atoll, _atoll_l, _wtoll, _wtoll_l
ms.date: 4/2/2020
api_name:
- _wtoll
- _atoll_l
- _wtoll_l
- atoll
- _o__atoll_l
- _o__wtoll
- _o__wtoll_l
- _o_atoll
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
ms.openlocfilehash: 34b7d0fdedb55241452f9a7f9937b64c58f7772c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348716"
---
# <a name="atoll-_atoll_l-_wtoll-_wtoll_l"></a>atoll, _atoll_l, _wtoll, _wtoll_l

Konwertuje ciąg na **długą** **długą** liczę całkowitą.

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

*Str*<br/>
Ciąg do konwersji.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca **długą** **wartość,** która jest wytwarzana przez interpretację znaków wejściowych jako liczby. Zwracana wartość **atolu** wynosi 0, jeśli nie można przekonwertować danych wejściowych na wartość tego typu.

W przypadku przepełnienia dużymi dodatnimi wartościami całkowitymi **atol** zwraca **LLONG_MAX**, a w przypadku przepełnienia dużymi ujemnymi wartościami całkowitymi zwraca **LLONG_MIN**.

We wszystkich przypadkach poza zasięgiem **errno** jest ustawiony na **ERANGE**. Jeśli parametr, który jest przekazywany w jest **NULL**, nieprawidłowy program obsługi parametrów jest wywoływany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, te funkcje ustawić **errno** **na EINVAL** i zwracać 0.

## <a name="remarks"></a>Uwagi

Te funkcje konwertują ciąg znaków na **długą** **długą** wartość całkowitą.

Ciąg wejściowy jest sekwencją znaków, które mogą być interpretowane jako wartość liczbowa określonego typu. Funkcja zatrzymuje odczytywanie ciągu wejściowego przy pierwszym znaku, który nie może rozpoznać jako część liczby. Ten znak może być znakiem zerowym ('\0' lub L'\0'), który kończy ciąg.

Argument *str* do **atolu** ma następującą formę:

> [*odstępy*] [*znak*] [*cyfry*]

Odstęp *składa* się ze znaków spacji lub tabulacji, które są ignorowane; *znak* jest plus (+) lub minus (-); i *cyfry* są jedną lub więcej cyfr.

**_wtoll** jest identyczna **z atolem,** z tą różnicą, że przyjmuje szeroki ciąg znaków jako parametr.

Wersje tych funkcji, które mają sufiks **_l** są identyczne z wersjami, które go nie mają, z tą różnicą, że używają parametru ustawień regionalnych, który jest przekazywany zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tstoll**|**Atoll**|**Atoll**|**_wtoll**|
|**_tstoll_l**|**_atoll_l**|**_atoll_l**|**_wtoll_l**|
|**_ttoll**|**_atoll**|**_atoll**|**_wtoll**|

## <a name="requirements"></a>Wymagania

|Procedur|Wymagany nagłówek|
|--------------|---------------------|
|**atol**, **_atoll_l**|\<>|
|**_wtoll**, **_wtoll_l**|\<> lub \<wchar.h>|

## <a name="example"></a>Przykład

Ten program pokazuje, jak korzystać z funkcji **atolu** do konwersji liczb przechowywanych jako ciągi do wartości liczbowych.

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

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
