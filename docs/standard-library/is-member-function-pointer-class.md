---
title: is_member_function_pointer — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_member_function_pointer
helpviewer_keywords:
- is_member_function_pointer class
- is_member_function_pointer
ms.assetid: 02e372c4-2714-40f2-b376-2e10ca91c8ed
ms.openlocfilehash: 0eb758977abf889a7d5ec8cdec9213980493ba2e
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521729"
---
# <a name="ismemberfunctionpointer-class"></a>is_member_function_pointer — Klasa

Sprawdza, czy typ jest wskaźnikiem do funkcji członkowskiej.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_member_function_pointer;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* jest wskaźnikiem do funkcji składowej lub `cv-qualified` wskaźnik do elementu członkowskiego funkcji, w przeciwnym razie przechowuje wartość false.

## <a name="example"></a>Przykład

```cpp
// std__type_traits__is_member_function_pointer.cpp
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
    std::cout << "is_member_function_pointer<trivial *> == "
        << std::boolalpha
        << std::is_member_function_pointer<trivial *>::value
        << std::endl;
    std::cout << "is_member_function_pointer<int trivial::*> == "
        << std::boolalpha
        << std::is_member_function_pointer<int trivial::*>::value
        << std::endl;
    std::cout << "is_member_function_pointer<int (functional::*)()> == "
        << std::boolalpha
        << std::is_member_function_pointer<int (functional::*)()>::value
        << std::endl;

    return (0);
    }
```

```Output
is_member_function_pointer<trivial *> == false
is_member_function_pointer<int trivial::*> == false
is_member_function_pointer<int (functional::*)()> == true
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_member_pointer, klasa](../standard-library/is-member-pointer-class.md)<br/>
