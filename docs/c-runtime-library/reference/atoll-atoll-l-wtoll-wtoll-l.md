---
title: Atol, _atoll_l —, _wtoll — _wtoll_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- atoll function
- _wtoll_l function
- _wtoll function
- _atoll_l function
ms.assetid: 5e85fcac-b351-4882-bff2-6e7c469b7fa8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 15a0753a487d969d3f75e1e41b6509ea40b9b19f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396118"
---
# <a name="atoll-atolll-wtoll-wtolll"></a>atoll, _atoll_l, _wtoll, _wtoll_l

Konwertuje ciąg na **długi** **długi** liczby całkowitej.

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
Ciąg do przekonwertowania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca każdej funkcji **długi** **długi** wartość, która jest generowany przez interpretowanie znaków wejściowy jako liczby. Wartość zwracana **Atol** wynosi 0, jeśli dane wejściowe nie można przekonwertować wartości tego typu.

Dla przepełnienie o dużych dodatnie wartości całkowite **Atol** zwraca **LLONG_MAX**, i do przepełnienia o dużych wartościach całkowitych ujemnych, zwraca **LLONG_MIN**.

We wszystkich przypadkach out-of-range **errno** ustawiono **erange —**. Jeśli parametr przekazywany jest **NULL**, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji **errno** do **einval —** i zwraca 0.

## <a name="remarks"></a>Uwagi

Ciąg znaków, aby przekonwertować te funkcje **długi** **długi** wartości całkowitej.

Ciąg wejściowy jest sekwencji znaków, które mogą być interpretowane jako wartość liczbowa określonego typu. Funkcja zatrzymuje odczytywania ciąg wejściowy pierwszego znaku, który nie jest rozpoznawana jako część liczby. Ten znak może być znak null ('\0' lub L '\0'), który kończy ciąg.

*Str* argument **Atol** ma następujący format:

> [*odstępem*] [*znak*] [*cyfr*]

A *odstępem* zawiera spację lub tabulator znaki, które są ignorowane. *znak* jest plus (+) lub minus (-); i *cyfr* są co najmniej jedną cyfrę.

**_wtoll —** jest taka sama jak **Atol** z tą różnicą, że trwa ciąg znaków typu wide jako parametr.

Wersje tych funkcji, które mają **_l** sufiks są takie same jak wersje, które nie mają, z wyjątkiem tego, aby używały parametr ustawień regionalnych, który jest przekazywany w zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

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

Ten program przedstawia sposób użycia **Atol** funkcji konwertuje przechowywanych jako ciągi jako wartości liczbowych.

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
