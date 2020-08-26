---
title: '&lt;&gt;operatory scoped_allocator'
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 907772069c192b3ef75c7366e079b1da1dd36f8d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846254"
---
# <a name="ltscoped_allocatorgt-operators"></a>&lt;&gt;operatory scoped_allocator

[operator! =](#op_neq)\
[operator = =](#op_eq_eq)

## <a name="operator"></a><a name="op_neq"></a> operator! =

Testuje dwa `scoped_allocator_adaptor` obiekty pod kątem nierówności.

```cpp
template <class Outer, class... Inner>
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Parametry

*lewym*\
Lewy `scoped_allocator_adaptor` obiekt.

*Kliknij*\
Prawidłowy `scoped_allocator_adaptor` obiekt.

### <a name="return-value"></a>Wartość zwracana

`!(left == right)`

## <a name="operator"></a><a name="op_eq_eq"></a> operator = =

Testuje dwa `scoped_allocator_adaptor` obiekty pod kątem równości.

```cpp
template <class Outer, class... Inner>
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Parametry

*lewym*\
Lewy `scoped_allocator_adaptor` obiekt.

*Kliknij*\
Prawidłowy `scoped_allocator_adaptor` obiekt.

### <a name="return-value"></a>Wartość zwracana

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>Zobacz też

[<scoped_allocator>](../standard-library/scoped-allocator.md)
