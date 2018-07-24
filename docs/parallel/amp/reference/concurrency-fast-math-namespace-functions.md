---
title: CONCURRENCY::fast_math, funkcje przestrzeni nazw | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4fad0d6f5823a205490038755f9de4eef10eae8
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39208513"
---
# <a name="concurrencyfastmath-namespace-functions"></a>CONCURRENCY::fast_math, funkcje przestrzeni nazw
||||  
|-|-|-|  
|[ACOS](#acos)|[acosf](#acosf)|[ASIN](#asin)|  
|[asinf —](#asinf)|[atan](#atan)|[atan2](#atan2)|  
|[atan2f](#atan2f)|[atanf](#atanf)|[Ceil —](#ceil)|  
|[ceilf](#ceilf)|[COS](#cos)|[cosf](#cosf)|  
|[COSH](#cosh)|[coshf](#coshf)|[EXP](#exp)|  
|[exp2](#exp2)|[exp2f](#exp2f)|[expf](#expf)|  
|[fabs —](#fabs)|[fabsf —](#fabsf)|[FLOOR](#floor)|  
|[floorf](#floorf)|[fmax](#fmax)|[fmaxf](#fmaxf)|  
|[fmin](#fmin)|[fminf —](#fminf)|[Fmod —](#fmod)|  
|[fmodf](#fmodf)|[frexp](#frexp)|[frexpf](#frexpf)|  
|[isfinite](#isfinite)|[isinf —](#isinf)|[isNaN —](#isnan)|  
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[log](#log)|  
|[log10](#log10)|[log10f](#log10f)|[log2](#log2)|  
|[log2f](#log2f)|[logf](#logf)|[modf](#modf)|  
|[modff](#modff)|[Pow](#pow)|[powf](#powf)|  
|[ROUND](#round)|[roundf](#roundf)|[rsqrt](#rsqrt)|  
|[rsqrtf](#rsqrtf)|[signbit](#signbit)|[signbitf](#signbitf)|  
|[SIN](#sin)|[sincos —](#sincos)|[sincosf](#sincosf)|  
|[sinf](#sinf)|[SINH](#sinh)|[sinhf](#sinhf)|  
|[sqrt](#sqrt)|[sqrtf](#sqrtf)|[tan](#tan)|  
|[tanf —](#tanf)|[TANH](#tanh)|[tanhf](#tanhf)|  
|[TRUNC —](#trunc)|[truncf](#truncf)|  
  
##  <a name="acos"></a>  ACOS  
 Oblicza arcus cosinus argumentu  
  
```  
inline float acos(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość cosinus argumentu  
  
##  <a name="acosf"></a>  acosf —  
 Oblicza arcus cosinus argumentu  
  
```  
inline float acosf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość cosinus argumentu  
  
##  <a name="asin"></a>  ASIN  
 Oblicza arcus sinus argumentu  
  
```  
inline float asin(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość arcus sinus argumentu  
  
##  <a name="asinf"></a>  asinf —  
 Oblicza arcus sinus argumentu  
  
```  
inline float asinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość arcus sinus argumentu  
  
##  <a name="atan"></a>  ATAN  
 Oblicza arcus tangens argumentu  
  
```  
inline float atan(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość arcus tangens argumentu  
  
##  <a name="atan2"></a>  funkcja ATAN2  
 Oblicza arcus tangens dla _Y/_X  
  
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
 Zwraca wartość arcus tangens dla _Y/_X  
  
##  <a name="atan2f"></a>  atan2f —  
 Oblicza arcus tangens dla _Y/_X  
  
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
 Zwraca wartość arcus tangens dla _Y/_X  
  
##  <a name="atanf"></a>  atanf —  
 Oblicza arcus tangens argumentu  
  
```  
inline float atanf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość arcus tangens argumentu  
  
##  <a name="ceil"></a>  Ceil —  
 Oblicza Zaokrąglenie w górę argumentu  
  
```  
inline float ceil(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca limit argumentu  
  
##  <a name="ceilf"></a>  ceilf —  
 Oblicza Zaokrąglenie w górę argumentu  
  
```  
inline float ceilf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca limit argumentu  
  
##  <a name="cosf"></a>  cosf —  
 Oblicza cosinus argumentu  
  
```  
inline float cosf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość funkcji cosinus argumentu  
  
##  <a name="coshf"></a>  coshf —  
 Oblicza wartość funkcji cosinus hiperboliczny dla argumentu  
  
```  
inline float coshf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość funkcji cosinus hiperboliczny dla argumentu  
  
##  <a name="cos"></a>  COS  
 Oblicza cosinus argumentu  
  
```  
inline float cos(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość funkcji cosinus argumentu  
  
##  <a name="cosh"></a>  COSH  
 Oblicza wartość funkcji cosinus hiperboliczny dla argumentu  
  
```  
inline float cosh(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość funkcji cosinus hiperboliczny dla argumentu  
  
##  <a name="exp"></a>  EXP  
 Oblicza eksponentę argumentu  
  
```  
inline float exp(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca eksponentę argumentu  
  
##  <a name="exp2"></a>  exp2 —  
 Oblicza base 2 wykładniczego argumentu  
  
```  
inline float exp2(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca base 2 wykładniczego argumentu  
  
##  <a name="exp2f"></a>  exp2f —  
 Oblicza base 2 wykładniczego argumentu  
  
```  
inline float exp2f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca base 2 wykładniczego argumentu  
  
##  <a name="expf"></a>  expf —  
 Oblicza eksponentę argumentu  
  
```  
inline float expf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca eksponentę argumentu  
  
##  <a name="fabs"></a>  fabs —  
 Zwraca wartość bezwzględną argumentu  
  
```  
inline float fabs(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość całkowita  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość bezwzględną argumentu  
  
##  <a name="fabsf"></a>  fabsf —  
 Zwraca wartość bezwzględną argumentu  
  
```  
inline float fabsf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość bezwzględną argumentu  
  
##  <a name="floor"></a>  FLOOR  
 Oblicza Zaokrąglenie w dół argumentu  
  
```  
inline float floor(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca floor argumentu  
  
##  <a name="floorf"></a>  floorf —  
 Oblicza Zaokrąglenie w dół argumentu  
  
```  
inline float floorf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca floor argumentu  
  
##  <a name="fmax"></a>  Fmax —  
 Określić maksymalną wartość liczbową z podanych argumentów  
  
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
 Zwraca największą wartość liczbową z podanych argumentów  
  
##  <a name="fmaxf"></a>  fmaxf —  
 Określić maksymalną wartość liczbową z podanych argumentów  
  
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
 Zwraca największą wartość liczbową z podanych argumentów  
  
##  <a name="fmin"></a>  Fmin —  
 Określić minimalną wartość liczbową z podanych argumentów  
  
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
 Zwraca minimalną wartość liczbową argumentów  
  
##  <a name="fminf"></a>  fminf —  
 Określić minimalną wartość liczbową z podanych argumentów  
  
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
 Zwraca minimalną wartość liczbową argumentów  
  
##  <a name="fmod"></a>  Fmod —  
 Oblicza zmiennoprzecinkową resztę działania _X/_Y  
  
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
 Zwraca zmiennoprzecinkową resztę działania _X/_Y  
  
##  <a name="fmodf"></a>  fmodf —  
 Oblicza zmiennoprzecinkową resztę działania _X/_Y.  
  
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
 Zwraca zmiennoprzecinkową resztę działania _X/_Y  
  
##  <a name="frexp"></a>  frexp —  
 Pobiera mantysę i wykładnik _X  
  
```  
inline float frexp(
    float _X,  
    _Out_ int* _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
 `_Exp`  
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
 `_X`  
 Wartość zmiennoprzecinkowa  
  
 `_Exp`  
 Zwraca wartość zmiennoprzecinkową całkowitą wykładnik _X  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca _X mantysy  
  
##  <a name="isfinite"></a>  isfinite —  
 Określa, czy argument ma skończoną wartość  
  
```  
inline int isfinite(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość różną od zera, tylko wtedy, gdy argument ma skończoną wartość  
  
##  <a name="isinf"></a>  isinf —  
 Określa, czy argument jest nieskończony  
  
```  
inline int isinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość różną od zera, tylko wtedy, gdy argument ma wartość nieskończona  
  
##  <a name="isnan"></a>  isNaN —  
 Określa, czy argument jest NaN.  
  
```  
inline int isnan(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość różną od zera, tylko wtedy, gdy argument ma wartość NaN  
  
##  <a name="ldexp"></a>  ldexp —  
 Oblicza liczbę rzeczywistą z mantysy i wykładnika  
  
```  
inline float ldexp(
    float _X,  
    int _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa, mentissa  
  
 `_Exp`  
 Wykładnik potęgi liczby całkowitej  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca _X \* 2 ^ _Exp  
  
##  <a name="ldexpf"></a>  ldexpf —  
 Oblicza liczbę rzeczywistą z mantysy i wykładnika  
  
```  
inline float ldexpf(
    float _X,  
    int _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa, mentissa  
  
 `_Exp`  
 Wykładnik potęgi liczby całkowitej  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca _X \* 2 ^ _Exp  
  
##  <a name="log"></a>  Dziennik  
 Oblicza logarytm podstawa e argumentu  
  
```  
inline float log(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca logarytm o podstawie base e argumentu  
  
##  <a name="log10"></a>  LOG10  
 Oblicza logarytm base 10 argumentu  
  
```  
inline float log10(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca logarytm o podstawie base 10 argumentu  
  
##  <a name="log10f"></a>  log10f —  
 Oblicza logarytm base 10 argumentu  
  
```  
inline float log10f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca logarytm o podstawie base 10 argumentu  
  
##  <a name="log2"></a>  log2 —  
 Oblicza logarytm podstawie 2 dla podanego argumentu  
  
```  
inline float log2(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca logarytm o podstawie 2 dla podanego argumentu  
  
##  <a name="log2f"></a>  log2f —  
 Oblicza logarytm podstawie 2 dla podanego argumentu  
  
```  
inline float log2f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca logarytm o podstawie base 10 argumentu  
  
##  <a name="logf"></a>  logf —  
 Oblicza logarytm podstawa e argumentu  
  
```  
inline float logf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca logarytm o podstawie base e argumentu  
  
##  <a name="modf"></a>  modf —  
 Dzieli _X na ułamkową i całkowitą części.  
  
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
 Zwraca część ułamkową ze znakiem _X  
  
##  <a name="modff"></a>  modff —  
 Dzieli _X na ułamkową i całkowitą części.  
  
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
 Zwraca część ułamkową ze znakiem _X  
  
##  <a name="pow"></a>  Pow  
 Oblicza _X podniesione do potęgi _y  
  
```  
inline float pow(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa, podstawowy  
  
 `_Y`  
 Wartość zmiennoprzecinkowa, wykładnika  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość _X podniesione do potęgi _y  
  
##  <a name="powf"></a>  powf —  
 Oblicza _X podniesione do potęgi _y  
  
```  
inline float powf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa, podstawowy  
  
 `_Y`  
 Wartość zmiennoprzecinkowa, wykładnika  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="round"></a>  ROUND  
 Zaokrągla liczbę _X do najbliższej liczby całkowitej.  
  
```  
inline float round(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę całkowitą najbliższej _x  
  
##  <a name="roundf"></a>  roundf —  
 Zaokrągla liczbę _X do najbliższej liczby całkowitej.  
  
```  
inline float roundf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę całkowitą najbliższej _x  
  
##  <a name="rsqrt"></a>  rsqrt —  
 Zwraca odwrotność pierwiastek kwadratowy argumentu  
  
```  
inline float rsqrt(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwrotność pierwiastek kwadratowy argumentu  
  
##  <a name="rsqrtf"></a>  rsqrtf —  
 Zwraca odwrotność pierwiastek kwadratowy argumentu  
  
```  
inline float rsqrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwrotność pierwiastek kwadratowy argumentu  
  
##  <a name="signbit"></a>  signbit —  
 Określa, czy znak _X jest ujemna  
  
```  
inline int signbit(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość różną od zera, tylko wtedy, gdy znak _X jest ujemna  
  
##  <a name="signbitf"></a>  signbitf —  
 Określa, czy znak _X jest ujemna  
  
```  
inline int signbitf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość różną od zera, tylko wtedy, gdy znak _X jest ujemna  
  
##  <a name="sin"></a>  SIN  
 Oblicza wartość funkcji sinus argumentu  
  
```  
inline float sin(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość funkcji sinus argumentu  
  
##  <a name="sinf"></a>  sinf —  
 Oblicza wartość funkcji sinus argumentu  
  
```  
inline float sinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość funkcji sinus argumentu  
  
##  <a name="sincos"></a>  sincos —  
 Oblicza wartość funkcji sinus i cosinus z _X  
  
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
 Zwraca wartość funkcji sinus _X  
  
 `_C`  
 Zwraca wartość funkcji cosinus z _X  
  
##  <a name="sincosf"></a>  sincosf —  
 Oblicza wartość funkcji sinus i cosinus z _X  
  
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
 Zwraca wartość funkcji sinus _X  
  
 `_C`  
 Zwraca wartość funkcji cosinus z _X  
  
##  <a name="sinh"></a>  SINH  
 Oblicza wartość funkcji sinus hiperboliczny dla argumentu  
  
```  
inline float sinh(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca sinus hiperboliczny wartość argumentu  
  
##  <a name="sinhf"></a>  sinhf —  
 Oblicza wartość funkcji sinus hiperboliczny dla argumentu  
  
```  
inline float sinhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca sinus hiperboliczny wartość argumentu  
  
##  <a name="sqrt"></a>  SQRT  
 Oblicza squre kwadratowy argumentu  
  
```  
inline float sqrt(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca katalog główny squre argumentu  
  
##  <a name="sqrtf"></a>  sqrtf —  
 Oblicza squre kwadratowy argumentu  
  
```  
inline float sqrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca katalog główny squre argumentu  
  
##  <a name="tan"></a>  tan  
 Oblicza wartość funkcji tangens argumentu  
  
```  
inline float tan(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość funkcji tangens argumentu  
  
##  <a name="tanf"></a>  tanf —  
 Oblicza wartość funkcji tangens argumentu  
  
```  
inline float tanf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość funkcji tangens argumentu  
  
##  <a name="tanh"></a>  TANH  
 Oblicza wartość funkcji tangens hiperboliczny dla argumentu  
  
```  
inline float tanh(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość funkcji tangens hiperboliczny dla argumentu  
  
##  <a name="tanhf"></a>  tanhf —  
 Oblicza wartość funkcji tangens hiperboliczny dla argumentu  
  
```  
inline float tanhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość funkcji tangens hiperboliczny dla argumentu  
  
##  <a name="trunc"></a>  TRUNC —  
 Obcina argument do składnika całkowitego  
  
```  
inline float trunc(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę całkowitą argumentu  
  
##  <a name="truncf"></a>  truncf —  
 Obcina argument do składnika całkowitego  
  
```  
inline float truncf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_X`  
 Wartość zmiennoprzecinkowa  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę całkowitą argumentu  

## <a name="requirements"></a>Wymagania
**Nagłówek:** amp_math.h **Namespace:** Concurrency::fast_math
  
## <a name="see-also"></a>Zobacz też  
 [Concurrency::fast_math, przestrzeń nazw](concurrency-fast-math-namespace.md)
