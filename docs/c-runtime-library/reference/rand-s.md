---
title: rand_s
ms.date: 01/02/2018
api_name:
- rand_s
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
- api-ms-win-crt-utility-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- rand_s
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, cryptographically secure
- random numbers, generating
- rand_s function
- numbers, pseudorandom
- cryptographically secure random numbers
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: 652521ab472736783ba1b4498ca7d7c3f297e7ee
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949658"
---
# <a name="rand_s"></a>rand_s

Generuje numer pseudolosowych. Jest to bezpieczniejsza wersja funkcji [Rand](rand.md)z ulepszeniami zabezpieczeń opisanymi w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>Parametry

*randomValue*<br/>
Wskaźnik do liczby całkowitej, która przechowuje wygenerowaną wartość.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie, w przeciwnym razie, kod błędu. Jeśli wskaźnik wejściowy _randomValue_ jest wskaźnikiem o wartości null, funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca **EINVAL** i ustawia **errno** na **EINVAL**. Jeśli funkcja nie powiedzie się z innego powodu, *_randomValue_ jest ustawiona na 0.

## <a name="remarks"></a>Uwagi

Funkcja **rand_s** zapisuje liczbę całkowitą pseudolosowych z zakresu od 0 do **UINT_MAX** na wskaźnik wejściowy. Funkcja **rand_s** używa systemu operacyjnego do generowania kryptograficznie zabezpieczonych liczb losowych. Nie używa inicjatora wygenerowanego przez funkcję [srand](srand.md) ani nie ma wpływu na losową sekwencję liczbową używaną przez [Rand](rand.md).

Funkcja **rand_s** wymaga, aby stała **_CRT_RAND_S** była zdefiniowana przed instrukcją dołączenia dla funkcji, która ma zostać zadeklarowana, tak jak w poniższym przykładzie:

```C
#define _CRT_RAND_S
#include <stdlib.h>
```

**rand_s** zależy od interfejsu API [RtlGenRandom](/windows/win32/api/ntsecapi/nf-ntsecapi-rtlgenrandom) , który jest dostępny tylko w systemie Windows XP i nowszych.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**rand_s**|\<stdlib.h>|

Aby uzyskać więcej informacji, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_rand_s.c
// This program illustrates how to generate random
// integer or floating point numbers in a specified range.

// Remembering to define _CRT_RAND_S prior
// to inclusion statement.
#define _CRT_RAND_S

#include <stdlib.h>
#include <stdio.h>
#include <limits.h>

int main( void )
{
    int             i;
    unsigned int    number;
    double          max = 100.0;
    errno_t         err;

    // Display 10 random integers in the range [ 1,10 ].
    for( i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %u\n", (unsigned int) ((double)number /
                       ((double) UINT_MAX + 1 ) * 10.0) + 1);
    }

    printf_s("\n");

    // Display 10 random doubles in [0, max).
    for (i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %g\n", (double) number /
                          ((double) UINT_MAX + 1) * max );
    }
}
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
10
4
5
2
8
2
5
6
1
1

32.6617
29.4471
11.5413
6.41924
20.711
60.2878
61.0094
20.1222
80.9192
65.0712
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
[srand](srand.md)<br/>
