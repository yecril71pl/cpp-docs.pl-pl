---
title: remove_volatile — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_volatile
helpviewer_keywords:
- remove_volatile class
- remove_volatile
ms.assetid: 8b87e2c2-a581-4eb3-8691-c5603910d61d
ms.openlocfilehash: 19514d1839fa6e0afcecb690dcb12657a85f3c2e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451262"
---
# <a name="removevolatile-class"></a>remove_volatile — Klasa

Tworzy typ inny niż volatile z typu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct remove_volatile;

template <class T>
using remove_volatile_t = typename remove_volatile<T>::type;
```

### <a name="parameters"></a>Parametry

*&* \
Typ do modyfikacji.

## <a name="remarks"></a>Uwagi

Wystąpienie `remove_volatile<T>` ma zmodyfikowany typ, który jest `T1` , gdy *t* ma postać `volatile T1`, w przeciwnym razie *t*.

## <a name="example"></a>Przykład

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    int *p = (std::remove_volatile_t<volatile int> *)0;

    p = p;  // to quiet "unused" warning
    std::cout << " remove_volatile_t<volatile int> == "
        << typeid(*p).name() << std::endl;

    return (0);
    }
```

```Output
remove_volatile_t<volatile int> == int
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md)\
[add_volatile, klasa](../standard-library/add-volatile-class.md)
