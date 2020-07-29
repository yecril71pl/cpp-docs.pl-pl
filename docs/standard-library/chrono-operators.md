---
title: '&lt;&gt;Operatory Chrono'
ms.date: 11/04/2016
f1_keywords:
- chrono/std::operator modulo
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
ms.openlocfilehash: 82f0b7b0f55cf4d71ef7c0ed92a55ca0fa1139e0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230146"
---
# <a name="ltchronogt-operators"></a>&lt;&gt;Operatory Chrono

## <a name="operator-"></a><a name="operator-"></a>zakład

Operator odejmowania lub negacji [czasu trwania](../standard-library/duration-class.md) i [time_point](../standard-library/time-point-class.md) obiektów.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type
   operator-(
       const duration<Rep1, Period1>& Left,
       cconst duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Rep2, class Period2>
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type
   operator-(
       const time_point<Clock, Duration1>& Time,
       const duration<Rep2, Period2>& Dur);

template <class Clock, class Duration1, class Duration2>
constexpr typename common_type<Duration1, Duration2>::type
   operator-(
       const time_point<Clock, Duration1>& Left,
       const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parametry

*Lewym*\
Lewo `duration` lub `time_point` obiekt.

*Kliknij*\
Prawo `duration` lub `time_point` obiekt.

*Pierwszym*\
Obiekt `time_point`.

*Trwania*\
Obiekt `duration`.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja zwraca obiekt, `duration` którego długość interwału jest różnica między przedziałami czasu dwóch argumentów.

Druga funkcja zwraca `time_point` obiekt, który reprezentuje punkt w czasie, który jest przewidziany przez negację przedziału czasu, który jest reprezentowany przez *czas* *trwania*, od momentu określonego w czasie.

Trzecia funkcja zwraca `duration` obiekt, który reprezentuje przedział czasu od *lewej* do *prawej*.

## <a name="operator"></a><a name="op_neq"></a>operator! =

Operator nierówności dla obiektów [Duration](../standard-library/duration-class.md) lub [time_point](../standard-library/time-point-class.md) .

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator!=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator!=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parametry

*Lewym*\
Lewo `duration` lub `time_point` obiekt.

*Kliknij*\
Prawo `duration` lub `time_point` obiekt.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca wartość `!(Left == Right)` .

## <a name="operator"></a><a name="op_star"></a>zakład

Operator mnożenia dla obiektów [czasu trwania](../standard-library/chrono-operators.md#op_star) .

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1>
   operator*(
      const duration<Rep1, Period1>& Dur,
      const Rep2& Mult);

template <class Rep1, class Rep2, class Period2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period2>
   operator*(
       const Rep1& Mult,
       const duration<Rep2,
       Period2>& Dur);
```

### <a name="parameters"></a>Parametry

*Trwania*\
Obiekt `duration`.

*Iloczyn*\
Wartość całkowita.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca `duration` obiekt, którego długość interwału jest *iloczyn* pomnożona przez długość wartości czasu *trwania*.

O ile nie `is_convertible<Rep2, common_type<Rep1, Rep2>>` *ma wartości true*, Pierwsza funkcja nie uczestniczy w przeciążeniu do przeciążenia. Aby uzyskać więcej informacji, zobacz [<type_traits>](../standard-library/type-traits.md).

O ile nie `is_convertible<Rep1, common_type<Rep1, Rep2>>` *ma wartości true*, druga funkcja nie uczestniczy w rozpoznawaniu przeciążenia. Aby uzyskać więcej informacji, zobacz [<type_traits>](../standard-library/type-traits.md).

## <a name="operator"></a><a name="op_div"></a>zakład

Operator dzielenia dla obiektów [czasu trwania](../standard-library/chrono-operators.md#op_star) .

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1>
   operator/(
     const duration<Rep1, Period1>& Dur,
     const Rep2& Div);

template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<Rep1, Rep2>::type
   operator/(
     const duration<Rep1, Period1>& Left,
     const duration<Rep2, Period2>& Right);
```

### <a name="parameters"></a>Parametry

*Trwania*\
Obiekt `duration`.

*Służąc*\
Wartość całkowita.

*Lewym*\
Lewy `duration` obiekt.

*Kliknij*\
Prawidłowy `duration` obiekt.

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator zwraca obiekt czasu trwania, którego długość interwału jest długością *podzieloną* przez wartość *DIV*.

Drugi operator zwraca stosunek długości interwału od *lewej* do *prawej*.

Chyba że `is_convertible<Rep2, common_type<Rep1, Rep2>>` ma *wartość true*i `Rep2` nie jest wystąpieniem `duration` , Pierwszy operator nie bierze udziału w przeciążeniu. Aby uzyskać więcej informacji, zobacz [<type_traits>](../standard-library/type-traits.md).

## <a name="operator"></a><a name="op_add"></a>operator +

Dodaje [czas trwania](../standard-library/duration-class.md) i [time_point](../standard-library/time-point-class.md) obiektów.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type
   operator+(
      const duration<Rep1, Period1>& Left,
      const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Rep2, class Period2>
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type>
   operator+(
      const time_point<Clock, Duration1>& Time,
      const duration<Rep2, Period2>& Dur);

template <class Rep1, class Period1, class Clock, class Duration2>
time_point<Clock, constexpr typename common_type<duration<Rep1, Period1>, Duration2>::type>
   operator+(
      const duration<Rep1, Period1>& Dur,
      const time_point<Clock, Duration2>& Time);
```

### <a name="parameters"></a>Parametry

*Lewym*\
Lewo `duration` lub `time_point` obiekt.

*Kliknij*\
Prawo `duration` lub `time_point` obiekt.

*Pierwszym*\
Obiekt `time_point`.

*Trwania*\
Obiekt `duration`.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja zwraca `duration` obiekt, który ma interwał czasu, który jest równy sumie interwałów od *lewej* do *prawej*.

Druga i trzecia funkcja zwraca `time_point` obiekt, który reprezentuje punkt w czasie, który jest przemieszczenia przez interwał czasu *trwania*od momentu w *czasie*.

## <a name="operatorlt"></a><a name="op_lt"></a>zakład&lt;

Określa, czy jeden obiekt [czasu trwania](../standard-library/duration-class.md) lub [time_point](../standard-library/time-point-class.md) jest mniejszy niż inny `duration` `time_point` obiekt lub.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator<(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator<(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parametry

*Lewym*\
Lewo `duration` lub `time_point` obiekt.

*Kliknij*\
Prawo `duration` lub `time_point` obiekt.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja zwraca, **`true`** Jeśli długość interwału *po lewej stronie* jest mniejsza niż długość interwału *po prawej stronie*. W przeciwnym razie funkcja zwraca wartość **`false`** .

Druga funkcja zwraca **`true`** Jeśli *Left* poprzedza *prawo*. W przeciwnym razie funkcja zwraca wartość **`false`** .

## <a name="operatorlt"></a><a name="op_lt_eq"></a>zakład&lt;=

Określa, czy jeden obiekt [czasu trwania](../standard-library/duration-class.md) lub [time_point](../standard-library/time-point-class.md) jest mniejszy lub równy innemu `duration` lub `time_point` obiektowi.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator<=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator<=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parametry

*Lewym*\
Lewo `duration` lub `time_point` obiekt.

*Kliknij*\
Prawo `duration` lub `time_point` obiekt.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca wartość `!(Right < Left)` .

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

Określa, czy dwa `duration` obiekty reprezentują przedziały czasu mające taką samą długość, czy dwa `time_point` obiekty reprezentują ten sam punkt w czasie.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator==(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator==(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parametry

*Lewym*\
Lewo `duration` lub `time_point` obiekt.

*Kliknij*\
Prawo `duration` lub `time_point` obiekt.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja zwraca **`true`** Jeśli *po lewej* i *prawej stronie* przedziały czasu mają tę samą długość. W przeciwnym razie funkcja zwraca wartość **`false`** .

Druga funkcja zwraca **`true`** Jeśli *Left* i *Right* reprezentują ten sam punkt w czasie. W przeciwnym razie funkcja zwraca wartość **`false`** .

## <a name="operatorgt"></a><a name="op_gt"></a>zakład&gt;

Określa, czy jeden obiekt [czasu trwania](../standard-library/duration-class.md) lub [time_point](../standard-library/time-point-class.md) jest większy niż inny `duration` `time_point` obiekt lub.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator>(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator>(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parametry

*Lewym*\
Lewo `duration` lub `time_point` obiekt.

*Kliknij*\
Prawo `duration` lub `time_point` obiekt.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca wartość `Right < Left` .

## <a name="operatorgt"></a><a name="op_gt_eq"></a>zakład&gt;=

Określa, czy jeden obiekt [czasu trwania](../standard-library/duration-class.md) lub [time_point](../standard-library/time-point-class.md) jest większy lub równy innemu `duration` lub `time_point` obiektowi.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator>=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator>=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parametry

*Lewym*\
Lewo `duration` lub `time_point` obiekt.

*Kliknij*\
Prawo `duration` lub `time_point` obiekt.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca wartość `!(Left < Right)` .

## <a name="operator-modulo"></a><a name="op_modulo"></a>modulo operatorów

Operator dla operacji modulo na obiektach [czasu trwania](../standard-library/duration-class.md) .

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<Rep1, Period1, Rep2>::type
   operator%(
      const duration<Rep1, Period1>& Dur,
      const Rep2& Div);

template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, _Period1>, duration<Rep2, Period2>>::type
   operator%(
     const duration<Rep1, Period1>& Left,
     const duration<Rep2, Period2>& Right);
```

### <a name="parameters"></a>Parametry

*Trwania*\
Obiekt `duration`.

*Służąc*\
Wartość całkowita.

*Lewym*\
Lewy `duration` obiekt.

*Kliknij*\
Prawidłowy `duration` obiekt.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja zwraca obiekt, `duration` którego długość interwału jest *Dur* równy czasowi *DIV*modulo.

Druga funkcja zwraca wartość, która reprezentuje *lewe* *prawo*modulo.
