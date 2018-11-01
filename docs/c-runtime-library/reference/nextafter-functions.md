---
title: nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl
ms.date: 04/05/2018
apiname:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
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
- nextafter
- _nextafter
- nextafterf
- nextafterl
- _nextafterf
- math/nextafter
- math/nextafterf
- math/nextafterl
- nexttoward
- nexttowardf
- nexttowardl
- math/nexttoward
- math/nexttowardf
- math/nexttowardl
helpviewer_keywords:
- _nextafter function
- nextafter function
- _nextafterf function
- nextafterf function
- nextafterl function
- nexttoward function
- nexttowardf function
- nexttowardl function
ms.assetid: 9785bfb9-de53-4bd0-9637-f05fa0c1f6ab
ms.openlocfilehash: 0e0a60dc9f7c068d8c18c10f3c6b819b9e06d3b7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444867"
---
# <a name="nextafter-nextafterf-nextafterl-nextafter-nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl

Zwraca następną wartość zmiennoprzecinkową.

## <a name="syntax"></a>Składnia

```C
double nextafter( double x, double y );
float nextafterf( float x, float y );
long double nextafterl( long double x, long double y );

double _nextafter( double x, double y );
float _nextafterf( float x, float y ); /* x64 only */

double nexttoward( double x, long double y );
float nexttowardf( float x, long double y );
long double nexttowardl( long double x, long double y );
```

```cpp
float nextafter( float x, float y ); /* C++ only, requires <cmath> */
long double nextafter( long double x, long double y ); /* C++ only, requires <cmath> */

float nexttoward( float x, long double y ); /* C++ only, requires <cmath> */
long double nexttoward( long double x, long double y ); /* C++ only, requires <cmath> */
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa, aby rozpocząć od.

*y*<br/>
Wartość zmiennoprzecinkowa, aby przejść do.

## <a name="return-value"></a>Wartość zwracana

Zwraca następną wartość zmiennoprzecinkowa typu zwracanego po *x* w kierunku *y*. Jeśli *x* i *y* są takie same, funkcja zwraca *y*, przekonwertowane na typ zwracany, bez wyjątku wyzwolone. Jeśli *x* nie jest równa *y*, a wynik jest denormal lub zero, **FE_UNDERFLOW** i **FE_INEXACT** stany wyjątków dotyczących liczb zmiennoprzecinkowych są skonfigurowane, i zostanie zwrócony odpowiedni wynik. Jeśli *x* lub *y* jest NAN, wówczas wartość zwracana jest jednym z danych wejściowych NANs. Jeśli *x* jest jednak ograniczona i wynikiem jest nieskończona lub nie stałego w typie, poprawnie podpisane infinity lub NAN jest zwracany, **FE_OVERFLOW** i **FE_INEXACT** wyjątek zmiennoprzecinkowy, którego stany są skonfigurowane, i **errno** ustawiono **ERANGE**.

## <a name="remarks"></a>Uwagi

**Nextafter —** i **nexttoward** rodziny funkcji są równoważne, z wyjątkiem typ parametru *y*. Jeśli *x* i *y* są równe, wartość zwracana jest *y* konwertowane na typ zwracany.

Ponieważ C++ pozwala na przeciążenie, Jeśli dołączysz \<cmath > można wywoływać przeciążenia **nextafter —** i **nexttoward** zwracające **float** i **długie** **double** typów. W programie C **nextafter —** i **nexttoward** zawsze zwracają **double**.

**_Nextafter —** i **_nextafterf** funkcje są specyficzne dla firmy Microsoft. **_Nextafterf** funkcja jest dostępna tylko podczas kompilowania x64.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter —**, **nextafterf —**, **nextafterl**, **_nextafterf**, **nexttoward**, **nexttowardf** , **nexttowardl**|\<math.h>|\<Math.h > lub \<cmath >|
|**_nextafter**|\<float.h>|\<float.h > lub \<cfloat — >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
