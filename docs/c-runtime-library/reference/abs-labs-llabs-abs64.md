---
title: Funkcje ABS, laboratoria, llabs — _abs64 — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- abs
- _abs64
- labs
- llabs
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
- stdlib/_abs64
- math/abs
- _abs64
- abs
- labs
- math/labs
- llabs
- math/llabs
- cmath/abs
dev_langs:
- C++
helpviewer_keywords:
- absolute values
- abs function
- abs64 function
- _abs64 function
- calculating absolute values
ms.assetid: 60f789d1-4a1e-49f5-9e4e-0bdb277ea26a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1380a6e56ce444e80feccf3e8306a0a589c98d01
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085267"
---
# <a name="abs-labs-llabs-abs64"></a>Funkcje ABS, laboratoria, llabs — _abs64 —

Oblicza wartość bezwzględną argumentu.

## <a name="syntax"></a>Składnia

```C
int abs( int n );
long labs( long n );
long long llabs( long long n );
__int64 _abs64( __int64 n );
```

```cpp
long abs( long n );   // C++ only
long long abs( long long n );   // C++ only
double abs( double n );   // C++ only
long double abs( long double n );   // C++ only
float abs( float n );   // C++ only
```

### <a name="parameters"></a>Parametry

*N*<br/>
Wartość liczbowa.

## <a name="return-value"></a>Wartość zwracana

**Abs**, **labs**, **llabs —** i **_abs64 —** funkcje zwracają wartość bezwzględna parametru *n*. Nie będzie zwrotu błędu.

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na przeciążenie, można wywoływać przeciążenia **abs** przyjmujące i zwracające **długie**, **długie** **długie**,  **float**, **double**, i **długie** **double** wartości. Te przeciążenia są zdefiniowane w \<cmath > nagłówka. W programie C **abs** zawsze przyjmuje i zwraca **int**.

**Microsoft Specific**: ponieważ zakres ujemnych liczb całkowitych, które mogą być reprezentowane za pomocą dowolnego typu integralnego, jest większy niż zakres dodatnich liczb całkowitych, które mogą być reprezentowane za pomocą tego typu, jest możliwe, aby podać argument do tych Funkcje, które nie może zostać przekonwertowany. Jeśli wartość bezwzględna argumentu nie może być przedstawiona przez zwracany typ **abs** funkcje zwracają niezmienioną wartość argumentu. W szczególności `abs(INT_MIN)` zwraca `INT_MIN`, `labs(LONG_MIN)` zwraca `LONG_MIN`, `llabs(LLONG_MIN)` zwraca `LLONG_MIN`, i `_abs64(_I64_MIN)` zwraca `_I64_MIN`. Oznacza to, że **abs** funkcji nie może służyć do zagwarantowania wartości dodatniej.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek języka C|Wymagany nagłówek C++|
|-------------|-----------------------|---------------------------|
|**ABS**, **labs**, **llabs —**|\<Math.h > lub \<stdlib.h >|\<cmath >, \<cstdlib — >, \<stdlib.h > lub \<math.h >|
|**_abs64**|\<stdlib.h>|\<cstdlib — > lub \<stdlib.h >|

Aby użyć przeciążone wersje **abs** w języku C++, należy uwzględnić \<cmath > nagłówka.

## <a name="example"></a>Przykład

Program ten wylicza i wyświetla wartości bezwzględne dla kilku numerów.

```C
// crt_abs.c
// Build: cl /W3 /TC crt_abs.c
// This program demonstrates the use of the abs function
// by computing and displaying the absolute values of
// several numbers.

#include <stdio.h>
#include <math.h>
#include <stdlib.h>
#include <limits.h>

int main( void )
{
    int ix = -4;
    long lx = -41567L;
    long long llx = -9876543210LL;
    __int64 wx = -1;

    // absolute 32 bit integer value
    printf_s("The absolute value of %d is %d\n", ix, abs(ix));

    // absolute long integer value
    printf_s("The absolute value of %ld is %ld\n", lx, labs(lx));

    // absolute long long integer value
    printf_s("The absolute value of %lld is %lld\n", llx, llabs(llx));

    // absolute 64 bit integer value
    printf_s("The absolute value of 0x%.16I64x is 0x%.16I64x\n", wx,
        _abs64(wx));

    // Integer error cases:
    printf_s("Microsoft implementation-specific results:\n");
    printf_s(" abs(INT_MIN) returns %d\n", abs(INT_MIN));
    printf_s(" labs(LONG_MIN) returns %ld\n", labs(LONG_MIN));
    printf_s(" llabs(LLONG_MIN) returns %lld\n", llabs(LLONG_MIN));
    printf_s(" _abs64(_I64_MIN) returns 0x%.16I64x\n", _abs64(_I64_MIN));
}
```

```Output
The absolute value of -4 is 4
The absolute value of -41567 is 41567
The absolute value of -9876543210 is 9876543210
The absolute value of 0xffffffffffffffff is 0x0000000000000001
Microsoft implementation-specific results:
abs(INT_MIN) returns -2147483648
labs(LONG_MIN) returns -2147483648
llabs(LLONG_MIN) returns -9223372036854775808
_abs64(_I64_MIN) returns 0x8000000000000000
```

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[_cabs](cabs.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[imaxabs](imaxabs.md)