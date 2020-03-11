---
title: Concurrency::precise_math, funkcje przestrzeni nazw
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::precise_math::acos
- amp_math/Concurrency::precise_math::acosh
- amp_math/Concurrency::precise_math::acoshf
- amp_math/Concurrency::precise_math::asinf
- amp_math/Concurrency::precise_math::asinh
- amp_math/Concurrency::precise_math::atan
- amp_math/Concurrency::precise_math::atan2
- amp_math/Concurrency::precise_math::atanf
- amp_math/Concurrency::precise_math::atanh
- amp_math/Concurrency::precise_math::cbrt
- amp_math/Concurrency::precise_math::cbrtf
- amp_math/Concurrency::precise_math::ceilf
- amp_math/Concurrency::precise_math::copysign
- amp_math/Concurrency::precise_math::cos
- amp_math/Concurrency::precise_math::cosf
- amp_math/Concurrency::precise_math::coshf
- amp_math/Concurrency::precise_math::cospi
- amp_math/Concurrency::precise_math::erf
- amp_math/Concurrency::precise_math::erfc
- amp_math/Concurrency::precise_math::erfcinv
- amp_math/Concurrency::precise_math::erfcinvf
- amp_math/Concurrency::precise_math::erfinv
- amp_math/Concurrency::precise_math::erfinvf
- amp_math/Concurrency::precise_math::exp10
- amp_math/Concurrency::precise_math::exp10f
- amp_math/Concurrency::precise_math::exp2f
- amp_math/Concurrency::precise_math::expf
- amp_math/Concurrency::precise_math::expm1f
- amp_math/Concurrency::precise_math::fabs
- amp_math/Concurrency::precise_math::floor
- amp_math/Concurrency::precise_math::fdim
- amp_math/Concurrency::precise_math::floorf
- amp_math/Concurrency::precise_math::fmaf
- amp_math/Concurrency::precise_math::fmaxf
- amp_math/Concurrency::precise_math::fmin
- amp_math/Concurrency::precise_math::fmod
- amp_math/Concurrency::precise_math::fmodf
- amp_math/Concurrency::precise_math::frexp
- amp_math/Concurrency::precise_math::frexpf
- amp_math/Concurrency::precise_math::hypotf
- amp_math/Concurrency::precise_math::ilogb
- amp_math/Concurrency::precise_math::isfinite
- amp_math/Concurrency::precise_math::isinf
- amp_math/Concurrency::precise_math::isnormal
- amp_math/Concurrency::precise_math::ldexp
- amp_math/Concurrency::precise_math::lgamma
- amp_math/Concurrency::precise_math::lgammaf
- amp_math/Concurrency::precise_math::log10
- amp_math/Concurrency::precise_math::log10f
- amp_math/Concurrency::precise_math::log1pf
- amp_math/Concurrency::precise_math::log2
- amp_math/Concurrency::precise_math::logb
- amp_math/Concurrency::precise_math::logbf
- amp_math/Concurrency::precise_math::modf
- amp_math/Concurrency::precise_math::modff
- amp_math/Concurrency::precise_math::nanf
- amp_math/Concurrency::precise_math::nearbyint
- amp_math/Concurrency::precise_math::nextafter
- amp_math/Concurrency::precise_math::nextafterf
- amp_math/Concurrency::precise_math::phif
- amp_math/Concurrency::precise_math::pow
- amp_math/Concurrency::precise_math::probit
- amp_math/Concurrency::precise_math::probitf
- amp_math/Concurrency::precise_math::rcbrtf
- amp_math/Concurrency::precise_math::remainder
- amp_math/Concurrency::precise_math::remquo
- amp_math/Concurrency::precise_math::remquof
- amp_math/Concurrency::precise_math::roundf
- amp_math/Concurrency::precise_math::rsqrt
- amp_math/Concurrency::precise_math::scalb
- amp_math/Concurrency::precise_math::scalbf
- amp_math/Concurrency::precise_math::scalbnf
- amp_math/Concurrency::precise_math::signbit
- amp_math/Concurrency::precise_math::sin
- amp_math/Concurrency::precise_math::sincos
- amp_math/Concurrency::precise_math::sinf
- amp_math/Concurrency::precise_math::sinh
- amp_math/Concurrency::precise_math::sinpi
- amp_math/Concurrency::precise_math::sinpif
- amp_math/Concurrency::precise_math::sqrtf
- amp_math/Concurrency::precise_math::tan
- amp_math/Concurrency::precise_math::tanh
- amp_math/Concurrency::precise_math::tanhf
- amp_math/Concurrency::precise_math::tanpif
- amp_math/Concurrency::precise_math::tgamma
- amp_math/Concurrency::precise_math::trunc
- amp_math/Concurrency::precise_math::truncf
ms.assetid: fae53ab4-d1c5-45bb-a6a0-a74258e9aea3
ms.openlocfilehash: 53ebaf8d9cc1bca53b1fe51464668d6df8e08424
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890697"
---
# <a name="concurrencyprecise_math-namespace-functions"></a>Concurrency::precise_math, funkcje przestrzeni nazw

||||
|-|-|-|
|[Acos](#acos)|[acosf —](#acosf)|[ACOSH —](#acosh)|
|[acoshf —](#acoshf)|[Asin](#asin)|[asinf —](#asinf)|
|[ASINH —](#asinh)|[asinhf —](#asinhf)|[atan](#atan)|
|[atan2](#atan2)|[atan2f —](#atan2f)|[atanf —](#atanf)|
|[ATANH —](#atanh)|[atanhf —](#atanhf)|[cbrt —](#cbrt)|
|[cbrtf —](#cbrtf)|[CEIL —](#ceil)|[ceilf —](#ceilf)|
|[copysign —](#copysign)|[copysignf —](#copysignf)|[cosinus](#cos)|
|[cosf —](#cosf)|[cosh —](#cosh)|[coshf —](#coshf)|
|[cospi —](#cospi)|[cospif —](#cospif)|[Funkcja](#erf)|
|[ERFC —](#erfc)|[erfcf —](#erfcf)|[erfcinv —](#erfcinv)|
|[erfcinvf —](#erfcinvf)|[erff —](#erff)|[erfinv —](#erfinv)|
|[erfinvf](#erfinvf)|[EXP](#exp)|[exp10 —](#exp10)|
|[exp10f —](#exp10f)|[exp2 —](#exp2)|[exp2f —](#exp2f)|
|[expf —](#expf)|[expm1 —](#expm1)|[expm1f —](#expm1f)|
|[fabs —](#fabs)|[fabsf —](#fabsf)|[wykładzin](#floor)|
|[fdim —](#fdim)|[fdimf —](#fdimf)||
|[floorf —](#floorf)|[FMA](#fma)|[fmaf —](#fmaf)|
[Fmax —](#fmax)|[fmaxf —](#fmaxf)||
|[fmin —](#fmin)|[fminf —](#fminf)|[FMOD —](#fmod)|
|[fmodf —](#fmodf)|[fpclassify](#fpclassify)|[frexp](#frexp)|
|[frexpf —](#frexpf)|[hypot —](#hypot)|[hypotf —](#hypotf)|
|[ilogb —](#ilogb)|[ilogbf —](#ilogbf)|[isFinite](#isfinite)|
|[isinf](#isinf)|[isNaN](#isnan)|[isnormal](#isnormal)|
|[ldexp](#ldexp)|[ldexpf —](#ldexpf)|[lgamma —](#lgamma)|
|[lgammaf —](#lgammaf)|[rejestrowane](#log)|[log10 —](#log10)|
|[log10f —](#log10f)|[log1p —](#log1p)|[log1pf —](#log1pf)|
|[log2 —](#log2)|[log2f —](#log2f)|[logb —](#logb)|
|[logbf —](#logbf)|[logf —](#logf)|[modf —](#modf)|
|[modff —](#modff)|[NaN](#nan)|[nanf —](#nanf)|
|[nearbyint —](#nearbyint)|[nearbyintf —](#nearbyintf)|[nextafter —](#nextafter)|
|[nextafterf —](#nextafterf)|[zdrowiu](#phi)|[phif](#phif)|
|[pow](#pow)|[powf —](#powf)|[probit](#probit)|
|[probitf](#probitf)|[rcbrt —](#rcbrt)|[rcbrtf —](#rcbrtf)|
|[pozostałej części](#remainder)|[remainderf —](#remainderf)|[remquo —](#remquo)|
|[remquof —](#remquof)|[Nit](#round)|[roundf —](#roundf)|
|[rsqrt —](#rsqrt)|[rsqrtf —](#rsqrtf)|[scalb —](#scalb)|
|[scalbf —](#scalbf)|[scalbn —](#scalbn)|[scalbnf —](#scalbnf)|
|[signbit](#signbit)|[signbitf —](#signbitf)|[sinus](#sin)|
|[SinCos —](#sincos)|[sincosf —](#sincosf)|[SINF —](#sinf)|
|[SINH](#sinh)|[sinhf —](#sinhf)|[sinpi —](#sinpi)|
|[sinpif —](#sinpif)|[sqrt](#sqrt)|[sqrtf —](#sqrtf)|
|[Tan](#tan)|[TANF —](#tanf)|[TANH —](#tanh)|
|[tanhf —](#tanhf)|[tanpi —](#tanpi)|[tanpif —](#tanpif)|
|[tgamma —](#tgamma)|[tgammaf —](#tgammaf)|[TRUNC —](#trunc)|
|[truncf —](#truncf)|

## <a name="acos"></a>Acos

Oblicza arcus cosinus argumentu

```cpp
inline float acos(float _X) restrict(amp);

inline double acos(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość arcus cosinus argumentu

## <a name="acosf"></a>acosf —

Oblicza arcus cosinus argumentu

```cpp
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość arcus cosinus argumentu

## <a name="acosh"></a>ACOSH —

Oblicza odwrotny cosinus hiperboliczny argumentu

```cpp
inline float acosh(float _X) restrict(amp);

inline double acosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotną wartość cosinusa hiperbolicznego argumentu.

## <a name="acoshf"></a>acoshf —

Oblicza odwrotny cosinus hiperboliczny argumentu

```cpp
inline float acoshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotną wartość cosinusa hiperbolicznego argumentu.

## <a name="asin"></a>Asin

Oblicza arcus sinus argumentu

```cpp
inline float asin(float _X) restrict(amp);

inline double asin(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość arcus sinus argumentu

## <a name="asinf"></a>asinf —

Oblicza arcus sinus argumentu

```cpp
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość arcus sinus argumentu

## <a name="asinh"></a>ASINH —

Oblicza odwrotny sinus hiperboliczny argumentu

```cpp
inline float asinh(float _X) restrict(amp);

inline double asinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotną wartość sinusa hiperbolicznego argumentu

## <a name="asinhf"></a>asinhf —

Oblicza odwrotny sinus hiperboliczny argumentu

```cpp
inline float asinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotną wartość sinusa hiperbolicznego argumentu

## <a name="atan"></a>atan

Oblicza arcus tangens argumentu

```cpp
inline float atan(float _X) restrict(amp);

inline double atan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość arcus tangens argumentu

## <a name="atan2"></a>atan2

Oblicza arcus tangens _Y/_X

```cpp
inline float atan2(
    float _Y,
    float _X) restrict(amp);

inline double atan2(
    double _Y,
    double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Y*<br/>
Wartość zmiennoprzecinkowa

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość arcus tangens _Y/_X

## <a name="atan2f"></a>atan2f —

Oblicza arcus tangens _Y/_X

```cpp
inline float atan2f(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Y*<br/>
Wartość zmiennoprzecinkowa

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość arcus tangens _Y/_X

## <a name="atanf"></a>atanf —

Oblicza arcus tangens argumentu

```cpp
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość arcus tangens argumentu

## <a name="atanh"></a>ATANH —

Oblicza odwrotny tangens hiperboliczny argumentu

```cpp
inline float atanh(float _X) restrict(amp);

inline double atanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotną wartość tangens hiperboliczny argumentu

## <a name="atanhf"></a>atanhf —

Oblicza odwrotny tangens hiperboliczny argumentu

```cpp
inline float atanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotną wartość tangens hiperboliczny argumentu

## <a name="cbrt"></a>cbrt —

Oblicza element główny modułu w rzeczywistym argumencie

```cpp
inline float cbrt(float _X) restrict(amp);

inline double cbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca element główny modułu w rzeczywistym argumencie

## <a name="cbrtf"></a>cbrtf —

Oblicza element główny modułu w rzeczywistym argumencie

```cpp
inline float cbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca element główny modułu w rzeczywistym argumencie

## <a name="ceil"></a>CEIL —

Oblicza górny limit argumentu

```cpp
inline float ceil(float _X) restrict(amp);

inline double ceil(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca górny limit argumentu

## <a name="ceilf"></a>ceilf —

Oblicza górny limit argumentu

```cpp
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca górny limit argumentu

## <a name="copysign"></a>copysign —

Tworzy wartość o wielkości _X i znaku _Y

```cpp
inline float copysign(
    float _X,
    float _Y) restrict(amp);

inline double copysign(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Y*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość o wielkości _X i znaku _Y

## <a name="copysignf"></a>copysignf —

Tworzy wartość o wielkości _X i znaku _Y

```cpp
inline float copysignf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Y*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość o wielkości _X i znaku _Y

## <a name="cos"></a>cosinus

Oblicza cosinus argumentu

```cpp
inline float cos(float _X) restrict(amp);

inline double cos(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość cosinusa argumentu

## <a name="cosf"></a>cosf —

Oblicza cosinus argumentu

```cpp
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość cosinusa argumentu

## <a name="cosh"></a>cosh —

Oblicza wartość cosinus hiperboliczny argumentu

```cpp
inline float cosh(float _X) restrict(amp);

inline double cosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość cosinus hiperboliczny argumentu

## <a name="coshf"></a>coshf —

Oblicza wartość cosinus hiperboliczny argumentu

```cpp
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość cosinus hiperboliczny argumentu

## <a name="cospi"></a>cospi —

Oblicza wartość cosinusa liczby pi \* _X

```cpp
inline float cospi(float _X) restrict(amp);

inline double cospi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość cosinusa liczby pi \* _X

## <a name="cospif"></a>cospif —

Oblicza wartość cosinusa liczby pi \* _X

```cpp
inline float cospif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość cosinusa liczby pi \* _X

## <a name="erf"></a>Funkcja

Oblicza funkcję błędu _X

```cpp
inline float erf(float _X) restrict(amp);

inline double erf(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję błędu _X

## <a name="erfc"></a>ERFC —

Oblicza komplementarną funkcję błędu _X

```cpp
inline float erfc(float _X) restrict(amp);

inline double erfc(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca uzupełniającą funkcję błędu _X

## <a name="erfcf"></a>erfcf —

Oblicza komplementarną funkcję błędu _X

```cpp
inline float erfcf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca uzupełniającą funkcję błędu _X

## <a name="erfcinv"></a>erfcinv —

Oblicza odwrotną komplementarną funkcję błędu _X

```cpp
inline float erfcinv(float _X) restrict(amp);

inline double erfcinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotną funkcję błędu komplementarnego _X

## <a name="erfcinvf"></a>erfcinvf —

Oblicza odwrotną komplementarną funkcję błędu _X

```cpp
inline float erfcinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotną funkcję błędu komplementarnego _X

## <a name="erff"></a>erff —

Oblicza funkcję błędu _X

```cpp
inline float erff(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję błędu _X

## <a name="erfinv"></a>erfinv —

Oblicza funkcję odwrotnego błędu _X

```cpp
inline float erfinv(float _X) restrict(amp);

inline double erfinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję odwrotnego błędu _X

## <a name="erfinvf"></a>erfinvf

Oblicza funkcję odwrotnego błędu _X

```cpp
inline float erfinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję odwrotnego błędu _X

## <a name="exp10"></a>exp10 —

Oblicza wartość logarytmu dziesiętnego dla argumentu

```cpp
inline float exp10(float _X) restrict(amp);

inline double exp10(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość liczbową z argumentu Base-10.

## <a name="exp10f"></a>exp10f —

Oblicza wartość logarytmu dziesiętnego dla argumentu

```cpp
inline float exp10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość liczbową z argumentu Base-10.

## <a name="expm1"></a>expm1 —

Oblicza wartość wykładniczą (podstawa e) argumentu, minus 1

```cpp
inline float expm1(float exponent) restrict(amp);

inline double expm1(double exponent) restrict(amp);
```

### <a name="parameters"></a>Parametry

*zapis*<br/>
Wykładniczy termin *n* wyrażenia matematycznego `e`<sup>n</sup>, gdzie `e` jest podstawą logarytmu naturalnego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość wykładniczą (podstawa e) argumentu, minus 1

## <a name="expm1f"></a>expm1f —

Oblicza wartość wykładniczą (podstawa e) argumentu, minus 1

```cpp
inline float expm1f(float exponent) restrict(amp);
```

### <a name="parameters"></a>Parametry

*zapis*<br/>
Wykładniczy termin *n* wyrażenia matematycznego `e`<sup>n</sup>, gdzie `e` jest podstawą logarytmu naturalnego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość wykładniczą (podstawa e) argumentu, minus 1

## <a name="exp"></a>EXP

Oblicza wykładniczą wartość argumentu

```cpp
inline float exp(float _X) restrict(amp);

inline double exp(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wykładniczą wartość argumentu

## <a name="expf"></a>expf —

Oblicza wykładniczą wartość argumentu

```cpp
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wykładniczą wartość argumentu

## <a name="exp2"></a>exp2 —

Oblicza wartość typu wykładniczego na podstawie 2 dla argumentu

```cpp
inline float exp2(float _X) restrict(amp);

inline double exp2(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość typu wykładniczego 2 dla argumentu

## <a name="exp2f"></a>exp2f —

Oblicza wartość typu wykładniczego na podstawie 2 dla argumentu

```cpp
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość typu wykładniczego 2 dla argumentu

## <a name="fabs"></a>fabs —

Zwraca wartość bezwzględną argumentu.

```cpp
inline float fabs(float _X) restrict(amp);

inline double fabs(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość bezwzględną argumentu.

## <a name="fabsf"></a>fabsf —

Zwraca wartość bezwzględną argumentu.

```cpp
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość bezwzględną argumentu.

## <a name="fdim"></a>fdim —

Oblicza dodatnią różnicę między argumentami.

```cpp
inline float fdim(
   float _X,
   float _Y
) restrict(amp);
inline double fdim(
   double _X,
   double _Y
) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa *_Y*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Różnica między _X i _Y, jeśli _X jest większa niż _Y; w przeciwnym razie + 0.

## <a name="fdimf"></a>fdimf —

Oblicza dodatnią różnicę między argumentami.

```cpp
inline float fdimf(
   float _X,
   float _Y
) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa *_Y*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Różnica między _X i _Y, jeśli _X jest większa niż _Y; w przeciwnym razie + 0.

## <a name="floor"></a>wykładzin

Oblicza piętro argumentu

```cpp
inline float floor(float _X) restrict(amp);

inline double floor(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca podłogę argumentu

## <a name="floorf"></a>floorf —

Oblicza piętro argumentu

```cpp
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca podłogę argumentu

## <a name="a-namefma-fma"></a><a name="fma"> FMA

Oblicza iloczyn pierwszego i drugiego określonego argumentu, a następnie dodaje trzeci określony argument do wyniku; całe obliczenie jest wykonywane jako pojedyncza operacja.

```cpp
inline float fma(
   float _X,
   float _Y,
   float _Z
) restrict(amp);

inline double fma(
   double _X,
   double _Y,
   double _Z
) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Pierwszy argument zmiennoprzecinkowy.
*_Y*<br/>
Drugi argument zmiennoprzecinkowy.
*_Z*<br/>
Trzeci argument zmiennoprzecinkowy.

### <a name="return-value"></a>Wartość zwracana

Wynik wyrażenia (_X \* _Y) + _Z. Całe obliczenie jest wykonywane jako pojedyncza operacja; oznacza to, że wyrażenia podrzędne są obliczane z dokładnością nieskończoną i zaokrąglany jest tylko wynik końcowy.

## <a name="fmaf"></a>fmaf —

Oblicza iloczyn pierwszego i drugiego określonego argumentu, a następnie dodaje trzeci określony argument do wyniku; całe obliczenie jest wykonywane jako pojedyncza operacja.

```cpp
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Pierwszy argument zmiennoprzecinkowy.
*_Y*<br/>
Drugi argument zmiennoprzecinkowy.
*_Z*<br/>
Trzeci argument zmiennoprzecinkowy.

### <a name="return-value"></a>Wartość zwracana

Wynik wyrażenia (_X \* _Y) + _Z. Całe obliczenie jest wykonywane jako pojedyncza operacja; oznacza to, że wyrażenia podrzędne są obliczane z dokładnością nieskończoną i zaokrąglany jest tylko wynik końcowy.

## <a name="fmax"></a>Fmax —

Określanie maksymalnej wartości liczbowej argumentów

```cpp
inline float fmax(
    float _X,
    float _Y) restrict(amp);

inline double fmax(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Y*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca maksymalną wartość liczbową argumentów

## <a name="fmaxf"></a>fmaxf —

Określanie maksymalnej wartości liczbowej argumentów

```cpp
inline float fmaxf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Y*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca maksymalną wartość liczbową argumentów

## <a name="fmin"></a>fmin —

Określ minimalną wartość liczbową argumentów

```cpp
inline float fmin(
    float _X,
    float _Y) restrict(amp);

inline double fmin(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Y*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwróć minimalną wartość liczbową argumentów

## <a name="fminf"></a>fminf —

Określ minimalną wartość liczbową argumentów

```cpp
inline float fminf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Y*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwróć minimalną wartość liczbową argumentów

## <a name="fmod"></a>Funkcja FMOD — (C++ amp)

Oblicza pozostałą część pierwszego określonego argumentu podzieloną przez drugi określony argument.

```cpp
inline float fmod(
    float _X,
    float _Y) restrict(amp);

inline double fmod(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Pierwszy argument zmiennoprzecinkowy.

*_Y*<br/>
Drugi argument zmiennoprzecinkowy.

### <a name="return-value"></a>Wartość zwracana

Pozostała część `_X` podzielona przez `_Y`; oznacza to, że wartość `_X` - `_Y`*n*, gdzie *n* jest liczbą całkowitą, tak że rozmiar `_X` - `_Y`*n* jest mniejszy niż rozmiar `_Y`.

## <a name="fmodf"></a>fmodf —

Oblicza pozostałą część pierwszego określonego argumentu podzieloną przez drugi określony argument.

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Pierwszy argument zmiennoprzecinkowy.

*_Y*<br/>
Drugi argument zmiennoprzecinkowy.

### <a name="return-value"></a>Wartość zwracana

Pozostała część `_X` podzielona przez `_Y`; oznacza to, że wartość `_X` - `_Y`*n*, gdzie *n* jest liczbą całkowitą, tak że rozmiar `_X` - `_Y`*n* jest mniejszy niż rozmiar `_Y`.

## <a name="fpclassify"></a>fpclassify —

Klasyfikuje wartość argumentu jako NaN, nieskończone, normalne, subnormalne, zero

```cpp
inline int fpclassify(float _X) restrict(amp);

inline int fpclassify(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość makra klasyfikacji liczbowej odpowiednie dla wartości argumentu.

## <a name="frexp"></a>frexp —

Pobiera mantysy i wykładnik _X

```cpp
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);

inline double frexp(
    double _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Exp*<br/>
Zwraca wykładnik całkowity _X w wartości zmiennoprzecinkowej

### <a name="return-value"></a>Wartość zwracana

Zwraca _X mantysy

## <a name="frexpf"></a>frexpf —

Pobiera mantysy i wykładnik _X

```cpp
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Exp*<br/>
Zwraca wykładnik całkowity _X w wartości zmiennoprzecinkowej

### <a name="return-value"></a>Wartość zwracana

Zwraca _X mantysy

## <a name="hypot"></a>hypot —

Oblicza pierwiastek kwadratowy sumy kwadratów _X i _Y

```cpp
inline float hypot(
    float _X,
    float _Y) restrict(amp);

inline double hypot(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Y*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca pierwiastek kwadratowy sumy kwadratów _X i _Y

## <a name="hypotf"></a>hypotf —

Oblicza pierwiastek kwadratowy sumy kwadratów _X i _Y

```cpp
inline float hypotf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Y*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca pierwiastek kwadratowy sumy kwadratów _X i _Y

## <a name="ilogb"></a>ilogb —

Wyodrębnij wykładnik _X jako podpisaną wartość int

```cpp
inline int ilogb(float _X) restrict(amp);

inline int ilogb(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wykładnik _X jako podpisaną wartość int

## <a name="ilogbf"></a>ilogbf —

Wyodrębnij wykładnik _X jako podpisaną wartość int

```cpp
inline int ilogbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wykładnik _X jako podpisaną wartość int

## <a name="isfinite"></a>isFinite

Określa, czy argument ma skończoną wartość

```cpp
inline int isfinite(float _X) restrict(amp);

inline int isfinite(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość różną od zera, jeśli i tylko wtedy, gdy argument ma skończoną wartość

## <a name="isinf"></a>isinf —

Określa, czy argument jest nieskończonością

```cpp
inline int isinf(float _X) restrict(amp);

inline int isinf(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość różną od zera, jeśli i tylko wtedy, gdy argument ma wartość nieskończoną.

## <a name="isnan"></a>isNaN

Określa, czy argument jest NaN

```cpp
inline int isnan(float _X) restrict(amp);

inline int isnan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość różną od zera, jeśli i tylko wtedy, gdy argument ma wartość NaN

## <a name="isnormal"></a>isnormal —

Określa, czy argument jest normalny

```cpp
inline int isnormal(float _X) restrict(amp);

inline int isnormal(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość różną od zera, jeśli i tylko wtedy, gdy argument ma wartość normalną.

## <a name="ldexp"></a>ldexp —

Oblicza liczbę rzeczywistą z określonego mantysy i wykładnika.

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);

inline double ldexp(
    double _X,
    double _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa, mantysy

*_Exp*<br/>
Wartość całkowita, wykładnik

### <a name="return-value"></a>Wartość zwracana

Zwraca _X \* 2 ^ _Exp

## <a name="ldexpf"></a>ldexpf —

Oblicza liczbę rzeczywistą z określonego mantysy i wykładnika.

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa, mantysy

*_Exp*<br/>
Wartość całkowita, wykładnik

### <a name="return-value"></a>Wartość zwracana

Zwraca _X \* 2 ^ _Exp

## <a name="lgamma"></a>lgamma —

Oblicza logarytm naturalny wartości bezwzględnej gamma argumentu

```cpp
inline float lgamma(
    float _X,
    _Out_ int* _Sign) restrict(amp);

inline double lgamma(
    double _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Sign*<br/>
Zwraca znak

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm naturalny wartości absolutnej argumentu

## <a name="lgammaf"></a>lgammaf —

Oblicza logarytm naturalny wartości bezwzględnej gamma argumentu

```cpp
inline float lgammaf(
    float _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Sign*<br/>
Zwraca znak

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm naturalny wartości absolutnej argumentu

## <a name="log"></a>rejestrowane

Oblicza logarytm dziesiętny argumentu

```cpp
inline float log(float _X) restrict(amp);

inline double log(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm dziesiętny argumentu

## <a name="log10"></a>log10 —

Oblicza logarytm dziesiętny argumentu

```cpp
inline float log10(float _X) restrict(amp);

inline double log10(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm dziesiętny argumentu

## <a name="log10f"></a>log10f —

Oblicza logarytm dziesiętny argumentu

```cpp
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm dziesiętny argumentu

## <a name="log1p"></a>log1p —

Oblicza logarytm dziesiętny wartości 1 i argumentu

```cpp
inline float log1p(float _X) restrict(amp);

inline double log1p(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość logarytmu podstawowego-e z 1 i argumentu

## <a name="log1pf"></a>log1pf —

Oblicza logarytm dziesiętny wartości 1 i argumentu

```cpp
inline float log1pf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość logarytmu podstawowego-e z 1 i argumentu

## <a name="log2"></a>log2 —

Oblicza logarytm dziesiętny argumentu

```cpp
inline float log2(float _X) restrict(amp);

inline double log2(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm dziesiętny argumentu

## <a name="log2f"></a>log2f —

Oblicza logarytm dziesiętny argumentu

```cpp
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm dziesiętny argumentu

## <a name="logb"></a>logb —

Wyodrębnienie wykładnika _X jako wartości całkowitej ze znakiem w formacie liczb zmiennoprzecinkowych

```cpp
inline float logb(float _X) restrict(amp);

inline double logb(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca podpisany wykładnik _X

## <a name="logbf"></a>logbf —

Wyodrębnienie wykładnika _X jako wartości całkowitej ze znakiem w formacie liczb zmiennoprzecinkowych

```cpp
inline float logbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca podpisany wykładnik _X

## <a name="logf"></a>logf —

Oblicza logarytm dziesiętny argumentu

```cpp
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm dziesiętny argumentu

## <a name="modf"></a>modf —

Dzieli określony argument na części ułamkowe i całkowite.

```cpp
inline float modf(
    float _X,
    _Out_ float* _Iptr) restrict(amp);

inline double modf(
    double _X,
    _Out_ double* _Iptr) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Iptr*<br/>
określoną Część całkowita `_X`, jako wartość zmiennoprzecinkowa.

### <a name="return-value"></a>Wartość zwracana

Podpisana część ułamkowa `_X`.

## <a name="modff"></a>modff —

Dzieli określony argument na części ułamkowe i całkowite.

```cpp
inline float modff(
    float _X,
    _Out_ float* _Iptr) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Iptr*<br/>
Część całkowita `_X`, jako wartość zmiennoprzecinkowa.

### <a name="return-value"></a>Wartość zwracana

Zwraca podpisaną część ułamkową `_X`.

## <a name="nan"></a>NaN

Zwraca cichy element NaN

```cpp
inline double nan(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca cichy NaN, jeśli jest dostępny, z zawartością wskazywaną w _X

## <a name="nanf"></a>nanf —

Zwraca cichy element NaN

```cpp
inline float nanf(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca cichy NaN, jeśli jest dostępny, z zawartością wskazywaną w _X

## <a name="nearbyint"></a>nearbyint —

Zaokrągla argument do wartości całkowitej w formacie zmiennoprzecinkowym przy użyciu bieżącego kierunku zaokrąglenia.

```cpp
inline float nearbyint(float _X) restrict(amp);

inline double nearbyint(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca zaokrągloną wartość całkowitą.

## <a name="nearbyintf"></a>nearbyintf —

Zaokrągla argument do wartości całkowitej w formacie zmiennoprzecinkowym przy użyciu bieżącego kierunku zaokrąglenia.

```cpp
inline float nearbyintf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca zaokrągloną wartość całkowitą.

## <a name="nextafter"></a>nextafter —

Określ następną reprezentację wartości w typie funkcji po _X w kierunku _Y

```cpp
inline float nextafter(
    float _X,
    float _Y) restrict(amp);

inline double nextafter(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Y*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca następną reprezentację wartości w typie funkcji po _X w kierunku _Y

## <a name="nextafterf"></a>nextafterf —

Określ następną reprezentację wartości w typie funkcji po _X w kierunku _Y

```cpp
inline float nextafterf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Y*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca następną reprezentację wartości w typie funkcji po _X w kierunku _Y

## <a name="phi"></a>zdrowiu

Zwraca funkcję rozkładu skumulowanego argumentu

```cpp
inline float phi(float _X) restrict(amp);

inline double phi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję rozkładu skumulowanego argumentu

## <a name="phif"></a>phif

Zwraca funkcję rozkładu skumulowanego argumentu

```cpp
inline float phif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję rozkładu skumulowanego argumentu

## <a name="pow"></a>pow

Oblicza _X podniesioną do potęgi _Y

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);

inline double pow(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa, podstawa

*_Y*<br/>
Wartość zmiennoprzecinkowa, wykładnik

### <a name="return-value"></a>Wartość zwracana

## <a name="powf"></a>powf —

Oblicza _X podniesioną do potęgi _Y

```cpp
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa, podstawa

*_Y*<br/>
Wartość zmiennoprzecinkowa, wykładnik

### <a name="return-value"></a>Wartość zwracana

## <a name="probit"></a>probit

Zwraca odwrotną funkcję rozkładu skumulowanego argumentu

```cpp
inline float probit(float _X) restrict(amp);

inline double probit(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotną funkcję rozkładu skumulowanego argumentu

## <a name="probitf"></a>probitf

Zwraca odwrotną funkcję rozkładu skumulowanego argumentu

```cpp
inline float probitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotną funkcję rozkładu skumulowanego argumentu

## <a name="rcbrt"></a>rcbrt —

Zwraca odwrotność elementu głównego modułu argumentu

```cpp
inline float rcbrt(float _X) restrict(amp);

inline double rcbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotność elementu głównego modułu argumentu

## <a name="rcbrtf"></a>rcbrtf —

Zwraca odwrotność elementu głównego modułu argumentu

```cpp
inline float rcbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotność elementu głównego modułu argumentu

## <a name="remainder"></a>pozostałej części

Oblicza resztę: _X REM _Y

```cpp
inline float remainder(
    float _X,
    float _Y) restrict(amp);

inline double remainder(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Y*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca _X REM _Y

## <a name="remainderf"></a>remainderf —

Oblicza resztę: _X REM _Y

```cpp
inline float remainderf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Y*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca _X REM _Y

## <a name="remquo"></a>remquo —

Oblicza pozostałą część pierwszego określonego argumentu podzieloną przez drugi określony argument. Oblicza także iloraz mantysę pierwszego określonego argumentu podzieloną przez mantysę drugiego określonego argumentu i zwraca iloraz przy użyciu lokalizacji określonej w trzecim argumencie.

```cpp
inline float remquo(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);

inline double remquo(
    double _X,
    double _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Pierwszy argument zmiennoprzecinkowy.

*_Y*<br/>
Drugi argument zmiennoprzecinkowy.

*_Quo*<br/>
określoną Adres liczby całkowitej, która jest używana do zwrócenia ilorazu ułamków częściowych `_X` podzielona przez ułamkowe bity `_Y`.

### <a name="return-value"></a>Wartość zwracana

Zwraca resztę `_X` podzieloną przez `_Y`.

## <a name="remquof"></a>remquof —

Oblicza pozostałą część pierwszego określonego argumentu podzieloną przez drugi określony argument. Oblicza także iloraz mantysę pierwszego określonego argumentu podzieloną przez mantysę drugiego określonego argumentu i zwraca iloraz przy użyciu lokalizacji określonej w trzecim argumencie.

```cpp
inline float remquof(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Pierwszy argument zmiennoprzecinkowy.

*_Y*<br/>
Drugi argument zmiennoprzecinkowy.

*_Quo*<br/>
określoną Adres liczby całkowitej, która jest używana do zwrócenia ilorazu ułamków częściowych `_X` podzielona przez ułamkowe bity `_Y`.

### <a name="return-value"></a>Wartość zwracana

Zwraca resztę `_X` podzieloną przez `_Y`.

## <a name="round"></a>Nit

Zaokrągla _X do najbliższej liczby całkowitej

```cpp
inline float round(float _X) restrict(amp);

inline double round(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca najbliższą liczbę całkowitą z _X

## <a name="roundf"></a>roundf —

Zaokrągla _X do najbliższej liczby całkowitej

```cpp
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca najbliższą liczbę całkowitą z _X

## <a name="rsqrt"></a>rsqrt —

Zwraca odwrotność korzenia kwadratowego argumentu

```cpp
inline float rsqrt(float _X) restrict(amp);

inline double rsqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotność korzenia kwadratowego argumentu

## <a name="rsqrtf"></a>rsqrtf —

Zwraca odwrotność korzenia kwadratowego argumentu

```cpp
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotność korzenia kwadratowego argumentu

## <a name="scalb"></a>scalb —

Mnoży _X przez FLT_RADIX do _Y potęgi

```cpp
inline float scalb(
    float _X,
    float _Y) restrict(amp);

inline double scalb(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Y*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca \* _X (FLT_RADIX ^ _Y)

## <a name="scalbf"></a>scalbf —

Mnoży _X przez FLT_RADIX do _Y potęgi

```cpp
inline float scalbf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Y*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca \* _X (FLT_RADIX ^ _Y)

## <a name="scalbn"></a>scalbn —

Mnoży _X przez FLT_RADIX do _Y potęgi

```cpp
inline float scalbn(
    float _X,
    int _Y) restrict(amp);

inline double scalbn(
    double _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Y*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca \* _X (FLT_RADIX ^ _Y)

## <a name="scalbnf"></a>scalbnf —

Mnoży _X przez FLT_RADIX do _Y potęgi

```cpp
inline float scalbnf(
    float _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Y*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca \* _X (FLT_RADIX ^ _Y)

## <a name="signbit"></a>signbit —

Określa, czy znak _X jest ujemny

```cpp
inline int signbit(float _X) restrict(amp);

inline int signbit(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość różną od zera, jeśli i tylko wtedy, gdy znak _X jest ujemny

## <a name="signbitf"></a>signbitf —

Określa, czy znak _X jest ujemny

```cpp
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość różną od zera, jeśli i tylko wtedy, gdy znak _X jest ujemny

## <a name="sin"></a>sinus

Oblicza wartość sinusa argumentu

```cpp
inline float sin(float _X) restrict(amp);

inline double sin(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość sinusa argumentu

## <a name="sinf"></a>SINF —

Oblicza wartość sinusa argumentu

```cpp
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość sinusa argumentu

## <a name="sincos"></a>SinCos —

Oblicza sinus i wartość cosinusa _X

```cpp
inline void sincos(
    float _X,
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);

inline void sincos(
    double _X,
    _Out_ double* _S,
    _Out_ double* _C) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_S*<br/>
Zwraca wartość sinusa _X

*_C*<br/>
Zwraca wartość cosinusa _X

## <a name="sincosf"></a>sincosf —

Oblicza sinus i wartość cosinusa _X

```cpp
inline void sincosf(
    float _X,
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_S*<br/>
Zwraca wartość sinusa _X

*_C*<br/>
Zwraca wartość cosinusa _X

## <a name="sinh"></a>SINH

Oblicza wartość sinus hiperboliczny argumentu

```cpp
inline float sinh(float _X) restrict(amp);

inline double sinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość sinus hiperboliczny argumentu

## <a name="sinhf"></a>sinhf —

Oblicza wartość sinus hiperboliczny argumentu

```cpp
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość sinus hiperboliczny argumentu

## <a name="sinpi"></a>sinpi —

Oblicza wartość sinusa liczby pi \* _X

```cpp
inline float sinpi(float _X) restrict(amp);

inline double sinpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość sinusa liczby pi \* _X

## <a name="sinpif"></a>sinpif —

Oblicza wartość sinusa liczby pi \* _X

```cpp
inline float sinpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość sinusa liczby pi \* _X

## <a name="sqrt"></a>sqrt

Oblicza korzeń Squre argumentu

```cpp
inline float sqrt(float _X) restrict(amp);

inline double sqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca korzeń Squre argumentu

## <a name="sqrtf"></a>sqrtf —

Oblicza korzeń Squre argumentu

```cpp
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca korzeń Squre argumentu

## <a name="tan"></a>Tan

Oblicza wartość tangensa argumentu

```cpp
inline float tan(float _X) restrict(amp);

inline double tan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość tangensa argumentu

## <a name="tanf"></a>TANF —

Oblicza wartość tangensa argumentu

```cpp
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość tangensa argumentu

## <a name="tanh"></a>TANH —

Oblicza wartość tangensa hiperbolicznego argumentu

```cpp
inline float tanh(float _X) restrict(amp);

inline double tanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość tangensa hiperbolicznego argumentu

## <a name="tanhf"></a>tanhf —

Oblicza wartość tangensa hiperbolicznego argumentu

```cpp
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość tangensa hiperbolicznego argumentu

## <a name="tanpi"></a>tanpi —

Oblicza wartość tangens liczby pi \* _X

```cpp
inline float tanpi(float _X) restrict(amp);

inline double tanpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość tangens liczby pi \* _X

## <a name="tanpif"></a>tanpif —

Oblicza wartość tangens liczby pi \* _X

```cpp
inline float tanpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość tangens liczby pi \* _X

## <a name="tgamma"></a>tgamma —

Oblicza funkcję gamma elementu _X

```cpp
inline float tgamma(float _X) restrict(amp);

inline double tgamma(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wynik funkcji gamma elementu _X

## <a name="tgammaf"></a>tgammaf —

Oblicza funkcję gamma elementu _X

```cpp
inline float tgammaf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wynik funkcji gamma elementu _X

## <a name="trunc"></a>TRUNC —

Obcina argument do składnika liczby całkowitej

```cpp
inline float trunc(float _X) restrict(amp);

inline double trunc(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca składnik całkowity argumentu

## <a name="truncf"></a>truncf —

Obcina argument do składnika liczby całkowitej

```cpp
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca składnik całkowity argumentu

## <a name="see-also"></a>Zobacz także

[Concurrency::precise_math, przestrzeń nazw](concurrency-precise-math-namespace.md)
