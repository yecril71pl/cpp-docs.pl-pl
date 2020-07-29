---
title: '&lt;&gt;Operatory wątku'
ms.date: 11/04/2016
f1_keywords:
- thread/std::operator!=
- thread/std::operator&gt;
- thread/std::operator&gt;=
- thread/std::operator&lt;
- thread/std::operator&lt;&lt;
- thread/std::operator&lt;=
- thread/std::operator==
ms.assetid: e6bb6c0f-64f9-4cb2-9ff2-05b88a6ba7ac
helpviewer_keywords:
- std::operator!= (thread)
- std::operator&gt; (thread)
- std::operator&gt;= (thread)
- std::operator&lt; (thread)
- std::operator&lt;&lt; (thread)
- std::operator&lt;= (thread)
- std::operator== (thread)
ms.openlocfilehash: e7321831b9356fdb9ae5ce147319726def69efc7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215572"
---
# <a name="ltthreadgt-operators"></a>&lt;&gt;Operatory wątku

||||
|-|-|-|
|[operator! =](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|[operator&lt;=](#op_lt_eq)|
|[operator = =](#op_eq_eq)|

## <a name="operatorgt"></a><a name="op_gt_eq"></a>zakład&gt;=

Określa, czy jeden `thread::id` obiekt jest większy lub równy drugiemu.

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Lewym*\
Lewy `thread::id` obiekt.

*Kliknij*\
Prawidłowy `thread::id` obiekt.

### <a name="return-value"></a>Wartość zwracana

`!(Left < Right)`

### <a name="remarks"></a>Uwagi

Ta funkcja nie generuje żadnych wyjątków.

## <a name="operatorgt"></a><a name="op_gt"></a>zakład&gt;

Określa, czy jeden `thread::id` obiekt jest większy niż inny.

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Lewym*\
Lewy `thread::id` obiekt.

*Kliknij*\
Prawidłowy `thread::id` obiekt.

### <a name="return-value"></a>Wartość zwracana

`Right < Left`

### <a name="remarks"></a>Uwagi

Ta funkcja nie generuje żadnych wyjątków.

## <a name="operatorlt"></a><a name="op_lt_eq"></a>zakład&lt;=

Określa, czy jeden `thread::id` obiekt jest mniejszy lub równy drugiemu.

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Lewym*\
Lewy `thread::id` obiekt.

*Kliknij*\
Prawidłowy `thread::id` obiekt.

### <a name="return-value"></a>Wartość zwracana

`!(Right < Left)`

### <a name="remarks"></a>Uwagi

Ta funkcja nie generuje żadnych wyjątków.

## <a name="operatorlt"></a><a name="op_lt"></a>zakład&lt;

Określa, czy jeden `thread::id` obiekt jest mniejszy niż inny.

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Lewym*\
Lewy `thread::id` obiekt.

*Kliknij*\
Prawidłowy `thread::id` obiekt.

### <a name="return-value"></a>Wartość zwracana

**`true`** po *lewej stronie* poprzedza *prawo* w całkowitej kolejności; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Operator definiuje całkowitą kolejność dla wszystkich `thread::id` obiektów. Te obiekty mogą być używane jako klucze w kontenerach asocjacyjnych.

Ta funkcja nie generuje żadnych wyjątków.

## <a name="operator"></a><a name="op_neq"></a>operator! =

Porównuje dwa `thread::id` obiekty pod kątem nierówności.

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Lewym*\
Lewy `thread::id` obiekt.

*Kliknij*\
Prawidłowy `thread::id` obiekt.

### <a name="return-value"></a>Wartość zwracana

`!(Left == Right)`

### <a name="remarks"></a>Uwagi

Ta funkcja nie generuje żadnych wyjątków.

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

Porównuje dwa `thread::id` obiekty pod kątem równości.

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Lewym*\
Lewy `thread::id` obiekt.

*Kliknij*\
Prawidłowy `thread::id` obiekt.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli dwa obiekty reprezentują ten sam wątek wykonywania lub jeśli żaden z obiektów nie reprezentuje wątku wykonywania; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Ta funkcja nie generuje żadnych wyjątków.

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>zakład&lt;&lt;

Wstawia tekstową reprezentację `thread::id` obiektu do strumienia.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>Parametry

*Ostr*\
Obiekt [basic_ostream](../standard-library/basic-ostream-class.md) .

*#C1*\
Obiekt `thread::id`.

### <a name="return-value"></a>Wartość zwracana

*Ostr*.

### <a name="remarks"></a>Uwagi

Ta funkcja wstawia *Identyfikator* do *ostr*.

Jeśli dwa `thread::id` obiekty są porównywane jako równe, wstawiona tekstowa reprezentacja tych obiektów jest taka sama.

## <a name="see-also"></a>Zobacz także

[\<thread>](../standard-library/thread.md)
