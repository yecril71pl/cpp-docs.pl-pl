---
title: opcjonalne operatory&gt; &lt;
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
ms.openlocfilehash: c5d0de435180054b186400384fc0583df5b03246
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419694"
---
# <a name="ltoptionalgt-operators"></a>opcjonalne operatory&gt; &lt;

## <a name="op_eq_eq"></a>operator = =

Testuje, czy obiekt `optional` po lewej stronie operatora jest równy obiektowi `optional` po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator==(const optional<T>& left, const optional<U>& right);
template <class T> constexpr bool operator==(const optional<T>& left, nullopt_t right) noexcept;
template <class T> constexpr bool operator==(nullopt_t left, const optional<T>& right) noexcept;
template <class T, class U> constexpr bool operator==(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator==(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `optional`, `nullopt_t`lub `T`.

*prawa*\
Obiekt typu `optional`, `nullopt_t`lub `T`.

## <a name="op_neq"></a>operator! =

Testuje, czy obiekt `optional` po lewej stronie operatora nie jest równy obiektowi `optional` po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator!=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator!=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator!=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator!=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator!=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `optional`, `nullopt_t`lub `T`.

*prawa*\
Obiekt typu `optional`, `nullopt_t`lub `T`.

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu zwraca `!(left == right)`.

## <a name="op_lt"></a>&lt; operatora

Testuje, czy obiekt `optional` po lewej stronie operatora jest mniejszy niż obiekt `optional` po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator<(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `optional`, `nullopt_t`lub `T`.

*prawa*\
Obiekt typu `optional`, `nullopt_t`lub `T`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli lista po lewej stronie operatora jest mniejsza niż, ale nie równa liście po prawej stronie operatora; w przeciwnym razie **false**.

## <a name="op_lt_eq"></a>&lt;operatora =

Testuje, czy obiekt `optional` po lewej stronie operatora jest mniejszy niż lub równy obiektowi `optional` po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator<=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `optional`, `nullopt_t`lub `T`.

*prawa*\
Obiekt typu `optional`, `nullopt_t`lub `T`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli lista po lewej stronie operatora jest mniejsza lub równa liście po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu zwraca `!(right < left)`.

## <a name="op_gt"></a>&gt; operatora

Testuje, czy obiekt `optional` po lewej stronie operatora jest większy niż obiekt `optional` po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator>(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `optional`, `nullopt_t`lub `T`.

*prawa*\
Obiekt typu `optional`, `nullopt_t`lub `T`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli lista po lewej stronie operatora jest większa niż lista po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu zwraca `right < left`.

## <a name="op_gt_eq"></a>&gt;operatora =

Testuje, czy obiekt `optional` po lewej stronie operatora jest większy niż lub równy obiektowi `optional` po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator>=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `optional`, `nullopt_t`lub `T`.

*prawa*\
Obiekt typu `optional`, `nullopt_t`lub `T`.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli `optional` po lewej stronie operatora jest większy lub równy `optional` po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca `!(left < right)`.
