---
title: '&lt;chrono&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- chrono/std::operator modulo
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
ms.openlocfilehash: 1ac1051ddaa67dc1970119586ecb9e937583c58a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33847403"
---
# <a name="ltchronogt-operators"></a>&lt;chrono&gt; operatory

||||
|-|-|-|
|[Operator modulo](#op_modulo)|[operator!=](#op_neq)|[Operator&gt;](#op_gt)|
|[Operator&gt;=](#op_gt_eq)|[Operator&lt;](#op_lt)|[Operator&lt;=](#op_lt_eq)|
|[operator *](#op_star)|[operator +](#op_add)|[operator-](#operator-)|
|[operator /](#op_div)|[operator==](#op_eq_eq)|

## <a name="operator-"></a>  operator-

Operator odejmowania lub Negacja [czas trwania](../standard-library/duration-class.md) i [time_point —](../standard-library/time-point-class.md) obiektów.

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

`Left` Po lewej stronie `duration` lub `time_point` obiektu.

`Right` Prawo `duration` lub `time_point` obiektu.

`Time` A `time_point` obiektu.

`Dur` A `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca pierwszą funkcję `duration` obiektów o długości interwału różni się od przedziały czasu dwóch argumentów.

Zwraca funkcję drugi `time_point` obiekt, który reprezentuje punkt w czasie, który jest przesuwane, za pomocą Negacja przedział czasu, który jest reprezentowany przez `Dur`, od punktu w czasie określonym przez `Time`.

Zwraca funkcję trzeci `duration` obiekt, który reprezentuje odstęp czasu między `Left` i `Right`.

## <a name="op_neq"></a>  operator! =

Operator nierówności [czas trwania](../standard-library/duration-class.md) lub [time_point —](../standard-library/time-point-class.md) obiektów.

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

`Left` Po lewej stronie `duration` lub `time_point` obiektu.

`Right` Prawo `duration` lub `time_point` obiektu.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca `!(Left == Right)`.

## <a name="op_star"></a>  operator *

Operator mnożenia dla [czas trwania](../standard-library/chrono-operators.md#op_star) obiektów.

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

`Dur` A `duration` obiektu.

`Mult` Wartością całkowitą.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca `duration` obiektów o długości interwału `Mult` pomnożona przez długości `Dur`.

O ile `is_convertible<Rep2, common_type<Rep1, Rep2>>` *jest spełniony*, pierwszej funkcji nie uczestniczy w Rozpoznanie przeciążenia. Aby uzyskać więcej informacji, sssee [< type_traits >](../standard-library/type-traits.md).

O ile `is_convertible<Rep1, common_type<Rep1, Rep2>>` *jest spełniony*, funkcji second nie uczestniczy w Rozpoznanie przeciążenia. Aby uzyskać więcej informacji, zobacz [< type_traits >](../standard-library/type-traits.md).

## <a name="op_div"></a>  operator /

Operator dzielenia dla [czas trwania](../standard-library/chrono-operators.md#op_star) obiektów.

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

`Dur` A `duration` obiektu.

`Div` Wartością całkowitą.

`Left` Po lewej stronie `duration` obiektu.

`Right` Prawo `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator zwraca obiekt czas trwania odstępach długość wynosi długość `Dur` podzielona przez wartość `Div`.

Drugi operator zwraca stosunek długości interwału `Left` i `Right`.

O ile `is_convertible<Rep2, common_type<Rep1, Rep2>>` *jest spełniony*, i `Rep2` nie jest instancją typu `duration`, pierwszy operator nie uczestniczy w Rozpoznanie przeciążenia. Aby uzyskać więcej informacji, zobacz [< type_traits >](../standard-library/type-traits.md).

## <a name="op_add"></a>  operator +

Dodaje [czas trwania](../standard-library/duration-class.md) i [time_point —](../standard-library/time-point-class.md) obiektów.

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

`Left` Po lewej stronie `duration` lub `time_point` obiektu.

`Right` Prawo `duration` lub `time_point` obiektu.

`Time` A `time_point` obiektu.

`Dur` A `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca pierwszą funkcję `duration` obiektu, który ma przedział czasu, która jest równa sumie interwały `Left` i `Right`.

Drugi i trzeci zwracają `time_point` obiekt, który reprezentuje punkt w czasie, który jest przesuwane, za pomocą interwał `Dur`, od punktu w czasie `Time`.

## <a name="op_lt"></a>  Operator&lt;

Określa, czy co najmniej [czas trwania](../standard-library/duration-class.md) lub [time_point —](../standard-library/time-point-class.md) obiekt jest mniejszy niż innego `duration` lub `time_point` obiektu.

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

`Left` Po lewej stronie `duration` lub `time_point` obiektu.

`Right` Prawo `duration` lub `time_point` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca pierwszą funkcję `true` Jeśli długość interwału `Left` jest mniejsza od długości interwału `Right`. W przeciwnym razie funkcja zwraca `false`.

Zwraca funkcję drugi `true` Jeśli `Left` poprzedza `Right`. W przeciwnym razie funkcja zwraca `false`.

## <a name="op_lt_eq"></a>  Operator&lt;=

Określa, czy co najmniej [czas trwania](../standard-library/duration-class.md) lub [time_point —](../standard-library/time-point-class.md) obiekt jest mniejszy niż lub równy do innego `duration` lub `time_point` obiektu.

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

`Left` Po lewej stronie `duration` lub `time_point` obiektu.

`Right` Prawo `duration` lub `time_point` obiektu.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca `!(Right < Left)`.

## <a name="op_eq_eq"></a>  operator ==

Określa, czy dwa `duration` reprezentować przedziały czasu, które mają taką samą długość lub czy dwa `time_point` obiekty reprezentują tego samego punktu w czasie.

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

`Left` Po lewej stronie `duration` lub `time_point` obiektu.

`Right` Prawo `duration` lub `time_point` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca pierwszą funkcję `true` Jeśli `Left` i `Right` reprezentują przedziały czasu, które mają taką samą długość. W przeciwnym razie funkcja zwraca `false`.

Zwraca funkcję drugi `true` Jeśli `Left` i `Right` reprezentują tego samego punktu w czasie. W przeciwnym razie funkcja zwraca `false`.

## <a name="op_gt"></a>  Operator&gt;

Określa, czy co najmniej [czas trwania](../standard-library/duration-class.md) lub [time_point —](../standard-library/time-point-class.md) obiekt jest większy niż innego `duration` lub `time_point` obiektu.

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

`Left` Po lewej stronie `duration` lub `time_point` obiektu.

`Right` Prawo `duration` lub `time_point` obiektu.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca `Right < Left`.

## <a name="op_gt_eq"></a>  Operator&gt;=

Określa, czy co najmniej [czas trwania](../standard-library/duration-class.md) lub [time_point —](../standard-library/time-point-class.md) obiektu jest większa lub równa innej `duration` lub `time_point` obiektu.

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

`Left` Po lewej stronie `duration` lub `time_point` obiektu.

`Right` Prawo `duration` lub `time_point` obiektu.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca `!(Left < Right)`.

## <a name="op_modulo"></a>  Operator modulo

Operator modulo operacje na [czas trwania](../standard-library/duration-class.md) obiektów.

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

`Dur` A `duration` obiektu.

`Div` Wartością całkowitą.

`Left` Po lewej stronie `duration` obiektu.

`Right` Prawo `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca pierwszą funkcję `duration` obiektów o długości interwału `Dur` modulo `Div`.

Druga funkcja zwraca wartość, która reprezentuje `Left` modulo `Right`.

## <a name="see-also"></a>Zobacz także

[\<chrono>](../standard-library/chrono.md)<br/>
