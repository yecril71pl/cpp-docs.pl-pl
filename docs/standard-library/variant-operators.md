---
title: '&lt;Wariant&gt; operatorów'
ms.date: 04/04/2019
f1_keywords:
- variant/std::operator!=
- variant/std::operator==
- variant/std::operatoroperator&gt;
- variant/std::operatoroperator&gt=;
- variant/std::operatoroperator&lt;
- variant/std::operatoroperator&lt;=
helpviewer_keywords:
- std::operator!= (variant)
- std::operator== (variant)
- std::operatoroperator&gt; (variant)
- std::operatoroperator&gt=; (variant)
- std::operatoroperator&lt; (variant)
- std::operatoroperator&lt;= (variant)
ms.openlocfilehash: 0c4042ca1d89f9835b32924b268ef17a56619009
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267923"
---
# <a name="ltvariantgt-operators"></a>&lt;Wariant&gt; operatorów

## <a name="op_eq_eq"></a> operator ==

Sprawdza, czy obiekt listy do przodu po lewej stronie operatora jest równy obiektowi do przodu listy po prawej stronie.

```cpp
template <class... Types>
    constexpr bool operator==(const variant<Types...>&, const variant<Types...>&);
```

## <a name="op_neq"></a> operator! =

Sprawdza, czy obiekt listy do przodu po lewej stronie operatora nie jest taki sam jak obiekt do przodu listy po prawej stronie.

```cpp
template <class... Types>
    constexpr bool operator!=(const variant<Types...>&, const variant<Types...>&);
```

## <a name="op_lt"></a> Operator&lt;

Sprawdza, czy obiekt listy do przodu, po lewej stronie operatora jest mniejszy niż obiekt listy do przodu, po prawej stronie.

```cpp
template <class... Types>
    constexpr bool operator<(const variant<Types...>&, const variant<Types...>&);
```

## <a name="op_lt_eq"></a> Operator&lt;=

Sprawdza, czy obiekt listy do przodu, po lewej stronie operatora jest mniejszy niż lub równy obiektowi do przodu listy po prawej stronie.

```cpp
template <class... Types>
    constexpr bool operator<=(const variant<Types...>&, const variant<Types...>&);
```

## <a name="op_gt"></a> Operator&gt;

Sprawdza, czy obiekt listy do przodu, po lewej stronie operatora jest większy niż obiekt listy do przodu, po prawej stronie.

```cpp
template <class... Types> constexpr
    bool operator>(const variant<Types...>&, const variant<Types...>&);
```

## <a name="op_gt_eq"></a> Operator&gt;=

Sprawdza, czy obiekt listy do przodu po lewej stronie operatora jest większy lub równy obiektowi do przodu listy po prawej stronie.

```cpp
template <class... Types> constexpr
    bool operator>=(const variant<Types...>&, const variant<Types...>&);
```
