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
ms.openlocfilehash: ee6ab2313fbdc288ebba1b3fdacf192b7b578eb6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321856"
---
# <a name="concurrencyprecise_math-namespace-functions"></a>Concurrency::precise_math, funkcje przestrzeni nazw

||||
|-|-|-|
|[Acos](#acos)|[acosf ( acosf )](#acosf)|[acosh (acosh)](#acosh)|
|[acoshf](#acoshf)|[Asin](#asin)|[asinf](#asinf)|
|[asinh ( asinh )](#asinh)|[asinhf ( asinhf )](#asinhf)|[Atan](#atan)|
|[atan2 (atan2)](#atan2)|[atan2f](#atan2f)|[atanf ( atanf )](#atanf)|
|[atanh ( atanh )](#atanh)|[atanhf ( atanhf )](#atanhf)|[cbrt ( cbrt )](#cbrt)|
|[cbrtf ( cbrtf )](#cbrtf)|[Ceil](#ceil)|[ceilf](#ceilf)|
|[znak kopiowania](#copysign)|[copysignf (podpis kserokopii)](#copysignf)|[cos](#cos)|
|[cosf ( cosf )](#cosf)|[Cosh](#cosh)|[coshf ( coshf )](#coshf)|
|[cospi ( cospi )](#cospi)|[cospif ( cospif )](#cospif)|[Erf](#erf)|
|[erfc (erfc)](#erfc)|[erfcf (erfcf)](#erfcf)|[erfcinv ( erfcinv )](#erfcinv)|
|[erfcinvf](#erfcinvf)|[erff (erff)](#erff)|[erfinv ( erfinv )](#erfinv)|
|[erfinvf ( erfinvf )](#erfinvf)|[Exp](#exp)|[exp10](#exp10)|
|[exp10f](#exp10f)|[exp2](#exp2)|[exp2f](#exp2f)|
|[expf (wycho.](#expf)|[expm1](#expm1)|[expm1f](#expm1f)|
|[Fabs](#fabs)|[fabsf ( fabsf )](#fabsf)|[Podłogi](#floor)|
|[fdim ( fdim )](#fdim)|[fdimf ( fdimf )](#fdimf)||
|[podłoga](#floorf)|[Fma](#fma)|[fmaf (fmaf)](#fmaf)|
[fmax ( fmax )](#fmax)|[fmaxf ( fmaxf )](#fmaxf)||
|[fmin ( fmin )](#fmin)|[fminf (fminf)](#fminf)|[Fmod](#fmod)|
|[fmodf ( fmodf )](#fmodf)|[fpclassify](#fpclassify)|[frexp](#frexp)|
|[frexpf](#frexpf)|[hypot](#hypot)|[hypotf (hipotf)](#hypotf)|
|[ilogb ( ilogb )](#ilogb)|[ilogbf ( ilogbf )](#ilogbf)|[isfinite](#isfinite)|
|[isinf](#isinf)|[Isnan (isnan)](#isnan)|[isnormal](#isnormal)|
|[ldexp](#ldexp)|[ldexpf ( ldexpf )](#ldexpf)|[lgamma](#lgamma)|
|[lgammaf](#lgammaf)|[Dziennika](#log)|[log10](#log10)|
|[log10f](#log10f)|[log1p](#log1p)|[log1pf](#log1pf)|
|[log2](#log2)|[log2f](#log2f)|[logb (logb)](#logb)|
|[logbf (logbf)](#logbf)|[logf (logf)](#logf)|[modf ( modf )](#modf)|
|[modff ( modff )](#modff)|[Nan](#nan)|[nanf](#nanf)|
|[w pobliżu](#nearbyint)|[w pobliżuintf](#nearbyintf)|[następna po](#nextafter)|
|[następnypo](#nextafterf)|[Phi](#phi)|[phif ( phif )](#phif)|
|[Pow](#pow)|[powf (powf)](#powf)|[probit](#probit)|
|[probitf](#probitf)|[rcbrt ( rcbrt )](#rcbrt)|[rcbrtf ( rcbrtf )](#rcbrtf)|
|[Pozostałą część](#remainder)|[resekt](#remainderf)|[remquo](#remquo)|
|[remquof](#remquof)|[Okrągłe](#round)|[zaokrąglony](#roundf)|
|[rsqrt ( rsqrt )](#rsqrt)|[rsqrtf](#rsqrtf)|[scalb](#scalb)|
|[scalbf (scalbf)](#scalbf)|[scalbn](#scalbn)|[scalbnf](#scalbnf)|
|[signbit](#signbit)|[signbitf](#signbitf)|[Grzechu](#sin)|
|[sincos (sincos)](#sincos)|[sincosf ( sincosf )](#sincosf)|[Sinf](#sinf)|
|[Sinh](#sinh)|[sinhf](#sinhf)|[sinpi (sinpi)](#sinpi)|
|[sinpif (sinpif)](#sinpif)|[Sqrt](#sqrt)|[sqrtf (](#sqrtf)|
|[Tan](#tan)|[tanf ( tanf )](#tanf)|[Tanh](#tanh)|
|[tanhf ( tanhf )](#tanhf)|[tanpi ( tanpi )](#tanpi)|[tanpif ( tanpif )](#tanpif)|
|[tgamma ( tgamma )](#tgamma)|[tgammaf ( tgammaf )](#tgammaf)|[Trunc](#trunc)|
|[obcinanie](#truncf)|

## <a name="acos"></a><a name="acos"></a>Acos

Oblicza arccosine argumentu

```cpp
inline float acos(float _X) restrict(amp);

inline double acos(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca arccosine wartość argumentu

## <a name="acosf"></a><a name="acosf"></a>acosf ( acosf )

Oblicza arccosine argumentu

```cpp
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca arccosine wartość argumentu

## <a name="acosh"></a><a name="acosh"></a>acosh (acosh)

Oblicza odwrotną cosine hiperboliczny argumentu

```cpp
inline float acosh(float _X) restrict(amp);

inline double acosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotną wartość cosine hiperbolicznej argumentu

## <a name="acoshf"></a><a name="acoshf"></a>acoshf

Oblicza odwrotną cosine hiperboliczny argumentu

```cpp
inline float acoshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotną wartość cosine hiperbolicznej argumentu

## <a name="asin"></a><a name="asin"></a>Asin

Oblicza łuk argumentu

```cpp
inline float asin(float _X) restrict(amp);

inline double asin(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość arcsine argumentu

## <a name="asinf"></a><a name="asinf"></a>asinf

Oblicza łuk argumentu

```cpp
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość arcsine argumentu

## <a name="asinh"></a><a name="asinh"></a>asinh ( asinh )

Oblicza odwrotną sinus hiperboliczny argumentu

```cpp
inline float asinh(float _X) restrict(amp);

inline double asinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotną wartość sinusoidy hiperbolicznej argumentu

## <a name="asinhf"></a><a name="asinhf"></a>asinhf ( asinhf )

Oblicza odwrotną sinus hiperboliczny argumentu

```cpp
inline float asinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotną wartość sinusoidy hiperbolicznej argumentu

## <a name="atan"></a><a name="atan"></a>Atan

Oblicza arctangent argumentu

```cpp
inline float atan(float _X) restrict(amp);

inline double atan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca arctangent wartość argumentu

## <a name="atan2"></a><a name="atan2"></a>atan2 (atan2)

Oblicza arctangent _Y/_X

```cpp
inline float atan2(
    float _Y,
    float _X) restrict(amp);

inline double atan2(
    double _Y,
    double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_y*<br/>
Wartość zmiennoprzecinowa

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość arctangent _Y/_X

## <a name="atan2f"></a><a name="atan2f"></a>atan2f

Oblicza arctangent _Y/_X

```cpp
inline float atan2f(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_y*<br/>
Wartość zmiennoprzecinowa

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość arctangent _Y/_X

## <a name="atanf"></a><a name="atanf"></a>atanf ( atanf )

Oblicza arctangent argumentu

```cpp
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca arctangent wartość argumentu

## <a name="atanh"></a><a name="atanh"></a>atanh ( atanh )

Oblicza odwrotną styczną hiperboliczną argumentu

```cpp
inline float atanh(float _X) restrict(amp);

inline double atanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotną wartość hiperboliczną stycznej argumentu

## <a name="atanhf"></a><a name="atanhf"></a>atanhf ( atanhf )

Oblicza odwrotną styczną hiperboliczną argumentu

```cpp
inline float atanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotną wartość hiperboliczną stycznej argumentu

## <a name="cbrt"></a><a name="cbrt"></a>cbrt ( cbrt )

Oblicza prawdziwy katalog główny modułu argumentu

```cpp
inline float cbrt(float _X) restrict(amp);

inline double cbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca prawdziwy katalog główny modułu argumentu

## <a name="cbrtf"></a><a name="cbrtf"></a>cbrtf ( cbrtf )

Oblicza prawdziwy katalog główny modułu argumentu

```cpp
inline float cbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca prawdziwy katalog główny modułu argumentu

## <a name="ceil"></a><a name="ceil"></a>Ceil

Oblicza pułap argumentu

```cpp
inline float ceil(float _X) restrict(amp);

inline double ceil(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca pułap argumentu

## <a name="ceilf"></a><a name="ceilf"></a>ceilf

Oblicza pułap argumentu

```cpp
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca pułap argumentu

## <a name="copysign"></a><a name="copysign"></a>znak kopiowania

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

*_x*<br/>
Wartość zmiennoprzecinowa

*_y*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość o wielkości _X i znaku _Y

## <a name="copysignf"></a><a name="copysignf"></a>copysignf (podpis kserokopii)

Tworzy wartość o wielkości _X i znaku _Y

```cpp
inline float copysignf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_y*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość o wielkości _X i znaku _Y

## <a name="cos"></a><a name="cos"></a>cos

Oblicza cosine argumentu

```cpp
inline float cos(float _X) restrict(amp);

inline double cos(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość cosine argumentu

## <a name="cosf"></a><a name="cosf"></a>cosf ( cosf )

Oblicza cosine argumentu

```cpp
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość cosine argumentu

## <a name="cosh"></a><a name="cosh"></a>Cosh

Oblicza wartość cosine hiperbolicznej argumentu

```cpp
inline float cosh(float _X) restrict(amp);

inline double cosh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość cosine hiperbolicznej argumentu

## <a name="coshf"></a><a name="coshf"></a>coshf ( coshf )

Oblicza wartość cosine hiperbolicznej argumentu

```cpp
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość cosine hiperbolicznej argumentu

## <a name="cospi"></a><a name="cospi"></a>cospi ( cospi )

Oblicza wartość cosine \* pi _X

```cpp
inline float cospi(float _X) restrict(amp);

inline double cospi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość cosine \* pi _X

## <a name="cospif"></a><a name="cospif"></a>cospif ( cospif )

Oblicza wartość cosine \* pi _X

```cpp
inline float cospif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość cosine \* pi _X

## <a name="erf"></a><a name="erf"></a>Erf

Oblicza funkcję błędu _X

```cpp
inline float erf(float _X) restrict(amp);

inline double erf(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję błędu _X

## <a name="erfc"></a><a name="erfc"></a>erfc (erfc)

Oblicza funkcję błędu uzupełniającego _X

```cpp
inline float erfc(float _X) restrict(amp);

inline double erfc(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję błędu uzupełniającego _X

## <a name="erfcf"></a><a name="erfcf"></a>erfcf (erfcf)

Oblicza funkcję błędu uzupełniającego _X

```cpp
inline float erfcf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję błędu uzupełniającego _X

## <a name="erfcinv"></a><a name="erfcinv"></a>erfcinv ( erfcinv )

Oblicza odwrotną funkcję błędu uzupełniającego _X

```cpp
inline float erfcinv(float _X) restrict(amp);

inline double erfcinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję błędu uzupełniającego _X

## <a name="erfcinvf"></a><a name="erfcinvf"></a>erfcinvf

Oblicza odwrotną funkcję błędu uzupełniającego _X

```cpp
inline float erfcinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję błędu uzupełniającego _X

## <a name="erff"></a><a name="erff"></a>erff (erff)

Oblicza funkcję błędu _X

```cpp
inline float erff(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję błędu _X

## <a name="erfinv"></a><a name="erfinv"></a>erfinv ( erfinv )

Oblicza funkcję odwrotnego błędu _X

```cpp
inline float erfinv(float _X) restrict(amp);

inline double erfinv(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję odwrotnego błędu _X

## <a name="erfinvf"></a><a name="erfinvf"></a>erfinvf ( erfinvf )

Oblicza funkcję odwrotnego błędu _X

```cpp
inline float erfinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję odwrotnego błędu _X

## <a name="exp10"></a><a name="exp10"></a>exp10

Oblicza wartość podstawową-10 wykładniczą argumentu

```cpp
inline float exp10(float _X) restrict(amp);

inline double exp10(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość wykładnicza base-10 argumentu

## <a name="exp10f"></a><a name="exp10f"></a>exp10f

Oblicza wartość podstawową-10 wykładniczą argumentu

```cpp
inline float exp10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość wykładnicza base-10 argumentu

## <a name="expm1"></a><a name="expm1"></a>expm1

Oblicza wartość wykładniczą (podstawa e) argumentu, minus 1

```cpp
inline float expm1(float exponent) restrict(amp);

inline double expm1(double exponent) restrict(amp);
```

### <a name="parameters"></a>Parametry

*Wykładnik*<br/>
Wykładniczy termin *n* wyrażenia `e`matematycznego <sup>n</sup> `e` , gdzie jest podstawą logarytmu naturalnego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość wykładniczą (podstawa e) argumentu, minus 1

## <a name="expm1f"></a><a name="expm1f"></a>expm1f

Oblicza wartość wykładniczą (podstawa e) argumentu, minus 1

```cpp
inline float expm1f(float exponent) restrict(amp);
```

### <a name="parameters"></a>Parametry

*Wykładnik*<br/>
Wykładniczy termin *n* wyrażenia `e`matematycznego <sup>n</sup> `e` , gdzie jest podstawą logarytmu naturalnego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość wykładniczą (podstawa e) argumentu, minus 1

## <a name="exp"></a><a name="exp"></a>Exp

Oblicza wykładniczą bazę e argumentu

```cpp
inline float exp(float _X) restrict(amp);

inline double exp(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wykładniczą bazę e argumentu

## <a name="expf"></a><a name="expf"></a>expf (wycho.

Oblicza wykładniczą bazę e argumentu

```cpp
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wykładniczą bazę e argumentu

## <a name="exp2"></a><a name="exp2"></a>exp2

Oblicza wykładniczą bazową-2 argumentu

```cpp
inline float exp2(float _X) restrict(amp);

inline double exp2(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość wykładnicza base-2 argumentu

## <a name="exp2f"></a><a name="exp2f"></a>exp2f

Oblicza wykładniczą bazową-2 argumentu

```cpp
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość wykładnicza base-2 argumentu

## <a name="fabs"></a><a name="fabs"></a>Fabs

Zwraca wartość bezwzględną argumentu

```cpp
inline float fabs(float _X) restrict(amp);

inline double fabs(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość bezwzględną argumentu

## <a name="fabsf"></a><a name="fabsf"></a>fabsf ( fabsf )

Zwraca wartość bezwzględną argumentu

```cpp
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość bezwzględną argumentu

## <a name="fdim"></a><a name="fdim"></a>fdim ( fdim )

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

*_x*<br/>
*_Y* wartości zmiennoprzecinowej<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Różnica między _X a _Y, jeśli _X jest większa niż _Y; w przeciwnym razie +0.

## <a name="fdimf"></a><a name="fdimf"></a>fdimf ( fdimf )

Oblicza dodatnią różnicę między argumentami.

```cpp
inline float fdimf(
   float _X,
   float _Y
) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
*_Y* wartości zmiennoprzecinowej<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Różnica między _X a _Y, jeśli _X jest większa niż _Y; w przeciwnym razie +0.

## <a name="floor"></a><a name="floor"></a>Podłogi

Oblicza podłogę argumentu

```cpp
inline float floor(float _X) restrict(amp);

inline double floor(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca podłogę argumentu

## <a name="floorf"></a><a name="floorf"></a>podłoga

Oblicza podłogę argumentu

```cpp
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca podłogę argumentu

## <a name="a-namefma-fma"></a><a name="fma">Fma

Oblicza iloczyn pierwszego i drugiego określonego argumentu, a następnie dodaje trzeci określony argument do wyniku; całe obliczenia są wykonywane jako pojedyncza operacja.

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

*_x*<br/>
Pierwszy argument zmiennoprzecinkowy.
*_y*<br/>
Drugi argument zmiennoprzecinowy.
*_Z*<br/>
Trzeci argument zmiennoprzecinowy.

### <a name="return-value"></a>Wartość zwracana

Wynik wyrażenia (_X \* _Y) + _Z. Całe obliczenia są wykonywane jako pojedyncza operacja; oznacza to, że wyrażenia podrzędne są obliczane na nieskończoną precyzję i tylko wynik końcowy jest zaokrąglany.

## <a name="fmaf"></a><a name="fmaf"></a>fmaf (fmaf)

Oblicza iloczyn pierwszego i drugiego określonego argumentu, a następnie dodaje trzeci określony argument do wyniku; całe obliczenia są wykonywane jako pojedyncza operacja.

```cpp
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Pierwszy argument zmiennoprzecinkowy.
*_y*<br/>
Drugi argument zmiennoprzecinowy.
*_Z*<br/>
Trzeci argument zmiennoprzecinowy.

### <a name="return-value"></a>Wartość zwracana

Wynik wyrażenia (_X \* _Y) + _Z. Całe obliczenia są wykonywane jako pojedyncza operacja; oznacza to, że wyrażenia podrzędne są obliczane na nieskończoną precyzję i tylko wynik końcowy jest zaokrąglany.

## <a name="fmax"></a><a name="fmax"></a>fmax ( fmax )

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

*_x*<br/>
Wartość zmiennoprzecinowa

*_y*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca maksymalną wartość liczbową argumentów

## <a name="fmaxf"></a><a name="fmaxf"></a>fmaxf ( fmaxf )

Określanie maksymalnej wartości liczbowej argumentów

```cpp
inline float fmaxf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_y*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca maksymalną wartość liczbową argumentów

## <a name="fmin"></a><a name="fmin"></a>fmin ( fmin )

Określanie minimalnej wartości liczbowej argumentów

```cpp
inline float fmin(
    float _X,
    float _Y) restrict(amp);

inline double fmin(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_y*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca minimalną wartość liczbową argumentów

## <a name="fminf"></a><a name="fminf"></a>fminf (fminf)

Określanie minimalnej wartości liczbowej argumentów

```cpp
inline float fminf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_y*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca minimalną wartość liczbową argumentów

## <a name="fmod-function-c-amp"></a><a name="fmod"></a>Funkcja fmod (C++ AMP)

Oblicza pozostałą część pierwszego określonego argumentu podzielonego przez drugi określony argument.

```cpp
inline float fmod(
    float _X,
    float _Y) restrict(amp);

inline double fmod(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Pierwszy argument zmiennoprzecinkowy.

*_y*<br/>
Drugi argument zmiennoprzecinowy.

### <a name="return-value"></a>Wartość zwracana

Pozostała część `_X` podzielona `_Y`przez ; oznacza to, że `_X`  -  `_Y`wartość *n*, gdzie *n* jest całkowitą `_X`  -  `_Y`całkowitej takiej, że `_Y`wielkość *n* jest mniejsza niż wielkość .

## <a name="fmodf"></a><a name="fmodf"></a>fmodf ( fmodf )

Oblicza pozostałą część pierwszego określonego argumentu podzielonego przez drugi określony argument.

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Pierwszy argument zmiennoprzecinkowy.

*_y*<br/>
Drugi argument zmiennoprzecinowy.

### <a name="return-value"></a>Wartość zwracana

Pozostała część `_X` podzielona `_Y`przez ; oznacza to, że `_X`  -  `_Y`wartość *n*, gdzie *n* jest całkowitą `_X`  -  `_Y`całkowitej takiej, że `_Y`wielkość *n* jest mniejsza niż wielkość .

## <a name="fpclassify"></a><a name="fpclassify"></a>fpclassify

Klasyfikuje wartość argumentu jako NaN, nieskończony, normalny, subnormal, zero

```cpp
inline int fpclassify(float _X) restrict(amp);

inline int fpclassify(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość makro klasyfikacji liczb odpowiednie do wartości argumentu.

## <a name="frexp"></a><a name="frexp"></a>frexp ( frexp )

Pobiera mantysi i wykładnika _X

```cpp
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);

inline double frexp(
    double _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_Exp*<br/>
Zwraca wykładnik liczby całkowitej _X w wartości zmiennoprzecinkowej

### <a name="return-value"></a>Wartość zwracana

Zwraca _X modliszki

## <a name="frexpf"></a><a name="frexpf"></a>frexpf

Pobiera mantysi i wykładnika _X

```cpp
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_Exp*<br/>
Zwraca wykładnik liczby całkowitej _X w wartości zmiennoprzecinkowej

### <a name="return-value"></a>Wartość zwracana

Zwraca _X modliszki

## <a name="hypot"></a><a name="hypot"></a>hypot

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

*_x*<br/>
Wartość zmiennoprzecinowa

*_y*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca pierwiastek kwadratowy sumy kwadratów _X i _Y

## <a name="hypotf"></a><a name="hypotf"></a>hypotf (hipotf)

Oblicza pierwiastek kwadratowy sumy kwadratów _X i _Y

```cpp
inline float hypotf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_y*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca pierwiastek kwadratowy sumy kwadratów _X i _Y

## <a name="ilogb"></a><a name="ilogb"></a>ilogb ( ilogb )

Wyodrębnianie wykładnika _X jako podpisanej wartości int

```cpp
inline int ilogb(float _X) restrict(amp);

inline int ilogb(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wykładnik _X jako podpisaną wartość int

## <a name="ilogbf"></a><a name="ilogbf"></a>ilogbf ( ilogbf )

Wyodrębnianie wykładnika _X jako podpisanej wartości int

```cpp
inline int ilogbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wykładnik _X jako podpisaną wartość int

## <a name="isfinite"></a><a name="isfinite"></a>isfinite

Określa, czy argument ma wartość skończoną

```cpp
inline int isfinite(float _X) restrict(amp);

inline int isfinite(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość niezerową, jeśli i tylko wtedy, gdy argument ma wartość skończoną

## <a name="isinf"></a><a name="isinf"></a>isinf (isinf)

Określa, czy argument jest nieskończonością

```cpp
inline int isinf(float _X) restrict(amp);

inline int isinf(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość niezerową, jeśli i tylko wtedy, gdy argument ma nieskończoną wartość

## <a name="isnan"></a><a name="isnan"></a>Isnan (isnan)

Określa, czy argument jest NaN

```cpp
inline int isnan(float _X) restrict(amp);

inline int isnan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość niezerową, jeśli i tylko wtedy, gdy argument ma wartość NaN

## <a name="isnormal"></a><a name="isnormal"></a>jestnormalna

Określa, czy argument jest normalny

```cpp
inline int isnormal(float _X) restrict(amp);

inline int isnormal(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość niezerową, jeśli i tylko wtedy, gdy argument ma wartość normalną

## <a name="ldexp"></a><a name="ldexp"></a>ldexp

Oblicza rzeczywistą liczbę z określonej modliszki i wykładnika.

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);

inline double ldexp(
    double _X,
    double _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinku, mantissa

*_Exp*<br/>
Wartość całkowita, wykładnik

### <a name="return-value"></a>Wartość zwracana

Zwraca _X \* 2^_Exp

## <a name="ldexpf"></a><a name="ldexpf"></a>ldexpf ( ldexpf )

Oblicza rzeczywistą liczbę z określonej modliszki i wykładnika.

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinku, mantissa

*_Exp*<br/>
Wartość całkowita, wykładnik

### <a name="return-value"></a>Wartość zwracana

Zwraca _X \* 2^_Exp

## <a name="lgamma"></a><a name="lgamma"></a>lgamma

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

*_x*<br/>
Wartość zmiennoprzecinowa

*_Sign*<br/>
Zwraca znak

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm naturalny wartości bezwzględnej gamma argumentu

## <a name="lgammaf"></a><a name="lgammaf"></a>lgammaf

Oblicza logarytm naturalny wartości bezwzględnej gamma argumentu

```cpp
inline float lgammaf(
    float _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_Sign*<br/>
Zwraca znak

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm naturalny wartości bezwzględnej gamma argumentu

## <a name="log"></a><a name="log"></a>Dziennika

Oblicza logarytm base-e argumentu

```cpp
inline float log(float _X) restrict(amp);

inline double log(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm base-e argumentu

## <a name="log10"></a><a name="log10"></a>log10

Oblicza logarytm base-10 argumentu

```cpp
inline float log10(float _X) restrict(amp);

inline double log10(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm base-10 argumentu

## <a name="log10f"></a><a name="log10f"></a>log10f

Oblicza logarytm base-10 argumentu

```cpp
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm base-10 argumentu

## <a name="log1p"></a><a name="log1p"></a>log1p

Oblicza logarytm base-e 1 plus argument

```cpp
inline float log1p(float _X) restrict(amp);

inline double log1p(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm base-e 1 plus argument

## <a name="log1pf"></a><a name="log1pf"></a>log1pf

Oblicza logarytm base-e 1 plus argument

```cpp
inline float log1pf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm base-e 1 plus argument

## <a name="log2"></a><a name="log2"></a>log2

Oblicza logarytm base-2 argumentu

```cpp
inline float log2(float _X) restrict(amp);

inline double log2(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm base-10 argumentu

## <a name="log2f"></a><a name="log2f"></a>log2f

Oblicza logarytm base-2 argumentu

```cpp
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm base-10 argumentu

## <a name="logb"></a><a name="logb"></a>logb (logb)

Wyodrębnia wykładnik _X, jako podpisaną wartość całkowitą w formacie zmiennoprzecinkowym

```cpp
inline float logb(float _X) restrict(amp);

inline double logb(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca podpisany wykładnik _X

## <a name="logbf"></a><a name="logbf"></a>logbf (logbf)

Wyodrębnia wykładnik _X, jako podpisaną wartość całkowitą w formacie zmiennoprzecinkowym

```cpp
inline float logbf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca podpisany wykładnik _X

## <a name="logf"></a><a name="logf"></a>logf (logf)

Oblicza logarytm base-e argumentu

```cpp
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm base-e argumentu

## <a name="modf"></a><a name="modf"></a>modf ( modf )

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

*_x*<br/>
Wartość zmiennoprzecinowa

*_Iptr*<br/>
[na zewnątrz] Część całkowita , `_X`jako wartość zmiennoprzecinkowa.

### <a name="return-value"></a>Wartość zwracana

Podpisana ułamkowa `_X`część .

## <a name="modff"></a><a name="modff"></a>modff ( modff )

Dzieli określony argument na części ułamkowe i całkowite.

```cpp
inline float modff(
    float _X,
    _Out_ float* _Iptr) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_Iptr*<br/>
Część całkowita , `_X`jako wartość zmiennoprzecinkowa.

### <a name="return-value"></a>Wartość zwracana

Zwraca podpisaną część `_X`ułamkową .

## <a name="nan"></a><a name="nan"></a>Nan

Zwraca cichą NaN

```cpp
inline double nan(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca cichą sieć NaN, jeśli jest dostępna, z zawartością wskazaną w _X

## <a name="nanf"></a><a name="nanf"></a>nanf

Zwraca cichą NaN

```cpp
inline float nanf(int _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca cichą sieć NaN, jeśli jest dostępna, z zawartością wskazaną w _X

## <a name="nearbyint"></a><a name="nearbyint"></a>w pobliżu

Zaokrągla argument do wartości całkowitej w formacie zmiennoprzecinkowym, używając bieżącego kierunku zaokrąglania.

```cpp
inline float nearbyint(float _X) restrict(amp);

inline double nearbyint(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca zaokrągloną wartość całkowitą.

## <a name="nearbyintf"></a><a name="nearbyintf"></a>w pobliżuintf

Zaokrągla argument do wartości całkowitej w formacie zmiennoprzecinkowym, używając bieżącego kierunku zaokrąglania.

```cpp
inline float nearbyintf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca zaokrągloną wartość całkowitą.

## <a name="nextafter"></a><a name="nextafter"></a>następna po

Określ następną wartość reprezentowalną, w typie funkcji, po _X w kierunku _Y

```cpp
inline float nextafter(
    float _X,
    float _Y) restrict(amp);

inline double nextafter(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_y*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca następną wartość reprezentowalną, w typie funkcji, po _X w kierunku _Y

## <a name="nextafterf"></a><a name="nextafterf"></a>następnypo

Określ następną wartość reprezentowalną, w typie funkcji, po _X w kierunku _Y

```cpp
inline float nextafterf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_y*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca następną wartość reprezentowalną, w typie funkcji, po _X w kierunku _Y

## <a name="phi"></a><a name="phi"></a>Phi

Zwraca skumulowaną funkcję rozkładu argumentu

```cpp
inline float phi(float _X) restrict(amp);

inline double phi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca skumulowaną funkcję rozkładu argumentu

## <a name="phif"></a><a name="phif"></a>phif ( phif )

Zwraca skumulowaną funkcję rozkładu argumentu

```cpp
inline float phif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca skumulowaną funkcję rozkładu argumentu

## <a name="pow"></a><a name="pow"></a>Pow

Oblicza _X podniesiony do potęgi _Y

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);

inline double pow(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinku, podstawa

*_y*<br/>
Wartość zmiennoprzecinku, wykładnik

### <a name="return-value"></a>Wartość zwracana

## <a name="powf"></a><a name="powf"></a>powf (powf)

Oblicza _X podniesiony do potęgi _Y

```cpp
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinku, podstawa

*_y*<br/>
Wartość zmiennoprzecinku, wykładnik

### <a name="return-value"></a>Wartość zwracana

## <a name="probit"></a><a name="probit"></a>probit

Zwraca odwrotną funkcję skumulowanego rozkładu argumentu

```cpp
inline float probit(float _X) restrict(amp);

inline double probit(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotną funkcję skumulowanego rozkładu argumentu

## <a name="probitf"></a><a name="probitf"></a>probitf

Zwraca odwrotną funkcję skumulowanego rozkładu argumentu

```cpp
inline float probitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotną funkcję skumulowanego rozkładu argumentu

## <a name="rcbrt"></a><a name="rcbrt"></a>rcbrt ( rcbrt )

Zwraca odwrotność katalogu głównego modułu argumentu

```cpp
inline float rcbrt(float _X) restrict(amp);

inline double rcbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotność katalogu głównego modułu argumentu

## <a name="rcbrtf"></a><a name="rcbrtf"></a>rcbrtf ( rcbrtf )

Zwraca odwrotność katalogu głównego modułu argumentu

```cpp
inline float rcbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotność katalogu głównego modułu argumentu

## <a name="remainder"></a><a name="remainder"></a>Pozostałą część

Oblicza pozostałą część: _X REM _Y

```cpp
inline float remainder(
    float _X,
    float _Y) restrict(amp);

inline double remainder(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_y*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca _X REM _Y

## <a name="remainderf"></a><a name="remainderf"></a>resekt

Oblicza pozostałą część: _X REM _Y

```cpp
inline float remainderf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_y*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca _X REM _Y

## <a name="remquo"></a><a name="remquo"></a>remquo

Oblicza pozostałą część pierwszego określonego argumentu podzielonego przez drugi określony argument. Oblicza również iloraz significand pierwszego określonego argumentu podzielonego przez oznaczenia i drugiego określonego argumentu i zwraca iloraz przy użyciu lokalizacji określonej w trzecim argum.

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

*_x*<br/>
Pierwszy argument zmiennoprzecinkowy.

*_y*<br/>
Drugi argument zmiennoprzecinowy.

*_Quo*<br/>
[na zewnątrz] Adres liczby całkowitej, która jest używana do zwracania ilorazu `_X` bitów ułamkowych podzielonych przez ułamkowe bity . `_Y`

### <a name="return-value"></a>Wartość zwracana

Zwraca pozostałą `_X` część `_Y`podzieloną przez .

## <a name="remquof"></a><a name="remquof"></a>remquof

Oblicza pozostałą część pierwszego określonego argumentu podzielonego przez drugi określony argument. Oblicza również iloraz significand pierwszego określonego argumentu podzielonego przez oznaczenia i drugiego określonego argumentu i zwraca iloraz przy użyciu lokalizacji określonej w trzecim argum.

```cpp
inline float remquof(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Pierwszy argument zmiennoprzecinkowy.

*_y*<br/>
Drugi argument zmiennoprzecinowy.

*_Quo*<br/>
[na zewnątrz] Adres liczby całkowitej, która jest używana do zwracania ilorazu `_X` bitów ułamkowych podzielonych przez ułamkowe bity . `_Y`

### <a name="return-value"></a>Wartość zwracana

Zwraca pozostałą `_X` część `_Y`podzieloną przez .

## <a name="round"></a><a name="round"></a>Okrągłe

Zaokrągla _X do najbliższej liczby całkowitej

```cpp
inline float round(float _X) restrict(amp);

inline double round(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca najbliższą liczbę całkowitą _X

## <a name="roundf"></a><a name="roundf"></a>zaokrąglony

Zaokrągla _X do najbliższej liczby całkowitej

```cpp
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca najbliższą liczbę całkowitą _X

## <a name="rsqrt"></a><a name="rsqrt"></a>rsqrt ( rsqrt )

Zwraca odwrotność pierwiastek kwadratowy argumentu

```cpp
inline float rsqrt(float _X) restrict(amp);

inline double rsqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotność pierwiastek kwadratowy argumentu

## <a name="rsqrtf"></a><a name="rsqrtf"></a>rsqrtf

Zwraca odwrotność pierwiastek kwadratowy argumentu

```cpp
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca odwrotność pierwiastek kwadratowy argumentu

## <a name="scalb"></a><a name="scalb"></a>scalb

Mnoży _X przez FLT_RADIX do _Y mocy

```cpp
inline float scalb(
    float _X,
    float _Y) restrict(amp);

inline double scalb(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_y*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca _X \* (FLT_RADIX ^ _Y)

## <a name="scalbf"></a><a name="scalbf"></a>scalbf (scalbf)

Mnoży _X przez FLT_RADIX do _Y mocy

```cpp
inline float scalbf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_y*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca _X \* (FLT_RADIX ^ _Y)

## <a name="scalbn"></a><a name="scalbn"></a>scalbn

Mnoży _X przez FLT_RADIX do _Y mocy

```cpp
inline float scalbn(
    float _X,
    int _Y) restrict(amp);

inline double scalbn(
    double _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_y*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca _X \* (FLT_RADIX ^ _Y)

## <a name="scalbnf"></a><a name="scalbnf"></a>scalbnf

Mnoży _X przez FLT_RADIX do _Y mocy

```cpp
inline float scalbnf(
    float _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_y*<br/>
Wartość całkowita

### <a name="return-value"></a>Wartość zwracana

Zwraca _X \* (FLT_RADIX ^ _Y)

## <a name="signbit"></a><a name="signbit"></a>signbit

Określa, czy znak _X jest ujemny

```cpp
inline int signbit(float _X) restrict(amp);

inline int signbit(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość niezerową, jeśli i tylko wtedy, gdy znak _X jest ujemny

## <a name="signbitf"></a><a name="signbitf"></a>signbitf

Określa, czy znak _X jest ujemny

```cpp
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość niezerową, jeśli i tylko wtedy, gdy znak _X jest ujemny

## <a name="sin"></a><a name="sin"></a>Grzechu

Oblicza wartość sinusoidy argumentu

```cpp
inline float sin(float _X) restrict(amp);

inline double sin(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość sinusoidy argumentu

## <a name="sinf"></a><a name="sinf"></a>Sinf

Oblicza wartość sinusoidy argumentu

```cpp
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość sinusoidy argumentu

## <a name="sincos"></a><a name="sincos"></a>sincos (sincos)

Oblicza sinusoidę i cosine wartość _X

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

*_x*<br/>
Wartość zmiennoprzecinowa

*_s*<br/>
Zwraca wartość sinusoidy _X

*_C*<br/>
Zwraca wartość cosine _X

## <a name="sincosf"></a><a name="sincosf"></a>sincosf ( sincosf )

Oblicza sinusoidę i cosine wartość _X

```cpp
inline void sincosf(
    float _X,
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_s*<br/>
Zwraca wartość sinusoidy _X

*_C*<br/>
Zwraca wartość cosine _X

## <a name="sinh"></a><a name="sinh"></a>Sinh

Oblicza wartość sinusoidy hiperbolicznej argumentu

```cpp
inline float sinh(float _X) restrict(amp);

inline double sinh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość sinusoidy hiperbolicznej argumentu

## <a name="sinhf"></a><a name="sinhf"></a>sinhf

Oblicza wartość sinusoidy hiperbolicznej argumentu

```cpp
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość sinusoidy hiperbolicznej argumentu

## <a name="sinpi"></a><a name="sinpi"></a>sinpi (sinpi)

Oblicza wartość sinusoidy pi \* _X

```cpp
inline float sinpi(float _X) restrict(amp);

inline double sinpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość sinusoidy pi \* _X

## <a name="sinpif"></a><a name="sinpif"></a>sinpif (sinpif)

Oblicza wartość sinusoidy pi \* _X

```cpp
inline float sinpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość sinusoidy pi \* _X

## <a name="sqrt"></a><a name="sqrt"></a>Sqrt

Oblicza pierwiastek squre argumentu

```cpp
inline float sqrt(float _X) restrict(amp);

inline double sqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca katalog główny squre argumentu

## <a name="sqrtf"></a><a name="sqrtf"></a>sqrtf (

Oblicza pierwiastek squre argumentu

```cpp
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca katalog główny squre argumentu

## <a name="tan"></a><a name="tan"></a>Tan

Oblicza wartość styczną argumentu

```cpp
inline float tan(float _X) restrict(amp);

inline double tan(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość styczną argumentu

## <a name="tanf"></a><a name="tanf"></a>tanf ( tanf )

Oblicza wartość styczną argumentu

```cpp
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość styczną argumentu

## <a name="tanh"></a><a name="tanh"></a>Tanh

Oblicza hiperboliczną wartość styczną argumentu

```cpp
inline float tanh(float _X) restrict(amp);

inline double tanh(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca hiperboliczną wartość styczną argumentu

## <a name="tanhf"></a><a name="tanhf"></a>tanhf ( tanhf )

Oblicza hiperboliczną wartość styczną argumentu

```cpp
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca hiperboliczną wartość styczną argumentu

## <a name="tanpi"></a><a name="tanpi"></a>tanpi ( tanpi )

Oblicza wartość styczną \* pi _X

```cpp
inline float tanpi(float _X) restrict(amp);

inline double tanpi(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość styczną \* pi _X

## <a name="tanpif"></a><a name="tanpif"></a>tanpif ( tanpif )

Oblicza wartość styczną \* pi _X

```cpp
inline float tanpif(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość styczną \* pi _X

## <a name="tgamma"></a><a name="tgamma"></a>tgamma ( tgamma )

Oblicza funkcję gamma _X

```cpp
inline float tgamma(float _X) restrict(amp);

inline double tgamma(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wynik funkcji gamma _X

## <a name="tgammaf"></a><a name="tgammaf"></a>tgammaf ( tgammaf )

Oblicza funkcję gamma _X

```cpp
inline float tgammaf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wynik funkcji gamma _X

## <a name="trunc"></a><a name="trunc"></a>Trunc

Obcina argument do składnika liczby całkowitej

```cpp
inline float trunc(float _X) restrict(amp);

inline double trunc(double _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca składnik liczby całkowitej argumentu

## <a name="truncf"></a><a name="truncf"></a>obcinanie

Obcina argument do składnika liczby całkowitej

```cpp
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca składnik liczby całkowitej argumentu

## <a name="see-also"></a>Zobacz też

[Współbieżność::prepreise_math Obszar nazw](concurrency-precise-math-namespace.md)
