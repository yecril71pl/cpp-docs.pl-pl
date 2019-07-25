---
title: '&lt;Operatory&gt; wątku'
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
ms.openlocfilehash: c0593b8016cf45abe64114958ccda84eb3704844
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458442"
---
# <a name="ltthreadgt-operators"></a>&lt;Operatory&gt; wątku

||||
|-|-|-|
|[operator!=](#op_neq)|[zakład&gt;](#op_gt)|[zakład&gt;=](#op_gt_eq)|
|[zakład&lt;](#op_lt)|[zakład&lt;&lt;](#op_lt_lt)|[zakład&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|

## <a name="op_gt_eq"></a>zakład&gt;=

Określa, czy `thread::id` jeden obiekt jest większy lub równy drugiemu.

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

## <a name="op_gt"></a>zakład&gt;

Określa, czy `thread::id` jeden obiekt jest większy niż inny.

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

## <a name="op_lt_eq"></a>zakład&lt;=

Określa, czy `thread::id` jeden obiekt jest mniejszy lub równy drugiemu.

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

## <a name="op_lt"></a>zakład&lt;

Określa, czy `thread::id` jeden obiekt jest mniejszy niż inny.

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

**wartość true** , jeśli *Left* poprzedza *prawo* w całkowitej kolejności; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Operator definiuje całkowitą kolejność dla wszystkich `thread::id` obiektów. Te obiekty mogą być używane jako klucze w kontenerach asocjacyjnych.

Ta funkcja nie generuje żadnych wyjątków.

## <a name="op_neq"></a>operator! =

Porównuje `thread::id` dwa obiekty pod kątem nierówności.

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

## <a name="op_eq_eq"></a>operator = =

Porównuje `thread::id` dwa obiekty pod kątem równości.

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

**ma wartość true** , jeśli dwa obiekty reprezentują ten sam wątek wykonywania lub jeśli żaden z obiektów nie reprezentuje wątku wykonywania; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja nie generuje żadnych wyjątków.

## <a name="op_lt_lt"></a>zakład&lt;&lt;

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
`thread::id` Obiekt.

### <a name="return-value"></a>Wartość zwracana

*Ostr*.

### <a name="remarks"></a>Uwagi

Ta funkcja wstawia *Identyfikator* do *ostr*.

Jeśli dwa `thread::id` obiekty są porównywane jako równe, wstawiona tekstowa reprezentacja tych obiektów jest taka sama.

## <a name="see-also"></a>Zobacz także

[\<> wątku](../standard-library/thread.md)
