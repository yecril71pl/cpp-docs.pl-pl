---
title: basic_regex — Klasa
ms.date: 03/27/2019
f1_keywords:
- regex/std::basic_regex
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
ms.openlocfilehash: 4348941e065680a54f9bd0c9f5b7ab2ff1af5e56
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219225"
---
# <a name="basic_regex-class"></a>basic_regex — Klasa

Owija wyrażenie regularne.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class RXtraits>
class basic_regex
```

## <a name="parameters"></a>Parametry

*Elem*\
Typ elementów, do których ma pasować.

*RXtraits*\
Klasa cech dla elementów.

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje obiekt, który przechowuje wyrażenie regularne. Obiekty tego szablonu klasy mogą być przekazane do funkcji szablonu [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search)i [regex_replace](../standard-library/regex-functions.md#regex_replace)wraz z odpowiednimi argumentami ciągu tekstowego, aby wyszukać tekst zgodny z wyrażeniem regularnym. Istnieją dwie specjalizacje tego szablonu klasy, z definicjami typu [wyrażenie regularne](../standard-library/regex-typedefs.md#regex) dla elementów typu **`char`** , i [wRegex —](../standard-library/regex-typedefs.md#wregex) dla elementów typu **`wchar_t`** .

Argument szablonu *RXtraits* opisuje różne ważne właściwości składni wyrażeń regularnych obsługiwanych przez szablon klasy. Klasa, która określa te cechy wyrażenia regularnego, musi mieć ten sam interfejs zewnętrzny co obiekt typu [Regex_traits Class](../standard-library/regex-traits-class.md).

Niektóre funkcje przyjmują sekwencję operandów, która definiuje wyrażenie regularne. Można określić taką sekwencję operandów na kilka sposobów:

`ptr`--sekwencję zakończoną znakiem null (taką jak ciąg C, dla *elem* typu **`char`** ) rozpoczynającą się od `ptr` (która nie może być pustym wskaźnikiem), gdzie element kończący jest wartością `value_type()` i nie jest częścią sekwencji operandu

`ptr`, `count` --sekwencja `count` elementów rozpoczynająca się o `ptr` (nie może być pustym wskaźnikiem)

`str`--Sekwencja określona przez `basic_string` obiekt`str`

`first`, `last` --sekwencja elementów rozdzielanych przez Iteratory `first` i `last` , z zakresu`[first, last)`

`right`-- `basic_regex` obiekt`right`

Te funkcje składowe również przyjmują argument `flags` , który określa różne opcje interpretacji wyrażenia regularnego, a także te opisane przez typ *RXtraits* .

### <a name="members"></a>Elementy członkowskie

|Członek|Wartość domyślna|
|-|-|
|publiczna statyczna stała flag_type icase|regex_constants:: icase|
|publiczna statyczna stała flag_type SubSub|regex_constants:: nosub|
|publiczna statyczna stała flag_type Optymalizuj|regex_constants:: Optymalizuj|
|publiczne statyczne stałe flag_type COLLATE|regex_constants:: COLLATE|
|publiczna statyczna stała flag_type ECMAScript|regex_constants:: ECMAScript|
|publiczna statyczna stała flag_type podstawowa|regex_constants:: Basic|
|publiczna statyczna stała flag_type rozszerzona|regex_constants:: Extended|
|publiczna statyczna stała flag_type AWK|regex_constants:: AWK|
|publiczna statyczna stała flag_type grep|regex_constants:: grep|
|publiczna statyczna stała flag_type egrep|regex_constants:: egrep|
|prywatne cechy RXtraits||

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[basic_regex](#basic_regex)|Konstruowanie obiektu wyrażenia regularnego.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[flag_type](#flag_type)|Typ flag opcji składni.|
|[locale_type](#locale_type)|Typ przechowywanego obiektu ustawień regionalnych.|
|[value_type](#value_type)|Typ elementu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[przypisać](#assign)|Przypisuje wartość do obiektu wyrażenia regularnego.|
|[flagi](#flags)|Zwraca flagi opcji składni.|
|[getloc](#getloc)|Zwraca przechowywany obiekt locale.|
|[imbue —](#imbue)|Zmienia przechowywany obiekt locale.|
|[mark_count](#mark_count)|Zwraca liczbę dopasowanych podwyrażeń.|
|[wymiany](#swap)|Zamienia dwa obiekty wyrażeń regularnych.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator =](#op_eq)|Przypisuje wartość do obiektu wyrażenia regularnego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<regex>

**Przestrzeń nazw:** std

## <a name="example"></a>Przykład

```cpp
// std__regex__basic_regex.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

using namespace std;

int main()
{
    regex::value_type elem = 'x';
    regex::flag_type flag = regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

    // constructors
    regex rx0;
    cout << "match(\"abc\", \"\") == " << boolalpha
        << regex_match("abc", rx0) << endl;

    regex rx1("abcd", regex::ECMAScript);
    cout << "match(\"abc\", \"abcd\") == " << boolalpha
        << regex_match("abc", rx1) << endl;

    regex rx2("abcd", 3);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx2) << endl;

    regex rx3(rx2);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx3) << endl;

    string str("abcd");
    regex rx4(str);
    cout << "match(string(\"abcd\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx4) << endl;

    regex rx5(str.begin(), str.end() - 1);
    cout << "match(string(\"abc\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx5) << endl;
    cout << endl;

    // assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

    // mark_count
    cout << "\"abc\" mark_count == "
        << regex("abc").mark_count() << endl;
    cout << "\"(abc)\" mark_count == "
        << regex("(abc)").mark_count() << endl;

    // locales
    regex::locale_type loc = rx0.imbue(locale());
    cout << "getloc == imbued == " << boolalpha
        << (loc == rx0.getloc()) << endl;

    // initializer_list
    regex rx6({ 'a', 'b', 'c' }, regex::ECMAScript);
    cout << "match(\"abc\") == " << boolalpha
        << regex_match("abc", rx6);
    cout << endl;
}
```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
match("abc") == true
```

## <a name="basic_regexassign"></a><a name="assign"></a>basic_regex:: Assign

Przypisuje wartość do obiektu wyrażenia regularnego.

```cpp
basic_regex& assign(
    const basic_regex& right);

basic_regex& assign(
    const Elem* ptr,
    flag_type flags = ECMAScript);

basic_regex& assign(
    const Elem* ptr,
    size_type len,
    flag_type flags = ECMAScript);

basic_regex& assign(
    initializer_list<_Elem> IList,
    flag_type flags = regex_constants::ECMAScript);

template <class STtraits, class STalloc>
basic_regex& assign(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags = ECMAScript);

template <class InIt>
basic_regex& assign(
    InIt first, InIt last,
    flag_type flags = ECMAScript);
```

### <a name="parameters"></a>Parametry

*STtraits*\
Klasa cech dla źródła ciągu.

*STalloc*\
Klasa alokatora dla źródła ciągu.

*InIt*\
Typ iteratora danych wejściowych dla źródła zakresu.

*Kliknij*\
Źródło wyrażenia regularnego do skopiowania.

*PTR*\
Wskaźnik na początek sekwencji do skopiowania.

*znaczników*\
Flagi opcji składni, które mają zostać dodane podczas kopiowania.

*>len/TD*\
Długość sekwencji do skopiowania.

*str*\
Ciąg do skopiowania.

*pierwszego*\
Początek sekwencji do skopiowania.

*ostatniego*\
Koniec sekwencji do skopiowania.

*IList*\
Initializer_list do skopiowania.

### <a name="remarks"></a>Uwagi

Wszystkie funkcje składowe zastępują wyrażenie regularne przechowywane przez **`*this`** wyrażenie regularne opisane przez sekwencję operandu, a następnie zwracają **`*this`** .

## <a name="basic_regexbasic_regex"></a><a name="basic_regex"></a>basic_regex:: basic_regex

Konstruowanie obiektu wyrażenia regularnego.

```cpp
basic_regex();

explicit basic_regex(
    const Elem* ptr,
    flag_type flags);

explicit basic_regex(
    const Elem* ptr,
    size_type len,
    flag_type flags);

basic_regex(
    const basic_regex& right);

basic_regex(
    initializer_list<Type> IList,
    flag_type flags);

template <class STtraits, class STalloc>
explicit basic_regex(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags);

template <class InIt>
explicit basic_regex(
    InIt first,
    InIt last,
    flag_type flags);
```

### <a name="parameters"></a>Parametry

*STtraits*\
Klasa cech dla źródła ciągu.

*STalloc*\
Klasa alokatora dla źródła ciągu.

*InIt*\
Typ iteratora danych wejściowych dla źródła zakresu.

*Kliknij*\
Źródło wyrażenia regularnego do skopiowania.

*PTR*\
Wskaźnik na początek sekwencji do skopiowania.

*znaczników*\
Flagi opcji składni, które mają zostać dodane podczas kopiowania.

*>len/TD*\
Długość sekwencji do skopiowania.

*str*\
Ciąg do skopiowania.

*pierwszego*\
Początek sekwencji do skopiowania.

*ostatniego*\
Koniec sekwencji do skopiowania.

*IList*\
Initializer_list do skopiowania.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują domyślnie skonstruowany obiekt typu `RXtraits` .

Pierwszy Konstruktor konstruuje pusty `basic_regex` obiekt. Inne konstruktory konstruują `basic_regex` obiekt, który przechowuje wyrażenie regularne opisane przez sekwencję operandu.

Pusty `basic_regex` obiekt nie pasuje do żadnej sekwencji znaków podczas przekazywania do [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search)lub [regex_replace](../standard-library/regex-functions.md#regex_replace).

## <a name="basic_regexflag_type"></a><a name="flag_type"></a>basic_regex:: flag_type

Typ flag opcji składni.

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla [regex_constants:: syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

## <a name="basic_regexflags"></a><a name="flags"></a>basic_regex:: flags

Zwraca flagi opcji składni.

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca wartość `flag_type` argumentu przekazywanego do ostatniego wywołania do jednej z [basic_regex:: Assign](#assign) funkcje Członkowskie lub, jeśli takie wywołanie nie zostało wykonane, wartość przekazano do konstruktora.

## <a name="basic_regexgetloc"></a><a name="getloc"></a>basic_regex:: getloc

Zwraca przechowywany obiekt locale.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `traits.` [regex_traits:: getloc](../standard-library/regex-traits-class.md#getloc) `()` .

## <a name="basic_regeximbue"></a><a name="imbue"></a>basic_regex:: imbue —

Zmienia przechowywany obiekt locale.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Parametry

*Loc*\
Obiekt ustawień regionalnych do przechowywania.

### <a name="remarks"></a>Uwagi

Funkcja członkowska opróżnia **`*this`** i zwraca `traits.` [regex_traits:: imbue —](../standard-library/regex-traits-class.md#imbue) `(loc)` .

## <a name="basic_regexlocale_type"></a><a name="locale_type"></a>basic_regex:: locale_type

Typ przechowywanego obiektu ustawień regionalnych.

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla [regex_traits:: locale_type](../standard-library/regex-traits-class.md#locale_type).

## <a name="basic_regexmark_count"></a><a name="mark_count"></a>basic_regex:: mark_count

Zwraca liczbę dopasowanych podwyrażeń.

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę grup przechwytywania w wyrażeniu regularnym.

## <a name="basic_regexoperator"></a><a name="op_eq"></a>basic_regex:: operator =

Przypisuje wartość do obiektu wyrażenia regularnego.

```cpp
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```

### <a name="parameters"></a>Parametry

*STtraits*\
Klasa cech dla źródła ciągu.

*STalloc*\
Klasa alokatora dla źródła ciągu.

*Kliknij*\
Źródło wyrażenia regularnego do skopiowania.

*str*\
Ciąg do skopiowania.

### <a name="remarks"></a>Uwagi

Operatorzy każdy zastępują wyrażenie regularne przechowywane przy **`*this`** użyciu wyrażenia regularnego opisanego przez sekwencję operandu, a następnie zwracają **`*this`** .

## <a name="basic_regexswap"></a><a name="swap"></a>basic_regex:: swap

Zamienia dwa obiekty wyrażeń regularnych.

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt wyrażenia regularnego do zamiany.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia wyrażenia regularne między **`*this`** i *po prawej*. Robi to w stałym czasie i nie zgłasza wyjątków.

## <a name="basic_regexvalue_type"></a><a name="value_type"></a>basic_regex:: value_type

Typ elementu.

```cpp
typedef Elem value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu *elem*.

## <a name="see-also"></a>Zobacz także

[\<regex>](../standard-library/regex.md)\
[regex_match](../standard-library/regex-functions.md#regex_match)\
[regex_search](../standard-library/regex-functions.md#regex_search)\
[regex_replace](../standard-library/regex-functions.md#regex_replace)\
[wyrażeń](../standard-library/regex-typedefs.md#regex)\
[wRegex —](../standard-library/regex-typedefs.md#wregex)\
[Klasa regex_traits](../standard-library/regex-traits-class.md)
