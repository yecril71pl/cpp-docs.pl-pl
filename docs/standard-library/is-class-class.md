---
title: is_class — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_class
helpviewer_keywords:
- is_class class
- is_class
ms.assetid: 96fc34a3-a81b-4ec6-b7fb-baafde1a0f4e
ms.openlocfilehash: 4122ad2b4adbd0ed290f26428560c569b3754d7d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222449"
---
# <a name="is_class-class"></a>is_class — Klasa

Testuje, czy typ jest klasą.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_class;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *ty* jest typem zdefiniowanym w postaci lub lub postaci **`class`** **`struct`** `cv-qualified` jednego z nich, w przeciwnym razie ma wartość false.

## <a name="example"></a>Przykład

```cpp
// std__type_traits__is_class.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_class<trivial> == " << std::boolalpha
        << std::is_class<trivial>::value << std::endl;
    std::cout << "is_class<int> == " << std::boolalpha
        << std::is_class<int>::value << std::endl;

    return (0);
    }
```

```Output
is_class<trivial> == true
is_class<int> == false
```

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<type_traits>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)\
[Klasa is_compound](../standard-library/is-compound-class.md)\
[Klasa is_union](../standard-library/is-union-class.md)
