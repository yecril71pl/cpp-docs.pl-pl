---
title: '&lt;chrono&gt; operatorów'
ms.date: 11/04/2016
f1_keywords:
- chrono/std::operator modulo
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
ms.openlocfilehash: d86fbf15313c25dd28b9220c654750ee8bc96d81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631858"
---
# <a name="ltchronogt-operators"></a>&lt;chrono&gt; operatorów

||||
|-|-|-|
|[Operator modulo](#op_modulo)|[operator!=](#op_neq)|[Operator&gt;](#op_gt)|
|[Operator&gt;=](#op_gt_eq)|[Operator&lt;](#op_lt)|[Operator&lt;=](#op_lt_eq)|
|[operator *](#op_star)|[operator +](#op_add)|[operator-](#operator-)|
|[operator /](#op_div)|[operator==](#op_eq_eq)|

## <a name="operator-"></a>  operator-

Operator odejmowania lub negacji [czas trwania](../standard-library/duration-class.md) i [time_point](../standard-library/time-point-class.md) obiektów.

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

*po lewej stronie*<br/>
Po lewej stronie `duration` lub `time_point` obiektu.

*po prawej stronie*<br/>
Po prawej stronie `duration` lub `time_point` obiektu.

*czas*<br/>
Element `time_point` obiektu.

*Czas trwania*<br/>
Element `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja zwraca `duration` obiektu, którego długość interwału jest różnicą między odstępami czasowymi dwóch argumentów.

Druga funkcja zwraca `time_point` obiekt, który reprezentuje punkt w czasie, który jest przesunięty przez negację interwału czasu, który jest reprezentowany przez *czas trwania*, od punktu w czasie, który jest określony przez *czasu*.

Trzecia funkcja zwraca `duration` obiekt, który reprezentuje odstęp czasu między *po lewej stronie* i *po prawej stronie*.

## <a name="op_neq"></a>  operator! =

Operator nierówności dla [czas trwania](../standard-library/duration-class.md) lub [time_point](../standard-library/time-point-class.md) obiektów.

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

*po lewej stronie*<br/>
Po lewej stronie `duration` lub `time_point` obiektu.

*po prawej stronie*<br/>
Po prawej stronie `duration` lub `time_point` obiektu.

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

*Czas trwania*<br/>
Element `duration` obiektu.

*Iloczyn*<br/>
Wartość całkowita.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca `duration` obiektu, którego długość interwału jest *iloczyn* pomnożona przez długość *czas trwania*.

Chyba że `is_convertible<Rep2, common_type<Rep1, Rep2>>` *prawdziwe*, pierwsza funkcja nie uczestniczy w przeciążeniu rozdzielczości. Aby uzyskać więcej informacji, zobacz [< type_traits >](../standard-library/type-traits.md).

Chyba że `is_convertible<Rep1, common_type<Rep1, Rep2>>` *prawdziwe*, druga funkcja nie uczestniczy w przeciążeniu rozdzielczości. Aby uzyskać więcej informacji, zobacz [< type_traits >](../standard-library/type-traits.md).

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

*Czas trwania*<br/>
Element `duration` obiektu.

*Div*<br/>
Wartość całkowita.

*po lewej stronie*<br/>
Po lewej stronie `duration` obiektu.

*po prawej stronie*<br/>
Po prawej stronie `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator zwraca obiekt czasu trwania, którego przedział długości jest długością *czas trwania* podzieloną przez wartość *Div*.

Drugi operator zwraca współczynnik długości interwału *po lewej stronie* i *po prawej stronie*.

Chyba że `is_convertible<Rep2, common_type<Rep1, Rep2>>` *prawdziwe*, i `Rep2` nie jest egzemplarz o `duration`, pierwszy operator nie uczestniczy w przeciążeniu rozdzielczości. Aby uzyskać więcej informacji, zobacz [< type_traits >](../standard-library/type-traits.md).

## <a name="op_add"></a>  operator +

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

*po lewej stronie*<br/>
Po lewej stronie `duration` lub `time_point` obiektu.

*po prawej stronie*<br/>
Po prawej stronie `duration` lub `time_point` obiektu.

*czas*<br/>
Element `time_point` obiektu.

*Czas trwania*<br/>
Element `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja zwraca `duration` obiekt, który ma przedział czasu, który jest równy sumie odstępów *po lewej stronie* i *po prawej stronie*.

Drugi i trzeci funkcje zwracają `time_point` obiekt, który reprezentuje punkt w czasie, który jest przesunięty od przedziału *czas trwania*, od punktu w czasie *czasu*.

## <a name="op_lt"></a>  Operator&lt;

Określa, czy jeden [czas trwania](../standard-library/duration-class.md) lub [time_point](../standard-library/time-point-class.md) obiekt jest mniejszy niż inny `duration` lub `time_point` obiektu.

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

*po lewej stronie*<br/>
Po lewej stronie `duration` lub `time_point` obiektu.

*po prawej stronie*<br/>
Po prawej stronie `duration` lub `time_point` obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja zwraca **true** Jeśli długość interwału *po lewej stronie* jest mniejsza niż długość interwału *po prawej stronie*. W przeciwnym razie funkcja zwraca **false**.

Druga funkcja zwraca **true** Jeśli *po lewej stronie* poprzedza *po prawej stronie*. W przeciwnym razie funkcja zwraca **false**.

## <a name="op_lt_eq"></a>  Operator&lt;=

Określa, czy jeden [czas trwania](../standard-library/duration-class.md) lub [time_point](../standard-library/time-point-class.md) obiekt jest mniejszy niż lub równy innemu `duration` lub `time_point` obiektu.

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

*po lewej stronie*<br/>
Po lewej stronie `duration` lub `time_point` obiektu.

*po prawej stronie*<br/>
Po prawej stronie `duration` lub `time_point` obiektu.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca `!(Right < Left)`.

## <a name="op_eq_eq"></a>  operator ==

Określa, czy dwa `duration` obiekty reprezentują przedziały czasowe, które mają taką samą długość, czy dwa `time_point` obiekty reprezentują tego samego punktu w czasie.

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

*po lewej stronie*<br/>
Po lewej stronie `duration` lub `time_point` obiektu.

*po prawej stronie*<br/>
Po prawej stronie `duration` lub `time_point` obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja zwraca **true** Jeśli *po lewej stronie* i *po prawej stronie* reprezentują przedziały czasowe, które mają tę samą długość. W przeciwnym razie funkcja zwraca **false**.

Druga funkcja zwraca **true** Jeśli *po lewej stronie* i *po prawej stronie* reprezentują tego samego punktu w czasie. W przeciwnym razie funkcja zwraca **false**.

## <a name="op_gt"></a>  Operator&gt;

Określa, czy jeden [czas trwania](../standard-library/duration-class.md) lub [time_point](../standard-library/time-point-class.md) obiekt jest większy niż inny `duration` lub `time_point` obiektu.

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

*po lewej stronie*<br/>
Po lewej stronie `duration` lub `time_point` obiektu.

*po prawej stronie*<br/>
Po prawej stronie `duration` lub `time_point` obiektu.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca `Right < Left`.

## <a name="op_gt_eq"></a>  Operator&gt;=

Określa, czy jeden [czas trwania](../standard-library/duration-class.md) lub [time_point](../standard-library/time-point-class.md) obiekt jest większy niż lub równy innemu `duration` lub `time_point` obiektu.

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

*po lewej stronie*<br/>
Po lewej stronie `duration` lub `time_point` obiektu.

*po prawej stronie*<br/>
Po prawej stronie `duration` lub `time_point` obiektu.

### <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca `!(Left < Right)`.

## <a name="op_modulo"></a>  Operator modulo

Operator modulo operacji na [czas trwania](../standard-library/duration-class.md) obiektów.

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

*Czas trwania*<br/>
Element `duration` obiektu.

*Div*<br/>
Wartość całkowita.

*po lewej stronie*<br/>
Po lewej stronie `duration` obiektu.

*po prawej stronie*<br/>
Po prawej stronie `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja zwraca `duration` obiektu, którego długość interwału jest *czas trwania* modulo *Div*.

Druga funkcja zwraca wartość, która reprezentuje *po lewej stronie* modulo *po prawej stronie*.

## <a name="see-also"></a>Zobacz także

[\<chrono>](../standard-library/chrono.md)<br/>
