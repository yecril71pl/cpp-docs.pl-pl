---
title: Operatory &lt;Chrono&gt;
ms.date: 11/04/2016
f1_keywords:
- chrono/std::operator modulo
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
ms.openlocfilehash: 398e2429c38cffb454c7b510aa5ab44fbe4cfef6
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865206"
---
# <a name="ltchronogt-operators"></a>Operatory &lt;Chrono&gt;

## <a name="operator-"></a>zakład

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

\ *lewo*
Lewy `duration` lub `time_point` obiektu.

*Prawa*\
Właściwy `duration` lub `time_point` obiektu.

\ *czasu*
Obiekt `time_point`.

Czas *trwania*\
Obiekt `duration`.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja zwraca obiekt `duration`, którego długość interwału jest różnica między przedziałami czasu dwóch argumentów.

Druga funkcja zwraca obiekt `time_point`, który reprezentuje punkt w czasie, który jest przewidziany przez negację przedziału czasu, który jest reprezentowany przez czas *trwania*, od punktu w czasie, który jest określony w *czasie*.

Trzecia funkcja zwraca obiekt `duration`, który reprezentuje przedział czasu od *lewej* do *prawej*.

## <a name="op_neq"></a>operator! =

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

\ *lewo*
Lewy `duration` lub `time_point` obiektu.

*Prawa*\
Właściwy `duration` lub `time_point` obiektu.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca `!(Left == Right)`.

## <a name="op_star"></a>zakład

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

Czas *trwania*\
Obiekt `duration`.

*Iloczyn*\
Wartość całkowita.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca obiekt `duration`, którego długość interwału jest *iloczyn* pomnożona przez długość czasu *trwania*.

Chyba że `is_convertible<Rep2, common_type<Rep1, Rep2>>`*ma wartość true*, Pierwsza funkcja nie bierze udziału w przeciążeniu. Aby uzyskać więcej informacji, zobacz [< type_traits >](../standard-library/type-traits.md).

Jeśli `is_convertible<Rep1, common_type<Rep1, Rep2>>`*ma wartość true*, druga funkcja nie bierze udziału w przeciążeniu. Aby uzyskać więcej informacji, zobacz [< type_traits >](../standard-library/type-traits.md).

## <a name="op_div"></a>zakład

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

Czas *trwania*\
Obiekt `duration`.

\ *DIV*
Wartość całkowita.

\ *lewo*
Obiekt `duration` po lewej stronie.

*Prawa*\
Właściwy `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator zwraca obiekt czasu trwania, którego długość interwału jest długością *podzieloną* przez wartość *DIV*.

Drugi operator zwraca stosunek długości interwału od *lewej* do *prawej*.

Chyba że `is_convertible<Rep2, common_type<Rep1, Rep2>>`ma *wartość true*, a `Rep2` nie jest wystąpieniem `duration`, Pierwszy operator nie uczestniczy w rozpoznawaniu przeciążenia. Aby uzyskać więcej informacji, zobacz [< type_traits >](../standard-library/type-traits.md).

## <a name="op_add"></a>operator +

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

\ *lewo*
Lewy `duration` lub `time_point` obiektu.

*Prawa*\
Właściwy `duration` lub `time_point` obiektu.

\ *czasu*
Obiekt `time_point`.

Czas *trwania*\
Obiekt `duration`.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja zwraca obiekt `duration`, który ma interwał czasu, który jest równy sumie interwałów od *lewej* do *prawej*.

Drugie i trzecie funkcje zwracają `time_point` obiektu, który reprezentuje punkt w czasie, który jest przemieszczenia, przez interwał czasu *trwania*od momentu w *czasie.*

## <a name="op_lt"></a>&lt; operatora

Określa, czy jeden obiekt [czasu trwania](../standard-library/duration-class.md) lub [time_point](../standard-library/time-point-class.md) jest mniejszy niż inny obiekt `duration` lub `time_point`.

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

\ *lewo*
Lewy `duration` lub `time_point` obiektu.

*Prawa*\
Właściwy `duration` lub `time_point` obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja zwraca **wartość true** , jeśli długość interwału *po lewej stronie* jest mniejsza niż długość interwału *po prawej stronie*. W przeciwnym razie funkcja zwraca **wartość false**.

Druga funkcja zwraca **wartość true** , jeśli *Left* poprzedza *prawo*. W przeciwnym razie funkcja zwraca **wartość false**.

## <a name="op_lt_eq"></a>&lt;operatora =

Określa, czy jeden obiekt [czasu trwania](../standard-library/duration-class.md) lub [time_point](../standard-library/time-point-class.md) jest mniejszy lub równy innemu `duration` lub `time_point` obiektu.

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

\ *lewo*
Lewy `duration` lub `time_point` obiektu.

*Prawa*\
Właściwy `duration` lub `time_point` obiektu.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca `!(Right < Left)`.

## <a name="op_eq_eq"></a>operator = =

Określa, czy dwa `duration` obiekty reprezentują przedziały czasu mające taką samą długość, czy dwa obiekty `time_point` reprezentują ten sam punkt w czasie.

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

\ *lewo*
Lewy `duration` lub `time_point` obiektu.

*Prawa*\
Właściwy `duration` lub `time_point` obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja zwraca **wartość true** , jeśli *Left* i *Right* reprezentuje przedziały czasu, które mają tę samą długość. W przeciwnym razie funkcja zwraca **wartość false**.

Druga funkcja zwraca **wartość true** , jeśli *Left* i *Right* reprezentuje ten sam punkt w czasie. W przeciwnym razie funkcja zwraca **wartość false**.

## <a name="op_gt"></a>&gt; operatora

Określa, czy jeden obiekt [czasu trwania](../standard-library/duration-class.md) lub [time_point](../standard-library/time-point-class.md) jest większy niż inny obiekt `duration` lub `time_point`.

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

\ *lewo*
Lewy `duration` lub `time_point` obiektu.

*Prawa*\
Właściwy `duration` lub `time_point` obiektu.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca `Right < Left`.

## <a name="op_gt_eq"></a>&gt;operatora =

Określa, czy jeden obiekt [czasu trwania](../standard-library/duration-class.md) lub [time_point](../standard-library/time-point-class.md) jest większy lub równy innemu `duration` lub `time_point` obiektu.

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

\ *lewo*
Lewy `duration` lub `time_point` obiektu.

*Prawa*\
Właściwy `duration` lub `time_point` obiektu.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca `!(Left < Right)`.

## <a name="op_modulo"></a>modulo operatorów

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

Czas *trwania*\
Obiekt `duration`.

\ *DIV*
Wartość całkowita.

\ *lewo*
Obiekt `duration` po lewej stronie.

*Prawa*\
Właściwy `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja zwraca obiekt `duration`, którego długość interwału jest *równa wartość elementu* *DIV*modulo.

Druga funkcja zwraca wartość, która reprezentuje *lewe* *prawo*modulo.
