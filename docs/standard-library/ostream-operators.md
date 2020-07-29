---
title: '&lt;&gt;Operatory ostream'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::operator&lt;&lt;
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
ms.openlocfilehash: 3851003500d37a11a88736cf611b69a2d6b1813c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228157"
---
# <a name="ltostreamgt-operators"></a>&lt;&gt;Operatory ostream

||
|-|
|[operator&lt;&lt;](#op_lt_lt)|

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>zakład&lt;&lt;

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
Obiekt `basic_ostream`.

*str*\
Ciąg znaków.

*_Tr*\
Cechy znaków.

*użyte*\
Typ

### <a name="return-value"></a>Wartość zwracana

Strumień.

### <a name="remarks"></a>Uwagi

`basic_ostream`Klasa definiuje również kilka operatorów wstawiania. Aby uzyskać więcej informacji, zobacz [basic_ostream:: &lt; &lt; operator](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt).

Funkcja szablonu

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

Określa długość N = `traits_type::` [Długość](../standard-library/char-traits-struct.md#length)( `str` ) sekwencji rozpoczynającej się o *str*i wstawia sekwencję. Jeśli N < `_Ostr.` [Szerokość](../standard-library/ios-base-class.md#width), funkcja wstawia również powtarzające się `_Ostr.width` znaki wypełnienia (-N). Powtórzenie poprzedza sekwencję if ( `_Ostr` . [flags](../standard-library/ios-base-class.md#flags)  &  flagi `adjustfield` ! = [Left](../standard-library/ios-functions.md#left). W przeciwnym razie powtórzenia następuje po sekwencji. Funkcja zwraca *_Ostr*.

Funkcja szablonu

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

Wstawia element `_Ch` . Jeśli 1 < `_Ostr.width` , funkcja wstawia również powtarzające się `_Ostr.width` znaki wypełniania-1. Powtórzenie poprzedza sekwencję `_Ostr.flags & adjustfield != left` . W przeciwnym razie powtórzenia następuje po sekwencji. Zwraca *_Ostr*.

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

z tą różnicą, że każdy element *_Ch* sekwencji zaczynającej się od *str* jest konwertowany na obiekt typu `Elem` przez wywołanie metody `_Ostr.` [Put](../standard-library/basic-ostream-class.md#put)( `_Ostr.` [rozszerzone](../standard-library/basic-ios-class.md#widen)( `_Ch` )).

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

z tą różnicą, że *_Ch* jest konwertowany na obiekt typu `Elem` przez wywoływanie `_Ostr.put( _Ostr.widen( _Ch ))` .

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

Zwraca wartość `_Ostr << (const char *)str` .

Funkcja szablonu

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```

Zwraca wartość `_Ostr << (char)_Ch` .

Funkcja szablonu:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```

Zwraca wartość `_Ostr << (const char *)str` .

Funkcja szablonu:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```

Zwraca wartość `_Ostr << (char)_Ch` .

Funkcja szablonu:

```cpp
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```

zwraca `_Ostr << val` (i konwertuje [odwołanie rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) do `_Ostr` lvalue w procesie).

### <a name="example"></a>Przykład

Zobacz [opróżnianie](../standard-library/ostream-functions.md#flush) , aby zapoznać się z przykładem `operator<<` .

## <a name="see-also"></a>Zobacz także

[\<ostream>](../standard-library/ostream.md)
