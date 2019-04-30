---
title: '&lt;string_view&gt; operatorów'
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
ms.openlocfilehash: 1fbb7faf7d6fc92a053c0f4d47575c5c53c7968e
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346630"
---
# <a name="ltstringviewgt-operators"></a>&lt;string_view&gt; operatorów

Użyj tych operatorów do porównywania dwóch obiektów string_view, lub string_view i innego obiektu stringu (na przykład [std::string](basic-string-class.md), lub **char\***) dla niejawnej konwersji znajdujący się. 

||||
|-|-|-|
|[operator!=](#op_neq)|[Operator&gt;](#op_gt)|[Operator&gt;=](#op_gt_eq)|
|[Operator&lt;](#op_lt)|[Operator&lt;&lt;](#op_lt_lt)|[Operator&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|[operator""sv](#op_sv)|

## <a name="op_neq"></a> operator! =

Sprawdza, czy obiekt po lewej stronie operatora nie jest równy obiektowi po prawej stronie.

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

*left*<br/>
Dowolny typ konwertowany ciąg lub obiekt typu `basic_string_view` mają być porównane.

*right*<br/>
Dowolny typ konwertowany ciąg lub obiekt typu `basic_string_view` mają być porównane.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekt po lewej stronie operatora nie jest leksykograficznie równy obiektowi po prawej stronie, a w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Musi istnieć niejawna konwersja *convertible_string_type* do string_view po drugiej stronie. 

Porównanie opiera się na parowania porównanie lexicographical sekwencji znaków. Jeśli mają taką samą liczbę elementów, a elementy są równe, dwa obiekty są równe. W przeciwnym razie są nierówne.

## <a name="op_eq_eq"></a> operator ==

Sprawdza, czy obiekt po lewej stronie operatora jest równy obiektowi po prawej stronie.

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

*left*<br/>
Dowolny typ konwertowany ciąg lub obiekt typu `basic_string_view` mają być porównane.

*right*<br/>
Dowolny typ konwertowany ciąg lub obiekt typu `basic_string_view` mają być porównane.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekt po lewej stronie operatora jest leksykograficznie równy obiektowi po prawej stronie, a w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Musi istnieć niejawna konwersja *convertible_string_type* do string_view po drugiej stronie. 

Porównanie opiera się na parowania porównanie lexicographical sekwencji znaków. Jeśli mają taką samą liczbę elementów, a elementy są równe, dwa obiekty są równe.


## <a name="op_lt"></a> Operator&lt;

Sprawdza, czy obiekt po lewej stronie operatora jest mniejszy niż obiekt w prawo sidestring_view
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

*left*<br/>
Dowolny typ konwertowany ciąg lub obiekt typu `basic_string_view` mają być porównane.

*right*<br/>
Dowolny typ konwertowany ciąg lub obiekt typu `basic_string_view` mają być porównane.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiektu po lewej stronie operatora jest leksykograficznie krótszy niż obiekt po prawej stronie; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Musi istnieć niejawna konwersja *convertible_string_type* do string_view po drugiej stronie. 

Porównanie opiera się na parowania porównanie lexicographical sekwencji znaków. Po napotkaniu pierwszego nierówne pary znaków wynik tego porównania jest zwracana. Jeśli zostaną znalezione żadne znaki nie nierówne, ale jednej sekwencji jest krótszy, krótszy sekwencji jest mniejsza niż dłużej. Innymi słowy "cat" jest mniejsza niż "cats".

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

## <a name="op_lt_eq"></a> Operator&lt;=

Sprawdza, czy obiekt po lewej stronie operatora jest mniejszy niż lub równy obiektowi po prawej stronie.

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

*left*<br/>
Dowolny typ konwertowany ciąg lub obiekt typu `basic_string_view` mają być porównane.

*right*<br/>
Dowolny typ konwertowany ciąg lub obiekt typu `basic_string_view` mają być porównane.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiektu po lewej stronie operatora jest leksykograficznie krótszy niż lub równy obiektowi po prawej stronie, w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Zobacz [operator&lt;](#op_lt).

## <a name="op_lt_lt"></a> Operator&lt;&lt;

Zapisuje string_view do strumienia wyjściowego.

```cpp
template <class CharType, class Traits>
inline basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& Ostr, const basic_string_view<CharType, Traits> Str);
```

### <a name="parameters"></a>Parametry

*Ostr*<br/>
były zapisywane do strumienia wyjściowego.

*str*<br/>
String_view wprowadzonych do strumienia wyjściowego.

### <a name="return-value"></a>Wartość zwracana

były zapisywane do strumienia wyjściowego.

### <a name="remarks"></a>Uwagi

Użyj tego operatora, aby wstawić zawartość string_view do strumienia wyjściowego, np. przy użyciu [std::cout](iostream.md#cout).

## <a name="op_gt"></a> Operator&gt;

Sprawdza, czy obiekt po lewej stronie operatora jest większy niż obiekt po prawej stronie.

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

*left*<br/>
Dowolny typ konwertowany ciąg lub obiekt typu `basic_string_view` mają być porównane.

*right*<br/>
Dowolny typ konwertowany ciąg lub obiekt typu `basic_string_view` mają być porównane.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekt po lewej stronie operatora jest leksykograficznie większy niż obiekt string_view po prawej stronie, a w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Zobacz [operator&lt;](#op_lt).

## <a name="op_gt_eq"></a> Operator&gt;=

Sprawdza, czy obiekt po lewej stronie operatora jest większy lub równy obiektowi po prawej stronie.

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

*left*<br/>
Dowolny typ konwertowany ciąg lub obiekt typu `basic_string_view` mają być porównane.

*right*<br/>
Dowolny typ konwertowany ciąg lub obiekt typu `basic_string_view` mają być porównane.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekt po lewej stronie operatora jest leksykograficznie większa niż lub równy obiektowi po prawej stronie, w przeciwnym **false**.

### <a name="remarks"></a>Uwagi

Zobacz [operator&lt;](#op_lt).

## <a name="op_sv"></a> operator"" sv (string_view literału)

Tworzy string_view z literału ciągu znaków. Przestrzeń nazw wymaga `std::literals::string_view_literals`. 

### <a name="example"></a>Przykład

```cpp

using namespace std;
using namespace literals::string_view_literals;

    string_view sv{ "Hello"sv };
    wstring_view wsv{ L"Hello"sv };
    u16string_view sv16{ u"Hello"sv };
    u32string_view sv32{ U"Hello"sv };
```

## <a name="see-also"></a>Zobacz także

[\<string_view >](../standard-library/string-view.md)<br/>
