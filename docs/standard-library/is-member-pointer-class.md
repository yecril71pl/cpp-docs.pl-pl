---
title: is_member_pointer — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_member_pointer
helpviewer_keywords:
- is_member_pointer class
- is_member_pointer
ms.assetid: da07ff4e-9ee0-4baa-ad93-1741f10913d1
ms.openlocfilehash: f07e32c8ab1ea82a0c3616e96baca920a95e3042
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456135"
---
# <a name="ismemberpointer-class"></a>is_member_pointer — Klasa

Testuje, czy typ jest wskaźnikiem do elementu członkowskiego.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_member_pointer;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *ty* jest wskaźnikiem do funkcji składowej lub wskaźnikiem do obiektu elementu członkowskiego lub `cv-qualified` z jednym z nich, w przeciwnym razie ma wartość false.

## <a name="example"></a>Przykład

```cpp
// std__type_traits__is_member_pointer.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

struct functional
    {
    int f();
    };

int main()
    {
    std::cout << "is_member_pointer<trivial *> == "
        << std::boolalpha
        << std::is_member_pointer<trivial *>::value
        << std::endl;
    std::cout << "is_member_pointer<int trivial::*> == "
        << std::boolalpha
        << std::is_member_pointer<int trivial::*>::value
        << std::endl;
    std::cout << "is_member_pointer<int (functional::*)()> == "
        << std::boolalpha
        << std::is_member_pointer<int (functional::*)()>::value
        << std::endl;

    return (0);
    }
```

```Output
is_member_pointer<trivial *> == false
is_member_pointer<int trivial::*> == true
is_member_pointer<int (functional::*)()> == true
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md)\
[Klasa is_member_function_pointer](../standard-library/is-member-function-pointer-class.md)\
[is_member_object_pointer Class](../standard-library/is-member-object-pointer-class.md)\
[is_pointer, klasa](../standard-library/is-pointer-class.md)
