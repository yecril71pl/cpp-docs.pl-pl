---
title: 'Funkcje Bessela: _j0, _j1, _jn, _y0, _y1, _yn'
ms.date: 04/05/2018
apiname:
- _j0
- _j1
- _jn
- _y0
- _y1
- _yn
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- c.bessel
- _j0
- _j1
- _jn
- _y0
- _y1
- _yn
helpviewer_keywords:
- Bessel functions
- _j0 function
- _j1 function
- _jn function
- _y0 function
- _y1 function
- _yn function
ms.assetid: a21a8bf1-df9d-4ba0-a8c2-e7ef71921d96
ms.openlocfilehash: 682eaa99d0be1b959152ff94cc10a86aa68d988d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531866"
---
# <a name="bessel-functions-j0-j1-jn-y0-y1-yn"></a>Funkcje Bessela: _j0, _j1, _jn, _y0, _y1, _yn

Oblicza funkcję Bessela rodzaju pierwszej lub drugiej zamówień 0, 1 lub n. Funkcje Bessela są często używane w matematyce teorii elektromagnetycznych wave.

## <a name="syntax"></a>Składnia

```C
double _j0(
   double x
);
double _j1(
   double x
);
double _jn(
   int n,
   double x
);
double _y0(
   double x
);
double _y1(
   double x
);
double _yn(
   int n,
   double x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa.

*N*<br/>
Liczba całkowita kolejność Bessela funkcji.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca funkcja Bessela *x*. Jeśli *x* ma ujemną wartość w **_y0**, **_y1**, lub **_yn** funkcje, rutynowe zestawy **errno** do  **EDOM**, drukuje **_domeny** komunikat o błędzie **stderr**i zwraca **_HUGE_VAL**. Możesz zmodyfikować obsługi przy użyciu błędów **_matherr**.

## <a name="remarks"></a>Uwagi

**_J0**, **_j1**, i **_jn** procedury wróć Bessela funkcje pierwszy rodzaj: porządkuje 0, 1 i n, odpowiednio.

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|GRANICACH **QNAN**, **ZNAJDŹ**|**NIEPRAWIDŁOWY**|**_DOMENY**|

**_Y0**, **_y1**, i **_yn** procedury wróć Bessela funkcji drugiego rodzaju: porządkuje 0, 1 i n, odpowiednio.

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|GRANICACH **QNAN**, **ZNAJDŹ**|**NIEPRAWIDŁOWY**|**_DOMENY**|
|± 0|**ZERODIVIDE**|**_SING**|
|&#124;x&#124; < 0.0|**NIEPRAWIDŁOWY**|**_DOMENY**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_j0**, **_j1**, **_jn**, **_y0**, **_y1**, **_yn**|\<cmath > (C++), \<math.h > (C, C++)|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_bessel1.c
#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.387;
   int n = 3, c;

   printf( "Bessel functions for x = %f:\n", x );
   printf( "   Kind   Order  Function     Result\n\n" );
   printf( "   First  0      _j0( x )     %f\n", _j0( x ) );
   printf( "   First  1      _j1( x )     %f\n", _j1( x ) );
   for( c = 2; c < 5; c++ )
      printf( "   First  %d      _jn( %d, x )  %f\n", c, c, _jn( c, x ) );
   printf( "   Second 0      _y0( x )     %f\n", _y0( x ) );
   printf( "   Second 1      _y1( x )     %f\n", _y1( x ) );
   for( c = 2; c < 5; c++ )
      printf( "   Second %d      _yn( %d, x )  %f\n", c, c, _yn( c, x ) );
}
```

```Output
Bessel functions for x = 2.387000:
   Kind   Order  Function     Result

   First  0      _j0( x )     0.009288
   First  1      _j1( x )     0.522941
   First  2      _jn( 2, x )  0.428870
   First  3      _jn( 3, x )  0.195734
   First  4      _jn( 4, x )  0.063131
   Second 0      _y0( x )     0.511681
   Second 1      _y1( x )     0.094374
   Second 2      _yn( 2, x )  -0.432608
   Second 3      _yn( 3, x )  -0.819314
   Second 4      _yn( 4, x )  -1.626833
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[_matherr](matherr.md)<br/>
