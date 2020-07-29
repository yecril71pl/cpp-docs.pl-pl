---
title: nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl
ms.date: 4/2/2020
api_name:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
- _o__nextafter
- _o_nextafter
- _o_nextafterf
- _o_nextafterl
- _o_nexttoward
- _o_nexttowardf
- _o_nexttowardl
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
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 6122fd8921bdb413c4b24128b2428a70ccda0892
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213518"
---
# <a name="nextafter-nextafterf-nextafterl-_nextafter-_nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl

Zwraca następną reprezentację wartości zmiennoprzecinkowej.

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
Wartość zmiennoprzecinkowa do rozpoczęcia.

*t*<br/>
Wartość zmiennoprzecinkowa do osiągnięcia.

## <a name="return-value"></a>Wartość zwracana

Zwraca następną reprezentację wartości zmiennoprzecinkowej zwracanego typu po *x* w kierunku wartości *y*. Jeśli *x* i *y* są równe, funkcja zwraca *y*, przekonwertowane na typ zwracany, bez wyzwolonego wyjątku. Jeśli *x* nie jest równa *y*, a wynik jest nienormalny lub równy zero, ustawiana jest **FE_UNDERFLOW** i **FE_INEXACT** Stany wyjątków zmiennoprzecinkowych i zwracany jest prawidłowy wynik. Jeśli parametr *x* lub *y* jest NaN, wartość zwracana jest jednym z NANs danych wejściowych. Jeśli wartość *x* jest skończona, a wynik jest nieskończony lub nie można go zaprezentować w typie, zostanie zwrócona prawidłowo podpisana nieskończoność lub NAN, **FE_OVERFLOW** i **FE_INEXACT** Stany wyjątków zmiennoprzecinkowych są ustawione, a **errno** jest ustawiony na **ERANGE**.

## <a name="remarks"></a>Uwagi

Rodziny funkcji **nextafter —** i **nexttoward** są równoważne, z wyjątkiem typu parametru *y*. Jeśli *x* i *y* są równe, zwrócona wartość to *y* konwertowana na typ zwracany.

Ponieważ C++ pozwala na Przeciążenie, w przypadku dołączenia można \<cmath> wywoływać przeciążenia **nextafter —** i **nexttoward** , które zwracają **`float`** i **`long double`** typy. W programie C **nextafter —** i **nexttoward** zawsze zwracają **`double`** .

**_Nextafter** i **_nextafterf** funkcje są specyficzne dla firmy Microsoft. Funkcja **_nextafterf** jest dostępna tylko w przypadku kompilowania dla architektury x64.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter —**, **nextafterf —**, **nextafterl**, **_nextafterf**, **nexttoward**, **nexttowardf**, **nexttowardl**|\<math.h>|\<math.h> lub \<cmath>|
|**_nextafter**|\<float.h>|\<float.h> lub \<cfloat>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
