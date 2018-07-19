---
title: output_iterator_tag — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xutility/std::output_iterator_tag
dev_langs:
- C++
helpviewer_keywords:
- output_iterator_tag class
- output_iterator_tag struct
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6130a6de2504f2a625677ceaac00d23bdbcd9372
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961087"
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
