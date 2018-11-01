---
title: Operatory przestrzeni nazw współbieżności (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: cd40f771cbab5651b2f33f0ed2e84ea1412855bd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598046"
---
# <a name="concurrency-namespace-operators-amp"></a>Operatory przestrzeni nazw współbieżności (AMP)

||||
|-|-|-|
|[operator!=](#operator_neq)|[operator%](#operator_mod)|[operator *](#operator_star)|
|[operator +](#operator_add)|[operator-](#operator-)|[operator /](#operator_div)|
|[operator==](#operator_eq_eq)|

##  <a name="operator_eq_eq"></a>  operator ==

Określa, czy określone argumenty są takie same.

```
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
Ranga argumentów krotek.

*_Lhs*<br/>
Jedna z krotek do porównania.

*_Rhs*<br/>
Jedna z krotek do porównania.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli kolekcje są równe; w przeciwnym razie **false**.

##  <a name="operator_neq"></a>  operator! =

Określa, czy określone argumenty są równe.

```
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
Ranga argumentów krotek.

*_Lhs*<br/>
Jedna z krotek do porównania.

*_Rhs*<br/>
Jedna z krotek do porównania.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli kolekcje nie są równe; w przeciwnym razie **false**.

##  <a name="operator_add"></a>  operator +

Oblicza sumę dotyczącą składnika dla określonych argumentów.

```
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
Ranga argumentów krotek.

*_Lhs*<br/>
Jeden z argumentów do dodania.

*_Rhs*<br/>
Jeden z argumentów do dodania.

### <a name="return-value"></a>Wartość zwracana

Dotycząca składników Suma określonych argumentów.

##  <a name="operator-"></a>  operator-

Oblicza różnicę dotyczącą składnika między określonymi argumentami.

```
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
Ranga argumentów krotek.

*_Lhs*<br/>
Argument do odjęcia od.

*_Rhs*<br/>
Argument do odjęcia.

### <a name="return-value"></a>Wartość zwracana

Różnicę dotyczącą składnika między określonymi argumentami.

##  <a name="operator_star"></a>  operator *

Oblicza iloczyn dotyczący składnika dla określonych argumentów.

```
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
Ranga argumentów krotek.

*_Lhs*<br/>
Jedna ze spójnych kolekcji do pomnożenia.

*_Rhs*<br/>
Jedna ze spójnych kolekcji do pomnożenia.

### <a name="return-value"></a>Wartość zwracana

Iloczyn dotyczący składnika dla określonych argumentów.

##  <a name="operator_div"></a>  operator /

Oblicza iloraz dotyczący składnika dla określonych argumentów.

```
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
Ranga argumentów krotek.

*_Lhs*<br/>
Krotka można podzielić.

*_Rhs*<br/>
Spójna kolekcja znajdująca się dzielnikiem.

### <a name="return-value"></a>Wartość zwracana

Oblicza iloraz dotyczący składnika dla określonych argumentów.

##  <a name="operator_mod"></a>  operator %

Oblicza moduł pierwszego określonego argumentu przez drugi określony argument.

```
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
Ranga argumentów krotek.

*_Lhs*<br/>
Krotka, z której oblicza się modulo.

*_Rhs*<br/>
Krotka do modulo przez.

### <a name="return-value"></a>Wartość zwracana

Wynik pierwszego argumentu określonego moduł drugi określony argument.

## <a name="see-also"></a>Zobacz też

[Współbieżność Namespace ](concurrency-namespace-cpp-amp.md)
