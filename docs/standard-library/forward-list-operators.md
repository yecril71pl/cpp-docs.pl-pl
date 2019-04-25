---
title: '&lt;forward_list —&gt; operatorów'
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
ms.openlocfilehash: 4126b81f61bd37a7a12e0621c323ec832c5b2ab7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159434"
---
# <a name="ltforwardlistgt-operators"></a>&lt;forward_list —&gt; operatorów

||||
|-|-|-|
|[operator!=](#op_neq)|[Operator&gt;](#op_gt)|[Operator&gt;=](#op_gt_eq)|
|[Operator&lt;](#op_lt)|[Operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a>  operator ==

Sprawdza, czy obiekt listy do przodu po lewej stronie operatora jest równy obiektowi do przodu listy po prawej stronie.

```cpp
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*left*|Obiekt typu `forward_list`.|
|*right*|Obiekt typu `forward_list`.|

### <a name="remarks"></a>Uwagi

Przeciążenia tej funkcji szablonu `operator==` do porównywania dwóch obiektów klasy szablonu `forward_list`. Funkcja zwraca `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`.

## <a name="op_neq"></a>  operator! =

Sprawdza, czy obiekt listy do przodu po lewej stronie operatora nie jest taki sam jak obiekt do przodu listy po prawej stronie.

```cpp
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*left*|Obiekt typu `forward_list`.|
|*right*|Obiekt typu `forward_list`.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** listy nie są równe; **false** list są równe.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca `!(left == right)`.

## <a name="op_lt"></a>  Operator&lt;

Sprawdza, czy obiekt listy do przodu, po lewej stronie operatora jest mniejszy niż obiekt listy do przodu, po prawej stronie.

```cpp
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*left*|Obiekt typu `forward_list`.|
|*right*|Obiekt typu `forward_list`.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli na liście po lewej stronie operatora jest mniejszy niż, ale nie równa listy po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Przeciążenia tej funkcji szablonu `operator<` do porównywania dwóch obiektów klasy szablonu `forward_list`. Funkcja zwraca `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`.

## <a name="op_lt_eq"></a>  Operator&lt;=

Sprawdza, czy obiekt listy do przodu, po lewej stronie operatora jest mniejszy niż lub równy obiektowi do przodu listy po prawej stronie.

```cpp
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*left*|Obiekt typu `forward_list`.|
|*right*|Obiekt typu `forward_list`.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli lista po lewej stronie operatora jest mniejszy niż lub równe do listy po prawej stronie operatora; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca `!(right < left)`.

## <a name="op_gt"></a>  Operator&gt;

Sprawdza, czy obiekt listy do przodu, po lewej stronie operatora jest większy niż obiekt listy do przodu, po prawej stronie.

```cpp
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*left*|Obiekt typu `forward_list`.|
|*right*|Obiekt typu `forward_list`.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli lista po lewej stronie operatora jest większy niż listy po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca `right < left`.

## <a name="op_gt_eq"></a>  Operator&gt;=

Sprawdza, czy obiekt listy do przodu po lewej stronie operatora jest większy lub równy obiektowi do przodu listy po prawej stronie.

```cpp
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*left*|Obiekt typu `forward_list`.|
|*right*|Obiekt typu `forward_list`.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli do przodu lista po lewej stronie operatora jest większy niż lub równe do przekierowania listy po prawej stronie operatora; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca `!(left < right)`.

## <a name="see-also"></a>Zobacz także

[<forward_list>](../standard-library/forward-list.md)<br/>
