---
title: Operatory &lt;ostream&gt;
ms.date: 11/04/2016
f1_keywords:
- ostream/std::operator&lt;&lt;
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
ms.openlocfilehash: c80abcb08423b4bb269e7d60ac43ef97d197a0e9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874835"
---
# <a name="ltostreamgt-operators"></a>Operatory &lt;ostream&gt;

||
|-|
|[&lt;operatora &lt;](#op_lt_lt)|

## <a name="op_lt_lt"></a>&lt;operatora &lt;

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

*val*\
Typ

### <a name="return-value"></a>Wartość zwracana

Strumień.

### <a name="remarks"></a>Uwagi

Klasa `basic_ostream` definiuje również kilka operatorów wstawiania. Aby uzyskać więcej informacji, zobacz [basic_ostream:: operator&lt;&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt).

Funkcja szablonu

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

Określa długość N = `traits_type::`[Długość](../standard-library/char-traits-struct.md#length)(`str`) sekwencji rozpoczynającej się o *str*i wstawia sekwencję. Jeśli N < [szerokość](../standard-library/ios-base-class.md#width)`_Ostr.`, funkcja wstawia również powtarzanie `_Ostr.width`-N znaków wypełnienia. Powtórzenie poprzedza sekwencję if (`_Ostr`. [flagi](../standard-library/ios-base-class.md#flags) & `adjustfield`! = [Left](../standard-library/ios-functions.md#left). W przeciwnym razie powtórzenia następuje po sekwencji. Funkcja zwraca *_Ostr*.

Funkcja szablonu

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

Wstawia element `_Ch`. Jeśli 1 < `_Ostr.width`, funkcja wstawia również powtarzające się znaki wypełnienia `_Ostr.width`-1. Powtórzenie poprzedza sekwencję, jeśli `_Ostr.flags & adjustfield != left`. W przeciwnym razie powtórzenia następuje po sekwencji. Zwraca *_Ostr*.

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

z tą różnicą, że każdy element *_Ch* sekwencji zaczynającej się od *str* jest konwertowany na obiekt typu `Elem`, wywołując `_Ostr.`[put](../standard-library/basic-ostream-class.md#put)(`_Ostr.`[rozszerzając](../standard-library/basic-ios-class.md#widen)(`_Ch`)).

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

z tą różnicą, że *_Ch* jest konwertowana na obiekt typu `Elem` przez wywoływanie `_Ostr.put`(`_Ostr.widen`(`_Ch`)).

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

zwraca `_Ostr` `<<` `val` (i konwertuje [odwołanie rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) na `_Ostr` do lvalue w procesie).

### <a name="example"></a>Przykład

Zobacz [opróżnianie](../standard-library/ostream-functions.md#flush) , aby zapoznać się z przykładem przy użyciu `operator<<`.

## <a name="see-also"></a>Zobacz także

[\<ostream >](../standard-library/ostream.md)
