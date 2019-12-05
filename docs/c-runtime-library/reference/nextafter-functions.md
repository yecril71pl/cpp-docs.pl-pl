---
title: nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl
ms.date: 04/05/2018
api_name:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
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
ms.openlocfilehash: c6b100fb24d879a16780650d8a374ec26f28c048
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857726"
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

*y*<br/>
Wartość zmiennoprzecinkowa do osiągnięcia.

## <a name="return-value"></a>Wartość zwrócona

Zwraca następną reprezentację wartości zmiennoprzecinkowej zwracanego typu po *x* w kierunku wartości *y*. Jeśli *x* i *y* są równe, funkcja zwraca *y*, przekonwertowane na typ zwracany, bez wyzwolonego wyjątku. Jeśli *x* nie jest równa *y*, a wynik jest nienormalny lub równy zero, ustawiana jest **FE_UNDERFLOW** i **FE_INEXACT** Stany wyjątków zmiennoprzecinkowych i zwracany jest prawidłowy wynik. Jeśli parametr *x* lub *y* jest NaN, wartość zwracana jest jednym z NANs danych wejściowych. Jeśli wartość *x* jest skończona, a wynik jest nieskończony lub nie można go zaprezentować w typie, zostanie zwrócona prawidłowo podpisana nieskończoność lub NAN, **FE_OVERFLOW** i **FE_INEXACT** Stany wyjątków zmiennoprzecinkowych są ustawione, a **errno** jest ustawiony na **ERANGE**.

## <a name="remarks"></a>Uwagi

Rodziny funkcji **nextafter —** i **nexttoward** są równoważne, z wyjątkiem typu parametru *y*. Jeśli *x* i *y* są równe, zwrócona wartość to *y* konwertowana na typ zwracany.

Ponieważ C++ umożliwia Przeciążenie, w przypadku uwzględnienia \<cmath > można wywoływać przeciążenia **nextafter —** i **nexttoward** , które zwracają **zmiennoprzecinkowe** i **długie** **podwójne** typy. W programie w języku C **nextafter —** i **nexttoward** zawsze zwracają wartość **Double**.

**_Nextafter** i **_nextafterf** funkcje są specyficzne dla firmy Microsoft. Funkcja **_nextafterf** jest dostępna tylko w przypadku kompilowania dla architektury x64.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter —** , **nextafterf —** , **nextafterl**, **_nextafterf**, **nexttoward**, **nexttowardf**, **nexttowardl**|\<math.h>|\<Math. h > lub \<cmath >|
|**_nextafter**|\<float.h>|\<float. h > lub \<cfloat >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
