---
title: '&lt;Wykonanie&gt;'
ms.date: 04/18/2019
f1_keywords:
- <execution>
- std::<execution>
helpviewer_keywords:
- execution header
ms.openlocfilehash: 3bce34019f9ed4880d72a9d16c3c8b78dde0e0e3
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267881"
---
# <a name="ltexecutiongt"></a>&lt;Wykonanie&gt;

W tym artykule opisano zasady wykonywania równoległych algorytmów.

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
|[is_execution_policy — struktura](is-execution-policy-struct.md)|Wykrywa zasad wykonywania na potrzeby sygnatury funkcji z wyjątkiem z udziału rozpoznawania przeciążenie inaczej niejednoznaczne.|
|[parallel_policy klasy](parallel-policy-class.md)|Używany jako unikatowy typ, do odróżniania przeciążenie algorytmu równoległego i wskazują, że wykonywanie algorytmu równoległego może odbywać się równolegle.|
|[parallel_unsequenced_policy klasy](parallel-unsequenced-policy-class.md)|Używany jako unikatowy typ, do odróżniania przeciążenie algorytmu równoległego i wskazywać, że algorytmu równoległego wykonywania może być zrównoleglona i zwektoryzowana.|
|[sequenced_policy klasy](sequenced-policy-class.md)|Używane jako typ unikatowy odróżnić przeciążenie algorytmu równoległego, i wymagają, że algorytmu równoległego wykonywania może nie być przetwarzane równolegle.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wykonywania >

**Namespace:** stdext

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](cpp-standard-library-reference.md)
