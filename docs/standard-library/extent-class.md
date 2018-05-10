---
title: Extent — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::extent
dev_langs:
- C++
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7fb721b23f473c59051e72edc969e5de38f1c984
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="extent-class"></a>extent — Klasa

Pobiera wymiaru tablicy.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty, unsigned I = 0>
struct extent;
```

### <a name="parameters"></a>Parametry

`Ty` Typ do zapytania.

`I` Tablica jest powiązana z zapytania.

## <a name="remarks"></a>Uwagi

Jeśli `Ty` jest typem tablicy, która ma co najmniej `I` wymiarów, zapytania typu zawiera liczbę elementów w wymiarze określony przez `I`. Jeśli `Ty` nie jest typem tablicowym lub jego pozycja jest mniejsza niż `I`, lub, jeśli `I` wynosi zero i `Ty` jest typu "granica tablicy nieznany `U`", zapytanie typu ma wartość 0.

## <a name="example"></a>Przykład

```cpp
// std__type_traits__extent.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "extent 0 == "
        << std::extent<int[5][10]>::value << std::endl;
    std::cout << "extent 1 == "
        << std::extent<int[5][10], 1>::value << std::endl;

    return (0);
    }

```

```Output
extent 0 == 5
extent 1 == 10
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_all_extents, klasa](../standard-library/remove-all-extents-class.md)<br/>
[remove_extent, klasa](../standard-library/remove-extent-class.md)<br/>
