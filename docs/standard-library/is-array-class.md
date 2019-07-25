---
title: is_array — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_array
helpviewer_keywords:
- is_array class
- is_array
ms.assetid: 61fb2201-8de3-4746-9721-617f02df170f
ms.openlocfilehash: c54664ed5f56411929c60a0f15ae3c4f0e4581ce
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456659"
---
# <a name="isarray-class"></a>is_array — Klasa

Testuje, czy typ jest tablicą.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_array;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *ty* jest typem tablicy, w przeciwnym razie zawiera wartość false.

## <a name="example"></a>Przykład

```cpp
// std__type_traits__is_array.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_array<trivial> == " << std::boolalpha
        << std::is_array<trivial>::value << std::endl;
    std::cout << "is_array<int> == " << std::boolalpha
        << std::is_array<int>::value << std::endl;
    std::cout << "is_array<int[5]> == " << std::boolalpha
        << std::is_array<int[5]>::value << std::endl;

    return (0);
    }
```

```Output
is_array<trivial> == false
is_array<int> == false
is_array<int[5]> == true
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md)\
[Klasa zakresu](../standard-library/extent-class.md)\
[rank, klasa](../standard-library/rank-class.md)
