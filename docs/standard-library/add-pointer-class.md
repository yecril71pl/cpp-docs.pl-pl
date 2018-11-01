---
title: add_pointer — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_pointer
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
ms.openlocfilehash: fda2bcbd3484b9244d69358aac3e9baf5d37a4ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566013"
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

*T*<br/>
Typ do modyfikacji.

## <a name="remarks"></a>Uwagi

Element członkowski **typedef** `type` nazwy tego samego typu co `remove_reference<T>::type*`. Alias `add_pointer_t` to skrót umożliwiający dostęp do elementu członkowskiego **typedef** `type`.

Ponieważ jest ono nieprawidłowe tworzenie wskaźnika z odwołania `add_pointer` Usuwa odwołanie, jeśli istnieje, z określonego typu, zanim sprawia, że wskaźnik do typu. W związku z tym, można użyć typu z `add_pointer` nie, czy typ jest odwołaniem.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, że `add_pointer` typu jest taki sam jak wskaźnik do tego typu.

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

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_pointer, klasa](../standard-library/remove-pointer-class.md)<br/>
