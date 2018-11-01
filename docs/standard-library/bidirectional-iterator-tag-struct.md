---
title: bidirectional_iterator_tag — Struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::bidirectional_iterator_tag
helpviewer_keywords:
- bidirectional_iterator_tag class
- bidirectional_iterator_tag struct
ms.assetid: 9ac06066-b8ae-44b6-bee4-b05855f6a31a
ms.openlocfilehash: c8296ddf30c0e2a3d34e69cbf079c0477e0e8b7a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661516"
---
# <a name="bidirectionaliteratortag-struct"></a>bidirectional_iterator_tag — Struktura

Klasa udostępniająca typ zwracany dla `iterator_category` funkcja, która reprezentuje iterator dwukierunkowy.

## <a name="syntax"></a>Składnia

```cpp
struct bidirectional_iterator_tag    : public forward_iterator_tag {};
```

## <a name="remarks"></a>Uwagi

Klasy tagów kategorii są używane, jak skompilować tagów dla algorytm wybór. Funkcja szablonu musi znaleźć najbardziej specyficzną kategorię argumentem iteratora tak, aby możliwe było użycie algorytmu najbardziej wydajne w czasie kompilacji. Dla każdego iteratora typu `Iterator`, `iterator_traits` <  `Iterator`>:: **iterator_category** muszą być zdefiniowane bardziej konkretny od pozostałych tag kategorii, który określa zachowanie iteratora.

Typ jest taki sam jak **iteratora** \< **Iter**>:: **iterator_category** podczas `Iter` opisuje obiekt, który może służyć jako dwukierunkowy Iterator.

## <a name="example"></a>Przykład

Zobacz [random_access_iterator_tag —](../standard-library/random-access-iterator-tag-struct.md) przykład sposobu użycia `bidirectional_iterator_tag`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<iterator >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[forward_iterator_tag, struktura](../standard-library/forward-iterator-tag-struct.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
