---
title: '&lt;Wątek&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- thread/std::operator!=
- thread/std::operator&gt;
- thread/std::operator&gt;=
- thread/std::operator&lt;
- thread/std::operator&lt;&lt;
- thread/std::operator&lt;=
- thread/std::operator==
dev_langs:
- C++
ms.assetid: e6bb6c0f-64f9-4cb2-9ff2-05b88a6ba7ac
helpviewer_keywords:
- std::operator!= (thread)
- std::operator&gt; (thread)
- std::operator&gt;= (thread)
- std::operator&lt; (thread)
- std::operator&lt;&lt; (thread)
- std::operator&lt;= (thread)
- std::operator== (thread)
ms.openlocfilehash: 1f5f523b19581fe11f01266c90e6b8612da125fc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltthreadgt-operators"></a>&lt;Wątek&gt; operatory

||||
|-|-|-|
|[operator!=](#op_neq)|[Operator&gt;](#op_gt)|[Operator&gt;=](#op_gt_eq)|
|[Operator&lt;](#op_lt)|[Operator&lt;&lt;](#op_lt_lt)|[Operator&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|

## <a name="op_gt_eq"></a>  Operator&gt;=

Określa, czy co najmniej `thread::id` obiektu jest większa lub równa innej.

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

`Left` Po lewej stronie `thread::id` obiektu.

`Right` Prawo `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwracana

`!(Left < Right)`

### <a name="remarks"></a>Uwagi

Tej funkcji nie generują żadnych wyjątków.

## <a name="op_gt"></a>  Operator&gt;

Określa, czy co najmniej `thread::id` obiekt jest większy niż innym.

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

`Left` Po lewej stronie `thread::id` obiektu.

`Right` Prawo `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwracana

`Right < Left`

### <a name="remarks"></a>Uwagi

Tej funkcji nie generują żadnych wyjątków.

## <a name="op_lt_eq"></a>  Operator&lt;=

Określa, czy co najmniej `thread::id` obiekt jest mniejszy niż lub równy do innego.

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

`Left` Po lewej stronie `thread::id` obiektu.

`Right` Prawo `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwracana

`!(Right < Left)`

### <a name="remarks"></a>Uwagi

Tej funkcji nie generują żadnych wyjątków.

## <a name="op_lt"></a>  Operator&lt;

Określa, czy co najmniej `thread::id` obiekt jest mniejszy niż innym.

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

`Left` Po lewej stronie `thread::id` obiektu.

`Right` Prawo `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli `Left` poprzedza `Right` w kolejności całkowita; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Definiuje operator całkowita kolejności na wszystkich `thread::id` obiektów. Te obiekty może służyć jako klucze w kontenerach asocjacyjnej.

Tej funkcji nie generują żadnych wyjątków.

## <a name="op_neq"></a>  operator! =

Porównuje dwa `thread::id` obiekty pod kątem nierówności.

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

`Left` Po lewej stronie `thread::id` obiektu.

`Right` Prawo `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwracana

`!(Left == Right)`

### <a name="remarks"></a>Uwagi

Tej funkcji nie generują żadnych wyjątków.

## <a name="op_eq_eq"></a>  operator ==

Porównuje dwa `thread::id` obiekty pod kątem równości.

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

`Left` Po lewej stronie `thread::id` obiektu.

`Right` Prawo `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli dwa obiekty reprezentują tego samego wątku wykonywania lub jeśli żaden obiekt reprezentuje wątku do wykonania; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Tej funkcji nie generują żadnych wyjątków.

## <a name="op_lt_lt"></a>  Operator&lt;&lt;

Wstawia tekst reprezentację `thread::id` obiektu do strumienia.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>Parametry

`Ostr` A [basic_ostream —](../standard-library/basic-ostream-class.md) obiektu.

`Id` A `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwracana

`Ostr`.

### <a name="remarks"></a>Uwagi

Ta funkcja wstawia `Id` do `Ostr`.

Jeśli dwa `thread::id` obiektów porównanie, reprezentacje wstawionego tekstu te obiekty są takie same.

## <a name="see-also"></a>Zobacz także

[\<Wątek >](../standard-library/thread.md)<br/>
