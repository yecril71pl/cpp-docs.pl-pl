---
title: DIV, ldiv, LLDiv
ms.date: 04/05/2018
api_name:
- div
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
- div
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
ms.openlocfilehash: 24432ec1514f6cd2d569fd5752a8ed7118059d6a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234227"
---
# <a name="div-ldiv-lldiv"></a>DIV, ldiv, LLDiv

Oblicza iloraz i resztę dwóch wartości całkowitych.

## <a name="syntax"></a>Składnia

```C
div_t div(
   int numer,
   int denom
);
ldiv_t ldiv(
   long numer,
   long denom
);
lldiv_t lldiv(
   long long numer,
   long long denom
);
```

```cpp
ldiv_t div(
   long numer,
   long denom
); /* C++ only */
lldiv_t div(
   long long numer,
   long long denom
); /* C++ only */
```

### <a name="parameters"></a>Parametry

*numeracj*<br/>
Licznik.

*denom*<br/>
Mianownik.

## <a name="return-value"></a>Wartość zwracana

**blok DIV** wywoływany za pomocą argumentów typu **`int`** zwraca strukturę typu **div_t**, która składa się z ilorazu i reszty. Zwracaną wartością z argumentami typu **`long`** jest **ldiv_t**, a zwracaną wartością z argumentami typu **`long long`** jest **lldiv_t**. **div_t**, **ldiv_t**i **lldiv_t** są zdefiniowane w \<stdlib.h> .

## <a name="remarks"></a>Uwagi

Funkcja **DIV** dzieli *numer* przez *denom* , a tym samym Oblicza iloraz i resztę. Struktura [div_t](../../c-runtime-library/standard-types.md) zawiera iloraz, **Quote**i resztę, **REM**. Znak ilorazu jest taki sam jak w przypadku ilorazu matematycznego. Wartość bezwzględna jest największą liczbą całkowitą, która jest mniejsza niż wartość bezwzględna ilorazu matematycznego. Jeśli mianownik ma wartość 0, program kończy pracę z komunikatem o błędzie.

Przeciążenia elementu **DIV** , które przyjmują argumenty typu **`long`** lub **`long long`** są dostępne tylko dla kodu C++. Typy zwracane [ldiv_t](../../c-runtime-library/standard-types.md) i [lldiv_t](../../c-runtime-library/standard-types.md) zawierają elementy **Quote** i **REM**, które mają takie same znaczenie jak elementy członkowskie **div_t**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**DIV**, **ldiv**, **LLDiv**|\<stdlib.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_div.c
// arguments: 876 13

// This example takes two integers as command-line
// arguments and displays the results of the integer
// division. This program accepts two arguments on the
// command line following the program name, then calls
// div to divide the first argument by the second.
// Finally, it prints the structure members quot and rem.
//

#include <stdlib.h>
#include <stdio.h>
#include <math.h>

int main( int argc, char *argv[] )
{
   int x,y;
   div_t div_result;

   x = atoi( argv[1] );
   y = atoi( argv[2] );

   printf( "x is %d, y is %d\n", x, y );
   div_result = div( x, y );
   printf( "The quotient is %d, and the remainder is %d\n",
           div_result.quot, div_result.rem );
}
```

```Output
x is 876, y is 13
The quotient is 67, and the remainder is 5
```

## <a name="see-also"></a>Zobacz także

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
