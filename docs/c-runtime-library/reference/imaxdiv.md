---
title: imaxdiv
ms.date: 04/05/2018
api_name:
- imaxdiv
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
- imaxdiv
helpviewer_keywords:
- imaxdiv function
ms.assetid: 7d90126f-fdc2-4986-9cdf-94e4c9123d26
ms.openlocfilehash: 72bbb1198b79d79bb81acc35ce6c2a836fdd5f1d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954634"
---
# <a name="imaxdiv"></a>imaxdiv

Oblicza iloraz i resztę dwóch wartości całkowitych dowolnego rozmiaru w ramach jednej operacji.

## <a name="syntax"></a>Składnia

```C
imaxdiv_t imaxdiv(
   intmax_t numer,
   intmax_t denom
);
```

### <a name="parameters"></a>Parametry

*numeracj*<br/>
Licznik.

*denom*<br/>
Mianownik.

## <a name="return-value"></a>Wartość zwracana

**imaxdiv** wywołana z argumentami typu [intmax_t](../../c-runtime-library/standard-types.md) zwraca strukturę typu [imaxdiv_t](../../c-runtime-library/standard-types.md) , która składa się z ilorazu i reszty.

## <a name="remarks"></a>Uwagi

Funkcja **imaxdiv** dzieli *numer* przez *denom* , a tym samym Oblicza iloraz i resztę. Struktura **imaxdiv_t** zawiera iloraz, **intmax_t** **Quote**i resztę, **intmax_t** **REM**. Znak ilorazu jest taki sam jak w przypadku ilorazu matematycznego. Wartość bezwzględna jest największą liczbą całkowitą, która jest mniejsza niż wartość bezwzględna ilorazu matematycznego. Jeśli mianownik ma wartość 0, program kończy pracę z komunikatem o błędzie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**imaxdiv**|\<inttypes.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_imaxdiv.c
// Build using: cl /W3 /Tc crt_imaxdiv.c
// This example takes two integers as command-line
// arguments and calls imaxdiv to divide the first
// argument by the second, then displays the results.

#include <stdio.h>
#include <stdlib.h>
#include <inttypes.h>

int main(int argc, char *argv[])
{
   intmax_t x,y;
   imaxdiv_t div_result;

   x = atoll(argv[1]);
   y = atoll(argv[2]);

   printf("The call to imaxdiv(%lld, %lld)\n", x, y);
   div_result = imaxdiv(x, y);
   printf("results in a quotient of %lld, and a remainder of %lld\n\n",
          div_result.quot, div_result.rem);
}
```

Po skompilowaniu `9460730470000000 8766`, a następnie wywołaniu przy użyciu parametrów wiersza polecenia, kod generuje te dane wyjściowe:

```Output
The call to imaxdiv(9460730470000000, 8766)
results in a quotient of 1079252848505, and a remainder of 5170
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[div](div.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
