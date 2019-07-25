---
title: add_volatile — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_volatile
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
ms.openlocfilehash: becea4ff52342a79d0b87ffe0022e2cf84c47949
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456529"
---
# <a name="addvolatile-class"></a>add_volatile — Klasa

Tworzy typ  nietrwały z określonego typu.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct add_volatile;

template <class T>
using add_volatile_t = typename add_volatile<T>::type;
```

### <a name="parameters"></a>Parametry

*&* \
Typ do modyfikacji.

## <a name="remarks"></a>Uwagi

Wystąpienie `add_volatile<T>` ma element członkowski **typedef** `type` , który jest *t* if *t* jest odwołaniem, funkcją lub typem kwalifikowanym niestabilnym, w przeciwnym razie **volatile** *t*. Alias `add_volatile_t` jest skrótem umożliwiającym dostęp do elementu członkowskiego **typedef** `type`.

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

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[< type_traits >](../standard-library/type-traits.md)\
[remove_volatile, klasa](../standard-library/remove-volatile-class.md)
