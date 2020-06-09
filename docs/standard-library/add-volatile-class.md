---
title: add_volatile — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_volatile
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
ms.openlocfilehash: 1a4ad8a86b88cdfa98f043bb49ba6eeff8b090c9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619206"
---
# <a name="add_volatile-class"></a>add_volatile — Klasa

Tworzy typ **nietrwały** z określonego typu.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct add_volatile;

template <class T>
using add_volatile_t = typename add_volatile<T>::type;
```

### <a name="parameters"></a>Parametry

*&*\
Typ do modyfikacji.

## <a name="remarks"></a>Uwagi

Wystąpienie ma element `add_volatile<T>` członkowski **typedef** `type` , który jest *t* if *t* jest odwołaniem, funkcją lub typem kwalifikowanym niestabilnym, w przeciwnym razie **volatile** *t*. Alias `add_volatile_t` jest skrótem umożliwiającym dostęp do elementu członkowskiego **typedef** `type` .

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

**Nagłówek:**\<type_traits>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz też

[<type_traits>](type-traits.md)\
[Klasa remove_volatile](remove-volatile-class.md)
