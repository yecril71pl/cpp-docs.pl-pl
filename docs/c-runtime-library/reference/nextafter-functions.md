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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 7b1416147ed000dd3dd9a13bd52e41a474a8e9d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338564"
---
# <a name="nextafter-nextafterf-nextafterl-_nextafter-_nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl

Zwraca następną reprezentowalną wartość zmiennoprzecinkową.

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

*X*<br/>
Wartość zmiennoprzecinkowa, od aby rozpocząć.

*Y*<br/>
Wartość zmiennoprzecinkowa, do w kierunku.

## <a name="return-value"></a>Wartość zwracana

Zwraca następną reprezentowalną wartość zmiennoprzecinkową typu zwracanego po *x* w kierunku *y*. Jeśli *x* i *y* są równe, funkcja zwraca *y*, przekonwertowane na typ zwracany, bez wyjątku wyzwalane. Jeśli *x* nie jest równa *y*, a wynik jest denormal lub zero, **FE_UNDERFLOW** i **FE_INEXACT** stanów wyjątków zmiennoprzecinkowych są ustawiane i zwracany jest poprawny wynik. Jeśli *x* lub *y* jest siecią NAN, wartość zwracana jest jedną z wejściowych sieci NAN. Jeśli *x* jest skończony, a wynik jest nieskończony lub nie można go przedstawić w typie, zwracany jest poprawnie podpisana nieskończoność lub numer NAN, ustawiono **FE_OVERFLOW** i **FE_INEXACT** stanów wyjątków zmiennoprzecinkowych, a **errno** jest ustawione na **ERANGE**.

## <a name="remarks"></a>Uwagi

Rodziny funkcji **nextafter** i **next do są** równoważne, z wyjątkiem typu parametru *y*. Jeśli *x* i *y* są równe, zwracana wartość *jest* konwertowana na typ zwracany.

Ponieważ C++ umożliwia przeciążenie, \<jeśli dodasz cmath> można wywołać przeciążenia **nextafter** i **nexttoward,** że powrót **float** i **długie** **podwójne** typy. W programie C, **nextafter** i **nexttoward** zawsze **zwracaj podwójnie**.

Funkcje **_nextafter** i **_nextafterf** są specyficzne dla firmy Microsoft. Funkcja **_nextafterf** jest dostępna tylko podczas kompilowania dla x64.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter**, **nextafterf**, **nextafterl**, **_nextafterf**, **nexttoward**, **nexttowardf**, **nexttowardl**|\<> math.h|\<>> lub \<cmath>|
|**_nextafter**|\<> float.h|\<> float.h lub \<cfloat>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
