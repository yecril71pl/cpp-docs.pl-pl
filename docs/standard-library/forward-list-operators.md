---
title: '&lt;forward_list operatory&gt;'
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
ms.openlocfilehash: 1ddfb56c7ff68ec10c7bb56af3495e4042acb83c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421794"
---
# <a name="ltforward_listgt-operators"></a>&lt;forward_list operatory&gt;

## <a name="op_eq_eq"></a>operator = =

Testuje, czy obiekt listy do przodu po lewej stronie operatora jest równy obiektowi listy do przodu po prawej stronie.

```cpp
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `forward_list`.

*prawa*\
Obiekt typu `forward_list`.

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu przeciąża `operator==`, aby porównać dwa obiekty `forward_list`szablonu klasy. Funkcja zwraca `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`.

## <a name="op_neq"></a>operator! =

Testuje, czy obiekt listy do przodu po lewej stronie operatora nie jest równy obiektowi listy do przodu po prawej stronie.

```cpp
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `forward_list`.

*prawa*\
Obiekt typu `forward_list`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli listy nie są równe; **wartość false** , jeśli listy są równe.

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu zwraca `!(left == right)`.

## <a name="op_lt"></a>&lt; operatora

Testuje, czy obiekt listy do przodu po lewej stronie operatora jest mniejszy niż obiekt listy do przodu po prawej stronie.

```cpp
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `forward_list`.

*prawa*\
Obiekt typu `forward_list`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli lista po lewej stronie operatora jest mniejsza niż, ale nie równa liście po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu przeciąża `operator<`, aby porównać dwa obiekty `forward_list`szablonu klasy. Funkcja zwraca `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`.

## <a name="op_lt_eq"></a>&lt;operatora =

Testuje, czy obiekt listy do przodu po lewej stronie operatora jest mniejszy niż lub równy obiektowi listy do przodu po prawej stronie.

```cpp
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `forward_list`.

*prawa*\
Obiekt typu `forward_list`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli lista po lewej stronie operatora jest mniejsza lub równa liście po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu zwraca `!(right < left)`.

## <a name="op_gt"></a>&gt; operatora

Testuje, czy obiekt listy do przodu po lewej stronie operatora jest większy niż obiekt listy do przodu po prawej stronie.

```cpp
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `forward_list`.

*prawa*\
Obiekt typu `forward_list`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli lista po lewej stronie operatora jest większa niż lista po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu zwraca `right < left`.

## <a name="op_gt_eq"></a>&gt;operatora =

Testuje, czy obiekt listy do przodu po lewej stronie operatora jest większy niż lub równy obiektowi listy do przodu po prawej stronie.

```cpp
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `forward_list`.

*prawa*\
Obiekt typu `forward_list`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli lista przesyłania dalej po lewej stronie operatora jest większa lub równa liście do przodu po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca `!(left < right)`.
