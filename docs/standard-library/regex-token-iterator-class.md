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
ms.openlocfilehash: 2cb66ce4cbee0936211e5e991b18f3ae4b8a7fe5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473518"
---
# <a name="regextokeniterator-class"></a>regex_token_iterator — Klasa

Klasa iteratora poddopasowania.

## <a name="syntax"></a>Składnia

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_token_iterator
```

## <a name="parameters"></a>Parametry

*BidIt*<br/>
Typ iteratora poddopasowania.

*Elem*<br/>
Typ elementów, do których ma pasować.

*RXtraits*<br/>
Klasa cech dla elementów.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt stały iterator do przodu. Model zawiera `regex_iterator` obiekt, który używa do wyszukiwania dla wyrażenia regularnego pasuje do sekwencji znaków. Wyodrębnia obiekty typu `sub_match<BidIt>` reprezentujący poddopasowania identyfikowane za pomocą wartości indeksu w wektorze przechowywanych `subs` dla każdego dopasowania wyrażenia regularnego.

Wartość indeksu,-1 wskazuje sekwencję znaków, począwszy od natychmiast po zakończeniu poprzedniego dopasowania wyrażenia regularnego lub od początku sekwencji znaków, jeśli wystąpił nie poprzedniego dopasowania wyrażenia regularnego i rozszerzanie na, ale nie Jeśli nie zostanie odnaleziony odpowiednik bieżącego w tym pierwszego znaku, bieżące dopasowanie wyrażenia regularnego lub na końcu sekwencji znaków. Dowolna inna wartość indeksu `idx` wyznacza zawartość grupy przechwytywania, przechowywane w `it.match[idx]`.

### <a name="members"></a>Elementy członkowskie

|Element członkowski|Wartość domyślna|
|-|-|
|`private regex_iterator<BidIt, Elem, RXtraits> it`||
|`private vector<int> subs`||
|`private int pos`||

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[regex_token_iterator](#regex_token_iterator)|Tworzy iterator.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[difference_type](#difference_type)|Typ różnicy iteratora.|
|[iterator_category](#iterator_category)|Typ kategorii iteratora.|
|[pointer](#pointer)|Typ wskaźnika do dopasowania.|
|[Odwołanie](#reference)|Typ odwołania do poddopasowanie.|
|[regex_type](#regex_type)|Typ wyrażenia regularnego do dopasowania.|
|[value_type](#value_type)|Typ poddopasowanie.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](#op_neq)|Porównuje Iteratory pod kątem nierówności.|
|[operator *](#op_star)|Uzyskuje dostęp do wyznaczonej poddopasowanie.|
|[operator++](#op_add_add)|Inkrementuje iterator.|
|[operator==](#op_eq_eq)|Porównuje Iteratory pod kątem równości.|
|[operator ->](#op_arrow)|Uzyskuje dostęp do wyznaczonej poddopasowanie.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wyrażenia regularnego >

**Namespace:** standardowe

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

## <a name="difference_type"></a>  regex_token_iterator::difference_type

Typ różnicy iteratora.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `std::ptrdiff_t`.

## <a name="iterator_category"></a>  regex_token_iterator::iterator_category

Typ kategorii iteratora.

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `std::forward_iterator_tag`.

## <a name="op_neq"></a>  regex_token_iterator::operator! =

Porównuje Iteratory pod kątem nierówności.

```cpp
bool operator!=(const regex_token_iterator& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Iterator do porównania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `!(*this == right)`.

## <a name="op_star"></a>  regex_token_iterator::operator *

Uzyskuje dostęp do wyznaczonej poddopasowanie.

```cpp
const sub_match<BidIt>& operator*();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `sub_match<BidIt>` obiekt reprezentujący grupy przechwytywania, określonego przez wartość indeksu `subs[pos]`.

## <a name="op_add_add"></a>  regex_token_iterator::operator ++

Inkrementuje iterator.

```cpp
regex_token_iterator& operator++();

regex_token_iterator& operator++(int);
```

### <a name="remarks"></a>Uwagi

Jeśli przechowywany iterator `it` jest iterator sekwencja kończenia pierwszy operator ustawia wartość przechowywaną `pos` wartość `subs.size()` (dzięki czemu iterator sekwencja kończenia). W przeciwnym razie operator zwiększa przechowywaną wartość `pos`; Jeśli wynik jest równa wartości `subs.size()` ustawia wartości przechowywanej `pos` zero i inkrementuje przechowywany iterator `it`. Jeśli zwiększenie pozostawia przechowywanego iteratora nierówne do iteratora sekwencja kończenia operator nic nie robi więcej. W przeciwnym razie, jeśli końcu poprzedniego dopasowania na końcu sekwencji znaków operatora ustawia przechowywaną wartość `pos` do `subs.size()`. W przeciwnym razie operator wielokrotnie zwiększa przechowywaną wartość `pos` aż `pos == subs.size()` lub `subs[pos] == -1` (co pozwala na zapewnienie dalej wyłuskania iteratora zwróci ogona sekwencji znaków, jeśli jedna z wartości indeksu jest wartość -1). We wszystkich przypadkach operator zwraca obiekt.

Drugi operator tworzy kopię obiektu, zwiększa obiektu, a następnie zwraca kopię.

## <a name="op_eq_eq"></a>  regex_token_iterator::operator ==

Porównuje Iteratory pod kątem równości.

```cpp
bool operator==(const regex_token_iterator& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Iterator do porównania.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `it == right.it && subs == right.subs && pos == right.pos`.

## <a name="op_arrow"></a>  regex_token_iterator::operator-&gt;

Uzyskuje dostęp do wyznaczonej poddopasowanie.

```cpp
const sub_match<BidIt> * operator->();
```

### <a name="remarks"></a>Uwagi

Element członkowski funkcji zwraca wskaźnik do `sub_match<BidIt>` obiekt reprezentujący grupy przechwytywania, określonego przez wartość indeksu `subs[pos]`.

## <a name="pointer"></a>  regex_token_iterator::Pointer

Typ wskaźnika do dopasowania.

```cpp
typedef sub_match<BidIt> *pointer;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `sub_match<BidIt>*`, gdzie `BidIt` jest parametr szablonu.

## <a name="reference"></a>  regex_token_iterator::Reference

Typ odwołania do poddopasowanie.

```cpp
typedef sub_match<BidIt>& reference;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `sub_match<BidIt>&`, gdzie `BidIt` jest parametr szablonu.

## <a name="regex_token_iterator"></a>  regex_token_iterator::regex_token_iterator

Tworzy iterator.

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

*pierwszy*<br/>
Początek sekwencji w celu dopasowania.

*ostatni*<br/>
Koniec sekwencji w celu dopasowania.

*środowisko odzyskiwania*<br/>
Wyrażenie regularne do dopasowania.

*f*<br/>
Flagi dopasowania.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje iterator sekwencja kończenia.

Drugi Konstruktor konstruuje obiekt, którego przechowywanego iteratora `it` jest inicjowany do `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, którego przechowywane wektor `subs` zawiera dokładnie jedną liczbę całkowitą z zakresu o wartości `submatch`i którego wartość przechowywana `pos` wynosi zero. Uwaga: wynikowy obiekt wyodrębnia poddopasowanie identyfikowane za pomocą wartości indeksu `submatch` dla każdego dopasowania wyrażenia regularnego pomyślnie.

Trzeci Konstruktor konstruuje obiekt, którego przechowywanego iteratora `it` jest inicjowany do `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, którego przechowywane wektor `subs` przechowuje kopię argumentu konstruktora `submatches`i którego wartość przechowywana `pos` wynosi zero.

Czwarty Konstruktor konstruuje obiekt, którego przechowywanego iteratora `it` jest inicjowany do `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, którego przechowywane wektor `subs` przechowuje `N` wartości wskazywany przez argument konstruktora `submatches`i którego przechowywane wartość `pos` wynosi zero.

## <a name="regex_type"></a>  regex_token_iterator::regex_type

Typ wyrażenia regularnego do dopasowania.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Uwagi

Typedef jest synonimem dla `basic_regex<Elem, RXtraits>`.

## <a name="value_type"></a>  regex_token_iterator::value_type

Typ poddopasowanie.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `sub_match<BidIt>`, gdzie `BidIt` jest parametr szablonu.

## <a name="see-also"></a>Zobacz także

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants, klasa](../standard-library/regex-constants-class.md)<br/>
[regex_error, klasa](../standard-library/regex-error-class.md)<br/>
[\<wyrażenie regularne > funkcji](../standard-library/regex-functions.md)<br/>
[regex_iterator, klasa](../standard-library/regex-iterator-class.md)<br/>
[\<wyrażenie regularne > operatorów](../standard-library/regex-operators.md)<br/>
[regex_traits, klasa](../standard-library/regex-traits-class.md)<br/>
[\<wyrażenie regularne > definicje typów](../standard-library/regex-typedefs.md)<br/>
