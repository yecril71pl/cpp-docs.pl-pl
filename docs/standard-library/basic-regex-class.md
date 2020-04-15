---
title: basic_regex — Klasa
ms.date: 03/27/2019
f1_keywords:
- regex/std::basic_regex
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
ms.openlocfilehash: 74a8684c619e2cfbd5417950aa6108ad93511bf7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376750"
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

*RXtraits ( RXtraits )*\
Klasa cech dla elementów.

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje obiekt, który zawiera wyrażenie regularne. Obiekty tego szablonu klasy mogą być przekazywane do funkcji [szablonu, regex_match](../standard-library/regex-functions.md#regex_match) [, regex_search](../standard-library/regex-functions.md#regex_search)i [regex_replace](../standard-library/regex-functions.md#regex_replace), wraz z odpowiednimi argumentami ciągu tekstowego, aby wyszukać tekst odpowiadający wyrażeniu regularnej. Istnieją dwie specjalizacje tego szablonu klasy, z definicjami typu [regex](../standard-library/regex-typedefs.md#regex) dla elementów typu **char**i [wregex](../standard-library/regex-typedefs.md#wregex) dla elementów typu **wchar_t**.

Argument szablonu *RXtraits* opisuje różne ważne właściwości składni wyrażeń regularnych, które obsługuje szablon klasy. Klasa określająca te cechy wyrażenia regularnego musi mieć ten sam interfejs zewnętrzny co obiekt typu [regex_traits Class](../standard-library/regex-traits-class.md).

Niektóre funkcje przyjmują sekwencję operandów, która definiuje wyrażenie regularne. Można określić taką sekwencję operandów na kilka sposobów:

`ptr`-- sekwencja zakończona z wartością null (np. ciąg C, `ptr` dla *Elem* typu **char)** zaczynając od (która `value_type()` nie może być wskaźnikiem zerowym), gdzie element kończący jest wartością i nie jest częścią sekwencji operandu

`ptr`, `count` -- sekwencja elementów zaczynających `count` się `ptr` od (która nie może być wskaźnikiem zerowym)

`str`-- sekwencja określona `basic_string` przez obiekt`str`

`first`, `last` -- sekwencja elementów rozdzielonych przez `first` `last`iteratory i , w zakresie`[first, last)`

`right`-- `basic_regex` obiekt`right`

Te funkcje członkowskie `flags` również wziąć argument, który określa różne opcje interpretacji wyrażenia regularnego oprócz tych opisanych przez *RXtraits* typu.

### <a name="members"></a>Elementy członkowskie

|Członek|Wartość domyślna|
|-|-|
|publiczne statyczne const flag_type icase|regex_constants::icase|
|publiczne statyczne const flag_type nosubs|regex_constants::nosubs|
|publiczne statyczne flag_type optymalizacji|regex_constants::optymalizacja|
|publiczne statyczne flag_type sortowanie|regex_constants::sortowanie|
|publiczny statyczny flag_type ECMAScript|regex_constants::ECMAScript|
|publiczne statyczne flag_type podstawowe|regex_constants::basic|
|publiczne statyczne flag_type konsycowe rozszerzone|regex_constants::rozszerzony|
|publiczny statyczny const flag_type awk|regex_constants::awk|
|publiczny statyczny const flag_type grep|regex_constants::grep|
|publiczny statyczny const flag_type egrep|regex_constants::egrep|
|prywatne cechy RXtraits||

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_regex](#basic_regex)|Konstruuj obiekt wyrażenia regularnego.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[flag_type](#flag_type)|Typ opcji składni flagi.|
|[locale_type](#locale_type)|Typ przechowywanego obiektu ustawień regionalnych.|
|[value_type](#value_type)|Typ elementu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Przypisać](#assign)|Przypisuje wartość do obiektu wyrażenia regularnego.|
|[flagi](#flags)|Zwraca flagi opcji składni.|
|[getlok](#getloc)|Zwraca przechowywany obiekt ustawień regionalnych.|
|[Nasycić](#imbue)|Zmienia przechowywany obiekt ustawień regionalnych.|
|[mark_count](#mark_count)|Zwraca liczbę dopasowanych podwyrażenia.|
|[Wymiany](#swap)|Zamienia dwa obiekty wyrażenia regularnego.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje wartość do obiektu wyrażenia regularnego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> regex

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

## <a name="basic_regexassign"></a><a name="assign"></a>basic_regex::przypisywanie

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

*STtraits ( STtraits )*\
Klasa cech dla źródła ciągu.

*STalloc ( STalloc )*\
Klasy alokatora dla źródła ciągu.

*Init*\
Typ iteratora wejściowego dla źródła zakresu.

*Prawo*\
Źródło Regex do skopiowania.

*Ptr*\
Wskaźnik do początku sekwencji do skopiowania.

*Flagi*\
Flaga opcji składni do dodania podczas kopiowania.

*>len/TD*\
Długość sekwencji do skopiowania.

*Str*\
Ciąg do skopiowania.

*Pierwszym*\
Początek sekwencji do skopiowania.

*Ostatnio*\
Koniec sekwencji do skopiowania.

*Ilist*\
initializer_list do skopiowania.

### <a name="remarks"></a>Uwagi

Funkcje członkowskie zastępują wyrażenie `*this` regularne, które jest utrzymywane przez wyrażenie `*this`regularne opisane przez sekwencję operandu, a następnie zwracają .

## <a name="basic_regexbasic_regex"></a><a name="basic_regex"></a>basic_regex::basic_regex

Konstruuj obiekt wyrażenia regularnego.

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

*STtraits ( STtraits )*\
Klasa cech dla źródła ciągu.

*STalloc ( STalloc )*\
Klasy alokatora dla źródła ciągu.

*Init*\
Typ iteratora wejściowego dla źródła zakresu.

*Prawo*\
Źródło Regex do skopiowania.

*Ptr*\
Wskaźnik do początku sekwencji do skopiowania.

*Flagi*\
Flaga opcji składni do dodania podczas kopiowania.

*>len/TD*\
Długość sekwencji do skopiowania.

*Str*\
Ciąg do skopiowania.

*Pierwszym*\
Początek sekwencji do skopiowania.

*Ostatnio*\
Koniec sekwencji do skopiowania.

*Ilist*\
initializer_list do skopiowania.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują obiekt `RXtraits`o typie skonstruowany domyślnie .

Pierwszy konstruktor tworzy `basic_regex` pusty obiekt. Inne konstruktory `basic_regex` konstruować obiekt, który zawiera wyrażenie regularne opisane przez sekwencję operand.

Pusty `basic_regex` obiekt nie pasuje do żadnej sekwencji znaków po przekazaniu do [regex_match](../standard-library/regex-functions.md#regex_match) [, regex_search](../standard-library/regex-functions.md#regex_search)lub [regex_replace](../standard-library/regex-functions.md#regex_replace).

## <a name="basic_regexflag_type"></a><a name="flag_type"></a>basic_regex::flag_type

Typ opcji składni flagi.

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

## <a name="basic_regexflags"></a><a name="flags"></a>basic_regex::flagi

Zwraca flagi opcji składni.

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `flag_type` wartość argumentu przekazanego do ostatniego wywołania do jednego z [funkcji basic_regex::assign](#assign) member lub, jeśli nie zostało wykonane żadne takie wywołanie, wartość przekazana konstruktorowi.

## <a name="basic_regexgetloc"></a><a name="getloc"></a>basic_regex::getloc

Zwraca przechowywany obiekt ustawień regionalnych.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu `traits.`członkowskiego zwraca [regex_traits::getloc](../standard-library/regex-traits-class.md#getloc)`()`.

## <a name="basic_regeximbue"></a><a name="imbue"></a>basic_regex::imbue

Zmienia przechowywany obiekt ustawień regionalnych.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Parametry

*Loc*\
Obiekt ustawień regionalnych do przechowywania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego `*this` opróżnia i zwraca `traits.` [regex_traits::imbue](../standard-library/regex-traits-class.md#imbue)`(loc)`.

## <a name="basic_regexlocale_type"></a><a name="locale_type"></a>basic_regex::locale_type

Typ przechowywanego obiektu ustawień regionalnych.

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem [regex_traits::locale_type](../standard-library/regex-traits-class.md#locale_type).

## <a name="basic_regexmark_count"></a><a name="mark_count"></a>basic_regex::mark_count

Zwraca liczbę dopasowanych podwyrażenia.

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca liczbę grup przechwytywania w wyrażeniu regularnym.

## <a name="basic_regexoperator"></a><a name="op_eq"></a>basic_regex::operator=

Przypisuje wartość do obiektu wyrażenia regularnego.

```cpp
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```

### <a name="parameters"></a>Parametry

*STtraits ( STtraits )*\
Klasa cech dla źródła ciągu.

*STalloc ( STalloc )*\
Klasy alokatora dla źródła ciągu.

*Prawo*\
Źródło Regex do skopiowania.

*Str*\
Ciąg do skopiowania.

### <a name="remarks"></a>Uwagi

Operatory, z których każdy `*this` zastępuje wyrażenie regularne, które jest utrzymywane `*this`przez wyrażenie regularne opisane przez sekwencję operandu, a następnie zwracają .

## <a name="basic_regexswap"></a><a name="swap"></a>basic_regex::swap

Zamienia dwa obiekty wyrażenia regularnego.

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>Parametry

*Prawo*\
Obiekt wyrażenia regularnego do wymiany.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia wyrażenia `*this` regularne między i *po prawej stronie*. Robi to w stałym czasie i nie zgłasza żadnych wyjątków.

## <a name="basic_regexvalue_type"></a><a name="value_type"></a>basic_regex::value_type

Typ elementu.

```cpp
typedef Elem value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu *Elem*.

## <a name="see-also"></a>Zobacz też

[\<>regex](../standard-library/regex.md)\
[regex_match](../standard-library/regex-functions.md#regex_match)\
[regex_search](../standard-library/regex-functions.md#regex_search)\
[regex_replace](../standard-library/regex-functions.md#regex_replace)\
[Regex](../standard-library/regex-typedefs.md#regex)\
[wregex](../standard-library/regex-typedefs.md#wregex)\
[regex_traits — Klasa](../standard-library/regex-traits-class.md)
