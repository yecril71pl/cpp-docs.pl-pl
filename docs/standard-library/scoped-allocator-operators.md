---
title: '&lt;scoped_allocator&gt; operatorów'
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 7c9f2c3a2425bf3ac6e62ce7fcecfe9315c3e04e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512466"
---
# <a name="ltscopedallocatorgt-operators"></a>&lt;scoped_allocator&gt; operatorów

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator! =

Testuje dwa `scoped_allocator_adaptor` obiekty pod kątem nierówności.

```cpp
template <class Outer, class... Inner>
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie `scoped_allocator_adaptor` obiektu.

*right*<br/>
Po prawej stronie `scoped_allocator_adaptor` obiektu.

### <a name="return-value"></a>Wartość zwracana

`!(left == right)`

## <a name="op_eq_eq"></a>  operator ==

Testuje dwa `scoped_allocator_adaptor` obiekty pod kątem równości.

```cpp
template <class Outer, class... Inner>
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Parametry

*left*<br/>
Po lewej stronie `scoped_allocator_adaptor` obiektu.

*right*<br/>
Po prawej stronie `scoped_allocator_adaptor` obiektu.

### <a name="return-value"></a>Wartość zwracana

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>Zobacz także

[<scoped_allocator>](../standard-library/scoped-allocator.md)<br/>
