---
title: CONCURRENCY::precise_math, funkcje przestrzeni nazw
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
ms.openlocfilehash: ccbb9bdda3132626a6bf76161104c9716a9b5c89
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469358"
---
# <a name="concurrencyprecisemath-namespace-functions"></a>CONCURRENCY::precise_math, funkcje przestrzeni nazw

||||
|-|-|-|
|[ACOS](#acos)|[acosf](#acosf)|[ACOSH —](#acosh)|
|[acoshf](#acoshf)|[ASIN](#asin)|[asinf —](#asinf)|
|[ASINH —](#asinh)|[asinhf](#asinhf)|[atan](#atan)|
|[atan2](#atan2)|[atan2f](#atan2f)|[atanf](#atanf)|
|[atanh](#atanh)|[atanhf](#atanhf)|[cbrt](#cbrt)|
|[cbrtf](#cbrtf)|[Ceil —](#ceil)|[ceilf](#ceilf)|
|[copysign —](#copysign)|[copysignf](#copysignf)|[COS](#cos)|
|[cosf](#cosf)|[COSH](#cosh)|[coshf](#coshf)|
|[cospi —](#cospi)|[cospif](#cospif)|[erf](#erf)|
|[ERFC —](#erfc)|[erfcf](#erfcf)|[erfcinv —](#erfcinv)|
|[erfcinvf](#erfcinvf)|[erff](#erff)|[erfinv —](#erfinv)|
|[erfinvf](#erfinvf)|[EXP](#exp)|[exp10](#exp10)|
|[exp10f](#exp10f)|[exp2](#exp2)|[exp2f](#exp2f)|
|[expf](#expf)|[expm1 —](#expm1)|[expm1f —](#expm1f)|
|[fabs —](#fabs)|[fabsf —](#fabsf)|[FLOOR](#floor)|
|[fdim](#fdim)|[fdimf](#fdimf)||
|[floorf](#floorf)|[fma](#fma)|[fmaf](#fmaf)|
[fmax](#fmax)|[fmaxf](#fmaxf)||
|[fmin](#fmin)|[fminf —](#fminf)|[Fmod —](#fmod)|
|[fmodf](#fmodf)|[fpclassify](#fpclassify)|[frexp](#frexp)|
|[frexpf](#frexpf)|[hypot](#hypot)|[hypotf](#hypotf)|
|[ilogb](#ilogb)|[ilogbf](#ilogbf)|[isfinite](#isfinite)|
|[isinf —](#isinf)|[isNaN —](#isnan)|[isnormal —](#isnormal)|
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[lgamma](#lgamma)|
|[lgammaf](#lgammaf)|[log](#log)|[log10](#log10)|
|[log10f](#log10f)|[log1p](#log1p)|[log1pf](#log1pf)|
|[log2](#log2)|[log2f](#log2f)|[logb](#logb)|
|[logbf](#logbf)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[nan](#nan)|[nanf](#nanf)|
|[nearbyint](#nearbyint)|[nearbyintf](#nearbyintf)|[nextafter](#nextafter)|
|[nextafterf](#nextafterf)|[Phi](#phi)|[phif](#phif)|
|[Pow](#pow)|[powf](#powf)|[probit —](#probit)|
|[probitf —](#probitf)|[rcbrt](#rcbrt)|[rcbrtf](#rcbrtf)|
|[Pozostała](#remainder)|[remainderf](#remainderf)|[remquo](#remquo)|
|[remquof](#remquof)|[ROUND](#round)|[roundf](#roundf)|
|[rsqrt](#rsqrt)|[rsqrtf](#rsqrtf)|[scalb](#scalb)|
|[scalbf](#scalbf)|[scalbn](#scalbn)|[scalbnf](#scalbnf)|
|[signbit](#signbit)|[signbitf](#signbitf)|[SIN](#sin)|
|[sincos —](#sincos)|[sincosf](#sincosf)|[sinf](#sinf)|
|[SINH](#sinh)|[sinhf](#sinhf)|[sinpi —](#sinpi)|
|[sinpif](#sinpif)|[sqrt](#sqrt)|[sqrtf](#sqrtf)|
|[tan](#tan)|[tanf —](#tanf)|[TANH](#tanh)|
|[tanhf](#tanhf)|[tanpi —](#tanpi)|[tanpif —](#tanpif)|
|[tgamma](#tgamma)|[tgammaf](#tgammaf)|[TRUNC —](#trunc)|
|[truncf](#truncf)|

##  <a name="acos"></a>  ACOS

Oblicza arcus cosinus argumentu

```
inline float acos(float _X) restrict(amp);

inline double acos(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość cosinus argumentu

##  <a name="acosf"></a>  acosf —

Oblicza arcus cosinus argumentu

```
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość cosinus argumentu

##  <a name="acosh"></a>  ACOSH —

Oblicza arcus cosinus hiperboliczny argumentu

```
inline float acosh(float _X) restrict(amp);

inline double acosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca cosinus hiperboliczny wartość argumentu

##  <a name="acoshf"></a>  acoshf —

Oblicza arcus cosinus hiperboliczny argumentu

```
inline float acoshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca cosinus hiperboliczny wartość argumentu

##  <a name="asin"></a>  ASIN

Oblicza arcus sinus argumentu

```
inline float asin(float _X) restrict(amp);

inline double asin(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość arcus sinus argumentu

##  <a name="asinf"></a>  asinf —

Oblicza arcus sinus argumentu

```
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość arcus sinus argumentu

##  <a name="asinh"></a>  ASINH —

Oblicza arcus sinus hiperboliczny argumentu

```
inline float asinh(float _X) restrict(amp);

inline double asinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca sinus hiperboliczny wartość argumentu

##  <a name="asinhf"></a>  asinhf —

Oblicza arcus sinus hiperboliczny argumentu

```
inline float asinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca sinus hiperboliczny wartość argumentu

##  <a name="atan"></a>  ATAN

Oblicza arcus tangens argumentu

```
inline float atan(float _X) restrict(amp);

inline double atan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość arcus tangens argumentu

##  <a name="atan2"></a>  funkcja ATAN2

Oblicza arcus tangens dla _Y/_X

```
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

Zwraca wartość arcus tangens dla _Y/_X

##  <a name="atan2f"></a>  atan2f —

Oblicza arcus tangens dla _Y/_X

```
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

Zwraca wartość arcus tangens dla _Y/_X

##  <a name="atanf"></a>  atanf —

Oblicza arcus tangens argumentu

```
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość arcus tangens argumentu

##  <a name="atanh"></a>  ATANH —

Oblicza arcus tangens hiperboliczny argumentu

```
inline float atanh(float _X) restrict(amp);

inline double atanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotność wartość funkcji tangens hiperboliczny dla argumentu

##  <a name="atanhf"></a>  atanhf —

Oblicza arcus tangens hiperboliczny argumentu

```
inline float atanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotność wartość funkcji tangens hiperboliczny dla argumentu

##  <a name="cbrt"></a>  cbrt —

Oblicza rzeczywistych kwadratowy modułu argumentu

```
inline float cbrt(float _X) restrict(amp);

inline double cbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca pierwiastek modułu rzeczywistego argumentu

##  <a name="cbrtf"></a>  cbrtf —

Oblicza rzeczywistych kwadratowy modułu argumentu

```
inline float cbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca pierwiastek modułu rzeczywistego argumentu

##  <a name="ceil"></a>  Ceil —

Oblicza Zaokrąglenie w górę argumentu

```
inline float ceil(float _X) restrict(amp);

inline double ceil(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca limit argumentu

##  <a name="ceilf"></a>  ceilf —

Oblicza Zaokrąglenie w górę argumentu

```
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca limit argumentu

##  <a name="copysign"></a>  copysign —

Tworzy wartość o wielkości _X i _Y znak

```
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

Zwraca wartość o wielkości _X i _Y znak

##  <a name="copysignf"></a>  copysignf —

Tworzy wartość o wielkości _X i _Y znak

```
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

Zwraca wartość o wielkości _X i _Y znak

##  <a name="cos"></a>  COS

Oblicza cosinus argumentu

```
inline float cos(float _X) restrict(amp);

inline double cos(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji cosinus argumentu

##  <a name="cosf"></a>  cosf —

Oblicza cosinus argumentu

```
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji cosinus argumentu

##  <a name="cosh"></a>  COSH

Oblicza wartość funkcji cosinus hiperboliczny dla argumentu

```
inline float cosh(float _X) restrict(amp);

inline double cosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji cosinus hiperboliczny dla argumentu

##  <a name="coshf"></a>  coshf —

Oblicza wartość funkcji cosinus hiperboliczny dla argumentu

```
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji cosinus hiperboliczny dla argumentu

##  <a name="cospi"></a>  cospi —

Oblicza wartość funkcji cosinus liczby pi \* _X

```
inline float cospi(float _X) restrict(amp);

inline double cospi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji cosinus liczby pi \* _X

##  <a name="cospif"></a>  cospif —

Oblicza wartość funkcji cosinus liczby pi \* _X

```
inline float cospif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji cosinus liczby pi \* _X

##  <a name="erf"></a>  ERF —

Oblicza funkcję błędu _X

```
inline float erf(float _X) restrict(amp);

inline double erf(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji błędu _x

##  <a name="erfc"></a>  ERFC —

Oblicza komplementarną funkcję błędu _x

```
inline float erfc(float _X) restrict(amp);

inline double erfc(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca komplementarną funkcję błędu _x

##  <a name="erfcf"></a>  erfcf —

Oblicza komplementarną funkcję błędu _x

```
inline float erfcf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca komplementarną funkcję błędu _x

##  <a name="erfcinv"></a>  erfcinv —

Oblicza odwrotność komplementarną funkcję błędu _x

```
inline float erfcinv(float _X) restrict(amp);

inline double erfcinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotność komplementarną funkcję błędu _x

##  <a name="erfcinvf"></a>  erfcinvf —

Oblicza odwrotność komplementarną funkcję błędu _x

```
inline float erfcinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotność komplementarną funkcję błędu _x

##  <a name="erff"></a>  erff —

Oblicza funkcję błędu _X

```
inline float erff(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji błędu _x

##  <a name="erfinv"></a>  erfinv —

Oblicza funkcję błędu odwrotność _X

```
inline float erfinv(float _X) restrict(amp);

inline double erfinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji odwrotny błąd _x

##  <a name="erfinvf"></a>  erfinvf —

Oblicza funkcję błędu odwrotność _X

```
inline float erfinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji odwrotny błąd _x

##  <a name="exp10"></a>  exp10 —

Oblicza base 10 wykładniczego argumentu

```
inline float exp10(float _X) restrict(amp);

inline double exp10(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość base 10 wykładniczego argumentu

##  <a name="exp10f"></a>  exp10f —

Oblicza base 10 wykładniczego argumentu

```
inline float exp10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość base 10 wykładniczego argumentu

##  <a name="expm1"></a>  expm1 —

Oblicza wartość wykładniczą (podstawa e) argumentu, minus 1

```
inline float expm1(float exponent) restrict(amp);

inline double expm1(double exponent) restrict(amp);
```

### <a name="parameters"></a>Parametry

*Wykładnik*<br/>
Termin wykładniczego *n* wyrażenia matematyczne `e` <sup>n</sup>, gdzie `e` jest podstawą logarytmu naturalnego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość wykładniczą (podstawa e) argumentu, minus 1

##  <a name="expm1f"></a>  expm1f —

Oblicza wartość wykładniczą (podstawa e) argumentu, minus 1

```
inline float expm1f(float exponent) restrict(amp);
```

### <a name="parameters"></a>Parametry

*Wykładnik*<br/>
Termin wykładniczego *n* wyrażenia matematyczne `e` <sup>n</sup>, gdzie `e` jest podstawą logarytmu naturalnego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość wykładniczą (podstawa e) argumentu, minus 1

##  <a name="exp"></a>  EXP

Oblicza eksponentę argumentu

```
inline float exp(float _X) restrict(amp);

inline double exp(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca eksponentę argumentu

##  <a name="expf"></a>  expf —

Oblicza eksponentę argumentu

```
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca eksponentę argumentu

##  <a name="exp2"></a>  exp2 —

Oblicza base 2 wykładniczego argumentu

```
inline float exp2(float _X) restrict(amp);

inline double exp2(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca base 2 wykładniczego argumentu

##  <a name="exp2f"></a>  exp2f —

Oblicza base 2 wykładniczego argumentu

```
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca base 2 wykładniczego argumentu

##  <a name="fabs"></a>  fabs —

Zwraca wartość bezwzględną argumentu

```
inline float fabs(float _X) restrict(amp);

inline double fabs(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość bezwzględną argumentu

##  <a name="fabsf"></a>  fabsf —

Zwraca wartość bezwzględną argumentu

```
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość bezwzględną argumentu

## <a name="fdim"></a> fdim —

Określa dodatnią różnicę między argumentami.
```
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

Różnica między _X i _Y, jeśli _X jest większa niż _Y; w przeciwnym razie, + 0.

## <a name="fdimf"></a> fdimf —

Określa dodatnią różnicę między argumentami.
```
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

Różnica między _X i _Y, jeśli _X jest większa niż _Y; w przeciwnym razie, + 0.

##  <a name="floor"></a>  FLOOR

Oblicza Zaokrąglenie w dół argumentu

```
inline float floor(float _X) restrict(amp);

inline double floor(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca floor argumentu

##  <a name="floorf"></a>  floorf —

Oblicza Zaokrąglenie w dół argumentu

```
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca floor argumentu

## <a name="a-namefma-fma"></a><a name="fma"> fma

Oblicza iloczyn określonych argumentów pierwszego i drugiego, a następnie dodaje trzeci określony argument do wyniku; całe obliczenie jest wykonywane jako pojedyncza operacja.
```
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

Wynik wyrażenia (_X \* _Y) + _Z. Całe obliczenie jest wykonywane jako pojedyncza operacja; czyli wyrażenia podrzędne są obliczane z dokładnością do nieskończoności, i tylko ostateczny wynik jest zaokrąglany.

## <a name="fmaf"></a> fmaf —

Oblicza iloczyn określonych argumentów pierwszego i drugiego, a następnie dodaje trzeci określony argument do wyniku; całe obliczenie jest wykonywane jako pojedyncza operacja.
```
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

Wynik wyrażenia (_X \* _Y) + _Z. Całe obliczenie jest wykonywane jako pojedyncza operacja; czyli wyrażenia podrzędne są obliczane z dokładnością do nieskończoności, i tylko ostateczny wynik jest zaokrąglany.

##  <a name="fmax"></a>  Fmax —

Określić maksymalną wartość liczbową z podanych argumentów

```
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

Zwraca największą wartość liczbową z podanych argumentów

##  <a name="fmaxf"></a>  fmaxf —

Określić maksymalną wartość liczbową z podanych argumentów

```
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

Zwraca największą wartość liczbową z podanych argumentów

##  <a name="fmin"></a>  Fmin —

Określić minimalną wartość liczbową z podanych argumentów

```
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

Zwraca minimalną wartość liczbową argumentów

##  <a name="fminf"></a>  fminf —

Określić minimalną wartość liczbową z podanych argumentów

```
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

Zwraca minimalną wartość liczbową argumentów

##  <a name="fmod"></a>  fmod — funkcja (C++ AMP)

Oblicza pozostałą część pierwszego określonego argumentu podzieloną przez drugi określony argument.

```
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

W pozostałej części `_X` podzielona przez `_Y`; czyli wartość `_X`  -  `_Y` *n*, gdzie *n* jest liczbą całkowitą tak, aby wielkość `_X`  -  `_Y` *n* jest mniejszy niż wielkość `_Y`.

##  <a name="fmodf"></a>  fmodf —

Oblicza pozostałą część pierwszego określonego argumentu podzieloną przez drugi określony argument.

```
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

W pozostałej części `_X` podzielona przez `_Y`; czyli wartość `_X`  -  `_Y` *n*, gdzie *n* jest liczbą całkowitą tak, aby wielkość `_X`  -  `_Y` *n* jest mniejszy niż wielkość `_Y`.

##  <a name="fpclassify"></a>  fpclassify —

Klasyfikuje wartość argumentu, jak NaN, nieskończoną, normalny, subnormal, zero

```
inline int fpclassify(float _X) restrict(amp);

inline int fpclassify(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość numeru makra klasyfikacji właściwą wartość argumentu.

##  <a name="frexp"></a>  frexp —

Pobiera mantysę i wykładnik _X

```
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
Zwraca wartość zmiennoprzecinkową całkowitą wykładnik _X

### <a name="return-value"></a>Wartość zwracana

Zwraca _X mantysy

##  <a name="frexpf"></a>  frexpf —

Pobiera mantysę i wykładnik _X

```
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Exp*<br/>
Zwraca wartość zmiennoprzecinkową całkowitą wykładnik _X

### <a name="return-value"></a>Wartość zwracana

Zwraca _X mantysy

##  <a name="hypot"></a>  hypot —

Oblicza pierwiastek kwadratowy suma kwadratów _X i _Y

```
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

Zwraca pierwiastek kwadratowy suma kwadratów _X i _Y

##  <a name="hypotf"></a>  hypotf —

Oblicza pierwiastek kwadratowy suma kwadratów _X i _Y

```
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

Zwraca pierwiastek kwadratowy suma kwadratów _X i _Y

##  <a name="ilogb"></a>  ilogb —

Wyodrębnij wykładnik _X jako wartość typu int podpisem

```
inline int ilogb(float _X) restrict(amp);

inline int ilogb(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wykładnik _X jako wartość typu int podpisem

##  <a name="ilogbf"></a>  ilogbf —

Wyodrębnij wykładnik _X jako wartość typu int podpisem

```
inline int ilogbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wykładnik _X jako wartość typu int podpisem

##  <a name="isfinite"></a>  isfinite —

Określa, czy argument ma skończoną wartość

```
inline int isfinite(float _X) restrict(amp);

inline int isfinite(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość różną od zera, tylko wtedy, gdy argument ma skończoną wartość

##  <a name="isinf"></a>  isinf —

Określa, czy argument jest nieskończony

```
inline int isinf(float _X) restrict(amp);

inline int isinf(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość różną od zera, tylko wtedy, gdy argument ma wartość nieskończona

##  <a name="isnan"></a>  isNaN —

Określa, czy argument jest NaN.

```
inline int isnan(float _X) restrict(amp);

inline int isnan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość różną od zera, tylko wtedy, gdy argument ma wartość NaN

##  <a name="isnormal"></a>  isnormal —

Określa, czy argument jest normalnego

```
inline int isnormal(float _X) restrict(amp);

inline int isnormal(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość różną od zera, tylko wtedy, gdy argument ma wartość normalna

##  <a name="ldexp"></a>  ldexp —

Oblicza liczbę rzeczywistą z określonych mantysy i wykładnika.

```
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);

inline double ldexp(
    double _X,
    double _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa, mantysa

*_Exp*<br/>
Wartość całkowita, wykładnicza

### <a name="return-value"></a>Wartość zwracana

Zwraca _X \* 2 ^ _Exp

##  <a name="ldexpf"></a>  ldexpf —

Oblicza liczbę rzeczywistą z określonych mantysy i wykładnika.

```
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa, mantysa

*_Exp*<br/>
Wartość całkowita, wykładnicza

### <a name="return-value"></a>Wartość zwracana

Zwraca _X \* 2 ^ _Exp

##  <a name="lgamma"></a>  lgamma —

Oblicza wartość bezwzględną liczby gamma argumentu logarytm naturalny

```
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

*Zalo_guj*<br/>
Zwraca znak

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm naturalny wartość bezwzględną liczby gamma argumentu

##  <a name="lgammaf"></a>  lgammaf —

Oblicza wartość bezwzględną liczby gamma argumentu logarytm naturalny

```
inline float lgammaf(
    float _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*Zalo_guj*<br/>
Zwraca znak

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm naturalny wartość bezwzględną liczby gamma argumentu

##  <a name="log"></a>  Dziennik

Oblicza logarytm podstawa e argumentu

```
inline float log(float _X) restrict(amp);

inline double log(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm o podstawie base e argumentu

##  <a name="log10"></a>  LOG10

Oblicza logarytm base 10 argumentu

```
inline float log10(float _X) restrict(amp);

inline double log10(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm o podstawie base 10 argumentu

##  <a name="log10f"></a>  log10f —

Oblicza logarytm base 10 argumentu

```
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm o podstawie base 10 argumentu

##  <a name="log1p"></a>  log1p —

Oblicza logarytm podstawa e 1 oraz argumentu

```
inline float log1p(float _X) restrict(amp);

inline double log1p(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm podstawa e 1 oraz argumentu

##  <a name="log1pf"></a>  log1pf —

Oblicza logarytm podstawa e 1 oraz argumentu

```
inline float log1pf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm podstawa e 1 oraz argumentu

##  <a name="log2"></a>  log2 —

Oblicza logarytm podstawie 2 dla podanego argumentu

```
inline float log2(float _X) restrict(amp);

inline double log2(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm o podstawie base 10 argumentu

##  <a name="log2f"></a>  log2f —

Oblicza logarytm podstawie 2 dla podanego argumentu

```
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm o podstawie base 10 argumentu

##  <a name="logb"></a>  logb —

Wyodrębnia wykładnik _X, jako wartość liczby całkowitej ze znakiem w formacie zmiennoprzecinkowych

```
inline float logb(float _X) restrict(amp);

inline double logb(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca podpisem wykładnik _X

##  <a name="logbf"></a>  logbf —

Wyodrębnia wykładnik _X, jako wartość liczby całkowitej ze znakiem w formacie zmiennoprzecinkowych

```
inline float logbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca podpisem wykładnik _X

##  <a name="logf"></a>  logf —

Oblicza logarytm podstawa e argumentu

```
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm o podstawie base e argumentu

##  <a name="modf"></a>  modf —

Dzieli określony argument na ułamkową i całkowitą części.

```
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
[out] Część całkowita `_X`, jako wartość zmiennoprzecinkowa.

### <a name="return-value"></a>Wartość zwracana

Oznaczona ułamkowa część `_X`.

##  <a name="modff"></a>  modff —

Dzieli określony argument na ułamkową i całkowitą części.

```
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

Zwraca część ułamkową ze znakiem `_X`.

##  <a name="nan"></a>  NaN

Zwraca ciche NaN

```
inline double nan(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca ciche NaN, jeżeli udostępniono zawartość w _X

##  <a name="nanf"></a>  nanf —

Zwraca ciche NaN

```
inline float nanf(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca ciche NaN, jeżeli udostępniono zawartość w _X

##  <a name="nearbyint"></a>  nearbyint —

Zaokrągla wartość argumentu na wartość całkowitą w formacie zmiennoprzecinkowych, przy użyciu bieżącego kierunek zaokrąglania.

```
inline float nearbyint(float _X) restrict(amp);

inline double nearbyint(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość całkowitą z zaokrąglonymi.

##  <a name="nearbyintf"></a>  nearbyintf —

Zaokrągla wartość argumentu na wartość całkowitą w formacie zmiennoprzecinkowych, przy użyciu bieżącego kierunek zaokrąglania.

```
inline float nearbyintf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość całkowitą z zaokrąglonymi.

##  <a name="nextafter"></a>  nextafter —

Określić następną wartość, w typie funkcji, po _X w kierunku _Y

```
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

Zwraca następną wartość, w typie funkcji, po _X w kierunku _Y

##  <a name="nextafterf"></a>  nextafterf —

Określić następną wartość, w typie funkcji, po _X w kierunku _Y

```
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

Zwraca następną wartość, w typie funkcji, po _X w kierunku _Y

##  <a name="phi"></a>  Phi

Zwraca funkcję rozkładu skumulowanego argumentu

```
inline float phi(float _X) restrict(amp);

inline double phi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję rozkładu skumulowanego argumentu

##  <a name="phif"></a>  phif —

Zwraca funkcję rozkładu skumulowanego argumentu

```
inline float phif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję rozkładu skumulowanego argumentu

##  <a name="pow"></a>  Pow

Oblicza _X podniesione do potęgi _y

```
inline float pow(
    float _X,
    float _Y) restrict(amp);

inline double pow(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa, podstawowy

*_Y*<br/>
Wartość zmiennoprzecinkowa, wykładnika

### <a name="return-value"></a>Wartość zwracana

##  <a name="powf"></a>  powf —

Oblicza _X podniesione do potęgi _y

```
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa, podstawowy

*_Y*<br/>
Wartość zmiennoprzecinkowa, wykładnika

### <a name="return-value"></a>Wartość zwracana

##  <a name="probit"></a>  probit —

Zwraca funkcję rozkładu skumulowanego odwrotność argumentu

```
inline float probit(float _X) restrict(amp);

inline double probit(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję rozkładu skumulowanego odwrotność argumentu

##  <a name="probitf"></a>  probitf —

Zwraca funkcję rozkładu skumulowanego odwrotność argumentu

```
inline float probitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję rozkładu skumulowanego odwrotność argumentu

##  <a name="rcbrt"></a>  rcbrt —

Zwraca odwrotność kwadratowy modułu argumentu

```
inline float rcbrt(float _X) restrict(amp);

inline double rcbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotność kwadratowy modułu argumentu

##  <a name="rcbrtf"></a>  rcbrtf —

Zwraca odwrotność kwadratowy modułu argumentu

```
inline float rcbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotność kwadratowy modułu argumentu

##  <a name="remainder"></a>  Pozostała

Oblicza pozostałą: _X REM _Y

```
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

##  <a name="remainderf"></a>  remainderf —

Oblicza pozostałą: _X REM _Y

```
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

##  <a name="remquo"></a>  remquo —

Oblicza pozostałą część pierwszego określonego argumentu podzieloną przez drugi określony argument. Ponadto oblicza iloraz mantysy pierwszego określonego argumentu przez mantysę drugiego określonego argumentu i zwraca wartość ilorazu przy użyciu lokalizacji określonej w trzecim argumencie.

```
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
[out] Adres liczby całkowitej, która służy do zwracania ilorazu ułamków `_X` podzielona przez ułamków `_Y`.

### <a name="return-value"></a>Wartość zwracana

Zwraca resztę z `_X` podzielona przez `_Y`.

##  <a name="remquof"></a>  remquof —

Oblicza pozostałą część pierwszego określonego argumentu podzieloną przez drugi określony argument. Ponadto oblicza iloraz mantysy pierwszego określonego argumentu przez mantysę drugiego określonego argumentu i zwraca wartość ilorazu przy użyciu lokalizacji określonej w trzecim argumencie.

```
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
[out] Adres liczby całkowitej, która służy do zwracania ilorazu ułamków `_X` podzielona przez ułamków `_Y`.

### <a name="return-value"></a>Wartość zwracana

Zwraca resztę z `_X` podzielona przez `_Y`.

##  <a name="round"></a>  ROUND

Zaokrągla liczbę _X do najbliższej liczby całkowitej.

```
inline float round(float _X) restrict(amp);

inline double round(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę całkowitą najbliższej _x

##  <a name="roundf"></a>  roundf —

Zaokrągla liczbę _X do najbliższej liczby całkowitej.

```
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę całkowitą najbliższej _x

##  <a name="rsqrt"></a>  rsqrt —

Zwraca odwrotność pierwiastek kwadratowy argumentu

```
inline float rsqrt(float _X) restrict(amp);

inline double rsqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotność pierwiastek kwadratowy argumentu

##  <a name="rsqrtf"></a>  rsqrtf —

Zwraca odwrotność pierwiastek kwadratowy argumentu

```
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotność pierwiastek kwadratowy argumentu

##  <a name="scalb"></a>  scalb —

Mnoży _X przez FLT_RADIX do _Y zasilania

```
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

Zwraca _X \* (FLT_RADIX ^ _Y)

##  <a name="scalbf"></a>  scalbf —

Mnoży _X przez FLT_RADIX do _Y zasilania

```
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

Zwraca _X \* (FLT_RADIX ^ _Y)

##  <a name="scalbn"></a>  scalbn —

Mnoży _X przez FLT_RADIX do _Y zasilania

```
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

Zwraca _X \* (FLT_RADIX ^ _Y)

##  <a name="scalbnf"></a>  scalbnf —

Mnoży _X przez FLT_RADIX do _Y zasilania

```
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

Zwraca _X \* (FLT_RADIX ^ _Y)

##  <a name="signbit"></a>  signbit —

Określa, czy znak _X jest ujemna

```
inline int signbit(float _X) restrict(amp);

inline int signbit(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość różną od zera, tylko wtedy, gdy znak _X jest ujemna

##  <a name="signbitf"></a>  signbitf —

Określa, czy znak _X jest ujemna

```
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość różną od zera, tylko wtedy, gdy znak _X jest ujemna

##  <a name="sin"></a>  SIN

Oblicza wartość funkcji sinus argumentu

```
inline float sin(float _X) restrict(amp);

inline double sin(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji sinus argumentu

##  <a name="sinf"></a>  sinf —

Oblicza wartość funkcji sinus argumentu

```
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji sinus argumentu

##  <a name="sincos"></a>  sincos —

Oblicza wartość funkcji sinus i cosinus z _X

```
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
Zwraca wartość funkcji sinus _X

*_KOŃCE*<br/>
Zwraca wartość funkcji cosinus z _X

##  <a name="sincosf"></a>  sincosf —

Oblicza wartość funkcji sinus i cosinus z _X

```
inline void sincosf(
    float _X,
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_S*<br/>
Zwraca wartość funkcji sinus _X

*_KOŃCE*<br/>
Zwraca wartość funkcji cosinus z _X

##  <a name="sinh"></a>  SINH

Oblicza wartość funkcji sinus hiperboliczny dla argumentu

```
inline float sinh(float _X) restrict(amp);

inline double sinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca sinus hiperboliczny wartość argumentu

##  <a name="sinhf"></a>  sinhf —

Oblicza wartość funkcji sinus hiperboliczny dla argumentu

```
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca sinus hiperboliczny wartość argumentu

##  <a name="sinpi"></a>  sinpi —

Oblicza wartość funkcji sinus liczby pi \* _X

```
inline float sinpi(float _X) restrict(amp);

inline double sinpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji sinus liczby pi \* _X

##  <a name="sinpif"></a>  sinpif —

Oblicza wartość funkcji sinus liczby pi \* _X

```
inline float sinpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji sinus liczby pi \* _X

##  <a name="sqrt"></a>  SQRT

Oblicza squre kwadratowy argumentu

```
inline float sqrt(float _X) restrict(amp);

inline double sqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca katalog główny squre argumentu

##  <a name="sqrtf"></a>  sqrtf —

Oblicza squre kwadratowy argumentu

```
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca katalog główny squre argumentu

##  <a name="tan"></a>  tan

Oblicza wartość funkcji tangens argumentu

```
inline float tan(float _X) restrict(amp);

inline double tan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji tangens argumentu

##  <a name="tanf"></a>  tanf —

Oblicza wartość funkcji tangens argumentu

```
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji tangens argumentu

##  <a name="tanh"></a>  TANH

Oblicza wartość funkcji tangens hiperboliczny dla argumentu

```
inline float tanh(float _X) restrict(amp);

inline double tanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji tangens hiperboliczny dla argumentu

##  <a name="tanhf"></a>  tanhf —

Oblicza wartość funkcji tangens hiperboliczny dla argumentu

```
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji tangens hiperboliczny dla argumentu

##  <a name="tanpi"></a>  tanpi —

Oblicza wartość funkcji tangens liczby pi \* _X

```
inline float tanpi(float _X) restrict(amp);

inline double tanpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji tangens liczby pi \* _X

##  <a name="tanpif"></a>  tanpif —

Oblicza wartość funkcji tangens liczby pi \* _X

```
inline float tanpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji tangens liczby pi \* _X

##  <a name="tgamma"></a>  tgamma —

Oblicza funkcja gamma _x

```
inline float tgamma(float _X) restrict(amp);

inline double tgamma(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wynik funkcji gamma _x

##  <a name="tgammaf"></a>  tgammaf —

Oblicza funkcja gamma _x

```
inline float tgammaf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wynik funkcji gamma _x

##  <a name="trunc"></a>  TRUNC —

Obcina argument do składnika całkowitego

```
inline float trunc(float _X) restrict(amp);

inline double trunc(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę całkowitą argumentu

##  <a name="truncf"></a>  truncf —

Obcina argument do składnika całkowitego

```
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę całkowitą argumentu

## <a name="see-also"></a>Zobacz też

[Concurrency::precise_math, przestrzeń nazw](concurrency-precise-math-namespace.md)
