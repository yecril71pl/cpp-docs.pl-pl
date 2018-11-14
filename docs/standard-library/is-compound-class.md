---
title: is_compound — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_compound
helpviewer_keywords:
- is_compound class
- is_compound
ms.assetid: bdad1167-cf3f-4f37-8321-62a5df159ead
ms.openlocfilehash: f270a1a58bb8023d91d84b0d1ca3395d36298c95
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523068"
---
# <a name="iscompound-class"></a>is_compound — Klasa

Sprawdza, czy określony typ nie jest podstawową.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_compound;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma **false** Jeśli typ *Ty* jest typem podstawowym (to znaczy, jeśli [is_fundamental —](../standard-library/is-fundamental-class.md)\<Ty > przechowuje  **wartość true,**); w przeciwnym razie przechowuje **true**. W związku z tym, zawiera predykat **true** Jeśli *Ty* jest typu tablicowego, typu funkcji, wskaźnik do **void** lub obiekt lub funkcję, a odwołanie, klasę, złożenia, wyliczenia lub w wskaźnik do składowej niestatycznych klas lub *kwalifikowana cv* postaci jednego z nich.

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

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_class, klasa](../standard-library/is-class-class.md)<br/>
