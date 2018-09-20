---
title: CONCURRENCY::fast_math Namespace | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- amp_math/Concurrency::fast_math
dev_langs:
- C++
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd39e2057225aa09fd0bf0907e90abbf79b16172
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410289"
---
# <a name="concurrencyfastmath-namespace"></a>Concurrency::fast_math — Przestrzeń nazw

Funkcje w `fast_math` przestrzeni nazw są mniej dokładne, obsługują tylko pojedynczą precyzję (`float`) i wywoływać funkcje wewnętrzne DirectX. Istnieją dwie wersje każdej funkcji, na przykład `cos` i `cosf`. Obie wersje przyjmują i zwracają `float`, ale każda wywołuje sam DirectX wewnętrzne.

## <a name="syntax"></a>Składnia

```
namespace fast_math;
```

## <a name="members"></a>Elementy członkowskie

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[COS](concurrency-fast-math-namespace-functions.md#cos)|Oblicza arcus cosinus argumentu|
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|Oblicza arcus cosinus argumentu|
|[ASIN](concurrency-fast-math-namespace-functions.md#asin)|Oblicza arcus sinus argumentu|
|[asinf —](concurrency-fast-math-namespace-functions.md#asinf)|Oblicza arcus sinus argumentu|
|[atan](concurrency-fast-math-namespace-functions.md#atan)|Oblicza arcus tangens argumentu|
|[atan2](concurrency-fast-math-namespace-functions.md#atan2)|Oblicza arcus tangens dla _Y/_X|
|[atan2f](concurrency-fast-math-namespace-functions.md#atan2f)|Oblicza arcus tangens dla _Y/_X|
|[atanf](concurrency-fast-math-namespace-functions.md#atanf)|Oblicza arcus tangens argumentu|
|[Ceil —](concurrency-fast-math-namespace-functions.md#ceil)|Oblicza Zaokrąglenie w górę argumentu|
|[ceilf](concurrency-fast-math-namespace-functions.md#ceilf)|Oblicza Zaokrąglenie w górę argumentu|
|[COS](concurrency-fast-math-namespace-functions.md#cos)|Oblicza cosinus argumentu|
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|Oblicza cosinus argumentu|
|[COSH](concurrency-fast-math-namespace-functions.md#cosh)|Oblicza wartość funkcji cosinus hiperboliczny dla argumentu|
|[coshf](concurrency-fast-math-namespace-functions.md#coshf)|Oblicza wartość funkcji cosinus hiperboliczny dla argumentu|
|[EXP](concurrency-fast-math-namespace-functions.md#exp)|Oblicza eksponentę argumentu|
|[exp2](concurrency-fast-math-namespace-functions.md#exp2)|Oblicza base 2 wykładniczego argumentu|
|[exp2f](concurrency-fast-math-namespace-functions.md#exp2f)|Oblicza base 2 wykładniczego argumentu|
|[expf](concurrency-fast-math-namespace-functions.md#expf)|Oblicza eksponentę argumentu|
|[fabs —](concurrency-fast-math-namespace-functions.md#fabs)|Zwraca wartość bezwzględną argumentu|
|[fabsf —](concurrency-fast-math-namespace-functions.md#fabsf)|Zwraca wartość bezwzględną argumentu|
|[FLOOR](concurrency-fast-math-namespace-functions.md#floor)|Oblicza Zaokrąglenie w dół argumentu|
|[floorf](concurrency-fast-math-namespace-functions.md#floorf)|Oblicza Zaokrąglenie w dół argumentu|
|[fmax](concurrency-fast-math-namespace-functions.md#fmax)|Określić maksymalną wartość liczbową z podanych argumentów|
|[fmaxf](concurrency-fast-math-namespace-functions.md#fmaxf)|Określić maksymalną wartość liczbową z podanych argumentów|
|[fmin](concurrency-fast-math-namespace-functions.md#fmin)|Określić minimalną wartość liczbową z podanych argumentów|
|[fminf —](concurrency-fast-math-namespace-functions.md#fminf)|Określić minimalną wartość liczbową z podanych argumentów|
|[Fmod —](concurrency-fast-math-namespace-functions.md#fmod)|Oblicza zmiennoprzecinkową resztę działania _X/_Y|
|[fmodf](concurrency-fast-math-namespace-functions.md#fmodf)|Oblicza zmiennoprzecinkową resztę działania _X/_Y|
|[frexp](concurrency-fast-math-namespace-functions.md#frexp)|Pobiera mantysę i wykładnik _X|
|[frexpf](concurrency-fast-math-namespace-functions.md#frexpf)|Pobiera mantysę i wykładnik _X|
|[isfinite](concurrency-fast-math-namespace-functions.md#isfinite)|Określa, czy argument ma skończoną wartość|
|[isinf —](concurrency-fast-math-namespace-functions.md#isinf)|Określa, czy argument jest nieskończony|
|[isNaN —](concurrency-fast-math-namespace-functions.md#isnan)|Określa, czy argument jest NaN.|
|[ldexp](concurrency-fast-math-namespace-functions.md#ldexp)|Oblicza liczbę rzeczywistą z mantysy i wykładnika|
|[ldexpf](concurrency-fast-math-namespace-functions.md#ldexpf)|Oblicza liczbę rzeczywistą z mantysy i wykładnika|
|[log](concurrency-fast-math-namespace-functions.md#log)|Oblicza logarytm podstawa e argumentu|
|[log10](concurrency-fast-math-namespace-functions.md#log10)|Oblicza logarytm base 10 argumentu|
|[log10f](concurrency-fast-math-namespace-functions.md#log10f)|Oblicza logarytm base 10 argumentu|
|[log2](concurrency-fast-math-namespace-functions.md#log2)|Oblicza logarytm podstawie 2 dla podanego argumentu|
|[log2f](concurrency-fast-math-namespace-functions.md#log2f)|Oblicza logarytm podstawie 2 dla podanego argumentu|
|[logf](concurrency-fast-math-namespace-functions.md#logf)|Oblicza logarytm podstawa e argumentu|
|[modf](concurrency-fast-math-namespace-functions.md#modf)|Dzieli _X na ułamkową i całkowitą części.|
|[modff](concurrency-fast-math-namespace-functions.md#modff)|Dzieli _X na ułamkową i całkowitą części.|
|[Pow](concurrency-fast-math-namespace-functions.md#pow)|Oblicza _X podniesione do potęgi _y|
|[powf](concurrency-fast-math-namespace-functions.md#powf)|Oblicza _X podniesione do potęgi _y|
|[ROUND](concurrency-fast-math-namespace-functions.md#round)|Zaokrągla liczbę _X do najbliższej liczby całkowitej.|
|[roundf](concurrency-fast-math-namespace-functions.md#roundf)|Zaokrągla liczbę _X do najbliższej liczby całkowitej.|
|[rsqrt](concurrency-fast-math-namespace-functions.md#rsqrt)|Zwraca odwrotność pierwiastek kwadratowy argumentu|
|[rsqrtf](concurrency-fast-math-namespace-functions.md#rsqrtf)|Zwraca odwrotność pierwiastek kwadratowy argumentu|
|[signbit](concurrency-fast-math-namespace-functions.md#signbit)|Zwraca znak argumentu|
|[signbitf](concurrency-fast-math-namespace-functions.md#signbitf)|Zwraca znak argumentu|
|[SIN](concurrency-fast-math-namespace-functions.md#sin)|Oblicza wartość funkcji sinus argumentu|
|[sincos —](concurrency-fast-math-namespace-functions.md#sincos)|Oblicza wartość funkcji sinus i cosinus z _X|
|[sincosf](concurrency-fast-math-namespace-functions.md#sincosf)|Oblicza wartość funkcji sinus i cosinus z _X|
|[sinf](concurrency-fast-math-namespace-functions.md#sinf)|Oblicza wartość funkcji sinus argumentu|
|[SINH](concurrency-fast-math-namespace-functions.md#sinh)|Oblicza wartość funkcji sinus hiperboliczny dla argumentu|
|[sinhf](concurrency-fast-math-namespace-functions.md#sinhf)|Oblicza wartość funkcji sinus hiperboliczny dla argumentu|
|[sqrt](concurrency-fast-math-namespace-functions.md#sqrt)|Oblicza pierwiastek kwadratowy argumentu|
|[sqrtf](concurrency-fast-math-namespace-functions.md#sqrtf)|Oblicza pierwiastek kwadratowy argumentu|
|[tan](concurrency-fast-math-namespace-functions.md#tan)|Oblicza wartość funkcji tangens argumentu|
|[tanf —](concurrency-fast-math-namespace-functions.md#tanf)|Oblicza wartość funkcji tangens argumentu|
|[TANH](concurrency-fast-math-namespace-functions.md#tanh)|Oblicza wartość funkcji tangens hiperboliczny dla argumentu|
|[tanhf](concurrency-fast-math-namespace-functions.md#tanhf)|Oblicza wartość funkcji tangens hiperboliczny dla argumentu|
|[TRUNC —](concurrency-fast-math-namespace-functions.md#trunc)|Obcina argument do składnika całkowitego|
|[truncf](concurrency-fast-math-namespace-functions.md#truncf)|Obcina argument do składnika całkowitego|

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp_math.h

**Namespace:** Concurrency::fast_math

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
