---
title: imaxdiv — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- imaxdiv
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
- imaxdiv
dev_langs:
- C++
helpviewer_keywords:
- imaxdiv function
ms.assetid: 7d90126f-fdc2-4986-9cdf-94e4c9123d26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db2a57e9b91672d39fbce5eaee061043604a0998
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399699"
---
# <a name="imaxdiv"></a>imaxdiv

Oblicza iloraz i pozostałej części dwóch wartości całkowite o dowolnym rozmiarze jako jedna operacja.

## <a name="syntax"></a>Składnia

```C
imaxdiv_t imaxdiv(
   intmax_t numer,
   intmax_t denom
);
```

### <a name="parameters"></a>Parametry

*numer*<br/>
Licznik.

*denom*<br/>
Denominator.

## <a name="return-value"></a>Wartość zwracana

**imaxdiv —** wywołana z argumentami typu [intmax_t](../../c-runtime-library/standard-types.md) zwraca struktura typu [imaxdiv_t](../../c-runtime-library/standard-types.md) który obejmuje iloraz, a reszta.

## <a name="remarks"></a>Uwagi

**Imaxdiv —** funkcji bez reszty *numer* przez *denom* i tym samym oblicza iloraz, a reszta. **Imaxdiv_t** struktura zawiera iloraz, **intmax_t** **quot**, a reszta, **intmax_t** **rem**. Znak iloraz jest taka sama jak iloraz matematycznych. Największa liczba całkowita, która jest mniejsza niż wartość bezwzględną liczby matematyczne iloraz ma jego wartość bezwzględna. Jeżeli dzielnik wynosi 0, program zakończy się z komunikatem o błędzie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**imaxdiv**|\<inttypes.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

Gdy wbudowane i następnie wywołana z parametrów wiersza polecenia `9460730470000000 8766`, kod generuje te dane wyjściowe:

```Output
The call to imaxdiv(9460730470000000, 8766)
results in a quotient of 1079252848505, and a remainder of 5170
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[div](div.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
