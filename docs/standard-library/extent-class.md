---
title: extent — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::extent
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
ms.openlocfilehash: 0cd53ba8537e706a68ffdcf08df998108266ad20
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457792"
---
# <a name="extent-class"></a>extent — Klasa

Pobiera wymiar tablicy.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty, unsigned I = 0>
struct extent;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do zapytania.

*MAM*\
Tablica powiązana z kwerendą.

## <a name="remarks"></a>Uwagi

Jeśli *ty* jest typem tablicy, który ma co najmniej *I* wymiary, zapytanie typu przechowuje liczbę elementów w wymiarze określonym przez *i*. Jeśli *ty* nie jest typem tablicy lub jego rangą jest mniejsza niż *I*lub jeśli *i* jest zero i *ty* jest `U`typu "tablica nieznanej granicy", zapytanie typu utrzymuje wartość 0.

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

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md)\
[Klasa remove_all_extents](../standard-library/remove-all-extents-class.md)\
[remove_extent, klasa](../standard-library/remove-extent-class.md)
