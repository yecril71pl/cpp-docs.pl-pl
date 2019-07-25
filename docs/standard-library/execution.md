---
title: '&lt;działania&gt;'
ms.date: 04/18/2019
f1_keywords:
- <execution>
- std::<execution>
helpviewer_keywords:
- execution header
ms.openlocfilehash: 3b0ccd540c56500c2f265aa6192a12fc2d5078b0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457966"
---
# <a name="ltexecutiongt"></a>&lt;działania&gt;

Opisuje zasady wykonywania dla algorytmów równoległych.

## <a name="syntax"></a>Składnia

```
namespace std {
    template<class T> inline constexpr bool is_execution_policy_v = is_execution_policy<T>::value;
}
namespace std::execution {
    inline constexpr sequenced_policy seq { unspecified };
    inline constexpr parallel_policy par { unspecified };
    inline constexpr parallel_unsequenced_policy par_unseq { unspecified };
}
```
### <a name="classes-and-structs"></a>Klasy i struktury

|||
|-|-|
|[is_execution_policy, struktura](is-execution-policy-struct.md)|Wykrywa zasady wykonywania w celu wykluczania podpisów funkcji ze względu na niejednoznaczny udział w rozpoznawaniu przeciążenia.|
|[Klasa parallel_policy](parallel-policy-class.md)|Używany jako unikatowy typ niejednoznacznego przeciążenia algorytmu równoległego i wskazujący, że wykonywanie algorytmu równoległego może być równoległe.|
|[Klasa parallel_unsequenced_policy](parallel-unsequenced-policy-class.md)|Używany jako unikatowy typ niejednoznacznego przeciążenia algorytmu równoległego i wskazujący, że wykonywanie algorytmu równoległego może być równoległe i wektorowe.|
|[Klasa sequenced_policy](sequenced-policy-class.md)|Używany jako unikatowy typ odróżnienia przeciążenia algorytmu równoległego i wymaganie, aby wykonywanie algorytmu równoległego mogło nie być równoległe.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> wykonywania

**Przestrzeń nazw:** stdext

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](cpp-standard-library-reference.md)
