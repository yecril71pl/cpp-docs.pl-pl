---
title: add_volatile — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::add_volatile
dev_langs:
- C++
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d66f7c315fe406a7ac7cbcb3abe706ae702cdf13
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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
