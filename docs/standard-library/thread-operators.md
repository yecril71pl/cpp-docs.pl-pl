---
title: '&lt;Wątek&gt; operatorów'
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
ms.openlocfilehash: 5a2fd845598ac9f9c983bf53cbd7665ef66ffb70
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636907"
---
# <a name="ltthreadgt-operators"></a>&lt;Wątek&gt; operatorów

||||
|-|-|-|
|[operator!=](#op_neq)|[Operator&gt;](#op_gt)|[Operator&gt;=](#op_gt_eq)|
|[Operator&lt;](#op_lt)|[Operator&lt;&lt;](#op_lt_lt)|[Operator&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|

## <a name="op_gt_eq"></a>  Operator&gt;=

Określa, czy jeden `thread::id` obiekt jest większy niż lub równy innemu.

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*po lewej stronie*<br/>
Po lewej stronie `thread::id` obiektu.

*po prawej stronie*<br/>
Po prawej stronie `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwracana

`!(Left < Right)`

### <a name="remarks"></a>Uwagi

Ta funkcja nie generuje żadnych wyjątków.

## <a name="op_gt"></a>  Operator&gt;

Określa, czy jeden `thread::id` obiekt jest większy niż inny.

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*po lewej stronie*<br/>
Po lewej stronie `thread::id` obiektu.

*po prawej stronie*<br/>
Po prawej stronie `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwracana

`Right < Left`

### <a name="remarks"></a>Uwagi

Ta funkcja nie generuje żadnych wyjątków.

## <a name="op_lt_eq"></a>  Operator&lt;=

Określa, czy jeden `thread::id` obiekt jest mniejszy niż lub równe drugiemu.

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*po lewej stronie*<br/>
Po lewej stronie `thread::id` obiektu.

*po prawej stronie*<br/>
Po prawej stronie `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwracana

`!(Right < Left)`

### <a name="remarks"></a>Uwagi

Ta funkcja nie generuje żadnych wyjątków.

## <a name="op_lt"></a>  Operator&lt;

Określa, czy jeden `thread::id` obiekt jest mniejszy niż inny.

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*po lewej stronie*<br/>
Po lewej stronie `thread::id` obiektu.

*po prawej stronie*<br/>
Po prawej stronie `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *po lewej stronie* poprzedza *po prawej stronie* w kolejności całkowita; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Operator definiuje kolejność całkowita we wszystkich `thread::id` obiektów. Te obiekty może służyć jako klucze w kontenerach asocjacyjnych.

Ta funkcja nie generuje żadnych wyjątków.

## <a name="op_neq"></a>  operator! =

Porównuje dwa `thread::id` obiekty pod kątem nierówności.

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*po lewej stronie*<br/>
Po lewej stronie `thread::id` obiektu.

*po prawej stronie*<br/>
Po prawej stronie `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwracana

`!(Left == Right)`

### <a name="remarks"></a>Uwagi

Ta funkcja nie generuje żadnych wyjątków.

## <a name="op_eq_eq"></a>  operator ==

Porównuje dwa `thread::id` obiekty pod kątem równości.

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*po lewej stronie*<br/>
Po lewej stronie `thread::id` obiektu.

*po prawej stronie*<br/>
Po prawej stronie `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** czy dwa obiekty reprezentują ten sam wątek wykonywania, czy żaden obiekt reprezentuje wątek wykonywania; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja nie generuje żadnych wyjątków.

## <a name="op_lt_lt"></a>  Operator&lt;&lt;

Wstawia tekstowa reprezentacja `thread::id` obiektu do strumienia.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>Parametry

*Ostr*<br/>
A [basic_ostream](../standard-library/basic-ostream-class.md) obiektu.

*Id*<br/>
Element `thread::id` obiektu.

### <a name="return-value"></a>Wartość zwracana

*OSTR*.

### <a name="remarks"></a>Uwagi

Ta funkcja wstawia *identyfikator* do *Ostr*.

Jeśli dwa `thread::id` obiekty są sobie równe, reprezentujący wstawiony tekst te obiekty są takie same.

## <a name="see-also"></a>Zobacz także

[\<Wątek >](../standard-library/thread.md)<br/>
