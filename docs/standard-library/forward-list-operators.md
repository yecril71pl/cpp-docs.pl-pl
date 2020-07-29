---
title: '&lt;&gt;operatory forward_list'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::operator!=
- forward_list/std::operator==
- forward_list/std::operatoroperator&gt;
- forward_list/std::operatoroperator&gt=;
- forward_list/std::operatoroperator&lt;
- forward_list/std::operatoroperator&lt;=
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (forward_list)
- std::operator== (forward_list)
- std::operatoroperator&gt; (forward_list)
- std::operatoroperator&gt=; (forward_list)
- std::operatoroperator&lt; (forward_list)
- std::operatoroperator&lt;= (forward_list)
ms.openlocfilehash: beb02a8353c6c5187dd0fa0171518c753eee7868
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193344"
---
# <a name="ltforward_listgt-operators"></a>&lt;&gt;operatory forward_list

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

Testuje, czy obiekt listy do przodu po lewej stronie operatora jest równy obiektowi listy do przodu po prawej stronie.

```cpp
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `forward_list`.

*Kliknij*\
Obiekt typu `forward_list`.

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu przeciąża `operator==` , aby porównać dwa obiekty szablonu klasy `forward_list` . Funkcja zwraca wartość `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())` .

## <a name="operator"></a><a name="op_neq"></a>operator! =

Testuje, czy obiekt listy do przodu po lewej stronie operatora nie jest równy obiektowi listy do przodu po prawej stronie.

```cpp
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `forward_list`.

*Kliknij*\
Obiekt typu `forward_list`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli listy nie są równe; **`false`** Jeśli listy są równe.

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu zwraca wartość `!(left == right)` .

## <a name="operatorlt"></a><a name="op_lt"></a>zakład&lt;

Testuje, czy obiekt listy do przodu po lewej stronie operatora jest mniejszy niż obiekt listy do przodu po prawej stronie.

```cpp
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `forward_list`.

*Kliknij*\
Obiekt typu `forward_list`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli lista po lewej stronie operatora jest mniejsza niż, ale nie równa liście po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu przeciąża `operator<` , aby porównać dwa obiekty szablonu klasy `forward_list` . Funkcja zwraca wartość `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())` .

## <a name="operatorlt"></a><a name="op_lt_eq"></a>zakład&lt;=

Testuje, czy obiekt listy do przodu po lewej stronie operatora jest mniejszy niż lub równy obiektowi listy do przodu po prawej stronie.

```cpp
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `forward_list`.

*Kliknij*\
Obiekt typu `forward_list`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli lista po lewej stronie operatora jest mniejsza lub równa liście po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu zwraca wartość `!(right < left)` .

## <a name="operatorgt"></a><a name="op_gt"></a>zakład&gt;

Testuje, czy obiekt listy do przodu po lewej stronie operatora jest większy niż obiekt listy do przodu po prawej stronie.

```cpp
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `forward_list`.

*Kliknij*\
Obiekt typu `forward_list`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli lista po lewej stronie operatora jest większa niż lista po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu zwraca wartość `right < left` .

## <a name="operatorgt"></a><a name="op_gt_eq"></a>zakład&gt;=

Testuje, czy obiekt listy do przodu po lewej stronie operatora jest większy niż lub równy obiektowi listy do przodu po prawej stronie.

```cpp
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `forward_list`.

*Kliknij*\
Obiekt typu `forward_list`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli lista przesyłania dalej po lewej stronie operatora jest większa lub równa liście do przodu po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca wartość `!(left < right)` .
