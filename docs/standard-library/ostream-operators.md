---
title: '&lt;ostream&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ostream/std::operator&lt;&lt;
dev_langs:
- C++
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4819f5b5d5d6a16720bce29dd176fd0eb873014a
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955936"
---
# <a name="ltostreamgt-operators"></a>&lt;ostream&gt; operatorów

||
|-|
|[Operator&lt;&lt;](#op_lt_lt)|

## <a name="op_lt_lt"></a>  Operator&lt;&lt;

Zapisuje różnych typów w strumieniu.

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

*_Ch* znak.

*_Elem* typ elementu.

*_Ostr* A `basic_ostream` obiektu.

*str* ciąg znaków.

*_Tr* znak cech.

*Val* typu

### <a name="return-value"></a>Wartość zwracana

Strumień.

### <a name="remarks"></a>Uwagi

`basic_ostream` Klasa definiuje również wiele operatorów wstawiania. Aby uzyskać więcej informacji, zobacz [basic_ostream::operator&lt;&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt).

Funkcja szablonu

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

Określa długość N = `traits_type::` [długość](../standard-library/char-traits-struct.md#length)(`str`) na początku sekwencji *str*i wstawia sekwencję. Jeśli N < `_Ostr.` [szerokość](../standard-library/ios-base-class.md#width), wówczas funkcja również wstawia powtórzenia `_Ostr.width` -N znaki. Powtarzanie poprzedza sekwencji, jeśli (`_Ostr`. [flagi](../standard-library/ios-base-class.md#flags)  &  `adjustfield` ! = [po lewej stronie](../standard-library/ios-functions.md#left). W przeciwnym razie powtarzania następuje sekwencji. Funkcja zwraca *_Ostr*.

Funkcja szablonu

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

Wstawia element `_Ch`. Jeśli 1 < `_Ostr.width`, wówczas funkcja również wstawia powtórzenia `_Ostr.width` - 1 wprowadź znaki. Powtarzanie poprzedza sekwencji, jeśli `_Ostr.flags & adjustfield != left`. W przeciwnym razie powtarzania następuje sekwencji. Zwraca *_Ostr*.

Funkcja szablonu

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const char *str);
```

działa tak samo jak

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

z tą różnicą, że każdy element *_Ch* na początku sekwencji *str* jest konwertowany na obiekt typu `Elem` przez wywołanie metody `_Ostr.` [umieścić](../standard-library/basic-ostream-class.md#put)(`_Ostr.` [mogą zostać poszerzone](../standard-library/basic-ios-class.md#widen)(`_Ch`)).

Funkcja szablonu

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    char _Ch);
```

działa tak samo jak

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

z tą różnicą, że *_Ch* jest konwertowany na obiekt typu `Elem` przez wywołanie metody `_Ostr.put`( `_Ostr.widen`( `_Ch`)).

Funkcja szablonu

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char *str);
```

działa tak samo jak

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

(Go nie ma rozszerzenie elementy przed wstawieniem ich).

Funkcja szablonu

```cpp
template <class _Tr>
basic_ostream<char, Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    char _Ch);
```

działa tak samo jak

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

(Nie ma rozszerzenie *_Ch* przed wstawieniem.)

Funkcja szablonu

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char *str);
```

Zwraca `_Ostr` << (`const char *`) `str`.

Funkcja szablonu

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```

Zwraca `_Ostr` << (`char`) `_Ch`.

Funkcja szablonu:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```

Zwraca `_Ostr` << (`const char *`) `str`.

Funkcja szablonu:

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```

Zwraca `_Ostr` << (`char`) `_Ch`.

Funkcja szablonu:

```cpp
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```

Zwraca `_Ostr` `<<` `val` (i konwertuje [odwołanie RValue](../cpp/rvalue-reference-declarator-amp-amp.md) do `_Ostr` z wartościowaniem lewostronnym w procesie).

### <a name="example"></a>Przykład

Zobacz [opróżniania](../standard-library/ostream-functions.md#flush) dla przykłady dotyczące używania `operator<<`.

## <a name="see-also"></a>Zobacz także

[\<ostream>](../standard-library/ostream.md)<br/>
