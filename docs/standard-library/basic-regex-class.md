---
title: basic_regex — Klasa
ms.date: 03/27/2019
f1_keywords:
- regex/std::basic_regex
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
ms.openlocfilehash: 8df9e927c430f3b94f5857bf18f575e79d6b922a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453437"
---
# <a name="basicregex-class"></a>basic_regex — Klasa

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

Klasa szablonu opisuje obiekt, który zawiera wyrażenie regularne. Obiekty tej klasy szablonu można przekazać do funkcji szablonu [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search)i [regex_replace](../standard-library/regex-functions.md#regex_replace), a także odpowiednich argumentów ciągu tekstowego, aby wyszukać tekst zgodny z wyrażeniem regularnym. Istnieją dwie specjalizacje tej klasy szablonu, z definicjami typów [wyrażenie regularne](../standard-library/regex-typedefs.md#regex) dla elementów typu **char**i [wRegex —](../standard-library/regex-typedefs.md#wregex) dla elementów typu **wchar_t**.

Argument szablonu *RXtraits* opisuje różne ważne właściwości składni wyrażeń regularnych obsługiwanych przez klasę szablonu. Klasa, która określa te cechy wyrażenia regularnego, musi mieć ten sam interfejs zewnętrzny co obiekt klasy szablonu Klasa [regex_traits](../standard-library/regex-traits-class.md).

Niektóre funkcje przyjmują sekwencję operandów, która definiuje wyrażenie regularne. Można określić taką sekwencję operandów na kilka sposobów:

`ptr`--sekwencję zakończoną znakiem null (na przykład ciąg C, dla *elem* typu **char** `ptr` ) zaczynającą się od (nie może być pustym wskaźnikiem), gdzie element kończący jest wartością `value_type()` i nie jest częścią sekwencji operandu

`ptr`, `count` -- `count` sekwencja elementów rozpoczynająca się o `ptr` (nie może być pustym wskaźnikiem)

`str`--Sekwencja określona przez `basic_string` obiekt`str`

`first`, `last` --sekwencja elementów rozdzielanych przez `first` Iteratory i `last`, z zakresu`[first, last)`

`right`-- `basic_regex` obiekt`right`

Te funkcje składowe również przyjmują `flags` argument, który określa różne opcje interpretacji wyrażenia regularnego, a także te opisane przez typ *RXtraits* .

### <a name="members"></a>Elementy członkowskie

|Element członkowski|Wartość domyślna|
|-|-|
|publiczna statyczna stała flag_type icase|regex_constants::icase|
|publiczna statyczna stała flag_type nosub|regex_constants:: SubSub|
|publiczna statyczna stała flag_type Optymalizuj|regex_constants:: Optimize|
|publiczne statyczne stałe flag_type posortowane|regex_constants:: COLLATE|
|publiczna statyczna stała flag_typea ECMAScript|regex_constants:: ECMAScript|
|publiczna statyczna stała flag_type podstawowa|regex_constants:: Basic|
|publiczna statyczna stała flag_type rozszerzona|regex_constants:: Extended|
|publiczna statyczna stała flag_type AWK|regex_constants::awk|
|public static const flag_type grep|regex_constants:: grep|
|publiczna statyczna stała flag_type egrep|regex_constants:: egrep|
|prywatne cechy RXtraits||

### <a name="constructors"></a>Konstruktorów

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
|[ponownie](#assign)|Przypisuje wartość do obiektu wyrażenia regularnego.|
|[znaczników](#flags)|Zwraca flagi opcji składni.|
|[getloc](#getloc)|Zwraca przechowywany obiekt locale.|
|[imbue](#imbue)|Zmienia przechowywany obiekt locale.|
|[mark_count](#mark_count)|Zwraca liczbę dopasowanych podwyrażeń.|
|[swap](#swap)|Zamienia dwa obiekty wyrażeń regularnych.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje wartość do obiektu wyrażenia regularnego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> wyrażeń regularnych

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

## <a name="assign"></a>basic_regex:: Assign

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

*> len/TD*\
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

Wszystkie funkcje składowe zastępują wyrażenie regularne przechowywane przez `*this` wyrażenie regularne opisane przez sekwencję operandu, a następnie zwracają `*this`.

## <a name="basic_regex"></a>basic_regex::basic_regex

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

*> len/TD*\
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

Wszystkie konstruktory przechowują domyślnie skonstruowany obiekt typu `RXtraits`.

Pierwszy Konstruktor konstruuje pusty `basic_regex` obiekt. Inne konstruktory konstruują `basic_regex` obiekt, który przechowuje wyrażenie regularne opisane przez sekwencję operandu.

Pusty `basic_regex` obiekt nie pasuje do żadnej sekwencji znaków, gdy zostanie przesłany do [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search)lub [regex_replace](../standard-library/regex-functions.md#regex_replace).

## <a name="flag_type"></a>basic_regex::flag_type

Typ flag opcji składni.

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla [regex_constants:: syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

## <a name="flags"></a>basic_regex:: flags

Zwraca flagi opcji składni.

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca wartość `flag_type` argumentu przekazywanego do ostatniego wywołania do jednej z [basic_regex:: Assign](#assign) funkcje Członkowskie lub, jeśli takie wywołanie nie zostało wykonane, wartość przekazano do konstruktora.

## <a name="getloc"></a>  basic_regex::getloc

Zwraca przechowywany obiekt locale.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `traits.` [regex_traits:: getloc](../standard-library/regex-traits-class.md#getloc)`()`.

## <a name="imbue"></a>basic_regex:: imbue —

Zmienia przechowywany obiekt locale.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Parametry

*Loc*\
Obiekt ustawień regionalnych do przechowywania.

### <a name="remarks"></a>Uwagi

`*this` Funkcja członkowska opróżnia i `traits.`zwraca [regex_traits:: imbue —](../standard-library/regex-traits-class.md#imbue)`(loc)`.

## <a name="locale_type"></a>basic_regex::locale_type

Typ przechowywanego obiektu ustawień regionalnych.

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla [regex_traits:: locale_type](../standard-library/regex-traits-class.md#locale_type).

## <a name="mark_count"></a>basic_regex::mark_count

Zwraca liczbę dopasowanych podwyrażeń.

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca liczbę grup przechwytywania w wyrażeniu regularnym.

## <a name="op_eq"></a>basic_regex:: operator =

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

Operatorzy każdy zastępują wyrażenie regularne przechowywane `*this` przy użyciu wyrażenia regularnego opisanego przez sekwencję operandu, a następnie zwracają. `*this`

## <a name="swap"></a>basic_regex:: swap

Zamienia dwa obiekty wyrażeń regularnych.

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt wyrażenia regularnego do zamiany.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia wyrażenia regularne między `*this` i *po prawej*. Robi to w stałym czasie i nie zgłasza wyjątków.

## <a name="value_type"></a>basic_regex::value_type

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
[regex](../standard-library/regex-typedefs.md#regex)\
[wRegex —](../standard-library/regex-typedefs.md#wregex)\
[regex_traits, klasa](../standard-library/regex-traits-class.md)
