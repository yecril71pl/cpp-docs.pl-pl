---
title: output_iterator_tag — Struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::output_iterator_tag
helpviewer_keywords:
- output_iterator_tag class
- output_iterator_tag struct
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
ms.openlocfilehash: cb2a59d2c81e6d7cc80de2714ba86476c5fa837f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370856"
---
# <a name="outputiteratortag-struct"></a>output_iterator_tag — Struktura

Klasa udostępniająca typ zwracany dla `iterator_category` funkcja, która reprezentuje iterator wyjściowy.

## <a name="syntax"></a>Składnia

output_iterator_tag — struktura {};

## <a name="remarks"></a>Uwagi

Klasy tagów kategorii są używane, jak skompilować tagów dla algorytm wybór. Funkcja szablonu musi znaleźć najbardziej specyficzną kategorię jej argument iteratora, tak, aby możliwe było użycie algorytmu najbardziej wydajne w czasie kompilacji. Dla każdego iteratora typu `Iterator`, `iterator_traits` <  `Iterator` >  **:: iterator_category** muszą być zdefiniowane bardziej konkretny od pozostałych tag kategorii, który określa zachowanie iteratora.

Typ jest taki sam jak **iteratora** \< **Iter**> **:: iterator_category** podczas `Iter` opisuje obiekt, który może służyć jako iterator danych wyjściowych.

Ten tag nie jest parametryzowane na `value_type` lub `difference_type` dla iteratora, podobnie jak w przypadku innych tagów iteratora, ponieważ dane wyjściowe Iteratory albo nie ma `value_type` lub `difference_type`.

## <a name="example"></a>Przykład

Zobacz [iterator_traits —](../standard-library/iterator-traits-struct.md) lub [random_access_iterator_tag —](../standard-library/random-access-iterator-tag-struct.md) przykład sposobu użycia `iterator_tag`s.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<iterator >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
