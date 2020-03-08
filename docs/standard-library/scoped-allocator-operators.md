---
title: '&lt;scoped_allocator operatory&gt;'
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::operator!=
- scoped_allocator/std::operator==
ms.assetid: 4dfe0805-cc6e-479f-887f-a1c164f73837
ms.openlocfilehash: 071fc3b73cd3378b110d6d412bb7575e35a77478
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876338"
---
# <a name="ltscoped_allocatorgt-operators"></a>&lt;scoped_allocator operatory&gt;

|||
|-|-|
|[operator!=](#op_neq)|[operator = =](#op_eq_eq)|

## <a name="op_neq"></a>operator! =

Testuje dwa `scoped_allocator_adaptor` obiektów pod kątem nierówności.

```cpp
template <class Outer, class... Inner>
bool operator!=(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt `scoped_allocator_adaptor` po lewej stronie.

*prawa*\
Właściwy `scoped_allocator_adaptor` obiektu.

### <a name="return-value"></a>Wartość zwracana

`!(left == right)`

## <a name="op_eq_eq"></a>operator = =

Testuje dwa `scoped_allocator_adaptor` obiektów pod kątem równości.

```cpp
template <class Outer, class... Inner>
bool operator==(
    const scoped_allocator_adaptor<Outer, Inner...>& left,
    const scoped_allocator_adaptor<Outer, Inner...>& right) noexcept;
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt `scoped_allocator_adaptor` po lewej stronie.

*prawa*\
Właściwy `scoped_allocator_adaptor` obiektu.

### <a name="return-value"></a>Wartość zwracana

`left.outer_allocator() == right.outer_allocator() && left.inner_allocator() == right.inner_allocator()`

## <a name="see-also"></a>Zobacz też

[<scoped_allocator>](../standard-library/scoped-allocator.md)
