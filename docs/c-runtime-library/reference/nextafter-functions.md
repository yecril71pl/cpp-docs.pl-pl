---
title: nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c68d039ff1318ea082d409078a55c8d337a48de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="nextafter-nextafterf-nextafterl-nextafter-nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl

Zwraca następnej można przedstawić wartości zmiennoprzecinkowych.

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
Wartość zmiennoprzecinkowa, aby uruchomić z.

*y*<br/>
Wartość zmiennoprzecinkowa, aby przejść do.

## <a name="return-value"></a>Wartość zwracana

Zwraca następnej można przedstawić wartości zmiennoprzecinkowych typu zwracanego po *x* w kierunku *y*. Jeśli *x* i *y* są takie same, funkcja zwraca *y*konwersji na zwracany typ nie wyjątek wyzwolone. Jeśli *x* nie jest równa *y*, a wynik jest nieznormalizowany lub zero, **FE_UNDERFLOW** i **FE_INEXACT** stanów wyjątków dotyczących liczb zmiennoprzecinkowych są skonfigurowane, i poprawny wynik zostanie zwrócony. Jeśli dowolny *x* lub *y* jest NAN, a następnie wartość zwracana jest jednym z wejściowej wartości NaN. Jeśli *x* jest jednak ograniczona i wynik jest nieskończone lub nie można przedstawić w typie, poprawnie podpisane infinity lub NAN jest zwracany, **FE_OVERFLOW** i **FE_INEXACT** Stany zmiennoprzecinkowych wyjątków są skonfigurowane, i **errno** ustawiono **erange —**.

## <a name="remarks"></a>Uwagi

**Nextafter —** i **nexttoward** rodziny funkcji są równoważne, z wyjątkiem typu parametru *y*. Jeśli *x* i *y* są takie same, jest zwracana wartość *y* przekonwertować na typ zwracany.

Ponieważ C++ pozwala przeciążeniu, Jeśli dołączysz \<cmath > można wywoływać przeciążenia **nextafter —** i **nexttoward** zwracające **float** i **długo** **podwójne** typów. W programie C **nextafter —** i **nexttoward** zawsze zwraca **podwójne**.

**_Nextafter —** i **_nextafterf** funkcje są określone firmy Microsoft. **_Nextafterf** funkcja jest dostępna tylko podczas kompilowania dla x64.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymaganego nagłówka (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter —**, **nextafterf —**, **nextafterl**, **_nextafterf**, **nexttoward**, **nexttowardf** , **nexttowardl**|\<math.h>|\<Math.h > lub \<cmath >|
|**_nextafter**|\<float.h>|\<float.h — > lub \<cfloat — >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
