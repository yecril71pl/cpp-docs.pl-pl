---
title: add_volatile — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::add_volatile
dev_langs:
- C++
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf15ef0b5134af7831cf2e71b4235df9534f3425
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33841300"
---
# <a name="addvolatile-class"></a>add_volatile — Klasa

Sprawia, że typ volatile z określonego typu.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct add_volatile;

template <class T>
using add_volatile_t = typename add_volatile<T>::type;
```

### <a name="parameters"></a>Parametry

*T* typu do zmodyfikowania.

## <a name="remarks"></a>Uwagi

Wystąpienie `add_volatile<T>` ma typedef elementu członkowskiego `type` czyli *T* Jeśli *T* jest odwołanie, funkcji lub typu kwalifikowana volatile `volatile` *T*. Alias `add_volatile_t` to skrót do dostępu — element członkowski typedef `type`.

## <a name="example"></a>Przykład

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_volatile_t<int> *p = (volatile int *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_volatile<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_volatile<int> == int
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_volatile, klasa](../standard-library/remove-volatile-class.md)<br/>
