---
title: forward_iterator_tag — Struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::forward_iterator_tag
helpviewer_keywords:
- forward_iterator_tag struct
- forward_iterator_tag class
ms.assetid: 68b633ac-b135-4e9e-837d-14248a262ec5
ms.openlocfilehash: 04d526e7778dc219a8d9a49db40751b4418cc82d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434258"
---
# <a name="forwarditeratortag-struct"></a>forward_iterator_tag — Struktura

Klasa udostępniająca typ zwracany dla **iterator_category** funkcja, która reprezentuje iterator do przodu.

## <a name="syntax"></a>Składnia

```cpp
struct forward_iterator_tag    : public input_iterator_tag {};
```

## <a name="remarks"></a>Uwagi

Klasy tagów kategorii są używane, jak skompilować tagów dla algorytm wybór. Funkcja szablonu wymaga dowiedzieć się, co to jest najbardziej specyficzną kategorię jej argument iteratora, tak, aby możliwe było użycie algorytmu najbardziej wydajne w czasie kompilacji. Dla każdego iteratora typu `Iterator`, `iterator_traits` <  `Iterator` >  **:: iterator_category** muszą być zdefiniowane bardziej konkretny od pozostałych tag kategorii, który określa zachowanie iteratora.

Typ jest taki sam jak **iteratora** \< **Iter**> **:: iterator_category** podczas **Iter** opisuje obiekt, który może służyć jako iterator do przodu.

## <a name="example"></a>Przykład

Zobacz [iterator_traits —](../standard-library/iterator-traits-struct.md) lub [random_access_iterator_tag —](../standard-library/random-access-iterator-tag-struct.md) przykład sposobu użycia **iterator_tag**s.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<iterator >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[input_iterator_tag, struktura](../standard-library/input-iterator-tag-struct.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
