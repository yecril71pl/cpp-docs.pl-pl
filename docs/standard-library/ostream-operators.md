---
title: '&lt;Operatory&gt; ostream'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::operator&lt;&lt;
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
ms.openlocfilehash: c80abcb08423b4bb269e7d60ac43ef97d197a0e9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453519"
---
# <a name="ltostreamgt-operators"></a>&lt;Operatory&gt; ostream

||
|-|
|[zakład&lt;&lt;](#op_lt_lt)|

## <a name="op_lt_lt"></a>zakład&lt;&lt;

Zapisuje różne typy w strumieniu.

```cpp
template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const Elem* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    Elem _Ch);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const char* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);

template <class _Elem, class _Tr, class T>
basic_ostream <_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>&& _Ostr,
    Ty val);
```

### <a name="parameters"></a>Parametry

*_Ch*\
Znak.

*_Elem*\
Typ elementu.

*_Ostr*\
Element `basic_ostream` obiektu.

*str*\
Ciąg znaków.

*_Tr*\
Cechy znaków.

*użyte*\
Typ

### <a name="return-value"></a>Wartość zwracana

Strumień.

### <a name="remarks"></a>Uwagi

`basic_ostream` Klasa definiuje również kilka operatorów wstawiania. Aby uzyskać więcej informacji, zobacz [basic_ostream::&lt;operator&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt).

Funkcja szablonu

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

Określa długość `traits_type::`N = [Długość](../standard-library/char-traits-struct.md#length)(`str`) sekwencji rozpoczynającej się o *str*i wstawia sekwencję. Jeśli N < `_Ostr.` [Szerokość](../standard-library/ios-base-class.md#width), funkcja wstawia również powtarzające `_Ostr.width` się znaki wypełnienia (-N). Powtórzenie poprzedza sekwencję if (`_Ostr`. [](../standard-library/ios-base-class.md#flags)flagi & != [Left](../standard-library/ios-functions.md#left).`adjustfield` W przeciwnym razie powtórzenia następuje po sekwencji. Funkcja zwraca *_Ostr*.

Funkcja szablonu

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

Wstawia element `_Ch`. Jeśli 1 < `_Ostr.width`, funkcja wstawia również powtarzające `_Ostr.width` się znaki wypełniania-1. Powtórzenie poprzedza sekwencję `_Ostr.flags & adjustfield != left`. W przeciwnym razie powtórzenia następuje po sekwencji. Zwraca *_Ostr*.

Funkcja szablonu

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const char *str);
```

zachowuje się tak samo jak

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

z tą różnicą, że każdy element *_Ch* sekwencji zaczynającej się od *str* jest konwertowany na `Elem` obiekt typu `_Ostr.`przez wywołanie`_Ostr.`metody [Put](../standard-library/basic-ostream-class.md#put)([rozszerzając](../standard-library/basic-ios-class.md#widen)(`_Ch`)).

Funkcja szablonu

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    char _Ch);
```

zachowuje się tak samo jak

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

z tą różnicą, że *_Ch* jest konwertowany na `Elem` obiekt typu `_Ostr.put`przez `_Ostr.widen`wywoływanie (( `_Ch`)).

Funkcja szablonu

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char *str);
```

zachowuje się tak samo jak

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

(Nie trzeba poszerzać elementów przed wstawianiem ich).

Funkcja szablonu

```cpp
template <class _Tr>
basic_ostream<char, Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    char _Ch);
```

zachowuje się tak samo jak

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

(Nie musi on poszerzać *_Ch* przed wstawieniem).

Funkcja szablonu

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char *str);
```

zwraca `_Ostr` < < (`const char *`) `str`.

Funkcja szablonu

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```

zwraca `_Ostr` < < (`char`) `_Ch`.

Funkcja szablonu:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```

zwraca `_Ostr` < < (`const char *`) `str`.

Funkcja szablonu:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```

zwraca `_Ostr` < < (`char`) `_Ch`.

Funkcja szablonu:

```cpp
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```

zwraca `_Ostr` `_Ostr` [](../cpp/rvalue-reference-declarator-amp-amp.md) (i konwertuje odwołanie rvalue do lvalue w procesie). `<<` `val`

### <a name="example"></a>Przykład

Zobacz [opróżnianie](../standard-library/ostream-functions.md#flush) , aby zapoznać `operator<<`się z przykładem.

## <a name="see-also"></a>Zobacz także

[\<ostream>](../standard-library/ostream.md)
