---
title: Operatory&gt; wątku &lt;
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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420723"
---
# <a name="ltthreadgt-operators"></a>Operatory&gt; wątku &lt;

||||
|-|-|-|
|[operator!=](#op_neq)|[&gt; operatora](#op_gt)|[&gt;operatora =](#op_gt_eq)|
|[&lt; operatora](#op_lt)|[&lt;operatora &lt;](#op_lt_lt)|[&lt;operatora =](#op_lt_eq)|
|[operator = =](#op_eq_eq)|

## <a name="op_gt_eq"></a>&gt;operatora =

Określa, czy jeden `thread::id` obiektu jest większy lub równy drugiemu.

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt `thread::id` po lewej stronie.

*Prawa*\
Właściwy `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwrócona

`!(Left < Right)`

### <a name="remarks"></a>Uwagi

Ta funkcja nie generuje żadnych wyjątków.

## <a name="op_gt"></a>&gt; operatora

Określa, czy jeden `thread::id` obiektu jest większy niż inny.

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt `thread::id` po lewej stronie.

*Prawa*\
Właściwy `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwrócona

`Right < Left`

### <a name="remarks"></a>Uwagi

Ta funkcja nie generuje żadnych wyjątków.

## <a name="op_lt_eq"></a>&lt;operatora =

Określa, czy jeden `thread::id` obiektu jest mniejszy lub równy drugiemu.

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt `thread::id` po lewej stronie.

*Prawa*\
Właściwy `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwrócona

`!(Right < Left)`

### <a name="remarks"></a>Uwagi

Ta funkcja nie generuje żadnych wyjątków.

## <a name="op_lt"></a>&lt; operatora

Określa, czy jeden `thread::id` obiektu jest mniejszy niż inny.

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt `thread::id` po lewej stronie.

*Prawa*\
Właściwy `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwrócona

**wartość true** , jeśli *Left* poprzedza *prawo* w całkowitej kolejności; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Operator definiuje łączną kolejność wszystkich obiektów `thread::id`. Te obiekty mogą być używane jako klucze w kontenerach asocjacyjnych.

Ta funkcja nie generuje żadnych wyjątków.

## <a name="op_neq"></a>operator! =

Porównuje dwa obiekty `thread::id` pod kątem nierówności.

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt `thread::id` po lewej stronie.

*Prawa*\
Właściwy `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwrócona

`!(Left == Right)`

### <a name="remarks"></a>Uwagi

Ta funkcja nie generuje żadnych wyjątków.

## <a name="op_eq_eq"></a>operator = =

Porównuje dwa obiekty `thread::id` dla równości.

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt `thread::id` po lewej stronie.

*Prawa*\
Właściwy `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli dwa obiekty reprezentują ten sam wątek wykonywania lub jeśli żaden z obiektów nie reprezentuje wątku wykonywania; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja nie generuje żadnych wyjątków.

## <a name="op_lt_lt"></a>&lt;operatora &lt;

Wstawia tekstową reprezentację obiektu `thread::id` w strumieniu.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>Parametry

*Ostr*\
Obiekt [basic_ostream](../standard-library/basic-ostream-class.md) .

*Identyfikator*\
Obiekt `thread::id`.

### <a name="return-value"></a>Wartość zwrócona

*Ostr*.

### <a name="remarks"></a>Uwagi

Ta funkcja wstawia *Identyfikator* do *ostr*.

Jeśli dwa `thread::id` obiekty porównują równe, wstawiona tekstowa reprezentacja tych obiektów jest taka sama.

## <a name="see-also"></a>Zobacz też

[> wątku \<](../standard-library/thread.md)
