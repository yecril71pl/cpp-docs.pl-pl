---
title: '&lt;Operatory&gt; scoped_allocator'
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 071fc3b73cd3378b110d6d412bb7575e35a77478
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447338"
---
# <a name="ltscopedallocatorgt-operators"></a>&lt;Operatory&gt; scoped_allocator

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>operator! =

Testuje `scoped_allocator_adaptor` dwa obiekty pod kątem nierówności.

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

## <a name="op_eq_eq"></a>operator = =

Testuje `scoped_allocator_adaptor` dwa obiekty pod kątem równości.

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

## <a name="see-also"></a>Zobacz także

[<scoped_allocator>](../standard-library/scoped-allocator.md)
