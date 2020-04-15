---
title: regex_token_iterator — Klasa
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_token_iterator
- regex/std::regex_token_iterator::regex_type
- regex/std::regex_token_iterator::value_type
- regex/std::regex_token_iterator::iterator_category
- regex/std::regex_token_iterator::difference_type
- regex/std::regex_token_iterator::pointer
- regex/std::regex_token_iterator::reference
- regex/std::regex_token_iterator::operator==
- regex/std::regex_token_iterator::operator!=
- regex/std::regex_token_iterator::operator*
- regex/std::regex_token_iterator::operator->
- regex/std::regex_token_iterator::operator++
helpviewer_keywords:
- std::regex_token_iterator [C++]
- std::regex_token_iterator [C++], regex_type
- std::regex_token_iterator [C++], value_type
- std::regex_token_iterator [C++], iterator_category
- std::regex_token_iterator [C++], difference_type
- std::regex_token_iterator [C++], pointer
- std::regex_token_iterator [C++], reference
ms.assetid: a213ba48-8e4e-4b6b-871a-2637acf05f15
ms.openlocfilehash: 5ada2ad69cbcac15e09968045e54095dfb2623d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366400"
---
# <a name="regex_token_iterator-class"></a>regex_token_iterator — Klasa

Klasa iteratora dla podmeczów.

## <a name="syntax"></a>Składnia

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_token_iterator
```

## <a name="parameters"></a>Parametry

*OfertaIt*\
Typ iteratora dla podmeczów.

*Elem*\
Typ elementów, do których ma pasować.

*RXtraits ( RXtraits )*\
Klasa cech dla elementów.

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje stały obiekt iteratora do przodu. Koncepcyjnie `regex_iterator` zawiera obiekt, który używa do wyszukiwania dopasowania wyrażenia regularnego w sekwencji znaków. Wyodrębnia obiekty typu `sub_match<BidIt>` reprezentujące podmeczy identyfikowane przez wartości indeksu `subs` w przechowywanym wektorze dla każdego dopasowania wyrażenia regularnego.

Wartość indeksu -1 wyznacza sekwencję znaków rozpoczynającą się bezpośrednio po zakończeniu poprzedniego dopasowania wyrażenia regularnego lub rozpoczynającą się na początku sekwencji znaków, jeśli nie było poprzedniego dopasowania wyrażenia regularnego i rozszerzając do, ale nie obejmując pierwszego znaku bieżącego dopasowania wyrażenia regularnego lub do końca sekwencji znaków, jeśli nie ma bieżącego dopasowania. Każda inna `idx` wartość indeksu oznacza zawartość grupy `it.match[idx]`przechwytywania przechowywanej w programie .

### <a name="members"></a>Elementy członkowskie

|Członek|Wartość domyślna|
|-|-|
|`private regex_iterator<BidIt, Elem, RXtraits> it`||
|`private vector<int> subs`||
|`private int pos`||

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[regex_token_iterator](#regex_token_iterator)|Konstruuje iteratora.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[difference_type](#difference_type)|Typ różnicy iteratora.|
|[Iterator_category](#iterator_category)|Typ kategorii iteratora.|
|[pointer](#pointer)|Typ wskaźnika do dopasowania.|
|[Odwołanie](#reference)|Typ odwołania do podmeczu.|
|[regex_type](#regex_type)|Typ wyrażenia regularnego do dopasowania.|
|[value_type](#value_type)|Typ podmeczu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](#op_neq)|Porównuje iteratory dla nierówności.|
|[operator*](#op_star)|Uzyskuje dostęp do wyznaczonego podmeczu.|
|[operator++](#op_add_add)|Zwiększa iteratora.|
|[operator==](#op_eq_eq)|Porównuje iteratory dla równości.|
|[operator->](#op_arrow)|Uzyskuje dostęp do wyznaczonego podmeczu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> regex

**Przestrzeń nazw:** std

## <a name="example"></a>Przykład

```cpp
#include <regex>
#include <iostream>

typedef std::regex_token_iterator<const char *> Myiter;
int main()
    {
    const char *pat = "aaxaayaaz";
    Myiter::regex_type rx("(a)a");
    Myiter next(pat, pat + strlen(pat), rx);
    Myiter end;

// show whole match
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefix before match
    next = Myiter(pat, pat + strlen(pat), rx, -1);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show (a) submatch only
    next = Myiter(pat, pat + strlen(pat), rx, 1);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefixes and submatches
    std::vector<int> vec;
    vec.push_back(-1);
    vec.push_back(1);
    next = Myiter(pat, pat + strlen(pat), rx, vec);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefixes and whole matches
    int arr[] = {-1, 0};
    next = Myiter(pat, pat + strlen(pat), rx, arr);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// other members
    Myiter it1(pat, pat + strlen(pat), rx);
    Myiter it2(it1);
    next = it1;

    Myiter::iterator_category cat = std::forward_iterator_tag();
    Myiter::difference_type dif = -3;
    Myiter::value_type mr = *it1;
    Myiter::reference ref = mr;
    Myiter::pointer ptr = &ref;

    dif = dif; // to quiet "unused" warnings
    ptr = ptr;

    return (0);
    }
```

```Output
match == aa
match == aa
match == aa

match ==
match == x
match == y
match == z

match == a
match == a
match == a

match ==
match == a
match == x
match == a
match == y
match == a
match == z

match ==
match == aa
match == x
match == aa
match == y
match == aa
match == z
```

## <a name="regex_token_iteratordifference_type"></a><a name="difference_type"></a>regex_token_iterator::d00_typ

Typ różnicy iteratora.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `std::ptrdiff_t`.

## <a name="regex_token_iteratoriterator_category"></a><a name="iterator_category"></a>regex_token_iterator::iterator_category

Typ kategorii iteratora.

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `std::forward_iterator_tag`.

## <a name="regex_token_iteratoroperator"></a><a name="op_neq"></a>regex_token_iterator::operator!=

Porównuje iteratory dla nierówności.

```cpp
bool operator!=(const regex_token_iterator& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Iterator do porównania.

### <a name="remarks"></a>Uwagi

Funkcja elementu `!(*this == right)`członkowskiego zwraca .

## <a name="regex_token_iteratoroperator"></a><a name="op_star"></a>regex_token_iterator::operator*

Uzyskuje dostęp do wyznaczonego podmeczu.

```cpp
const sub_match<BidIt>& operator*();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego `sub_match<BidIt>` zwraca obiekt reprezentujący grupę przechwytywania identyfikowaną przez wartość `subs[pos]`indeksu .

## <a name="regex_token_iteratoroperator"></a><a name="op_add_add"></a>regex_token_iterator::operator++

Zwiększa iteratora.

```cpp
regex_token_iterator& operator++();

regex_token_iterator& operator++(int);
```

### <a name="remarks"></a>Uwagi

Jeśli przechowywany iterator `it` jest iteratorem końca sekwencji, pierwszy `pos` operator ustawia `subs.size()` wartość przechowywaną na wartość (tworząc w ten sposób iterator końca sekwencji). W przeciwnym razie operator zwiększa `pos`wartość przechowywaną; jeśli wynik jest równy `subs.size()` wartości, ustawia `pos` wartość przechowywaną na zero i `it`zwiększa przechowywany iterator . Jeśli przyrost przechowywane iterator pozostawia nierówne do iteratora końca sekwencji operator nie robi nic dalej. W przeciwnym razie, jeśli koniec poprzedniego dopasowania znajdował się na końcu sekwencji `pos` `subs.size()`znaków, operator ustawia zapisaną wartość na . W przeciwnym razie operator wielokrotnie zwiększa `pos` wartość `pos == subs.size()` `subs[pos] == -1` przechowywaną do lub (zapewniając w ten sposób, że następny wyłuskanie iteratora zwróci ogon sekwencji znaków, jeśli jedna z wartości indeksu jest -1). We wszystkich przypadkach operator zwraca obiekt.

Drugi operator tworzy kopię obiektu, zwiększa obiekt, a następnie zwraca kopię.

## <a name="regex_token_iteratoroperator"></a><a name="op_eq_eq"></a>regex_token_iterator::operator==

Porównuje iteratory dla równości.

```cpp
bool operator==(const regex_token_iterator& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Iterator do porównania.

### <a name="remarks"></a>Uwagi

Funkcja elementu `it == right.it && subs == right.subs && pos == right.pos`członkowskiego zwraca .

## <a name="regex_token_iteratoroperator-gt"></a><a name="op_arrow"></a>regex_token_iterator::operator-&gt;

Uzyskuje dostęp do wyznaczonego podmeczu.

```cpp
const sub_match<BidIt> * operator->();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `sub_match<BidIt>` wskaźnik do obiektu reprezentującego grupę `subs[pos]`przechwytywania identyfikowaną przez wartość indeksu .

## <a name="regex_token_iteratorpointer"></a><a name="pointer"></a>regex_token_iterator::pointer

Typ wskaźnika do dopasowania.

```cpp
typedef sub_match<BidIt> *pointer;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `sub_match<BidIt>*`, `BidIt` gdzie jest parametr szablonu.

## <a name="regex_token_iteratorreference"></a><a name="reference"></a>regex_token_iterator::odwołanie

Typ odwołania do podmeczu.

```cpp
typedef sub_match<BidIt>& reference;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `sub_match<BidIt>&`, `BidIt` gdzie jest parametr szablonu.

## <a name="regex_token_iteratorregex_token_iterator"></a><a name="regex_token_iterator"></a>regex_token_iterator::regex_token_iterator

Konstruuje iteratora.

```cpp
regex_token_iterator();

regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, int submatch = 0,
    regex_constants::match_flag_type f = regex_constants::match_default);

regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, const vector<int> submatches,
    regex_constants::match_flag_type f = regex_constants::match_default);

template <std::size_t N>
regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, const int (&submatches)[N],
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Początek sekwencji do dopasowania.

*Ostatnio*\
Koniec sekwencji do dopasowania.

*Ponownie*\
Wyrażenie regularne dla dopasowań.

*F*\
Flagi dla meczów.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor tworzy iterator końca sekwencji.

Drugi konstruktor tworzy obiekt, którego `it` przechowywany iterator jest inicjowany `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`do , którego przechowywany wektor `subs` zawiera dokładnie jedną całkowitą, z wartością, `submatch`i którego wartość `pos` przechowywana wynosi zero. Uwaga: wynikowy obiekt wyodrębnia podmecz identyfikowany `submatch` przez wartość indeksu dla każdego pomyślnego dopasowania wyrażenia regularnego.

Trzeci konstruktor tworzy obiekt, którego `it` przechowywany iterator jest inicjowany `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`do , którego przechowywany wektor `subs` przechowuje kopię argumentu `submatches`konstruktora i którego przechowywana wartość `pos` wynosi zero.

Czwarty konstruktor tworzy obiekt, którego `it` przechowywany iterator jest inicjowany `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`do , którego przechowywany wektor `subs` przechowuje `N` wartości wskazane przez argument `submatches`konstruktora, a którego wartość przechowywana `pos` wynosi zero.

## <a name="regex_token_iteratorregex_type"></a><a name="regex_type"></a>regex_token_iterator::regex_type

Typ wyrażenia regularnego do dopasowania.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem `basic_regex<Elem, RXtraits>`.

## <a name="regex_token_iteratorvalue_type"></a><a name="value_type"></a>regex_token_iterator::value_type

Typ podmeczu.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `sub_match<BidIt>`, `BidIt` gdzie jest parametr szablonu.

## <a name="see-also"></a>Zobacz też

[\<>regex](../standard-library/regex.md)\
[Klasa regex_constants](../standard-library/regex-constants-class.md)\
[Klasa regex_error](../standard-library/regex-error-class.md)\
[\<funkcje> regex](../standard-library/regex-functions.md)\
[Klasa regex_iterator](../standard-library/regex-iterator-class.md)\
[\<operatorzy> regex](../standard-library/regex-operators.md)\
[Klasa regex_traits](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)
