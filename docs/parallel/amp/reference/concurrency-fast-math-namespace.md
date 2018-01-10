---
title: "CONCURRENCY::fast_math — Namespace | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: amp_math/Concurrency::fast_math
dev_langs: C++
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 047eee60eb409e86d77faf6f637a88a56f271094
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="concurrencyfastmath-namespace"></a>Concurrency::fast_math — Przestrzeń nazw
Funkcje w `fast_math` przestrzeni nazw ma zmniejszenie dokładności, obsługuje tylko pojedynczej precyzji (`float`) i Wywołaj funkcje wewnętrzne DirectX. Dostępne są dwie wersje każdej funkcji, na przykład `cos` i `cosf`. Obie wersje przyjmować i zwracać `float`, a każdego wywołania tej samej technologii DirectX wewnętrznej.  
  
## <a name="syntax"></a>Składnia  
  
```  
namespace fast_math;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="functions"></a>Funkcje  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COS](concurrency-fast-math-namespace-functions.md#cos)|Oblicza cosinus argumentu|  
|[cosf —](concurrency-fast-math-namespace-functions.md#cosf)|Oblicza cosinus argumentu|  
|[ASIN](concurrency-fast-math-namespace-functions.md#asin)|Oblicza sinus argumentu|  
|[asinf —](concurrency-fast-math-namespace-functions.md#asinf)|Oblicza sinus argumentu|  
|[ATAN](concurrency-fast-math-namespace-functions.md#atan)|Oblicza tangens argumentu|  
|[ATAN2](concurrency-fast-math-namespace-functions.md#atan2)|Oblicza tangens _Y/_X|  
|[atan2f —](concurrency-fast-math-namespace-functions.md#atan2f)|Oblicza tangens _Y/_X|  
|[atanf —](concurrency-fast-math-namespace-functions.md#atanf)|Oblicza tangens argumentu|  
|[ceil](concurrency-fast-math-namespace-functions.md#ceil)|Oblicza Zaokrąglenie w górę argument|  
|[ceilf —](concurrency-fast-math-namespace-functions.md#ceilf)|Oblicza Zaokrąglenie w górę argument|  
|[COS](concurrency-fast-math-namespace-functions.md#cos)|Oblicza cosinus argumentu|  
|[cosf —](concurrency-fast-math-namespace-functions.md#cosf)|Oblicza cosinus argumentu|  
|[COSH](concurrency-fast-math-namespace-functions.md#cosh)|Oblicza cosinus hiperboliczny wartość argumentu|  
|[coshf —](concurrency-fast-math-namespace-functions.md#coshf)|Oblicza cosinus hiperboliczny wartość argumentu|  
|[EXP](concurrency-fast-math-namespace-functions.md#exp)|Oblicza base e wykładniczej argumentu|  
|[exp2 —](concurrency-fast-math-namespace-functions.md#exp2)|Oblicza base 2 wykładniczej argumentu|  
|[exp2f —](concurrency-fast-math-namespace-functions.md#exp2f)|Oblicza base 2 wykładniczej argumentu|  
|[expf —](concurrency-fast-math-namespace-functions.md#expf)|Oblicza base e wykładniczej argumentu|  
|[fabs —](concurrency-fast-math-namespace-functions.md#fabs)|Zwraca wartość bezwzględną argumentu|  
|[fabsf —](concurrency-fast-math-namespace-functions.md#fabsf)|Zwraca wartość bezwzględną argumentu|  
|[FLOOR](concurrency-fast-math-namespace-functions.md#floor)|Oblicza Zaokrąglenie w dół argumentu|  
|[floorf —](concurrency-fast-math-namespace-functions.md#floorf)|Oblicza Zaokrąglenie w dół argumentu|  
|[Fmax](concurrency-fast-math-namespace-functions.md#fmax)|Określić maksymalną wartość liczbową argumentów|  
|[fmaxf —](concurrency-fast-math-namespace-functions.md#fmaxf)|Określić maksymalną wartość liczbową argumentów|  
|[Fmin —](concurrency-fast-math-namespace-functions.md#fmin)|Określić minimalną wartość liczbową argumentów|  
|[fminf —](concurrency-fast-math-namespace-functions.md#fminf)|Określić minimalną wartość liczbową argumentów|  
|[fmod —](concurrency-fast-math-namespace-functions.md#fmod)|Oblicza resztę zmiennoprzecinkowe z _X/_Y|  
|[fmodf —](concurrency-fast-math-namespace-functions.md#fmodf)|Oblicza resztę zmiennoprzecinkowe z _X/_Y|  
|[frexp](concurrency-fast-math-namespace-functions.md#frexp)|Pobiera mantysa i wykładnik _X|  
|[frexpf —](concurrency-fast-math-namespace-functions.md#frexpf)|Pobiera mantysa i wykładnik _X|  
|[isfinite](concurrency-fast-math-namespace-functions.md#isfinite)|Określa, czy argument ma wartością skończoną|  
|[isinf —](concurrency-fast-math-namespace-functions.md#isinf)|Określa, czy argument jest nieskończoność.|  
|[isNaN](concurrency-fast-math-namespace-functions.md#isnan)|Określa, czy argument jest wartością typu NaN|  
|[ldexp](concurrency-fast-math-namespace-functions.md#ldexp)|Oblicza liczba rzeczywista z mantysa i wykładnik|  
|[ldexpf —](concurrency-fast-math-namespace-functions.md#ldexpf)|Oblicza liczba rzeczywista z mantysa i wykładnik|  
|[Dziennik](concurrency-fast-math-namespace-functions.md#log)|Oblicza logarytm naturalny argumentu|  
|[LOG10](concurrency-fast-math-namespace-functions.md#log10)|Oblicza logarytm base 10 argumentu|  
|[log10f —](concurrency-fast-math-namespace-functions.md#log10f)|Oblicza logarytm base 10 argumentu|  
|[log2](concurrency-fast-math-namespace-functions.md#log2)|Oblicza logarytm base-2 argumentu|  
|[log2f —](concurrency-fast-math-namespace-functions.md#log2f)|Oblicza logarytm base-2 argumentu|  
|[logf —](concurrency-fast-math-namespace-functions.md#logf)|Oblicza logarytm naturalny argumentu|  
|[modf —](concurrency-fast-math-namespace-functions.md#modf)|Dzieli _X do ułamkowa i części liczby całkowitej.|  
|[modff —](concurrency-fast-math-namespace-functions.md#modff)|Dzieli _X do ułamkowa i części liczby całkowitej.|  
|[Pow](concurrency-fast-math-namespace-functions.md#pow)|Oblicza _X podniesionej do potęgi _Y|  
|[powf —](concurrency-fast-math-namespace-functions.md#powf)|Oblicza _X podniesionej do potęgi _Y|  
|[ROUND](concurrency-fast-math-namespace-functions.md#round)|Zaokrągla _X do najbliższej liczby całkowitej.|  
|[roundf —](concurrency-fast-math-namespace-functions.md#roundf)|Zaokrągla _X do najbliższej liczby całkowitej.|  
|[rsqrt —](concurrency-fast-math-namespace-functions.md#rsqrt)|Zwraca odwrotność pierwiastek kwadratowy argumentu|  
|[rsqrtf —](concurrency-fast-math-namespace-functions.md#rsqrtf)|Zwraca odwrotność pierwiastek kwadratowy argumentu|  
|[signbit —](concurrency-fast-math-namespace-functions.md#signbit)|Zwraca znak argumentu|  
|[signbitf —](concurrency-fast-math-namespace-functions.md#signbitf)|Zwraca znak argumentu|  
|[SIN](concurrency-fast-math-namespace-functions.md#sin)|Oblicza sinus wartość argumentu|  
|[sincos —](concurrency-fast-math-namespace-functions.md#sincos)|Oblicza sinus i cosinus wartość _X|  
|[sincosf —](concurrency-fast-math-namespace-functions.md#sincosf)|Oblicza sinus i cosinus wartość _X|  
|[sinf —](concurrency-fast-math-namespace-functions.md#sinf)|Oblicza sinus wartość argumentu|  
|[SINH](concurrency-fast-math-namespace-functions.md#sinh)|Oblicza sinus hiperboliczny wartość argumentu|  
|[sinhf —](concurrency-fast-math-namespace-functions.md#sinhf)|Oblicza sinus hiperboliczny wartość argumentu|  
|[SQRT](concurrency-fast-math-namespace-functions.md#sqrt)|Oblicza pierwiastek kwadratowy argumentu|  
|[sqrtf —](concurrency-fast-math-namespace-functions.md#sqrtf)|Oblicza pierwiastek kwadratowy argumentu|  
|[tan](concurrency-fast-math-namespace-functions.md#tan)|Oblicza tangens wartość argumentu|  
|[tanf —](concurrency-fast-math-namespace-functions.md#tanf)|Oblicza tangens wartość argumentu|  
|[TANH](concurrency-fast-math-namespace-functions.md#tanh)|Oblicza tangens hiperboliczny wartość argumentu|  
|[tanhf —](concurrency-fast-math-namespace-functions.md#tanhf)|Oblicza tangens hiperboliczny wartość argumentu|  
|[TRUNC —](concurrency-fast-math-namespace-functions.md#trunc)|Obcina argument składnika liczba całkowita|  
|[truncf —](concurrency-fast-math-namespace-functions.md#truncf)|Obcina argument składnika liczba całkowita|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amp_math.h  
  
 **Namespace:** CONCURRENCY::fast_math —  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
