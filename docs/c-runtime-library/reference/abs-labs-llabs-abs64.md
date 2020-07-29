---
title: abs, labs, llabs, _abs64
ms.date: 04/05/2018
api_name:
- abs
- _abs64
- labs
- llabs
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
- stdlib/_abs64
- math/abs
- _abs64
- abs
- labs
- math/labs
- llabs
- math/llabs
- cmath/abs
helpviewer_keywords:
- absolute values
- abs function
- abs64 function
- _abs64 function
- calculating absolute values
ms.assetid: 60f789d1-4a1e-49f5-9e4e-0bdb277ea26a
ms.openlocfilehash: 96363f8d2139a5c75ee25a2c43b4c7ef55094f13
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221994"
---
# <a name="abs-labs-llabs-_abs64"></a>abs, labs, llabs, _abs64

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

*Azotan*<br/>
Wartość numeryczna.

## <a name="return-value"></a>Wartość zwracana

Funkcje **ABS**, **Labs**, **llabs** i **_abs64** zwracają wartość bezwzględną parametru *n*. Brak powrotu błędu.

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia metody **ABS** , które pobierają i **`long`** zwracają **`long long`** wartości,,, **`float`** **`double`** i **`long double`** . Te przeciążenia są zdefiniowane w \<cmath> nagłówku. W programie w języku C funkcja **ABS** zawsze przyjmuje i zwraca **`int`** .

**Specyficzne dla firmy Microsoft**: ponieważ zakres ujemnych liczb całkowitych, które mogą być reprezentowane przy użyciu dowolnego typu całkowitego, jest większy niż zakres dodatnich liczb całkowitych, które mogą być reprezentowane za pomocą tego typu, możliwe jest podanie argumentu tym funkcjom, których nie można przekonwertować. Jeśli wartość bezwzględna argumentu nie może być reprezentowana przez zwracany typ, funkcje **ABS** zwracają wartość argumentu bez zmian. W celu zwraca, zwraca, zwraca, `abs(INT_MIN)` `INT_MIN` `labs(LONG_MIN)` `LONG_MIN` `llabs(LLONG_MIN)` `LLONG_MIN` i `_abs64(_I64_MIN)` zwraca `_I64_MIN` . Oznacza to, że funkcje **ABS** nie mogą być używane w celu zagwarantowania wartości dodatniej.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek C|Wymagany nagłówek C++|
|-------------|-----------------------|---------------------------|
|**ABS**, **Labs**, **llabs**|\<math.h> lub \<stdlib.h>|\<cmath>, \<cstdlib> \<stdlib.h> lub\<math.h>|
|**_abs64**|\<stdlib.h>|\<cstdlib> lub \<stdlib.h>|

Aby użyć przeciążonych wersji elementów **ABS** w języku C++, należy dołączyć \<cmath> nagłówek.

## <a name="example"></a>Przykład

Ten program oblicza i wyświetla wartości bezwzględne kilku liczb.

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
[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[_cabs](cabs.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[imaxabs](imaxabs.md)
