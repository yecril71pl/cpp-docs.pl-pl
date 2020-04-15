---
title: Operatory przestrzeni nazw współbieżności (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: c4086029b71d71091a12b9b6023cc6098faf2f85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376291"
---
# <a name="concurrency-namespace-operators-amp"></a>Operatory przestrzeni nazw współbieżności (AMP)

||||
|-|-|-|
|[operator!=](#operator_neq)|[% operator](#operator_mod)|[operator*](#operator_star)|
|[operator+](#operator_add)|[operator-](#operator-)|[operator/](#operator_div)|
|[operator==](#operator_eq_eq)|

## <a name="operator"></a><a name="operator_eq_eq"></a>operator==

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

**true,** jeśli krotki są równe; w przeciwnym razie **false**.

## <a name="operator"></a><a name="operator_neq"></a>operator!=

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

**true,** jeśli krotki nie są równe; w przeciwnym razie **false**.

## <a name="operator"></a><a name="operator_add"></a>operator+

Oblicza sumę składników określonych argumentów.

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
Jeden z argumentów, aby dodać.

*_Rhs*<br/>
Jeden z argumentów, aby dodać.

### <a name="return-value"></a>Wartość zwracana

Suma składników określonych argumentów.

## <a name="operator-"></a><a name="operator-"></a>operator-

Oblicza różnicę składników między określonymi argumentami.

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
Argument, od który należy odjąć.

*_Rhs*<br/>
Argument do odjęcie.

### <a name="return-value"></a>Wartość zwracana

Różnica między określonymi argumentami.

## <a name="operator"></a><a name="operator_star"></a>operator*

Oblicza produkt składników określonych argumentów.

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

Produkt składników określonych argumentów.

## <a name="operator"></a><a name="operator_div"></a>operator/

Oblicza iloraz określony argumentów.

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
Krotka do podziału.

*_Rhs*<br/>
Krotka do podziału.

### <a name="return-value"></a>Wartość zwracana

Iloraz określonych argumentów.

## <a name="operator"></a><a name="operator_mod"></a>% operator

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
Krotka, z której obliczany jest modulo.

*_Rhs*<br/>
Krotka do modulo przez.

### <a name="return-value"></a>Wartość zwracana

Wynik pierwszego określonego argumentu modułuje drugi określony argument.

## <a name="see-also"></a>Zobacz też

[Obszar nazw współbieżności](concurrency-namespace-cpp-amp.md)
