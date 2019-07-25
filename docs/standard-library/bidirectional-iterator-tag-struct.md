---
title: bidirectional_iterator_tag — Struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::bidirectional_iterator_tag
helpviewer_keywords:
- bidirectional_iterator_tag class
- bidirectional_iterator_tag struct
ms.assetid: 9ac06066-b8ae-44b6-bee4-b05855f6a31a
ms.openlocfilehash: bab2664fcb552a72baa032d719cf6b0141ffe525
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456634"
---
# <a name="bidirectionaliteratortag-struct"></a>bidirectional_iterator_tag — Struktura

Klasa udostępniająca typ zwracany dla `iterator_category` funkcji, która reprezentuje iterator dwukierunkowy.

## <a name="syntax"></a>Składnia

```cpp
struct bidirectional_iterator_tag    : public forward_iterator_tag {};
```

## <a name="remarks"></a>Uwagi

Klasy tagów kategorii są używane jako Tagi kompilacji do wyboru algorytmów. Funkcja szablonu musi znaleźć najbardziej specyficzną kategorię jego argumentu iteratora, tak aby można było użyć najbardziej wydajnego algorytmu w czasie kompilacji. Dla każdego iteratora typu `Iterator`, `iterator_traits` <  `Iterator`>:: **iterator_category** musi być zdefiniowana jako najbardziej konkretny tag kategorii, który opisuje zachowanie iteratora.

Typ jest taki sam jak **iterator** \< **ITER**>:: **iterator_category** , gdy `Iter` opisuje obiekt, który może być używany jako iterator dwukierunkowy.

## <a name="example"></a>Przykład

Zobacz [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) , aby zapoznać się z przykładem `bidirectional_iterator_tag`użycia.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> iteratora

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[forward_iterator_tag, struktura](../standard-library/forward-iterator-tag-struct.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
