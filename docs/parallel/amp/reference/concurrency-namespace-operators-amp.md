---
title: Operatory przestrzeni nazw współbieżności (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: 03079f8899f3b13c8509e1affd10a82191b1817c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228482"
---
# <a name="concurrency-namespace-operators-amp"></a>Operatory przestrzeni nazw współbieżności (AMP)

||||
|-|-|-|
|[operator! =](#operator_neq)|[zakład](#operator_mod)|[zakład](#operator_star)|
|[operator +](#operator_add)|[zakład](#operator-)|[zakład](#operator_div)|
|[operator = =](#operator_eq_eq)|

## <a name="operator"></a><a name="operator_eq_eq"></a>operator = =

Określa, czy określone argumenty są równe.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
bool operator== (
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Ranga argumentów krotki.

*_Lhs*<br/>
Jedna z krotek do porównania.

*_Rhs*<br/>
Jedna z krotek do porównania.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli krotki są równe; w przeciwnym razie **`false`** .

## <a name="operator"></a><a name="operator_neq"></a>operator! =

Określa, czy określone argumenty nie są równe.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
bool operator!= (
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Ranga argumentów krotki.

*_Lhs*<br/>
Jedna z krotek do porównania.

*_Rhs*<br/>
Jedna z krotek do porównania.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli krotki nie są równe; w przeciwnym razie **`false`** .

## <a name="operator"></a><a name="operator_add"></a>operator +

Oblicza sumę elementów dla określonych argumentów.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Ranga argumentów krotki.

*_Lhs*<br/>
Jeden z argumentów do dodania.

*_Rhs*<br/>
Jeden z argumentów do dodania.

### <a name="return-value"></a>Wartość zwracana

Suma składnika dla określonych argumentów.

## <a name="operator-"></a><a name="operator-"></a>zakład

Oblicza różnicę składnika między określonymi argumentami.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Ranga argumentów krotki.

*_Lhs*<br/>
Argument, z którego ma zostać odjęta wartość.

*_Rhs*<br/>
Argument odejmowania.

### <a name="return-value"></a>Wartość zwracana

Różnica składnika między określonymi argumentami.

## <a name="operator"></a><a name="operator_star"></a>zakład

Oblicza produkt ze składnikami dla określonych argumentów.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator*(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator*(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp, cpu);
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Ranga argumentów krotki.

*_Lhs*<br/>
Jedna z krotek do pomnożenia.

*_Rhs*<br/>
Jedna z krotek do pomnożenia.

### <a name="return-value"></a>Wartość zwracana

Iloczyn dotyczący składnika określonych argumentów.

## <a name="operator"></a><a name="operator_div"></a>zakład

Oblicza iloraz składnika dla określonych argumentów.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator/(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator/(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Ranga argumentów krotki.

*_Lhs*<br/>
Krotka, która ma zostać podzielona.

*_Rhs*<br/>
Krotka, według której ma zostać podzielona wartość.

### <a name="return-value"></a>Wartość zwracana

Iloraz składnika dla określonych argumentów.

## <a name="operator"></a><a name="operator_mod"></a>zakład

Oblicza moduł pierwszego określonego argumentu przez drugi określony argument.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator%(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator%(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Ranga argumentów krotki.

*_Lhs*<br/>
Krotka, z której jest obliczane modulo.

*_Rhs*<br/>
Krotka do modulo przez.

### <a name="return-value"></a>Wartość zwracana

Wynik pierwszego określonego argumentu, który został określony dla drugiego określonego argumentu.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace-cpp-amp.md)
