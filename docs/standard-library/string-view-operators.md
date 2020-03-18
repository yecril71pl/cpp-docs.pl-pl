---
title: '&lt;string_view operatory&gt;'
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
ms.openlocfilehash: 699b1f1bddeb71ecbf03297d162a7e45ebd39609
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419421"
---
# <a name="ltstring_viewgt-operators"></a>&lt;string_view operatory&gt;

Te operatory służą do porównywania dwóch string_view obiektów lub string_view i niektórych innych obiektów String (na przykład [std:: String](basic-string-class.md)lub **char\*** ), dla których podano niejawną konwersję. 

||||
|-|-|-|
|[operator!=](#op_neq)|[&gt; operatora](#op_gt)|[&gt;operatora =](#op_gt_eq)|
|[&lt; operatora](#op_lt)|[&lt;operatora &lt;](#op_lt_lt)|[&lt;operatora =](#op_lt_eq)|
|[operator = =](#op_eq_eq)|[operator "" SV](#op_sv)|

## <a name="op_neq"></a>operator! =

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

\ *lewo*
Każdy typ ciągu z konwersją lub obiekt typu `basic_string_view` do porównania.

*prawa*\
Każdy typ ciągu z konwersją lub obiekt typu `basic_string_view` do porównania.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli obiekt po lewej stronie operatora nie jest lexicographically równy obiektowi po prawej stronie; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Niejawna konwersja musi istnieć w *convertible_string_type* do string_view po drugiej stronie. 

Porównanie jest oparte na lexicographical parowania sekwencji znaków. Jeśli mają taką samą liczbę elementów, a wszystkie elementy są równe, te dwa obiekty są równe. W przeciwnym razie są one nierówne.

## <a name="op_eq_eq"></a>operator = =

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

\ *lewo*
Każdy typ ciągu z konwersją lub obiekt typu `basic_string_view` do porównania.

*prawa*\
Każdy typ ciągu z konwersją lub obiekt typu `basic_string_view` do porównania.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli obiekt po lewej stronie operatora jest lexicographically równy obiektowi po prawej stronie; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Niejawna konwersja musi istnieć w *convertible_string_type* do string_view po drugiej stronie. 

Porównanie jest oparte na lexicographical parowania sekwencji znaków. Jeśli mają taką samą liczbę elementów, a wszystkie elementy są równe, te dwa obiekty są równe.


## <a name="op_lt"></a>&lt; operatora

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

\ *lewo*
Każdy typ ciągu z konwersją lub obiekt typu `basic_string_view` do porównania.

*prawa*\
Każdy typ ciągu z konwersją lub obiekt typu `basic_string_view` do porównania.

### <a name="return-value"></a>Wartość zwrócona

**true** , jeśli obiekt po lewej stronie operatora jest lexicographically mniejszy niż obiekt po prawej stronie; w przeciwnym razie **false**.

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

## <a name="op_lt_eq"></a>&lt;operatora =

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

\ *lewo*
Każdy typ ciągu z konwersją lub obiekt typu `basic_string_view` do porównania.

*prawa*\
Każdy typ ciągu z konwersją lub obiekt typu `basic_string_view` do porównania.

### <a name="return-value"></a>Wartość zwrócona

**true** , jeśli obiekt po lewej stronie operatora jest lexicographically mniejszy lub równy obiektowi po prawej stronie; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zobacz [&lt;operatora ](#op_lt).

## <a name="op_lt_lt"></a>&lt;operatora &lt;

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

### <a name="return-value"></a>Wartość zwrócona

strumień wyjściowy, w którym jest zapisywane.

### <a name="remarks"></a>Uwagi

Użyj tego operatora, aby wstawić zawartość string_view do strumienia wyjściowego, na przykład używając [std:: cout](iostream.md#cout).

## <a name="op_gt"></a>&gt; operatora

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

\ *lewo*
Każdy typ ciągu z konwersją lub obiekt typu `basic_string_view` do porównania.

*prawa*\
Każdy typ ciągu z konwersją lub obiekt typu `basic_string_view` do porównania.

### <a name="return-value"></a>Wartość zwrócona

**true** , jeśli obiekt po lewej stronie operatora jest lexicographically większy niż obiekt string_view po prawej stronie; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zobacz [&lt;operatora ](#op_lt).

## <a name="op_gt_eq"></a>&gt;operatora =

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

\ *lewo*
Każdy typ ciągu z konwersją lub obiekt typu `basic_string_view` do porównania.

*prawa*\
Każdy typ ciągu z konwersją lub obiekt typu `basic_string_view` do porównania.

### <a name="return-value"></a>Wartość zwrócona

**true** , jeśli obiekt po lewej stronie operatora jest lexicographically większy lub równy obiektowi po prawej stronie; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zobacz [&lt;operatora ](#op_lt).

## <a name="op_sv"></a>operator "" OHR (string_view literal)

Konstruuje string_view z literału ciągu. Wymaga `std::literals::string_view_literals`przestrzeni nazw. 

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

[\<string_view >](../standard-library/string-view.md)
