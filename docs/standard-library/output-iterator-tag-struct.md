---
title: output_iterator_tag — Struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::output_iterator_tag
helpviewer_keywords:
- output_iterator_tag class
- output_iterator_tag struct
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
ms.openlocfilehash: 942e2214f42f97e262d4daf7836e8b6ced0e0ab2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453019"
---
# <a name="outputiteratortag-struct"></a>output_iterator_tag — Struktura

Klasa udostępniająca typ zwracany dla `iterator_category` funkcji, która reprezentuje iterator wyjściowy.

## <a name="syntax"></a>Składnia

output_iterator_tag {}struktury;

## <a name="remarks"></a>Uwagi

Klasy tagów kategorii są używane jako Tagi kompilacji do wyboru algorytmów. Funkcja szablonu musi znaleźć najbardziej specyficzną kategorię jego argumentu iteratora, aby można było używać najbardziej wydajnego algorytmu w czasie kompilacji. Dla każdego iteratora typu `Iterator`, `iterator_traits` < ::iterator_category musi być zdefiniowana jako najbardziej konkretny tag kategorii, który opisuje zachowanie iteratora.  `Iterator` > 

Typ jest taki sam jak **iterator** \< **ITER**>  **:: iterator_category** , gdy `Iter` opisuje obiekt, który może być używany jako iterator wyjściowy.

Ten tag nie jest sparametryzowany `value_type` na lub `difference_type` dla iteratora, podobnie jak w przypadku innych tagów iteratora, ponieważ Iteratory wyjściowe nie `difference_type`mają `value_type` albo lub.

## <a name="example"></a>Przykład

Zobacz [iterator_traits](../standard-library/iterator-traits-struct.md) lub [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) , aby zapoznać się z przykładem `iterator_tag`użycia usługi s.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> iteratora

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
