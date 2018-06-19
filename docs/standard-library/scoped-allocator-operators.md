---
title: '&lt;scoped_allocator&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
dev_langs:
- C++
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 66cf60dd3d70719fe42645215b1190c9fb752ff3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854681"
---
# <a name="ltscopedallocatorgt-operators"></a>&lt;scoped_allocator&gt; operatory

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator! =

Sprawdza dwie `scoped_allocator_adaptor` obiekty pod kątem nierówności.

```cpp
template <class Outer, class... Inner>
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Parametry

`left` Po lewej stronie `scoped_allocator_adaptor` obiektu.

`right` Prawo `scoped_allocator_adaptor` obiektu.

### <a name="return-value"></a>Wartość zwracana

`!(left == right)`

## <a name="op_eq_eq"></a>  operator ==

Sprawdza dwie `scoped_allocator_adaptor` obiekty pod kątem równości.

```cpp
template <class Outer, class... Inner>
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Parametry

`left` Po lewej stronie `scoped_allocator_adaptor` obiektu.

`right` Prawo `scoped_allocator_adaptor` obiektu.

### <a name="return-value"></a>Wartość zwracana

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>Zobacz także

[<scoped_allocator>](../standard-library/scoped-allocator.md)<br/>
