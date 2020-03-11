---
title: Concurrency::fast_math, funkcje przestrzeni nazw
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::fast_math::acos
- amp_math/Concurrency::fast_math::asin
- amp_math/Concurrency::fast_math::asinf
- amp_math/Concurrency::fast_math::atan2
- amp_math/Concurrency::fast_math::atan2f
- amp_math/Concurrency::fast_math::ceil
- amp_math/Concurrency::fast_math::ceilf
- amp_math/Concurrency::fast_math::cosf
- amp_math/Concurrency::fast_math::cosh
- amp_math/Concurrency::fast_math::exp
- amp_math/Concurrency::fast_math::exp2
- amp_math/Concurrency::fast_math::expf
- amp_math/Concurrency::fast_math::fabs
- amp_math/Concurrency::fast_math::floor
- amp_math/Concurrency::fast_math::floorf
- amp_math/Concurrency::fast_math::fmaxf
- amp_math/Concurrency::fast_math::fmin
- amp_math/Concurrency::fast_math::fmod
- amp_math/Concurrency::fast_math::fmodf
- amp_math/Concurrency::fast_math::frexpf
- amp_math/Concurrency::fast_math::isfinite
- amp_math/Concurrency::fast_math::isnan
- amp_math/Concurrency::fast_math::ldexp
- amp_math/Concurrency::fast_math::log
- amp_math/Concurrency::fast_math::log10
- amp_math/Concurrency::fast_math::log2
- amp_math/Concurrency::fast_math::log2f
- amp_math/Concurrency::fast_math::modf
- amp_math/Concurrency::fast_math::modff
- amp_math/Concurrency::fast_math::powf
- amp_math/Concurrency::fast_math::round
- amp_math/Concurrency::fast_math::rsqrt
- amp_math/Concurrency::fast_math::rsqrtf
- amp_math/Concurrency::fast_math::signbitf
- amp_math/Concurrency::fast_math::sin
- amp_math/Concurrency::fast_math::sincosf
- amp_math/Concurrency::fast_math::sinf
- amp_math/Concurrency::fast_math::sinhf
- amp_math/Concurrency::fast_math::sqrt
- amp_math/Concurrency::fast_math::tan
- amp_math/Concurrency::fast_math::tanf
- amp_math/Concurrency::fast_math::tanhf
- amp_math/Concurrency::fast_math::trunc
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
ms.openlocfilehash: 3652e02d9f3ff7b09ee7334dba20188e40344cb5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865473"
---
# <a name="concurrencyfast_math-namespace-functions"></a>Concurrency::fast_math, funkcje przestrzeni nazw

||||
|-|-|-|
|[Acos](#acos)|[acosf —](#acosf)|[Asin](#asin)|
|[asinf —](#asinf)|[atan](#atan)|[atan2](#atan2)|
|[atan2f —](#atan2f)|[atanf —](#atanf)|[CEIL —](#ceil)|
|[ceilf —](#ceilf)|[cosinus](#cos)|[cosf —](#cosf)|
|[cosh —](#cosh)|[coshf —](#coshf)|[EXP](#exp)|
|[exp2 —](#exp2)|[exp2f —](#exp2f)|[expf —](#expf)|
|[fabs —](#fabs)|[fabsf —](#fabsf)|[wykładzin](#floor)|
|[floorf —](#floorf)|[Fmax —](#fmax)|[fmaxf —](#fmaxf)|
|[fmin —](#fmin)|[fminf —](#fminf)|[FMOD —](#fmod)|
|[fmodf —](#fmodf)|[frexp](#frexp)|[frexpf —](#frexpf)|
|[isFinite](#isfinite)|[isinf](#isinf)|[isNaN](#isnan)|
|[ldexp](#ldexp)|[ldexpf —](#ldexpf)|[rejestrowane](#log)|
|[log10 —](#log10)|[log10f —](#log10f)|[log2 —](#log2)|
|[log2f —](#log2f)|[logf —](#logf)|[modf —](#modf)|
|[modff —](#modff)|[pow](#pow)|[powf —](#powf)|
|[Nit](#round)|[roundf —](#roundf)|[rsqrt —](#rsqrt)|
|[rsqrtf —](#rsqrtf)|[signbit](#signbit)|[signbitf —](#signbitf)|
|[sinus](#sin)|[SinCos —](#sincos)|[sincosf —](#sincosf)|
|[SINF —](#sinf)|[SINH](#sinh)|[sinhf —](#sinhf)|
|[sqrt](#sqrt)|[sqrtf —](#sqrtf)|[Tan](#tan)|
|[TANF —](#tanf)|[TANH —](#tanh)|[tanhf —](#tanhf)|
|[TRUNC —](#trunc)|[truncf —](#truncf)|

## <a name="acos"></a>Acos

Oblicza arcus cosinus argumentu

```cpp
inline float acos(float _X) restrict(amp);
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

## <a name="asin"></a>Asin

Oblicza arcus sinus argumentu

```cpp
inline float asin(float _X) restrict(amp);
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

## <a name="atan"></a>atan

Oblicza arcus tangens argumentu

```cpp
inline float atan(float _X) restrict(amp);
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

## <a name="ceil"></a>CEIL —

Oblicza górny limit argumentu

```cpp
inline float ceil(float _X) restrict(amp);
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

## <a name="cos"></a>cosinus

Oblicza cosinus argumentu

```cpp
inline float cos(float _X) restrict(amp);
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
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość cosinus hiperboliczny argumentu

## <a name="exp"></a>EXP

Oblicza wykładniczą wartość argumentu

```cpp
inline float exp(float _X) restrict(amp);
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

## <a name="fabs"></a>fabs —

Zwraca wartość bezwzględną argumentu.

```cpp
inline float fabs(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

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

## <a name="floor"></a>wykładzin

Oblicza piętro argumentu

```cpp
inline float floor(float _X) restrict(amp);
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

## <a name="fmax"></a>Fmax —

Określanie maksymalnej wartości liczbowej argumentów

```cpp
inline float max(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

*_Y*<br/>
Wartość całkowita

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
inline float min(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość całkowita

*_Y*<br/>
Wartość całkowita

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

## <a name="fmod"></a>FMOD —

Oblicza pozostałą liczbę zmiennoprzecinkową _X/_Y

```cpp
inline float fmod(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Y*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca pozostałą liczbę zmiennoprzecinkową _X/_Y

## <a name="fmodf"></a>fmodf —

Oblicza pozostałą liczbę zmiennoprzecinkową _X/_Y.

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Y*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca pozostałą liczbę zmiennoprzecinkową _X/_Y

## <a name="frexp"></a>frexp —

Pobiera mantysy i wykładnik _X

```cpp
inline float frexp(
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

## <a name="isfinite"></a>isFinite

Określa, czy argument ma skończoną wartość

```cpp
inline int isfinite(float _X) restrict(amp);
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
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość różną od zera, jeśli i tylko wtedy, gdy argument ma wartość NaN

## <a name="ldexp"></a>ldexp —

Oblicza liczbę rzeczywistą z mantysy i wykładnika

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa, mentissa

*_Exp*<br/>
Wykładnik wartości całkowitej

### <a name="return-value"></a>Wartość zwracana

Zwraca _X \* 2 ^ _Exp

## <a name="ldexpf"></a>ldexpf —

Oblicza liczbę rzeczywistą z mantysy i wykładnika

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa, mentissa

*_Exp*<br/>
Wykładnik wartości całkowitej

### <a name="return-value"></a>Wartość zwracana

Zwraca _X \* 2 ^ _Exp

## <a name="log"></a>rejestrowane

Oblicza logarytm dziesiętny argumentu

```cpp
inline float log(float _X) restrict(amp);
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

## <a name="log2"></a>log2 —

Oblicza logarytm dziesiętny argumentu

```cpp
inline float log2(float _X) restrict(amp);
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

Dzieli _X na części ułamkowe i całkowite.

```cpp
inline float modf(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Ip*<br/>
Odbiera część całkowitą wartości

### <a name="return-value"></a>Wartość zwracana

Zwraca podpisaną część ułamkową _X

## <a name="modff"></a>modff —

Dzieli _X na części ułamkowe i całkowite.

```cpp
inline float modff(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa

*_Ip*<br/>
Odbiera część całkowitą wartości

### <a name="return-value"></a>Wartość zwracana

Zwraca podpisaną część ułamkową _X

## <a name="pow"></a>pow

Oblicza _X podniesioną do potęgi _Y

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_X*<br/>
Wartość zmiennoprzecinkowa, podstawa

*_Y*<br/>
Wartość zmiennoprzecinkowa, wykładnik

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość _X podniesioną do potęgi _Y

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

## <a name="round"></a>Nit

Zaokrągla _X do najbliższej liczby całkowitej

```cpp
inline float round(float _X) restrict(amp);
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

## <a name="signbit"></a>signbit —

Określa, czy znak _X jest ujemny

```cpp
inline int signbit(float _X) restrict(amp);
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
    float* _S,
    float* _C) restrict(amp);
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
    float* _S,
    float* _C) restrict(amp);
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

## <a name="sqrt"></a>sqrt

Oblicza korzeń Squre argumentu

```cpp
inline float sqrt(float _X) restrict(amp);
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

## <a name="trunc"></a>TRUNC —

Obcina argument do składnika liczby całkowitej

```cpp
inline float trunc(float _X) restrict(amp);
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

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_math. h **przestrzeń nazw:** concurrency:: fast_math

## <a name="see-also"></a>Zobacz także

[Concurrency::fast_math, przestrzeń nazw](concurrency-fast-math-namespace.md)
