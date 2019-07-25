---
title: is_compound — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_compound
helpviewer_keywords:
- is_compound class
- is_compound
ms.assetid: bdad1167-cf3f-4f37-8321-62a5df159ead
ms.openlocfilehash: 003ddcf77c30bc2dc5491218dfbf00731517bdeb
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452906"
---
# <a name="iscompound-class"></a>is_compound — Klasa

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

Wystąpienie predykatu typu ma **wartość false** , jeśli typ *ty* jest typem podstawowym (czyli jeśli [is_fundamental](../standard-library/is-fundamental-class.md)\<> ty ma **wartość true**); w przeciwnym razie **ma wartość true**. W związku z tym predykat ma **wartość true** , jeśli *ty* jest typem tablicy, typem funkcji, wskaźnikiem do **void** lub obiektem lub funkcją, odwołaniem, klasą, Unią, wyliczeniem lub wskaźnikiem do niestatycznego elementu członkowskiego klasy lub z kwalifikowaną postacią *CV* jeden z nich.

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

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md)\
[is_class, klasa](../standard-library/is-class-class.md)
