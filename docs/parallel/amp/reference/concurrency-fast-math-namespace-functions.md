---
title: "CONCURRENCY::fast_math — przestrzeń nazw funkcji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c9566468c2b9ba6447ce3a8ef2c09e4981edafef
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="concurrencyfastmath-namespace-functions"></a>CONCURRENCY::fast_math — przestrzeń nazw funkcji
||||  
|-|-|-|  
|[ACOS](#acos)|[acosf —](#acosf)|[ASIN](#asin)|  
|[asinf —](#asinf)|[ATAN](#atan)|[ATAN2](#atan2)|  
|[atan2f —](#atan2f)|[atanf —](#atanf)|[ceil](#ceil)|  
|[ceilf —](#ceilf)|[COS](#cos)|[cosf —](#cosf)|  
|[COSH](#cosh)|[coshf —](#coshf)|[EXP](#exp)|  
|[exp2 —](#exp2)|[exp2f —](#exp2f)|[expf —](#expf)|  
|[fabs —](#fabs)|[fabsf —](#fabsf)|[FLOOR](#floor)|  
|[floorf —](#floorf)|[Fmax](#fmax)|[fmaxf —](#fmaxf)|  
|[Fmin —](#fmin)|[fminf —](#fminf)|[fmod —](#fmod)|  
|[fmodf —](#fmodf)|[frexp —](#frexp)|[frexpf —](#frexpf)|  
|[isfinite](#isfinite)|[isinf —](#isinf)|[isNaN](#isnan)|  
|[ldexp —](#ldexp)|[ldexpf —](#ldexpf)|[Dziennik](#log)|  
|[LOG10](#log10)|[log10f —](#log10f)|[log2](#log2)|  
|[log2f —](#log2f)|[logf —](#logf)|[modf —](#modf)|  
|[modff —](#modff)|[Pow](#pow)|[powf —](#powf)|  
|[ROUND](#round)|[roundf —](#roundf)|[rsqrt —](#rsqrt)|  
|[rsqrtf —](#rsqrtf)|[signbit —](#signbit)|[signbitf —](#signbitf)|  
|[SIN](#sin)|[sincos —](#sincos)|[sincosf —](#sincosf)|  
|[sinf —](#sinf)|[SINH](#sinh)|[sinhf —](#sinhf)|  
|[SQRT](#sqrt)|[sqrtf —](#sqrtf)|[tan](#tan)|  
|[tanf —](#tanf)|[TANH](#tanh)|[tanhf —](#tanhf)|  
|[TRUNC —](#trunc)|[truncf —](#truncf)|  
  
##  <a name="acos"></a>ACOS  
 Oblicza cosinus argumentu  
  
```  
inline float acos(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca arcus cosinus wartość argumentu  
  
##  <a name="acosf"></a>acosf —  
 Oblicza cosinus argumentu  
  
```  
inline float acosf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca arcus cosinus wartość argumentu  
  
##  <a name="asin"></a>ASIN  
 Oblicza sinus argumentu  
  
```  
inline float asin(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca arcus sinus wartość argumentu  
  
##  <a name="asinf"></a>asinf —  
 Oblicza sinus argumentu  
  
```  
inline float asinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca arcus sinus wartość argumentu  
  
##  <a name="atan"></a>ATAN  
 Oblicza tangens argumentu  
  
```  
inline float atan(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca arcus tangens wartość argumentu  
  
##  <a name="atan2"></a>ATAN2  
 Oblicza tangens _Y/_X  
  
```  
inline float atan2(
    float _Y,  
    float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Y`  
 Wartość zmiennoprzecinkowa  
  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca arcus tangens wartość _Y/_X  
  
##  <a name="atan2f"></a>atan2f —  
 Oblicza tangens _Y/_X  
  
```  
inline float atan2f(
    float _Y,  
    float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Y`  
 Wartość zmiennoprzecinkowa  
  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca arcus tangens wartość _Y/_X  
  
##  <a name="atanf"></a>atanf —  
 Oblicza tangens argumentu  
  
```  
inline float atanf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca arcus tangens wartość argumentu  
  
##  <a name="ceil"></a>ceil  
 Oblicza Zaokrąglenie w górę argument  
  
```  
inline float ceil(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca limitu argumentu  
  
##  <a name="ceilf"></a>ceilf —  
 Oblicza Zaokrąglenie w górę argument  
  
```  
inline float ceilf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca limitu argumentu  
  
##  <a name="cosf"></a>cosf —  
 Oblicza cosinus argumentu  
  
```  
inline float cosf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca cosinus wartość argumentu  
  
##  <a name="coshf"></a>coshf —  
 Oblicza cosinus hiperboliczny wartość argumentu  
  
```  
inline float coshf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca cosinus hiperboliczny wartość argumentu  
  
##  <a name="cos"></a>COS  
 Oblicza cosinus argumentu  
  
```  
inline float cos(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca cosinus wartość argumentu  
  
##  <a name="cosh"></a>COSH  
 Oblicza cosinus hiperboliczny wartość argumentu  
  
```  
inline float cosh(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca cosinus hiperboliczny wartość argumentu  
  
##  <a name="exp"></a>EXP  
 Oblicza base e wykładniczej argumentu  
  
```  
inline float exp(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wykładniczej argumentu base-e  
  
##  <a name="exp2"></a>exp2 —  
 Oblicza base 2 wykładniczej argumentu  
  
```  
inline float exp2(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wykładniczej argumentu base-2  
  
##  <a name="exp2f"></a>exp2f —  
 Oblicza base 2 wykładniczej argumentu  
  
```  
inline float exp2f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wykładniczej argumentu base-2  
  
##  <a name="expf"></a>expf —  
 Oblicza base e wykładniczej argumentu  
  
```  
inline float expf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wykładniczej argumentu base-e  
  
##  <a name="fabs"></a>fabs —  
 Zwraca wartość bezwzględną argumentu  
  
```  
inline float fabs(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość całkowita  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość bezwzględną argumentu  
  
##  <a name="fabsf"></a>fabsf —  
 Zwraca wartość bezwzględną argumentu  
  
```  
inline float fabsf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość bezwzględną argumentu  
  
##  <a name="floor"></a>FLOOR  
 Oblicza Zaokrąglenie w dół argumentu  
  
```  
inline float floor(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca floor argumentu  
  
##  <a name="floorf"></a>floorf —  
 Oblicza Zaokrąglenie w dół argumentu  
  
```  
inline float floorf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca floor argumentu  
  
##  <a name="fmax"></a>Fmax  
 Określić maksymalną wartość liczbową argumentów  
  
```  
inline float max(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość całkowita  
  
 `_Y`  
 Wartość całkowita  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca maksymalną wartość liczbową argumentów  
  
##  <a name="fmaxf"></a>fmaxf —  
 Określić maksymalną wartość liczbową argumentów  
  
```  
inline float fmaxf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
 `_Y`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca maksymalną wartość liczbową argumentów  
  
##  <a name="fmin"></a>Fmin —  
 Określić minimalną wartość liczbową argumentów  
  
```  
inline float min(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość całkowita  
  
 `_Y`  
 Wartość całkowita  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca minimalną wartość liczbowa argumentów  
  
##  <a name="fminf"></a>fminf —  
 Określić minimalną wartość liczbową argumentów  
  
```  
inline float fminf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
 `_Y`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca minimalną wartość liczbowa argumentów  
  
##  <a name="fmod"></a>fmod —  
 Oblicza resztę zmiennoprzecinkowe z _X/_Y  
  
```  
inline float fmod(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
 `_Y`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zmiennoprzecinkowe pozostałej części _X/_Y  
  
##  <a name="fmodf"></a>fmodf —  
 Oblicza resztę zmiennoprzecinkowe z _X/_Y.  
  
```  
inline float fmodf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
 `_Y`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca zmiennoprzecinkowe pozostałej części _X/_Y  
  
##  <a name="frexp"></a>frexp —  
 Pobiera mantysa i wykładnik _X  
  
```  
inline float frexp(
    float _X,  
    _Out_ int* _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
 `_Exp`  
 Zwraca wykładnik całkowitą _X wartości zmiennoprzecinkowych  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca _X mantysy  
  
##  <a name="frexpf"></a>frexpf —  
 Pobiera mantysa i wykładnik _X  
  
```  
inline float frexpf(
    float _X,  
    _Out_ int* _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
 `_Exp`  
 Zwraca wykładnik całkowitą _X wartości zmiennoprzecinkowych  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca _X mantysy  
  
##  <a name="isfinite"></a>isfinite  
 Określa, czy argument ma wartością skończoną  
  
```  
inline int isfinite(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość niezerową tylko wtedy, gdy argument jest wartością skończoną  
  
##  <a name="isinf"></a>isinf —  
 Określa, czy argument jest nieskończoność.  
  
```  
inline int isinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość niezerową tylko wtedy, gdy argument ma wartość nieskończona  
  
##  <a name="isnan"></a>isNaN  
 Określa, czy argument jest wartością typu NaN  
  
```  
inline int isnan(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość niezerową tylko wtedy, gdy argument ma wartość NaN  
  
##  <a name="ldexp"></a>ldexp —  
 Oblicza liczba rzeczywista z mantysa i wykładnik  
  
```  
inline float ldexp(
    float _X,  
    int _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa mentissa  
  
 `_Exp`  
 Wykładnik liczba całkowita  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca _X * 2 ^ _Exp  
  
##  <a name="ldexpf"></a>ldexpf —  
 Oblicza liczba rzeczywista z mantysa i wykładnik  
  
```  
inline float ldexpf(
    float _X,  
    int _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa mentissa  
  
 `_Exp`  
 Wykładnik liczba całkowita  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca _X * 2 ^ _Exp  
  
##  <a name="log"></a>Dziennik  
 Oblicza logarytm naturalny argumentu  
  
```  
inline float log(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca logarytm naturalny argumentu  
  
##  <a name="log10"></a>LOG10  
 Oblicza logarytm base 10 argumentu  
  
```  
inline float log10(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca logarytm o podstawie base 10 argumentu  
  
##  <a name="log10f"></a>log10f —  
 Oblicza logarytm base 10 argumentu  
  
```  
inline float log10f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca logarytm o podstawie base 10 argumentu  
  
##  <a name="log2"></a>log2  
 Oblicza logarytm base-2 argumentu  
  
```  
inline float log2(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca logarytm base-2 argumentu  
  
##  <a name="log2f"></a>log2f —  
 Oblicza logarytm base-2 argumentu  
  
```  
inline float log2f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca logarytm o podstawie base 10 argumentu  
  
##  <a name="logf"></a>logf —  
 Oblicza logarytm naturalny argumentu  
  
```  
inline float logf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca logarytm naturalny argumentu  
  
##  <a name="modf"></a>modf —  
 Dzieli _X do ułamkowa i części liczby całkowitej.  
  
```  
inline float modf(
    float _X,  
    float* _Ip) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
 `_Ip`  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca podpisem części ułamkowej _X  
  
##  <a name="modff"></a>modff —  
 Dzieli _X do ułamkowa i części liczby całkowitej.  
  
```  
inline float modff(
    float _X,  
    float* _Ip) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
 `_Ip`  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca podpisem części ułamkowej _X  
  
##  <a name="pow"></a>Pow  
 Oblicza _X podniesionej do potęgi _Y  
  
```  
inline float pow(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa podstawowej  
  
 `_Y`  
 Wartość zmiennoprzecinkowa wykładnika  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość _X podniesionej do potęgi _Y  
  
##  <a name="powf"></a>powf —  
 Oblicza _X podniesionej do potęgi _Y  
  
```  
inline float powf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa podstawowej  
  
 `_Y`  
 Wartość zmiennoprzecinkowa wykładnika  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="round"></a>ROUND  
 Zaokrągla _X do najbliższej liczby całkowitej.  
  
```  
inline float round(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca najbliższej liczby całkowitej z _X  
  
##  <a name="roundf"></a>roundf —  
 Zaokrągla _X do najbliższej liczby całkowitej.  
  
```  
inline float roundf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca najbliższej liczby całkowitej z _X  
  
##  <a name="rsqrt"></a>rsqrt —  
 Zwraca odwrotność pierwiastek kwadratowy argumentu  
  
```  
inline float rsqrt(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwrotność pierwiastek kwadratowy argumentu  
  
##  <a name="rsqrtf"></a>rsqrtf —  
 Zwraca odwrotność pierwiastek kwadratowy argumentu  
  
```  
inline float rsqrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwrotność pierwiastek kwadratowy argumentu  
  
##  <a name="signbit"></a>signbit —  
 Określa, czy znak _X jest ujemna  
  
```  
inline int signbit(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość niezerową tylko wtedy, gdy znak _X jest ujemna.  
  
##  <a name="signbitf"></a>signbitf —  
 Określa, czy znak _X jest ujemna  
  
```  
inline int signbitf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość niezerową tylko wtedy, gdy znak _X jest ujemna.  
  
##  <a name="sin"></a>SIN  
 Oblicza sinus wartość argumentu  
  
```  
inline float sin(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca sinus wartość argumentu  
  
##  <a name="sinf"></a>sinf —  
 Oblicza sinus wartość argumentu  
  
```  
inline float sinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca sinus wartość argumentu  
  
##  <a name="sincos"></a>sincos —  
 Oblicza sinus i cosinus wartość _X  
  
```  
inline void sincos(
    float _X,  
    float* _S,  
    float* _C) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
 `_S`  
 Zwraca sinus wartość _X  
  
 `_C`  
 Zwraca cosinus wartość _X  
  
##  <a name="sincosf"></a>sincosf —  
 Oblicza sinus i cosinus wartość _X  
  
```  
inline void sincosf(
    float _X,  
    float* _S,  
    float* _C) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
 `_S`  
 Zwraca sinus wartość _X  
  
 `_C`  
 Zwraca cosinus wartość _X  
  
##  <a name="sinh"></a>SINH  
 Oblicza sinus hiperboliczny wartość argumentu  
  
```  
inline float sinh(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca sinus hiperboliczny wartość argumentu  
  
##  <a name="sinhf"></a>sinhf —  
 Oblicza sinus hiperboliczny wartość argumentu  
  
```  
inline float sinhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca sinus hiperboliczny wartość argumentu  
  
##  <a name="sqrt"></a>SQRT  
 Oblicza pierwiastek squre argumentu  
  
```  
inline float sqrt(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca pierwiastek squre argumentu  
  
##  <a name="sqrtf"></a>sqrtf —  
 Oblicza pierwiastek squre argumentu  
  
```  
inline float sqrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca pierwiastek squre argumentu  
  
##  <a name="tan"></a>tan  
 Oblicza tangens wartość argumentu  
  
```  
inline float tan(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca tangens wartość argumentu  
  
##  <a name="tanf"></a>tanf —  
 Oblicza tangens wartość argumentu  
  
```  
inline float tanf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca tangens wartość argumentu  
  
##  <a name="tanh"></a>TANH  
 Oblicza tangens hiperboliczny wartość argumentu  
  
```  
inline float tanh(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca tangens hiperboliczny wartość argumentu  
  
##  <a name="tanhf"></a>tanhf —  
 Oblicza tangens hiperboliczny wartość argumentu  
  
```  
inline float tanhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca tangens hiperboliczny wartość argumentu  
  
##  <a name="trunc"></a>TRUNC —  
 Obcina argument składnika liczba całkowita  
  
```  
inline float trunc(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę całkowitą argumentu  
  
##  <a name="truncf"></a>truncf —  
 Obcina argument składnika liczba całkowita  
  
```  
inline float truncf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę całkowitą argumentu  

## <a name="requirements"></a>Wymagania
**Nagłówek:** amp_math.h **Namespace:** CONCURRENCY::fast_math —
  
## <a name="see-also"></a>Zobacz też  
 [CONCURRENCY::fast_math — Namespace](concurrency-fast-math-namespace.md)
