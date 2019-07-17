---
title: '&lt;Opcjonalnie&gt; operatorów'
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
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268031"
---
# <a name="ltoptionalgt-operators"></a>&lt;Opcjonalnie&gt; operatorów

## <a name="op_eq_eq"></a> operator ==

Sprawdza, czy `optional` obiekt po lewej stronie operatora jest równy `optional` obiektu po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator==(const optional<T>& left, const optional<U>& right);
template <class T> constexpr bool operator==(const optional<T>& left, nullopt_t right) noexcept;
template <class T> constexpr bool operator==(nullopt_t left, const optional<T>& right) noexcept;
template <class T, class U> constexpr bool operator==(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator==(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*po lewej stronie*\
Obiekt typu `optional`, `nullopt_t`, lub `T`.

*po prawej stronie*\
Obiekt typu `optional`, `nullopt_t`, lub `T`.

## <a name="op_neq"></a> operator! =

Sprawdza, czy `optional` obiektu po lewej stronie operatora nie jest równa `optional` obiektu po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator!=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator!=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator!=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator!=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator!=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*po lewej stronie*\
Obiekt typu `optional`, `nullopt_t`, lub `T`.

*po prawej stronie*\
Obiekt typu `optional`, `nullopt_t`, lub `T`.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca `!(left == right)`.

## <a name="op_lt"></a> Operator&lt;

Sprawdza, czy `optional` obiekt po lewej stronie operatora jest mniejszy od `optional` obiektu po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator<(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*po lewej stronie*\
Obiekt typu `optional`, `nullopt_t`, lub `T`.

*po prawej stronie*\
Obiekt typu `optional`, `nullopt_t`, lub `T`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli na liście po lewej stronie operatora jest mniejszy niż, ale nie równa listy po prawej stronie operatora; w przeciwnym razie **false**.

## <a name="op_lt_eq"></a>  Operator&lt;=

Sprawdza, czy `optional` obiekt po lewej stronie operatora jest mniejszy niż lub równe `optional` obiektu po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator<=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*po lewej stronie*\
Obiekt typu `optional`, `nullopt_t`, lub `T`.

*po prawej stronie*\
Obiekt typu `optional`, `nullopt_t`, lub `T`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli lista po lewej stronie operatora jest mniejszy niż lub równe do listy po prawej stronie operatora; w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca `!(right < left)`.

## <a name="op_gt"></a> Operator&gt;

Sprawdza, czy `optional` obiekt po lewej stronie operatora jest większy niż `optional` obiektu po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator>(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*po lewej stronie*\
Obiekt typu `optional`, `nullopt_t`, lub `T`.

*po prawej stronie*\
Obiekt typu `optional`, `nullopt_t`, lub `T`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli lista po lewej stronie operatora jest większy niż listy po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca `right < left`.

## <a name="op_gt_eq"></a> Operator&gt;=

Sprawdza, czy `optional` obiektu po lewej stronie operatora jest większy niż lub równa `optional` obiektu po prawej stronie.

```cpp
template <class T, class U> constexpr bool operator>=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*po lewej stronie*\
Obiekt typu `optional`, `nullopt_t`, lub `T`.

*po prawej stronie*\
Obiekt typu `optional`, `nullopt_t`, lub `T`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `optional` po lewej stronie operatora jest większy niż lub równa `optional` po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca `!(left < right)`.
