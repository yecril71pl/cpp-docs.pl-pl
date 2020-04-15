---
title: '&lt;operatorzy gwintów&gt;'
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
ms.openlocfilehash: 6312d14dc681736ee396d5c7af6c50ba8d72cd3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375830"
---
# <a name="ltthreadgt-operators"></a>&lt;operatorzy gwintów&gt;

||||
|-|-|-|
|[operator!=](#op_neq)|[Operator&gt;](#op_gt)|[Operator&gt;=](#op_gt_eq)|
|[Operator&lt;](#op_lt)|[Operator&lt;&lt;](#op_lt_lt)|[Operator&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|

## <a name="operatorgt"></a><a name="op_gt_eq"></a>Operator&gt;=

Określa, czy `thread::id` jeden obiekt jest większy lub równy innemu.

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Lewej*\
Lewy `thread::id` obiekt.

*Prawo*\
Właściwy `thread::id` obiekt.

### <a name="return-value"></a>Wartość zwracana

`!(Left < Right)`

### <a name="remarks"></a>Uwagi

Ta funkcja nie zgłasza żadnych wyjątków.

## <a name="operatorgt"></a><a name="op_gt"></a>Operator&gt;

Określa, czy `thread::id` jeden obiekt jest większy niż inny.

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Lewej*\
Lewy `thread::id` obiekt.

*Prawo*\
Właściwy `thread::id` obiekt.

### <a name="return-value"></a>Wartość zwracana

`Right < Left`

### <a name="remarks"></a>Uwagi

Ta funkcja nie zgłasza żadnych wyjątków.

## <a name="operatorlt"></a><a name="op_lt_eq"></a>Operator&lt;=

Określa, czy `thread::id` jeden obiekt jest mniejszy lub równy innemu.

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Lewej*\
Lewy `thread::id` obiekt.

*Prawo*\
Właściwy `thread::id` obiekt.

### <a name="return-value"></a>Wartość zwracana

`!(Right < Left)`

### <a name="remarks"></a>Uwagi

Ta funkcja nie zgłasza żadnych wyjątków.

## <a name="operatorlt"></a><a name="op_lt"></a>Operator&lt;

Określa, czy `thread::id` jeden obiekt jest mniejszy niż inny.

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Lewej*\
Lewy `thread::id` obiekt.

*Prawo*\
Właściwy `thread::id` obiekt.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli *left* poprzedza *Right* w całkowitej kolejności; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Operator definiuje całkowitą kolejność na `thread::id` wszystkich obiektach. Obiekty te mogą służyć jako klucze w kontenerach zespolonych.

Ta funkcja nie zgłasza żadnych wyjątków.

## <a name="operator"></a><a name="op_neq"></a>operator!=

Porównuje dwa `thread::id` obiekty dla nierówności.

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Lewej*\
Lewy `thread::id` obiekt.

*Prawo*\
Właściwy `thread::id` obiekt.

### <a name="return-value"></a>Wartość zwracana

`!(Left == Right)`

### <a name="remarks"></a>Uwagi

Ta funkcja nie zgłasza żadnych wyjątków.

## <a name="operator"></a><a name="op_eq_eq"></a>operator==

Porównuje dwa `thread::id` obiekty dla równości.

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Lewej*\
Lewy `thread::id` obiekt.

*Prawo*\
Właściwy `thread::id` obiekt.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli dwa obiekty reprezentują ten sam wątek wykonywania lub jeśli żaden z obiektów reprezentuje wątek wykonywania; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja nie zgłasza żadnych wyjątków.

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>Operator&lt;&lt;

Wstawia reprezentację `thread::id` tekstową obiektu do strumienia.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>Parametry

*Ostr*\
Obiekt [basic_ostream.](../standard-library/basic-ostream-class.md)

*Identyfikator*\
Obiekt `thread::id`.

### <a name="return-value"></a>Wartość zwracana

*Ostr*.

### <a name="remarks"></a>Uwagi

Ta funkcja wstawia *identyfikator* do *ostr*.

Jeśli `thread::id` dwa obiekty porównują się równe, wstawione reprezentacje tekstowe tych obiektów są takie same.

## <a name="see-also"></a>Zobacz też

[\<>gwintów](../standard-library/thread.md)
