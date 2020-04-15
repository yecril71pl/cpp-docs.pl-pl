---
title: '&lt;opcjonalne&gt; operatory'
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
ms.openlocfilehash: 9bdef0669f90da7865f7652ff4528e51e584e1a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373634"
---
# <a name="ltoptionalgt-operators"></a>&lt;opcjonalne&gt; operatory

## <a name="operator"></a><a name="op_eq_eq"></a>operator==

Sprawdza, `optional` czy obiekt po lewej stronie operatora `optional` jest równy obiektowi po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator==(const optional<T>& left, const optional<U>& right);
template <class T> constexpr bool operator==(const optional<T>& left, nullopt_t right) noexcept;
template <class T> constexpr bool operator==(nullopt_t left, const optional<T>& right) noexcept;
template <class T, class U> constexpr bool operator==(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator==(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*Lewej*\
Obiekt typu `optional`, `nullopt_t`, `T`lub .

*Prawo*\
Obiekt typu `optional`, `nullopt_t`, `T`lub .

## <a name="operator"></a><a name="op_neq"></a>operator!=

Sprawdza, `optional` czy obiekt po lewej stronie operatora nie `optional` jest równy obiektowi po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator!=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator!=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator!=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator!=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator!=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*Lewej*\
Obiekt typu `optional`, `nullopt_t`, `T`lub .

*Prawo*\
Obiekt typu `optional`, `nullopt_t`, `T`lub .

### <a name="remarks"></a>Uwagi

Ta funkcja `!(left == right)`szablonu zwraca .

## <a name="operatorlt"></a><a name="op_lt"></a>Operator&lt;

Sprawdza, `optional` czy obiekt po lewej stronie operatora `optional` jest mniejszy niż obiekt po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator<(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*Lewej*\
Obiekt typu `optional`, `nullopt_t`, `T`lub .

*Prawo*\
Obiekt typu `optional`, `nullopt_t`, `T`lub .

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli lista po lewej stronie operatora jest mniejsza, ale nie równa się wykazowi po prawej stronie operatora; w przeciwnym razie **false**.

## <a name="operatorlt"></a><a name="op_lt_eq"></a>Operator&lt;=

Sprawdza, `optional` czy obiekt po lewej stronie operatora jest mniejszy `optional` lub równy obiektowi po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator<=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*Lewej*\
Obiekt typu `optional`, `nullopt_t`, `T`lub .

*Prawo*\
Obiekt typu `optional`, `nullopt_t`, `T`lub .

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeżeli lista po lewej stronie operatora jest mniejsza lub równa liście po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja `!(right < left)`szablonu zwraca .

## <a name="operatorgt"></a><a name="op_gt"></a>Operator&gt;

Sprawdza, `optional` czy obiekt po lewej stronie operatora `optional` jest większy niż obiekt po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator>(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*Lewej*\
Obiekt typu `optional`, `nullopt_t`, `T`lub .

*Prawo*\
Obiekt typu `optional`, `nullopt_t`, `T`lub .

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli lista po lewej stronie operatora jest większa niż lista po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja `right < left`szablonu zwraca .

## <a name="operatorgt"></a><a name="op_gt_eq"></a>Operator&gt;=

Sprawdza, `optional` czy obiekt po lewej stronie operatora jest większy `optional` lub równy obiektowi po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator>=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*Lewej*\
Obiekt typu `optional`, `nullopt_t`, `T`lub .

*Prawo*\
Obiekt typu `optional`, `nullopt_t`, `T`lub .

### <a name="return-value"></a>Wartość zwracana

**prawda,** `optional` jeżeli po lewej stronie operatora jest większa `optional` lub równa po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Funkcja szablonu `!(left < right)`zwraca .
