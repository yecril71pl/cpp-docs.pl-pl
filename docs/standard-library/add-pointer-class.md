---
title: add_pointer — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_pointer
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
ms.openlocfilehash: 74e8cf037f8adfb6fdd9338c3cd95e2363f8de75
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222618"
---
# <a name="add_pointer-class"></a>add_pointer — Klasa

Tworzy wskaźnik do typu z określonego typu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct add_pointer;

template <class T>
using add_pointer_t = typename add_pointer<T>::type;
```

### <a name="parameters"></a>Parametry

*&*\
Typ do modyfikacji.

## <a name="remarks"></a>Uwagi

Nazwa elementu członkowskiego tego **`typedef`** `type` samego typu co `remove_reference<T>::type*` . Alias `add_pointer_t` jest skrótem, aby uzyskać dostęp do elementu członkowskiego **`typedef`** `type` .

Ponieważ nie jest to prawidłowe, aby można było utworzyć wskaźnik z odwołania, `add_pointer` usuwa odwołanie, jeśli istnieje, z określonego typu, zanim przetworzy wskaźnik do typu. W związku z tym można użyć typu z `add_pointer` bez względu na to, czy typ jest odwołaniem.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, że `add_pointer` Typ jest taki sam jak wskaźnik do tego typu.

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_pointer_t<int> *p = (int **)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_pointer_t<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_pointer_t<int> == int *
```

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<type_traits>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](type-traits.md)\
[Klasa remove_pointer](remove-pointer-class.md)
