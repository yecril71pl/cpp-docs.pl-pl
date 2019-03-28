---
title: basic_regex — Klasa
ms.date: 03/27/2019
f1_keywords:
- regex/std::basic_regex
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
ms.openlocfilehash: e3a38dc186a52c8431442d58bb10e56837396b07
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565454"
---
# <a name="basicregex-class"></a>basic_regex — Klasa

Owija wyrażenie regularne.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class RXtraits>
class basic_regex
```

## <a name="parameters"></a>Parametry

*Elem*<br/>
Typ elementów, do których ma pasować.

*RXtraits*<br/>
Klasa cech dla elementów.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt, który zawiera wyrażenie regularne. Obiekty tej klasy szablonu mogą być przekazywane do funkcji szablonu [regex_match —](../standard-library/regex-functions.md#regex_match), [regex_search —](../standard-library/regex-functions.md#regex_search), i [regex_replace —](../standard-library/regex-functions.md#regex_replace), wraz z odpowiednimi argumentami ciągu tekstu, Aby wyszukać tekst, który odpowiada wyrażeniu regularnemu. Istnieją dwie specjalizacje tej klasy szablonu, z definicjami typu [wyrażenia regularnego](../standard-library/regex-typedefs.md#regex) dla elementów typu **char**, i [wregex](../standard-library/regex-typedefs.md#wregex) dla elementów typu  **wchar_t**.

Argument szablonu *RXtraits* opisuje różne ważne właściwości składni wyrażeń regularnych, które obsługuje klasa szablonu. Klasa, która określa te cechy wyrażeń regularnych musi mieć ten sam interfejs zewnętrzny co obiekt klasy szablonu [regex_traits, klasa](../standard-library/regex-traits-class.md).

Niektóre funkcje przyjmują sekwencję operandów, która definiuje wyrażenie regularne. Można określić taką sekwencję operandów na kilka sposobów:

`ptr` --sekwencję zakończony znakiem null (taka jak ciąg C dla *Elem* typu **char**) począwszy od `ptr` (może nie być wskaźnikiem typu null), gdzie element kończący jest wartością `value_type()` i nie jest częścią sekwencji operandu

`ptr`, `count` — Sekwencja `count` elementów, poczynając od `ptr` (może nie być wskaźnikiem typu null)

`str` — Sekwencja określona przez `basic_string` obiektu `str`

`first`, `last` — sekwencja elementów rozdzielonych iteratorami `first` i `last`, w zakresie `[first, last)`

`right` -- `basic_regex` obiektu `right`

Te funkcje elementów członkowskich również przyjmują argument `flags` , który określa różne opcje dla interpretacji wyrażenia regularnego w uzupełnieniu do opisanych przez *RXtraits* typu.

### <a name="members"></a>Elementy członkowskie

|Element członkowski|Wartość domyślna|
|-|-|
|publiczne statyczne icase flag_type const|regex_constants::icase|
|publiczne statyczne nosubs flag_type const|regex_constants::nosubs|
|Optymalizowanie publiczne statyczne flag_type const|regex_constants::Optimize|
|collate publiczne statyczne flag_type const|regex_constants::collate|
|publiczne statyczne flag_type const ECMAScript|regex_constants::ECMAScript|
|publiczne statyczne const flag_type podstawowe|regex_constants::basic|
|publiczne statyczne flag_type const rozszerzone|regex_constants::extended|
|publiczne statyczne awk flag_type const|regex_constants::awk|
|publiczne statyczne grep flag_type const|regex_constants::grep|
|publiczne statyczne egrep flag_type const|regex_constants::egrep|
|prywatne cech RXtraits||

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_regex](#basic_regex)|Skonstruuj obiekt będący wyrażeniem regularnym.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[flag_type](#flag_type)|Typ składni flagi opcji.|
|[locale_type](#locale_type)|Typ obiektu przechowywanych ustawień regionalnych.|
|[value_type](#value_type)|Typ elementu.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Przypisz](#assign)|Przypisuje wartość do obiektu będącego wyrażeniem regularnym.|
|[flagi](#flags)|Zwraca składni flagi opcji.|
|[getloc](#getloc)|Zwraca obiekt ustawień regionalnych przechowywanych.|
|[imbue](#imbue)|Zmienia obiektu przechowywanych ustawień regionalnych.|
|[mark_count —](#mark_count)|Zwraca liczbę dopasowane podwyrażenia.|
|[swap](#swap)|Zamienia dwa obiekty wyrażeń regularnych.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje wartość do obiektu będącego wyrażeniem regularnym.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wyrażenia regularnego >

**Namespace:** standardowe

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

## <a name="assign"></a>  basic_regex::ASSIGN

Przypisuje wartość do obiektu będącego wyrażeniem regularnym.

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

*STtraits*<br/>
Klasa cech dla źródła ciągu.

*STalloc*<br/>
Klasa alokatora źródła ciągu.

*InIt*<br/>
Typ iteratora danych wejściowych dla źródła zakresu.

*right*<br/>
Wyrażenie regularne źródła do skopiowania.

*ptr*<br/>
Wskaźnik do początku sekwencji do skopiowania.

*flagi*<br/>
Flagi opcji składni można dodać podczas kopiowania.

*len/TD>*<br/>
Długość sekwencji do skopiowania.

*str*<br/>
Ciąg do skopiowania.

*pierwszy*<br/>
Początek sekwencji do skopiowania.

*last*<br/>
Koniec sekwencji do skopiowania.

*IList*<br/>
Lista initializer_list do skopiowania.

### <a name="remarks"></a>Uwagi

Funkcje elementów członkowskich Zastąp wyrażenie regularne w posiadaniu `*this` z wyrażeniem regularnym opisanego przez sekwencję operandów, zwracany jest `*this`.

## <a name="basic_regex"></a>  basic_regex::basic_regex

Skonstruuj obiekt będący wyrażeniem regularnym.

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

*STtraits*<br/>
Klasa cech dla źródła ciągu.

*STalloc*<br/>
Klasa alokatora źródła ciągu.

*InIt*<br/>
Typ iteratora danych wejściowych dla źródła zakresu.

*right*<br/>
Wyrażenie regularne źródła do skopiowania.

*ptr*<br/>
Wskaźnik do początku sekwencji do skopiowania.

*flagi*<br/>
Flagi opcji składni można dodać podczas kopiowania.

*len/TD>*<br/>
Długość sekwencji do skopiowania.

*str*<br/>
Ciąg do skopiowania.

*pierwszy*<br/>
Początek sekwencji do skopiowania.

*last*<br/>
Koniec sekwencji do skopiowania.

*IList*<br/>
Lista initializer_list do skopiowania.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory zapisują obiekt zbudowanego domyślnie typu `RXtraits`.

Pierwszy Konstruktor konstruuje pustą `basic_regex` obiektu. Inne konstruktory konstruowania `basic_regex` obiekt, który zawiera wyrażenie regularne opisanego przez sekwencję operandów.

Pusta `basic_regex` obiekt nie jest zgodny z dowolnej sekwencji znaków, gdy przekazywane do [regex_match —](../standard-library/regex-functions.md#regex_match), [regex_search —](../standard-library/regex-functions.md#regex_search), lub [regex_replace —](../standard-library/regex-functions.md#regex_replace).

## <a name="flag_type"></a>  basic_regex::flag_type

Typ składni flagi opcji.

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

## <a name="flags"></a>  basic_regex::Flags

Zwraca składni flagi opcji.

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca wartość `flag_type` argument przekazany do jednej z najbardziej aktualną wywołania [basic_regex::assign](#assign) funkcji składowych lub, jeśli brak takiego wywołania zostały wprowadzone, wartość przekazywana do konstruktora.

## <a name="getloc"></a>  basic_regex::getloc

Zwraca obiekt ustawień regionalnych przechowywanych.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `traits.` [regex_traits::getloc](../standard-library/regex-traits-class.md#getloc)`()`.

## <a name="imbue"></a>  basic_regex::imbue

Zmienia obiektu przechowywanych ustawień regionalnych.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Parametry

*Lokalizacja*<br/>
Obiekt ustawień regionalnych, który ma być przechowywany.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego opróżnia `*this` i zwraca `traits.` [regex_traits::imbue](../standard-library/regex-traits-class.md#imbue)`(loc)`.

## <a name="locale_type"></a>  basic_regex::locale_type

Typ obiektu przechowywanych ustawień regionalnych.

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla [regex_traits::locale_type](../standard-library/regex-traits-class.md#locale_type).

## <a name="mark_count"></a>  basic_regex::mark_count

Zwraca liczbę dopasowane podwyrażenia.

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>Uwagi

Element członkowski funkcji zwraca liczbę grup przechwytywania w wyrażeniu regularnym.

## <a name="op_eq"></a>  basic_regex::operator =

Przypisuje wartość do obiektu będącego wyrażeniem regularnym.

```cpp
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```

### <a name="parameters"></a>Parametry

*STtraits*<br/>
Klasa cech dla źródła ciągu.

*STalloc*<br/>
Klasa alokatora źródła ciągu.

*right*<br/>
Wyrażenie regularne źródła do skopiowania.

*str*<br/>
Ciąg do skopiowania.

### <a name="remarks"></a>Uwagi

Operatory każdego Zastąp wyrażenie regularne w posiadaniu `*this` z wyrażeniem regularnym opisanego przez sekwencję operandów, zwracany jest `*this`.

## <a name="swap"></a>  basic_regex::swap

Zamienia dwa obiekty wyrażeń regularnych.

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>Parametry

*right*<br/>
Obiekt wyrażenia regularnego do wymiany.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia wyrażeń regularnych między `*this` i *prawo*. Ją w stałym czasie i zgłasza żadnych wyjątków.

## <a name="value_type"></a>  basic_regex::value_type

Typ elementu.

```cpp
typedef Elem value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu *Elem*.

## <a name="see-also"></a>Zobacz także

[\<regex>](../standard-library/regex.md)<br/>
[regex_match](../standard-library/regex-functions.md#regex_match)<br/>
[regex_search](../standard-library/regex-functions.md#regex_search)<br/>
[regex_replace](../standard-library/regex-functions.md#regex_replace)<br/>
[regex](../standard-library/regex-typedefs.md#regex)<br/>
[wregex](../standard-library/regex-typedefs.md#wregex)<br/>
[regex_traits, klasa](../standard-library/regex-traits-class.md)<br/>
