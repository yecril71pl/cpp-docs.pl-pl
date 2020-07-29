---
title: Concurrency::fast_math — Przestrzeń nazw
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::fast_math
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
ms.openlocfilehash: 6ed8dcfa2faff49e8811769b76aad9df15b2fe7b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226753"
---
# <a name="concurrencyfast_math-namespace"></a>Concurrency::fast_math — Przestrzeń nazw

Funkcje w `fast_math` przestrzeni nazw mają mniejszą dokładność, obsługują tylko jedną precyzję ( **`float`** ) i wywołują elementy wewnętrzne DirectX. Istnieją dwie wersje każdej funkcji, na przykład `cos` i `cosf` . Obie wersje pobierają i zwracają **`float`** , ale każdy wywołuje te same wewnętrzne środowiska DirectX.

## <a name="syntax"></a>Składnia

```cpp
namespace fast_math;
```

## <a name="members"></a>Elementy członkowskie

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[cosinus](concurrency-fast-math-namespace-functions.md#cos)|Oblicza arcus cosinus argumentu|
|[cosf —](concurrency-fast-math-namespace-functions.md#cosf)|Oblicza arcus cosinus argumentu|
|[Asin](concurrency-fast-math-namespace-functions.md#asin)|Oblicza arcus sinus argumentu|
|[asinf —](concurrency-fast-math-namespace-functions.md#asinf)|Oblicza arcus sinus argumentu|
|[atan](concurrency-fast-math-namespace-functions.md#atan)|Oblicza arcus tangens argumentu|
|[atan2](concurrency-fast-math-namespace-functions.md#atan2)|Oblicza arcus tangens _Y/_X|
|[atan2f —](concurrency-fast-math-namespace-functions.md#atan2f)|Oblicza arcus tangens _Y/_X|
|[atanf —](concurrency-fast-math-namespace-functions.md#atanf)|Oblicza arcus tangens argumentu|
|[CEIL —](concurrency-fast-math-namespace-functions.md#ceil)|Oblicza górny limit argumentu|
|[ceilf —](concurrency-fast-math-namespace-functions.md#ceilf)|Oblicza górny limit argumentu|
|[cosinus](concurrency-fast-math-namespace-functions.md#cos)|Oblicza cosinus argumentu|
|[cosf —](concurrency-fast-math-namespace-functions.md#cosf)|Oblicza cosinus argumentu|
|[cosh —](concurrency-fast-math-namespace-functions.md#cosh)|Oblicza wartość cosinus hiperboliczny argumentu|
|[coshf —](concurrency-fast-math-namespace-functions.md#coshf)|Oblicza wartość cosinus hiperboliczny argumentu|
|[EXP](concurrency-fast-math-namespace-functions.md#exp)|Oblicza wykładniczą wartość argumentu|
|[exp2 —](concurrency-fast-math-namespace-functions.md#exp2)|Oblicza wartość typu wykładniczego na podstawie 2 dla argumentu|
|[exp2f —](concurrency-fast-math-namespace-functions.md#exp2f)|Oblicza wartość typu wykładniczego na podstawie 2 dla argumentu|
|[expf —](concurrency-fast-math-namespace-functions.md#expf)|Oblicza wykładniczą wartość argumentu|
|[fabs —](concurrency-fast-math-namespace-functions.md#fabs)|Zwraca wartość bezwzględną argumentu.|
|[fabsf —](concurrency-fast-math-namespace-functions.md#fabsf)|Zwraca wartość bezwzględną argumentu.|
|[wykładzin](concurrency-fast-math-namespace-functions.md#floor)|Oblicza piętro argumentu|
|[floorf —](concurrency-fast-math-namespace-functions.md#floorf)|Oblicza piętro argumentu|
|[Fmax —](concurrency-fast-math-namespace-functions.md#fmax)|Określanie maksymalnej wartości liczbowej argumentów|
|[fmaxf —](concurrency-fast-math-namespace-functions.md#fmaxf)|Określanie maksymalnej wartości liczbowej argumentów|
|[fmin —](concurrency-fast-math-namespace-functions.md#fmin)|Określ minimalną wartość liczbową argumentów|
|[fminf —](concurrency-fast-math-namespace-functions.md#fminf)|Określ minimalną wartość liczbową argumentów|
|[FMOD —](concurrency-fast-math-namespace-functions.md#fmod)|Oblicza pozostałą liczbę zmiennoprzecinkową _X/_Y|
|[fmodf —](concurrency-fast-math-namespace-functions.md#fmodf)|Oblicza pozostałą liczbę zmiennoprzecinkową _X/_Y|
|[frexp](concurrency-fast-math-namespace-functions.md#frexp)|Pobiera mantysy i wykładnik _X|
|[frexpf —](concurrency-fast-math-namespace-functions.md#frexpf)|Pobiera mantysy i wykładnik _X|
|[isFinite](concurrency-fast-math-namespace-functions.md#isfinite)|Określa, czy argument ma skończoną wartość|
|[isinf](concurrency-fast-math-namespace-functions.md#isinf)|Określa, czy argument jest nieskończonością|
|[isNaN](concurrency-fast-math-namespace-functions.md#isnan)|Określa, czy argument jest NaN|
|[ldexp](concurrency-fast-math-namespace-functions.md#ldexp)|Oblicza liczbę rzeczywistą z mantysy i wykładnika|
|[ldexpf —](concurrency-fast-math-namespace-functions.md#ldexpf)|Oblicza liczbę rzeczywistą z mantysy i wykładnika|
|[rejestrowane](concurrency-fast-math-namespace-functions.md#log)|Oblicza logarytm dziesiętny argumentu|
|[log10 —](concurrency-fast-math-namespace-functions.md#log10)|Oblicza logarytm dziesiętny argumentu|
|[log10f —](concurrency-fast-math-namespace-functions.md#log10f)|Oblicza logarytm dziesiętny argumentu|
|[log2 —](concurrency-fast-math-namespace-functions.md#log2)|Oblicza logarytm dziesiętny argumentu|
|[log2f —](concurrency-fast-math-namespace-functions.md#log2f)|Oblicza logarytm dziesiętny argumentu|
|[logf —](concurrency-fast-math-namespace-functions.md#logf)|Oblicza logarytm dziesiętny argumentu|
|[modf —](concurrency-fast-math-namespace-functions.md#modf)|Dzieli _X na części ułamkowe i całkowite.|
|[modff —](concurrency-fast-math-namespace-functions.md#modff)|Dzieli _X na części ułamkowe i całkowite.|
|[pow](concurrency-fast-math-namespace-functions.md#pow)|Oblicza _X podniesioną do potęgi _Y|
|[powf —](concurrency-fast-math-namespace-functions.md#powf)|Oblicza _X podniesioną do potęgi _Y|
|[Nit](concurrency-fast-math-namespace-functions.md#round)|Zaokrągla _X do najbliższej liczby całkowitej|
|[roundf —](concurrency-fast-math-namespace-functions.md#roundf)|Zaokrągla _X do najbliższej liczby całkowitej|
|[rsqrt —](concurrency-fast-math-namespace-functions.md#rsqrt)|Zwraca odwrotność korzenia kwadratowego argumentu|
|[rsqrtf —](concurrency-fast-math-namespace-functions.md#rsqrtf)|Zwraca odwrotność korzenia kwadratowego argumentu|
|[signbit](concurrency-fast-math-namespace-functions.md#signbit)|Zwraca znak argumentu.|
|[signbitf —](concurrency-fast-math-namespace-functions.md#signbitf)|Zwraca znak argumentu.|
|[sinus](concurrency-fast-math-namespace-functions.md#sin)|Oblicza wartość sinusa argumentu|
|[SinCos —](concurrency-fast-math-namespace-functions.md#sincos)|Oblicza sinus i wartość cosinusa _X|
|[sincosf —](concurrency-fast-math-namespace-functions.md#sincosf)|Oblicza sinus i wartość cosinusa _X|
|[SINF —](concurrency-fast-math-namespace-functions.md#sinf)|Oblicza wartość sinusa argumentu|
|[SINH](concurrency-fast-math-namespace-functions.md#sinh)|Oblicza wartość sinus hiperboliczny argumentu|
|[sinhf —](concurrency-fast-math-namespace-functions.md#sinhf)|Oblicza wartość sinus hiperboliczny argumentu|
|[sqrt](concurrency-fast-math-namespace-functions.md#sqrt)|Oblicza pierwiastek kwadratowy argumentu|
|[sqrtf —](concurrency-fast-math-namespace-functions.md#sqrtf)|Oblicza pierwiastek kwadratowy argumentu|
|[Tan](concurrency-fast-math-namespace-functions.md#tan)|Oblicza wartość tangensa argumentu|
|[TANF —](concurrency-fast-math-namespace-functions.md#tanf)|Oblicza wartość tangensa argumentu|
|[TANH —](concurrency-fast-math-namespace-functions.md#tanh)|Oblicza wartość tangensa hiperbolicznego argumentu|
|[tanhf —](concurrency-fast-math-namespace-functions.md#tanhf)|Oblicza wartość tangensa hiperbolicznego argumentu|
|[TRUNC —](concurrency-fast-math-namespace-functions.md#trunc)|Obcina argument do składnika liczby całkowitej|
|[truncf —](concurrency-fast-math-namespace-functions.md#truncf)|Obcina argument do składnika liczby całkowitej|

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_math. h

**Przestrzeń nazw:** Concurrency:: fast_math

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
