---
title: '&lt;&gt;operatory string_view'
ms.date: 04/19/2019
f1_keywords:
- xstring/basic_string_view::operator!=
- xstring/basic_string_view::operator&gt;
- xstring/basic_string_view::operator&gt;=
- xstring/basic_string_view::operator&lt;
- xstring/basic_string_view::operator&lt;&lt;
- xstring/basic_string_view::operator&lt;=
- xstring/basic_string_view::operator+
- xstring/basic_string_view::operator==
helpviewer_keywords:
- std::basic_string_view::operator!=
- std::basic_string_view::operator&gt;
- std::basic_string_view::operator&gt;=
- std::basic_string_view::operator&lt;
- std::basic_string_view::operator&lt;&lt;
- std::basic_string_view::operator&lt;=, std::basic_string_view::operator==
ms.openlocfilehash: b0761c1af7b2ed9f34917d2e4165561b357f0a30
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833221"
---
# <a name="ltstring_viewgt-operators"></a>&lt;&gt;operatory string_view

Te operatory służą do porównywania dwóch string_view obiektów lub string_view i niektórych innych obiektów String (na przykład [std:: String](basic-string-class.md)lub **char \* **), dla których podano niejawną konwersję.

[operator! =](#op_neq)\
[zakład&gt;](#op_gt)\
[zakład&gt;=](#op_gt_eq)\
[zakład&lt;](#op_lt)\
[zakład&lt;&lt;](#op_lt_lt)\
[zakład&lt;=](#op_lt_eq)\
[operator = =](#op_eq_eq)\
[operator "" SV](#op_sv)

## <a name="operator"></a><a name="op_neq"></a> operator! =

Testuje, czy obiekt po lewej stronie operatora nie jest równy obiektowi po prawej stronie.

```cpp
template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator!=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Dowolny typ ciągu z konwersją lub obiekt typu `basic_string_view` , który ma zostać porównany.

*Kliknij*\
Dowolny typ ciągu z konwersją lub obiekt typu `basic_string_view` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekt po lewej stronie operatora nie jest lexicographically równy obiektowi po prawej stronie; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Niejawna konwersja musi istnieć w *convertible_string_type* do string_view po drugiej stronie.

Porównanie jest oparte na lexicographical parowania sekwencji znaków. Jeśli mają taką samą liczbę elementów, a wszystkie elementy są równe, te dwa obiekty są równe. W przeciwnym razie są one nierówne.

## <a name="operator"></a><a name="op_eq_eq"></a> operator = =

Testuje, czy obiekt po lewej stronie operatora jest równy obiektowi po prawej stronie.

```cpp
template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator==(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Dowolny typ ciągu z konwersją lub obiekt typu `basic_string_view` , który ma zostać porównany.

*Kliknij*\
Dowolny typ ciągu z konwersją lub obiekt typu `basic_string_view` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekt po lewej stronie operatora jest lexicographically równy obiektowi po prawej stronie; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Niejawna konwersja musi istnieć w *convertible_string_type* do string_view po drugiej stronie.

Porównanie jest oparte na lexicographical parowania sekwencji znaków. Jeśli mają taką samą liczbę elementów, a wszystkie elementy są równe, te dwa obiekty są równe.

## <a name="operatorlt"></a><a name="op_lt"></a> zakład&lt;

Testuje, czy obiekt po lewej stronie operatora jest mniejszy niż obiekt z prawej strony sidestring_view

```cpp
template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Dowolny typ ciągu z konwersją lub obiekt typu `basic_string_view` , który ma zostać porównany.

*Kliknij*\
Dowolny typ ciągu z konwersją lub obiekt typu `basic_string_view` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekt po lewej stronie operatora jest lexicographically mniejszy niż obiekt po prawej stronie; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Niejawna konwersja musi istnieć w *convertible_string_type* do string_view po drugiej stronie.

Porównanie jest oparte na lexicographical parowania sekwencji znaków. Po napotkaniu pierwszej nierównej pary znaków jest zwracany wynik tego porównania. Jeśli nie zostaną znalezione żadne nierówne znaki, ale jedna sekwencja jest krótsza, krótsza sekwencja jest mniejsza niż dłuższa. Inaczej mówiąc, "Cat" jest mniejszy niż "koty".

### <a name="example"></a>Przykład

```cpp
#include <string>
#include <string_view>

using namespace std;

int main()
{
    string_view sv1 { "ABA" };
    string_view sv2{ "ABAC" };
    string_view sv3{ "ABAD" };
    string_view sv4{ "ABACE" };

    bool result = sv2 > sv1; // true
    result = sv3 > sv2; // true
    result = sv3 != sv1; // true
    result = sv4 < sv3; // true because `C` < `D`
}
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a> zakład&lt;=

Testuje, czy obiekt po lewej stronie operatora jest mniejszy od lub równy obiektowi po prawej stronie.

```cpp
template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Dowolny typ ciągu z konwersją lub obiekt typu `basic_string_view` , który ma zostać porównany.

*Kliknij*\
Dowolny typ ciągu z konwersją lub obiekt typu `basic_string_view` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekt po lewej stronie operatora jest lexicographically mniejszy lub równy obiektowi po prawej stronie; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Zobacz [operator &lt; ](#op_lt).

## <a name="operatorltlt"></a><a name="op_lt_lt"></a> zakład&lt;&lt;

Zapisuje string_view w strumieniu wyjściowym.

```cpp
template <class CharType, class Traits>
inline basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& Ostr, const basic_string_view<CharType, Traits> Str);
```

### <a name="parameters"></a>Parametry

*Ostr*\
strumień wyjściowy, w którym jest zapisywane.

*Str*\
String_view, które mają zostać wprowadzone do strumienia wyjściowego.

### <a name="return-value"></a>Wartość zwracana

strumień wyjściowy, w którym jest zapisywane.

### <a name="remarks"></a>Uwagi

Użyj tego operatora, aby wstawić zawartość string_view do strumienia wyjściowego, na przykład używając [std:: cout](iostream.md#cout).

## <a name="operatorgt"></a><a name="op_gt"></a> zakład&gt;

Testuje, czy obiekt po lewej stronie operatora jest większy niż obiekt po prawej stronie.

```cpp
template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Dowolny typ ciągu z konwersją lub obiekt typu `basic_string_view` , który ma zostać porównany.

*Kliknij*\
Dowolny typ ciągu z konwersją lub obiekt typu `basic_string_view` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekt po lewej stronie operatora jest lexicographically większy niż obiekt string_view po prawej stronie; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Zobacz [operator &lt; ](#op_lt).

## <a name="operatorgt"></a><a name="op_gt_eq"></a> zakład&gt;=

Testuje, czy obiekt po lewej stronie operatora jest większy niż lub równy obiektowi po prawej stronie.

```cpp
template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parametry

*lewym*\
Dowolny typ ciągu z konwersją lub obiekt typu `basic_string_view` , który ma zostać porównany.

*Kliknij*\
Dowolny typ ciągu z konwersją lub obiekt typu `basic_string_view` , który ma zostać porównany.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekt po lewej stronie operatora jest lexicographically większy lub równy obiektowi po prawej stronie; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Zobacz [operator &lt; ](#op_lt).

## <a name="operator-sv-string_view-literal"></a><a name="op_sv"></a> operator "" OHR (string_view literal)

Konstruuje string_view z literału ciągu. Wymaga przestrzeni nazw `std::literals::string_view_literals` .

### <a name="example"></a>Przykład

```cpp

using namespace std;
using namespace literals::string_view_literals;

    string_view sv{ "Hello"sv };
    wstring_view wsv{ L"Hello"sv };
    u16string_view sv16{ u"Hello"sv };
    u32string_view sv32{ U"Hello"sv };
```

## <a name="see-also"></a>Zobacz też

[\<string_view>](../standard-library/string-view.md)
