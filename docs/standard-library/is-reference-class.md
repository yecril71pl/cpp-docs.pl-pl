---
title: is_reference — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_reference
helpviewer_keywords:
- is_reference class
- is_reference
ms.assetid: 3d9e631f-3092-430c-843e-e914ab58c257
ms.openlocfilehash: dd2d95e2c0bc20ac64b50e731122fda96c097de5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481994"
---
# <a name="isreference-class"></a>is_reference — Klasa

Sprawdza, czy typ to odwołanie.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_reference;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* jest odwołaniem do obiektu lub funkcji, w przeciwnym razie przechowuje wartość false.

## <a name="example"></a>Przykład

```cpp
// std__type_traits__is_reference.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_reference<trivial> == " << std::boolalpha
        << std::is_reference<trivial>::value << std::endl;
    std::cout << "is_reference<trivial&> == " << std::boolalpha
        << std::is_reference<trivial&>::value << std::endl;
    std::cout << "is_reference<int()> == " << std::boolalpha
        << std::is_reference<int()>::value << std::endl;
    std::cout << "is_reference<int(&)()> == " << std::boolalpha
        << std::is_reference<int(&)()>::value << std::endl;

    return (0);
    }

```

```Output
is_reference<trivial> == false
is_reference<trivial&> == true
is_reference<int()> == false
is_reference<int(&)()> == true
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_pointer, klasa](../standard-library/is-pointer-class.md)<br/>
