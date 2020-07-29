---
title: is_compound — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_compound
helpviewer_keywords:
- is_compound class
- is_compound
ms.assetid: bdad1167-cf3f-4f37-8321-62a5df159ead
ms.openlocfilehash: ae2e3c66b3abf22bbefbcb0fcd3292f0a3dbdbe2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215715"
---
# <a name="is_compound-class"></a>is_compound — Klasa

Testuje, czy określony typ nie jest podstawowy.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_compound;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu jest przechowywane, **`false`** Jeśli typ *ty* jest typem podstawowym (czyli jeśli [is_fundamental](../standard-library/is-fundamental-class.md) \<Ty> utrzymuje **`true`** ); w przeciwnym razie zawiera **`true`** . W związku z tym predykat zawiera, **`true`** Jeśli *ty* jest typem tablicy, typem funkcji, wskaźnikiem do **`void`** lub obiektem lub funkcją, odwołaniem, klasą, Unią, wyliczeniem lub wskaźnikiem do niestatycznego elementu członkowskiego klasy, lub z *kwalifikowaną* postacią CV jednego z nich.

## <a name="example"></a>Przykład

```cpp
// std__type_traits__is_compound.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_compound<trivial> == " << std::boolalpha
        << std::is_compound<trivial>::value << std::endl;
    std::cout << "is_compound<int[]> == " << std::boolalpha
        << std::is_compound<int[]>::value << std::endl;
    std::cout << "is_compound<int()> == " << std::boolalpha
        << std::is_compound<int()>::value << std::endl;
    std::cout << "is_compound<int&> == " << std::boolalpha
        << std::is_compound<int&>::value << std::endl;
    std::cout << "is_compound<void *> == " << std::boolalpha
        << std::is_compound<void *>::value << std::endl;
    std::cout << "is_compound<int> == " << std::boolalpha
        << std::is_compound<int>::value << std::endl;

    return (0);
    }
```

```Output
is_compound<trivial> == true
is_compound<int[]> == true
is_compound<int()> == true
is_compound<int&> == true
is_compound<void *> == true
is_compound<int> == false
```

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<type_traits>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)\
[Klasa is_class](../standard-library/is-class-class.md)
