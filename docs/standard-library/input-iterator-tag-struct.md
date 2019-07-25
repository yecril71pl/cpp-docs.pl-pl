---
title: input_iterator_tag — Struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::input_iterator_tag
helpviewer_keywords:
- input_iterator_tag class
- input_iterator_tag struct
ms.assetid: ad68a4c6-f315-4ce1-8b74-c1fc71bd1577
ms.openlocfilehash: 47e0d08f79cfa41c414ac4fcd570ce8fdfbd0b35
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455316"
---
# <a name="inputiteratortag-struct"></a>input_iterator_tag — Struktura

Klasa udostępniająca typ zwracany dla `iterator_category` funkcji, która reprezentuje iterator wejściowy.

## <a name="syntax"></a>Składnia

input_iterator_tag {}struktury;

## <a name="remarks"></a>Uwagi

Klasy tagów kategorii są używane jako Tagi kompilacji do wyboru algorytmów. Funkcja szablonu musi znaleźć najbardziej specyficzną kategorię jego argumentu iteratora, aby można było używać najbardziej wydajnego algorytmu w czasie kompilacji. Dla każdego iteratora typu `Iterator`, `iterator_traits` < ::iterator_category musi być zdefiniowana jako najbardziej konkretny tag kategorii, który opisuje zachowanie iteratora.  `Iterator` > 

Typ jest taki sam jak **iterator** \< **ITER**>  **:: iterator_category** , gdy `Iter` opisuje obiekt, który może być używany jako iterator wejściowy.

## <a name="example"></a>Przykład

Zobacz [iterator_traits](../standard-library/iterator-traits-struct.md) lub [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) , aby zapoznać się z przykładem `iterator_tag`użycia usługi s.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> iteratora

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
