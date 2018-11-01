---
title: rand_s
ms.date: 1/02/2018
apiname:
- rand_s
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: d196a6f5d7483deb9a7e1b8d7fa929532b6197db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572721"
---
# <a name="rands"></a>rand_s

Generuje numer pseudolosowych. Jest to bardziej bezpieczna wersja funkcji [rand](rand.md), ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>Parametry

*randomValue*<br/>
Wskaźnik na liczbę całkowitą zawierającą wygenerowaną wartość.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli operacja się powiedzie, w przeciwnym razie, kod błędu. Jeśli wskaźnik danych wejściowych _randomValue_ jest pustym wskaźnikiem, funkcja wywołuje program obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca **EINVAL** i ustawia **errno** do **EINVAL**. Jeśli funkcja nie powiedzie się z jakiegokolwiek powodu, *_randomValue_ jest równa 0.

## <a name="remarks"></a>Uwagi

**Rand_s —** funkcja zapisuje pseudolosowych liczbą całkowitą z zakresu od 0 do **UINT_MAX** na wskaźnik danych wejściowych. **Rand_s —** funkcja używa systemu operacyjnego do generowania liczb losowych kryptograficznie bezpieczne. Używaj inicjatora generowane przez [srand —](srand.md) funkcji, ani nie ogranicza losową sekwencję liczb, używane przez [rand](rand.md).

**Rand_s —** funkcja wymaga, aby stała tym **_CRT_RAND_S** można zdefiniować przed instrukcji dołączania dla funkcji, które mają zostać zadeklarowane, jak w poniższym przykładzie:

```C
#define _CRT_RAND_S
#include <stdlib.h>
```

**rand_s —** zależy od [RtlGenRandom](/windows/desktop/api/ntsecapi/nf-ntsecapi-rtlgenrandom) interfejsu API, który jest tylko dostępne w Windows XP i nowszych wersjach.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**rand_s**|\<stdlib.h>|

Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
