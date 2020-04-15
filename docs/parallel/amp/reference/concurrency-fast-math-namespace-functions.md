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
ms.openlocfilehash: cd0882b072cfe26cd83e63024ae6837dc962ebf9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376394"
---
# <a name="concurrencyfast_math-namespace-functions"></a>Concurrency::fast_math, funkcje przestrzeni nazw

||||
|-|-|-|
|[Acos](#acos)|[acosf ( acosf )](#acosf)|[Asin](#asin)|
|[asinf](#asinf)|[Atan](#atan)|[atan2 (atan2)](#atan2)|
|[atan2f](#atan2f)|[atanf ( atanf )](#atanf)|[Ceil](#ceil)|
|[ceilf](#ceilf)|[cos](#cos)|[cosf ( cosf )](#cosf)|
|[Cosh](#cosh)|[coshf ( coshf )](#coshf)|[Exp](#exp)|
|[exp2](#exp2)|[exp2f](#exp2f)|[expf (wycho.](#expf)|
|[Fabs](#fabs)|[fabsf ( fabsf )](#fabsf)|[Podłogi](#floor)|
|[podłoga](#floorf)|[fmax ( fmax )](#fmax)|[fmaxf ( fmaxf )](#fmaxf)|
|[fmin ( fmin )](#fmin)|[fminf (fminf)](#fminf)|[Fmod](#fmod)|
|[fmodf ( fmodf )](#fmodf)|[frexp](#frexp)|[frexpf](#frexpf)|
|[isfinite](#isfinite)|[isinf](#isinf)|[Isnan (isnan)](#isnan)|
|[ldexp](#ldexp)|[ldexpf ( ldexpf )](#ldexpf)|[Dziennika](#log)|
|[log10](#log10)|[log10f](#log10f)|[log2](#log2)|
|[log2f](#log2f)|[logf (logf)](#logf)|[modf ( modf )](#modf)|
|[modff ( modff )](#modff)|[Pow](#pow)|[powf (powf)](#powf)|
|[Okrągłe](#round)|[zaokrąglony](#roundf)|[rsqrt ( rsqrt )](#rsqrt)|
|[rsqrtf](#rsqrtf)|[signbit](#signbit)|[signbitf](#signbitf)|
|[Grzechu](#sin)|[sincos (sincos)](#sincos)|[sincosf ( sincosf )](#sincosf)|
|[Sinf](#sinf)|[Sinh](#sinh)|[sinhf](#sinhf)|
|[Sqrt](#sqrt)|[sqrtf (](#sqrtf)|[Tan](#tan)|
|[tanf ( tanf )](#tanf)|[Tanh](#tanh)|[tanhf ( tanhf )](#tanhf)|
|[Trunc](#trunc)|[obcinanie](#truncf)|

## <a name="acos"></a><a name="acos"></a>Acos

Oblicza arccosine argumentu

```cpp
inline float acos(float _X) restrict(amp);
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

## <a name="asin"></a><a name="asin"></a>Asin

Oblicza łuk argumentu

```cpp
inline float asin(float _X) restrict(amp);
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

## <a name="atan"></a><a name="atan"></a>Atan

Oblicza arctangent argumentu

```cpp
inline float atan(float _X) restrict(amp);
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

## <a name="ceil"></a><a name="ceil"></a>Ceil

Oblicza pułap argumentu

```cpp
inline float ceil(float _X) restrict(amp);
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

## <a name="cos"></a><a name="cos"></a>cos

Oblicza cosine argumentu

```cpp
inline float cos(float _X) restrict(amp);
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
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość cosine hiperbolicznej argumentu

## <a name="exp"></a><a name="exp"></a>Exp

Oblicza wykładniczą bazę e argumentu

```cpp
inline float exp(float _X) restrict(amp);
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

## <a name="fabs"></a><a name="fabs"></a>Fabs

Zwraca wartość bezwzględną argumentu

```cpp
inline float fabs(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość całkowita

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

## <a name="floor"></a><a name="floor"></a>Podłogi

Oblicza podłogę argumentu

```cpp
inline float floor(float _X) restrict(amp);
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

## <a name="fmax"></a><a name="fmax"></a>fmax ( fmax )

Określanie maksymalnej wartości liczbowej argumentów

```cpp
inline float max(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość całkowita

*_y*<br/>
Wartość całkowita

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
inline float min(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość całkowita

*_y*<br/>
Wartość całkowita

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

## <a name="fmod"></a><a name="fmod"></a>Fmod

Oblicza pozostałą część zmiennoprzecinkową _X/_Y

```cpp
inline float fmod(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_y*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca pozostałą część punktu zmiennoprzecinkowego _X/_Y

## <a name="fmodf"></a><a name="fmodf"></a>fmodf ( fmodf )

Oblicza pozostałą część zmiennoprzecinkową _X/_Y.

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_y*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca pozostałą część punktu zmiennoprzecinkowego _X/_Y

## <a name="frexp"></a><a name="frexp"></a>frexp ( frexp )

Pobiera mantysi i wykładnika _X

```cpp
inline float frexp(
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

## <a name="isfinite"></a><a name="isfinite"></a>isfinite

Określa, czy argument ma wartość skończoną

```cpp
inline int isfinite(float _X) restrict(amp);
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
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość niezerową, jeśli i tylko wtedy, gdy argument ma wartość NaN

## <a name="ldexp"></a><a name="ldexp"></a>ldexp

Oblicza rzeczywistą liczbę z mantysi i wykładnika

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinku, mentissa

*_Exp*<br/>
Wykładnik liczby całkowitej

### <a name="return-value"></a>Wartość zwracana

Zwraca _X \* 2^_Exp

## <a name="ldexpf"></a><a name="ldexpf"></a>ldexpf ( ldexpf )

Oblicza rzeczywistą liczbę z mantysi i wykładnika

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinku, mentissa

*_Exp*<br/>
Wykładnik liczby całkowitej

### <a name="return-value"></a>Wartość zwracana

Zwraca _X \* 2^_Exp

## <a name="log"></a><a name="log"></a>Dziennika

Oblicza logarytm base-e argumentu

```cpp
inline float log(float _X) restrict(amp);
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

## <a name="log2"></a><a name="log2"></a>log2

Oblicza logarytm base-2 argumentu

```cpp
inline float log2(float _X) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

### <a name="return-value"></a>Wartość zwracana

Zwraca logarytm base-2 argumentu

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

Dzieli _X na części ułamkowe i całkowite.

```cpp
inline float modf(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_Ip*<br/>
Odbiera część całkowitą wartości

### <a name="return-value"></a>Wartość zwracana

Zwraca podpisaną ułamkową część _X

## <a name="modff"></a><a name="modff"></a>modff ( modff )

Dzieli _X na części ułamkowe i całkowite.

```cpp
inline float modff(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinowa

*_Ip*<br/>
Odbiera część całkowitą wartości

### <a name="return-value"></a>Wartość zwracana

Zwraca podpisaną ułamkową część _X

## <a name="pow"></a><a name="pow"></a>Pow

Oblicza _X podniesiony do potęgi _Y

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_x*<br/>
Wartość zmiennoprzecinku, podstawa

*_y*<br/>
Wartość zmiennoprzecinku, wykładnik

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość _X podniesiona do potęgi _Y

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

## <a name="round"></a><a name="round"></a>Okrągłe

Zaokrągla _X do najbliższej liczby całkowitej

```cpp
inline float round(float _X) restrict(amp);
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

## <a name="signbit"></a><a name="signbit"></a>signbit

Określa, czy znak _X jest ujemny

```cpp
inline int signbit(float _X) restrict(amp);
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
    float* _S,
    float* _C) restrict(amp);
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
    float* _S,
    float* _C) restrict(amp);
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

## <a name="sqrt"></a><a name="sqrt"></a>Sqrt

Oblicza pierwiastek squre argumentu

```cpp
inline float sqrt(float _X) restrict(amp);
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

## <a name="trunc"></a><a name="trunc"></a>Trunc

Obcina argument do składnika liczby całkowitej

```cpp
inline float trunc(float _X) restrict(amp);
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

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_math.h **Obszar nazw:** Współbieżność::fast_math

## <a name="see-also"></a>Zobacz też

[Concurrency::fast_math, przestrzeń nazw](concurrency-fast-math-namespace.md)
