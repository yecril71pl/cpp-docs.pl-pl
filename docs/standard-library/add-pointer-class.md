---
title: add_pointer — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_pointer
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
ms.openlocfilehash: 759867a542aa128755ba31e090984eb5b3fe6963
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456558"
---
# <a name="addpointer-class"></a>add_pointer — Klasa

Tworzy wskaźnik do typu z określonego typu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct add_pointer;

template <class T>
using add_pointer_t = typename add_pointer<T>::type;
```

### <a name="parameters"></a>Parametry

*&* \
Typ do modyfikacji.

## <a name="remarks"></a>Uwagi

Element **typedef** `type` składa się z tego samego `remove_reference<T>::type*`typu co. Alias `add_pointer_t` jest skrótem umożliwiającym dostęp do elementu członkowskiego **typedef** `type`.

Ponieważ nie jest to prawidłowe, aby można było utworzyć wskaźnik z `add_pointer` odwołania, usuwa odwołanie, jeśli istnieje, z określonego typu, zanim przetworzy wskaźnik do typu. W związku z tym można użyć typu z `add_pointer` bez względu na to, czy typ jest odwołaniem.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, że `add_pointer` typ jest taki sam jak wskaźnik do tego typu.

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

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md)\
[remove_pointer, klasa](../standard-library/remove-pointer-class.md)
