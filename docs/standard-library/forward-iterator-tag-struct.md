---
title: forward_iterator_tag — Struktura
ms.date: 11/04/2016
f1_keywords:
- xutility/std::forward_iterator_tag
helpviewer_keywords:
- forward_iterator_tag struct
- forward_iterator_tag class
ms.assetid: 68b633ac-b135-4e9e-837d-14248a262ec5
ms.openlocfilehash: 687e39ce752bc0d4d289421887570dea6870f8f3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457117"
---
# <a name="forwarditeratortag-struct"></a>forward_iterator_tag — Struktura

Klasa udostępniająca typ zwracany dla funkcji **iterator_category** , która reprezentuje iterator do przodu.

## <a name="syntax"></a>Składnia

```cpp
struct forward_iterator_tag    : public input_iterator_tag {};
```

## <a name="remarks"></a>Uwagi

Klasy tagów kategorii są używane jako Tagi kompilacji do wyboru algorytmów. Funkcja szablonu musi dowiedzieć się, co jest najbardziej konkretną kategorią argumentu iteratora, tak aby można było użyć najbardziej wydajnego algorytmu w czasie kompilacji. Dla każdego iteratora typu `Iterator`, `iterator_traits` < ::iterator_category musi być zdefiniowana jako najbardziej konkretny tag kategorii, który opisuje zachowanie iteratora.  `Iterator` > 

Typ jest taki sam jak **iterator** \< **ITER**>  **:: iterator_category** , gdy **ITER** opisuje obiekt, który może być używany jako iterator do przodu.

## <a name="example"></a>Przykład

Zobacz [iterator_traits](../standard-library/iterator-traits-struct.md) lub [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) , aby zapoznać się z przykładem użycia **iterator_tag**s.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> iteratora

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[input_iterator_tag, struktura](../standard-library/input-iterator-tag-struct.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
