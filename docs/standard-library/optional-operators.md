---
title: '&lt;&gt;Operatory opcjonalne'
ms.date: 11/04/2016
f1_keywords:
- optional/std::operator!=
- optional/std::operator==
- optional/std::operatoroperator&gt;
- optional/std::operatoroperator&gt=;
- optional/std::operatoroperator&lt;
- optional/std::operatoroperator&lt;=
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (optional)
- std::operator== (optional)
- std::operatoroperator&gt; (optional)
- std::operatoroperator&gt=; (optional)
- std::operatoroperator&lt; (optional)
- std::operatoroperator&lt;= (optional)
ms.openlocfilehash: c7eca76f71f12e7f7fe0e60c0a4cfe456d54c374
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224685"
---
# <a name="ltoptionalgt-operators"></a>&lt;&gt;Operatory opcjonalne

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

Testuje, czy `optional` obiekt po lewej stronie operatora jest równy `optional` obiektowi po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator==(const optional<T>& left, const optional<U>& right);
template <class T> constexpr bool operator==(const optional<T>& left, nullopt_t right) noexcept;
template <class T> constexpr bool operator==(nullopt_t left, const optional<T>& right) noexcept;
template <class T, class U> constexpr bool operator==(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator==(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `optional` , `nullopt_t` , lub `T` .

*Kliknij*\
Obiekt typu `optional` , `nullopt_t` , lub `T` .

## <a name="operator"></a><a name="op_neq"></a>operator! =

Testuje, czy `optional` obiekt po lewej stronie operatora nie jest równy `optional` obiektowi po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator!=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator!=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator!=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator!=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator!=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `optional` , `nullopt_t` , lub `T` .

*Kliknij*\
Obiekt typu `optional` , `nullopt_t` , lub `T` .

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu zwraca wartość `!(left == right)` .

## <a name="operatorlt"></a><a name="op_lt"></a>zakład&lt;

Testuje, czy `optional` obiekt po lewej stronie operatora jest mniejszy od `optional` obiektu po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator<(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `optional` , `nullopt_t` , lub `T` .

*Kliknij*\
Obiekt typu `optional` , `nullopt_t` , lub `T` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli lista po lewej stronie operatora jest mniejsza niż, ale nie równa liście po prawej stronie operatora; w przeciwnym razie **`false`** .

## <a name="operatorlt"></a><a name="op_lt_eq"></a>zakład&lt;=

Testuje, czy `optional` obiekt po lewej stronie operatora jest mniejszy od lub równy `optional` obiektowi po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator<=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `optional` , `nullopt_t` , lub `T` .

*Kliknij*\
Obiekt typu `optional` , `nullopt_t` , lub `T` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli lista po lewej stronie operatora jest mniejsza lub równa liście po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu zwraca wartość `!(right < left)` .

## <a name="operatorgt"></a><a name="op_gt"></a>zakład&gt;

Testuje, czy `optional` obiekt po lewej stronie operatora jest większy niż `optional` obiekt po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator>(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `optional` , `nullopt_t` , lub `T` .

*Kliknij*\
Obiekt typu `optional` , `nullopt_t` , lub `T` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli lista po lewej stronie operatora jest większa niż lista po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu zwraca wartość `right < left` .

## <a name="operatorgt"></a><a name="op_gt_eq"></a>zakład&gt;=

Testuje, czy `optional` obiekt po lewej stronie operatora jest większy niż lub równy `optional` obiektowi po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator>=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*lewym*\
Obiekt typu `optional` , `nullopt_t` , lub `T` .

*Kliknij*\
Obiekt typu `optional` , `nullopt_t` , lub `T` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli po `optional` lewej stronie operatora jest większy lub równy po `optional` prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca wartość `!(left < right)` .
